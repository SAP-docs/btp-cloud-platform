<!-- loio40ded9d449124946b9a36e3d43e4c982 -->

# Migrating Applications from XSJS to Async-XSJS

This page explains how to migrate XSJS to Async-XSJS to benefit from latest Node.js versions \(16 and later\).



<a name="loio40ded9d449124946b9a36e3d43e4c982__section_wmd_ghc_rvb"/>

## Context

SAP HANA XSJS applications are based on *synchronous* API. On the other hand, Node.js is an *asynchronous* runtime. Thus, for XSJS applications that run on Node.js there is a certain code incompatibility. Up until Node.js 14, this incompatibility has been handled by an NPM package called [@sap/fibers](https://www.npmjs.com/package/@sap/fibers) \(forked from [laverdet/node-fibers](https://github.com/laverdet/node-fibers)\). Unfortunately, *@sap/fibers* is not compatible with Node.js version 16 and higher.

Also, Node.js supports two kinds of scripts:

-   CommonJS - it's synchronous and does not support top-level await. In XSJS, all files are loaded as common Java scripts.

-   ECMAScript - it's fully asynchronous and supports top-level await


The only possible way for your XSJS applications to be up and running on latest Node.js versions is to modify their codes – by migrating them to a new XSJS layer with asynchronous API. See the migration process below to learn what you need to do.

> ### Note:  
> In exceptional cases \(if you haven’t completed the migration to Async-XSJS\), to avoid application failures during redeployment, you may pin the last buildpack version that contains Node.js14, as provided by the [nodejs-buildpack](https://github.com/cloudfoundry/nodejs-buildpack) community. You can do this in your **manifest.yml** file, and then redeploy your app. To learn how, see: [Specify a buildpack version in manifest.yml](tips-and-tricks-for-node-js-applications-3a5fe88.md#loio3a5fe887f6e64abb827494baac352059__specify_node_bp_version) 
> 
> Please be advised, that SAP does **not** recommended usage of Node.js 14 after April 2023, as no support and security fixes will be provided for this version.



<a name="loio40ded9d449124946b9a36e3d43e4c982__section_akt_ghc_rvb"/>

## Migration Process

1.  To switch from XSJS to Async-XSJS, open your `package.json` file, and in the **dependencies** section, add the [@sap/async-xsjs](https://www.npmjs.com/package/@sap/async-xsjs) package. For example:

    ```
    
    {
      "name": "myapp",
      "engines": {
        "node": "16.x.x"
      },
    ...
      "dependencies": {
    	"express": "^4.18.1", 
    	"@sap/xssec" : "^3.2.15",
    	"@sap/async-xsjs": "^1.0.0"	
      }
    ...
    }
    ```

2.  Enable the ECMAScript virtual-machine interface on application startup.

    With *@sap/async-xsjs*, your asynchronous JavaScript code is loaded by default as ECMAScript \(ES\). To make use of the support that Node.js provides for ES modules, you need to start your application using the option *\--experimental-vm-modules*.

    ```
    
    {
      "name": "myapp",
      "engines": {
        "node": "16.x.x"
      },
    ...
      "dependencies": {
    	"express": "^4.18.1", 
    	"@sap/xssec" : "^3.2.15",
    	"@sap/async-xsjs": "^1.0.0"	
      }
      "scripts": {
        "start": "node --experimental-vm-modules index.js"
    	...
      },
    ...
    }
    ```

3.  In all your `.xsjs` and `.xsjslib` files, for every asynchronous function call, add an **await** statement.

4.  Every function that uses an **await** statement must be declared as **async**.

5.  XSJS files should be loaded as ECMAScript. To do this, in the end of every function in an `.xsjslib` file, add an **export** statement.

    > ### Note:  
    > You can do this for `.xsjs` files too, but that would be only necessary if a function needs to be exported for some reason \(like job execution or job handling\).

6.  If you're using the [@sap/audit-logging](https://www.npmjs.com/package/@sap/audit-logging) package in your XSJS application, the code must be migrated. For example, if you have a code snippet like this:

    ```
    
    auditLog
      .securityMessage('Content of the message')
      .by($.session.getUsername())
      .sync.log();
    ```

    it should be converted to:

    ```
    
    await auditLog
      .securityMessage('Content of the message')
      .by($.session.getUsername())
      .log();
    ```


To do these steps, refer to the API of the new [@sap/async-xsjs](https://www.npmjs.com/package/@sap/async-xsjs) package. See: [SAP HANA 2 - ASYNC XS JavaScript API Reference](https://help.sap.com/doc/215e6913c0e44223b2842f16c927ec6d/2.0.07/en-US/index.html) 

You can find this API reference if you go to the [SAP HANA Platform](https://help.sap.com/docs/SAP_HANA_PLATFORM?task=use_task) product page, and then choose *View All* → *SAP HANA Asynchronous XS JavaScript API Reference*.

> ### Note:  
> For huge application codes, you can optimize your work by using a migration tool. See: [@sap/async-migrator](https://github.com/sap/async-migrator) 
> 
> Bear in mind that this is an open-source product and a fully-covered migration of your XSJS code is not guaranteed.



<a name="loio40ded9d449124946b9a36e3d43e4c982__section_i1f_q33_fwb"/>

## Examples

The following exemplary code snippet from an `.xsjslib` file:

> ### Example:  
> Original Code
> 
> ```
> 
> ...
> 
> $.import('lib', 'converters');
> 
> function select(tableName){
>   let conn;
>   try {
>     conn = $.hdb.getConnection();
>     let resultSet = conn.executeQuery('SELECT * FROM "' + tableName + '"');
>     return $.lib.converters.resultSet_to_Entities(resultSet, ["id", "name"]);
>   } finally {
>     if (conn) {
>       conn.commit();
>       conn.close();
>     }
>   }
> }
> ```

should be converted to:

> ### Example:  
> Modified Code
> 
> ```
> 
> ...
> 
> await $.import('lib', 'converters');
> 
> async function select(tableName){
>   let conn;
>   try {
>     conn = await $.hdb.getConnection();
>     let resultSet = await conn.executeQuery('SELECT * FROM "' + tableName + '"');
>     return $.lib.converters.resultSet_to_Entities(resultSet, ["id", "name"]);
>   } finally {
>     if (conn) {
>       await conn.commit();
>       conn.close();
>     }
>   }
> }
> 
> export default {select};
> ```



<a name="loio40ded9d449124946b9a36e3d43e4c982__section_qyr_cxs_5vb"/>

## Side Effects



### `.sync` Statements

Since the [@sap/fibrous](https://www.npmjs.com/package/@sap/fibrous) package is not supported anymore, the **.sync** statements will no longer work. To fix a code that uses the `sync` property, see **step 4** from the procedure above.



### `this` Pointer

Since all `.xsjs` and `.xsjslib` files are based on ECMAScript module, **this** pointer behaves differently from when used with CommonJS. For example, when ECMAScript is loaded, the value of **this** is *undefined*.

In the context of a module function execution, the value of pointer **this** is the **export <object\>** module.

The following sample code will throw an error due to `this=undefined` during loading.

> ### Example:  
> === my.xsjslib ===XSJS ====
> 
> ```
> 
> this.funcA = function(){}
> (function(self){
>   self.funcB = function(){};
> })(this);
> 
> this.x = 5;
> 
> ```

Adapt the code to Async-XSJS:

> ### Example:  
> === my.xsjslib ===Async-XSJS ====
> 
> ```
> 
> function funcA(){}
> function funcB(){}
> 
> var x = 5;
> 
> export default {funcA, funcB, x};
> 
> 
> ```

This example just illustrates the problem and gives a possible solution. Depending on the software design of your application, there could be various solutions.

To learn more about the differences between these two kinds of Node.js scripts, see:

-   [ECMAScript documentation](https://www.ecma-international.org/technical-committees/tc39/)
-   [Differences between ES modules and CommonJS](https://nodejs.org/api/esm.html#differences-between-es-modules-and-commonjs)



### `Array.forEach` and `Array.map`

In the Async-XSJS layer, the **Array.forEach** and **Array.map** functions change their behavior when the argument function is asynchronous.

For example, the SQL statements are read and executed sequentially, one after the other, and then written to the database in the same order.

> ### Example:  
> === my.xsjslib ===XSJS ===
> 
> ```
> 
> var sqls = ['create table "PRODUCT"("ID" integer, "NAME": varchar(200))', 
>             'insert into "PRODUCT" values (1, \'iphone\')'
>                                 ];
> 
> function runSql(sql){
>   var conn = $.hdb.getConnection();
>   conn.execute(sql);
> }
> 
> sqls.forEach(runSql);
> 
> ...
> <additional code>
> 
> ```

The following example shows how the same code looks when adapted to Async-XSJS:

> ### Example:  
> === my.xsjslib ===Async-XSJS ===
> 
> ```
> 
> var sqls = ['create table "PRODUCT"("ID" integer, "NAME": varchar(200))', 
>             'insert into "PRODUCT" values (1, \'iphone\')'
>                                 ];
> 
> async function runSql(sql){
>   var conn = await $.hdb.getConnection();
>   await conn.execute(sql);
> }
> 
> sqls.forEach(runSql);
> 
> ...
> <some additional code>
> 
> 
> 
> ```

In the previous example, the SQL statements are only scheduled for execution; they are not executed immediately. When it is time to record them in the database, the order of operation might be different to the order in which the tables were initially read.

> ### Caution:  
> If you have additional code after the **sqls.forEach** function, it will be executed before any of the SQL statements.

To avoid unwanted side effects and ensure that the SQL statements are created in the database in the correct order, you can replace ***sqls.forEach\(runSql\);*** with one of the following examples:

-   > ### Example:  
    > *Sequential execution*
    > 
    > ```
    > 
    > for (int i=0; i<sqls.length; i++){
    >   await runSql(sqls[i]);
    > }
    > 
    > <some additional code>
    > 
    > //SQL statements are executed in the correct order, then the additional code is executed 
    > ```

-   > ### Example:  
    > *Parallel execution*
    > 
    > ```
    > 
    > await Promise.all(sqls.map(runSql));
    > 
    > <some additional code>
    > 
    > //SQL statements are executed in a random order, then the additional code is executed
    > 
    > 
    > ```


The same configuration steps can be applied for `Array.map` in analogical way – just replace `sqls.forEach` with **`sqls.map`**.

Another function that can be asynchronous is `Array.reduce`.

