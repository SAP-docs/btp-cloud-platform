<!-- loio2255375136f645cb96c26fb3d0105d5c -->

# Java Options

You can configure the Java properties by defining the JBP\_CONFIG\_JAVA\_OPTS environment variable.

Defining the JBP\_CONFIG\_JAVA\_OPTS environment variable in the `manifest.yml` file of the application.

> ### Sample Code:  
> manifest.yml
> 
> ```
> ---
> applications:
> - name: <app-name>
>   memory: 512M
> ...
>   env:
>      JBP_CONFIG_JAVA_OPTS: 'java_opts: ''-DtestJBPConfig=^%PATH^% -DtestJBPConfig1="test test" -DtestJBPConfig2="%PATH%"'''
> ```

Defining the JBP\_CONFIG\_JAVA\_OPTS environment variable by using the `cf set-env` command of the Cloud Foundry Command Line Interface \(cf CLI\).

```
cf set-env myapp JBP_CONFIG_JAVA_OPTS "[java_opts: '-DtestJBPConfig=^%PATH^% -DtestJBPConfig1=\"test test\" -DtestJBPConfig2=\"^%PATH^%\"']"
```



<a name="loio2255375136f645cb96c26fb3d0105d5c__section_ed4_jrv_42b"/>

## Escaping Strings



### When defining the JBP\_CONFIG\_JAVA\_OPTS in the manifest.yml file

A single quote ['\] is used to enclose the JBP\_CONFIG\_JAVA\_OPTS environment variable in the manifest.yml file. Strings containing the following characters must be quoted: [:\], [\{\], [\}\], [\[\], [\]\], [,\], [&\], [\*\], [\#\], [?\], [|\], [\-\], [<\], [\>\], [=\], [!\], [%\], [@\], [\\\].

When a single quote ['\] is used, other single quotes ['\] in the string must be escaped by doubling it [''\].



### When defining the JBP\_CONFIG\_JAVA\_OPTS by using the `cf set-env` command

The string must be enclosed in the double quotes ["\]. If there are other double quotes in the string, you have escape them using the backslash [\\\].



### When defining java options with values containing spaces

In case you need to specify a option value, which has blank spaces in it, you need to surround it with quotes ["\]. If the value contains special characters like for example [$\], you have to escape them using the escape character specific for the operating system shell where the application is pushed. In the example below the [$\] in the $PATH string is escaped using the [\\\] escape character for Linux. Otherwise, if the [$\] sign is not escaped, the value of the variable PATH is substituted in the property value.

> ### Sample Code:  
> manifest.yml
> 
> ```
>  ---
>  applications:
>  - name: <app-name>
>    memory: 512M
> ...
>    env:
>      JBP_CONFIG_JAVA_OPTS: 'java_opts: ''-DtestJBPConfig=\$PATH -DtestJBPConfig1="test test" -DtestJBPConfig2="$PATH"'''
> ```

