<!-- loio535e7af5291e48c18deb717167aaa8ef -->

# Inbound Service: Business User - Read



Technical name: `QUERYBUSINESSUSERIN`

This synchronous inbound SOAP service enables you to read users from your external data source such as an identity management system in SAP S/4HANA Cloud.



<a name="loio535e7af5291e48c18deb717167aaa8ef__section_gcn_jn5_qcb"/>

## Service Request

The service is structured into the following two top-level nodes:

**Business User \(`BusinessUser`\)**

The service node contains the search parameters.

**Nodes and Fields for the BusinessUser Node**


<table>
<tr>
<th valign="top" colspan="2">

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
<td valign="top" rowspan="3">

`PersonExternalIDInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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


This field is mandatory if `LowerBoundaryPersonExtID` is set.



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryPersonExtID` 



</td>
<td valign="top">

Employee name



</td>
<td valign="top">

60



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`UpperBoundaryPersonExtID` 



</td>
<td valign="top">



</td>
<td valign="top">

60



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`PersonIDInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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


This field is mandatory if `LowerBoundaryPersonID` is set.



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryPersonID` 



</td>
<td valign="top">



</td>
<td valign="top">

10



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`UpperBoundaryPersonID` 



</td>
<td valign="top">



</td>
<td valign="top">

10



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`BusinessPartnerRoleCodeInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryBusinessPartnerRoleCode` 



</td>
<td valign="top">

Only business partner role code BUP003 \(Employee\) is supported.



</td>
<td valign="top">

6



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`MarkedForArchivingIndicator`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

-   True

-   False




</td>
<td valign="top">

 



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryMarkedForArchivingIndicator` 



</td>
<td valign="top">

 



</td>
<td valign="top">

1



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`UserIDInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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


This field is mandatory if `LowerBoundaryUserID` is set.



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryUserID` 



</td>
<td valign="top">



</td>
<td valign="top">

12



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`UpperBoundaryUserID` 



</td>
<td valign="top">



</td>
<td valign="top">

12



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`UserNameInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryUserName` 



</td>
<td valign="top">



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

`UpperBoundaryUserName` 



</td>
<td valign="top">



</td>
<td valign="top">

40



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`FirstNameInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryFirstName` 



</td>
<td valign="top">



</td>
<td valign="top">

35



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`UpperBoundaryFirstName` 



</td>
<td valign="top">



</td>
<td valign="top">

35



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`LastNameInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

The following values exist:

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
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryLastName` 



</td>
<td valign="top">

 



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

`UpperBoundaryLastName` 



</td>
<td valign="top">

 



</td>
<td valign="top">

40



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" rowspan="3">

`EmailAddressInterval`

Cardinality: 0..unbounded



</td>
<td valign="top">

`IntervalBoundaryTypeCode` 



</td>
<td valign="top">

 



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LowerBoundaryEmailAddress` 



</td>
<td valign="top">



</td>
<td valign="top">

241



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`UpperBoundaryEmailAddress` 



</td>
<td valign="top">



</td>
<td valign="top">

241



</td>
<td valign="top">

0..1



</td>
</tr>
</table>

**Query Processing Conditions \(`QueryProcessingConditions`\)**

The service nodes contain the service's business data.

**Fields for the QueryProcessingConditions Node**


<table>
<tr>
<th valign="top">

Field



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
<td valign="top">

`QueryHitsTotalNumberIndicator` 



</td>
<td valign="top">

The following values exist:

-   True

-   False \(default\)




</td>
<td valign="top">

 



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`QueryHitsMaximumNumberValue` 



</td>
<td valign="top">

Enter the maximum number of hits. If no value is entered, the default is automatically set to 1000.



</td>
<td valign="top">

999999999



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`QueryHitsUnlimitedIndicator` 



</td>
<td valign="top">

The following values exist:

-   True

-   False \(default\)


Set **True** to get all data based on selection criteria.



</td>
<td valign="top">



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`QueryLastReturnedObjectID` 



</td>
<td valign="top">

The following values exist:

-   True

-   False \(default\)


If `QueryHitsMaximumNumberValue` is set and more data is available, you can set this value to **True**.



</td>
<td valign="top">

 



</td>
<td valign="top">

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
>             </PersonIDInterval>
>             <BusinessPartnerRoleCodeInterval>
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

1



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

1



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

1



</td>
</tr>
<tr>
<td valign="top" colspan="3">

`MarkedForArchivingIndicator` 



</td>
<td valign="top">

-   True

-   False




</td>
<td valign="top">

 



</td>
<td valign="top">

1



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



