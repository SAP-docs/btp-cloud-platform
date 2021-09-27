<!-- loio9a6fe7edf77a4f1299254c1c3c8bad48 -->

# Setting Up and Working with Your Landscape

Depending on your requirements, you need to adjust the setup of your software lifecycle management and the underlying landscape. The following sections give you examples for the most common setups

In general, the number of ABAP systems in your landscape is the result of the processes \(development \(DEV\), quality assurance \(QAS\), and production \(PRD\)\) that need to run in parallel and the number of branches of your biggest software component that is worked on or tested in parallel.

The number of ABAP systems = \(number of branches x DEV systems\) + \(number of branches x QAS systems\) + \(number of PRD systems\)

This is due to the fact that an ABAP system always checks out only one branch of a software component. Yet, several software components represented by one branch can run in one ABAP system in parallel.

-   **[Required Tools](Required_Tools_0b95882.md "")**  

-   **[Required Business Roles](Required_Business_Roles_01c96ed.md "")**  

-   **[Important Notes](Important_Notes_6d9a1b2.md "")**  

-   **[Use Case 1: One Codeline in a 3-ABAP-System Landscape](Use_Case_1_One_Codeline_in_a_3-ABAP-System_Landscape_2276142.md "")**  

-   **[Use Case 2: One Development and Correction Codeline in a 5-ABAP-System Landscape](Use_Case_2_One_Development_and_Correction_Codeline_in_a_5-ABAP-System_Landscape_4e53874.md "")**  

-   **[Use Case 3: One Codeline with On-Demand Development ABAP Systems](Use_Case_3_One_Codeline_with_On-Demand_Development_ABAP_Systems_ba7a9f3.md "")**  

-   **[Double Maintenance of Corrections into Development](Double_Maintenance_of_Corrections_into_Development_1241b14.md "")**  


