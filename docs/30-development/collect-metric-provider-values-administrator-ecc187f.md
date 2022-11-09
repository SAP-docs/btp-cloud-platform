<!-- loioecc187f05d384394a57f3fc187a14dd1 -->

# Collect Metric Provider Values \(Administrator\)

As an administrator, you must create an application job to collect metric providers and their measured values for the generic metric store. From the generic metric store, they can be pushed to SAP Cloud ALM or SAP Focused Run.



<a name="loioecc187f05d384394a57f3fc187a14dd1__prereq_vg3_xjr_x5b"/>

## Prerequisites

You need an administration role to be able to create application jobs.

You must set up a communication arrangement based on communication scenario `SAP_COM_0527`, so that metrics stored in the generic metric store are automatically pushed to Health Monitoring in SAP Cloud ALM and SAP Focused Run.



## Procedure

1.  In the SAP Fiori launchpad, open the *Schedule Metric Provider Collection* app.

2.  Choose *Create* to create a new application job.

    The job template for collecting metric provider values is already selected.

3.  To change job settings, follow the instructions of the in-built documentation of SAP Companion.

    > ### Note:  
    > Enter a recurrence that is a multiple of 5 minutes. **Don't** use a recurrence pattern that's shorter than 5 minutes.

4.  Schedule the job.




<a name="loioecc187f05d384394a57f3fc187a14dd1__result_grm_x4z_x5b"/>

## Results

The metric provider values are collected and saved to the generic metric store.

**Related Information**  


[Creating an Application Job](../50-administration-and-ops/creating-an-application-job-5c085de.md "Find out how to create your own application jobs in the Application Jobs app.")

