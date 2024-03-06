<!-- loio83d241613dcd41c99ccc308ed0d26399 -->

# Runtimes and Containers

Find out which application runtimes and containers you can use, depending on the Java buildpack your application is using.



-   [TomEE 7](tomee-7-79c039a.md) – use this runtime only with SAP Java Buildpack 1

-   [Tomcat 9](tomcat-9-ddfc101.md) – use this runtime only with SAP Java Buildpack 1

-   [Tomcat 10](tomcat-10-97d0e34.md) – use this runtime only with SAP Java Buildpack 2

-   [Java Main](java-main-8a1786a.md) – use the Java Main container with all Java buildpacks


> ### Restriction:  
> Currently, SAP Java Buildpack 2 does not support Apache TomEE. For this reason, we've temporarily forbidden deploying Java applications running on TomEE. That means, if you set **tomee** as a target runtime, your application will fail during the *staging* phase of the `cf push` command execution.
> 
> This restriction will be revoked when we provide a compatible Apache TomEE version for SAP Java Buildpack 2.

**Related Information**  


[Buildpacks](buildpacks-5e7fc02.md "")

