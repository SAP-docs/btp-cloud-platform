<!-- loiof8cb6e55496b4bd1be68d6dfa4d15487 -->

# Kubernetes Pod Security Recommendations



Pods are the smallest deployable units of computing that you can create and manage in Kubernetes. This document shows how to use Pods securely and ultimately have a secure workload. Follow the three-step guidelines depending on your workload's needs. First, decide on the basic security settings, then enable additional capabilities if needed, and finally, consider special features.



<a name="loiof8cb6e55496b4bd1be68d6dfa4d15487__section_id3_st3_mbc"/>

## 1. Decide on the Basic Security Settings



### Without Special Requirements: Highest Security

If you are not aware of any special requirements, set up your workload in the most secure way:

-   Specify a user for the Pod and container. If your application requires a specific user, change values for the `runAsUser` and `runAsGroup` parameters.

-   Run an unprivileged workload.

-   Drop all capabilities.

-   Use seccomp. For more details, read the [Kubernetes documentation](https://kubernetes.io/docs/tutorials/security/seccomp/).

-   Run with a read-only root file system.


Use the following `securityContext` configuration for the Pod and container.

> ### Sample Code:  
> ```
> # Pod spec
>   securityContext:
>     runAsUser: 10001
>     runAsGroup: 30001
>     runAsNonRoot: true
>     seccompProfile:
>       type: RuntimeDefault
> 
> # Container spec
>       securityContext:
>         privileged: false
>         allowPrivilegeEscalation: false
>         runAsNonRoot: true
>         capabilities:
>           drop:
>             - ALL
>         readOnlyRootFilesystem: true
> ```



### If Your Container Must Run as User Root

If your container must run as user root, use the following setup:

-   Do not use the `runAsUser` and `runAsGroup` parameters in the spec or set them to *0*.

-   Do not use the `runAsNonRoot` parameter.

-   Run an unprivileged workload and do not allow privilege escalation.

-   Drop all capabilities.

-   Use seccomp.

-   Run with a read-only root file system.


Use the following `securityContext` configuration for the Pod and container.

> ### Sample Code:  
> ```
> # Pod spec
>   securityContext:
>     seccompProfile:
>       type: RuntimeDefault
> 
> # Container spec
>       securityContext:
>         privileged: false
>         allowPrivilegeEscalation: false
>         readOnlyRootFilesystem: true
>         capabilities:
>           drop:
>             - ALL
> ```



<a name="loiof8cb6e55496b4bd1be68d6dfa4d15487__section_ypt_4w3_mbc"/>

## 2. Enable Additional Capabilities



### Add Storage to Your Pod

If you need storage, follow these recommendations:

-   Always use volumes instead of local storage in the container.

-   Avoid using `hostPath` volumes. If you must use them, follow these rules:

    -   **Whenever possible**mount `hostPath` volumes in the read-only mode.

    -   **Never**mount the following sensitive paths:

        -   `/proc` - a pseudo-file system that provides an interface to kernel data structures

        -   `/`- file system's root

        -   `/etc` - the directory that usually contains all system-related configuration files

        -   `/root` - the home directory of the root user

        -   `/var/run/docker.sock` - the Unix socket used to communicate with the Docker daemon

        -   `/var/run/crio/crio.sock` - the Unix socket used to communicate with the CRI-O Container Engine

        -   `/run/containerd/containerd.sock` - the Unix socket used to communicate with the Containerd container runtime

        -   `/home/admin` - the home directory of the admin user

        -   `/var/lib/kubelet` - the directory for kubelet-related configuration

        -   `/var/lib/kubelet/pki` - the directory containing the certificate and private key of the kubelet

        -   `/etc/kubernetes` - the directory containing Kubernetes-related configuration

        -   `/etc/kubernetes/manifests`


    -   Use only the *File* or *Directory* `hostPath.type`. Usually use *File*, and *Directory* as a fallback.
    -   Some files and directories on the host can only be accessible by root. Read more in the [Kubernetes documentation](https://kubernetes.io/docs/concepts/storage/volumes/#hostpath).


    Consider the following template for mounting `hostPath` volumes in order to create Kubernetes manifests:

    > ### Sample Code:  
    > ```
    > # Pod spec
    >   volumes:
    >     - name: <name>
    >       hostPath:
    >         path: <file or directory on the node>
    >         type: <File> or <Directory>
    > 
    > # Container spec
    >     volumeMounts:
    >       - mountPath: <path where hostpath has to be mounted>
    >         name: <name>
    >         readOnly: true
    > ```

-   Use `emptyDir` volumes for temporary file systems.

    If your application needs a temporary file system, for example, for caching purposes, use [`emptyDir`](https://kubernetes.io/docs/concepts/storage/volumes/#emptydir) volumes **instead of** mounting `hostPath` or making the root file system writable. Also, remember to always define a size limit for the volume. Use the following template:

    > ### Sample Code:  
    > ```
    > # Pod spec
    >   volumes:
    >   - name: <name>
    >     emptyDir:
    >       sizeLimit: <size of the volume>
    > # Container spec
    >     volumeMounts:
    >     - mountPath: <path where the file system has to be mounted>
    >       name: <name>
    > ```




### Add Other Capabilities

-   Before you add new cabilities to your Pod or container configuration, **always drop all** capabilities. Each container runs with a fixed set of default capabilities. You can find the containerd v1.7 default capabilities in [this code](https://github.com/containerd/containerd/blob/8c780b736a3f15cc17e32522c718eb9dbba3380e/oci/spec.go#L115).

-   Add only the capabilities you really need.

-   If possible, avoid the following capabilities that can be exploited to escalate privileges:

    -   CAP\_CHOWN

    -   CAP\_DAC\_OVERRIDE

    -   CAP\_DAC\_READ\_SEARCH

    -   CAP\_SETUID, CAP\_SETGID

    -   CAP\_NET\_RAW

    -   CAP\_SYS\_ADMIN

    -   CAP\_SYS\_PTRACE

    -   CAP\_SYS\_MODULE

    -   CAP\_FORMER

    -   CAP\_SETFCAP



If your application doesn't work as expected, you may need some additional capabilities. Find the full list of the available capabilities on the [Linux manual page](https://man7.org/linux/man-pages/man7/capabilities.7.html). Check which capabilities are missing using the [Inspector Gadget](https://github.com/inspektor-gadget/inspektor-gadget) tools. You can [install the toolset as a kubectl plugin using krew](https://github.com/inspektor-gadget/inspektor-gadget/blob/main/docs/getting-started/install-kubernetes.md#installing-kubectl-gadget). After it's installed, use the `kubectl gadget trace capabilities` command.



<a name="loiof8cb6e55496b4bd1be68d6dfa4d15487__section_gbk_4sn_mbc"/>

## 3. Consider Special Features



### Accessing Parts of the `/proc` file system

The `proc` file system provides a lot of critical information about the system and its running processes. To learn more, read [Exploring the Linux`/proc` file system](https://www.redhat.com/sysadmin/linux-proc-filesystem) and [Important Linux`/proc` file system files you need to know](https://www.redhat.com/sysadmin/important-proc-files). By default, container runtimes mask certain parts of the `/proc` file system from inside a container in order to prevent potential security issues.

> ### Caution:  
> You should change settings around the `/proc` file system only if you are aware of the impact. Changing the configuration may expose your system to security issues.

-   Check if you really need to use the `/proc` file system. For example, if you want to use it for image building purposes, check the latest version of your build tool because many of them no longer need it.

-   If you really need to use the `/proc` file system, only do so for a nested container. Never expose the `/proc` file system of your host system to a container.

-   If your application needs access to parts of the `/proc` file system, you can set the `procMount` field in the `PodSpec` to *unmasked* to remove the restriction on the visibility of the `/proc` file system from inside the container.




### Seccomp

Seccomp is a Linux kernel feature that allows filtering system calls made by a process. It is used to restrict the set of system calls that a process can make.

If, in `SecurityContext`, the `seccompProfile` is set to *RuntimeDefault*, the container uses the default seccomp profile provided by the container runtime.

Read more to learn about:

-   [Allowed system calls](https://github.com/containerd/containerd/blob/main/contrib/seccomp/seccomp_default.go) in the default profile of containerd.

-   The full list of [Linux system calls](https://man7.org/linux/man-pages/man2/syscalls.2.html).

-   How to work with Seccomp profiles in Kubernetes - [Restrict a Container's Syscalls with seccomp](https://kubernetes.io/docs/tutorials/security/seccomp/).

-   How to se tup a [Custom Seccomp Profile](https://gardener.cloud/docs/guides/applications/secure-seccomp/) in Gardener.




### Host Namespaces

Host namespaces \(Process ID namespace, Inter-Process Communication namespace, and network namespace\) allow you to access shared information. You can also use host namespaces to elevate privileges. By removing namespaces from Pods, you reduce isolation and circumvent the protection models that containers are based on. It allows the processes in the Pod to perform tasks as if they were running natively on the host.

In the Pod spec, the following fields represent the host namespaces:

-   `hostPID`: Process ID namespace

-   `hostIPC`: Inter-Process Communication namespace

-   `hostNetwork`: network namespace


The three fields are by default set to *false* and should remain so.

Usually, there is no need to remove this isolation and therefore, Pods should not have access to host namespaces. Removing namespaces from Pods is a very advanced feature. Use it only if you are certain you need it, for example, for low-level observation of other containers.

