<!-- loio3a5fe887f6e64abb827494baac352059 -->

# Tips and Tricks for Node.js Applications



<a name="loio3a5fe887f6e64abb827494baac352059__section_emv_pf1_m1b"/>

## Get to Know the Node.js Buildpack for the Cloud Foundry Environment

Check the Tips and Tricks for Node.js applications in the [Cloud Foundry Node.js Buildpack](https://docs.cloudfoundry.org/buildpacks/node/index.html) documentation.

 



<a name="loio3a5fe887f6e64abb827494baac352059__section_ddt_syz_lqb"/>

## NPM Version

When deploying an application in Cloud Foundry environment without specifying the *npm* version in **package.json**, it will install the default version \(currently 6.4.13\) during the build step. A version mismatch \(especially if using *npm* v.7 and higher\) can cause the build step to fail.

To check your *npm* version, you can execute:

```
npm --version
```

> ### Tip:  
> We recommend that you use the same *npm* version as the one on the Cloud Foundry environment.

Alternatively, you can specify the *npm* version in the **package.json** file:

```

```javascript
### Sample Code
"engines": {
"npm": "^7.20.2"
}
```
```



<a name="loio3a5fe887f6e64abb827494baac352059__section_vgc_pg1_m1b"/>

## Vendor Application Dependencies

Vendoring of Node.js application dependencies is discussed in the documentation for the Cloud Foundry environment. Even though SAP BTP is a connected environment, for productive applications we recommend that you vendor application dependencies.

There are various reasons for this. For example, productive applications usually rely on security scans and because `npm` doesn't provide reliable dependency fetch, it's possible that your application ends up with different dependencies in case such are installed during deployment. Additionally, `npm` downloads any missing dependencies from its registry, so if this registry isn't accessible for some reason, the deployment can fail.

> ### Note:  
> Be aware when using dependencies containing native code that you need to reinstall in the same environment as the Cloud Foundry container, or that the package has built-in support for it.

To ensure that prepackaged dependencies are pushed to the Cloud Foundry environment and on-premise runtime, make sure that `node_modules` directory isn’t listed in the `.cfignore` file. It’s also preferable that development dependencies aren't deployed for productive deployments. To ensure that, run this command:

```
npm prune --production
```



<a name="loio3a5fe887f6e64abb827494baac352059__section_p2n_yg1_m1b"/>

## Out of Memory at Runtime

For performance reasons, Node.js \(V8\) has lazy garbage collection. Even if there are no memory leaks in your application, this can cause occasional restarts, as explained in the [Tips for Node.js Applications](https://docs.cloudfoundry.org/buildpacks/node/node-tips.html) section in the Node.js Buildpack documentation for the Cloud Foundry Environment.

Enforce the garbage collector to run before the memory is consumed by limiting the V8 application’s heap size at about ~75% of the available memory.

You can either use the `OPTIMIZE_MEMORY` environment variable supported by Node.js buildpack, or specify the V8 heap size directly in your application start command \(recommended\). Example for an application started with 256M of RAM:

> ### Sample Code:  
> ```
> node --max_old_space_size=192 server.js
> ```

You can optimize V8 behavior using additional options. You can list them using the command:

```
node --v8-options
```



<a name="loio3a5fe887f6e64abb827494baac352059__section_q5v_fv5_41b"/>

## Specify Application Memory in `manifest.yml`

When deploying an application in the Cloud Foundry environment without specifying the application memory requirements, the controller of the Cloud Foundry environment assigns the default \(1G of RAM currently\) for your application. Many Node.js applications require less memory and assigning the default is a waste of resources.

To save memory from your quota, specify the memory size in the descriptor of the deployment in the Cloud Foundry environment – `manifest.yml`. To learn how to do that, see the open source Cloud Foundry environment documentation under [Deploying with Application Manifests](https://docs.cloudfoundry.org/devguide/deploy-apps/manifest.html#memory).

