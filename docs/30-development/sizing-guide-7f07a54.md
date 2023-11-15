<!-- loio7f07a54e4ea14ec389b17796287d81bc -->

# Sizing Guide

This guide explains how much application runtime you must purchase to run HTML5 applications.

To develop and run HTML5 Applications using a standalone application router on Cloud Foundry, customers must purchase the Cloud Foundry application runtime.

The memory consumption for an idle application router is around 50 MB. An application router process should run with at least 256MB memory. It may require more memory depending on the application. These aspects influence the memory usage:

-   Number of concurrent users. The number of users that log on to the applications at the same time has the greatest impact on the required runtime.

-   Number of active sessions

-   JWT token size

-   Backend session cookies


Using the following table, estimate how much application runtime allocation you need, based on t-shirt sizes and the expected number of concurrent users.


<table>
<tr>
<th valign="top">

T-Shirt Size

</th>
<th valign="top">

Concurrent Users

</th>
<th valign="top">

Required Application Runtime \(in GB\)

</th>
</tr>
<tr>
<td valign="top">

S

</td>
<td valign="top">

1000

</td>
<td valign="top">

1

</td>
</tr>
<tr>
<td valign="top">

M

</td>
<td valign="top">

10000

</td>
<td valign="top">

4

</td>
</tr>
<tr>
<td valign="top">

L

</td>
<td valign="top">

30000

</td>
<td valign="top">

8

</td>
</tr>
<tr>
<td valign="top">

XL

</td>
<td valign="top">

80000

</td>
<td valign="top">

16

</td>
</tr>
</table>



<a name="loio7f07a54e4ea14ec389b17796287d81bc__section_pnn_bm5_hzb"/>

## Testing the Required Memory

The following tests provide measurements for different application router scenarios. You can use the measurements to approximately calculate the amount of memory that will be required by the application router. The tables contain the exact results from the measurements with Node.js v6.9.1. We recommend assuming higher numbers for productive use.

All measurements were done with authentication. If you have additional session content and want to count the session memory consumption, take a look at what is stored in the session \(see "Sessions" in [Application Router Configuration](application-router-configuration-c19f165.md)\). You must add the calculated session size taking into account the number of different users and the session timeout. In our tests,the JWT token alone required approximately 4 KB.



### Testing the HTTP Traffic

We tested two different test scenarios

-   Scenario 1: A 'Hello World' static resource is served.

-   Scenario 2:

    -   A 'Hello World' static resource is served.

    -   A static resource of 84.78 KB \(compressed by application router to 28.36 KB\) is served.

    -   A backend application which returns a payload of 80 kb \(compressed by application router to 58 KB\) is called.

    -   Another backend which returns a payload of 160 KB \(compressed by application router to 116 KB\) is called.



**Results for HTTP Traffic Tests**


<table>
<tr>
<th valign="top">

Memory Limit

</th>
<th valign="top">

Max. Number of Sessions - Scenario 1

</th>
<th valign="top">

Max. Number of Sessions - Scenario 2

</th>
</tr>
<tr>
<td valign="top">

256 MB

</td>
<td valign="top">

5300

</td>
<td valign="top">

800

</td>
</tr>
<tr>
<td valign="top">

512 MB

</td>
<td valign="top">

13300

</td>
<td valign="top">

2300

</td>
</tr>
<tr>
<td valign="top">

1 GB

</td>
<td valign="top">

30100

</td>
<td valign="top">

8400

</td>
</tr>
<tr>
<td valign="top">

2 GB

</td>
<td valign="top">

65500

</td>
<td valign="top">

19500

</td>
</tr>
<tr>
<td valign="top">

4 GB

</td>
<td valign="top">

134900

</td>
<td valign="top">

46400

</td>
</tr>
<tr>
<td valign="top">

8 GB

</td>
<td valign="top">

275500

</td>
<td valign="top">

102300

</td>
</tr>
</table>



### Testing Web Socket Traffic

We tested two different test scenarios:

-   Scenario 1:

    -   A 'Hello World' static resource is served.

    -   A single 'Hello' message is sent and then received through a web socket connection.


-   Scenario 2:

    -   A 'Hello World' static resource is served.

    -   A static resource of 84.78 KB \(compressed by the application router to 28.36 KB\) is served.

    -   A backend which returns a payload of 80 KB over a web socket is called.

    -   Another backend which returns a payload of 160 KB over a web socket is called.



> ### Note:  
> Web sockets require a certain number of file handles to be available for the process. This number is approximately two times the number of the sessions. In Cloud Foundry, the default value is 16384.

**Results for Web Socket Traffic Tests**


<table>
<tr>
<th valign="top">

Memory Limit

</th>
<th valign="top">

Max. Number of Sessions - Scenario 1

</th>
<th valign="top">

Max. Number of Sessions - Scenario 1

</th>
</tr>
<tr>
<td valign="top">

256 MB

</td>
<td valign="top">

600

</td>
<td valign="top">

300

</td>
</tr>
<tr>
<td valign="top">

512 MB

</td>
<td valign="top">

1100

</td>
<td valign="top">

500

</td>
</tr>
<tr>
<td valign="top">

1 GB

</td>
<td valign="top">

3100

</td>
<td valign="top">

800

</td>
</tr>
<tr>
<td valign="top">

2 GB

</td>
<td valign="top">

6500

</td>
<td valign="top">

1400

</td>
</tr>
<tr>
<td valign="top">

4 GB

</td>
<td valign="top">

13300

</td>
<td valign="top">

2900

</td>
</tr>
<tr>
<td valign="top">

8 GB

</td>
<td valign="top">

20700

</td>
<td valign="top">

6100

</td>
</tr>
</table>

> ### Note:  
> `--max-old-space-size` restricts the amount of memory used in the JavaScript heap. Its default value is below 2 GB. To use the full resources that has been provided to the application, the value of this restriction should be set to a number equal to the memory limit of the whole application.
> 
> For example, if the application memory is limited to 2 GB, set the V8 heap limit in the `package.json` file as follows:
> 
> ```
> "scripts": {
>         	"start": "node --max-old-space-size=2048 node_modules/@sap/approuter/approuter.js"
>    	}
> 
> ```

