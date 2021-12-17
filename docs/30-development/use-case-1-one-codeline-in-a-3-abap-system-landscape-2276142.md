<!-- loio2276142117a54197bb05fb8481c10a08 -->

# Use Case 1: One Codeline in a 3-ABAP-System Landscape

You can apply this setup if you have occasional development activities for larger applications where testing needs to run in parallel to development or should take place in a non-development system to ensure the solution also runs in a non-development system. In this setup, you either need to be able to pause development for a fix that has to be delivered before the next release or you have to deliver fixes as part of the next possible release.

This landscape consists of a development, quality assurance, and production ABAP system.

![](images/One_Codeline_in_a_3-ABAP-System_Landscape_811e489.png)



<a name="loio2276142117a54197bb05fb8481c10a08__section_ltg_rbt_wlb"/>

## For Go Live/Development After Go Live \(Including Deferrable Corrections\)

**Starting situation for Go Live**

The Go Live process is characterized by creating different systems only when needed for the first time, however, you can provision the ABAP systems already beforehand. Furthermore, the software component of a planned solution does not exist from the beginning. The resulting release branch is YYYY-01. Apart from this, the Go Live process does not differ from the release development processes afterwards.

**Starting situation after Go Live**

-   Development ABAP system DEV is based on the main branch
-   Quality Assurance ABAP system QAS and production ABAP system PRD are based on the latest release branch YYYY-<nn\>. In case of a first release after the Go Live, YYYY-<nn\> is YYYY-01


The QAS ABAP system has always the same software state as the PRD ABAP system, unless a new change is tested and released. This means, transport requests are released in DEV ABAP systems only if development is completed and it is planned to import the changes to the production ABAP system.

This process can also be used for deferrable corrections, which do not need to reach production before the next development release. These corrections are handled like regular development.


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

0



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

At Go Live only: Create the software component and pull it initially



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

1a



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Develop new functionality or a deferrable correction. All changes are collected in transport requests



</td>
<td valign="top">

ADT for Eclipse



</td>
</tr>
<tr>
<td valign="top">

1b



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Business Configuration Expert



</td>
<td valign="top">

Maintain business configuration. All changes are collected in transport requests



</td>
<td valign="top">

*Business Configuration* app



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

Release the transport request. The changes are now in the release branch YYYY-<nn\>



</td>
<td valign="top">

ADT for Eclipse: Transport Organizer or *Export Customizing Transports* app



</td>
</tr>
<tr>
<td valign="top">

3



</td>
<td valign="top">

QAS



</td>
<td valign="top">

 



</td>
<td valign="top">

Check out main branch/at Go Live: pull software component into QAS



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

QAS



</td>
<td valign="top">

 



</td>
<td valign="top">

Test the change and report test result



</td>
<td valign="top">

ADT for Eclipse and custom SAP Fiori apps & external test tools

External documentation tool



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

If changes are required, repeat steps 1-4



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

QAS



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Release decision: the changes are successfully tested and approved



</td>
<td valign="top">

External documentation tool



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

QAS



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Create a release branch YYYY-<nn+1\> \(at Go Live: YYYY-01\)



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

7



</td>
<td valign="top">

QAS



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Check out the new release branch YYYY-<nn+1\> \(@Go Live: YYYY-01\) into QAS



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

8



</td>
<td valign="top">

PRD



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Check out the new release branch YYYY-<nn+1\> \(at Go Live: YYYY-01\) into PRD



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
</table>



<a name="loio2276142117a54197bb05fb8481c10a08__section_tnb_gzt_wlb"/>

## Urgent Corrections

-   Development ABAP system DEV is based on the main branch
-   Quality assurance ABAP system QAS and production ABAP system PRD are based on the latest release branch YYYY-<nn\>. In case of a correction after the Go Live before the second release, YYYY-<nn\> is YYYY-01

This process differs from the previous one in the branch it is developed in. As the correction is too urgent to release it with the next development release only, it is done in the release branch. To achieve this separation, all current development activities need to be paused because the DEV ABAP system needs to check out the latest release branch instead of the main branch.


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

Check out the release branch YYYY-<nn\>



</td>
<td valign="top">

Manage Software Components app



</td>
</tr>
<tr>
<td valign="top">

2a



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Developer



</td>
<td valign="top">

Fix existing functionality. All changes are collected in transport requests



</td>
<td valign="top">

ADT for Eclipse



</td>
</tr>
<tr>
<td valign="top">

2b



</td>
<td valign="top">

DEV



</td>
<td valign="top">

Business Configuration Expert



</td>
<td valign="top">

Maintain business configuration. All changes are collected in transport requests



</td>
<td valign="top">

Business Configuration app



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

Release the transport request. The changes are now in the main branch



</td>
<td valign="top">

ADT for Eclipse: Transport Organizer or *Export Customizing Transports* app



</td>
</tr>
<tr>
<td valign="top">

4



</td>
<td valign="top">

QAS



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Pull the software component to get correction into already checked out release branch YYYY-<nn\>



</td>
<td valign="top">

*Manage Software Components* app



</td>
</tr>
<tr>
<td valign="top">

5



</td>
<td valign="top">

QAS



</td>
<td valign="top">

Tester



</td>
<td valign="top">

Test the change and report the test result



</td>
<td valign="top">

ADT for Eclipse and custom SAP Fiori apps as well as external test tools

External documentation tool



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

If changes are required, repeat steps 2-5



</td>
<td valign="top">

 



</td>
</tr>
<tr>
<td valign="top">

6



</td>
<td valign="top">

QAS



</td>
<td valign="top">

Release Manager



</td>
<td valign="top">

Fix is successfully tested and approved



</td>
<td valign="top">

External documentation tool



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

Pull the software component to get correction into already checked out release branch YYYY-<nn\>



</td>
<td valign="top">

*Manage Software Components* app



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

Check out the main branch in DEV



</td>
<td valign="top">

*Manage Software Components* app



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

Developer



</td>
<td valign="top">

Perform the same changes as for the correction in the main branch and release them



</td>
<td valign="top">

ADT for Eclipse



</td>
</tr>
</table>

