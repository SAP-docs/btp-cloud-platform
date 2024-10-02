<!-- loio2f69be279c3b46aab70eaa5802930f1e -->

# Keda Module

Learn more about the Keda module. Use it to install and manage the [KEDA](https://keda.sh/) autoscaler in your Kubernetes cluster.



<a name="loio2f69be279c3b46aab70eaa5802930f1e__section_h2t_yq2_qbc"/>

## What Is KEDA?

Kubernetes-based Event Driven Autoscaler \(KEDA\) is an autoscaler that allows you to easily scale your Kubernetes-based resources. You can scale your applications on the basis of the data of your choice.

KEDA supports a great number of scalers that help you manage your deployments. For the complete list, check the[KEDA Scalers documentation](https://keda.sh/docs/latest/scalers/).

For more information about KEDA features, see the[KEDA documentation](https://keda.sh/docs/latest).



<a name="loio2f69be279c3b46aab70eaa5802930f1e__section_prg_1r2_qbc"/>

## Features

With the Keda module, you can have a custom event-driven autoscaling for Kubernetes workloads.



<a name="loio2f69be279c3b46aab70eaa5802930f1e__section_ixg_1r2_qbc"/>

## Architecture

![](images/Keda_module_architecture_0cb8230.svg)

1.  User applies the Keda custom resource \(CR\).

2.  Keda Manager watches the Keda CR.
3.  Keda Manager reconciles the KEDA workloads.

To learn more about the KEDA architecture, see the [KEDA architecture diagram](https://keda.sh/docs/latest/concepts/#architecture).



### Keda Manager

Keda Manager helps you to install and manage KEDA in your cluster. It manages the lifecycle of KEDA based on the dedicated Keda CR.



<a name="loio2f69be279c3b46aab70eaa5802930f1e__section_j3q_qr2_qbc"/>

## API/Custom Resource Definitions

For the Keda CR conditions, check [Keda Custom Resource Conditions](keda-custom-resource-conditions-12a88ed.md).

To learn more about the KEDA CR, see [KEDA Custom Resources](https://keda.sh/docs/latest/concepts/#custom-resources-crd).



<a name="loio2f69be279c3b46aab70eaa5802930f1e__section_u2c_qr2_qbc"/>

## Resource Consumption

To learn more about the resources used by the Keda module, see [Keda](../50-administration-and-ops/kyma-modules-sizing-3a92490.md#loio3a924906857b4f01969cb684ccd25309__section_keda).





<a name="loio2f69be279c3b46aab70eaa5802930f1e__section_jwg_3y1_tcc"/>

## Keda Module Demo Applications

To learn how to scale the Kubernetes workloads using the KEDA API based on a simple CPU consumption case and how the Keda module can complement other Kyma components, see [Demo Applications](https://github.com/kyma-project/keda-manager/blob/main/docs/user/04-20-demo-applications.md).

