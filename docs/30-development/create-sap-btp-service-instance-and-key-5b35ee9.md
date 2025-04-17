<!-- loio5b35ee98403045309bb0f8c7f0c79365 -->

# Create SAP BTP Service Instance and Key

Create a service instance and service key for accessing SAP AI Core, where the large language models in the generative AI hub are hosted. The X.509 service key is created with the downloaded client default certificate of the ABAP system passed as parameter.



<a name="loio5b35ee98403045309bb0f8c7f0c79365__prereq_cw2_s2f_jdc"/>

## Prerequisites

-   You have purchased the license for SAP AI Core.

-   You have an active global account on SAP BTP with access to the SAP BTP cockpit.

    For more information, see [Setting up a Global Account](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/667f34ba9222450491c2b848cd17e189.html).

-   You have subscribed to SAP AI Core.

-   You have already downloaded the client default certificate from the ABAP system. See, [Download Certificate](download-certificate-3645813.md)


<a name="task_o12_p2x_mdc"/>

<!-- task\_o12\_p2x\_mdc -->

## Create Service Instance



<a name="task_o12_p2x_mdc__context_mhx_r2x_mdc"/>

## Context

Once you have an active SAP BTP global account, create a service instance in your SAP BTP subaccount.

> ### Note:  
> This procedure is based on default content and UIs. Depending on your configuration settings, the procedure may be slightly different.



<a name="task_o12_p2x_mdc__steps_dmj_s2x_mdc"/>

## Procedure

To create service instance for SAP AI Core, see [Create a Service Instance](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/create-service-instance).

 > ### Remember:  
> While updating the basic information for your instance, ensure that you choose *Plan* as *Extended*. For more information, see [Service Plans](https://help.sap.com/docs/sap-ai-core/sap-ai-core-service-guide/service-plans)

 <a name="task_tr5_s2x_mdc"/>

<!-- task\_tr5\_s2x\_mdc -->

## Create Service Key



<a name="task_tr5_s2x_mdc__context_t25_xvv_ydc"/>

## Context

Create service key for OAuth 2.0-based authentication.



<a name="task_tr5_s2x_mdc__steps_up2_3md_ndc"/>

## Procedure

1.  On the *Instances and Subscriptions* page, find your new instance that you created and choose *Create Service Key* from the drop-down.

2.  Enter a name for your service key.

3.  Configure binding properties.

    1.  Enter *Binding Name* as SAP\_COM\_0A69\_Skey \(any name of your choice\).

    2.  The parameters you need to set when you create your service key or service binding are the following in JSON format:

        > ### Sample Code:  
        > ```
        > 
        > {
        >   "xsuaa": {
        >     "credential-type": "x509",
        >     "x509": {
        >       "certificate": "<Client-Default-Certificate>",
        >       "ensure-uniqueness": false,
        >       "certificate-pinning": true,
        >       "hide-certificate": true
        >     }
        >   }
        > }
        > ```

        For more information, see [Parameters for Self-Managed X.509 Certificates](https://help.sap.com/docs/btp/sap-business-technology-platform/parameters-for-self-managed-x-509-certificates?state=DRAFT&version=Cloud)


4.  Click *Create*.

5.  Download your service key to save it.




<a name="task_tr5_s2x_mdc__postreq_bnz_pxv_ydc"/>

## Next Steps

Save the service key details to use while creating the communication system and communication arrangement for the integration between ISLM and Generative AI Hub.

