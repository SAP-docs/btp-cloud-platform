<!-- loio8a1786acd70445768b35e50f3038a2a9 -->

# Java Main

You can create a Java application that starts its own run time. This allows the usage of frameworks and java runtimes, such as Spring Boot, Jetty, Undertow, or Netty.



<a name="loio8a1786acd70445768b35e50f3038a2a9__prereq_vsk_wdv_42b"/>

## Prerequisites

-   You are not using the [Resource Configuration](resource-configuration-c893e9c.md) feature of the buildpack.

> ### Note:  
> The resource configurations needed for the database connection are not applicable for the Java Main applications. For more information about database connections, see Related Information.



## Context

In this section such applications will be referred to as Java Main applications. The application container provided by the SAP Java Buildpack for running Java Main applications is referred as Java Main container.



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

    3.  You have packaged all your dependent libraries in the JAR file, also known as creating an uber JAR or a fat JAR.


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

3.  Push the application to Cloud Foundry.

    For the purpose use `cf push` command.




Donna Moore would like to create a Java Main application to use its own run time. For that purpose she performs the following steps:

1.  Creates a *sample\_main* application. Using Spring Boot for that purpose.

2.  Navigates to the `sample_main` directory of the application, using the command line tool, and builds it. She can perform this operation with the command `mvn clean install`.

3.  After the build is successful, she checks that the `sample_main` directory of the application, contains a sample\_main.jar file.

4.  She opens the sample\_main.jar file and checks that the `META-INF/MANIFEST.MF` file contains the Main-Class header with value, the name of the main class.

5.  She adds the path to the JAR file in the `manifest.yml` file.

    She needs to do that to make sure that the application can be pushed to the Cloud Foundry Environment. For that purpose, she adds the following line in the `manifest.yml` file:

    ```
    path: ./target/sample_main.jar
    ```

6.  Finally, she pushes the Java Main application with the following command:

    ```
    cf push sample_main
    ```


**Related Information**  


[Configuring a Database Connection](configuring-a-database-connection-7568c3d.md)

