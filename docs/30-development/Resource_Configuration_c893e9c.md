<!-- loioc893e9c7d05e4cca8151a5c3d87ec6ce -->

# Resource Configuration

Both application containers [Tomcat](Application_Containers_83d2416.md#loioddfc10180fe844049cc71f6989942dc2) and [TomEE](Application_Containers_83d2416.md#loioa9590c2f5ebc4d1586d9f0f53a60cfdc) are configured through text configuration files, examples are the`conf/server.xml`, `conf/tome.xml` or `conf/logging.properties` \([Apache Tomcat 8 Configuration Reference](https://tomcat.apache.org/tomcat-8.0-doc/config/)\). Resource configuration feature of the SAP Java buildpack provides means for changing parameterized values in all text files part of the application container or part of the application files during staging.

Files can contain multiple key value pairs containing placeholders \(makred as `${propname}`\). In order to prevent undesired modifications all files that could be changed must be explicitly listed by the application in a corresponding`resource_configuration.yml` file along with default values for all placeholders.

Example `resource_configuration.yml`:

```
---
filepath:
  key1: value1
  key2: value2
filepath2:
  key1: value1
```

The filepath must start with either `tomcat` or `tomee` to match the used application container and then contain a subpath to a resource.

When changing parametrized values inside application files the file path should look like: `<application_container>/webapps/ROOT/<path_to_file_relative_to_the_root_of_the_application>`

When changing parametrized values inside application container's configuration the file path should look like: `<application_container>/conf/<path_to_config_file>`

Example:

```
tomcat/webapps/ROOT/WEB-INF/mytextfile.txt:
  placeholder: "defaultValue"
tomcat/conf/server.xml
  connector.maxThreads: 800
```

Example:

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

Where the content of `mytextfile.txt` is:

```
My hometown is ${hometown}.
```

The `resource_configuration.yml` looks like:

```
---
tomcat/webapps/ROOT/WEB-INF/mytextfile.txt:
  hometown: "London"
```

After the application is staged the content of `mytextfile.txt` will be

```
My hometown is London.
```

The example below demonstrates how to provide values for placeholders during staging: Given the example above add the following environment variable in the `manifest.yml` file of the application:

```
env:
  JBP_CONFIG_RESOURCE_CONFIGURATION: "['tomcat/webapps/ROOT/WEB-INF/mytextfile.txt': {'hometown':"Paris"}]"
```

This gives the possibility to provide values for placeholders that differ from the provided in the example above defaults. Staging the application with this environment variable will modify the content of `mytextfile.txt` to:

```
My hometown is Paris.
```

