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

1.  Log in to a particular SAP BTP region and subaccount. Execute: `cf api <SAP BTP region>`

    For example: `cf api https://api.cf.eu10.hana.ondemand.com`

2.  Then execute: `cf buildpacks`


To learn about changes in Node.js versions and features, regularly check the latest [buildpack releases](https://github.com/cloudfoundry/nodejs-buildpack/releases) in the GitHub community page.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_w1d_tr1_krb"/>

## Supported Versions

The `nodejs_buildpack` supports the following versions:

-   Node.js **14**
-   Node.js **16**
-   Node.js **18**

> ### Caution:  
> For applications using the *@sap/xsjs* library, we recommend that you use version **14** until official SAP communication is sent for the successor of this library that will enable usage of Node.js 16 and later. See also: [Application stopped working after upgrade to Node v.16](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51218:52922/?version=current)
> 
> For all other applications \(not using *@sap/xsjs*\), we recommend that you use version **16** or later, or to proceed with migration to Node.js 16 or later.



### Node.js 14 is reaching end of life

To all Cloud Foundry customers using `nodejs_buildpack` – please be informed that Node.js 14 will reach end of life in **May 2023** as stated in the [Node.js Roadmap](https://github.com/nodejs/Release), and shortly after will be removed from the buildpack. This means that deployment and redeployment of applications with Node.js 14 will fail. To avoid such issues, please plan migration to Node.js 16 or later.

After May 2023, you can still pin to an **online** `nodejs_buildpack` version containing Node.js 14, by setting a URL to GitHub. Nevertheless, this approach can only be used as a temporary solution until you complete migration to a latest version of Node.js.

To pin to a particular buildpack version from GitHub, for example [1.8.4](https://github.com/cloudfoundry/nodejs-buildpack/releases/tag/v1.8.4), proceed as follows:

1.  Open the **manifest.yml** file of your application.

2.  For the `buildpack` attribute, add the URL to version 1.8.4, like this:

    ```
    
    ---
    applications:
    - name: myapp
      random-route: true
      buildpack: https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.4
      memory: 128M
    ```

3.  Redeploy your application by executing: `cf push myapp`


**Alternative way:**

If you don't want to make changes in your **manifest.yml** file, you can directly execute:

 `cf push myapp -b https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.4` 

> ### Tip:  
> To pin this buildpack version for all applications running in your SAP BTP subaccount, execute:
> 
> `cf push -b https://github.com/cloudfoundry/nodejs-buildpack.git#v1.8.4`

> ### Note:  
> Please be advised, that SAP does **not** recommended usage of Node.js 14 after May 2023, as no support will be provided for deprecated versions.



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_o5d_4t1_krb"/>

## What's New

To see the latest news and updates about the Node.js system buildpack, regularly check the release notes on the [What's New portal](https://help.sap.com/whats-new/cf0cb2cb149647329b5d02aa96303f56?locale=en-US&Component=Node.js%20System%20Buildpack).



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_iwr_zxf_hvb"/>

## Troubleshooting

-   Guided Answers: [Node.js Buildpack](https://ga.support.sap.com/dtp/viewer/#/tree/3254/actions/51226:51218/?version=current)
-   SAP Note: [3100002](https://launchpad.support.sap.com/#/notes/3100002) *How to pin the new nodejs\_buildpack\_migratе solution*



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_jnl_4xz_pdb"/>

## Node.js Tutorial

The following tutorial will guide you through creating a Node.js application in Cloud Foundry Command Line Interface \(cf CLI\), consuming a Cloud Foundry service, and setting up authentication and authorization checks. See: [Create a Node.js Application via CF CLI](https://developers.sap.com/tutorials/btp-cf-buildpacks-node-create.html)



<a name="loio3a7a0bece0d044eca59495965d8a0237__section_wc2_5xz_pdb"/>

## Tips and Tricks

For selected tips and tricks for your Node.js development, see [Tips and Tricks for Node.js Applications](tips-and-tricks-for-node-js-applications-3a5fe88.md).

