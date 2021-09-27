<!-- loio350356d1dc314d3199dca15bd2ab9b0e -->

# Regions

You can deploy applications in different **regions**. Each region represents a geographical location \(for example, Europe, US East\) where applications, data, or services are hosted. 



![Regions](images/Regions_85986d3.png)

Regions are provided either by SAP or by our Infrastructure-as-a-Service \(IaaS\) partners Amazon Web Services \(AWS\), Microsoft Azure, Google Cloud Platform \(GCP\), and Alibaba Cloud. The third-party region providers operate the infrastructure layer of the regions, whereas SAP operates the platform layer and Cloud Foundry.



For an overview of all available regions, see [SAP Discovery Center](https://discovery-center.cloud.sap/#/viewServices): 

![](images/DiscoveryCenter_Regions_0f17380.gif)



<a name="loio350356d1dc314d3199dca15bd2ab9b0e__select-region"/>

## Selecting a Region

A region is chosen at the subaccount level. For each subaccount, you select exactly one region. The selection of a region is dependent on many factors: For example, application performance \(response time, latency\) can be optimized by selecting a region close to the user. For more information, see [Selecting a Region](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/38ecf59cdda64150a102cfaa62d5faab.html#loioabaaf083a6574edc8ad30d9cd9a062f3 "You can deploy applications in different regions. Each region represents a geographical location (for example, Europe, US East) where applications, data, or services are hosted.") :arrow_upper_right:.



<a name="loio350356d1dc314d3199dca15bd2ab9b0e__deploy-applications"/>

## Deploying Applications in Regions

When deploying applications, consider that a subaccount is associated with a particular region and that this is independent of your own location. You may be located in the United States, for example, but operate your subaccount in a region in Europe. For more information on subaccounts, see [Subaccounts](Account_Model_8ed4a70.md#loio8d6e3a0fa4ab43e4a421d3ed08128afa).

To deploy an application in more than one region, execute the deployment separately for each host. For more information, see [Deploy an Application](../50-administration-and-ops/Deploy_an_Application_09fdb9b.md).



<a name="loio350356d1dc314d3199dca15bd2ab9b0e__access-cockpit"/>

## Accessing the SAP BTP Cockpit

When accessing the SAP BTP cockpit, be aware that your global account can be using either cloud management tools feature set A or B.

When using cloud management tools feature set A: Choose [https://account.eu1.hana.ondemand.com](https://account.eu1.hana.ondemand.com) to access the cockpit.

When using cloud management tools feature set B: Choose [https://cockpit.eu10.hana.ondemand.com/cockpit/](https://cockpit.eu10.hana.ondemand.com/cockpit/) to access the cockpit.

For more information, see [Cloud Management Tools — Feature Set Overview](Cloud_Management_Tools_—_Feature_Set_Overview_caf4e4e.md).

 <a name="loio350356d1dc314d3199dca15bd2ab9b0e loiof344a57233d34199b2123b9620d0bb41__loiof344a57233d34199b2123b9620d0bb41"/>

<!-- loiof344a57233d34199b2123b9620d0bb41 -->

# Regions and API Endpoints Available for the Cloud Foundry Environment



<a name="loio350356d1dc314d3199dca15bd2ab9b0e loiof344a57233d34199b2123b9620d0bb41__table_cb4_gj4_lpb"/>Regions for Enterprise Accounts


<table>
<tr>
<th>

IaaS Provider



</th>
<th>

Region



</th>
<th>

Region Name



</th>
<th>

Technical Key



</th>
<th>

Technical Key of IaaS Provider



</th>
<th>

NAT IPs \(egress, IPs for requests from a Cloud Foundry app\)



</th>
<th>

LB IPs \(ingress, for incoming requests\)



</th>
<th>

API Endpoint



</th>
<th>

Domain



</th>
<th>

Cockpit Logon



</th>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

eu20



</td>
<td>

Europe \(Netherlands\)



</td>
<td>

cf-eu20



</td>
<td>

West Europe



</td>
<td>

52.149.67.35, 20.82.96.175, 20.82.96.178, 20.82.96.211, 20.82.96.244, 20.82.96.220, 20.82.96.227, 20.82.97.50, 20.82.96.240, 20.82.96.234, 20.82.97.38, 20.82.96.222, 20.82.96.233, 20.82.96.248, 20.82.97.31, 20.82.97.45, 52.149.96.147, 20.56.169.152, 20.56.169.69, 20.56.169.0, 20.56.169.41, 20.56.169.58, 20.56.169.161, 20.56.169.116, 20.56.169.167, 20.56.169.50, 20.56.169.175, 20.56.169.131, 20.56.169.66, 20.56.169.71, 20.56.169.138, 20.56.169.91, 52.142.226.14, 20.86.1.84, 20.86.1.80, 20.86.0.233, 20.86.1.131, 20.86.1.54, 20.86.1.128, 20.86.1.134, 20.86.1.163, 20.86.1.15, 20.86.0.250, 20.86.1.107, 20.86.1.157, 20.86.0.253, 20.86.1.12, 20.86.1.97



</td>
<td>

40.119.153.88



</td>
<td>

api.cf.eu20.hana.ondemand.com



</td>
<td>

eu20.hana.ondemand.com



</td>
<td>

[Feature Set A ](https://account.eu1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-eu20)

[Feature Set B](https://cockpit.eu20.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

ap20



</td>
<td>

Australia \(Sydney\)



</td>
<td>

cf-ap20



</td>
<td>

Australia East



</td>
<td>

40.82.211.52, 40.82.206.131, 20.70.176.247



</td>
<td>

20.53.99.41



</td>
<td>

api.cf.ap20.hana.ondemand.com



</td>
<td>

ap20.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.ap1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-ap20)

[Feature Set B](https://cockpit.ap20.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

ap21



</td>
<td>

Singapore



</td>
<td>

cf-ap21



</td>
<td>

Southeast Asia



</td>
<td>

40.90.179.153, 20.198.169.214, 20.198.168.45, 20.198.169.5, 40.90.170.226, 20.198.225.78, 20.198.225.102, 20.198.225.27, 40.90.162.117, 20.191.154.174, 20.191.154.191, 20.191.154.193



</td>
<td>

20.184.61.122



</td>
<td>

api.cf.ap21.hana.ondemand.com



</td>
<td>

ap21.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.ap1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-ap21)

[Feature Set B](https://cockpit.ap21.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

us20



</td>
<td>

US West \(WA\)



</td>
<td>

cf-us20



</td>
<td>

West US 2



</td>
<td>

40.90.195.191, 20.57.129.106, 20.57.128.95, 20.57.128.118, 40.90.209.71, 20.72.210.109, 20.72.209.240, 20.72.209.187, 40.90.200.224, 40.90.201.197, 40.90.201.85, 40.90.200.237



</td>
<td>

40.91.120.100



</td>
<td>

api.cf.us20.hana.ondemand.com



</td>
<td>

us20.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.us2.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-us20)

[Feature Set B](https://cockpit.us20.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

jp20



</td>
<td>

Japan \(Tokyo\)



</td>
<td>

cf-jp20



</td>
<td>

Japan East



</td>
<td>

52.185.186.130, 20.194.193.229, 20.194.193.167, 20.194.194.97, 40.81.200.207, 20.78.122.9, 20.78.121.237, 20.78.122.8, 20.40.96.175, 20.78.2.104, 20.78.2.106, 20.78.2.107



</td>
<td>

20.43.89.91



</td>
<td>

api.cf.jp20.hana.ondemand.com



</td>
<td>

jp20.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.jp1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-jp20)

[Feature Set B](https://cockpit.jp20.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

us21



</td>
<td>

US East \(VA\)



</td>
<td>

cf-us21



</td>
<td>

East US



</td>
<td>

40.90.251.147, 52.146.1.155, 20.51.255.236, 52.146.1.223, 40.90.232.167, 20.55.49.185, 20.55.49.92, 20.55.49.186, 40.90.231.101, 52.151.248.29, 52.146.15.82, 52.146.10.227



</td>
<td>

40.88.52.17



</td>
<td>

api.cf.us21.hana.ondemand.com



</td>
<td>

us21.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.us1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-us21)

[Feature Set B](https://cockpit.us21.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

br10



</td>
<td>

Brazil \(São Paulo\)



</td>
<td>

cf-br10



</td>
<td>

sa-east-1



</td>
<td>

52.67.245.111, 18.231.45.151, 54.207.173.126, 18.229.169.29, 54.94.110.127, 18.231.101.158, 18.230.81.234, 54.232.227.140, 52.67.251.43, 54.232.20.181, 177.71.170.199, 54.94.136.11, 52.67.221.224, 18.229.54.222, 54.232.250.83



</td>
<td>

18.229.91.150, 52.67.135.4, 54.232.179.204



</td>
<td>

api.cf.br10.hana.ondemand.com



</td>
<td>

br10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.br1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-br10)

[Feature Set B](https://cockpit.br10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

jp10



</td>
<td>

Japan \(Tokyo\)



</td>
<td>

cf-jp10



</td>
<td>

ap-northeast-1



</td>
<td>

18.177.86.79, 35.74.144.49, 3.114.115.232, 35.74.54.33, 54.249.134.63, 18.179.66.68, 54.250.33.48, 18.179.150.168, 52.198.77.221, 35.73.255.50, 54.178.62.192, 54.95.22.24, 54.238.10.97, 54.250.43.250, 52.192.218.156



</td>
<td>

3.113.252.15, 3.114.248.68, 13.114.117.83



</td>
<td>

api.cf.jp10.hana.ondemand.com



</td>
<td>

jp10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.jp1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-jp10)

[Feature Set B](https://cockpit.jp10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

ap10



</td>
<td>

Australia \(Sydney\)



</td>
<td>

cf-ap10



</td>
<td>

ap-southeast-2



</td>
<td>

13.210.173.131, 13.54.77.205, 13.237.182.31, 13.55.239.117, 54.79.72.145, 13.236.142.207, 54.79.43.227, 52.65.102.82, 54.79.26.135, 13.54.220.129, 13.236.59.235, 13.54.252.220, 52.62.223.36, 13.55.100.204, 13.54.168.75



</td>
<td>

3.105.95.184, 13.211.73.244, 13.236.220.84



</td>
<td>

api.cf.ap10.hana.ondemand.com



</td>
<td>

ap10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.ap1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-ap10)

[Feature Set B](https://cockpit.ap10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

ap11



</td>
<td>

Asia Pacific \(Singapore\)



</td>
<td>

cf-ap11



</td>
<td>

ap-southeast-1



</td>
<td>

13.229.13.240, 54.251.74.134, 52.220.111.202, 52.76.185.92, 52.76.123.164, 54.179.253.138, 13.213.119.83, 54.179.77.154, 52.76.114.209, 13.213.105.43, 13.213.132.88, 3.1.38.48, 13.251.40.148, 13.228.68.14, 13.251.49.36



</td>
<td>

3.0.9.102, 18.139.147.53, 18.140.39.70



</td>
<td>

api.cf.ap11.hana.ondemand.com



</td>
<td>

ap11.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.ap1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-ap11)

[Feature Set B](https://cockpit.ap11.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

ap12



</td>
<td>

Asia Pacific \(Seoul\)



</td>
<td>

cf-ap12



</td>
<td>

ap-northeast-2



</td>
<td>

15.164.33.162, 3.34.19.116, 3.36.2.67, 52.78.49.16, 15.164.254.80, 3.36.165.189, 52.78.38.74, 3.35.57.231, 13.124.251.247, 13.124.16.17, 15.165.83.237, 15.165.249.251, 15.165.116.197, 54.180.53.68, 3.35.252.222



</td>
<td>

3.35.255.45, 3.35.106.215, 3.35.215.12



</td>
<td>

api.cf.ap12.hana.ondemand.com



</td>
<td>

ap12.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.ap1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-ap12)

[Feature Set B](https://cockpit.ap12.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

ca10



</td>
<td>

Canada \(Montreal\)



</td>
<td>

cf-ca10



</td>
<td>

ca-central-1



</td>
<td>

35.182.198.31, 35.182.118.205,3.98.159.3, 15.222.120.34, 3.96.14.215, 3.97.48.154, 3.96.101.45, 35.182.95.49, 3.97.228.23, 35.182.185.156, 3.97.119.250, 3.98.252.245, 15.223.62.0, 99.79.181.241, 3.98.167.60



</td>
<td>

35.182.75.101, 35.183.74.34, 3.98.102.153



</td>
<td>

api.cf.ca10.hana.ondemand.com



</td>
<td>

ca10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.ca1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-ca10)

[Feature Set B](https://cockpit.ca10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

eu10



</td>
<td>

Europe \(Frankfurt\)



</td>
<td>

cf-eu10



</td>
<td>

eu-central-1



</td>
<td>

3.68.51.135, 3.124.174.204, 3.68.31.37, 3.67.58.183, 3.67.0.172, 3.67.244.62, 3.126.117.58, 3.67.200.70, 3.68.13.226, 3.126.45.133, 3.67.249.135, 18.194.183.183, 3.67.246.74, 3.66.68.201, 3.68.0.70, 3.66.100.105, 3.126.95.250, 3.66.68.127, 18.195.244.40, 3.67.107.121, 3.67.24.253, 18.193.50.255, 3.121.35.143, 52.28.56.202, 52.59.128.222, 52.28.241.88, 18.184.81.94

**cf-eu10-002:**

18.197.134.65, 52.29.190.137, 3.67.255.232, 3.67.182.154, 3.68.44.236, 3.66.249.150, 18.198.196.89, 18.193.21.232, 3.65.9.91

**cf-eu10-003:**

3.68.40.83, 18.198.18.157, 3.68.17.221, 3.67.235.98, 3.68.38.23, 18.198.149.19, 3.64.131.199, 3.64.88.217, 3.64.142.243



</td>
<td>

3.124.222.77, 3.122.209.241, 3.124.208.223

**cf-eu10-002:**

3.64.227.236, 3.126.229.22, 18.193.180.19

**cf-eu10-003:**

18.156.151.247, 3.64.196.58, 3.127.77.3



</td>
<td>

api.cf.eu10.hana.ondemand.com



</td>
<td>

eu10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.eu2.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-eu10)

[Feature Set B](https://cockpit.eu10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

eu11



</td>
<td>

Europe \(Frankfurt\)



</td>
<td>

cf-eu11



</td>
<td>

eu-central-1



</td>
<td>

18.185.57.85, 3.121.79.209, 3.67.237.8, 52.59.77.121, 3.65.63.251, 3.122.176.63, 18.198.13.57, 35.156.31.32, 18.184.172.97, 18.159.180.188, 35.157.5.44, 18.157.114.142, 18.156.140.38, 3.121.55.100, 35.156.198.246



</td>
<td>

3.124.207.41, 18.157.105.117, 18.156.209.198



</td>
<td>

api.eu11.hana.ondemand.com



</td>
<td>

eu11.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.eu2.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-eu11)

[Feature Set B](https://cockpit.eu11.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

us10



</td>
<td>

US East \(VA\)



</td>
<td>

cf-us10



</td>
<td>

us-east-1



</td>
<td>

18.211.235.11, 54.156.172.106, 34.234.191.59, 34.192.134.47, 18.204.173.15, 3.213.197.54, 184.73.43.82, 18.210.47.160, 3.216.16.207, 34.225.190.250, 52.2.110.230, 54.234.93.200, 35.153.88.132, 52.204.111.138, 3.88.250.160, 52.20.242.182, 52.71.83.110, 52.200.165.163, 54.208.119.130, 34.202.136.35, 34.192.100.96, 54.85.65.82, 54.205.71.200, 54.221.30.91, 52.200.16.71, 52.23.123.125, 52.202.170.155

**cf-us10-001:**

34.233.151.91, 3.225.73.158, 3.222.22.16, 23.23.172.117, 34.194.239.31, 34.238.1.234, 18.213.153.162, 52.0.214.195, 54.227.144.195

**cf-us10-002:**

54.82.224.146, 18.232.28.65, 18.211.12.227, 3.221.4.74, 72.44.51.245, 54.159.45.198, 34.206.160.141, 35.168.80.144, 54.162.233.194



</td>
<td>

52.23.189.23, 52.4.101.240, 52.23.1.211

**cf-us10-002:**

34.202.68.0, 107.20.66.86, 54.234.152.59



</td>
<td>

api.cf.us10.hana.ondemand.com



</td>
<td>

us10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.us1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-us10)

[Feature Set B](https://cockpit.us10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Google Cloud Platform



</td>
<td>

us30



</td>
<td>

US Central \(IA\)



</td>
<td>

cf-us30



</td>
<td>

us-central-1



</td>
<td>

35.202.96.192, 35.193.171.152, 35.193.168.31, 35.202.69.204, 35.202.175.147, 35.193.69.164, 35.202.1.6, 23.236.63.113, 35.193.30.116, 35.202.66.196, 34.68.152.205, 35.222.158.222, 104.197.20.168, 35.232.105.70, 35.224.211.196, 35.222.192.158, 35.193.8.172



</td>
<td>

35.184.169.79



</td>
<td>

api.cf.us30.hana.ondemand.com



</td>
<td>

us30.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.us1.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-us30)

[Feature Set B](https://cockpit.us30.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Alibaba Cloud



</td>
<td>

cn40



</td>
<td>

China \(Shanghai\)



</td>
<td>

cf-cn40



</td>
<td>

cn-shanghai



</td>
<td>

101.132.190.155, 106.14.165.33, 106.14.184.113



</td>
<td>

139.224.7.71



</td>
<td>

api.cf.cn40.platform.sapcloud.cn



</td>
<td>

cn40.platform.sapcloud.cn



</td>
<td>

 [Feature Set B](https://cockpit.cn40.platform.sapcloud.cn/cockpit) 



</td>
</tr>
</table>

<a name="loio350356d1dc314d3199dca15bd2ab9b0e loiof344a57233d34199b2123b9620d0bb41__table_db4_gj4_lpb"/>Regions for Trial Accounts


<table>
<tr>
<th>

IaaS Provider



</th>
<th>

Region



</th>
<th>

Region Name



</th>
<th>

Technical Key



</th>
<th>

Technical Key of IaaS Provider



</th>
<th>

Trial NAT IPs \(egress, IPs for requests from a Cloud Foundry app\)



</th>
<th>

LB IPs \(ingress, for incoming requests\)



</th>
<th>

API Endpoint



</th>
<th>

Domain



</th>
<th>

Cockpit Logon



</th>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

eu10



</td>
<td>

Europe \(Frankfurt\)



</td>
<td>

cf-eu10



</td>
<td>

eu-central-1



</td>
<td>

3.124.22.250, 3.124.41.239, 52.29.53.204



</td>
<td>

3.124.222.77, 3.122.209.241, 3.124.208.223



</td>
<td>

api.cf.eu10.hana.ondemand.com



</td>
<td>

eu10.hana.ondemand.com



</td>
<td>

 [Trial](https://cockpit.eu10.hana.ondemand.com/trial) 



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

us10



</td>
<td>

US East \(VA\)



</td>
<td>

cf-us10



</td>
<td>

us-east-1



</td>
<td>

3.218.99.154, 52.72.147.227, 3.218.112.63



</td>
<td>

52.23.189.23, 52.4.101.240, 52.23.1.211



</td>
<td>

api.cf.us10.hana.ondemand.com



</td>
<td>

us10.hana.ondemand.com



</td>
<td>

[Trial](https://cockpit.us10.hana.ondemand.com/trial)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

ap21



</td>
<td>

Singapore



</td>
<td>

cf-ap21



</td>
<td>

Southeast Asia



</td>
<td>

52.139.216.172, 20.195.24.178, 20.195.9.169



</td>
<td>

20.184.61.122



</td>
<td>

api.cf.ap21.hana.ondemand.com



</td>
<td>

ap21.hana.ondemand.com



</td>
<td>

 [Trial](https://cockpit.ap21.hana.ondemand.com/trial) 



</td>
</tr>
</table>



> ### Note:  
> In the Cloud Foundry environment, IPs are controlled by the respective IaaS provider \(AWS, Azure, or GCP\). IPs may change due to network updates on the provider side. Any planned changes will be announced at least four weeks before they take effect.

 <a name="loio350356d1dc314d3199dca15bd2ab9b0e loio879f37370d9b45e99a16538e0f37ff2c__loio879f37370d9b45e99a16538e0f37ff2c"/>

<!-- loio879f37370d9b45e99a16538e0f37ff2c -->

# Regions and API Endpoints for the ABAP Environment



<a name="loio350356d1dc314d3199dca15bd2ab9b0e loio879f37370d9b45e99a16538e0f37ff2c__table_xps_cr3_3z"/>Regions and API Endpoints for the ABAP Environment


<table>
<tr>
<th>

Global Account Type



</th>
<th>

Region



</th>
<th>

IaaS Provider



</th>
<th>

Technical Key



</th>
<th>

Technical Key of IaaS Provider



</th>
<th>

API Endpoint & Domain



</th>
<th>

Cockpit Logon



</th>
</tr>
<tr>
<td rowspan="3">

Enterprise & trial account



</td>
<td>

Europe \(Frankfurt\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-eu10



</td>
<td>

eu-central-1



</td>
<td>

api.cf.eu10.hana.ondemand.com

Domain: eu10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.eu2.hana.ondemand.com/cockpit#/home/allaccounts/?datacenter=cf-eu10)

[Feature Set B](https://cockpit.eu10.hana.ondemand.com/)

[Trial](https://cockpit.eu10.hana.ondemand.com/trial)



</td>
</tr>
<tr>
<td>

US East \(VA\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-us10



</td>
<td>

us-east-1



</td>
<td>

api.cf.us10.hana.ondemand.com

Domain: us10.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.us1.hana.ondemand.com/cockpit#/home/allaccounts/%3Fdatacenter=cf-us10)

[Feature Set B](https://cockpit.us10.hana.ondemand.com/)



</td>
</tr>
<tr>
<td>

Japan \(Tokyo\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-jp10



</td>
<td>

ap-northeast-1



</td>
<td>

api.cf.jp10.hana.ondemand.com

Domain: ap21.hana.ondemand.com



</td>
<td>

[Feature Set A](https://account.jp1.hana.ondemand.com/cockpit#/home/allaccounts/%3Fdatacenter=cf-jp10)

[Feature Set B](https://cockpit.ap21.hana.ondemand.com/)

[Trial](https://cockpit.us10.hana.ondemand.com/trial/)



</td>
</tr>
</table>

> ### Caution:  
> Some customer contracts include EU access, which means that we only use European subprocessors to access personal data in cloud services, such as when we provide support. We currently cannot guarantee EU access in the ABAP environment. If your contract includes EU access, we cannot move services to the ABAP environment, without changing your contract.

 <a name="loio350356d1dc314d3199dca15bd2ab9b0e loio557ec3adc3174ed4914ec9d6d13487cf__loio557ec3adc3174ed4914ec9d6d13487cf"/>

<!-- loio557ec3adc3174ed4914ec9d6d13487cf -->

# Regions for the Kyma Environment

To work with the Kyma environment, you need to specify the region for both your subaccount and the cluster.



> ### Note:  
> In the Kyma environment, there are no static IP addresses. All IP addresses are configured dynamically for the NAT Gateway that handles the egress traffic.



## Subaccount Regions

The table lists the regions you can choose from when creating a subaccount.

<a name="loio350356d1dc314d3199dca15bd2ab9b0e loio557ec3adc3174ed4914ec9d6d13487cf__table_xps_cr3_3z"/>Subaccount Regions for the Kyma Environment


<table>
<tr>
<th>

Global Account Type



</th>
<th>

Region



</th>
<th>

IaaS Provider



</th>
<th>

Technical Key



</th>
<th>

Technical Key of IaaS Provider



</th>
</tr>
<tr>
<td>

Enterprise and trial account



</td>
<td>

Singapore



</td>
<td>

Microsoft Azure



</td>
<td>

cf-ap21



</td>
<td>

Southeast Asia



</td>
</tr>
<tr>
<td>

Enterprise and trial account



</td>
<td>

US East \(VA\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-us10



</td>
<td>

US East \(VA\)



</td>
</tr>
<tr>
<td>

Enterprise and trial account



</td>
<td>

Europe \(Frankfurt\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-eu10



</td>
<td>

Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

US West \(WA\)



</td>
<td>

Microsoft Azure



</td>
<td>

cf-us20



</td>
<td>

West US 2



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Japan \(Tokyo\)



</td>
<td>

Microsoft Azure



</td>
<td>

cf-jp20



</td>
<td>

Japan East



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

US East \(VA\)



</td>
<td>

Microsoft Azure



</td>
<td>

cf-us21



</td>
<td>

East US



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Europe \(Netherlands\)



</td>
<td>

Microsoft Azure



</td>
<td>

cf-eu20



</td>
<td>

West Europe



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Brazil \(São Paulo\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-br10



</td>
<td>

Brazil \(São Paulo\)



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Japan \(Tokyo\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-jp10



</td>
<td>

Japan \(Tokyo\)



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Canada \(Montreal\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-ca10



</td>
<td>

Canada \(Montreal\)



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

South Korea \(Seoul\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-ap12



</td>
<td>

Asia Pacific \(Seoul\)



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Australia \(Sydney\)



</td>
<td>

Amazon Web Services



</td>
<td>

cf-ap10



</td>
<td>

Asia Pacific \(Sydney\)



</td>
</tr>
<tr>
<td>

Enterprise account



</td>
<td>

Singapore



</td>
<td>

Amazon Web Services



</td>
<td>

cf-ap11



</td>
<td>

Asia Pacific \(Singapore\)



</td>
</tr>
</table>



<a name="loio350356d1dc314d3199dca15bd2ab9b0e loio557ec3adc3174ed4914ec9d6d13487cf__section_uqf_2sl_wlb"/>

## Cluster Regions

When you enable a Kyma environment for a given subaccount, you must select a plan and region where the cluster is going to be created. You can select one of the following regions:

<a name="loio350356d1dc314d3199dca15bd2ab9b0e loio557ec3adc3174ed4914ec9d6d13487cf__table_kyma_cluster_regions"/>Kyma Cluster Regions


<table>
<tr>
<th>

Plan



</th>
<th>

Region



</th>
<th>

Region Name



</th>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`centralus`



</td>
<td>

Central US \(Iowa\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`eastus`



</td>
<td>

East US \(Virginia\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`westus2`



</td>
<td>

West US2 \(Washington\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`northeurope`



</td>
<td>

North EU \(Ireland\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`uksouth`



</td>
<td>

UK South \(London\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`japaneast`



</td>
<td>

Japan East \(Tokyo\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`southeastasia`



</td>
<td>

Southeast Asia \(Singapore\)



</td>
</tr>
<tr>
<td>

Microsoft Azure



</td>
<td>

`westeurope`



</td>
<td>

West Europe \(Netherlands\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`eu-central-1`



</td>
<td>

Europe \(Frankfurt\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`eu-west-2`



</td>
<td>

Europe \(London\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`ca-central-1`



</td>
<td>

Canada \(Central\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`sa-east-1`



</td>
<td>

South America \(São Paulo\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`us-east-1`



</td>
<td>

US East \(N. Virginia\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`us-west-1`



</td>
<td>

US West \(N. California\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`ap-northeast-1`



</td>
<td>

Asia Pacific \(Tokyo\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`ap-northeast-2`



</td>
<td>

Asia Pacific \(Seoul\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`ap-south-1`



</td>
<td>

Asia Pacific \(Mumbai\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`ap-southeast-1`



</td>
<td>

Asia Pacific \(Singapore\)



</td>
</tr>
<tr>
<td>

Amazon Web Services



</td>
<td>

`ap-southeast-2`



</td>
<td>

Asia Pacific \(Sydney\)



</td>
</tr>
</table>

**Related Information**  


[Enable Kyma Environment](../50-administration-and-ops/Enable_Kyma_Environment_09dd313.md "Set up a Kubernetes cluster with project &quot;Kyma&quot; and use it to build applications and extensions to your SAP and third-party solutions.")

 <a name="loio350356d1dc314d3199dca15bd2ab9b0e loioe3ac4f7c25a3442ca585950095eec599__loioe3ac4f7c25a3442ca585950095eec599"/>

<!-- loioe3ac4f7c25a3442ca585950095eec599 -->

# Resilience, High Availability, and Disaster Recovery

SAP has a number of processes in place to support resilience in SAP BTP, and provides different offerings so that you can support the high availability of your applications.



<a name="loio350356d1dc314d3199dca15bd2ab9b0e loioe3ac4f7c25a3442ca585950095eec599__section_pxk_bqk_ylb"/>

## How SAP Provides Resilience

SAP applies resilience principles when developing, updating, and deploying our SAP BTP applications and services.

SAP BTP provides resilience through the following:


<table>
<tr>
<th>

Processes and Offerings



</th>
<th>

Description



</th>
<th>

Regional Availability



</th>
</tr>
<tr>
<td>

 **Availability Zones** 



</td>
<td>

To achieve better fault-tolerance in the Cloud Foundry environment, we deploy our services across multiple AZs, which improves the availability of a service if there are issues with the infrastructure of one AZ. For more information, see [Availability Zones in the Cloud Foundry Environment](Cloud_Foundry_Environment_9c7092c.md#loiob6a7e11c3a58416a9ab1175bba17193a).



</td>
<td>

All regions that support the Cloud Foundry environment. See [Regions and API Endpoints Available for the Cloud Foundry Environment](Regions_350356d.md#loiof344a57233d34199b2123b9620d0bb41).



</td>
</tr>
<tr>
<td>

 **Backups in the Kyma environment** 



</td>
<td>

The Kyma environment relies on managed Kubernetes clusters for periodic backups of Kubernetes objects. For more information, see [Kyma Environment Backup](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/ab959cfbd07b46af97aecfd6577bfb10.html).



</td>
<td>

All regions that support the Kyma environment. See [Regions for the Kyma Environment](Regions_350356d.md#loio557ec3adc3174ed4914ec9d6d13487cf).



</td>
</tr>
<tr>
<td>

 **Backup and Recovery for SAP HANA Cloud** 



</td>
<td>

If you use SAP HANA Cloud, your SAP HANA Cloud instances are continually backed up to safeguard your database and ensure that it can be recovered speedily. For more information, see [Backup and Recovery](https://help.sap.com/viewer/db19c7071e5f4101837e23f06e576495/cloud/en-US/89d71f01daca4ecaaa069d6a060167f5.html).



</td>
<td>

All regions where SAP HANA Cloud is available. See [Availability of SAP HANA Cloud](https://help.sap.com/doc/aa1ccd10da6c4337aa737df2ead1855b/Cloud/en-US/3b642f68227b4b1398d2ce1a5351389a.html?scp-name=SAP%20HANA%20Cloud).



</td>
</tr>
<tr>
<td>

 **Disaster Recovery** 



</td>
<td>

The SAP BTP Disaster Recovery \(DR\) Plan is part of the overall SAP BTP Business Continuity Plan, which includes crisis management and process continuity activities that are triggered by a declared disaster. For more information, see [Disaster Recovery as Part of the Business Continuity Plan](Regions_350356d.md#loio001180644f8a428bb422cd41caebb95f).



</td>
<td>

All regions.



</td>
</tr>
</table>



<a name="loio350356d1dc314d3199dca15bd2ab9b0e loioe3ac4f7c25a3442ca585950095eec599__section_n1c_dqk_ylb"/>

## Best Practices for Resilient Applications

In addition to the services offered by SAP BTP, you can follow our best practices for developing and deploying applications, which allow you to make your application running on SAP BTP stable and highly available.

-   **Develop Resilient Applications**

    When developing your applications, apply the principles and patterns of resilient software design that fit your use case. For more information, see [Developing Resilient Apps on SAP BTP](https://help.sap.com/viewer/eadaa45871804b4a974be865f627e791/Cloud/en-US/d1fe5fd8ecfb46c193221ebb991af3d7.html).

-   **Working with Availability Zones**

    To benefit from the high availability mechanisms in Cloud Foundry, set up your applications with multiple instances. For more information, see [Developing Resilient Applications in the Cloud Foundry Environment](https://help.sap.com/viewer/df50977d8bfa4c9a8a063ddb37113c43/Cloud/en-US/b1b929a5aea64571b2f74e810b622568.html "Our best practices about resilient application design help you to make your applications running on SAP BTP stable and highly available.") :arrow_upper_right:.


 <a name="loio350356d1dc314d3199dca15bd2ab9b0e loioe3ac4f7c25a3442ca585950095eec599 loio001180644f8a428bb422cd41caebb95f__loio001180644f8a428bb422cd41caebb95f"/>

<!-- loio001180644f8a428bb422cd41caebb95f -->

# Disaster Recovery as Part of the Business Continuity Plan

The cloud platform disaster recovery \(DR\) plan is part of the overall cloud platform business continuity plan, which includes crisis management and process continuity activities that are triggered by a declared disaster.



<a name="loio350356d1dc314d3199dca15bd2ab9b0e loioe3ac4f7c25a3442ca585950095eec599 loio001180644f8a428bb422cd41caebb95f__section_knl_qqp_j3b"/>

## Standard Disaster Recovery

SAP can restore productive tenants from backups as soon as practicable in case of a disaster resulting in the loss of the primary production data center.

As the magnitude of a disaster is unpredictable, a region might not be restored in a reasonable time. In addition, a new infrastructure might need to be set up at a different location, which might require the purchase and setup of new hardware. Therefore, we can't guarantee any fixed recovery timelines.

