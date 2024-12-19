<!-- loio4c78f5830663468588f3d45fac976e0e -->

# Verify Image Signatures in the Kyma Environment

Image signing and image signature verification are important countermeasures against security threats. They help you ensure the authenticity and integrity of the application you deploy in the runtime. You can be sure that what you deploy is what you have built in the build pipeline. While image signing happens in the automated Continuous Delivery \(CD\) workflow, image signature verification takes place at the time the workload is scheduled in the runtime. For this purpose, Kyma uses Warden, which is added to your cluster by default and ensures that the Kyma workloads are authentic.

Warden is automatically enabled in the namespaces managed by Kyma \(`kyma-system`, `istio-system`\). Therefore, you can be sure the Kyma-managed workloads are authentic. Use the `kubectl get namespaces -l namespaces.warden.kyma-project.io/validate=enabled` command to list the Kyma system namespaces, protected by Warden.

> ### Caution:  
> When you enable third-party Kubernetes tools that mutate workloads \(for example, Dynatrace that adds init containers\), you must exclude the Kyma-managed namespaces, which are protected by Warden, from the tool config. Otherwise, Warden blocks unknown images. Mind that disrupting the Kyma-managed namespaces may lead to an inability to uphold the Service Level Agreement \(SLA\).

**Related Information**  


[GitHub repository: Warden](https://github.com/kyma-project/warden)

