<!-- loiodbf4503053634acfa4465e0c6d25437f -->

# Kyma Security Measures

SAP BTP, Kyma runtime takes measures to ensure the security of the clusters and their underlying infrastructure on several levels, such as cloud infrastructure, Kubernetes control plane, worker nodes, network separation, authentication and authorization, high availability, and logging.



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_svs_s4y_pzb"/>

## Cloud Infrastructure

All components required to run Kyma, namely Gardener, Kyma Control Plane, and a Kyma cluster, are deployed on SAP-managed hyperscaler accounts. SAP has strict guidelines to secure hyperscaler accounts and the resources deployed into them. The secure configuration is monitored regularly, and the following preventive controls are in place to revert critical configurations that weaken the security of the hyperscaler account.



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

-   Kubernetes doesn’t store secrets as environment variables \(V-242415\).

-   The role-based access control \(RBAC\) is activated to control access. \(V-242435\).

-   Kubernetes is kept up to date with the latest patches, service packs, and hot fixes. A Patch Management process is in place \(V-242443\).

-   The Kubernetes `kubeadm.conf` \(V-242455\), `admin.conf` \(V-242460\), and PKI CRT \(V-242466\) have restrictive file permissions.

-   Access to the directory containing the Kubernetes PKI files is restricted \(V-242467\).

-   Kubernetes endpoints use the approved organizational certificate and key pair to protect information in transit \(V-245544\).




### API Server

The Kubernetes kube-apiserver:

-   Uses TLS 1.2, at a minimum, to protect the confidentiality of sensitive data during electronic dissemination \(V-242378\).

-   Has the Alpha APIs \(V-242400\) disabled.

-   Has the insecure bind address \(V-242388\) and insecure port \(V-242386\) not set, and a secure API server port \(V-242389\) configured.

-   Has the approved SSL Certificate Authority \(V-242419\) set.

-   Has configured only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) \(V-242410\).

-   Uses approved cipher suites \(V-242418\).

-   Has a certificate for communication \(V-242422\).

-   Has the `ValidatingAdmissionWebhook` enabled \(V-242436\).

-   Has appropriate timeouts set to limit attack surface \(V-242438\).

-   Has restrictive file permissions for the configuration files of the Control Plane services \(V-242458\).

-   Is configured to use only secure encryption protocols. SSL, TLS 1.0, and 1.1 are prohibited. \(V-242468\).




### Kubernetes Scheduler

The Kubernetes scheduler, namely, kube-scheduler:

-   Uses TLS 1.2, at a minimum, to protect the confidentiality of sensitive data during electronic dissemination \(V-242377\).

-   Has a secure binding to localhost \(127.0.0.1\) \(V-242384\).

-   Has configured only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) \(V-242411\).




### Controller Manager

The Kubernetes Controller Manager:

-   Uses TLS 1.2, at a minimum, to protect the confidentiality of sensitive data during electronic dissemination \(V-242376\).

-   Has unique service accounts for each work payload \(V-242381\).

-   Has a secure binding to localhost \(127.0.0.1\) \(V-242385\).

-   Has profiling disabled \(V-242409\).

-   Has the SSL Certificate Authority set \(V-242421\).

-   Has configured only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) \(V-242412\).




### etcd

The Kubernetes etcd:

-   The usage of self-signed certificates for client-to-server and server-to-server communication is prohibited \(V-242379, V-242380\).

-   Has configured only ports, protocols, and services \(PPS\) that adhere to the Ports, Protocols, and Services Management Category Assurance List \(PPSM CAL\) \(V-242413\).

-   Has certificate-base client authentication enabled \(V-242423\), \(V-242426\).

-   Has TLS encrypted client-to-server and server-to-server communication configured \(V-242427, V-242432, V-242433\). The communication between the API server and etcd is encrypted with TLS \(V-242431\).

-   Uses approved and valid certificates for the TLS encrypted connection between the API server and etcd \(V-242428, V-242430\). An SSL certificate authority is configured \(V-242429\).

-   Files are owned by etcd:etcd \(V-242445\).

-   Files have restrictive file permissions set. \(V-242459\).




