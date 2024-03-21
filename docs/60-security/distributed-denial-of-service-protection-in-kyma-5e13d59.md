<!-- loio5e13d59686384dc4aa6bb6d89219a997 -->

# Distributed Denial-of-Service Protection in Kyma

A distributed denial-of-service \(DDoS\) attack is a malicious attempt to disrupt the normal traffic of a targeted server, service or network by overwhelming the target or its surrounding infrastructure with a flood of Internet traffic.

With Kyma comes the default DDoS protection offered by the IaaS provider.

**Default DDoS Protection**


<table>
<tr>
<th valign="top">

IaaS Provider

</th>
<th valign="top">

Default DDoS Protection

</th>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Azure DDoS Protection Basic service

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

AWS Shield Standard

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

Standard network DDoS protection

</td>
</tr>
</table>

> ### Remember:  
> Because these are cloud providers' default offerings, they are subject to change as per the cloud providers' terms and conditions.



<a name="loio5e13d59686384dc4aa6bb6d89219a997__section_gr1_l41_tzb"/>

## Web Application Firewalls

It is not possible to configure or enable web application firewalls in SAP BTP, Kyma runtime.

