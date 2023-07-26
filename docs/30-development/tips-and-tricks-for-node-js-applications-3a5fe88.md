<!-- loio3a5fe887f6e64abb827494baac352059 -->

# Tips and Tricks for Node.js Applications



<a name="loio3a5fe887f6e64abb827494baac352059__section_emv_pf1_m1b"/>

## Get to Know the Node.js Buildpack for the Cloud Foundry Environment

Check the following Cloud Foundry documentation:

-   [Node.js Buildpack](https://docs.cloudfoundry.org/buildpacks/node/index.html)
-   [Tips for Node.js Developers](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html)



<a name="loio3a5fe887f6e64abb827494baac352059__section_ddt_syz_lqb"/>

## NPM Version

When deploying an application in Cloud Foundry environment without specifying the *npm* version in the **package.json** file, it will install the default *npm* version \(depending on the Node.js version\) during the build step. A version mismatch can cause the build step to fail.

To check your Node.js version, execute:

```
node --version
```

To check your npm version, execute:

```
npm --version
```

> ### Tip:  
> We recommend that you use the same *npm* version as the one on the Cloud Foundry environment.

Alternatively, you can specify the *npm* version in the **package.json** file. For example, if you use Node.js 16, you can set:

```


"engines": {
"npm": "^8.4.1"
},

```

> ### Note:  
> Bear in mind that **Node.js** and **npm** are different products, with their own independent versions. To check the version mapping between them, see [NodeJS: Previous Releases](https://nodejs.org/en/download/releases/).



<a name="loio3a5fe887f6e64abb827494baac352059__section_vgc_pg1_m1b"/>

## Vendor Application Dependencies

Sometimes, productive Cloud Foundry applications might need to be deployed as self-contained. That means, they need to carry all of their dependencies so that the staging process does not require any network calls. For more information, see: [Vendoring App Dependencies](https://docs.cloudfoundry.org/buildpacks/node/index.html#vendoring) 

Depending on the region where the application is deployed:

-   Running on the China \(Shanghai\) region: it is **mandatory** for the application to be deployed as self-contained.

-   Running on the AWS, Azure, or GCP regions: it is only **recommended** but not mandatory for the application to be deployed as self-contained.


There are various reasons to use vendoring. For example, productive applications usually rely on security scans and because *npm* doesn't provide reliable dependency fetch, it's possible that your Node.js application ends up with different dependencies in case such are installed during deployment. Additionally, *npm*downloads any missing dependencies from its registry, so if this registry isn't accessible for some reason, the deployment can fail.

> ### Note:  
> Bear in mind when using dependencies containing native code that you need to reinstall in the same environment as the Cloud Foundry container, or make sure that the package has built-in support for it.

To ensure that prepackaged dependencies are pushed to the Cloud Foundry environment and on-premise runtime, make sure that the **`node_modules`** directory isn’t listed in the `.cfignore` file. It’s also preferable that development dependencies are not deployed for productive deployments. To ensure that, execute:

```
npm prune --production
```



<a name="loio3a5fe887f6e64abb827494baac352059__section_p2n_yg1_m1b"/>

## Out of Memory at Runtime

For performance reasons, Node.js \(powered by V8 engine\) has lazy garbage collection. Even if there are no memory leaks in your application, this can cause occasional restarts, as explained in the official Cloud Foundry documentation – [Tips for Node.js Applications](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html).

Enforce the garbage collector to run before the memory is consumed by limiting the V8 application’s heap size at about ~75% of the available memory. To do that, you can either use the `OPTIMIZE_MEMORY` environment variable supported by the Node.js buildpack, or specify the V8 heap size directly in your application *start* command \(recommended\).

Example for an application started with 256M of RAM:

> ### Sample Code:  
> ```
> node --max_old_space_size=192 server.js
> ```

You can optimize V8 behavior using additional options. To list these options, execute:

```
node --v8-options
```



<a name="loio3a5fe887f6e64abb827494baac352059__specify_node_bp_version"/>

## Specify a buildpack version in `manifest.yml`

At some point, you might need \(or decide\) to deploy your application with a particular buildpack version from the community [nodejs-buildpack](https://github.com/cloudfoundry/nodejs-buildpack) repository. For example, if this buildpack contains a Node.js version that is no longer supported by SAP BTP, Cloud Foundry.

Let's say, you want to pin version [1.8.9](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.8.9). To do that, proceed as follows:

1.  Open the **manifest.yml** file of your Node.js application.

2.  For the `buildpack` attribute, add the URL to version 1.8.4, like this:

    ```
    
    ---
    applications:
    - name: myapp
      random-route: true
      buildpack: https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.9
      memory: 128M
    ```

3.  Redeploy your application by executing:

    ```
    cf push myapp
    ```


**Alternative way:**

If you don't want to make changes in your **manifest.yml** file, you can include the buildpack version in the `cf push` command.

-   To deploy just a **single** application with this particular buildpack version, execute:

    ```
    cf push myapp -b https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.9
    ```

-   To pin this buildpack version for **all** applications running in your SAP BTP, Cloud Foundry subaccount, execute:

    ```
    cf push -b https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.9
    ```




<a name="loio3a5fe887f6e64abb827494baac352059__section_q5v_fv5_41b"/>

## Specify application memory in `manifest.yml`

When deploying an application in the Cloud Foundry environment without specifying the application memory requirements, the Cloud Foundry controller assigns the default \(1G of RAM currently\) for your application. Many Node.js applications require less memory and assigning the default is a waste of resources.

To save memory from your quota, specify the memory size in the deployment descriptor of your Cloud Foundry application – `manifest.yml`. For example:

```

---
applications:
- name: myapp
  memory: 128M
  buildpack: nodejs_buildpack
...
```

