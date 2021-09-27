<!-- loio0a345880fa6f4aa8b7c481ea5677d690 -->

# Overriding Resources in Droplet

Applications can override resources in the droplet by placing files in `META-INF/sap_java_buildpack/resources/`. These files override files inside the droplet that have the same relative path to the droplet root.

The following example shows how application could override the default Tomcat's `server.xml`. Having the following structure in the application files:

```
META-INF/
- sap_java_buildpack/
  - resources/
    - tomcat/
      - conf/
        - server.xml/
WEB-INF/
```

will result in the following file structure in the droplet:

```
META-INF/
- .sap_java_buildpack/
  - tomcat
    - conf/
      - server.xml
WEB-INF/
```

Meaning that when the Tomcat container is started the `server.xml` file used will be the one comming from the application.

This mechanism also allows of adding new resources inside of the droplet on their respective places based on where the files are located under `META-INF/sap_java_buildpack/resources/`.

