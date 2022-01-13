<!-- loiocb4f958807e94ea5a2414cd261bcd6e3 -->

# Auditing and Logging Information

Here you can find a list of the security events that are logged by the HTML5 application repository.

<a name="loiocb4f958807e94ea5a2414cd261bcd6e3__table_dqf_pkf_p4b"/>Events written in audit logs


<table>
<tr>
<th valign="top">

Event grouping



</th>
<th valign="top">

What events are logged



</th>
<th valign="top">

How to identify related log events



</th>
<th valign="top">

Additional information



</th>
</tr>
<tr>
<td valign="top" rowspan="2">

Authentication failure



</td>
<td valign="top">

Authentication failed because of an invalid token



</td>
<td valign="top">



</td>
<td valign="top">

Message: *Authentication failure status: 401*



</td>
</tr>
<tr>
<td valign="top">

Authentication failed because of the token has expired



</td>
<td valign="top">



</td>
<td valign="top">

Message: *Authentication failure status: 403* 



</td>
</tr>
<tr>
<td valign="top">

Attempt to access an application with an invalid app-host



</td>
<td valign="top">

Attempt to access an application with invalid app-host



</td>
<td valign="top">

 



</td>
<td valign="top">

Message: *Invalid App Host ID*

If there was an attempt to get an application that was deployed by a developer in another space.



</td>
</tr>
<tr>
<td valign="top">

Attempt to access a private application from another space



</td>
<td valign="top">

Attempt to access a private application from another space



</td>
<td valign="top">

 



</td>
<td valign="top">

Message: *Attempt to access private application. application name :*`'+ appKey + ', app-host : ' + dtServiceInstanceId` 



</td>
</tr>
<tr>
<td valign="top" rowspan="2">

Deletion of an application



</td>
<td valign="top">

Deletion of data started



</td>
<td valign="top">

 



</td>
<td valign="top">

Message: *Deletion of data started for SPACE <space\> in ORG <org\>* 



</td>
</tr>
<tr>
<td valign="top">

Deletion of data completed



</td>
<td valign="top">

 



</td>
<td valign="top">

Message:*Deletion of data completed for SPACE <space\> in ORG <org\>* 



</td>
</tr>
</table>



The following information is described in the table columns:

-   *Event grouping* - Events that are logged with a similar format or are related to the same entities.

-   *What events are logged* - Description of the security or data protection and privacy related event that is logged.

-   *How to identify related log events* - Search criteria or key words, that are specific for a log event that is created along with the logged event.

-   *Additional information* - Any related information that can be helpful.


**Related Information**  


[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/f92c86ab11f6474ea5579d839051c334.html)

[Audit Logging in the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/02c39712c1064c96b37c1ea5bc9420dc.html)

