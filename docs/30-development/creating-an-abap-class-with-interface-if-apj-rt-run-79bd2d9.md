<!-- loio79bd2d9879a74f4c8512d374a3bc5416 -->

# Creating an ABAP Class with Interface IF\_APJ\_RT\_RUN

Learn how to create an ABAP class that implements the interface `IF_APJ_RT_RUN` to run the business logic of your application in an application job.

The interface `IF_APJ_RT_RUN` contains the following method:

-   `EXECUTE`: This method is called by the application job framework when the scheduled application job is run. This means that the ABAP coding that should run within the application job is implemented here.


Before you schedule an application job, you get a selection screen where you can enter values for the application job parameters. These parameters are used to control the processing of the business logic. If you put the business logic into an ABAP class with interface `IF_APJ_RT_RUN`, you can use the public attributes of the ABAP class as selection parameters. The parameters should fulfil the requirements described in [Defining Class Attributes Used as Selection Parameters](defining-class-attributes-used-as-selection-parameters-05d8bb4.md). Apart from the job catalog entry, the data type of the class attribute determines how the parameter is displayed and behaves on the selection screen.

Before the `EXECUTE` method is called by the application job framework during the job run, the class attributes are automatically filled with the values which were entered on the selection screen. The attributes can be used in the class coding without further preparations.

When you create a new application job template based on this class \(see [Creating the Job Template](creating-the-job-template-1f04ad2.md)\), its parameter values are prefilled with default values. To determine these default values, the class is instantiated and the values of the class attributes which have the same name as the template parameters are read. You have the following possibilities to set these default values:

-   In the definition section of the class as default values of the class attributes

-   In the `CONSTRUCTOR` of the class by setting values to the class attributes

-   In addition, you can implement the interface `IF_APJ_DT_DEFAULTS` in the class and define default values in method `FILL_ATTRIBUTE_DEFAULTS` by setting values to the class attributes


> ### Note:  
> If the parameter is a date field, you can use a command like `@STARTDAYPLUSDAY@:03` in the value field of the template to define a dynamic date. This command can't be set as default value in method `FILL_ATTRIBUTE_DEFAULTS`, but you can enter it into the template after the template has been created.

