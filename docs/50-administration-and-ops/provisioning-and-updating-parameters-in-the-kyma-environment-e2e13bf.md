<!-- loioe2e13bfaa2f54a4fb179f0f1f840353a -->

# Provisioning and Updating Parameters in the Kyma Environment

You can configure the cluster parameters in the Kyma environment.



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_qzp_1wv_yzb"/>

## Overview

To configure the cluster parameters, you can use your preferred interface, the SAP BTP cockpit or the SAP BTP command line interface.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

These are the configurable cluster parameters:

-   [Administrators](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators)
-   [Auto Scaler Max](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max)
-   [Auto Scaler Min](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min)
-   [Cluster Name\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name)
-   [Machine Type](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type)
-   [Modules](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules)
-   [Networking](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking)
-   [OpenID Connect \(OIDC\)](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC)
-   [Region\*](provisioning-and-updating-parameters-in-the-kyma-environment-e2e13bf.md#loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region)

To see which parameters are available for configuration in a particular plan, go to [Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md).



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Administrators"/>

## Administrators

The *Administrators* \(`administrators`\) parameter is an array of strings. It is a provisioning and updating parameter, which specifies the list of runtime administrators. Complete the list with the administrators' email addresses as shown in this example:

```
"administrators": [
        "example_1@mail.com",
        "example_2@mail.com",
        "example_3@mail.com"
    ]

```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Max"/>

## Auto Scaler Max

The *Auto Scaler Max* \(`autoScalerMax`\) is an integer parameter, which specifies the maximum number of virtual machines you can create.

**Auto Scaler Max Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Maximum Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

Standard: Amazon Web Services \(technical name: `aws`\)

Standard: Google Cloud \(technical name: `gcp`\)

Standard: Microsoft Azure \(technical name: `azure`\)

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

20

</td>
<td valign="top">

300

</td>
<td valign="top">

Number between 3 and 300, but greater than or equal to *Auto Scaler Min*.

</td>
</tr>
<tr>
<td valign="top">

Kyma Test Demo and Development \(Azure Lite\)

\(technical name: `azure_lite`\)

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

10

</td>
<td valign="top">

40

</td>
<td valign="top">

Number between 2 and 40, but greater than or equal to *Auto Scaler Min*.

</td>
</tr>
</table>

The default JSON input is:

```
"autoScalerMax": 20
```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Auto_Scaler_Min"/>

## Auto Scaler Min

The *Auto Scaler Min* \(`autoScalerMin`\) is an integer parameter, which specifies the minimum number of virtual machines you can create.

**Auto Scaler Min Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Minimum Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

Standard: Amazon Web Services \(technical name: `aws`\)

Standard: Google Cloud \(technical name: `gcp`\)

Standard: Microsoft Azure \(technical name: `azure`\)

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

3

</td>
<td valign="top">

3

</td>
<td valign="top">

Number between 3 and the current value set in *Auto Scaler Max*.

</td>
</tr>
<tr>
<td valign="top">

Kyma Test Demo and Development \(Azure Lite\)

\(technical name: `azure_lite`\)

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

2

</td>
<td valign="top">

2

</td>
<td valign="top">

Number between 2 and the current value set in *Auto Scaler Max*.

</td>
</tr>
</table>

Here is an example of the JSON input:

```
"autoScalerMin": 3
```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Cluster_Name"/>

## Cluster Name\*

The *Cluster Name* \(`name`\) is a string, which provides the name of your cluster.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Cluster Name Parameter**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Cluster Name\**

btp CLI parameter: `name`

type: string

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

Automatically generated as your Subaccount’s Subdomain.

</td>
<td valign="top">

Short string \(up to 32 characters\) that contains only alphanumeric characters \(A-Z, a-z, 0–9\), periods, underscores, and hyphens. It can't contain white spaces.

</td>
</tr>
</table>



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Machine_Type"/>

## Machine Type

The *Machine Type* \(`machineType`\) parameter is a string, which specifies the provider-specific virtual machine type.

**Machine Type Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
<th valign="top">

Virtual Machine Size

</th>
</tr>
<tr>
<td valign="top" rowspan="14">

Standard: Amazon Web Services

technical name: `aws`

</td>
<td valign="top" rowspan="14">

Provisioning

Updating

</td>
<td valign="top" rowspan="14">

`m6i.large`

</td>
<td valign="top">

`m6i.large`

</td>
<td valign="top">

2vCPU, 8GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.xlarge`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.2xlarge`

</td>
<td valign="top">

8vCPU, 32GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.4xlarge`

</td>
<td valign="top">

16vCPU, 64GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.8xlarge`

</td>
<td valign="top">

32vCPU, 128GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.12xlarge`

</td>
<td valign="top">

48vCPU, 192GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m6i.16xlarge`

</td>
<td valign="top">

64vCPU, 256GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.large`

</td>
<td valign="top">

2vCPU, 8GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.xlarge`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.2xlarge`

</td>
<td valign="top">

8vCPU, 32GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.4xlarge`

</td>
<td valign="top">

16vCPU, 64GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.8xlarge`

</td>
<td valign="top">

32vCPU, 128GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.12xlarge`

</td>
<td valign="top">

48vCPU, 192GB RAM

</td>
</tr>
<tr>
<td valign="top">

`m5.16xlarge`

</td>
<td valign="top">

64vCPU, 256GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

Standard: Google Cloud

technical name: `gcp`

</td>
<td valign="top" rowspan="7">

Provisioning

Updating

</td>
<td valign="top" rowspan="7">

`n2-standard-2`

</td>
<td valign="top">

`n2-standard-2`

</td>
<td valign="top">

2vCPU, 8GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-4`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-8`

</td>
<td valign="top">

8vCPU, 32GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-16`

</td>
<td valign="top">

16vCPU, 64GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-32`

</td>
<td valign="top">

32vCPU, 128GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-48`

</td>
<td valign="top">

48vCPU, 192GB RAM

</td>
</tr>
<tr>
<td valign="top">

`n2-standard-64`

</td>
<td valign="top">

64vCPU, 256GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="13">

Standard: Microsoft Azure

technical name: `azure`

</td>
<td valign="top" rowspan="13">

Provisioning

Updating

</td>
<td valign="top" rowspan="13">

`Standard_D2s_v5`

</td>
<td valign="top">

`Standard_D2s_v5`

</td>
<td valign="top">

2vCPU, 8GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4s_v5`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8s_v5`

</td>
<td valign="top">

8vCPU, 32GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16s_v5`

</td>
<td valign="top">

16vCPU, 64GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32s_v5`

</td>
<td valign="top">

32vCPU, 128GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48s_v5`

</td>
<td valign="top">

48vCPU, 192GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64s_v5`

</td>
<td valign="top">

64vCPU, 256GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4_v3`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D8_v3`

</td>
<td valign="top">

8vCPU, 32GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D16_v3`

</td>
<td valign="top">

16vCPU, 64GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D32_v3`

</td>
<td valign="top">

32vCPU, 128GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D48_v3`

</td>
<td valign="top">

48vCPU, 192GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D64_v3`

</td>
<td valign="top">

64vCPU, 256GB RAM

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Kyma Test Demo and Development \(Azure Lite\)

technical name: `azure_lite`

</td>
<td valign="top" rowspan="2">

Provisioning

Updating

</td>
<td valign="top" rowspan="2">

`Standard_D4s_v5`

</td>
<td valign="top">

`Standard_D4s_v5`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
<tr>
<td valign="top">

`Standard_D4_v3`

</td>
<td valign="top">

4vCPU, 16GB RAM

</td>
</tr>
</table>

Here is an example of the input for the *Machine Type* parameter:

```
"machineType": "m5.xlarge"
```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Modules"/>

## Modules

With the *Modules* \(`modules`\) object, you can define which Kyma modules you want to provision in your cluster. You can also use it to create a cluster without any modules.

> ### Note:  
> API for module configuration is built on the `oneOf` feature from the JSON schema. If the `modules` object is passed to API, it must have only one valid option: *Default* \(`default`\) or *Custom* \(`list`\). Even if you remove the `modules` object from the JSON schema, the default Kyma modules are provisioned in your cluster.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Modules Parameters**


<table>
<tr>
<th valign="top" colspan="2">

Nested Parameter

</th>
<th valign="top" colspan="2">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
</tr>
<tr>
<td valign="top" colspan="2">

*Default*

btp CLI parameter: `default`

type: boolean

</td>
<td valign="top" colspan="2">

Defines whether to use the default list of Kyma modules. Check the [Default Kyma Modules](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-modules?locale=en-US&version=Cloud) to find out which modules are in the default modules list.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

`true`

</td>
</tr>
<tr>
<td valign="top" colspan="2">

*Custom*

btp CLI parameter: `list`

type: array of objects

</td>
<td valign="top" colspan="2">

Defines a custom list of Kyma modules.

Leave your custom list of Kyma modules empty if you don't want any modules provisioned.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

\[ \] \(empty array\)

</td>
</tr>
</table>

The *Custom* \(`list`\) parameter includes three nested parameters: *Name\**, *Channel*, and *Custom Resource Policy*.

**Custom list Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
</tr>
<tr>
<td valign="top">

*Name\**

btp CLI parameter: `name`

type: string

</td>
<td valign="top">

Look up the available Kyma modules and their technical names at [Kyma Modules](../10-concepts/kyma-modules-0dda141.md).

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Channel*

btp CLI parameter: `channel`

type: string

</td>
<td valign="top">

Defines the preferred release channel. The default is `regular`. The other option is `fast`.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

"" \(an empty string\)

</td>
</tr>
<tr>
<td valign="top">

*Custom Resource Policy*

btp CLI parameter: `customResourcePolicy`

type: string

</td>
<td valign="top">

Defines how a module's custom resource configuration is handled during enablement and reconciliation.

By default, it is set to `CreateAndDelete` and allows the creation or deletion of a module's resource.

If you set it to `Ignore`, a module's resource is not created.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

"" \(an empty string\)

</td>
</tr>
</table>

You have the default Kyma modules provisioned in your cluster if you do not provide the `modules` object in the JSON payload, or if you use the following input:

```
"modules": { 
    "default": true 
} 
```

Here is an example of JSON input for a custom list of Kyma modules:

```
"modules": {
    "list": [
        {
            "name": "btp-operator"
        },
        {
            "name": "keda",
            "customResourcePolicy": "CreateAndDelete",
            "channel": "fast"
        }
    ]
}
```

Applying the following values results in Kyma runtime provisioning without any Kyma modules.

```
"modules": {
    "list": []
}
```

```
"modules": {
    "default": false
}
```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Networking"/>

## Networking

The *Networking* \(`networking`\) object provides networking configuration. These values are immutable and cannot be updated later.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**Networking Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*CIDR range for Nodes\**

btp CLI parameter: `nodes`

type: string

</td>
<td valign="top">

Defines a custom IP range for worker nodes.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

10.250.0.0/16

</td>
<td valign="top">

CIDR range for nodes must not overlap with the following CIDRs: 10.96.0.0/13, 10.104.0.0/13, 10.243.128.0/17, 10.242.0.0/16, 10.243.0.0/17, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16

</td>
</tr>
<tr>
<td valign="top">

*CIDR range for Pods*

btp CLI parameter: `pods`

type: string

</td>
<td valign="top">

Defines a custom IP range for Pods.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

10.96.0.0/13

</td>
<td valign="top">

CIDR range for Pods must not overlap with the following CIDRs: 10.96.0.0/13, 10.104.0.0/13, 10.243.128.0/17, 10.242.0.0/16, 10.243.0.0/17, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16

</td>
</tr>
<tr>
<td valign="top">

*CIDR range for Services*

btp CLI parameter: `services`

type: string

</td>
<td valign="top">

Defines a custom IP range for Services.

</td>
<td valign="top">

Provisioning

</td>
<td valign="top">

10.104.0.0/13

</td>
<td valign="top">

CIDR range for Services must not overlap with the following CIDRs: 10.96.0.0/13, 10.104.0.0/13, 10.243.128.0/17, 10.242.0.0/16, 10.243.0.0/17, 10.64.0.0/11, 10.254.0.0/16, 10.243.0.0/16

</td>
</tr>
</table>

Here is the default JSON input for the *Networking* object:

```
"networking": {
        "nodes": "10.250.0.0/22"
        "pods": "10.96.0.0/13"
        "services": "10.104.0.0/13"
    }

```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_OIDC"/>

## OpenID Connect \(OIDC\)

The *OpenID Connect* \(`oidc`\) object allows you to provide OIDC configuration. If you do not provide the `oidc` object or any custom values in the provisioning request, the default OIDC configuration is used. If you do not provide the `oidc` object in the update request or leave all object’s properties empty, the saved OIDC configuration remains unchanged.

> ### Remember:  
> The parameters marked with an asterisk "\*" are mandatory.

**OIDC Parameters**


<table>
<tr>
<th valign="top">

Nested Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Default Value

</th>
<th valign="top">

Allowed Input

</th>
</tr>
<tr>
<td valign="top">

*Client ID\**

btp CLI parameter: `clientID`

type: string

</td>
<td valign="top">

The client ID for the OpenID Connect client.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Issuer URL\**

btp CLI parameter: issuerURL

type: string

</td>
<td valign="top">

Provides the URL of the OpenID issuer.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Groups Claim*

btp CLI parameter: `groupsClaim`

type: string

</td>
<td valign="top">

If provided, specifies the name of a custom OIDC claim for specifying user groups.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

`groups`

</td>
<td valign="top">

n/a

</td>
</tr>
<tr>
<td valign="top">

*Username Claim*

btp CLI parameter: `usernameClaim`

type: string

</td>
<td valign="top">

Provides the OpenID claim to use as the user name.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

n/a

</td>
<td valign="top">

Only HTTPS scheme is accepted.

</td>
</tr>
<tr>
<td valign="top">

*Signing Algs*

btp CLI parameter: `signingAlgs`

type: array

</td>
<td valign="top">

Provides the OIDC signing algorithms for Kyma runtime.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

`RS256`

</td>
<td valign="top">

Comma separated list of allowed JOSE asymmetric signing algorithms, for example, `RS256`, `ES256`.

</td>
</tr>
<tr>
<td valign="top">

*Username Prefix*

btp CLI parameter: `usernamePrefix`

type: string

</td>
<td valign="top">

Provides an OIDC username prefix for Kyma runtime.

</td>
<td valign="top">

Provisioning

Updating

</td>
<td valign="top">

If not provided, username claims other than an email address are prefixed by the issuer URL to avoid clashes.

</td>
<td valign="top">

To skip any prefixing, provide the value "-" \(dash character without additional characters\).

</td>
</tr>
</table>

The following example shows the default configuration of the *OIDC* parameter. When you want to revert your changes to the default settings, copy and paste the following values:

```
 "oidc": {
        "clientID": "12b13a26-d993-4d0c-aa08-5f5852bbdff6",
        "groupsClaim": "groups",
        "issuerURL": "https://kyma.accounts.ondemand.com",
        "signingAlgs": ["RS256"],
        "usernameClaim": "sub",
        "usernamePrefix": "-"
    }
```



<a name="loioe2e13bfaa2f54a4fb179f0f1f840353a__section_Region"/>

## Region\*

*Region\** \(`region`\) is a mandatory string parameter, which defines a region where your cluster runs.

**Region Parameter**


<table>
<tr>
<th valign="top">

Plan

</th>
<th valign="top">

Supported Operation

</th>
<th valign="top">

Region Technical Key

</th>
<th valign="top">

Region Name

</th>
</tr>
<tr>
<td valign="top" rowspan="12">

Standard: Amazon Web Services

technical name: `aws`

Free

technical name: `free`

</td>
<td valign="top" rowspan="12">

Provisioning

</td>
<td valign="top">

`eu-central-1`

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
</tr>
<tr>
<td valign="top">

`eu-west-2`

</td>
<td valign="top">

Europe \(London\)

</td>
</tr>
<tr>
<td valign="top">

`ca-central-1`

</td>
<td valign="top">

Canada \(Montreal\)

</td>
</tr>
<tr>
<td valign="top">

`sa-east-1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top">

`us-east-1`

</td>
<td valign="top">

US East \(VA\)

</td>
</tr>
<tr>
<td valign="top">

`us-west-1`

</td>
<td valign="top">

US West \(N. California\)

</td>
</tr>
<tr>
<td valign="top">

`ap-northeast-1`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`ap-northeast-2`

</td>
<td valign="top">

South Korea \(Seoul\)

</td>
</tr>
<tr>
<td valign="top">

`ap-south-1`

</td>
<td valign="top">

India \(Mumbai\)

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-1`

</td>
<td valign="top">

Singapore

</td>
</tr>
<tr>
<td valign="top">

`ap-southeast-2`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`us-west-2`

</td>
<td valign="top">

US West \(Oregon\)

</td>
</tr>
<tr>
<td valign="top" rowspan="8">

Standard: Google Cloud

technical name: `gcp`

</td>
<td valign="top" rowspan="8">

Provisioning

</td>
<td valign="top">

`europe-west3`

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
</tr>
<tr>
<td valign="top">

`asia-south1`

</td>
<td valign="top">

India \(Mumbai\)

</td>
</tr>
<tr>
<td valign="top">

`us-central1`

</td>
<td valign="top">

US Central \(IA\)

</td>
</tr>
<tr>
<td valign="top">

`asia-northeast2`

</td>
<td valign="top">

Japan \(Osaka\)

</td>
</tr>
<tr>
<td valign="top">

`me-central2`

</td>
<td valign="top">

KSA \(Dammam\)

</td>
</tr>
<tr>
<td valign="top">

`me-west1`

</td>
<td valign="top">

Israel \(Tel Aviv\)

</td>
</tr>
<tr>
<td valign="top">

`australia-southeast1`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`southamerica-east1`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
<tr>
<td valign="top" rowspan="11">

Standard: Microsoft Azure

technical name: `azure`

Kyma Test Demo and Development \(Azure Lite\)

technical name: `azure_lite`

</td>
<td valign="top" rowspan="11">

Provisioning

</td>
<td valign="top">

`eastus`

</td>
<td valign="top">

US East \(VA\)

</td>
</tr>
<tr>
<td valign="top">

`centralus`

</td>
<td valign="top">

US Central \(IA\)

</td>
</tr>
<tr>
<td valign="top">

`westus2`

</td>
<td valign="top">

US West \(WA\)

</td>
</tr>
<tr>
<td valign="top">

`uksouth`

</td>
<td valign="top">

UK South \(London\)

</td>
</tr>
<tr>
<td valign="top">

`northeurope`

</td>
<td valign="top">

North EU \(Ireland\)

</td>
</tr>
<tr>
<td valign="top">

`westeurope`

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
</tr>
<tr>
<td valign="top">

`japaneast`

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
</tr>
<tr>
<td valign="top">

`southeastasia`

</td>
<td valign="top">

Singapore

</td>
</tr>
<tr>
<td valign="top">

`australiaeast`

</td>
<td valign="top">

Australia \(Sydney\)

</td>
</tr>
<tr>
<td valign="top">

`switzerlandnorth`

</td>
<td valign="top">

Switzerland \(Zurich\)

</td>
</tr>
<tr>
<td valign="top">

`brazilsouth`

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
</tr>
</table>

Here is an example of the JSON input for the *Region* parameter:

```
"region": "us-east-1"
```

**Related Information**  


[Available Plans in the Kyma Environment](available-plans-in-the-kyma-environment-befe01d.md "Depending on your global account type, you have access to a different plan that specifies the cluster parameters for the Kyma environment.")

[Regions for the Kyma Environment](../10-concepts/regions-for-the-kyma-environment-557ec3a.md "To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.")

[Kyma Modules](../10-concepts/kyma-modules-0dda141.md "With Kyma's modular approach, you can install just the modules you need, instead of a predefined set of components.")

[Account Administration Using the SAP BTP Command Line Interface \(btp CLI\)](account-administration-using-the-sap-btp-command-line-interface-btp-cli-7c6df2d.md "Use the SAP BTP command line interface (btp CLI) for all account administration tasks, such as creating or updating subaccounts, authorization management, and working with service brokers and platforms. It is an alternative to the SAP BTP cockpit for users who like to work in a terminal or want to automate operations using scripts.")

