<!-- loio1be599b74c9042b0b0b356598502b394 -->

# Function Security

When creating Functions, make sure you understand how they work to avoid potential threats.

To eliminate potential security risks when using Functions, bear in mind these few facts:

-   By default, JSON Web Tokens \(JWTs\) issued by Dex do not provide the **scope** parameter for Functions. This means that if you expose your Function and secure it with a JWT, you can use the token to validate access to all Functions within the cluster as well as other JWT-protected services.
-   There are no authorization policies defined that would restrict Functions' access to other resources within the Namespace. If you deploy a Function in a given Namespace, it can freely access all events and APIs of services within this Namespace.
-   All administrators and regular users who have access to a specific Namespace in a cluster can also access:
    -   Source code of all Functions within this Namespace
    -   Internal Docker registry that contains Function images


