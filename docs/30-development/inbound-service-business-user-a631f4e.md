<!-- loioa631f4ead22743598f1d14474384beb3 -->

# Inbound Service: Business User



Technical name: `MANAGEBUSINESSUSERIN`

This synchronous inbound SOAP service enables you to create, update, and delete business users from your external data sources, such as an identity management system. Deleting business users doesn't mean you've actually deleted them yet. The user assigned to the business user is deleted and the `MarkedForArchivingIndicator` has been set. Only during the ILM process the business user is physically deleted.

You can assign business role IDs to the users at the node `Role`.

We recommend processing blocks of 10 users to a maximum of 100 users. Otherwise, the target system may time out.

This service supports the business users Employee \(BUP003\).



> ### Caution:  
> This service directly influences the data and authorizations of business users. Changes are effective immediately in the target system.
> 
> Make sure to maintain only those authorizations that are intended for what a user needs to do in the system. Not doing so can cause security issues.



<a name="loioa631f4ead22743598f1d14474384beb3__section_gcn_jn5_qcb"/>

## Service Request

The service is structured into the following two top-level nodes:

**Message Header \(`MessageHeader`\)**

The service message header is not in use in this service.

**Business User \(`BusinessUser`\)**

The service nodes contain the service's business data.

> ### Note:  
> In the following table, attributes are marked in blue.

**Nodes and Fields for the BusinessUser Node**


<table>
<tr>
<th valign="top" colspan="3">

Node or Field

</th>
<th valign="top">

Description

</th>
<th valign="top">

Maximum Field Length

</th>
<th valign="top">

Cardinality

</th>
<th valign="top">

Necessity

</th>
</tr>
<tr>
<td valign="top" colspan="3">

`PersonExternalID` 

</td>
<td valign="top">

The Person External ID is the ID of the employee.

</td>
<td valign="top">

60

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Mandatory for create for business partner category \(`BUP003` - Employee\).

Optional for update \(at least one of the person IDs is mandatory.\)

</td>
</tr>
<tr>
<td valign="top" colspan="3">

`PersonID` 

</td>
<td valign="top">

Person ID is the ID of the business partner.

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

\(At least one of the person IDs is mandatory.\)

</td>
</tr>
<tr>
<td valign="top" colspan="3">

`PersonUUID` 

</td>
<td valign="top">

Person UUID is the unique ID of the business partner.

</td>
<td valign="top">

36

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

\(At least one of the person IDs is mandatory.\)

</td>
</tr>
<tr>
<td valign="top" colspan="3">

`BusinessPartnerRoleCode` 

</td>
<td valign="top">

Business Partner Role Code

</td>
<td valign="top">

6

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Mandatory for create for Business partner category \(`BUP003` - Employee\).

Optional for update.

</td>
</tr>
<tr>
<td valign="top" colspan="3">

`MarkedForArchivingIndicator` 

</td>
<td valign="top">

Mark for Archiving

Set to **True**:

-   The business user will be archived

-   The `actionCode` \[1\] for `User` must be set to 02


Set to **False**:

-   The business user will be reactivated \(Undo Archive\)

-   The `actionCode` \[1\] for `User` must be set to 02




</td>
<td valign="top">

 

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`ValidityPeriod`

Cardinality: 0..1

</td>
<td valign="top" colspan="2">

`StartDate` 

</td>
<td valign="top">

Format:

YYYY-MM-DD

By default, the system date is set.

</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`EndDate` 

</td>
<td valign="top">

Format:

YYYY-MM-DD

By default, 9999-12-31 is set.

</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" rowspan="16">

`PersonalInformation`

Cardinality: 0..1

</td>
<td valign="top" colspan="2">

`FormOfAddress` 

</td>
<td valign="top">

Form of address

</td>
<td valign="top">

4

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`FirstName` 

</td>
<td valign="top">

First name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`LastName` 

</td>
<td valign="top">

Last name

This field is mandatory.

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Mandatory

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`PersonFullName` 

