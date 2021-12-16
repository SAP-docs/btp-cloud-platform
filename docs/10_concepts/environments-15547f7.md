<!-- loio15547f7e7ecd47ee9fa052b0e18c7b0a -->

# Environments

Environments constitute the actual platform-as-a-service offering of SAP BTP that allows for the development and administration of business applications. Environments are anchored in SAP BTP on subaccount level. 



 Each environment comes equipped with specific tools, technologies, and runtimes that you need to build applications. So a multi-environment subaccount is your single address to host a variety of applications and offer diverse development options. One advantage of using different environments in one subaccount is that you only need to manage users, authorizations, and entitlements once per subaccount, and thus grant more flexibility to your developers.

![Environments on SAP BTP](images/Environment_ae827d3.png)



<a name="loio15547f7e7ecd47ee9fa052b0e18c7b0a__section_brc_k2l_kpb"/>

## Environment Instances

To actually use an environment in a subaccount, you need to**enable** it by creating an instance of that environment. There are several ways to create **environment instances**:

-   Using the subaccount overview page in the cockpit: choose Enable.

-   Using the Service Marketplace tab in the cockpit: here you get more information, such as the available plans and links to further information.

-   Using the btp CLI command `btp create accounts/environment-instance`


**Related Information**  


[Account Administration](../50_administration_and_ops/account-administration-5d62ec8.md "Learn how to manage global accounts, directories, and subaccounts on SAP BTP using different tools.")

