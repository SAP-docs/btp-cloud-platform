<!-- loio1462ff0fa7f04839a96c51d968d15b34 -->

# Node.js Buildpack: Troubleshooting

This page provides solutions on known issues related to the Node.js buildpack.

If you can't find a solution to your problem, create an incident to component **`BC-CP-CF-BLDP`**.

To learn how to start, see: [Troubleshooting](troubleshooting-073b7fc.md)



<a name="loio1462ff0fa7f04839a96c51d968d15b34__section_np5_node_ccc"/>

## XSJS application stopped working after upgrade to Node v.16



### Problem

You have an XSJS application, which was working fine on Node.js 14.

After an upgrade to Node 16, it fails to rebuild or redeploy and is no longer working. In the logs, you see the following error messages:

```

npm ERR! gyp ERR! command "/opt/nodejs/node-v16.15.0-linux-x64/bin/node"

"/home/user/.node_modules_global/lib/node_modules/npm/node_modules/node-gyp/bin/node-gyp.js"

"rebuild"npm ERR! gyp ERR! cwd /home/user/projects/DataCentral/dc_node/node_modules/@sap/xsjs/node_modules/@sap/fibers
```

You may also encounter the following error messages:

```

npm WARN EBADENGINE   required: { node: '^10 || ^12 || ^14' },

npm WARN EBADENGINE   current: { node: 'v16.19.0', npm: '8.19.3' }

npm WARN EBADENGINE Unsupported engine {

npm WARN EBADENGINE   package: '@sap/xsjs@6.7.5'
```



### Reason

XSJS applications use the [@sap/fibers](https://www.npmjs.com/package/@sap/fibers) library \(on which the [@sap/xsjs](https://www.npmjs.com/package/@sap/xsjs) package depends\), which is **not supported** on Node.js 16 and later versions.



### Solution

To keep your XSJS applications up and running on latest Node.js versions, you need to migrate them to the new XSJS layer with an asynchronous API. To learn how to do this, see:

-   [Migrating Applications from XSJS to Async-XSJS](migrating-applications-from-xsjs-to-async-xsjs-40ded9d.md)

-   [SAP HANA 2 - ASYNC XS JavaScript API Reference](https://help.sap.com/doc/215e6913c0e44223b2842f16c927ec6d/2.0.07/en-US/index.html)

-   [https://www.npmjs.com/package/@sap/async-xsjs](https://www.npmjs.com/package/@sap/async-xsjs)


> ### Note:  
> Bear in mind that Node.js 14 was removed from the [community buildpack](https://github.com/cloudfoundry/nodejs-buildpack) on **April 30, 2023**.

We recommend migration to Node.js 18 or 20, and respectively migration to Async-XSJS, as soon as possible.

In exceptional cases \(if you haven’t managed to complete the migration to Async-XSJS\), to avoid application failures during redeployment, you can pin the last buildpack version that contains Node.js 14, as provided by the [nodejs-buildpack](https://github.com/cloudfoundry/nodejs-buildpack/releases) community. To learn how to do this, see: [Specify a buildpack version in manifest.yml](https://help.sap.com/docs/btp/sap-business-technology-platform/tips-and-tricks-for-node-js-applications?version=Cloud#specify-a-buildpack-version-in-manifest-yml)

Nevertheless, this approach can only be used as a temporary solution, until you complete the migration!

> ### Remember:  
> SAP does **not** recommend use of deprecated Node.js versions, as support and security fixes are no longer provided for them.



<a name="loio1462ff0fa7f04839a96c51d968d15b34__section_np5_node_bbb"/>

## Node.js 16 has reached end of life



### Problem

Node.js 16 reached end of life on **September 11, 2023** \(instead of April 2024, as originally planned\), and shortly after was removed from the [community buildpack](https://github.com/cloudfoundry/nodejs-buildpack). This means that, after this date, deployment and redeployment of applications running on Node.js 16 would fail. For more information, see:

-   [Node.js Roadmap](https://github.com/nodejs/Release)

-   [Bringing forward the End-of-Life Date for Node.js 16](https://nodejs.org/en/blog/announcements/nodejs16-eol)




### Solution

To avoid such issues, please migrate to Node.js 18 or higher as soon as possible!

In exceptional cases \(if you haven’t managed to switch to Node.js 18 or 20 yet\), to avoid application failures during redeployment, you can pin the last buildpack version that contains Node.js 16, as provided by the [nodejs-buildpack](https://github.com/cloudfoundry/nodejs-buildpack/releases) community. To learn how to do this, see: [Specify a buildpack version in manifest.yml](https://help.sap.com/docs/btp/sap-business-technology-platform/tips-and-tricks-for-node-js-applications?version=Cloud#specify-a-buildpack-version-in-manifest-yml)

Nevertheless, this approach can only be used as a temporary solution, until you complete migration to a later version of Node.js!

> ### Remember:  
> SAP does **not** recommend use of deprecated Node.js versions, as support and security fixes are no longer provided for them.



<a name="loio1462ff0fa7f04839a96c51d968d15b34__section_node_ccc"/>

## Application running on Node.js 18 fails after restage or redeploy



### Problem

You have a working Node.js application, which runs on Node.js 18. After restage or redeploy, it fails and is no longer working. In the logs, you see the following error messages:

```

npm WARN EBADENGINE   required: { node: '^20 || ^22 || ^14' },
					
npm WARN EBADENGINE   current: { node: 'v18.19.0', npm: '8.19.3' }
					
npm WARN EBADENGINE Unsupported engine {

```



### Reason

Node.js 18 has reached end of life on **April 30, 2025** \(according to the [Node.js Roadmap](https://github.com/nodejs/Release)\), and was removed from the SAP BTP, Cloud Foundry environment with `nodejs_buildpack` version **v1.8.41**.



### Solution

To keep your Node.js applications up and running, please migrate to Node.js 20 or 22 as soon as possible.

In exceptional cases \(if you haven’t managed to migrate to a latest Node.js version\), to avoid application failures you can pin the last buildpack version that contains Node.js 18, for example, [v1.8.39](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.8.39). To learn how to do this, see: [Specify a buildpack version in manifest.yml](https://help.sap.com/docs/btp/sap-business-technology-platform/tips-and-tricks-for-node-js-applications?version=Cloud#specify-a-buildpack-version-in-manifest-yml)

If you are using MTA deployment descriptors, in your *mtad.yaml* file you need to define module type **javascript.nodejs** and set parameter `buildpack` to **nodejs\_buildpack**. For example:

```

modules:
- name: myapp
  type: javascript.nodejs
  parameters:
    memory: 512M
    buildpack: nodejs_buildpack
```

If you want to pin a particular buildpack version \(for example, **1.8.39**\), you can do it the following way:

```

modules:
- name: myapp
  type: javascript.nodejs
  parameters:
    memory: 512M
    buildpack: https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.39

```

To learn more, see [MTA Module Types](https://help.sap.com/docs/btp/sap-business-technology-platform/modules#mta-module-types).

> ### Note:  
> This approach can only be used as a temporary solution, until you complete the migration.

