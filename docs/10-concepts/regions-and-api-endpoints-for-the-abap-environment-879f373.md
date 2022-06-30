<!-- loio879f37370d9b45e99a16538e0f37ff2c -->

# Regions and API Endpoints for the ABAP Environment



<a name="loio879f37370d9b45e99a16538e0f37ff2c__table_cb4_gj4_lpb"/>Regions for Enterprise Accounts


<table>
<tr>
<th valign="top">

IaaS Provider



</th>
<th valign="top">

Region



</th>
<th valign="top">

Region Name



</th>
<th valign="top">

Technical Key



</th>
<th valign="top">

Technical Key of IaaS Provider



</th>
<th valign="top">

NAT IPs \(egress, IPs for requests from an ABAP System\)



</th>
<th valign="top">

API Endpoint



</th>
<th valign="top">

Domain



</th>
<th valign="top">

Cockpit Logon



</th>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

eu10



</td>
<td valign="top">

Europe \(Frankfurt\)



</td>
<td valign="top">

cf-eu10



</td>
<td valign="top">

eu-central-1



</td>
<td valign="top">

18.184.119.149, 18.184.95.49, 18.197.217.237, 18.198.153.44, 18.157.206.182



</td>
<td valign="top">

api.cf.eu10.hana.ondemand.com



</td>
<td valign="top">

eu10.hana.ondemand.com



</td>
<td valign="top">

[Feature Set A](https://account.eu2.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-eu10)

[Feature Set B](https://cockpit.eu10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

jp10



</td>
<td valign="top">

Japan \(Tokyo\)



</td>
<td valign="top">

cf-jp10



</td>
<td valign="top">

ap-northeast-1



</td>
<td valign="top">

13.112.212.221, 3.115.119.177, 35.75.28.56, 35.74.196.78, 35.74.158.17



</td>
<td valign="top">

api.cf.jp10.hana.ondemand.com



</td>
<td valign="top">

jp10.hana.ondemand.com



</td>
<td valign="top">

[Feature Set A](https://account.jp1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-jp10)

[Feature Set B](https://cockpit.jp10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

us10



</td>
<td valign="top">

US East \(VA\)



</td>
<td valign="top">

cf-us10



</td>
<td valign="top">

us-east-1



</td>
<td valign="top">

34.226.95.216, 52.5.218.33, 54.243.29.110, 18.215.92.120, 34.232.200.153



</td>
<td valign="top">

api.cf.us10.hana.ondemand.com



</td>
<td valign="top">

us10.hana.ondemand.com



</td>
<td valign="top">

[Feature Set A](https://account.us1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-us10)

[Feature Set B](https://cockpit.us10.hana.ondemand.com/)



</td>
</tr>
</table>

<a name="loio879f37370d9b45e99a16538e0f37ff2c__table_db4_gj4_lpb"/>Regions for Trial Accounts


<table>
<tr>
<th valign="top">

IaaS Provider



</th>
<th valign="top">

Region



</th>
<th valign="top">

Region Name



</th>
<th valign="top">

Technical Key



</th>
<th valign="top">

Technical Key of IaaS Provider



</th>
<th valign="top">

Trial NAT IPs \(egress, IPs for requests from a Cloud Foundry app\)



</th>
<th valign="top">

API Endpoint



</th>
<th valign="top">

Domain



</th>
<th valign="top">

Cockpit Logon



</th>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

eu10



</td>
<td valign="top">

Europe \(Frankfurt\)



</td>
<td valign="top">

cf-eu10



</td>
<td valign="top">

eu-central-1



</td>
<td valign="top">

3.124.22.250, 3.124.41.239, 52.29.53.204



</td>
<td valign="top">

api.cf.eu10.hana.ondemand.com



</td>
<td valign="top">

eu10.hana.ondemand.com



</td>
<td valign="top">

 [Trial](https://cockpit.eu10.hana.ondemand.com/trial) 



</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services



</td>
<td valign="top">

us10



</td>
<td valign="top">

US East \(VA\)



</td>
<td valign="top">

cf-us10



</td>
<td valign="top">

us-east-1



</td>
<td valign="top">

3.218.99.154, 52.72.147.227, 3.218.112.63



</td>
<td valign="top">

api.cf.us10.hana.ondemand.com



</td>
<td valign="top">

us10.hana.ondemand.com



</td>
<td valign="top">

[Trial](https://cockpit.us10.hana.ondemand.com/trial)



</td>
</tr>
</table>

> ### Restriction:  
> Trial accounts and subaccounts on trial can no longer be created on eu10, Europe \(Frankfurt\).
> 
> Existing trial accounts and subaccounts are not affected.

> ### Caution:  
> Some customer contracts include EU access, which means that we only use European subprocessors to access personal data in cloud services, such as when we provide support. We currently cannot guarantee EU access in the ABAP environment. If your contract includes EU access, we cannot move services to the ABAP environment, without changing your contract.

