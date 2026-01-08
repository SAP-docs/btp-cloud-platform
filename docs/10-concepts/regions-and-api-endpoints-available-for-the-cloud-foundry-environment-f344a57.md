<!-- loiof344a57233d34199b2123b9620d0bb41 -->

# Regions and API Endpoints Available for the Cloud Foundry Environment



> ### Note:  
> If you are using the Cloud Connector and/or the Destination service for connections between your SAP BTP applications and your local network or another \(web-based\) target system, and you restrict access by allowlisting IP addresses in your firewall rules, you must add connectivity-specific IPs to these rules for the respective SAP BTP region\(s\).
> 
> For the Destination service, both the egress and ingress IPs \(NAT and LB IPs\) may be relevant.
> 
> For more information, see:
> 
> -   [Prerequisites: Network](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/prerequisites#network) \(Cloud Connector\)
> -   [Configure Destination Service IPs in Firewall Rules](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/destination-service-nat-ips) \(Destination service\)

**Regions for Enterprise Accounts**


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

NAT IPs \(egress, IPs for requests from a Cloud Foundry app\)

</th>
<th valign="top">

LB IPs \(ingress, for incoming requests\)

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

Microsoft Azure

</td>
<td valign="top">

eu20

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
<td valign="top">

cf-eu20

</td>
<td valign="top">

West Europe

</td>
<td valign="top">

**cf-eu20:**

52.149.67.35, 20.82.96.175, 20.82.96.178, 20.82.96.211, 20.82.96.244, 20.82.96.220, 20.82.96.227, 20.82.97.50, 20.82.96.240, 20.82.96.234, 20.82.97.38, 20.82.96.222, 20.82.96.233, 20.82.96.248, 20.82.97.31, 20.82.97.45, 52.149.96.147, 20.56.169.152, 20.56.169.69, 20.56.169.0, 20.56.169.41, 20.56.169.58, 20.56.169.161, 20.56.169.116, 20.56.169.167, 20.56.169.50, 20.56.169.175, 20.56.169.131, 20.56.169.66, 20.56.169.71, 20.56.169.138, 20.56.169.91, 52.142.226.14, 20.86.1.84, 20.86.1.80, 20.86.0.233, 20.86.1.131, 20.86.1.54, 20.86.1.128, 20.86.1.134, 20.86.1.163, 20.86.1.15, 20.86.0.250, 20.86.1.107, 20.86.1.157, 20.86.0.253, 20.86.1.12, 20.86.1.97

**cf-eu20-001:**

20.54.248.90, 20.54.248.142, 20.54.250.88, 20.54.250.91, 20.56.17.109, 20.56.18.130, 20.56.18.132, 20.56.18.179, 20.86.17.114, 20.86.17.142, 20.86.17.153, 20.86.17.159

**cf-eu20-002:**

20.86.83.34, 50.85.208.116/31, 51.105.247.44, 134.149.194.28/31, 172.201.130.235, 172.211.56.76/31

</td>
<td valign="top">

**cf-eu20:**

40.119.153.88

**cf-eu20-001:**

20.82.83.59

**cf-eu20-002:**

98.64.76.0

</td>
<td valign="top">

**cf-eu20:**

api.cf.eu20.hana.ondemand.com

**cf-eu20-001:**

api.cf.eu20-001.hana.ondemand.com

**cf-eu20-002:**

api.cf.eu20-002.hana.ondemand.com

</td>
<td valign="top">

**cf-eu20:**

eu20.hana.ondemand.com

**cf-eu20-001:**

eu20-001.hana.ondemand.com

**cf-eu20-002:**eu20-002.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ap20

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap20

</td>
<td valign="top">

Australia East

</td>
<td valign="top">

40.82.211.52, 40.82.206.131, 20.70.176.247, 20.40.81.59, 20.40.80.246, 20.40.81.36, 20.70.208.178, 20.70.208.228, 20.70.208.235, 20.70.201.155, 20.70.201.89, 20.70.201.66

</td>
<td valign="top">

20.53.99.41

</td>
<td valign="top">

api.cf.ap20.hana.ondemand.com

</td>
<td valign="top">

ap20.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ap21

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

cf-ap21

</td>
<td valign="top">

Southeast Asia

</td>
<td valign="top">

40.90.179.153, 20.198.169.214, 20.198.168.45, 20.198.169.5, 40.90.170.226, 20.198.225.78, 20.198.225.102, 20.198.225.27, 40.90.162.117, 20.191.154.174, 20.191.154.191, 20.191.154.193

</td>
<td valign="top">

20.184.61.122

</td>
<td valign="top">

api.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

ap21.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

br20

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

cf-br20

</td>
<td valign="top">

Brazil South

</td>
<td valign="top">

20.206.161.114, 20.206.249.230, 191.233.21.237

</td>
<td valign="top">

4.228.118.21

</td>
<td valign="top">

api.cf.br20.hana.ondemand.com

</td>
<td valign="top">

br20.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ca20

</td>
<td valign="top">

Canada Central \(Toronto\)

</td>
<td valign="top">

cf-ca20

</td>
<td valign="top">

canadacentral

</td>
<td valign="top">

4.172.210.105, 4.172.226.192, 4.204.51.0, 4.248.154.171, 20.63.122.64, 20.151.145.75

</td>
<td valign="top">

4.172.17.29

</td>
<td valign="top">

api.cf.ca20.hana.ondemand.com

</td>
<td valign="top">

ca20.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

cn20

</td>
<td valign="top">

China \(North 3\)

</td>
<td valign="top">

cf-cn20

</td>
<td valign="top">

ChinaNorth3

</td>
<td valign="top">

159.27.65.75, 159.27.107.117, 159.27.217.233

</td>
<td valign="top">

143.64.224.195

</td>
<td valign="top">

api.cf.cn20.platform.sapcloud.cn

</td>
<td valign="top">

cn20.platform.sapcloud.cn

</td>
<td valign="top">

[Open Cockpit](https://cockpit.cn20.platform.sapcloud.cn/cockpit)

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

us20

</td>
<td valign="top">

US West \(WA\)

</td>
<td valign="top">

cf-us20

</td>
<td valign="top">

West US 2

</td>
<td valign="top">

40.90.195.191, 20.57.129.106, 20.57.128.95, 20.57.128.118, 40.90.209.71, 20.72.210.109, 20.72.209.240, 20.72.209.187, 40.90.200.224, 40.90.201.197, 40.90.201.85, 40.90.200.237

</td>
<td valign="top">

40.91.120.100

</td>
<td valign="top">

api.cf.us20.hana.ondemand.com

</td>
<td valign="top">

us20.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

jp20

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

cf-jp20

</td>
<td valign="top">

Japan East

</td>
<td valign="top">

52.185.186.130, 20.194.193.229, 20.194.193.167, 20.194.194.97, 40.81.200.207, 20.78.122.9, 20.78.121.237, 20.78.122.8, 20.40.96.175, 20.78.2.104, 20.78.2.106, 20.78.2.107

</td>
<td valign="top">

20.43.89.91

</td>
<td valign="top">

api.cf.jp20.hana.ondemand.com

</td>
<td valign="top">

jp20.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

us21

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

cf-us21

</td>
<td valign="top">

East US

</td>
<td valign="top">

40.90.251.147, 52.146.1.155, 20.51.255.236, 52.146.1.223, 40.90.232.167, 20.55.49.185, 20.55.49.92, 20.55.49.186, 40.90.231.101, 52.151.248.29, 52.146.15.82, 52.146.10.227

</td>
<td valign="top">

40.88.52.17

</td>
<td valign="top">

api.cf.us21.hana.ondemand.com

</td>
<td valign="top">

us21.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ch20

</td>
<td valign="top">

Switzerland \(Zurich\)

</td>
<td valign="top">

cf-ch20

</td>
<td valign="top">

Switzerland North

</td>
<td valign="top">

20.208.128.83, 20.208.128.86, 20.208.128.87, 20.208.128.88, 51.103.208.79, 51.103.208.81, 51.103.208.85, 51.103.208.87, 51.107.2.38, 51.107.2.50, 51.107.2.52, 51.107.2.54

</td>
<td valign="top">

20.208.56.83

</td>
<td valign="top">

api.cf.ch20.hana.ondemand.com

</td>
<td valign="top">

ch20.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://eu-access.cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

br10

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

cf-br10

</td>
<td valign="top">

sa-east-1

</td>
<td valign="top">

52.67.245.111, 18.231.45.151, 54.207.173.126, 18.230.81.234, 18.229.169.29, 54.94.110.127, 18.231.101.158, 177.71.170.199, 54.232.227.140, 52.67.251.43, 54.232.20.181, 54.94.136.11, 52.67.221.224, 18.229.54.222, 54.232.250.83, 18.228.194.102, 18.228.198.142, 177.71.168.150

</td>
<td valign="top">

18.229.91.150, 52.67.135.4, 54.232.179.204, 18.228.53.198, 52.67.149.240, 54.94.179.209

</td>
<td valign="top">

api.cf.br10.hana.ondemand.com

</td>
<td valign="top">

br10.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

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

54.238.10.97, 54.250.43.250, 52.192.218.156, 35.74.54.33, 18.177.86.79, 35.74.144.49, 3.114.115.232, 18.179.150.168, 54.249.134.63, 18.179.66.68, 54.250.33.48, 54.95.22.24, 52.198.77.221, 35.73.255.50, 54.178.62.192, 3.113.232.224, 52.198.66.114, 13.230.215.218

</td>
<td valign="top">

3.114.248.68, 3.113.252.15, 13.114.117.83, 18.178.155.134, 57.180.140.5, 57.180.145.179

</td>
<td valign="top">

api.cf.jp10.hana.ondemand.com

</td>
<td valign="top">

jp10.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ap10

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap10

</td>
<td valign="top">

ap-southeast-2

</td>
<td valign="top">

52.62.223.36, 13.55.100.204, 13.54.168.75, 13.55.239.117, 13.210.173.131, 13.54.77.205, 13.237.182.31, 52.65.102.82, 54.79.72.145, 13.236.142.207, 54.79.43.227, 13.54.252.220, 54.79.26.135, 13.54.220.129, 13.236.59.235, 13.238.9.23, 54.153.242.51, 3.105.234.54

</td>
<td valign="top">

13.236.220.84, 13.211.73.244, 3.105.95.184, 13.55.188.95, 3.105.212.249, 3.106.45.106

</td>
<td valign="top">

api.cf.ap10.hana.ondemand.com

</td>
<td valign="top">

ap10.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ap11

</td>
<td valign="top">

Asia Pacific \(Singapore\)

</td>
<td valign="top">

cf-ap11

</td>
<td valign="top">

ap-southeast-1

</td>
<td valign="top">

13.251.40.148, 13.228.68.14, 13.251.49.36, 52.76.185.92, 13.229.13.240, 54.251.74.134, 52.220.111.202, 54.179.77.154, 52.76.123.164, 54.179.253.138, 13.213.119.83, 3.1.38.48, 52.76.114.209, 13.213.105.43, 13.213.132.88, 13.250.92.77, 18.140.150.56, 18.140.255.164

</td>
<td valign="top">

18.139.147.53, 3.0.9.102, 18.140.39.70, 13.229.158.122, 18.140.228.217, 52.74.215.89

</td>
<td valign="top">

api.cf.ap11.hana.ondemand.com

</td>
<td valign="top">

ap11.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ap12

</td>
<td valign="top">

Asia Pacific \(Seoul\)

</td>
<td valign="top">

cf-ap12

</td>
<td valign="top">

ap-northeast-2

</td>
<td valign="top">

15.165.116.197, 54.180.53.68, 3.35.252.222, 52.78.49.16, 15.164.33.162, 3.34.19.116, 3.36.2.67, 3.35.57.231, 15.164.254.80, 3.36.165.189, 52.78.38.74, 15.165.249.251, 13.124.251.247, 13.124.16.17, 15.165.83.237

</td>
<td valign="top">

3.35.106.215, 3.35.255.45, 3.35.215.12, 13.209.236.215, 43.201.194.105, 43.202.204.5

</td>
<td valign="top">

api.cf.ap12.hana.ondemand.com

</td>
<td valign="top">

ap12.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ca10

</td>
<td valign="top">

Canada \(Montreal\)

</td>
<td valign="top">

cf-ca10

</td>
<td valign="top">

ca-central-1

</td>
<td valign="top">

35.182.118.205, 35.182.198.31, 3.98.159.3, 3.96.101.45, 15.222.120.34, 3.96.14.215, 3.97.48.154, 3.97.119.250, 35.182.95.49, 3.97.228.23, 35.182.185.156, 3.98.252.245, 15.223.62.0, 99.79.181.241, 3.98.167.60, 99.79.110.245, 52.60.239.204, 52.60.212.33

</td>
<td valign="top">

35.183.74.34, 35.182.75.101, 3.98.102.153, 15.157.88.166, 3.98.202.222, 52.60.210.33

</td>
<td valign="top">

api.cf.ca10.hana.ondemand.com

</td>
<td valign="top">

ca10.hana.ondemand.com

</td>
<td valign="top">

[Feature Set B](https://cockpit.btp.cloud.sap/) 

</td>
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

**cf-eu10:**

52.59.128.222, 52.28.241.88, 18.184.81.94, 3.67.200.70, 3.68.51.135, 3.124.174.204, 3.68.31.37, 3.67.58.183, 3.67.0.172, 3.67.244.62, 3.126.117.58, 3.66.100.105, 3.68.13.226, 3.126.45.133, 3.67.249.135, 18.194.183.183, 3.67.246.74, 3.66.68.201, 3.68.0.70, 52.28.56.202, 3.126.95.250, 3.66.68.127, 18.195.244.40, 3.67.107.121, 3.67.24.253, 18.193.50.255, 3.121.35.143

**cf-eu10-002:**

18.198.196.89, 18.193.21.232, 3.65.9.91, 52.29.190.137, 18.197.134.65, 3.67.182.154, 3.67.255.232, 3.66.249.150, 3.68.44.236

**cf-eu10-003:**

3.64.131.199, 3.64.88.217, 3.64.142.243, 18.198.18.157, 3.68.40.83, 3.67.235.98, 3.68.17.221, 18.198.149.19, 3.68.38.23

**cf-eu10-004:**

3.69.195.103, 3.64.170.167, 3.68.176.248, 3.121.49.211, 18.197.219.60, 3.70.38.84

**cf-eu10-005:**

35.159.192.144/28

</td>
<td valign="top">

**cf-eu10:**

3.124.208.223, 3.122.209.241, 3.124.222.77, 18.159.31.22, 3.69.186.98, 3.77.195.119

**cf-eu10-002:**

3.126.229.22, 18.193.180.19, 3.64.227.236, 18.153.123.11, 3.121.37.195, 3.73.215.90

**cf-eu10-003:**

3.127.77.3, 3.64.196.58, 18.156.151.247, 18.197.252.154, 3.79.137.29, 52.58.93.50

**cf-eu10-004:**

3.70.38.218, 18.196.206.8, 3.65.185.47, 3.73.109.100, 3.73.8.210, 52.59.18.183

**cf-eu10-005:**

3.78.172.245, 3.122.31.132, 18.193.56.244

</td>
<td valign="top">

**cf-eu10:**

api.cf.eu10.hana.ondemand.com

**cf-eu10-002:**

api.cf.eu10-002.hana.ondemand.com

**cf-eu10-003:**

api.cf.eu10-003.hana.ondemand.com

**cf-eu10-004:**

api.cf.eu10-004.hana.ondemand.com

**cf-eu10-005:**

api.cf.eu10-005.hana.ondemand.com

</td>
<td valign="top">

**cf-eu10:**

eu10.hana.ondemand.com

**cf-eu10-002:**

eu10-002.hana.ondemand.com

**cf-eu10-003:**

eu10-003.hana.ondemand.com

**cf-eu10-004:**

eu10-004.hana.ondemand.com

**cf-eu10-005:**

eu10-005.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

eu11

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
<td valign="top">

cf-eu11

</td>
<td valign="top">

eu-central-1

</td>
<td valign="top">

18.156.140.38, 3.121.55.100, 35.156.198.246, 52.59.77.121, 18.185.57.85, 3.121.79.209, 3.67.237.8, 35.156.31.32, 3.65.63.251, 3.122.176.63, 18.198.13.57, 18.157.114.142, 18.184.172.97, 18.159.180.188, 35.157.5.44

</td>
<td valign="top">

18.156.209.198, 18.157.105.117, 3.124.207.41, 3.66.26.249, 3.72.216.204, 3.74.99.245

</td>
<td valign="top">

api.cf.eu11.hana.ondemand.com

</td>
<td valign="top">

eu11.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://eu-access.cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

eu13

</td>
<td valign="top">

Europe \(Milan\)

</td>
<td valign="top">

cf-eu13

</td>
<td valign="top">

eu-south-1

</td>
<td valign="top">

15.161.87.249, 15.161.194.156, 18.99.209.0/27, 35.152.224.143

</td>
<td valign="top">

15.161.2.170, 18.102.32.205, 18.102.85.10

</td>
<td valign="top">

api.cf.eu13.hana.ondemand.com

</td>
<td valign="top">

eu13.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

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

**cf-us10:**

52.200.16.71, 52.23.123.125, 52.202.170.155, 18.97.43.224/27

**cf-us10-001:**

52.0.214.195, 18.213.153.162, 54.227.144.195, 3.225.73.158, 34.233.151.91, 23.23.172.117, 3.222.22.16, 34.238.1.234, 34.194.239.31, 3.225.44.56, 34.201.208.150, 75.101.157.228

**cf-us10-002:**

54.162.233.194, 34.206.160.141, 35.168.80.144, 18.232.28.65, 54.82.224.146, 3.221.4.74, 18.211.12.227, 54.159.45.198, 72.44.51.245

</td>
<td valign="top">

**cf-us10:**

18.213.242.208, 3.214.110.153, 34.205.56.51

**cf-us10-001:**

3.227.182.44, 52.86.131.53, 3.220.114.17, 44.218.82.203, 44.219.57.163, 50.16.106.103

**cf-us10-002:**

107.20.66.86, 54.234.152.59, 34.202.68.0, 3.214.116.95, 54.144.230.36, 54.226.37.104

</td>
<td valign="top">

**cf-us10:**

api.cf.us10.hana.ondemand.com

**cf-us10-001:**

api.cf.us10-001.hana.ondemand.com

**cf-us10-002:**

api.cf.us10-002.hana.ondemand.com

</td>
<td valign="top">

**cf-us10:**

us10.hana.ondemand.com

**cf-us10-001:**

us10-001.hana.ondemand.com

**cf-us10-002:**

us10-002.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

us11

</td>
<td valign="top">

US West \(Oregon\)

</td>
<td valign="top">

cf-us11

</td>
<td valign="top">

us-west-2

</td>
<td valign="top">

44.244.167.160/28

</td>
<td valign="top">

34.211.82.149, 35.95.238.236, 100.20.19.69

</td>
<td valign="top">

api.cf.us11.hana.ondemand.com

</td>
<td valign="top">

us11.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

us30

</td>
<td valign="top">

US Central \(IA\)

</td>
<td valign="top">

cf-us30

</td>
<td valign="top">

us-central1

</td>
<td valign="top">

35.202.96.192, 35.193.171.152, 35.193.168.31, 35.202.69.204, 35.202.175.147, 35.193.69.164, 35.202.1.6, 23.236.63.113, 35.193.30.116, 35.202.66.196, 34.68.152.205, 35.222.158.222, 104.197.20.168, 35.232.105.70, 35.224.211.196, 35.222.192.158, 35.193.8.172, 34.171.4.220, 34.172.37.175, 34.170.206.220, 34.172.145.231, 35.222.38.254, 35.239.28.216, 34.134.91.47, 34.123.17.36, 35.202.205.85, 34.118.207.84, 35.193.6.192, 34.122.222.203, 104.197.157.121, 34.135.159.154, 35.223.208.27, 146.148.74.171, 34.132.192.46, 34.68.109.37, 104.198.49.58, 35.225.164.132

</td>
<td valign="top">

35.184.169.79

</td>
<td valign="top">

api.cf.us30.hana.ondemand.com

</td>
<td valign="top">

us30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

eu30

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
<td valign="top">

cf-eu30

</td>
<td valign="top">

europe-west3

</td>
<td valign="top">

34.107.28.38, 34.141.10.217, 34.141.116.52, 34.141.1.228, 34.141.123.52, 34.141.125.107, 34.141.46.51, 34.89.130.182, 34.89.146.167, 34.89.203.91, 34.89.232.158, 34.89.243.40, 35.198.83.71, 35.234.65.38, 35.242.208.222, 35.246.155.42, 35.246.171.35, 34.141.28.26, 34.159.160.86, 34.107.19.175, 34.159.165.29, 35.242.240.154, 34.141.73.130, 34.159.27.236, 34.89.152.211, 35.242.194.75, 35.246.235.253, 34.159.127.190, 34.141.82.126, 35.234.69.102, 34.89.231.53, 34.159.188.133, 35.246.203.194, 34.159.201.78, 34.141.112.232, 35.198.84.213, 34.89.165.33

</td>
<td valign="top">

35.198.143.110

</td>
<td valign="top">

api.cf.eu30.hana.ondemand.com

</td>
<td valign="top">

eu30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

in30

</td>
<td valign="top">

India \(Mumbai\)

</td>
<td valign="top">

cf-in30

</td>
<td valign="top">

asia-south1

</td>
<td valign="top">

34.93.27.36, 34.93.89.145, 34.93.92.210, 34.93.137.163, 34.93.148.247, 34.93.155.252, 34.93.166.164, 34.93.180.0, 34.93.221.129, 35.200.131.125, 35.200.144.1, 35.200.175.62, 35.200.183.224, 35.200.194.175, 35.200.198.26, 35.200.209.142, 35.244.29.120, 35.200.137.225, 34.100.186.241, 35.200.169.254, 35.200.151.131, 35.200.252.103, 35.244.15.103, 35.244.16.76, 34.93.255.115, 35.244.53.153, 35.200.168.60, 35.200.222.30, 34.100.178.164, 35.244.2.193, 34.93.11.49, 34.100.211.195, 34.100.151.15, 34.93.95.83, 34.100.215.143, 34.93.205.174, 34.93.159.24

</td>
<td valign="top">

34.93.125.74

</td>
<td valign="top">

api.cf.in30.hana.ondemand.com

</td>
<td valign="top">

in30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

il30

</td>
<td valign="top">

Israel \(Tel Aviv\)

</td>
<td valign="top">

cf-il30

</td>
<td valign="top">

me-west1

</td>
<td valign="top">

34.165.0.14, 34.165.0.115, 34.165.5.181, 34.165.5.246, 34.165.7.73, 34.165.12.173, 34.165.16.177, 34.165.16.210, 34.165.17.27, 34.165.18.240, 34.165.21.242, 34.165.24.112, 34.165.26.162, 34.165.37.171, 34.165.38.114, 34.165.40.240, 34.165.41.254, 34.165.80.207, 34.165.81.54, 34.165.110.15, 34.165.136.9, 34.165.150.108, 34.165.168.74, 34.165.171.197, 34.165.172.4, 34.165.194.20, 34.165.222.104, 34.165.223.90, 34.165.228.95, 34.165.231.165

</td>
<td valign="top">

34.165.59.26

</td>
<td valign="top">

api.cf.il30.hana.ondemand.com

</td>
<td valign="top">

il30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

jp30

</td>
<td valign="top">

Japan \(Osaka\)

</td>
<td valign="top">

cf-jp30

</td>
<td valign="top">

asia-northeast2

</td>
<td valign="top">

34.97.10.131, 34.97.19.128, 34.97.24.15, 34.97.27.89, 34.97.33.154, 34.97.36.44, 34.97.42.85, 34.97.52.48, 34.97.71.122, 34.97.75.108, 34.97.76.16, 34.97.79.22, 34.97.116.150, 34.97.117.3, 34.97.126.206, 34.97.131.43, 34.97.140.64, 34.97.141.186, 34.97.147.230, 34.97.177.45, 34.97.185.68, 34.97.186.214, 34.97.190.161, 34.97.201.159, 34.97.209.167, 34.97.210.16, 34.97.210.66, 34.97.221.101, 34.97.246.18, 34.97.246.150

</td>
<td valign="top">

34.97.168.169

</td>
<td valign="top">

api.cf.jp30.hana.ondemand.com

</td>
<td valign="top">

jp30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

jp31

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

cf-jp31

</td>
<td valign="top">

asia-northeast1

</td>
<td valign="top">

34.84.6.224, 34.84.32.55, 34.84.34.158, 34.84.126.44, 34.84.134.209, 34.84.141.254, 34.84.220.103, 34.84.225.24, 34.84.231.92, 34.85.20.250, 34.85.75.175, 34.146.79.159, 34.146.122.64, 34.146.132.93, 34.146.132.147, 34.146.174.212, 34.146.180.55, 34.146.195.200, 34.146.196.228, 34.146.212.140, 34.146.251.151, 34.146.252.171, 35.189.143.202, 35.189.159.75, 35.189.159.240, 35.194.111.248, 35.194.117.168, 35.200.34.120, 35.221.109.129, 35.243.117.227

</td>
<td valign="top">

34.84.96.118

</td>
<td valign="top">

api.cf.jp31.hana.ondemand.com

</td>
<td valign="top">

jp31.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

sa30

</td>
<td valign="top">

KSA \(Dammam - KSA Regulated Customers\)

</td>
<td valign="top">

cf-sa30

</td>
<td valign="top">

me-central2

</td>
<td valign="top">

34.166.4.164, 34.166.4.182, 34.166.8.22, 34.166.10.68, 34.166.19.145, 34.166.20.65, 34.166.37.166, 34.166.38.149, 34.166.39.3, 34.166.40.145, 34.166.41.104, 34.166.44.55, 34.166.46.73, 34.166.46.216, 34.166.47.18, 34.166.50.229, 34.166.52.69, 34.166.53.147, 34.166.55.78, 34.166.57.177, 34.166.60.109, 34.166.61.61, 34.166.61.119, 34.166.61.169, 34.166.61.173, 34.166.62.51, 34.166.62.206, 34.166.63.160, 34.166.64.6, 34.166.65.231

</td>
<td valign="top">

34.166.32.46

</td>
<td valign="top">

api.cf.sa30.hana.ondemand.com

</td>
<td valign="top">

sa30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

sa31

</td>
<td valign="top">

KSA \(Dammam - KSA Non-Regulated Customers\)

</td>
<td valign="top">

cf-sa31

</td>
<td valign="top">

me-central2

</td>
<td valign="top">

34.166.3.142, 34.166.11.228, 34.166.14.210, 34.166.38.222, 34.166.41.150, 34.166.43.17, 34.166.43.183, 34.166.48.219, 34.166.66.132, 34.166.69.32, 34.166.73.246, 34.166.78.126, 34.166.80.128, 34.166.87.5, 34.166.87.129, 34.166.87.229, 34.166.90.71, 34.166.93.161, 34.166.102.223, 34.166.104.146, 34.166.105.14, 34.166.106.220, 34.166.115.33, 34.166.115.46/31, 34.166.116.103, 34.166.117.89, 34.166.123.179, 34.166.125.172, 34.166.127.149

</td>
<td valign="top">

34.166.72.122

</td>
<td valign="top">

api.cf.sa31.hana.ondemand.com

</td>
<td valign="top">

sa31.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

ap30

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap30

</td>
<td valign="top">

australia-southeast1

</td>
<td valign="top">

34.40.139.113, 34.40.148.106, 34.40.148.145, 34.87.197.203, 34.87.227.150, 34.87.246.15, 34.87.246.56, 34.116.64.18, 34.116.71.248, 34.116.93.109, 34.116.96.225, 34.116.98.18, 34.151.82.192, 34.151.84.167, 34.151.92.254, 34.151.95.105, 34.151.110.186, 34.151.113.55, 35.189.5.90, 35.189.6.201, 35.189.24.237, 35.189.29.223, 35.197.168.71, 35.201.9.202, 35.201.25.163, 35.201.28.91, 35.244.87.121, 35.244.96.216, 35.244.100.190, 35.244.124.253

</td>
<td valign="top">

35.244.71.16

</td>
<td valign="top">

api.cf.ap30.hana.ondemand.com

</td>
<td valign="top">

ap30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

br30

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

cf-br30

</td>
<td valign="top">

southamerica-east1

</td>
<td valign="top">

34.95.136.152, 34.95.141.244, 34.95.169.207, 34.95.175.231, 34.95.181.247, 34.95.184.165, 34.95.200.14, 34.95.201.213, 34.95.225.218, 34.95.243.255, 34.95.246.4, 34.151.201.167, 34.151.205.45, 34.151.212.79, 34.151.214.13, 34.151.221.155, 34.151.234.215, 34.151.243.44, 34.151.246.168, 34.151.248.189, 35.198.10.217, 35.198.12.163, 35.198.39.142, 35.198.49.194, 35.199.67.49, 35.199.97.244, 35.199.110.212, 35.199.114.60, 35.247.219.74, 35.247.250.157

</td>
<td valign="top">

34.95.189.118

</td>
<td valign="top">

api.cf.br30.hana.ondemand.com

</td>
<td valign="top">

br30.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/) 

</td>
</tr>
<tr>
<td valign="top">

Alibaba Cloud

</td>
<td valign="top">

cn40

</td>
<td valign="top">

China \(Shanghai\)

</td>
<td valign="top">

cf-cn40

</td>
<td valign="top">

cn-shanghai

</td>
<td valign="top">

101.132.190.155, 106.14.165.33, 106.14.184.113

</td>
<td valign="top">

139.224.7.71

</td>
<td valign="top">

api.cf.cn40.platform.sapcloud.cn

</td>
<td valign="top">

cn40.platform.sapcloud.cn

</td>
<td valign="top">

[Open Cockpit](https://cockpit.cn40.platform.sapcloud.cn/cockpit)

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

</td>
<td valign="top">

eu01

</td>
<td valign="top">

Europe \(Frankfurt\) - EU Access Only

</td>
<td valign="top">

cf-eu01

</td>
<td valign="top">

eu-de-2

</td>
<td valign="top">

130.214.199.0/25, 130.214.252.0/25

</td>
<td valign="top">

130.214.199.128/28, 130.214.252.224/28

</td>
<td valign="top">

api.cf.eu01.hana.ondemand.com

</td>
<td valign="top">

eu01.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

</td>
<td valign="top">

ae01

</td>
<td valign="top">

UAE \(Dubai\)

</td>
<td valign="top">

cf-ae01

</td>
<td valign="top">

ap-ae-1

</td>
<td valign="top">

130.214.81.0/25, 130.214.83.128/25

</td>
<td valign="top">

130.214.81.128/26, 130.214.83.0/26

</td>
<td valign="top">

api.cf.ae01.hana.ondemand.com

</td>
<td valign="top">

ae01.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

</td>
<td valign="top">

eu02

</td>
<td valign="top">

Europe \(Rot\) - SAP EU Access

</td>
<td valign="top">

cf-eu02

</td>
<td valign="top">

eu-de-1

</td>
<td valign="top">

130.214.61.128/25, 130.214.159.0/25

</td>
<td valign="top">

130.214.61.0/26, 130.214.159.128/26

</td>
<td valign="top">

api.cf.eu02.hana.ondemand.com

</td>
<td valign="top">

eu02.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

</td>
<td valign="top">

us02

</td>
<td valign="top">

US West \(Colorado\)

</td>
<td valign="top">

cf-us02

</td>
<td valign="top">

na-us-2

</td>
<td valign="top">

130.214.2.0/25, 130.214.185.128/25

</td>
<td valign="top">

130.214.2.128/26, 130.214.185.0/26

</td>
<td valign="top">

api.cf.us02.hana.ondemand.com

</td>
<td valign="top">

us02.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
<tr>
<td valign="top">

SAP Cloud Infrastructure

</td>
<td valign="top">

ap01

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap01

</td>
<td valign="top">

ap-au-1

</td>
<td valign="top">

130.214.42.0/25, 130.214.151.128/25

</td>
<td valign="top">

130.214.42.128/26, 130.214.151.0/26

</td>
<td valign="top">

api.cf.ap01.hana.ondemand.com

</td>
<td valign="top">

ap01.hana.ondemand.com

</td>
<td valign="top">

[Open Cockpit](https://cockpit.btp.cloud.sap/)

</td>
</tr>
</table>

**Regions for Trial Accounts**


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

LB IPs \(ingress, for incoming requests\)

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

18.213.242.208, 3.214.110.153, 34.205.56.51

</td>
<td valign="top">

api.cf.us10.hana.ondemand.com

</td>
<td valign="top">

us10.hana.ondemand.com

</td>
<td valign="top">

[Trial](https://cockpit.hanatrial.ondemand.com/trial)

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ap21

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

cf-ap21

</td>
<td valign="top">

Southeast Asia

</td>
<td valign="top">

52.139.216.172, 20.195.24.178, 20.195.9.169

</td>
<td valign="top">

20.184.61.122

</td>
<td valign="top">

api.cf.ap21.hana.ondemand.com

</td>
<td valign="top">

ap21.hana.ondemand.com

</td>
<td valign="top">

[Trial](https://cockpit.hanatrial.ondemand.com/trial) 

</td>
</tr>
</table>



> ### Note:  
> Trial accounts and subaccounts on trial can no longer be created on eu10, Europe \(Frankfurt\).
> 
> Existing trial accounts and subaccounts are not affected.

> ### Note:  
> In the Cloud Foundry environment, IPs are controlled by the respective IaaS provider \(AWS, Azure, or Google Cloud\). IPs may change due to network updates on the provider side. Any planned changes will be announced at least four weeks before they take effect. For information on how to subscribe to updates, see [Platform Updates and Notifications](https://help.sap.com/docs/btp/sap-business-technology-platform/platform-updates-and-notifications).

> ### Note:  
> In the Cloud Foundry environment, the region in which a global account was created determines the API endpoint of all subaccounts associated with it. For example, subaccounts created in a global account in region **eu10** share the API endpoint URL `api.cf.eu10.hana.ondemand.com`.

**Related Information**  


[Regions for the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-for-kyma-environment)

[Regions and API Endpoints for the ABAP Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-for-abap-environment)

[Regions and Hosts Available for the Neo Environment](https://help.sap.com/docs/btp/sap-btp-neo-environment/regions-and-hosts-available-for-neo-environment)

