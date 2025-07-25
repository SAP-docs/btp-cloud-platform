<!-- loio1462ff0fa7f04839a96c51d968d15b34 -->

# Node.js Buildpack

This page provides solutions on known issues related to the Node.js buildpack.

If you can't find a solution to your problem, create an incident to component **`BC-CP-CF-BLDP`**.



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



## Application running on Node.js 18 fails after restage or redeploy



### Problem

You have a working Node.js application, which runs on Node.js 18. After restage or redeploy, it fails and is no longer working. In the logs, you see the following error messages:

```

					npm WARN EBADENGINE   required: { node: '^20 || ^22 || ^14' },
					
					npm WARN EBADENGINE   current: { node: 'v18.19.0', npm: '8.19.3' }
					
					npm WARN EBADENGINE Unsupported engine {

```



### Reason

Node.js 18 has reached end of life on **April 30, 2025** \(according to the [Node.js Roadmap](https://github.com/nodejs/Release)\), and was removed from the SAP BTP, Cloud Foundry environment with `nodejs_buildpack` version **v1.8.39**.



### Solution

To keep your Node.js applications up and running, please migrate to Node.js 20 or 22 as soon as possible.

In exceptional cases \(if you haven’t managed to migrate to a latest Node.js version\), to avoid application failures you can pin the last buildpack version that contains Node.js 18, for example, [v1.8.38](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.8.38). To learn how to do this, see: [Specify a buildpack version in manifest.yml](https://help.sap.com/docs/btp/sap-business-technology-platform/tips-and-tricks-for-node-js-applications?version=Cloud#specify-a-buildpack-version-in-manifest-yml)

> ### Note:  
> This approach can only be used as a temporary solution, until you complete the migration.

