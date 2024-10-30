<!-- loioc107eb83ffd94bb49098659b5e3d4911 -->

# Application-Provided Library Components

SAP Java Buildpack can automatically provide JDBC drivers for SAP HANA and PostgreSQL in the classpath if the respective service instance is bound.

The application can also provide an own version of these drivers in the `WEB-INF/lib` directory. In this case, SAP Java Buildpack will not download the current version of the driver but place the application-provided version in the classpath. The drivers have to follow the respective file name pattern:

-   **ngdbc\*.jar**
-   **postgresql\*.jar**

> ### Note:  
> When using this mechanism, the application developer is responsible to keep the drivers up-to-date.



<a name="loioc107eb83ffd94bb49098659b5e3d4911__section_d3t_k4g_hcc"/>

## Auxiliary Library Components

The application developer can provide additional components alongside the aforementioned libraries. For example, this can be a custom SSL factory for the PostgreSQL JDBC Driver, which has to be accessible to the class loader that loads the actual library.

To do so, the additional libraries have to be placed in a JAR file in the `WEB-INF/lib` directory. The JAR file has to follow the respective file name pattern:

-   **sjb-ngdbc-aux\*.jar**
-   **sjb-postgresql-aux\*.jar**

Any number of files following these patterns can be placed in the `WEB-INF/lib` directory and will be handled by SAP Java Buildpack.

This mechanism works with both application-provided and buildpack-provided libraries.

