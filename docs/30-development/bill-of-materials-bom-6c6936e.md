<!-- loio6c6936e8e4ea40c9a9a69f6783b1e978 -->

# Bill of Materials \(BOM\)

For Maven projects, the versions of SAP Java Buildpack dependencies and the APIs provided by supported runtime containers can be consumed through a Bill of Materials \(BOM\).



The BOM contains the dependencies you can rely on in a runtime environment provided by SAP Java Buildpack. It can also be used to control the versions of a project's dependencies without the need to manually maintain the version of each single artifact.

The BOMs of SAP Java Buildpack are provided through [Maven Central](https://central.sonatype.com/search?q=com.sap.cloud.sjb.cf).



<a name="loio6c6936e8e4ea40c9a9a69f6783b1e978__section_zv5_4cj_v3b"/>

## Usage

There are two runtimes for which a BOM is provided: Tomcat and TomEE.

The version of the BOM must match the version of the `sap_java_buildpack` or `sap_java_buildpack_jakarta` you're using. For example, if your application uses **`sap_java_buildpack_jakarta`** version 2.24.0, the BOM must be in version 2.24.0 as well.

If you want to use version control, add the desired BOM artifact to your project's `pom.xml` file in the section **`dependencyManagement`**. The following codes are exemplary.

-   For Tomcat 10:

    ```
    
    ...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.sap.cloud.sjb.cf</groupId>
                <artifactId>cf-tomcat-bom</artifactId>
                <version>2.24.0</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    ...
    ```

-   For TomEE 10:

    ```
    ...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.sap.cloud.sjb.cf</groupId>
                <artifactId>cf-tomee-bom</artifactId>
                <version>2.24.0</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    ...
    ```


To add the dependencies you want, use *groupId* and *artifactId*:

```
...
<dependency>
    <groupId>com.sap.cloud.sjb</groupId>
    <artifactId>xs-env</artifactId>
</dependency>
<dependency>
    <groupId>com.sap.cloud.sjb</groupId>
    <artifactId>xs-user-holder</artifactId>
</dependency>
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-annotations</artifactId>
</dependency>
<dependency>
    <groupId>org.slf4j</groupId>
    <artifactId>jul-to-slf4j</artifactId>
</dependency>
<dependency>
    <groupId>ch.qos.logback</groupId>
    <artifactId>logback-access</artifactId>
</dependency>
...
```

If you want to have all dependencies in your project, you can add the BOM to your project's section as well. By doing so, you don't need to enumerate single dependency artifacts.

**Related Information**  


[Maven Repository: SAP Java Buildpack BOM](https://mvnrepository.com/artifact/com.sap.cloud.sjb.cf/sap-java-buildpack-bom)

