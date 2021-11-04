<!-- loioda6f25b1d3804445b478f40abee6cd8f -->

# Expert Sizing

As the ABAP environment is a platform-as-a-service offering, sizing in this context refers to applications that aren't standard SAP coding but are custom development of either an SAP partner or an SAP customer. This fact usually prevents the usage of the educated guess or t-shirt sizing method, as there's typically no reference available. This documentation therefore focuses on the expert sizing method.

Expert sizing involves the following steps:

1.  Identify the sizing-relevant \(main\) business scenarios and their variable dimensions.

2.  Determine the throughput requirements during defined time periods and their day-time distribution. As part of the requirement determination, separate scenarios that are time-critical from those scenarios that can be postponed to low load times.

3.  Define test cases for each relevant scenario with a reasonable number of input parameters and assumptions. These test cases must be self-contained and idempotent, which means repeatable with a stable load profile.

4.  Execute each test case in single-user mode to measure its individual workload profile.

5.  Create sizing models based on the results of the previous steps.

6.  Create a structured load analysis to verify and refine the sizing model regarding scalability aspects \(mass user testing\).

    > ### Note:  
    > This step isn't in the scope of this document.

7.  To simplify the consumption of the sizing formulas resulting from expert sizing, you can also define and precalculate representative t-shirt sizes for the system.


> ### Recommendation:  
> Changes to the underlying technology stack \(for example, configuration changes in the ABAP environment\), as well as changes in the application behavior \(for example, enhanced functionality in a new software release\) can invalidate your sizing results. We recommend that you validate from time to time whether the sizing is still adequate for your system workload.

