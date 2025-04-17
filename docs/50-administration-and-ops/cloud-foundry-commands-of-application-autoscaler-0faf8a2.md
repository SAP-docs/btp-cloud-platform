<!-- loio0faf8a26460a4fc99c5c72ce0113dd36 -->

# Cloud Foundry Commands of Application Autoscaler

The Application Autoscaler plugin for the Cloud Foundry Command Line Interface \(cf CLI\) includes commands that you can use to get some insights into your scaling policies and for debugging.



**Commands for the Application Autoscaler CLI Plugin**


<table>
<tr>
<th valign="top">

Command

</th>
<th valign="top">

Alias

</th>
<th valign="top">

Usage

</th>
<th valign="top">

Options

</th>
<th valign="top">

Description

</th>
<th valign="top">

Examples

</th>
</tr>
<tr>
<td valign="top">

`cf autoscaling-policy`

</td>
<td valign="top">

`asp`

</td>
<td valign="top">

`cf autoscaling-policy APP_NAME [--output PATH_TO_FILE]`

</td>
<td valign="top">

`--output` : dump the policy to a file in JSON format

</td>
<td valign="top">

Retrieve the scaling policy of an application. The policy will be displayed in JSON format.

</td>
<td valign="top">

View scaling policy, replace APP\_NAME with the name of your application:

```

$ cf autoscaling-policy APP_NAME
									
Showing policy for app APP_NAME...
{
	"instance_min_count": 1,
	"instance_max_count": 5,
	"scaling_rules": [
		{
			"metric_type": "memoryused",
			"breach_duration_secs": 120,
			"threshold": 15,
			"operator": ">=",
			"cool_down_secs": 120,
			"adjustment": "+1"
		},
		{
			"metric_type": "memoryused",
			"breach_duration_secs": 120,
			"threshold": 10,
			"operator": "<",
			"cool_down_secs": 120,
			"adjustment": "-1"
		}
	]
}
```

Dump the scaling policy to a file in JSON format:

```

$ cf asp APP_NAME --output PATH_TO_FILE
									
Saving policy for app APP_NAME to PATH_TO_FILE...
OK
```



</td>
</tr>
<tr>
<td valign="top">

`cf attach-autoscaling-policy`

</td>
<td valign="top">

`aasp`

</td>
<td valign="top">

`cf attach-autoscaling-policy APP_NAME PATH_TO_POLICY_FILE`

</td>
<td valign="top">

 

</td>
<td valign="top">

