<!-- loio4f03fd5a172247c7a32f6a1e60f0e815 -->

# Email Templates

An email template is a development object that contains HTML and/or text content.

These templates can be populated with placeholders during the creation process, either in the *Maintain Email Templates* app or using the backend editor in the ABAP Development Tools \(ADT\). These placeholders are replaced with actual content during runtime when emails are sent out using the template. This allows for the mass sending of emails containing different, recipient-specific data.

The creation of these templates is divided into the two mentioned editors:

**ADT Backend Editor:** This editor is used to create predefined templates that can be utilized for rendering emails and as a basis for further templates within the Maintain Email Templates app. Predelivered templates can only be edited in the backend editor.

**Fiori App Monitor Email Transmission:** This key user app provides the option to create and modify copies of the predefined templates in multiple languages. Only predefined email templates that are released for key user apps and use released CDS views \(with Stability Contract for System-Internal Use \(C1\)\) are visible in this app. Copies of predelivered templates can only be edited in the Fiori app *Maintain Email Templates* and can be transported via ATO transport to non-development systems.

By using these tools, users can efficiently manage and personalize their email communications at scale.

