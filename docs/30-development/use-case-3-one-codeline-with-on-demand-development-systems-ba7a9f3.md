<!-- loioba7a9f3031b442dfb2ca09f3980e1c1e -->

# Use Case 3: One Codeline with On-Demand Development Systems

You can apply this setup if you have:

-   Small development projects \(for example one SAP Fiori application, one developer\)
-   Occasional development activities \(for example after an initial development phase, it is expected to only implement new features on a yearly basis\)

The ABAP system landscape consists of a permanent production system and an on-demand development system.

![](images/Production_ABAP_system_and_an_on-demand_development_ABAP_system_d7688a6.png)

The advantage of this setup is that you have to administer few systems and only pay for the development system during the development periods. The payment model according to the lifetime of a system requires an SAP BTP enterprise agreement contract.

The disadvantages of this setup are that de-commissioning the development system means losing the change history as well as the configuration and application data.

The user base and authorizations have to be set up each time the development system is provisioned.

Not testing with a transported version of the solution always comes with the risk of forgetting to transport an object. This can be avoided by testing in the development system on the release branch.

A much more production-like test can only be ensured in a non-development system, where the objects of the solution are initially created and changed by pulls, and where there is no authorization automatism for testing, see tester role in [Required Business Roles](required-business-roles-01c96ed.md).

We thus strongly recommend developing with [Use Case 1: One Codeline in a 3-System Landscape](use-case-1-one-codeline-in-a-3-system-landscape-2276142.md) instead of use case 3. The quality assurance system might be de-/commissioned on demand then.



<a name="loioba7a9f3031b442dfb2ca09f3980e1c1e__section_ysx_fhb_xlb"/>

## For the Go Live

**Starting situation:** 

-   A \(temporary\) development system is set up
-   The production system is set up
-   Both systems are based on the main branch


<table>
<tr>
<th valign="top">

Step



</th>
<th valign="top">

System



</th>
<th valign="top">

Role



</th>
<th valign="top">

Task



</th>
<th valign="top">

Tool



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

DEV, PRD



</td>
<td valign="top">

System Administrator



</td>
<td valign="top">

Provision a development and a production system



</td>
<td valign="top">

SAP BTP cockpit 



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

DEV, PRD



</td>
<td valign="top">

User Administrator



</td>
<td valign="top">

Create users and maintain roles



</td>
<td valign="top">

*Maintain Business Users* and *Maintain Business Roles* app



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Create a software component of type *Development* and, if required, a software component of type *Business Configuration*. Pull the software component\(s\) into the development system.



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

PRD



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Pull the \(empty\) software component\(s\) into the production system



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

5a



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Develop new functional requirements or correct existing functionalities. All required changes are collected in Workbench transport requests



</td>
<td valign="top">

ABAP Development Tools for Eclipse



</td>
</tr>
<tr>
<td valign="top">

5b



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Business Configuration Expert



</td>
<td valign="top">

Maintain business configuration. All changes are collected in customizing transport requests.



</td>
<td valign="top">

*Maintain Business Configurations* app



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Tester



</td>
<td valign="top">

Test the change and report the test results



</td>
<td valign="top">

ABAP Development Tools for Eclipse with and custom SAP Fiori apps as well as external test tools

External documentation tool



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

If changes are required, repeat steps 5-6



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Release decision: the changes are successfully tested and approved.



</td>
<td valign="top">

External documentation tool



</td>
</tr>
<tr>
<td valign="top">

8



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Release the transport request\(s\)



</td>
<td valign="top">

ABAP Development Tools for Eclipse: Transport Organizer or *Export Customizing Transports* app



</td>
</tr>
<tr>
<td valign="top">

9



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Create a release branch YYYY-<nn\> for each software component



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

10



</td>
<td valign="top">

PRD



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Check out the release branch YYYY-<nn\> of each software component



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

11



</td>
<td valign="top">

DEV



</td>
<td valign="top">

System Administrator



</td>
<td valign="top">

De-provision system DEV



</td>
<td valign="top">

SAP BTP cockpit



</td>
</tr>
</table>



<a name="loioba7a9f3031b442dfb2ca09f3980e1c1e__section_erx_z4b_xlb"/>

## Productive Usage

-   The production ABAP system is based on the main branch
-   Since no development can be performed in the production ABAP system, a temporary development ABAP system must be set up if occasional development is required



<a name="loioba7a9f3031b442dfb2ca09f3980e1c1e__section_wkr_dpb_xlb"/>

## Occasional Development

-   The production ABAP system is based on the main branch
-   A temporary development ABAP system is set up
    -   All software components are imported



<table>
<tr>
<th valign="top">

Step



</th>
<th valign="top">

System



</th>
<th valign="top">

Role



</th>
<th valign="top">

Task



</th>
<th valign="top">

Tool



</th>
</tr>
<tr>
<td valign="top">

1



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Provision a new development system



</td>
<td valign="top">

SAP BTP cockpit



</td>
</tr>
<tr>
<td valign="top">

2



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Create users, maintain and assign roles



</td>
<td valign="top">

*Manage Business Users* and *Manage Business Roles* app



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Import main branch of each software component into the newly provisioned development system



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

4a



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Develop features. All required changes are collected in Workbench transport requests.



</td>
<td valign="top">

ADT for Eclipse



</td>
</tr>
<tr>
<td valign="top">

4b



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Business Configuration Expert



</td>
<td valign="top">

Maintain business configuration. All changes are collected in customizing transport requests.



</td>
<td valign="top">

*Maintain Business Configurations* app



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Release all transport requests



</td>
<td valign="top">

ADT for Eclipse: Transport Organizer or *Export Customizing Transports* app



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Tester



</td>
<td valign="top">

Test new developments/fixes



</td>
<td valign="top">

ADT for Eclipse and custom SAP Fiori apps as well as external test tools



</td>
</tr>
<tr>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

 



</td>
<td valign="top">

If changes are required, repeat steps 3-5



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

PRD



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Pull the main branch of each software component into system PRD



</td>
<td valign="top">

Manage Software Components app



</td>
</tr>
<tr>
<td valign="top">

8



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Delete the development system



</td>
<td valign="top">

SAP BTP cockpit



</td>
</tr>
</table>