</td>
<td valign="top">

Person full name

</td>
<td valign="top">

80

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`AcademicTitle` 

</td>
<td valign="top">

Academic title

</td>
<td valign="top">

4

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`CorrespondenceLanguage` 

</td>
<td valign="top">

Correspondence language

</td>
<td valign="top">

9

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`MiddleName` 

</td>
<td valign="top">

Middle name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`AdditionalLastName` 

</td>
<td valign="top">

Additional last name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`BirthName` 

</td>
<td valign="top">

Birth name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`NickName` 

</td>
<td valign="top">

Nick name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`Initials` 

</td>
<td valign="top">

Initials

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`AcademicSecondTitle` 

</td>
<td valign="top">

Academic second title

</td>
<td valign="top">

4

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`LastNamePrefix` 

</td>
<td valign="top">

Last name prefix

</td>
<td valign="top">

4

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`LastNameSecondPrefix` 

</td>
<td valign="top">

Last name second prefix

</td>
<td valign="top">

4

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`NameSupplement` 

</td>
<td valign="top">

Name supplement

</td>
<td valign="top">

4

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[2\] is not set and personal information data are given.

</td>
<td valign="top">

2

</td>
<td valign="top">

optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" rowspan="15">

`User` **\(only for Cloud\)**

Cardinality: 0..1

