<!-- loio3bf575a3dc5043f895f8bd411d2a86a1 -->

# Develop, Test, Build

To develop and provide add-ons, you have to set up a suitable system landscape and Cloud Foundry environment account structure.



You need a partner contract to create the account structure. The accounts for the upstream \(add-on development, test, build\) and downstream \(providing add-on as SaaS solution\) parts of the process need to be separated from each other and therefore are handled in dedicated global accounts. We refer to these as global accounts for development and production account. For more information regarding the development license, see [SAP PartnerEdge Test, Demo & Development Price List](https://partneredge.sap.com/en/library/assets/partnership/sales/order_license/pl_pl_part_price_list.html). To find out more about production licenses, see [SAP PartnerEdge: Resources for OEM Partners](https://partneredge.sap.com/en/partnership/manage/op_resource/oem.html).

> ### Tip:  
> For in-depth information about the system landscape/account model, check out [System Landscape/Account Model](concepts-9482e7e.md#loio4ca756395fc24e56a42b77632a6bd862).

For the initial add-on delivery, you should create a development and test landscape following the guidelines mentioned in [Concepts](concepts-9482e7e.md#loio9482e7eef4634cb993a4ae296b2029fa). Once backend and frontend development is completed, you can test the add-on implementation in a persistent test system. Upon successful completion of this step, set up a CI/CD server along with a Jenkins pipeline to execute the add-on build allowing for an automated and efficient assembly. This automated pipeline can then be reused transforming all upgrade and update activities into a straightforward process.

Once the add-on build/assembly is finished, you can release the add-on for installation/update. First, the add-on build is installed in a test system in the global account for development to verify that it works correctly. If successful, you can provide the add-on to customers.

> ### gCTS Delivery:  
> Besides using add-ons for delivering software components to production systems, gCTS transports can be used as an alternative approach. It is used for transporting software components between different ABAP systems.
> 
> See [Delivery via Add-On or gCTS](delivery-via-add-on-or-gcts-438d7eb.md#loio438d7ebfdc4a41de82dcdb156f01857e).

