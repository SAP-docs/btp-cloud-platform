<!-- loio156fa7509e76454db330e8e874d7acb7 -->

# Using an Agent

You can use any agent with the SAP Java Build pack. The agent must be included in the `.jar` or `.war` archive of your application. The SAP Java Build pack extracts the agent when the application is deployed. You can check if the agent is extracted to the expected location by using the `cf ssh` command.

To use an agent with the SAP Java Build pack, set the *<JBP\_CONFIG\_JAVA\_OPTS\>* environment variable as shown in the following example:

```
env:
    JBP_CONFIG_JAVA_OPTS: 'java_opts: "-javaagent:<PathToYourAgent>"'
```

The Java agent is platform-agnostic, but must be compatible to the version of the JVM you are using.

You can also use a native agent. Since a native agent is a dynamic library, it must be compatible with the architecture of the platform. For Cloud Foundry, this is Linux x86\_64. As the application developer you must make sure that the correct agent is used and apply updates whenever they are needed. To use a native agent, set the *<JBP\_CONFIG\_JAVA\_OPTS\>* as follows:

```
 env:
    JBP_CONFIG_JAVA_OPTS: 'java_opts: "-agentpath:<PathToYourAgent>"'
```

