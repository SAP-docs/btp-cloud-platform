<!-- loio43590d2e92c84bcf878babb28a7dad3d -->

# Function Security

To eliminate potential security risks when using Functions, bear in mind these facts:

-   Kyma Serverless applies a strict securityContext configuration at the Pod and container level \(non-root execution, minimal capabilities, and other hardening defaults\), allowing Functions to run in namespaces where the restricted Pod security level is enforced.

-   By default, JSON Web Tokens \(JWTs\) issued by an OpenID Connect-compliant identity provider do not provide the **scope** parameter for Functions. This means that if you expose your Function and secure it with a JWT, you can use the token to validate access to all Functions within the cluster as well as other JWT-protected services.

-   Kyma provides base images for serverless runtimes. Those default runtimes are maintained with regard to commonly known security advisories. It is possible to use a custom runtime image. For more information, see [Override Runtime Image](https://kyma-project.io/#/serverless-manager/user/tutorials/01-110-override-runtime-image). In such a case, you are responsible for security compliance and assessment of exploitability of any potential vulnerabilities of the custom runtime image. Additionally, your custom runtime image must support running as a non-root user under the restricted Pod security level, for example, no dependency on root ownership of writable paths, privileged operations, or added capabilities.

-   Kyma does not run any security scans against Functions and their images. Before you store any sensitive data in Functions, consider the potential risk of data leakage.

-   Kyma does not define any authorization policies that would restrict Functions' access to other resources within the namespace. If you deploy a Function in a given namespace, it can freely access all events and APIs of services within this namespace.

-   All administrators and regular users who have access to a specific namespace in a cluster can also access the source code of all Functions within this namespace.


