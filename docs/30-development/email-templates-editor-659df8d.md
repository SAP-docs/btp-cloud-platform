<!-- loio659df8de83524516bbbd5a2a326e1028 -->

# Email Templates Editor

You can create pre-delivered email templates for use with the email API `CL_BCS_MAIL_MESSAGE`.

Use the email template renderer \(see [Email Template Rendering](https://help.sap.com/docs/SAP_S4HANA_CLOUD/6aa39f1ac05441e5a23f484f31e477e7/b11428e38ad043b5bb407e62a5d78ed4.html?locale=en-US&state=DRAFT&version=2602.500)\) or use them as a model for additional email templates in the Fiori app*Maintain Email Templates* \(see [Maintain Email Templates](../50-administration-and-ops/maintain-email-templates-578952e.md)\).

Create new email templates using the editor in the ABAP Development Tools \(ADT\), as shown in the screenshot below.

![](images/Template_Content_28dd522.png)

Each template needs a CDS view to supply data for the placeholders in the emails. The email template also needs a subject and can include a description to clarify its intended use. The CDS view serves as the data source for any copies of the template created in the *Maintain Email Templates* app. Implementation checks ensure that the email template and its CDS view meet the requirements for use.

The email template appears in the logon language.

**Implementation checks**

The CDS view must meet the following criteria:

-   It should either be released for use in language version five or be in the same package as the calling API.
-   The CDS view must be supported and created for use in an email template. You can indicate this by adding the supported capabilities or modeling pattern annotation *OUTPUT\_EMAIL\_DATA\_PROVIDER* to the CDS view. For more details, see the section on [Supported Capabilities for CDS Views](https://help.sap.com/docs/SAP_S4HANA_ON-PREMISE/ee6ff9b281d8448f96b4fe6c89f2bdc8/6a6ff32b25dd473080e6aeddbefecfca.html?locale=en-US).

The email template needs to meet the following criteria:

-   It should be released for use in key user apps or in language version five. Otherwise, local APIs can use it.
-   It must be in the active state, meaning it shouldn't be deprecated or obsolete.

**Email Template Content**

You can maintain the content of an email template using the *Edit* action for both Body HTML and Body Plain Text. This action also lets you import or export the text fields. You must add any changes to the content to a transport request. If the email template is already assigned to a transport request, the *Transport* field is filled and can't be changed. If the *Transport* field is empty, you can choose a transport or use an automatically generated transport.

![](images/Edit_Email_Template_Content_d9a77c9.png)

**Tidy the HTML Content**

To tidy up HTML content, use the *Tidy HTML* action button. This action provides a view of both the current HTML content and a tidied version. To keep the tidied version, click the *OK* button. If the *Transport* field is empty, choose a transport or use an automatically generated one.

![](images/Tidy_HTML_Body_Content_42eee0a.png)

