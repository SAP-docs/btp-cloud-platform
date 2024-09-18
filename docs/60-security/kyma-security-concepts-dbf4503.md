<!-- loiodbf4503053634acfa4465e0c6d25437f -->

# Kyma Security Concepts

SAP BTP, Kyma runtime takes various security measures regarding your cluster and its underlying infrastructure. Benefit from the security setup that SAP BTP, Kyma runtime provides.



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_svs_s4y_pzb"/>

## Cloud Infrastructure

All components required to run Kyma, namely Gardener, Kyma Control Plane, and a Kyma cluster, are deployed on SAP-managed IaaS provider accounts. SAP has strict guidelines to secure IaaS provider accounts and the resources deployed into them. The secure configuration is monitored regularly, and the following preventive controls are in place to revert critical configurations that weaken the security of the IaaS provider account:



### Authentication

-   A strict password policy is in place.

-   Multi-factor authentication is enabled.




### Authorization

-   Permissions are assigned based on role-based access control \(RBAC\).

-   The principle of least privilege is followed.




### Storage

-   Storage services are not publicly accessible.

-   Encryption using Advanced Encryption Standard \(AES\) with a key length of at least 256 is used.




<a name="loiodbf4503053634acfa4465e0c6d25437f__section_yyn_rgb_rzb"/>

## Kubernetes Control Plane

Kyma uses Gardener as its managed Kubernetes offering. With Gardener, the control plane of a Kubernetes cluster is hosted as a set of Pods in the Gardener environment. See the overview of the [Gardener architecture](https://gardener.cloud/docs/gardener/concepts/architecture/#overview-architecture-diagram). In order to harden the Kubernetes control plane as well as the Kubernetes components on the worker nodes, Gardener sets up the cluster in accordance with the Defense Information Systems Agency \(DISA\) Security Technical Implementation Guides \(STIGs\) requirements \([V1R6](https://cyber.trackr.live/stig/Kubernetes/1/6)\).

The Kubernetes control plane fulfills the following DISA STIGs requirements:



### General

-   A kubectl version higher than 1.12.9 is used on the control plane \(V-242396\).

-   The Kubernetes DynamicAuditing \(V-242398\) and DynamicKubeletConfig \(V-242399\) are disabled.

-   Kubernetes manifests \(V-242405\), component manifests \(V-242444\), configuration files \(V-242446\), component PKI \(V-242451\), and `kubeadm.conf` \(V-242454\) are owned by root.

-   The Kubernetes manifest files have restrictive file permissions following the least privileges principle \(V-242408\).

-   Kubernetes doesn’t store Secrets as environment variables \(V-242415\).

-   The role-based access control \(RBAC\) is activated to control access \(V-242435\).

-   Kubernetes is kept up to date with the latest patches, service packs, and hot fixes. A patch management process is in place \(V-242443\).

-   The Kubernetes `kubeadm.conf` \(V-242455\), `admin.conf` \(V-242460\), and PKI CRT \(V-242466\) have restrictive file permissions.

-   Access to the directory containing the Kubernetes PKI files is restricted \(V-242467\).

-   Kubernetes endpoints use the approved organizational certificate and key pair to protect information in transit \(V-245544\).




### API Server

The Kubernetes kube-apiserver fulfills the following DISA STIGs requirements:

-   TLS 1.2, at a minimum, is used to protect the confidentiality of sensitive data during electronic dissemination \(V-242378\).

-   The Alpha APIs are disabled \(V-242400\).

-   The insecure bind address \(V-242388\) and insecure port \(V-242386\) are not set, and a secure API server port is configured \(V-242389\).

-   The approved SSL Certificate Authority is set \(V-242419\).

-   Only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) are configured \(V-242410\).

-   Approved cipher suites are used \(V-242418\).

-   A certificate for communication is used \(V-242422\).

-   The `ValidatingAdmissionWebhook` is enabled \(V-242436\).

-   Appropriate timeouts are set to limit attack surface \(V-242438\).

-   Restrictive file permissions for the configuration files of the Control Plane services are used \(V-242458\).

-   Only secure encryption protocols are used. SSL, TLS 1.0, and 1.1 are prohibited. \(V-242468\).




### Kubernetes Scheduler

The Kubernetes scheduler, namely, kube-scheduler fulfills the following DISA STIGs requirements:

-   TLS 1.2, at a minimum, is used to protect the confidentiality of sensitive data during electronic dissemination \(V-242377\).

-   A secure binding to localhost \(127.0.0.1\) is used \(V-242384\).

-   Only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) are configured \(V-242411\).




### Controller Manager

The Kubernetes Controller Manager fulfills the following DISA STIGs requirements:

-   TLS 1.2, at a minimum, is used to protect the confidentiality of sensitive data during electronic dissemination \(V-242376\).

-   Unique service accounts for each work payload are used \(V-242381\).

-   A secure binding to localhost \(127.0.0.1\) is used \(V-242385\).

-   Profiling is disabled \(V-242409\).

-   The SSL Certificate Authority is set \(V-242421\).

-   Only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) are configured \(V-242412\).




### etcd

The Kubernetes etcd fulfills the following DISA STIGs requirements:

-   The usage of self-signed certificates for client-to-server and server-to-server communication is prohibited \(V-242379, V-242380\).

-   Only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) are configured \(V-242413\).

-   Certificate-base client authentication is enabled \(V-242423\), \(V-242426\).

-   TLS encrypted client-to-server and server-to-server communication is configured \(V-242427, V-242432, V-242433\). The communication between the API server and etcd is encrypted with TLS \(V-242431\).

