<!-- loio4f03fd5a172247c7a32f6a1e60f0e815 -->

# Email Templates

An email template is a development object that serves as a predefined layout for generating and automatically sending emails from SAP applications.

Email templates can be created using the editor in ABAP Development Tools \(ADT\) for Eclipse. During template creation, placeholders can be inserted to enable dynamic content, such as recipient names or other message-specific details. At runtime, when emails are generated from the template, these placeholders are automatically replaced with actual values. The placeholders correspond to fields in the referenced Core Data Services \(CDS\) view, and the actual values are determined based on the key values provided during execution. This approach enables the mass distribution of emails with personalized, recipient-specific information.

Each email template is a transportable development object and can include both HTML and plain text content. Once activated, templates are ready to be used for rendering and sending emails.

