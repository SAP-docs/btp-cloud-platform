<!-- loio156fa7509e76454db330e8e874d7acb7 -->

# Using an Agent

SAP Java Buildpack can work with any Java agent as long as it's included in the `.jar` or `.war` archive of your application.

The buildpack extracts the agent when the application is deployed. To check if the agent is extracted to the expected location, run:

```
cf ssh
```

To use an agent with SAP Java Buildpack, set the *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable as follows:

```
env:
    JBP_CONFIG_JAVA_OPTS: 'java_opts: "-javaagent:<PathToYourAgent>"'
```

The Java agent is platform-agnostic, but must be compatible with the version of the JVM you are using \(SAP JVM or SapMachine\).



<a name="loio156fa7509e76454db330e8e874d7acb7__section_gg5_jfg_hcc"/>

## Native Agents

A native agent is a dynamic library. If you want to use one, it must be compatible with the architecture of the platform. For Cloud Foundry, this is Linux x86\_64. As an application developer, make sure that the correct agent is used, and regularly apply updates whenever they're needed.

To use a native agent, set the *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable as follows:

```
 env:
    JBP_CONFIG_JAVA_OPTS: 'java_opts: "-agentpath:<PathToYourAgent>"'
```