</td>
<td valign="top">



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top" colspan="2">

`EndDate` 



</td>
<td valign="top">

Format:

YYYY-MM-DD



</td>
<td valign="top">



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="15">

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
</tr>
<tr>
<td valign="top" colspan="2">

`LastName` 



</td>
<td valign="top">

Last name



</td>
<td valign="top">

40



</td>
<td valign="top">

0..1



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
</tr>
<tr>
<td valign="top" rowspan="11">

`User` **\(only for Cloud\)**

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
</tr>
<tr>
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

1



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
</tr>
<tr>
<td valign="top" colspan="2">

`DateFormatCode` 



</td>
<td valign="top">

The following values exist:

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
</tr>
<tr>
<td valign="top" colspan="2">

`DecimalFormatCode` 



</td>
<td valign="top">

The following values exist:

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
</tr>
<tr>
<td valign="top" colspan="2">

`TimeFormatCode` 



</td>
<td valign="top">

The following values exist:

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

If no start date is maintained for the `User`, the `StartDate` for the `BusinessUser` is entered.



</td>
<td valign="top">

 



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`EndDate` 



</td>
<td valign="top">

Format:

YYYY-MM-DD

If no `EndDate` is maintained, it is set to 9999-12-31.



</td>
<td valign="top">

 



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

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
</tr>
<tr>
<td valign="top" rowspan="3">

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
</tr>
<tr>
<td valign="top" colspan="2">

`UserName` 



</td>
<td valign="top">



</td>
<td valign="top">

40



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top" colspan="2">

`UserAssignmentStatusCode` 



</td>
<td valign="top">

The following values exist:

-   1 - is reserved

-   2 - is assigned




</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top" rowspan="10">

`WorkplaceInformation`

Cardinality: 0..1



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
</tr>
<tr>
<td valign="top" rowspan="5">

`PhoneInformation`

Cardinality: 0..2

One set of phone information per phone type supported.



</td>
<td valign="top">

`PhoneType` 



</td>
<td valign="top">

Phone type



</td>
<td valign="top">

1



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`CountryDialingCode` 



</td>
<td valign="top">

Country dialing code



</td>
<td valign="top">

10



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`PhoneNumberAreaID` 



</td>
<td valign="top">

Phone number area code



</td>
<td valign="top">

10



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`PhoneNumberSubscriberID` 



</td>
<td valign="top">

Phone number subscriber ID



</td>
<td valign="top">

30



</td>
<td valign="top">

0..1



</td>
</tr>
<tr>
<td valign="top">

`PhoneNumberExtension` 



</td>
<td valign="top">

Phone number extension



</td>
<td valign="top">

10



</td>
<td valign="top">

0..1



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
</tr>
</table>

**Response Processing Conditions \(`ResponseProcessingConditions`\)**


<table>
<tr>
<th valign="top">

Field



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
<td valign="top">

`HitsTotalNumberValue` 



</td>
<td valign="top">

Contains the number of users based on given criteria.



</td>
<td valign="top">

999999999



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`ReturnedQueryHitsNumberValue` 



</td>
<td valign="top">

Contains the number of found data sets for business users.



</td>
<td valign="top">

999999999



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`MoreHitsAvailableIndiactor` 



</td>
<td valign="top">

The indicator is set if the query was limited to a number of hits, but more business user data sets are available based on the query.



</td>
<td valign="top">



</td>
<td valign="top">

1



</td>
</tr>
<tr>
<td valign="top">

`LastReturnedObjectID` 



</td>
<td valign="top">

Displays the last row of the results list limited by the found hits or by the value given for `QueryHitsMaximumNumberValue`.



</td>
<td valign="top">

999999999



</td>
<td valign="top">

0..1



</td>
</tr>
</table>

**Log \(`Log`\)**

If errors occur, the log contains the information shown in the table below:


<table>
<tr>
<th valign="top" colspan="2">

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
<td valign="top" colspan="2">

`BusinessDocumentProcessingResultCode`



</td>
<td valign="top">



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

If several messages are stored for a business user, the most severe level is shown from the maximum of all received severity codes.



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

TypeID



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

CateoryCode



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

SeverityCode



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

Note



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

WebURI



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



<a name="loio535e7af5291e48c18deb717167aaa8ef__section_x5f_w45_qcb"/>

## Constraints

This service does not support:

-   Freelancer \(BBP010\) business users




<a name="loio535e7af5291e48c18deb717167aaa8ef__section_czf_fqf_zkb"/>

## Additional Information

> ### Note:  
> For more details about Communication Management, see [Communication Management](../50-administration-and-ops/communication-management-2e84a10.md).

