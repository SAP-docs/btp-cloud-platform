<!-- loio8a1786acd70445768b35e50f3038a2a9 -->

# Java Main

You can create a Java application that starts its own runtime. This allows the usage of frameworks and Java runtimes, such as Spring Boot, Jetty, Undertow, or Netty.



<a name="loio8a1786acd70445768b35e50f3038a2a9__prereq_vsk_wdv_42b"/>

## Prerequisites

-   You are not using the [Resource Configuration](resource-configuration-c893e9c.md) feature of the buildpack.

> ### Note:  
> The resource configurations needed for the database connection are not applicable for Java Main applications. For more information about database connections, see: [Configuring a Database Connection](configuring-a-database-connection-7568c3d.md)



## Context

In this section, applications like this are referred as *Java Main applications*. The application container provided by the SAP Java Buildpack for running Java Main applications is referred as *Java Main container*.



## Procedure

1.  Make sure your built JAR archive is configured properly.

    Regardless of the tool you use to build your Java application, you have to make sure that the following tasks are performed:

    1.  You have built a JAR archive.

    2.  You have specified a main class in the `META-INF/MANIFEST.MF` file of the JAR archive.

        > ### Sample Code:  
        > Manifest.MF
        > 
        > ```
        > Manifest-Version: 1.0
        > Archiver-Version: Plexus Archiver
        > Built-By: p123456
        > Created-By: Apache Maven 3.3.3
        > Build-Jdk: 1.8.0_45
        > Main-Class: com.companya.xs.java.main.Controller  
        > ```

    3.  You have packaged all your dependent libraries in the JAR file, also known as creating an [uber JAR](https://maven.apache.org/plugins/maven-shade-plugin/examples/includes-excludes.html) or a *flat JAR*.


    If you are using Maven as your build tool, you can use the `maven-shade-plugin` to perform the above tasks.

    > ### Sample Code:  
    > Sample configuration for the `maven-shade-plugin`
    > 
    > ```
    > <build>
    > <finalName>java-main-sample</finalName>
    > <plugins>
    >   <plugin>
    >     <groupId>org.apache.maven.plugins</groupId>
    >     <artifactId>maven-shade-plugin</artifactId>
    >     <version>2.4.3</version>
    >     <configuration>
    >       <createDependencyReducedPom>false</createDependencyReducedPom>
    >       <filters>
    >         <filter>
    >           <artifact>*:*</artifact>
    >           <excludes>
    >             <exclude>META-INF/*.SF</exclude>
    >             <exclude>META-INF/*.DSA</exclude>
    >             <exclude>META-INF/*.RSA</exclude>
    >           </excludes>
    >         </filter>
    >       </filters>
    >     </configuration>
    >     <executions>
    >       <execution>
    >         <phase>package</phase>
    >         <goals>
    >           <goal>shade</goal>
    >         </goals>
    >         <configuration>
    >           <transformers>
    >             <transformer implementation="org.apache.maven.plugins.shade.resource.ServicesResourceTransformer" />
    >             <transformer implementation="org.apache.maven.plugins.shade.resource.ManifestResourceTransformer">
    >               <manifestEntries>
    >                 <Main-Class>com.sap.xs.java.main.Controller</Main-Class>
    >               </manifestEntries>
    >             </transformer>
    >           </transformers>
    >         </configuration>
    >       </execution>
    >     </executions>
    >   </plugin>
    > </plugins>
    > </build>
    > ```

2.  Configure the `manifest.yml`.

    To be able to push the Java Main application, you need to specify the path to the `.jar` archive in the `manifest.yml` file.

    > ### Sample Code:  
    > manifest.yml
    > 
    > ```
    > ---
    > applications:
    > - name: java-main
    >   memory: 128M
    >   path: ./target/java-main-sample.jar
    >   instances: 1
    > ```

3.  \(Optional\) If you use SAP HANA JDBC, we recommend that you include the dependent JAR files in the uber JAR. Then refer these files, as a space separated list, in the `Class-Path` header field of the MANIFEST.MF file. For example:

    > ### Sample Code:  
    > ```
    > Class-Path: jar1-name jar2-name directory-name/jar3-name
    > ```

4.  Deploy the application on Cloud Foundry. Execute:

    ```
    cf push
    ```




Let's say, you want to create a Java Main application to use its own runtime. For that purpose, performs the following steps:

1.  Create a *sample\_main* application. Use Spring Boot for that purpose.

2.  Navigate to the `sample_main` directory of the application, using the command line tool, and build it. To do that, execute:

    ```
    mvn clean install
    ```

3.  After the successful build, check that the `sample_main` directory of the application contain a **sample\_main.jar** file.

4.  Open the **sample\_main.jar** file and check that the `META-INF/MANIFEST.MF` file contains the `Main-Class` header, whose value is the name of the main class.

5.  Add the path to the JAR file in the `manifest.yml` file.

    You need to do this to make sure that the application can be pushed to the Cloud Foundry environment. For that purpose, add the following line in the `manifest.yml` file:

    ```
    path: ./target/sample_main.jar
    ```

6.  Finally, deploy the Java Main application. Execute:

    ```
    cf push sample_main
    ```


