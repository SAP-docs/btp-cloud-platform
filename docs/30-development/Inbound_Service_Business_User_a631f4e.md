<!-- loioa631f4ead22743598f1d14474384beb3 -->

# Inbound Service: Business User



Technical name: `MANAGEBUSINESSUSERIN`

This synchronous inbound SOAP service enables you to create, update, and delete business users from your external data sources, such as an identity management system. Deleting business users doesn't mean you've actually deleted them yet. The user assigned to the business user is deleted and the `MarkedForArchivingIndicator` has been set. This is the prerequisite for the ILM process that physically deletes business users.

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

<a name="loioa631f4ead22743598f1d14474384beb3__table_ljn_ktm_2db"/>Nodes and Fields for the `BusinessUser` Node


<table>
<tr>
<th colspan="3">

Node or Field



</th>
<th>

Description



</th>
<th>

Maximum Field Length



</th>
<th>

Cardinality



</th>
</tr>
<tr>
<td colspan="3">

 `PersonExternalID` 



</td>
<td>

Person External ID

Mandatory for business partner category role BUP003 \(Employee\) at creation.



</td>
<td>

60



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="3">

 `PersonID` 



</td>
<td>

Person ID

At least one of the person IDs is mandatory.



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="3">

 `PersonUUID` 



</td>
<td>

Person UUID

At least one of the person IDs is mandatory.



</td>
<td>

36



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="3">

 `BusinessPartnerRoleCode` 



</td>
<td>

Business Partner Role Code

Only business partner role code BUP003 \(Employee\) is supported.

This field is mandatory.



</td>
<td>

6



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="3">

 `MarkedForArchivingIndicator` 



</td>
<td>

Mark for Archiving

Set to **True**:

-   The business user will be archived

-   The `actionCode` \[1\] for `User` must be set to 02


Set to **False**:

-   The business user will be reactivated \(Undo Archive\)

-   The `actionCode` \[1\] for `User` must be set to 02




</td>
<td>

 



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="2">

`ValidityPeriod`

Cardinality: 0..1



</td>
<td colspan="2">

 `StartDate` 



</td>
<td>

Format:

YYYY-MM-DD

By default, the system date is set.



</td>
<td>



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `EndDate` 



</td>
<td>

Format:

YYYY-MM-DD

By default, 9999-12-31 is set.



</td>
<td>



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="16">

`PersonalInformation`

Cardinality: 0..1



</td>
<td colspan="2">

 `FormOfAddress` 



</td>
<td>

Form of address



</td>
<td>

4



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `FirstName` 



</td>
<td>

First name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `LastName` 



</td>
<td>

Last name

This field is mandatory.



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `PersonFullName` 



</td>
<td>

Person full name



</td>
<td>

80



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `AcademicTitle` 



</td>
<td>

Academic title



</td>
<td>

4



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `CorrespondenceLanguage` 



</td>
<td>

Correspondence language



</td>
<td>

9



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `MiddleName` 



</td>
<td>

Middle name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `AdditionalLastName` 



</td>
<td>

Additional last name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `BirthName` 



</td>
<td>

Birth name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `NickName` 



</td>
<td>

Nick name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `Initials` 



</td>
<td>

Initials



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `AcademicSecondTitle` 



</td>
<td>

Academic second title



</td>
<td>

4



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `LastNamePrefix` 



</td>
<td>

Last name prefix



</td>
<td>

4



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `LastNameSecondPrefix` 



</td>
<td>

Last name second prefix



</td>
<td>

4



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `NameSupplement` 



</td>
<td>

Name supplement



</td>
<td>

4



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[2\] is not set and personal information data are given.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td rowspan="13">

`User`**\(only for Cloud\)**

Cardinality: 0..1



</td>
<td colspan="2">

 `UserName` 



</td>
<td>

User name/Alias



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `LogonLanguageCode` 



</td>
<td>

Logon language



</td>
<td>

9



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `DateFormatCode` 



</td>
<td>

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
<td>

2



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `DecimalFormatCode` 



</td>
<td>

You can use the following values:

-   1.234.567,89

-   X - 1,234,567.89

-   Y - 1 234 567,89




</td>
<td>

2



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `TimeZoneCode` 



</td>
<td>

Time zone



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `TimeFormatCode` 



</td>
<td>

You can use the following values:

-   0 - 24 Hour Format \(Example: 12:05:10\)

-   1 - 12 Hour Format \(Example: 12:05:10 PM\)

-   2 - 12 Hour Format \(Example: 12:05:10 pm\)

-   3 - Hours from 0 to 11 \(Example: 00:05:10 PM\)

-   4 - Hours from 0 to 11 \(Example: 00:05:10 pm\)




</td>
<td>

2



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `LockedIndicator` 



</td>
<td>

Locked indicator



</td>
<td>

5



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="2">

`ValidityPeriod`

Cardinality: 1



</td>
<td>

 `StartDate` 



</td>
<td>

Format:

YYYY-MM-DD

If no start date is maintained for the `User`, the `StartDate` for the `BusinessUser` is entered.



</td>
<td>

 



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `EndDate` 



</td>
<td>

Format:

YYYY-MM-DD

If no `EndDate` is maintained, it is set to 9999-12-31.



</td>
<td>

 



</td>
<td>

1



</td>
</tr>
<tr>
<td rowspan="2">

`Role`

Cardinality: 0..unbounded



</td>
<td>

 `RoleName` 



</td>
<td>

Role name



</td>
<td>

40



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   03 - Delete


