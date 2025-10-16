<!-- loioead08cdb6c20433f8d283e762fe81634 -->

# Assigning Kyma Instances to IaaS Provider Accounts

Assignment rules for SAP BTP, Kyma runtime to IaaS provider accounts determine how Kyma instances are mapped to specific cloud provider account pools based on provider type, plan, and, in some cases, region.

Each IaaS provider \(Amazon Web Services, Google Cloud, Microsoft Azure, SAP Cloud Infrastructure\) provides pools of accounts to which your Kyma instances are assigned. The assignment is primarily based on the IaaS provider type. This means that Kyma instances in one global account are assigned to a single account of a particular IaaS provider. The IaaS provider corresponds to a Kyma instance's plan and, in some cases, other requirements, such as EU Access. For example, a Kyma instance with the standard `aws` plan is assigned to an Amazon Web Services account, and a Kyma instance with the `build-runtime-azure` plan is assigned to a Microsoft Azure account.



<a name="loioead08cdb6c20433f8d283e762fe81634__section_mcb_mty_wgc"/>

## IaaS Provider Account Assignment Rules

The specific assignment options are the following:

-   Amazon Web Services offers the following account pools:
    -   An account pool for Kyma instances created with the service plans `aws`, `build-runtime-aws`, or `free`
    -   An account pool for Kyma instances created with the service plans `aws` or `build-runtime-aws` in the subaccount region cf-eu11, Europe \(Frankfurt\) EU Access
    -   A pool of shared accounts for trial Kyma instances

-   Microsoft Azure offers the following account pools:
    -   An account pool for Kyma instances created with the service plans `azure`, `build-runtime-azure`, test demo and development plan `azure-lite`, and `free`
    -   An account pool for Kyma instances created with the service plans `azure` or `build-runtime-azure` in the subaccount region cf-ch20, Switzerland \(Zurich\) EU Access

-   Google Cloud offers the following account pools:
    -   An account pool for Kyma instances created with the service plans `gcp` or `build-runtime-gcp`
    -   An account pool for Kyma instances created with the service plans `gcp` or `build-runtime-gcp` in the subaccount region cf-sa30, KSA \(Dammam\) GCP public sector, requiring Assured Workloads Kingdom of Saudi Arabia \(KSA\) control package.


For example, once you create the first Kyma instance with the standard `aws` plan in a non-EU region in your global account, it is automatically assigned to an account provided by Amazon Web Services. After that, all your Kyma instances in all subaccounts within the same global account created with the `aws` or `build-runtime-aws` plans in non-EU regions are assigned to the same Amazon Web Services account. Suppose you have no Kyma instances created in the `aws` EU region in the same global account. In that case, this is your only assignment to an Amazon Web Services account, regardless of the number of existing Kyma instances with the standard `aws` plan. However, if, in the same global account, there are also Kyma instances created with the `aws` or `build-runtime-aws` plans in the `aws` EU region, they are all assigned to another single account provided by Amazon Web Services. Therefore, your Kyma instances in this particular global account are assigned to two IaaS provider accounts. Adding more Kyma instances with other plans results in more assignments to the corresponding IaaS provider accounts.



<a name="loioead08cdb6c20433f8d283e762fe81634__section_igw_lbz_wgc"/>

## IaaS Account Assignments After Subaccount Transfers to Another Global Account

Within SAP Business Technology Platform \(BTP\), you can transfer solutions from one global account to another. See [2498151](https://me.sap.com/notes/2498151). However, the transfer does not affect your Kyma instance\(s\) assignment to IaaS provider accounts. The assignment is permanent and cannot be changed. This is also true when you migrate subaccounts with Kyma instances assigned to a specific IaaS provider account from one global account to another. The original account assignments remain unchanged even if the migrated Kyma instances and those existing in the target global account have the same characteristics.

For example, if you migrate Kyma instances created with the standard service plan `aws`, all assigned to a single account provided by Amazon Web Services, to another global account with existing Kyma instances also created with the standard service plan `aws`, all assigned to another account provided by Amazon Web Services, the assignments remain unchanged. Even though all your Kyma instances in this particular global account share the same characteristics, they remain assigned to two different IaaS provider accounts.

