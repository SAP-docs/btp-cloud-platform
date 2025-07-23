<!-- loio4e2f2b506c2d4ea49f808fee70bc2fe6 -->

# Community Java Buildpack

Find SAP-managed Cloud Foundry Java components and updates that belong to the community [java-buildpack](https://github.com/cloudfoundry/java-buildpack).



<a name="loio4e2f2b506c2d4ea49f808fee70bc2fe6__section_kfn_ldv_f5b"/>

## Buildpack Versioning

The SAP BTP, Cloud Foundry environment provides one recent version of **`java_buildpack`** as part of its system buildpacks. To check this version, proceed as follows:

1.  Log in to a particular SAP BTP region and subaccount. For example, if your region is **eu10**, run:

    ```
    cf login -a https://api.cf.eu10.hana.ondemand.com
    ```

2.  Then run:

    ```
    cf buildpacks
    ```


To learn about changes in the Java buildpack's versions and features, regularly check the latest [buildpack releases](https://github.com/cloudfoundry/java-buildpack/releases) in the GitHub community page.



<a name="loio4e2f2b506c2d4ea49f808fee70bc2fe6__section_drm_2w2_31c"/>

## Updates

-   **SapMachine** – as of [v4.55](https://github.com/cloudfoundry/java-buildpack/releases/tag/v4.55) of the `java-buildpack`, SAP provides SapMachine 11 and 17 instead of OpenJDK 11 and 17 in the offline **`java_buildpack`**.

    See SAP Note: [3261748](https://me.sap.com/notes/3261748) *SapMachine is replacing OpenJDK 11 & 17 in java\_buildpack*


