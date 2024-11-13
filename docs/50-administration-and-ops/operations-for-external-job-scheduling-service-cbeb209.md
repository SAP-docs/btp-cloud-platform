<!-- loiocbeb209d8bea43ddb4277ae95aa24759 -->

# Operations for External Job Scheduling Service

The external job scheduling service API offers the following operations:


<table>
<tr>
<th valign="top">

Operation

</th>
<th valign="top">

HTTP Method

</th>
<th valign="top">

Sample URL

</th>
</tr>
<tr>
<td valign="top">

[Read an Application Job Without Parameters](read-an-application-job-without-parameters-8cd59f9.md)

</td>
<td valign="top">

GET

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobHeaderSet\(JobName='JobName',JobRunCount='JobCount'\)?$expand=JobStepSet/JobStepLogInfoSet/JobLogMessageSet

</td>
</tr>
<tr>
<td valign="top">

[Read Application Job Templates](read-application-job-templates-b4f28ea.md)

</td>
<td valign="top">

GET

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobTemplateSet

</td>
</tr>
<tr>
<td valign="top">

[Schedule an Application Job](schedule-an-application-job-f2a48b0.md)

</td>
<td valign="top">

POST

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobSchedule?JobTemplateName='TemplateName'&JobText='Test'&JobUser='BusinessUser'&TestModeInd=false&JobParameterValues=''

</td>
</tr>
<tr>
<td valign="top">

[Read Application Job Status](read-application-job-status-1823561.md)

</td>
<td valign="top">

GET

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobStatusGet?JobName='JobName'&JobRunCount='JobCount'

</td>
</tr>
<tr>
<td valign="top">

[Abort a Running Application Job](abort-a-running-application-job-c018248.md) 

</td>
<td valign="top">

POST

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobAbort?JobName='JobName'&JobRunCount='JobCount'

</td>
</tr>
<tr>
<td valign="top">

[Cancel an Application Job](cancel-an-application-job-3018768.md)

</td>
<td valign="top">

POST

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobCancel?JobName='JobName'&JobRunCount='JobCount'

</td>
</tr>
<tr>
<td valign="top">

[Read Detailed Job and Step Information](read-detailed-job-and-step-information-7a63794.md) 

</td>
<td valign="top">

GET

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobinfoGet?JobName='JobName'&JobRunCount='JobCount'

</td>
</tr>
<tr>
<td valign="top">

[Read Application Job Status Texts](read-application-job-status-texts-2473b53.md)

</td>
<td valign="top">

GET

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobStatusInfoSet

</td>
</tr>
<tr>
<td valign="top">

[Restart a Failed Application Job](restart-a-failed-application-job-08a32d9.md)

</td>
<td valign="top">

POST

</td>
<td valign="top">

<host\>/sap/opu/odata/sap/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobRestart?JobName='JobName'&JobRunCount='JobCount'&JobRestartMode='E'

</td>
</tr>
<tr>
<td valign="top">

[Check Parameters for Scheduling a Job](check-parameters-for-scheduling-a-job-b331bde.md)

</td>
<td valign="top">

POST

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobScheduleCheck? JobTemplateName='TemplateName'&JobParameterValues='ParameterValueString'

</td>
</tr>
<tr>
<td valign="top">

[Retrieve Application Job Parameters](retrieve-application-job-parameters-117063a.md)

</td>
<td valign="top">

GET

</td>
<td valign="top">

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobParamValuesGet?JobName='JobName'&JobCount='JobCount'

and

<host\>/sap/opu/odata/SAP/BC\_EXT\_APPJOB\_MANAGEMENT;v=0002/JobParamValuesStructGet?JobName='JobName'&JobCount='JobCount'

</td>
</tr>
</table>