Mandatory if \[6\] is not set and role name data is given.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="2">

 `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[3\] is not set and user data \(`UserName` and `Role`\) are given.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="2">

\[6\] `roleListCompleteTransmissionIndicator` 



</td>
<td>

CTI for the `Role` node



</td>
<td>



</td>
<td>

optional



</td>
</tr>
<tr>
<td rowspan="2">

`UserAssignment`**\(only for on-premise\)**

Cardinality: 0..1



</td>
<td colspan="2">

 `UserID` 



</td>
<td>

User ID



</td>
<td>

12



</td>
<td>

1



</td>
</tr>
<tr>
<td colspan="2">

 `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[4\] is not set and User ID data are given.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td rowspan="13">

`WorkplaceInformation`

Cardinality: 0..1



</td>
<td colspan="2">

 `EmailAddress` 



</td>
<td>

Email address



</td>
<td>

241



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="6">

`PhoneInformation`

Cardinality: 0..2

One set of phone information per phone type supported.



</td>
<td>

 `PhoneType` 



</td>
<td>

Phone type

-   B - Business

-   C - Cell




</td>
<td>

1



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `CountryDialingCode` 



</td>
<td>

Country dialing code

Used for both phone types.



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `PhoneNumberAreaID` 



</td>
<td>

Phone number area code

Used for phone type B only.



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `PhoneNumberSubscriberID` 



</td>
<td>

Phone number subscriber ID

Used for both phone types.



</td>
<td>

30



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `PhoneNumberExtension` 



</td>
<td>

Phone number extension

Used for phone type B only.



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[7\] is not set and phone data is given.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="2">

 `FunctionalTitleName` 



</td>
<td>

Functional title name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `Department` 



</td>
<td>

Department name



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `RoomNumber` 



</td>
<td>

Room number



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `Building` 



</td>
<td>

Building name



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


Mandatory if \[5\] is not set and workplace information data is given.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="2">

\[7\] `phoneInformationListCompleteTransmissionIndicator` 



</td>
<td>

CTI for the `PhoneInformation` node



</td>
<td>



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="3">

\[1\] `actionCode` 



</td>
<td>

You can use the following values:

-   01 - Create

-   02 - Update

-   03 - Delete


This attribute is mandatory.



</td>
<td>

2



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="3">

\[2\] `personalInformationListCompleteTransmissionIndicator` 



</td>
<td>

CTI for the `PersonalInformation` node



</td>
<td>



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="3">

\[3\] `userListCompleteTransmissionIndicator` 



</td>
<td>

CTI for the `User` node



</td>
<td>



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="3">

\[4\] `userAssignmentListCompleteTransmissionIndicator` 



</td>
<td>

CTI for the `UserAssignment` node



</td>
<td>



</td>
<td>

optional



</td>
</tr>
<tr>
<td colspan="3">

\[5\] `workplaceInformationListCompleteTransmissionIndicator` 



</td>
<td>

CTI for the `WorkplaceInformation` node



</td>
<td>



</td>
<td>

optional



</td>
</tr>
</table>



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
<th colspan="3">

Field or Node



</th>
<th>

Description



</th>
<th>

Maximum Field Length



</th>
<th>

Cardinality



</th>
</tr>
<tr>
<td colspan="3">

 `PersonExternalID` 



</td>
<td>

Person External ID



</td>
<td>

60



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="3">

 `PersonID` 



</td>
<td>

Person ID



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="3">

 `PersonUUID` 



</td>
<td>

Person UUID



</td>
<td>

36



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="7">

`Log`

Cardinality: 1



</td>
<td colspan="2">

 `BusinessDocumentProcessingResultCode` 



</td>
<td>

Not in use



</td>
<td>

2



</td>
<td>

0..1



</td>
</tr>
<tr>
<td colspan="2">

 `MaximumLogItemSeverityCode` 



</td>
<td>

If several messages are stored for a business user, the maximum of all received severity codes the most severe level will be shown.



</td>
<td>

1



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="5">

`Item`

Cardinality: 0..unbounded



</td>
<td>

 `TypeID` 



</td>
<td>

Message number



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `CategoryCode` 



</td>
<td>

Not in use



</td>
<td>

15



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `SeverityCode` 



</td>
<td>

Severity code definition:

-   1 - Information

-   2 - Warning

-   3 - Error




</td>
<td>

1



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `Note` 



</td>
<td>

Contains the message texts.



</td>
<td>

200



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `WebURI` 



</td>
<td>

Not in use



</td>
<td>



</td>
<td>

0..1



</td>
</tr>
</table>

**Error Codes**

<a name="loioa631f4ead22743598f1d14474384beb3__table_nnf_vtp_jlb"/>


<table>
<tr>
<th>

Error Code



</th>
<th>

Description



</th>
</tr>
<tr>
<td>

104



</td>
<td>

Combination of Ext. ID &1 and ID &2 inconsistent. Processing cancelled.

`PersonExternalID` and `PersonID` have a 1:1 relationship. Enter the`PersonID` that corresponds with the `PersonExternalID`.



</td>
</tr>
<tr>
<td>

105



</td>
<td>

Combination of Ext. ID &1 and UUID &2 inconsistent.

`Person ExternalID` and `PersonUUID` have a 1:1 relationship.

Enter the`PersonUUID` that corresponds with the `PersonExternalID`



</td>
</tr>
</table>



<a name="loioa631f4ead22743598f1d14474384beb3__section_x5f_w45_qcb"/>

## Constraints

This service does not support:

-   Service Performer \(BBP005\) business users

-   Freelancer \(BBP010\) business users




<a name="loioa631f4ead22743598f1d14474384beb3__section_vnt_d3v_jlb"/>

## Additional Information

> ### Note:  
> For more information about the API, choose the *Details* tab on the SAP API Business Hub.
> 
> For more details about Communication Management, see [Communication Management](../50-administration-and-ops/Communication_Management_2e84a10.md).

