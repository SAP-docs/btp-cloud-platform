<!-- loio4eb2adf5cea24ed5940497ef26d3e4f3 -->

# Message Monitoring

You monitor the problems that occur in business event logging by using Application Interface Framework \(AIF\) . You can check the error status to identify failures. If there are failures in the queue, the business events aren't logged. However, the events aren't lost.



<a name="loio4eb2adf5cea24ed5940497ef26d3e4f3__section_xvy_py2_yqb"/>

## Prerequisites

To access Message Monitoring, create a business role and assign the role to a catalog. For more information about catalogs and other settings, refer to  <?sap-ot O2O class="- topic/xref " href="b0e61556c5317c65e10000000a44147b.xml" text="" desc="" xtrc="xref:1" xtrf="file:/home/builder/src/dita-all/jjq1673438782153/loio2080d0faf9d84ce6aa14caa4caa32935_en-US/src/content/localization/en-us/4eb2adf5cea24ed5940497ef26d3e4f3.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . Use the BEL\_IBD\_QUEUE\_MONITOR recipient to view Business Event Logging messages.



<a name="loio4eb2adf5cea24ed5940497ef26d3e4f3__section_z5f_vy2_yqb"/>

## Message Monitoring

1.  Log on to SAP Fiori launchpad.
2.  Open the *Message Monitoring Overview* app. For more information, refer to Message Monitoring Overview.
3.  Select *From* \(Date/Time\) and *To* \(Date/Time\) values to limit the time range for the monitoring records.

    > ### Note:  
    > The default time range is "last 2 weeks". If you want a custom time range, you can also select the values in the *From* and *To* fields.

4.  Choose *Go* to view the messages in this time range.
5.  Select the following cards to monitor the processing of business events for the business event log:

    -   Namespace: /BEL
    -   Interface:
        -   BEL\_IBD
        -   BEL\_LG\_MGR


    If you want to view only the error or success messages, choose *Error* or *Success*.

6.  On the *Message Monitoring* screen, in the *Log Messages* column, you can see all business event logging messages for your selected time range. All types of messages, such as success, error, warning, canceled, and in process are included.
7.  You can filter by *Status*.
8.  Choose *Message Details* to see all the message logs.

If a queue fails, the user can restart the queue manually with the AIF user interface. If errors occur during restart, create an incident under component **CA-GTF-BEL**.

