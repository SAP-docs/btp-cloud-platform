<!-- loioc107eb83ffd94bb49098659b5e3d4911 -->

# Application-Provided Library Components

SAP Java Buildpack can automatically provide JDBC drivers for SAP HANA and PostgreSQL in the classpath if the respective service instance is bound.

The application can also provide its own version of these drivers in the relevant directory:

-   `WEB-INF/lib` – for standard Java applications. It's loaded for all Java buildpacks
-   `BOOT-INF/lib` – for Spring Boot applications. It's only loaded for SAP Java Buildpack 2.

In this case, the application-provided version of the driver will be set in the classpath, not the one that comes with SAP Java Buildpack.

> ### Caution:  
> -   When using this mechanism, the application developer is responsible to keep the JDBC drivers up-to-date.
> -   Also, note that SAP Java Buildpack will move the JDBC driver from its original location \(`WEB-INF/lib` or `BOOT-INF/lib`\) to **`META-INF/.sap_java_buildpack/hana_jdbc`** or **`META-INF/.sap_java_buildpack/postgresql_jdbc`**, respectively. If you want to keep the driver in its original location, you have to set environment variable JBP\_SKIP\_PROVIDED\_LIBRARY\_COMPONENTS. To learn how to do this, see the section below.

The drivers have to follow the respective file name pattern:

-   **ngdbc\*.jar** – for SAP HANA Driver
-   **postgresql\*.jar** – for PostgreSQL JDBC Driver



<a name="loioc107eb83ffd94bb49098659b5e3d4911__section_jcs_r1k_pfc"/>

## JBP\_SKIP\_PROVIDED\_LIBRARY\_COMPONENTS

If you use the environment variable `JBP_SKIP_PROVIDED_LIBRARY_COMPONENTS` and set it to **true**, SAP Java Buildpack will keep the library components in their original location \(**`WEB-INF/lib`** or **`BOOT-INF/lib`**\).

This way, the new location \(`META-INF/.sap_java_buildpack/hana_jdbc` or `META-INF/.sap_java_buildpack/postgresql_jdbc`\) will not be created by the buildpack, nor added to the classpath.



<a name="loioc107eb83ffd94bb49098659b5e3d4911__section_d3t_k4g_hcc"/>

## Auxiliary Library Components

The application developer can provide additional components alongside the aforementioned libraries. For example, this can be a custom SSL factory for the PostgreSQL JDBC Driver, which has to be accessible to the class loader that loads the actual library.

To do so, the additional libraries have to be placed in a JAR file in the **`WEB-INF/lib`** or **`BOOT-INF/lib`** directory. The JAR file has to follow the respective file name pattern:

-   **sjb-ngdbc-aux\*.jar** – for SAP HANA Driver
-   **sjb-postgresql-aux\*.jar** – for PostgreSQL JDBC Driver

Any number of files following these patterns can be placed in the **`WEB-INF/lib`** or **`BOOT-INF/lib`** directory and will be handled by SAP Java Buildpack.

> ### Tip:  
> This mechanism works with both application-provided and buildpack-provided libraries.