<a name="loiodbf4503053634acfa4465e0c6d25437f__section_nzx_xrb_rzb"/>

## Kubernetes Worker Nodes

Kyma uses [Garden Linux](https://github.com/gardenlinux/gardenlinux) as its node operating system. Garden Linux is a specially crafted Linux distribution with a minimal set of applications optimized for use in Gardener landscapes. Kubernetes worker nodes use a kubectl version higher than 1.12.9 \(V-242396\).





### kubelet

The Kubernetes kubelet:

-   Has the read-only port flag \(V-242387\) and anonymous authentication \(V-242391\) disabled.

-   Requires explicit authorization \(V-242392\).

-   Denies hostname override \(V-242404\).

-   Has an SSL certificate authority configured \(V-242420\).

-   Has TLS enabled to enforce TLS encrypted communication sessions \(V-242424, V-242425\).

-   Has kernel protection set \(V-242434\).

-   Has a connection timeout set \(V-245541\).

-   Has no staticPodPath configured \(V-242397\).

-   The Kubernetes kubelet configuration file \(V-242406\), certificate authority \(V-242450\), and config \(V-242453, V-242457\) are owned by root.

-   The Kubernetes kubelet configuration files \(V-242407\), certificate authority file \(V-242449\), config file \(V-242452, V-242456\) have restrictive file permissions set \(V-242407\).




### kube-proxy

The Kubernetes kube-proxy:

-   Does not make use of a kubeconfig file \(V-242447, V-242448\).




<a name="loiodbf4503053634acfa4465e0c6d25437f__section_uwp_pvd_rzb"/>

## Network Separation



### Namespaces

Kyma components are deployed into the `kyma-system` and the `istio-system` namespaces. The default namespace is not used.



### Network Policies

The customer has full access to the cluster and can establish appropriate network policies to restrict network traffic. Because Istio is a default Kyma module, the customer can also establish PeerAuthentication policies to control the network traffic.



### Encryption

All communication in the Kyma cluster is encrypted using TLS 1.2.



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_hfc_lwd_rzb"/>

## Authentication and Authorization



### Authentication at the API Server

By default, a SAP BTP, Kyma runtime cluster is deployed with a shared tenant of SAP Cloud Identity Services provided by SAP. This Identity Provider \(IDP\) uses OIDC tokens to authenticate and is configured to enforce Multi-Factor Authentication.

As a best practice, change the IDP to one controlled by the customer. This gives them control over the identity lifecycle of your accounts. Learn how to [Configure a Custom Identity Provider for Kyma](configure-a-custom-identity-provider-for-kyma-67bcc6e.md).

Following DISA STIGs requirements, the Kubernetes API Server:

-   Has anonymous authentication disabled \(V-242390\).

-   Has basic authentication disabled to protect information in transit \(V-245542\).

-   Has token authentication disabled to protect information in transit \(V-245543\).




### Role-based Access Control

RBAC is enabled on Kyma clusters. The Roles and ClusterRoles deployed by Kyma follow the principle of least privilege.

Following DISA STIGs requirements, the Kubernetes API server enables RBAC as the authorization mode \(V-242382\).



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_sd2_fph_rzb"/>

## High Availability

Kyma worker nodes are distributed over several availability zones in order to prevent outages of the cloud providers’ availability zones.



<a name="loiodbf4503053634acfa4465e0c6d25437f__section_kpp_gph_rzb"/>

## Logging



### Kubernetes-Native Audit Logging Configuration

Audit Logging of the Kubernetes API server is active and the logs are written to SAP Platform Logging Service for SAP BTP.

Following DISA STIGs requirements, the Kubernetes API server:

-   Has an audit policy \(V-242401\), an audit log path \(V-242402, V-242465\), and audit log retention \(V-242464\) set.

-   Generates audit records that provide information about the type of event that has occurred, the source of the event, the results of the event, any users and containers associated with the event \(V-242403\).

-   Has audit logs enabled \(V-242461\).

-   Has audit log maximum size \(V-242462\), and maximum backup configured \(V-242463\).




### Container Logging

Kyma components ship logs that contain information relevant to the containers.

