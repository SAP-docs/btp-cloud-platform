<!-- loio6c6936e8e4ea40c9a9a69f6783b1e978 -->

# Bill of Materials \(BOM\)

For Maven projects, the versions of the SAP Java Buildpack dependencies and the APIs provided by supported runtime containers can be consumed through a Bill Of Materials \(BOM\).



The BOM contains the dependencies you can rely on in a runtime environment provided by the SAP Java Buildpack. It can also be used to control the versions of a project's dependencies without the need to manually maintain the version of each single artifact.

SAP Java Buildpack BOMs are provided through [Maven Central](https://search.maven.org/search?q=com.sap.cloud.sjb.cf).



<a name="loio6c6936e8e4ea40c9a9a69f6783b1e978__section_zv5_4cj_v3b"/>

## Usage

There are three runtimes for which a BOM is provided: Tomcat, TomEE and TomEE 7. The versions of the BOMs must match the version of the `sap_java_buildpack` you're using. For example, if your application uses `sap_java_buildpack` version 1.28.1, the BOM must be in version 1.28.1 as well.

If you want to use version control, add the desired BOM artifact to your project's `pom.xml` in the section *dependencyManagement*. The following code is just an example.

-   For Tomcat:

    ```
    ...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.sap.cloud.sjb.cf</groupId>
                <artifactId>cf-tomcat-bom</artifactId>
                <version>1.28.1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    ...
    ```

-   For TomEE:

    ```
    ...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.sap.cloud.sjb.cf</groupId>
                <artifactId>cf-tomee-bom</artifactId>
                <version>1.28.1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    ...
    ```

-   For TomEE 7:

    ```
    ...
    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>com.sap.cloud.sjb.cf</groupId>
                <artifactId>cf-tomee7-bom</artifactId>
                <version>1.28.1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>
    ...
    ```


To add the dependencies that you want, use *groupId* and *artifactId*:

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

If you simply want to have all dependencies in your project, you can also add the BOM to your project's section. Doing so removes the need to enumerate single dependency artifacts.

