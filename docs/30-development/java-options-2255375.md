<!-- loio2255375136f645cb96c26fb3d0105d5c -->

# Java Options

You can configure the Java properties by defining the JBP\_CONFIG\_JAVA\_OPTS environment variable.



You can define JBP\_CONFIG\_JAVA\_OPTS in two ways:

-   In the `manifest.yml` file of the application:

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
    >      JBP_CONFIG_JAVA_OPTS: 'java_opts: -DtestJBPConfig=\$PATH -DtestJBPConfig1=''test test'' -DtestJBPConfig2="$PATH"'
    > ```

-   Using the `cf set-env` command in the Cloud Foundry Command Line Interface \(cf CLI\):

    ```
    cf set-env myapp JBP_CONFIG_JAVA_OPTS "[java_opts: '-DtestJBPConfig=^%PATH^% -DtestJBPConfig1=''test test'' -DtestJBPConfig2="\$PATH"']"
    ```




<a name="loio2255375136f645cb96c26fb3d0105d5c__section_ed4_jrv_42b"/>

## Escape Strings when Defining JBP\_CONFIG\_JAVA\_OPTS



### In the `manifest.yml` File

A single quote ['\] is used to enclose the JBP\_CONFIG\_JAVA\_OPTS environment variable in the manifest.yml file. Strings containing the following characters must be quoted: [:\], [\{\], [\}\], [\[\], [\]\], [,\], [&\], [\*\], [\#\], [?\], [|\], [\-\], [<\], [\>\], [=\], [!\], [%\], [@\], [\\\]. When a single quote ['\] is used, other single quotes ['\] in the string must be escaped by doubling it [''\].



### Using the `cf set-env` Command

The string must be enclosed in the double quotes ["\]. If there are other double quotes in the string, you have escape them using the backslash [\\\].



### Using Values Containing Spaces

In case you need to specify an option value that has blank spaces in it, you need to surround it with two single quotes [''\]. If the value contains special characters, for example [$\], you have to escape them by using the escape character specific for the operating system shell where the application is pushed. In the example below, the [$\] in the $PATH string is escaped by using the [\\\] escape character for Linux:

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
>      JBP_CONFIG_JAVA_OPTS: 'java_opts: -DtestJBPConfig=\$PATH -DtestJBPConfig1=''test test'' -DtestJBPConfig2="$PATH"'
> ```

**NOTE:** If the [$\] sign is not escaped, the value of the PATH variable is substituted in the property value.

