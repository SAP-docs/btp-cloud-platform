<!-- loio535e7af5291e48c18deb717167aaa8ef -->

# Inbound Service: Business User - Read



Technical name: `QUERYBUSINESSUSERIN`

This synchronous inbound SOAP service enables you to provision users from your external data source such as an identity management system in SAP S/4HANA Cloud.



<a name="loio535e7af5291e48c18deb717167aaa8ef__section_gcn_jn5_qcb"/>

## Service Request

The service is structured into the following two top-level nodes:

**Business User \(`BusinessUser`\)**

The service node contains the search parameters.

<a name="loio535e7af5291e48c18deb717167aaa8ef__table_gxy_245_qcb"/>Nodes and Fields for the `BusinessUser` Node


<table>
<tr>
<th colspan="2">

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
<td rowspan="3">

`PersonExternalIdInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryPersonExtId` is set.



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

 `LowerBoundaryPersonExtId` 



</td>
<td>

Employee name



</td>
<td>

60



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `UpperBoundaryPersonExtId` 



</td>
<td>



</td>
<td>

60



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="3">

`PersonIDInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryPersonId` is set.



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

 `LowerBoundaryPersonId` 



</td>
<td>



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

 `UpperBoundaryPersonId` 



</td>
<td>



</td>
<td>

10



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="2">

`BusinessPartnerRoleCodeInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryBusinessPartnerRoleCode` is set.



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

 `LowerBoundaryBusinessPartnerRoleCode` 



</td>
<td>

Only business partner role code BUP003 \(Employee\) is supported.



</td>
<td>

6



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="2">

`MarketForArchivingIndicator`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   True

-   False




</td>
<td>

 



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `LowerBoundaryMarkedForArchivingIndicator` 



</td>
<td>

 



</td>
<td>

1



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="3">

`UserIdInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryUserId` is set.



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

 `LowerBoundaryUserId` 



</td>
<td>



</td>
<td>

12



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `UpperBoundaryUserId` 



</td>
<td>



</td>
<td>

12



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="3">

`UserNameInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryUserName` is set.



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

 `LowerBoundaryUserName` 



</td>
<td>



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

 `UpperBoundaryUserName` 



</td>
<td>



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="3">

`FirstNameInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryFirstName` is set.



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

 `LowerBoundaryFirstName` 



</td>
<td>



</td>
<td>

35



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `UpperBoundaryFirstName` 



</td>
<td>



</td>
<td>

35



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="3">

`LastNameInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

You can use the following values:

-   1- Equal

    No upper boundary value must be set.

-   3 - Between

    Upper boundary value is mandatory.

-   6 - Lower than

    Upper boundary value is optional.

-   7 - Lower equal

    Upper boundary value is optional.

-   8 - Greater than

    Upper boundary value is optional.

-   9 - Greater equal

    Upper boundary value is optional.


This field is mandatory if `LowerBoundaryLastName` is set.



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

 `LowerBoundaryLastName` 



</td>
<td>

 



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

 `UpperBoundaryLastName` 



</td>
<td>

 



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="3">

`EmailAddressInterval`

Cardinality: 0..unbounded



</td>
<td>

 `IntervalBoundaryTypeCode` 



</td>
<td>

 



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

 `LowerBoundaryEmailAddress` 



</td>
<td>



</td>
<td>

241



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `UpperBoundaryEmailAddress` 



</td>
<td>



</td>
<td>

241



</td>
<td>

0..1



</td>
</tr>
</table>

**Query Processing Conditions \(`QueryProcessingConditions`\)**

The service nodes contain the service's business data.

<a name="loio535e7af5291e48c18deb717167aaa8ef__table_rtt_5sh_hdb"/>Fields for the `QueryProcessingConditions` Node


<table>
<tr>
<th>

Field



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
<td>

 `QueryHitsTotalNumberIndicator` 



</td>
<td>

You can use the following values:

-   True

-   False \(default\)




</td>
<td>

 



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `QueryHitsMaximumNumberValue` 



</td>
<td>

Enter the maximum number of hits. If no value is entered, the default is automatically set to 1000.



</td>
<td>

999999999



</td>
<td>

0..1



</td>
</tr>
<tr>
<td>

 `QueryHitsUnlimitedIndicator` 



</td>
<td>

You can use the following values:

-   True

-   False \(default\)


Set **True** to get all data based on selection criteria.



</td>
<td>



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `QueryLastReturnedObjectID` 



</td>
<td>

You can use the following values:

-   True

-   False \(default\)


If `QueryHitsMaximumNumberValue` is set and more data is available, you can set this value to **True**.



</td>
<td>

 



</td>
<td>

0..1



</td>
</tr>
</table>



### Sample Payload

> ### Sample Code:  
> ```
> <soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:aba="http://sap.com/xi/ABA">
>    <soapenv:Header/>
>    <soapenv:Body>
>       <aba:BusinessUserSimpleByElementsQuery_sync>
>          <BusinessUser>
>             <PersonIDInterval>
>                <IntervalBoundaryTypeCode>1</IntervalBoundaryTypeCode>
>                <!--Optional:-->
>                <LowerBoundaryPersonID>9980035943</LowerBoundaryPersonID>
>                <!--Optional:-->
>            </PersonIDInterval>
>                 <BusinessPartnerRoleCodeInterval>
>                <IntervalBoundaryTypeCode>1</IntervalBoundaryTypeCode>
>                <!--Optional:-->
>                <LowerBoundaryBusinessPartnerRoleCode>bup003</LowerBoundaryBusinessPartnerRoleCode>
>             </BusinessPartnerRoleCodeInterval>
>          </BusinessUser>
>          <QueryProcessingConditions>
>             <!--Optional:-->
>             <QueryHitsMaximumNumberValue>1</QueryHitsMaximumNumberValue>
>             <QueryHitsUnlimitedIndicator>false</QueryHitsUnlimitedIndicator>
>          </QueryProcessingConditions>
>       </aba:BusinessUserSimpleByElementsQuery_sync>
>    </soapenv:Body>
> </soapenv:Envelope>
> ```



<a name="loio535e7af5291e48c18deb717167aaa8ef__section_jg1_p45_qcb"/>

## Service Response

**Business User \(`BusinessUser`\)**

> ### Note:  
> The fields below the node `User` will be filled.


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

1



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

1



</td>
</tr>
<tr>
<td colspan="3">

 `BusinessPartnerRoleCode` 



</td>
<td>

Business Partner Role Code



</td>
<td>

6



</td>
<td>

1



</td>
</tr>
<tr>
<td colspan="3">

 `MarkedForArchivingIndicator` 



</td>
<td>

-   True

-   False




</td>
<td>

 



</td>
<td>

1



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



</td>
<td>



</td>
<td>

1



</td>
</tr>
<tr>
<td colspan="2">

 `EndDate` 



</td>
<td>

Format:

YYYY-MM-DD



</td>
<td>



</td>
<td>

1



</td>
</tr>
<tr>
<td rowspan="15">

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
<td rowspan="11">

`User`

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

 `UserName` 



</td>
<td>

User name/Alias



</td>
<td>

40



</td>
<td>

1



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
<td>

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
<td rowspan="2">

`UserAssignment`

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

 `UserName` 



</td>
<td>



</td>
<td>

40



</td>
<td>

0..1



</td>
</tr>
<tr>
<td rowspan="10">

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
<td rowspan="5">

`PhoneInformation`

Cardinality: 0..2

One set of phone information per phone type supported.



</td>
<td>

 `PhoneType` 



</td>
<td>

Phone type



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
</table>

**Response Processing Conditions \(`ResponseProcessingConditions`\)**


<table>
<tr>
<th>

Field



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
<td>

 `HitsTotalNumberValue` 



</td>
<td>

Contains the number of users based on given criteria.



</td>
<td>

999999999



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `ReturnedQueryHitsNumberValue` 



</td>
<td>

Contains the number of found data sets for business users.



</td>
<td>

999999999



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `MoreHitsAvailableIndiactor` 



</td>
<td>

The indicator is set if the query was limited to a number of hits, but more business user data sets are available based on the query.



</td>
<td>



</td>
<td>

1



</td>
</tr>
<tr>
<td>

 `LastReturnedObjectID` 



</td>
<td>

Displays the last row of the found results list, limited by the found hits or by the value given for `QueryHitsMaximumNumberValue`.



</td>
<td>

999999999



</td>
<td>

0..1



</td>
</tr>
</table>

**Log \(`Log`\)**

If errors occur, the log contains the information shown in the table below:


<table>
<tr>
<th colspan="2">

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
<td colspan="2">

`BusinessDocumentProcessingResultCode`



</td>
<td>



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

If several messages are stored for a business user, the maximum of all dropped severity codes worst level will be shown.



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

TypeID



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

CateoryCode



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

SeverityCode



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

Note



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

WebURI



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



<a name="loio535e7af5291e48c18deb717167aaa8ef__section_x5f_w45_qcb"/>

## Constraints

This service does not support:

-   Service Performer \(BBP005\) business users

-   Freelancer \(BBP010\) business users




<a name="loio535e7af5291e48c18deb717167aaa8ef__section_czf_fqf_zkb"/>

## Additional Information

> ### Note:  
> For more information about the API, choose the *Details* tab on the SAP API Business Hub.
> 
> For more details about Communication Management, see [Communication Management](../50-administration-and-ops/Communication_Management_2e84a10.md).

