<!-- loio18564c54f529496ba420d4c83545a2ce -->

# How to Clone Software Components



<a name="loio18564c54f529496ba420d4c83545a2ce__section_q4w_4fj_1mb"/>

## Context

If a software component is not locally in your system yet, you will first need to clone it once to import it into your system.

> ### Note:  
> Cloning a software component is only necessary once per system instance.



<a name="loio18564c54f529496ba420d4c83545a2ce__section_kkv_vfj_1mb"/>

## Procedure

1.  Go to the details page of the software component you would like to clone.

2.  Click *Clone*.

3.  A pop-up opens. You can now select which branch you would like to import. If the software component does not have branches yet, the master or main branch \(dependent on when the repository was created\) is automatically selected. Select *By Tag* if you want to clone a specific git tag, which has been assigned to a commit. Select *By Commit* if you want to clone a software component with a specific commit ID. Confirm by clicking *Clone*.

    > ### Note:  
    > There is no input validation for the entered values for the options *By Tag* and *By Commit*. If the entered values are not valid the cloning process will start, but will be shown as failed in the end of the cloning process. In this case, the clone *Latest* option is automatically called as a fallback. With this, the repository is still useable, but not in the orginally requested version.

    > ### Note:  
    > If the initial clone of a software component runs into errors, the partly imported objects will be removed again from the system instance and the system will be kept clean. Please note that this rollback mechanism is only available for production systems.

4.  The software component with the selected branch is now imported into your current system instance. The *Clone* button turns into a *Pull* button. From now on, you can use it to pull \(remotely available\) changes of your software component to your system.


> ### Note:  
> It is recommended to clone multiple software components one by one. Please clone software components with objects that are reused by other components first.

**Related Information**  


[How to Pull Software Components](how-to-pull-software-components-90b9b9d.md "")