For more information on these operations, see [3383044](https://me.sap.com/notes/3383044).

**Working with $Batch**

The OData implementation can optionally support running multiple operations sent in a single HTTP request through the use of batching. This is especially useful when scheduling application jobs with a large amount of application job parameters, as these parameters are added to the request URL and may exceed the maximum number of allowed characters. For details, see the chapter **Batch** on page 17 of [3383044](https://me.sap.com/notes/3383044).

**Error Handling**

In case of an error, the external job scheduling service API sets the http status code to 400 and returns a message of an SAP message class. In the http response, you'll see the message class, the message number, and the message text. One example:

> ### Sample Code:  
> ```
> <code>APJ_RT/003</code><message xml:lang="en">Job doesn't exist.</message>
> ```

In this example, the message with number 003 of message class `APJ_RT` and the text "Job doesn't exist" was returned.

In most cases, a message of the message class `APJ_RT` is used. The following table lists the message numbers and the corresponding texts:


<table>
<tr>
<th valign="top">

Message code

</th>
<th valign="top">

Message constant

</th>
<th valign="top">

Text

</th>
</tr>
<tr>
<td valign="top">

001

</td>
<td valign="top">

TECHNICAL\_ERROR

</td>
<td valign="top">

Job was aborted due to a technical error.

</td>
</tr>
<tr>
<td valign="top">

002

</td>
<td valign="top">

no\_appl\_log\_found

</td>
<td valign="top">

No application log found

</td>
</tr>
<tr>
<td valign="top">

003

</td>
<td valign="top">

no\_job\_exists

</td>
<td valign="top">

Job doesn't exist.

</td>
</tr>
<tr>
<td valign="top">

004

</td>
<td valign="top">

cancel\_job\_failed

</td>
<td valign="top">

Job &1 couldn't be canceled.

</td>
</tr>
<tr>
<td valign="top">

005

</td>
<td valign="top">

no\_cancel\_privilege

</td>
<td valign="top">

User &1 has no authorization to cancel job &2.

</td>
</tr>
<tr>
<td valign="top">

006

</td>
<td valign="top">

delete\_job\_failed

</td>
<td valign="top">

Job &1 couldn't be deleted.

</td>
</tr>
<tr>
<td valign="top">

007

</td>
<td valign="top">

no\_job\_delete\_privilege

</td>
<td valign="top">

User &1 has no authorization to delete job &2.

</td>
</tr>
<tr>
<td valign="top">

008

</td>
<td valign="top">

job\_cancel\_internal\_error

</td>
<td valign="top">

Job &1 couldn't be canceled due to an internal error.

</td>
</tr>
<tr>
<td valign="top">

009

</td>
<td valign="top">

job\_cancellation\_succesful

</td>
<td valign="top">

Job &1 has been canceled.

</td>
</tr>
<tr>
<td valign="top">

010

</td>
<td valign="top">

job\_deletion\_succesful

</td>
<td valign="top">

Job &1 has been deleted.

</td>
</tr>
<tr>
<td valign="top">

011

</td>
<td valign="top">

job\_wrong\_state\_for\_deletion

</td>
<td valign="top">

You can't delete job &1 due to its status.

</td>
</tr>
<tr>
<td valign="top">

012

</td>
<td valign="top">

no\_runs\_for\_job\_found

</td>
<td valign="top">

Job &1 has no runs.

</td>
</tr>
<tr>
<td valign="top">

013

</td>
<td valign="top">

job\_schedule\_successfully

</td>
<td valign="top">

Job &1 has been scheduled.

</td>
</tr>
<tr>
<td valign="top">

014

</td>
<td valign="top">

job\_catalog\_entry\_not\_found

</td>
<td valign="top">

Job catalog entry &1 doesn't exist.

</td>
</tr>
<tr>
<td valign="top">

015

</td>
<td valign="top">

job\_template\_entry\_not\_found

</td>
<td valign="top">

Job template &1 doesn't exist.

</td>
</tr>
<tr>
<td valign="top">

016

</td>
<td valign="top">

report\_for\_job\_not\_found

</td>
<td valign="top">

Job &1 couldn't be created.

</td>
</tr>
<tr>
<td valign="top">

017

</td>
<td valign="top">

job\_creation\_failed

</td>
<td valign="top">

Report for job &1 couldn't be found.

</td>
</tr>
<tr>
<td valign="top">

018

</td>
<td valign="top">

job\_metadata\_inconsistent

</td>
<td valign="top">

Job &1 metadata are inconsistent.

</td>
</tr>
<tr>
<td valign="top">

019

</td>
<td valign="top">

read\_job\_log\_failed

</td>
<td valign="top">

Log for job &1 couldn't be read.

</td>
</tr>
<tr>
<td valign="top">

020

</td>
<td valign="top">

job\_start\_immediate\_failed

</td>
<td valign="top">

Job &1 couldn't start immediately

</td>
</tr>
<tr>
<td valign="top">

021

</td>
<td valign="top">

job\_invalid\_startdate

</td>
<td valign="top">

Job &1 has an invalid start date.

</td>
</tr>
<tr>
<td valign="top">

022

</td>
<td valign="top">

job\_close\_failed

</td>
<td valign="top">

Job &1 couldn't be scheduled.

</td>
</tr>
<tr>
<td valign="top">

023

</td>
<td valign="top">

job\_list\_internal\_error

</td>
<td valign="top">

Internal error occurred during job list processing.

</td>
</tr>
<tr>
<td valign="top">

024

</td>
<td valign="top">

user\_no\_auth\_report

</td>
<td valign="top">

User &1 not authorized to schedule report &2. Report on BC-SRV-APS-APJ.

</td>
</tr>
<tr>
<td valign="top">

025

</td>
<td valign="top">

future\_schedules\_restricted

</td>
<td valign="top">

Job &1 was restricted to 1000 scheduled runs.

</td>
</tr>
<tr>
<td valign="top">

026

</td>
<td valign="top">

job\_completed\_wo\_info

</td>
<td valign="top">

Job completed without errors

</td>
</tr>
<tr>
<td valign="top">

027

</td>
<td valign="top">

no\_auth\_appl\_log

</td>
<td valign="top">

User &1 is not authorized to read the log.

</td>
</tr>
<tr>
<td valign="top">

028

</td>
<td valign="top">

no\_auth\_job\_details

</td>
<td valign="top">

User &1 is not authorized to read the job details.

</td>
</tr>
<tr>
<td valign="top">

029

</td>
<td valign="top">

no\_auth\_job\_log

</td>
<td valign="top">

User &1 is not authorized to read the job log.

</td>
</tr>
<tr>
<td valign="top">

030

</td>
<td valign="top">

no\_auth\_job\_delete

</td>
<td valign="top">

User &1 is not authorized to delete the job.

</td>
</tr>
<tr>
<td valign="top">

031

</td>
<td valign="top">

no\_auth\_job\_cancel

</td>
<td valign="top">

User &1 is not authorized to cancel the job.

</td>
</tr>
<tr>
<td valign="top">

032

</td>
<td valign="top">

job\_schduling\_failed

</td>
<td valign="top">

Job couldn't be scheduled.

</td>
</tr>
<tr>
<td valign="top">

033

</td>
<td valign="top">

job\_no\_end\_date

</td>
<td valign="top">

No end date supplied for job &1.

</td>
</tr>
<tr>
<td valign="top">

034

</td>
<td valign="top">

job\_start\_before\_end\_date

</td>
<td valign="top">

Job &1 must start before the end date.

</td>
</tr>
<tr>
<td valign="top">

035

</td>
<td valign="top">

job\_no\_max\_iterations

</td>
<td valign="top">

Enter a number of iterations for the job &1.

</td>
</tr>
<tr>
<td valign="top">

036

</td>
<td valign="top">

job\_end\_cond\_ignored

</td>
<td valign="top">

End date of job &1 will be ignored due to missing recurrence pattern.

</td>
</tr>
<tr>
<td valign="top">

037

</td>
<td valign="top">

job\_aborted

</td>
<td valign="top">

An error occurred. Please create an incident on component &1.

</td>
</tr>
<tr>
<td valign="top">

038

</td>
<td valign="top">

job\_cancel\_checking\_failed

</td>
<td valign="top">

Job &1 couldn't be canceled: Check of job failed

</td>
</tr>
<tr>
<td valign="top">

039

</td>
<td valign="top">

job\_cancel\_not\_exist

</td>
<td valign="top">

Job couldn't be canceled: Job does not exist.

</td>
</tr>
<tr>
<td valign="top">

040

</td>
<td valign="top">

JOB\_CANCEL\_NOT\_RUNNING

</td>
<td valign="top">

Job couldn't be canceled: Job is not running.

</td>
</tr>
<tr>
<td valign="top">

041

</td>
<td valign="top">

job\_delete\_event\_failed

</td>
<td valign="top">

Job &1 couldn't be deleted: Event scheduling can't be deleted

</td>
</tr>
<tr>
<td valign="top">

042

</td>
<td valign="top">

job\_delete\_steps\_failed

</td>
<td valign="top">

Job &1 couldn't be deleted: Job steps couldn't be deleted

</td>
</tr>
<tr>
<td valign="top">

043

</td>
<td valign="top">

job\_delete\_time\_failed

</td>
<td valign="top">

Job &1 couldn't be deleted: Deadline scheduling can't be deleted

</td>
</tr>
<tr>
<td valign="top">

044

</td>
<td valign="top">

job\_delete\_derelease

</td>
<td valign="top">

Job &1 couldn't be deleted: Previous job can't be modified

</td>
</tr>
<tr>
<td valign="top">

045

</td>
<td valign="top">

job\_delete\_enq\_pre

</td>
<td valign="top">

Job &1 couldn't be deleted: Succeeding job can't be locked

</td>
</tr>
<tr>
<td valign="top">

046

</td>
<td valign="top">

job\_delete\_enq\_suc

</td>
<td valign="top">

Job &1 couldn't be deleted: Previous job can't be locked

</td>
</tr>
<tr>
<td valign="top">

047

</td>
<td valign="top">

job\_delete\_enq\_tbtco

</td>
<td valign="top">

Job &1 couldn't be deleted: Job can't be locked

</td>
</tr>
<tr>
<td valign="top">

048

</td>
<td valign="top">

job\_delete\_update\_pre

</td>
<td valign="top">

Job &1 couldn't be deleted: Previous job can't be modified

</td>
</tr>
<tr>
<td valign="top">

049

</td>
<td valign="top">

job\_delete\_update\_suc

</td>
<td valign="top">

Job &1 couldn't be deleted: Succeeding job can't be modified

</td>
</tr>
<tr>
<td valign="top">

050

</td>
<td valign="top">

job\_delete\_commit\_failed

</td>
<td valign="top">

Job &1 couldn't be deleted: A technical error occurred.

</td>
</tr>
<tr>
<td valign="top">

051

</td>
<td valign="top">

job\_delete\_already\_run

</td>
<td valign="top">

Job &1 couldn't be deleted: Job has already been published.

</td>
</tr>
<tr>
<td valign="top">

052

</td>
<td valign="top">

illegal\_report\_or\_variant

</td>
<td valign="top">

Report name or variant name contains invalid characters.

</td>
</tr>
<tr>
<td valign="top">

053

</td>
<td valign="top">

illegal\_variantname

</td>
<td valign="top">

Variant couldn't be created: Its name is empty, or contains '&' or '%'.

</td>
</tr>
<tr>
<td valign="top">

054

</td>
<td valign="top">

no\_auth\_variant\_create

</td>
<td valign="top">

User &1 is not authorized to create a variant.

</td>
</tr>
<tr>
<td valign="top">

055

</td>
<td valign="top">

variant\_not\_executed

</td>
<td valign="top">

Variant couldn't be created: Variant can't be executed.

</td>
</tr>
<tr>
<td valign="top">

056

</td>
<td valign="top">

variant\_no\_report\_exists

</td>
<td valign="top">

Variant couldn't be created: Report doesn't exist.

</td>
</tr>
<tr>
<td valign="top">

057

</td>
<td valign="top">

variant\_no\_report\_supplied

</td>
<td valign="top">

Variant couldn't be created: Report is not of type 1.

</td>
</tr>
<tr>
<td valign="top">

058

</td>
<td valign="top">

variant\_locked

</td>
<td valign="top">

Variant couldn't be created: Variant is locked.

</td>
</tr>
<tr>
<td valign="top">

059

</td>
<td valign="top">

variant\_lock\_enqueue\_error

</td>
<td valign="top">

Variant couldn't be created: Internal error from enqueue server

</td>
</tr>
<tr>
<td valign="top">

060

</td>
<td valign="top">

job\_must\_not\_periodic

</td>
<td valign="top">

Job &1 must not be periodic. Report incident on component BC-SRV-APS-APJ.

</td>
</tr>
<tr>
<td valign="top">

061

</td>
<td valign="top">

job\_wrong\_periodic\_value

</td>
<td valign="top">

Value &1 for recurrence pattern is invalid for job &2.

</td>
</tr>
<tr>
<td valign="top">

062

</td>
<td valign="top">

invalid\_factory\_calendar

</td>
<td valign="top">

Job &1 is not scheduled due to invalid calendar.

</td>
</tr>
<tr>
<td valign="top">

063

</td>
<td valign="top">

invalid\_restriction\_code

</td>
<td valign="top">

Job &1 is not scheduled due to invalid restriction code

</td>
</tr>
<tr>
<td valign="top">

064

</td>
<td valign="top">

job\_list\_filter\_failed

</td>
<td valign="top">

Filter for job list couldn't be applied.

</td>
</tr>
<tr>
<td valign="top">

065

</td>
<td valign="top">

job\_delete\_internal\_error

</td>
<td valign="top">

Job couldn't be deleted due to an internal error.

</td>
</tr>
<tr>
<td valign="top">

066

</td>
<td valign="top">

INVALID\_MONTH\_SHIFT\_DIR

</td>
<td valign="top">

Invalid shift direction for days of month

</td>
</tr>
<tr>
<td valign="top">

067

</td>
<td valign="top">

WEEKDAY\_WRONG\_STARTDATE

</td>
<td valign="top">

Start date and day of recurrence must be the same weekday.

</td>
</tr>
<tr>
<td valign="top">

068

</td>
<td valign="top">

INVALID\_TIMEZONE

</td>
<td valign="top">

Time zone &1 is invalid.

</td>
</tr>
<tr>
<td valign="top">

069

</td>
<td valign="top">

INVALID\_FC\_ID

</td>
<td valign="top">

Calendar &1 is invalid.

</td>
</tr>
<tr>
<td valign="top">

070

</td>
<td valign="top">

SCHEDULING\_DATE\_ADJUSTED

</td>
<td valign="top">

Start date was adjusted to fit the recurrence pattern.

</td>
</tr>
<tr>
<td valign="top">

071

</td>
<td valign="top">

INVALID\_SCHEDULING\_START\_TS

</td>
<td valign="top">

Job must start before the end date.

</td>
</tr>
<tr>
<td valign="top">

072

</td>
<td valign="top">

SELECT\_AT\_LEAST\_ONE\_WEEKDAY

</td>
<td valign="top">

For weekly recurrence, select at least one weekday.

</td>
</tr>
<tr>
<td valign="top">

073

</td>
<td valign="top">

CREATE\_JOB\_VARIANT\_FAILED

</td>
<td valign="top">

Job variant couldn't be created.

</td>
</tr>
<tr>
<td valign="top">

074

</td>
<td valign="top">

VALUES\_OF\_READ\_ONLY\_PARAM\_REM

</td>
<td valign="top">

Parameter &1 has been removed because it is read-only

</td>
</tr>
<tr>
<td valign="top">

075

</td>
<td valign="top">

USER\_NO\_AUTH\_TO\_SCHEDULE\_JOB

</td>
<td valign="top">

Parameter &1 has been removed because it's read-only

</td>
</tr>
<tr>
<td valign="top">

076

</td>
<td valign="top">

JOB\_CANCELED\_BY\_USER

</td>
<td valign="top">

Job was canceled by user &1.

</td>
</tr>
<tr>
<td valign="top">

077

</td>
<td valign="top">

NO\_AUTH\_SCHEDULE\_FOR\_USER

</td>
<td valign="top">

User &1 has no authorization to schedule the job.

</td>
</tr>
<tr>
<td valign="top">

078

</td>
<td valign="top">

PARAM\_CHANGE\_BEFORE\_SCHEDULE

</td>
<td valign="top">

Invalid change of parameter when scheduling. Please open a ticket on &1

</td>
</tr>
<tr>
<td valign="top">

079

</td>
<td valign="top">

INVALID\_JOB\_RUN\_STATUS

</td>
<td valign="top">

Invalid job run status.

</td>
</tr>
<tr>
<td valign="top">

080

</td>
<td valign="top">

JOBCATALOG\_IS\_NOT\_BASIC

</td>
<td valign="top">

Job catalog is not basic.

</td>
</tr>
<tr>
<td valign="top">

081

</td>
<td valign="top">

JOB\_RESTART\_INCORRECT\_STATUS

</td>
<td valign="top">

Can't restart the job due to the status

</td>
</tr>
<tr>
<td valign="top">

082

</td>
<td valign="top">

JOB\_RESTART\_INCORRECT\_MODE

</td>
<td valign="top">

Can't restart the job after the last step

</td>
</tr>
<tr>
<td valign="top">

083

</td>
<td valign="top">

INVALID\_USER

</td>
<td valign="top">

User &1 doesn't exist or is invalid.

</td>
</tr>
</table>

