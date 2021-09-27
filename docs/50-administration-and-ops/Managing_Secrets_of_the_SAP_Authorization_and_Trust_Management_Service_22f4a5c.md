<!-- loio22f4a5c77be944059776985cf625a30b -->

# Managing Secrets of the SAP Authorization and Trust Management Service

The SAP Authorization and Trust Management service maintains a number of secrets to ensure secure operation of the service. Your organization can have policies that require you change secrets or you may need to respond to the loss of a secret.

The SAP Authorization and Trust Management service uses the following secrets in its operation:

-   [Service Instance Secrets](Service_Instance_Secrets_5578ec4.md)

-   [Rotate Binding Secrets](Rotate_Binding_Secrets_618441b.md)

-   [Migrate from Instance Secrets to Binding Secrets](Migrate_from_Instance_Secrets_to_Binding_Secrets_dcee867.md)

-   [Rotating Instance Secrets](Rotating_Instance_Secrets_8bfbbf5.md)

-   [Rotate Signing Keys of Access Tokens](Rotate_Signing_Keys_of_Access_Tokens_b279adf.md)

-   [Rotate Signing Keys of SAML Token](Rotate_Signing_Keys_of_SAML_Token_052e9b4.md)


-   **[Service Instance Secrets](Service_Instance_Secrets_5578ec4.md "When an application consumes a service instance of the SAP Authorization and Trust
                                    Management service (XSUAA), the
		application identifies itself to the service instance with a client ID and client secret.
		The client ID and client secret are the credentials with which an application authenticates
		itself to the service instance.")**  
When an application consumes a service instance of the SAP Authorization and Trust Management service \(XSUAA\), the application identifies itself to the service instance with a client ID and client secret. The client ID and client secret are the credentials with which an application authenticates itself to the service instance.
-   **[Rotate Binding Secrets](Rotate_Binding_Secrets_618441b.md "Service instances of the SAP Authorization and Trust
                                    Management service use different
		binding secrets for each binding. To rotate binding secrets, unbind and rebind any consuming
		applications.")**  
Service instances of the SAP Authorization and Trust Management service use different binding secrets for each binding. To rotate binding secrets, unbind and rebind any consuming applications.
-   **[Migrate from Instance Secrets to Binding Secrets](Migrate_from_Instance_Secrets_to_Binding_Secrets_dcee867.md "To simplify the management of secrets for service instances of the SAP Authorization and Trust
                                    Management service, we recommend
		that you configure service instances to use binding secrets.")**  
To simplify the management of secrets for service instances of the SAP Authorization and Trust Management service, we recommend that you configure service instances to use binding secrets.
-   **[Rotating Instance Secrets](Rotating_Instance_Secrets_8bfbbf5.md "When configured for instance secrets, a service instance of the SAP Authorization and Trust
                                    Management service uses the same
		instance secret for all bindings. You can't really rotate instance secrets, but must rotate
		the applications and service instance together.")**  
When configured for instance secrets, a service instance of the SAP Authorization and Trust Management service uses the same instance secret for all bindings. You can't really rotate instance secrets, but must rotate the applications and service instance together.
-   **[Rotate Signing Keys of Access Tokens](Rotate_Signing_Keys_of_Access_Tokens_b279adf.md "Components of the Cloud
                                Foundry
		environment use the digital signature of the access tokens to verify the validity of access
		tokens. To rotate the signing keys of access token, use the Security Setting API of the
			SAP Authorization and Trust
                                    Management service.")**  
Components of the Cloud Foundry environment use the digital signature of the access tokens to verify the validity of access tokens. To rotate the signing keys of access token, use the Security Setting API of the SAP Authorization and Trust Management service.
-   **[Rotate Signing Keys of SAML Token](Rotate_Signing_Keys_of_SAML_Token_052e9b4.md "The SAP Authorization and Trust
                                    Management service uses an X.509 certificate to sign SAML 2.0 protocol
		messages between itself, a SAML service provider, and an SAML identity provider. To rotate the signing keys for SAML tokens, use the Security
		Settings API of the SAP Authorization and Trust
                                    Management service and then establish trust by exchanging
		metadata between the service provider and identity provider.")**  
The SAP Authorization and Trust Management service uses an X.509 certificate to sign SAML 2.0 protocol messages between itself, a SAML service provider, and an SAML identity provider. To rotate the signing keys for SAML tokens, use the Security Settings API of the SAP Authorization and Trust Management service and then establish trust by exchanging metadata between the service provider and identity provider.

