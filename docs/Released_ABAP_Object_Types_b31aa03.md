<!-- loiob31aa03640b940d5981ce2af1cd0a019 -->

# Released ABAP Object Types

The following table contains all the released ABAP object types that can be imported into your ABAP environment tenant.

> ### Note:  
> If you try to import or export objects that are not supported, you receive a warning during the transport operation. The objects that are not released are skipped and not transported. The avoid this, you have to manually copy the ABAP objects to the target system. Note that you have to create these objects using the same name in the target system, unless they already exist. Afterwards, you either have to manually copy the code or reconfigure the objects identically in the target system.


<table>
<tr>
<td>

APIS



</td>
<td>

API Release State of Objects



</td>
</tr>
<tr>
<td>

APLO



</td>
<td>

Application Log Object



</td>
</tr>
<tr>
<td>

AUTH



</td>
<td>

Authorization Check Fields



</td>
</tr>
<tr>
<td>

BDEF



</td>
<td>

Behavior Definition



</td>
</tr>
<tr>
<td>

CLAS



</td>
<td>

Class



</td>
</tr>
<tr>
<td>

CHDO



</td>
<td>

Change Documents Object



</td>
</tr>
<tr>
<td>

DCLS



</td>
<td>

ABAP Data Control Language Sources



</td>
</tr>
<tr>
<td>

DDLS



</td>
<td>

Data Definition Language Source



</td>
</tr>
<tr>
<td>

DDLX



</td>
<td>

CDS Metadata Extensions



</td>
</tr>
<tr>
<td>

DEVC



</td>
<td>

Package



</td>
</tr>
<tr>
<td>

DOMA



</td>
<td>

Domain



</td>
</tr>
<tr>
<td>

DTEL



</td>
<td>

Data Element



</td>
</tr>
<tr>
<td>

ENQU



</td>
<td>

Lock Object



</td>
</tr>
<tr>
<td>

ENHO



</td>
<td>

Enhancement Implementation Object



</td>
</tr>
<tr>
<td>

ENHS



</td>
<td>

Enhancement Spot Implementation Object



</td>
</tr>
<tr>
<td>

FUGR



</td>
<td>

Function Group



</td>
</tr>
<tr>
<td>

FUNC



</td>
<td>

Function Module



</td>
</tr>
<tr>
<td>

INTF



</td>
<td>

Interface



</td>
</tr>
<tr>
<td>

MSAG



</td>
<td>

Message Class



</td>
</tr>
<tr>
<td>

NROB



</td>
<td>

Number Range Object



</td>
</tr>
<tr>
<td>

SCO1



</td>
<td>

Communication Scenario



</td>
</tr>
<tr>
<td>

SCO2



</td>
<td>

Inbound Service



</td>
</tr>
<tr>
<td>

SCO3



</td>
<td>

Outbound Service



</td>
</tr>
<tr>
<td>

SIAD



</td>
<td>

Business Role Template Fiori Space Assignment



</td>
</tr>
<tr>
<td>

SIA1



</td>
<td>

Business Catalog



</td>
</tr>
<tr>
<td>

SIA2



</td>
<td>

Restriction Type



</td>
</tr>
<tr>
<td>

SIA3



</td>
<td>

Authorization Object Extension



</td>
</tr>
<tr>
<td>

SIA5



</td>
<td>

Restriction Field



</td>
</tr>
<tr>
<td>

SIA6



</td>
<td>

IAM: App



</td>
</tr>
<tr>
<td>

SIA7



</td>
<td>

Business Catalog App Assignment



</td>
</tr>
<tr>
<td>

SIA8



</td>
<td>

Business Role Template



</td>
</tr>
<tr>
<td>

SIA9



</td>
<td>

Business Role Template Business Catalog Assignment



</td>
</tr>
<tr>
<td>

SKTD



</td>
<td>

Knowledge Transfer Document



</td>
</tr>
<tr>
<td>

SRVB



</td>
<td>

Service Binding



</td>
</tr>
<tr>
<td>

SRVD



</td>
<td>

Service Definition



</td>
</tr>
<tr>
<td>

SUSH



</td>
<td>

Authorization Default Values



</td>
</tr>
<tr>
<td>

SUSO



</td>
<td>

Authorization Object



</td>
</tr>
<tr>
<td>

TABL



</td>
<td>

Table Definition



</td>
</tr>
<tr>
<td>

TTYP



</td>
<td>

Table Type



</td>
</tr>
<tr>
<td>

XSLT



</td>
<td>

Transformation



</td>
</tr>
</table>



<a name="loiob31aa03640b940d5981ce2af1cd0a019__section_st1_rrk_dhb"/>

## Restrictions

-   All objects imported with abapGit are imported as inactive, except the ones that don’t have an inactive state. Therefore, you have to activate all the imported objects after the import.

    > ### Note:  
    > During the activation process, some objects may depend on other objects which need to be activated beforehand.
    > 
    > Also note that mass activation is not supported.

-   All local changes to ABAP objects that are not saved are overwritten by the import.
-   Open transport requests for any of the imported ABAP objects must be released before they can be changed. Otherwise, they get locked.



<a name="loiob31aa03640b940d5981ce2af1cd0a019__section_sxt_ttv_qjb"/>

## Known Issues

-   Changes in table definitions could lead to data loss.