Attach a scaling policy to an application. The policy file must be a JSON file. See [policy specification](https://github.com/SAP-docs/btp-application-autoscaler/blob/2f16b768f9352ebde7aba72f42a965bfec26eb8c/docs/defining-a-scaling-policy-79f443a.md) for the policy format.

</td>
<td valign="top">

```
$ cf attach-autoscaling-policy APP_NAME PATH_TO_POLICY_FILE
									
Attaching policy for app APP_NAME...
OK
```



</td>
</tr>
<tr>
<td valign="top">

`cf detach-autoscaling-policy`

</td>
<td valign="top">

`dasp`

</td>
<td valign="top">

`cf detach-autoscaling-policy APP_NAME`

</td>
<td valign="top">

 

</td>
<td valign="top">

Detach the scaling policy from an application. The policy will be deleted when detached.

</td>
<td valign="top">

```
$ cf detach-autoscaling-policy APP_NAME
								
Detaching policy for app APP_NAME...
OK
```



</td>
</tr>
<tr>
<td valign="top">

`cf autoscaling-metrics`

</td>
<td valign="top">

`asm`

</td>
<td valign="top">

`cf autoscaling-metrics APP_NAME METRIC_NAME [--start START_TIME] [--end END_TIME] [--asc] [--output PATH_TO_FILE]`

</td>
<td valign="top">

-   METRIC\_NAME : default metrics "memoryused, memoryutil, responsetime, throughput, cpu" or customized name for your own metrics.
-   \--start : start time of metrics collected with format yyyy-MM-ddTHH:mm:ss+/-HH:mm or yyyy-MM-ddTHH:mm:ssZ, default to very beginning if not specified.
-   \--end : end time of the metrics collected with format yyyy-MM-ddTHH:mm:ss+/-HH:mm or yyyy-MM-ddTHH:mm:ssZ, default to current time if not speficied.
-   \--asc : display in ascending order, default to descending order if not specified
-   \--output : dump the metrics to a file



</td>
<td valign="top">

Retrieve the aggregated metrics of an application. You can specify the start/end time of the returned query result and the display order \(ascending or descending\). The metrics are shown in a table.

</td>
<td valign="top">

```

$ cf autoscaling-metrics APP_NAME memoryused --start 2018-12-27T11:49:00+08:00 --end 2018-12-27T11:52:20+08:00 --asc
								
Retreiving aggregated metrics for app APP_NAME...
Metrics Name        Value       Timestamp
memoryused          62MB        2018-12-27T11:49:00+08:00
memoryused          62MB        2018-12-27T11:49:40+08:00
memoryused          61MB        2018-12-27T11:50:20+08:00
memoryused          62MB        2018-12-27T11:51:00+08:00
memoryused          62MB        2018-12-27T11:51:40+08:00
```

**Description of table-columns:**

-   Metrics Name: name of the current metric item
-   Value: the value of the current metric item with unit
-   Timestamp: collect time of the current metric item



</td>
</tr>
<tr>
<td valign="top">

`cf autoscaling-history`

</td>
<td valign="top">

`ash`

</td>
<td valign="top">

`cf autoscaling-history APP_NAME [--start START_TIME] [--end END_TIME] [--asc] [--output PATH_TO_FILE]`

</td>
<td valign="top">

-   \--start : start time of the scaling history with format yyyy-MM-ddTHH:mm:ss+/-HH:mm or yyyy-MM-ddTHH:mm:ssZ, default to very beginning if not specified.
-   \--end : end time of the scaling history with format yyyy-MM-ddTHH:mm:ss+/-HH:mm or yyyy-MM-ddTHH:mm:ssZ, default to current time if not speficied.
-   \--asc : display in ascending order, default to descending order if not specified

-   \--output : dump the scaling history to a file



</td>
<td valign="top">

Retrieve the scaling event history of an application. You can specify the start/end time of the returned query result, and the display order \(ascending or descending\). The scaling event history is shown in a table.

</td>
<td valign="top">

```

$ cf autoscaling-history APP_NAME --start 2018-08-16T17:58:53+08:00 --end 2018-08-16T18:01:00+08:00 --asc
									
Showing history for app APP_NAME...
Scaling Type        Status          Instance Changes        Time                            Action                                                          Error
dynamic             failed          2->-1                   2018-08-16T17:58:53+08:00       -1 instance(s) because throughput  10rps for 120 seconds        app does not have policy set
dynamic             succeeded       2->3                    2018-08-16T17:59:33+08:00       +1 instance(s) because memoryused >= 15MB for 120 seconds
scheduled           succeeded       3->6                    2018-08-16T18:00:00+08:00       3 instance(s) because limited by min instances 6
```

**Description of table-columns:**

-   Scaling Type: the trigger type of the scaling action, possible scaling types: dynamic and scheduled
    -   dynamic: the scaling action is triggered by a dynamic rule \(memoryused, memoryutil, responsetime or throughput\)
    -   scheduled: the scaling action is triggered by a recurring schedule or specific date rule

-   Status: the result of the scaling action: succeeded or failed
-   Instance Changes: how the instances number get changed \(e.g. 1-\>2 means the application was scaled out from 1 instance to 2\)
-   Time: the finish time of scaling action, no mater succeeded or failed
-   Action: the detail information about why and how the application scaled
-   Error: the reason why scaling failed



</td>
</tr>
</table>

**Related Information**  


[What Is Application Autoscaler?](https://help.sap.com/viewer/7472b7d13d5d4862b2b06a730a2df086/Cloud/en-US/45341f37cf6e4738a4b7cd20f18350de.html "Automatically scale your applications to meet their dynamic resource needs.") :arrow_upper_right:

[Initial Setup](https://help.sap.com/viewer/7472b7d13d5d4862b2b06a730a2df086/Cloud/en-US/f3e7fa907e9d4da89fc55602818bd6f4.html "Create an instance of the Application Autoscaler service and bind it to your application. Install the Autoscaler plugin for the Cloud Foundry Command Line Interface (cf CLI).") :arrow_upper_right:

[Defining a Scaling Policy](https://help.sap.com/viewer/7472b7d13d5d4862b2b06a730a2df086/Cloud/en-US/79f443abe6b448ce9b606d10fd816f5c.html "Define a policy to scale your application instances either dynamically or based on schedules.") :arrow_upper_right:

