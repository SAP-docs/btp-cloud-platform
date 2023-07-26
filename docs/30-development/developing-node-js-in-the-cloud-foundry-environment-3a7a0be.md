<!-- loio3a7a0bece0d044eca59495965d8a0237 -->

# Developing Node.js in the Cloud Foundry Environment

This section offers selected information for Node.js development on SAP BTP, Cloud Foundry and references to more detailed sources.



You'll get information about the buildpack supported by SAP, the Node.js packages, and how to consume them in your application.

There is also a tutorial with an introduction to securing your application, and some tips and tricks for developing and running Node.js applications on SAP BTP, Cloud Foundry.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wzk_sdp_rdb"/>

## Node.js Community Buildpack

SAP BTP uses the standard [Node.js buildpack](https://github.com/cloudfoundry/nodejs-buildpack) provided by the Cloud Foundry community to deploy Node.js applications.

To get familiar with the buildpack and how to deploy applications with it, take a look at the [Cloud Foundry Node.js Buildpack documentation](https://docs.cloudfoundry.org/buildpacks/node/index.html).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_ndw_lxz_pdb"/>

## SAP Node.js Packages

You can download and consume SAP developed Node.js packages via the SAP NPM Registry. There is an overview of Node.js packages developed by SAP, what they are meant for, and where they are included in the SAP HANA Developer Guide for XS Advanced Model. See:

-   [Download and Consume SAP Node.js Packages](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/ddcff14e28384810a352bb6512cd3448.html)

-   [Standard Node.js Packages](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/54513272339246049bf438a03a8095e4.html)

-   [The SAP NPM Registry](https://help.sap.com/viewer/4505d0bdaf4948449b7f7379d24d0f0d/2.0.latest/en-US/726e5d41462c4eb29eaa6cc83ff41e84.html)




<a name="loio3a7a0bece0d044eca59495965d8a0237__section_kfn_ldv_f5b"/>

## Buildpack Versioning

The SAP BTP, Cloud Foundry environment provides one recent version of the Node.js buildpack as part of its system buildpacks. To check this version:

1.  Log in to a particular SAP BTP region and subaccount. Execute: **`cf api <SAP BTP region>`**

    For example: **`cf api https://api.cf.eu10.hana.ondemand.com`**

2.  Then execute: **`cf buildpacks`**


To learn about changes in Node.js versions and features, regularly check the latest [buildpack releases](https://github.com/cloudfoundry/nodejs-buildpack/releases) in the GitHub community page.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_w1d_tr1_krb"/>

## Supported Versions

The `nodejs_buildpack` running on SAP BTP, Cloud Foundry environment supports the following versions:

-   Node.js **16**
-   Node.js **18**



### Node.js 14 end of life

Please be informed that Node.js 14 reached end of life on **April 30, 2023** as stated in the [Node.js Roadmap](https://github.com/nodejs/Release), and was removed from the Cloud Foundry community in [version 1.8.10](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.8.10). This means that deployment and redeployment of applications with Node.js 14 will fail. To avoid such issues, please migrate to Node.js 16 or higher as soon as possible.

Applications using XSJS are strongly impacted as the [@sap/fibers](https://www.npmjs.com/package/@sap/fibers) library \(on which [@sap/xsjs](https://www.npmjs.com/package/@sap/xsjs) depends\) is **not supported** on Node.js 16 and later versions. To learn more, see: [Migrating Applications from XSJS to Async-XSJS](migrating-applications-from-xsjs-to-async-xsjs-40ded9d.md)

In exceptional cases \(if you haven’t completed the migration to Node.js 16\), to avoid application failures during redeployment, you may pin the last buildpack version that contains Node.js 14, as provided by the [nodejs-buildpack](https://github.com/cloudfoundry/nodejs-buildpack) community. To learn how, see: [Specify a buildpack version in manifest.yml](tips-and-tricks-for-node-js-applications-3a5fe88.md#loio3a5fe887f6e64abb827494baac352059__specify_node_bp_version) 

> ### Note:  
> Please be advised that SAP does **not** recommend use of Node.js 14, as no support and security fixes are provided for this version anymore.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_o5d_4t1_krb"/>

## What's New

To see the latest news and updates about the Node.js system buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=Node.js%20System%20Buildpack).

> ### Caution:  
> In May 2023, SAP migrated the root file system used in the Cloud Foundry environment in SAP BTP from the deprecated `cflinuxfs3` stack to **`cflinuxfs4`**. If you are running Node.js applications on SAP BTP, Cloud Foundry using the Node.js buildpack, we recommend that you update and migrate your applications, as well as the Node.js buildpack. For more information about migration timelines, risks, and consequences, see:
> 
> -   [Deprecation of Cloud Foundry Stack cflinuxfs3 and Migration to cflinuxfs4](https://blogs.sap.com/2023/02/16/deprecation-of-cloud-foundry-stack-cflinuxfs3-and-migration-to-cflinuxfs4/)
> 
> -   [What's New for SAP BTP, Cloud Foundry Runtime \(cflinuxfs\)](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?Component=SAP%20BTP,%20Cloud%20Foundry%20Runtime&q=cflinuxfs&locale=en-US&version=Cloud)



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_iwr_zxf_hvb"/>

## Troubleshooting

-   Guided Answers: [Node.js Buildpack](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51218/?version=current)
-   SAP Note: [3100002](https://launchpad.support.sap.com/#/notes/3100002) *How to pin the new nodejs\_buildpack\_migratе solution*



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_jnl_4xz_pdb"/>

## Node.js Tutorial

The following tutorial will guide you through creating a Node.js application in Cloud Foundry Command Line Interface \(cf CLI\), consuming a Cloud Foundry service, and setting up authentication and authorization checks. See: [Create an Application with Cloud Foundry Node.js Buildpack](https://developers.sap.com/tutorials/btp-cf-buildpacks-node-create.html)



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wc2_5xz_pdb"/>

## Tips and Tricks

For selected tips and tricks for your Node.js development, see [Tips and Tricks for Node.js Applications](tips-and-tricks-for-node-js-applications-3a5fe88.md).

