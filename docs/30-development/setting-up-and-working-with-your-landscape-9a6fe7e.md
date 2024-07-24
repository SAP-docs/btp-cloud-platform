<!-- loio9a6fe7edf77a4f1299254c1c3c8bad48 -->

# Setting Up and Working with Your Landscape

Depending on your requirements, you need to adjust the setup of your software lifecycle management and the underlying landscape. The following sections give you examples for the most common setups

In general, the number of ABAP systems in your landscape is the result of the processes \(development \(DEV\), quality assurance \(QAS\), and production \(PRD\)\) that need to run in parallel and the number of branches of your biggest software component that is worked on or tested in parallel.

The number of ABAP systems = \(number of branches x DEV systems\) + \(number of branches x QAS systems\) + \(number of PRD systems\)

An ABAP system allows only one active branch of a software component per system at any given point in time. Yet, several software components represented by one branch can run in one ABAP system in parallel. That means, unless your administrator checks out a different branch in the Manage Software Component app, all released transports will be committed to this active branch.