-   Approved and valid certificates for the TLS encrypted connection between the API server and etcd are used \(V-242428, V-242430\). An SSL certificate authority is configured \(V-242429\).

-   Files are owned by etcd:etcd \(V-242445\).

-   Files have restrictive file permissions set \(V-242459\).




<a name="loiodbf4503053634acfa4465e0c6d25437f__section_nzx_xrb_rzb"/>

## Kubernetes Worker Nodes

Kyma uses [Garden Linux](https://github.com/gardenlinux/gardenlinux) as its node operating system. Garden Linux is a Linux distribution with a minimal set of applications optimized for use in Gardener landscapes. Kubernetes worker nodes use a kubectl version higher than 1.12.9 \(V-242396\).





### kubelet

The Kubernetes kubelet fulfills the following DISA STIGs requirements:

-   The read-only port flag \(V-242387\) and anonymous authentication \(V-242391\) are disabled.

-   Explicit authorization is required \(V-242392\).

-   Hostname override is denied \(V-242404\).

-   An SSL certificate authority is configured \(V-242420\).

-   TLS is enabled to enforce TLS encrypted communication sessions \(V-242424, V-242425\).

-   Kernel protection is set \(V-242434\).

-   A connection timeout is set \(V-245541\).

-   No staticPodPath is configured \(V-242397\).

-   The Kubernetes kubelet configuration file \(V-242406\), certificate authority \(V-242450\), and config \(V-242453, V-242457\) are owned by root.

-   The Kubernetes kubelet configuration files \(V-242407\), certificate authority file \(V-242449\), config file \(V-242452, V-242456\) have restrictive file permissions set \(V-242407\).




### kube-proxy

The Kubernetes kube-proxy fulfills the following DISA STIGs requirements:

-   A kubeconfig file is not used \(V-242447, V-242448\).




<a name="loiodbf4503053634acfa4465e0c6d25437f__section_uwp_pvd_rzb"/>

## Network Separation



### Namespaces

Kyma components are deployed into the `kyma-system` and the `istio-system` namespaces. The default namespace is not used.



### Network Policies

You, the customer, have full access to the cluster and can establish appropriate network policies to restrict network traffic. Because Istio is a default Kyma module, the customer can also establish PeerAuthentication policies to control the network traffic.



### Encryption

All communication in the Kyma cluster is encrypted using TLS 1.2.



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_hfc_lwd_rzb"/>

## Authentication and Authorization



### Authentication at the API Server

By default, a SAP BTP, Kyma runtime cluster is deployed with a shared tenant of SAP Cloud Identity Services provided by SAP. This Identity Provider \(IDP\) uses OIDC tokens to authenticate and is configured to enforce multi-factor authentication.

As a best practice, you, the customer, can change the IdP to one controlled by you. This gives you control over the identity lifecycle of your accounts. Learn how to [Configure a Custom Identity Provider for Kyma](configure-a-custom-identity-provider-for-kyma-67bcc6e.md).

The Kubernetes API Server fulfills the following DISA STIGs requirements:

-   Anonymous authentication is disabled \(V-242390\).

-   Basic authentication is disabled to protect information in transit \(V-245542\).

-   Token authentication is disabled to protect information in transit \(V-245543\).




### Role-based Access Control

RBAC is enabled on Kyma clusters. The Roles and ClusterRoles deployed by Kyma follow the principle of least privilege.

Following DISA STIGs requirements, the Kubernetes API server enables RBAC as the authorization mode \(V-242382\).



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_sd2_fph_rzb"/>

## High Availability

Kyma worker nodes are distributed over several availability zones in order to prevent outages of the cloud providers’ availability zones.



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_kpp_gph_rzb"/>

## Logging



### Kubernetes-Native Audit Logging Configuration

Audit Logging of the Kubernetes API server is active, and the logs are written to SAP Platform Logging Service for SAP BTP.

The Kubernetes API server fulfils the following DISA STIGs requirements:

-   An audit policy \(V-242401\), an audit log path \(V-242402, V-242465\), and audit log retention \(V-242464\) are set.

-   Audit records that provide information about the type of event that has occurred, the source of the event, the results of the event, any users and containers associated with the event are generated \(V-242403\).

-   Audit logs are enabled \(V-242461\).

-   Audit log maximum size \(V-242462\), and maximum backup are configured \(V-242463\).




### Container Logging

Kyma modules ship logs that contain information relevant to the containers.

**Related Information**  


[Security Vulnerability Management in the Kyma Environment](security-vulnerability-management-in-the-kyma-environment-b1b0a64.md "")

[Distributed Denial-of-Service Protection in Kyma](distributed-denial-of-service-protection-in-kyma-5e13d59.md "A distributed denial-of-service (DDoS) attack is a malicious attempt to disrupt the normal traffic of a targeted server, service or network by overwhelming the target or its surrounding infrastructure with a flood of traffic.")

[Secure Administration and Operations in the Kyma Environment](secure-administration-and-operations-in-the-kyma-environment-a22ef28.md "Secure administration and operations focus on landscape setup, authentication, authorization, and Istio access logs. Learn about the security measures you can take to improve the security of your Kyma environment.")

[Secure Development in the Kyma Environment](secure-development-in-the-kyma-environment-ff51a32.md "Secure development focuses on Pod security, network traffic restriction, Istio sidecar proxy injection, and workload exposure. Learn about the security measures you can take to improve the security of your Kyma environment .")

