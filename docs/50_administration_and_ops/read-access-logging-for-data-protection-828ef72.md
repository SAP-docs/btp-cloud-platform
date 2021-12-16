<!-- loio828ef7239d4a494e8b67bc044186bdbc -->

# Read Access Logging for Data Protection

You can use Read Access Logging \(RAL\) to monitor and log access to personal data. The information provided may include, for example, which business users accessed business partner personal data, and in which time frame.

SAP delivers default configurations, which assign dedicated fields to log domains. A log domain is a category that groups semantically identical or related data fields. Logging occurs for all fields disclosed on the UI that are related to these domains. The domain is displayed in the log.

You can activate or deactivate the available RAL configurations in the *Read Access Logging Configuration* app, or make changes. You should carefully consider which information is relevant for logging. Configure your system to log only what you really control. If you maintain a wide scope of information to be logged, you will end up with a lot of data that will be more difficult to process than if you are more specific in your logging configurations.

The following table lists the log domains that are part of the delivered sample configuration content. You can use these log domains or define your own, according to your needs.


<table>
<tr>
<th valign="top">

Log Domain Name



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

 `BANK` 



</td>
<td valign="top">

Data referring to a bank account



</td>
</tr>
<tr>
<td valign="top">

 `BIOMETRIC`\*



</td>
<td valign="top">

Data referring to biometric data



</td>
</tr>
<tr>
<td valign="top">

 `CRIME`\*



</td>
<td valign="top">

Data referring to criminal or administrative offenses or suspected criminal or administrative offenses



</td>
</tr>
<tr>
<td valign="top">

 `ETHNIC_ORIGIN`\*



</td>
<td valign="top">

Data referring to racial or ethnic origin



</td>
</tr>
<tr>
<td valign="top">

 `GENETIC`\*



</td>
<td valign="top">

Data referring to genetic data



</td>
</tr>
<tr>
<td valign="top">

 `HEALTH`\*



</td>
<td valign="top">

Data referring to health data



</td>
</tr>
<tr>
<td valign="top">

 `POLITICAL_OPINION`\*



</td>
<td valign="top">

Data referring to political opinion



</td>
</tr>
<tr>
<td valign="top">

 `PROFILE`\*



</td>
<td valign="top">

Data which is usually based on profiling like: scoring, rating, unwanted customer



</td>
</tr>
<tr>
<td valign="top">

 `RELIGION`\*



</td>
<td valign="top">

Data referring to religious or philosophical beliefs



</td>
</tr>
<tr>
<td valign="top">

 `SECRECY`\*



</td>
<td valign="top">

Data referring to professional secrecy



</td>
</tr>
<tr>
<td valign="top">

 `SEX_LIFE`\*



</td>
<td valign="top">

Data referring to sex life



</td>
</tr>
<tr>
<td valign="top">

 `SEXUAL_ORIENTATION`\*



</td>
<td valign="top">

Data referring to sexual orientation



</td>
</tr>
<tr>
<td valign="top">

 `SSN` 



</td>
<td valign="top">

Data referring to social security number



</td>
</tr>
<tr>
<td valign="top">

 `TRADE_UNION`\*



</td>
<td valign="top">

Data referring to trade union membership



</td>
</tr>
</table>

These log domains are logged with fields related to business partner \(`BP`\), customer \(`CUSTOMER`\), supplier \(`VENDOR`\), legal entity \(`LEGAL_ENTITY`\), employee \(`EMPLOYEE`\), or student \(`STUDENT`\) because they are only identifiable with this additional personal data. For example,`TRADE_UNION` data requires details on the `EMPLOYEE`.

Log conditions are used, if required, to limit the logging of data \(in technical terms, these fields are considered as **and** conditions\). For example, you could configure RAL to log a field related to the employee in a specific transaction only if the employee’s religion is shown. If this field is only visible on a tab where the employee’s religion is not displayed, access to this field is not logged.

RAL is switched off by default. You can activate it in the respective section of the *Read Access Logging Configuration* app. In the *Read Access Logging: Monitor* app, you can view created logs. If you need a downloaded version of your RAL logs, please contact the Service Center. Also contact the Service Center if you need to create new configurations.



<a name="loio828ef7239d4a494e8b67bc044186bdbc__section_czf_1mh_hdb"/>

## More Information

For more information on Read Access Logging and the related apps, see [Read Access Logging](read-access-logging-5688c3a.md).

