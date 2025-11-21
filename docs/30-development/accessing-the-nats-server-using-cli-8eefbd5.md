<!-- loio8eefbd54171c492b89ffe855344a04ef -->

# Accessing the NATS Server Using CLI

Interact directly with your NATS server deployment in Kyma using the NATS command-line interface \(CLI\). Use the CLI to inspect server status, manage streams and consumers, and troubleshoot message flow.



<a name="loio8eefbd54171c492b89ffe855344a04ef__prereq_d52_gvs_dhc"/>

## Prerequisites

-   You have installed kubectl and [NATS CLI](https://github.com/nats-io/natscli).



## Context

Accessing certain resources in NATS requires [system account privileges](https://docs.nats.io/running-a-nats-service/configuration/sys_accounts). Kyma automatically generates a `system account` user using a Secret named `eventing-nats-secret` in the `kyma-system` namespace.



## Procedure

1.  Get the credentials. Run:

    ```
    kubectl get secrets -n kyma-system eventing-nats-secret -ogo-template='{{index .data "resolver.conf"|base64decode}}'| grep 'user:'| tr -d '{}'
    ```

    If you changed the default NATS instance name from `eventing-nats`, replace `eventing-nats-secret` with `{your_NATS_CR_name}-secret`.

    You receive the credentials for the `system account` user in the following format:

    ```
    user: admin, password: <your password>
    ```

2.  To access the NATS server with the NATS CLI tool, forward its port:

    ```
    kubectl port-forward -n kyma-system svc/eventing-nats 4222
    ```

3.  To send your NATS commands, pass the credentials:

    ```
    nats server info --user admin --password <your password>
    ```


