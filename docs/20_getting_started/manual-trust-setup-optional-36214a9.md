<!-- loio36214a93a8864662996a0d0814f3e1b7 -->

# Manual Trust Setup \(Optional\)

If you want to use Identity Authentication service as custom identity provider, you need to set up trust between the Cloud Foundry account and the Identity Authentication service.

> ### Note:  
> You only need to set up trust manually if you don't want to use the function to establish trust automatically \(see [Establish Trust Automatically](establish-trust-automatically-b9f4b0d.md)\).

You need to configure how the Cloud Foundry account, which acts as local service provider, communicates with the identity provider. This includes, for example, setting a signing key and certificate to verify the service provider’s identity and encrypt data. This configuration is later needed for developer authentication.

