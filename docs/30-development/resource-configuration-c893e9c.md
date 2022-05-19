<!-- loioc893e9c7d05e4cca8151a5c3d87ec6ce -->

# Resource Configuration

Both application containers [Tomcat](tomcat-ddfc101.md) and [TomEE](tomee-a9590c2.md) are configured through text configuration files. For example – `conf/server.xml`, `conf/tomee.xml` or `conf/logging.properties` \(see [Apache Tomcat 8 Configuration Reference](https://tomcat.apache.org/tomcat-8.0-doc/config/)\). Resource configuration feature of the SAP Java Buildpack provides means for changing parameterized values in all text files part of the application container or part of the application files during staging.

Files can contain multiple key value pairs containing placeholders \(marked as `${propname}`\). To prevent undesired modifications, all files that could be changed must be explicitly listed by the application in a corresponding `resource_configuration.yml` file along with the default values for all placeholders.

**Example** for `resource_configuration.yml`:

```
---
filepath:
  key1: value1
  key2: value2
filepath2:
  key1: value1
```

The `filepath` must start with either **tomcat** or **tomee** to match the used application container, and then contain a subpath to a resource.

-   When changing parametrized values inside application files, the file path should look like this:

    `<application_container>/webapps/ROOT/<path_to_file_relative_to_the_application_root>`

-   When changing parametrized values inside the configuration of an application container, the file path should look like this:

    `<application_container>/conf/<path_to_config_file>`


**Example 1**

```
tomcat/webapps/ROOT/WEB-INF/mytextfile.txt:
  placeholder: "defaultValue"
tomcat/conf/server.xml
  connector.maxThreads: 800
```

**Example 2** 

Given an application with the following application files:

```

src/
	main/
		java/
		resources/
		webapp/
			META-INF/
				sap_java_buildpack/
					config/
						resource_configuration.yml
			WEB-INF/
				mytextfile.txt

```

where the content of `mytextfile.txt` is:

```
My hometown is ${hometown}.
```

The `resource_configuration.yml` looks like:

```
---
tomcat/webapps/ROOT/WEB-INF/mytextfile.txt:
  hometown: "London"
```

After the application is staged, the content of `mytextfile.txt` will be:

```
My hometown is London.
```

**Example 3**

The follow example demonstrates how to provide values for placeholders during staging.

Given the example above, add the following environment variable in the `manifest.yml` file of the application:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/WEB-INF/mytextfile.txt': {'hometown':"Paris"}]"
```

This gives the possibility to provide values for placeholders that differ from the default ones provided in the example above. Staging the application with this environment variable will modify the content of `mytextfile.txt` to:

```
My hometown is Paris.
```