> ### Note:  
> For more information about default values, see [Defaulting of User Attributes](https://launchpad.support.sap.com/#/notes/3089625).



</td>
<td valign="top" colspan="2">

`UserName` 

</td>
<td valign="top">

User name/Alias

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`LogonLanguageCode` 

</td>
<td valign="top">

Logon language

</td>
<td valign="top">

9

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`DateFormatCode` 

</td>
<td valign="top">

You can use the following values:

-   1 - DD.MM.YYYY \(Gregorian Date\)

-   2 - MM/DD/YYYY \(Gregorian Date\)

-   3 - MM-DD-YYYY \(Gregorian Date\)

-   4 - YYYY.MM.DD \(Gregorian Date\)

-   5 - YYYY/MM/DD \(Gregorian Date\)

-   6 - YYYY-MM-DD \(Gregorian Date, ISO 8601\)

-   7 - GYY.MM.DD \(Japanese Date\)

-   8 - GYY/MM/DD \(Japanese Date\)

-   9 - GYY-MM-DD \(Japanese Date\)

-   A - YYYY/MM/DD \(Islamic Date 1\)

-   B - YYYY/MM/DD \(Islamic Date 2\)

-   C - YYYY/MM/DD \(Iranian Date\)




</td>
<td valign="top">

2

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`DecimalFormatCode` 

</td>
<td valign="top">

You can use the following values:

-   1.234.567,89

-   X - 1,234,567.89

-   Y - 1 234 567,89




</td>
<td valign="top">

2

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`TimeZoneCode` 

</td>
<td valign="top">

Time zone

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`TimeFormatCode` 

</td>
<td valign="top">

You can use the following values:

-   0 - 24 Hour Format \(Example: 12:05:10\)

-   1 - 12 Hour Format \(Example: 12:05:10 PM\)

-   2 - 12 Hour Format \(Example: 12:05:10 pm\)

-   3 - Hours from 0 to 11 \(Example: 00:05:10 PM\)

-   4 - Hours from 0 to 11 \(Example: 00:05:10 pm\)




</td>
<td valign="top">

2

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`LockedIndicator` 

</td>
<td valign="top">

Locked indicator

</td>
<td valign="top">

5

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`ValidityPeriod`

Cardinality: 1

</td>
<td valign="top">

`StartDate` 

</td>
<td valign="top">

Format:

YYYY-MM-DD

If the start date is not maintained for the `User`, the `StartDate` for the `BusinessUser` is entered.

</td>
<td valign="top">

 

</td>
<td valign="top">

1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`EndDate` 

</td>
<td valign="top">

Format:

YYYY-MM-DD

If the `EndDate` is not maintained, it is set to 9999-12-31.

</td>
<td valign="top">

 

</td>
<td valign="top">

1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`Role`

Cardinality: 0..unbounded

</td>
<td valign="top">

`RoleName` 

</td>
<td valign="top">

Role name

</td>
<td valign="top">

40

</td>
<td valign="top">

1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top">

`actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   03 - Delete


Mandatory if \[6\] is not set and role name data is given.

</td>
<td valign="top">

2

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

GlobalUserID

</td>
<td valign="top">

Used to uniquely identify your business user across different systems.

</td>
<td valign="top">

36

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

UserGroupCode

</td>
<td valign="top">

Assign a business user to an existing user group.

</td>
<td valign="top">

12

</td>
<td valign="top">

0..1

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[3\] is not set and user data \(`UserName` and `Role`\) are given.

</td>
<td valign="top">

2

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="2">

\[6\] `roleListCompleteTransmissionIndicator` 

</td>
<td valign="top">

CTI for the `Role` node

See [CTI note](inbound-service-business-user-a631f4e.md#loioa631f4ead22743598f1d14474384beb3__CTI_Note) for more information.

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`UserAssignment` **\(only for on-premise\)**

Cardinality: 0..1

</td>
<td valign="top" colspan="2">

`UserID` 

</td>
<td valign="top">

User ID

</td>
<td valign="top">

12

</td>
<td valign="top">

1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[4\] is not set and User ID data are given.

</td>
<td valign="top">

2

</td>
<td valign="top">

Optional

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" rowspan="13">

`WorkplaceInformation` 

</td>
<td valign="top" colspan="2">

`EmailAddress` 

</td>
<td valign="top">

Email address

</td>
<td valign="top">

241

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" rowspan="6">

`PhoneInformation`

Cardinality: 0..2

One set of phone information per phone type supported.

</td>
<td valign="top">

`PhoneType` 

</td>
<td valign="top">

Phone type

-   B - Business

-   C - Cell




</td>
<td valign="top">

1

</td>
<td valign="top">

1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`CountryDialingCode` 

</td>
<td valign="top">

Country dialing code

Used for both phone types.

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`PhoneNumberAreaID` 

</td>
<td valign="top">

Phone number area code

Used only for phone type B.

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`PhoneNumberSubscriberID` 

</td>
<td valign="top">

Phone number subscriber ID

Used for both phone types.

</td>
<td valign="top">

30

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`PhoneNumberExtension` 

</td>
<td valign="top">

Phone number extension

Used only for phone type B.

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[7\] is not set and phone data is given.

</td>
<td valign="top">

2

</td>
<td valign="top">

Optional

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`FunctionalTitleName` 

</td>
<td valign="top">

Functional title name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`Department` 

</td>
<td valign="top">

Department name

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`RoomNumber` 

</td>
<td valign="top">

Room number

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`Building` 

</td>
<td valign="top">

Building name

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[5\] is not set and workplace information data is given.

</td>
<td valign="top">

2

</td>
<td valign="top">

Optional

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

\[7\] `phoneInformationListCompleteTransmissionIndicator` 

</td>
<td valign="top">

CTI for the `PhoneInformation` node

See [CTI note](inbound-service-business-user-a631f4e.md#loioa631f4ead22743598f1d14474384beb3__CTI_Note) for more information.

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" rowspan="10">

`Relationship`\(only for on-premise\)

</td>
<td valign="top" rowspan="4">

`Partner1` 

</td>
<td valign="top">

`BusinessPartnerID` 

</td>
<td valign="top">



</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`BusinessPartnerUUID` 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`BusinessPartnerExternalID` 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`BusinessPartnerExternalIDCategoryCode` 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

 

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

`Partner2` 

</td>
<td valign="top">

`BusinessPartnerID` 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`BusinessPartnerUUID` 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`BusinessPartnerExternalID` 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top">

`BusinessPartnerExternalIDCategoryCode` 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`RelationshipCategoryCode` 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`actionCode` 

</td>
<td valign="top">



</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

N/A

</td>
</tr>
<tr>
<td valign="top" colspan="3">

\[1\] `actionCode` 

</td>
<td valign="top">

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


This attribute is mandatory.

</td>
<td valign="top">

2

</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="3">

\[2\] `personalInformationListCompleteTransmissionIndicator` 

</td>
<td valign="top">

CTI for the `PersonalInformation` node

See [CTI note](inbound-service-business-user-a631f4e.md#loioa631f4ead22743598f1d14474384beb3__CTI_Note) for more information.

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="3">

\[3\] `userListCompleteTransmissionIndicator` 

</td>
<td valign="top">

CTI for the `User` node

See [CTI note](inbound-service-business-user-a631f4e.md#loioa631f4ead22743598f1d14474384beb3__CTI_Note) for more information.

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="3">

\[4\] `userAssignmentListCompleteTransmissionIndicator` 

</td>
<td valign="top">

CTI for the `UserAssignment` node

See [CTI note](inbound-service-business-user-a631f4e.md#loioa631f4ead22743598f1d14474384beb3__CTI_Note) for more information.

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="3">

\[5\] `workplaceInformationListCompleteTransmissionIndicator` 

</td>
<td valign="top">

CTI for the `WorkplaceInformation` node

See [CTI note](inbound-service-business-user-a631f4e.md#loioa631f4ead22743598f1d14474384beb3__CTI_Note) for more information.

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
<tr>
<td valign="top" colspan="3">

\[5\] `relationshipListCompleteTransmissionIndicator` 

</td>
<td valign="top">

 

</td>
<td valign="top">



</td>
<td valign="top">

Optional

</td>
<td valign="top">

Optional

</td>
</tr>
</table>

> ### Note:  
> **Complete Transmission Indicator \(CTI\)**
> 
> The complete transmission indicator represents the state of the data in the inbound XML There are multiple transmission indicators that represents the state of the corresponding segment. The transmission indicator is interpreted by the web service:
> 
> -   If a complete transmission indicator is set to true, the existing data is overwritten by the newly entered data.
> -   If a complete transmission indicator is set to false, the value of the action code of the corresponding node applies.
> 
> -   If an action code and the complete transmission indicator are set, then the action code of the corresponding node applies.



### Sample Payload

> ### Sample Code:  
> ```
> <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:aba="http://sap.com/xi/ABA">
>    <soapenv:Header/>
>    <soapenv:Body>
>       <aba:BusinessUserBundleMaintainRequest_sync>
>           <!--1 or more repetitions:-->
>          <BusinessUser actionCode="01" personalInformationListCompleteTransmissionIndicator="false" userListCompleteTransmissionIndicator="false" userAssignmentListCompleteTransmissionIndicator="false" workplaceInformationListCompleteTransmissionIndicator="false">
>             <PersonExternalID>Muster01</PersonExternalID>
>             <BusinessPartnerRoleCode>BUP003</BusinessPartnerRoleCode>
>             <PersonalInformation actionCode="01">
>                <FormOfAddress>0002</FormOfAddress>
>                <FirstName>Max</FirstName>
>                <LastName>Muster</LastName>
>                <PersonFullName>Prof. Dr. Max Muster</PersonFullName>
>                <AcademicTitle>0002</AcademicTitle>
>               
>                <CorrespondenceLanguage>D</CorrespondenceLanguage>
>                <MiddleName>Michael</MiddleName>
>                <AcademicSecondTitle>0001</AcademicSecondTitle>
>                <BirthName>Milli</BirthName>
>                <NickName>Maxi</NickName>
>                <LastNamePrefix>0001</LastNamePrefix>
>             </PersonalInformation>
>             <User actionCode="01" roleListCompleteTransmissionIndicator="false">
>                <!--Optional:-->
>                <UserName>MAXMUSTER01</UserName>
>                <LogonLanguageCode>DE</LogonLanguageCode>
>                <LockedIndicator>false</LockedIndicator>
>                <Role actionCode="01">
>                   <RoleName>SAP_BR_MANAGER</RoleName>
>                </Role>
>                <Role actionCode="01">
>                   <RoleName>SAP_BR_BPC_EXPERT</RoleName>
>                </Role> 
>             </User>
>             <WorkplaceInformation actionCode="01" phoneInformationListCompleteTransmissionIndicator="true">
>                <EmailAddress>Max.Muster01@Test.com</EmailAddress>
>                <PhoneInformation actionCode="01">
>                   <PhoneType>C</PhoneType>
>                   <CountryDialingCode>+49</CountryDialingCode>
>                   <PhoneNumberSubscriberID>0160123456</PhoneNumberSubscriberID>
>                </PhoneInformation>
>                <PhoneInformation actionCode="01">
>                   <PhoneType>B</PhoneType>
>                   <CountryDialingCode>+49</CountryDialingCode>
>                   <PhoneNumberAreaID>06227</PhoneNumberAreaID>
>                   <PhoneNumberSubscriberID>7</PhoneNumberSubscriberID>
>                   <PhoneNumberExtension>12345</PhoneNumberExtension>
>                </PhoneInformation>
>                <FunctionalTitleName>TESTER</FunctionalTitleName>
>                <Department>QUALITY</Department>
>                <RoomNumber>C1.23</RoomNumber>
>                <Building>WDF01</Building>
>             </WorkplaceInformation>
>          </BusinessUser>
>          <BusinessUser actionCode="01" personalInformationListCompleteTransmissionIndicator="false" userListCompleteTransmissionIndicator="false" userAssignmentListCompleteTransmissionIndicator="false" workplaceInformationListCompleteTransmissionIndicator="false">
>             <PersonExternalID>MINIMUSTER01</PersonExternalID>
>             <BusinessPartnerRoleCode>BUP003</BusinessPartnerRoleCode>
>             <PersonalInformation actionCode="01">
>                <FormOfAddress>0001</FormOfAddress>
>                <FirstName>Mini</FirstName>
>                <LastName>Muster</LastName>
>                <PersonFullName>Prof. Dr. Mini Muster</PersonFullName>
>                <AcademicTitle>0002</AcademicTitle>
>                <CorrespondenceLanguage>D</CorrespondenceLanguage>
>                <AcademicSecondTitle>0001</AcademicSecondTitle>
>                <LastNamePrefix>0001</LastNamePrefix>
>             </PersonalInformation>
>             <User actionCode="01" roleListCompleteTransmissionIndicator="false">
>                <!--Optional:-->
>                <UserName>MINIMUSTER01</UserName>
>                <LogonLanguageCode>DE</LogonLanguageCode>
>                <LockedIndicator>false</LockedIndicator>
>                <Role actionCode="01">
>                   <RoleName>SAP_BR_MANAGER</RoleName>
>                </Role>
>                <Role actionCode="01">
>                   <RoleName>SAP_BR_BPC_EXPERT</RoleName>
>                </Role> 
>             </User>
>             <WorkplaceInformation actionCode="01" phoneInformationListCompleteTransmissionIndicator="true">
>                <EmailAddress>Mini.Muster01@Test.com</EmailAddress>
>                <PhoneInformation actionCode="01">
>                   <PhoneType>C</PhoneType>
>                   <CountryDialingCode>+49</CountryDialingCode>
>                   <PhoneNumberSubscriberID>0160123456</PhoneNumberSubscriberID>
>                </PhoneInformation>
>                <PhoneInformation actionCode="01">
>                   <PhoneType>B</PhoneType>
>                   <CountryDialingCode>+49</CountryDialingCode>
>                   <PhoneNumberAreaID>06227</PhoneNumberAreaID>
>                   <PhoneNumberSubscriberID>7</PhoneNumberSubscriberID>
>                   <PhoneNumberExtension>12345</PhoneNumberExtension>
>                </PhoneInformation>
>                <FunctionalTitleName>TESTER</FunctionalTitleName>
>                <Department>QUALITY</Department>
>                <RoomNumber>C1.23</RoomNumber>
>                <Building>WDF01</Building>
>             </WorkplaceInformation>
>          </BusinessUser>
>       </aba:BusinessUserBundleMaintainRequest_sync>
>    </soapenv:Body>
> </soapenv:Envelope>
> ```



<a name="loioa631f4ead22743598f1d14474384beb3__section_jg1_p45_qcb"/>

## Service Response

You receive a confirmation message response for each bundle of business users you send. If the service request is processed, a confirmation message is sent. This contain crucial information provided by the fields `PersonExternalID`, `PersonID`, and `PersonUUID` for each business user of the bundle.

The following table provides an overview of the response structure for the `BusinessUser` service node.


<table>
<tr>
<th valign="top" colspan="3">

Field or Node

</th>
<th valign="top">

Description

</th>
<th valign="top">

Maximum Field Length

</th>
<th valign="top">

Cardinality

</th>
</tr>
<tr>
<td valign="top" colspan="3">

`PersonExternalID` 

</td>
<td valign="top">

Person External ID

</td>
<td valign="top">

60

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top" colspan="3">

`PersonID` 

</td>
<td valign="top">

Person ID

</td>
<td valign="top">

10

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top" colspan="3">

`PersonUUID` 

</td>
<td valign="top">

Person UUID

</td>
<td valign="top">

36

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top" rowspan="7">

`Log`

Cardinality: 1

</td>
<td valign="top" colspan="2">

`BusinessDocumentProcessingResultCode` 

</td>
<td valign="top">

Not in use

</td>
<td valign="top">

2

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top" colspan="2">

`MaximumLogItemSeverityCode` 

</td>
<td valign="top">

If several messages are stored for a business user, the maximum of all received severity codes the most severe level will be shown.

</td>
<td valign="top">

1

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top" rowspan="5">

`Item`

Cardinality: 0..unbounded

</td>
<td valign="top">

`TypeID` 

</td>
<td valign="top">

Message number

</td>
<td valign="top">

40

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top">

`CategoryCode` 

</td>
<td valign="top">

Not in use

</td>
<td valign="top">

15

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top">

`SeverityCode` 

</td>
<td valign="top">

Severity code definition:

-   1 - Information

-   2 - Warning

-   3 - Error




</td>
<td valign="top">

1

</td>
<td valign="top">

0..1

</td>
</tr>
<tr>
<td valign="top">

`Note` 

</td>
<td valign="top">

Contains the message texts.

</td>
<td valign="top">

200

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

`WebURI` 

</td>
<td valign="top">

Not in use

</td>
<td valign="top">



</td>
<td valign="top">

0..1

</td>
</tr>
</table>

**Error Codes**

****


<table>
<tr>
<th valign="top">

Error Code

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

104

</td>
<td valign="top">

Combination of Ext. ID &1 and ID &2 inconsistent. Processing cancelled.

`PersonExternalID` and `PersonID` have a 1:1 relationship. Enter the`PersonID` that corresponds with the `PersonExternalID`.

</td>
</tr>
<tr>
<td valign="top">

105

</td>
<td valign="top">

Combination of Ext. ID &1 and UUID &2 inconsistent.

`Person ExternalID` and `PersonUUID` have a 1:1 relationship.

Enter the`PersonUUID` that corresponds with the `PersonExternalID`

</td>
</tr>
</table>



<a name="loioa631f4ead22743598f1d14474384beb3__section_x5f_w45_qcb"/>

## Constraints

This service does not support:

-   Freelancer \(BBP010\) business users




<a name="loioa631f4ead22743598f1d14474384beb3__section_vnt_d3v_jlb"/>

## Additional Information

> ### Note:  
> For more details about Communication Management, see [Communication Management](../50-administration-and-ops/communication-management-2e84a10.md).

