<!-- loio855d691feac24999a1ffebbc42fa2d96 -->

# Sizing Occasions and Methods

Sizing makes sense at different occasions, such as before a go-live or after an increased usage of applications. You can use different sizing methods, ranging from educated guess to expert sizing.



<a name="loio855d691feac24999a1ffebbc42fa2d96__section_q4k_22t_tqb"/>

## Occasions for Sizing

Sizing can be performed at different occasions:

-   Before the initial go-live of an application \(greenfield sizing\)

-   After the initial go-live and after an increased usage of applications, or after functionality has been added or changed \(delta sizing or resizing\)


Reliable sizing can only be achieved if the hardware as well as the platform layer used are scalable, but most importantly, the application software must be scalable. Load tests are used to check the scalability of all involved components.

In a typical productive environment, 80% of the workload is caused by 20% of the business processes. Consequently, detailed sizing focuses on these relevant business processes. Sizing for the remaining business processes is typically done using an educated guess.

As a rule of thumb, sizing should target an average resource utilization of no more than 70%. Keep extra space available for peak times as well as for anticipated future growth because of increasing business activity.

> ### Recommendation:  
> We recommend that you consider a resizing of the environment if the resource utilization frequently exceeds 80%. Going beyond 90% resource utilization in normal operation mode usually causes resource contention in individual components and can considerably impact user experience with longer response times.



<a name="loio855d691feac24999a1ffebbc42fa2d96__section_g12_gts_tqb"/>

## Sizing Methods

There are different sizing methods that allow you to perform sizing with different efforts required, but also resulting in different levels of accuracy. Sophisticated sizing methods are applied in environments where hardware resources are the main cost driver. Simple and less elaborate sizing methods can be applied in smaller environments, or to get a starting point for less critical scenarios.


<table>
<tr>
<th valign="top">

Sizing Method



</th>
<th valign="top">

Advantages



</th>
<th valign="top">

Disadvantages



</th>
</tr>
<tr>
<td valign="top">

Educated guess

\(Rule of thumb\)



</td>
<td valign="top">

-   Easy to apply

-   Delivers a quick rough estimate




</td>
<td valign="top">

-   Depends on many assumptions

-   Highly depends on the experience of the person who makes the guess




</td>
</tr>
<tr>
<td valign="top">

T-shirt sizing

\(Predefined application model and categories of workload sizes\)



</td>
<td valign="top">

-   Easy to apply

-   Easy to understand




</td>
<td valign="top">

-   Depends on many assumptions

-   Requires an underlying sizing model that fits well to the actual application




</td>
</tr>
<tr>
<td valign="top">

Expert sizing

\(Manual measurement and creation of sizing formula\)



</td>
<td valign="top">

-   Delivers the most realistic results

-   Allows for more variables

-   Transparent sizing model




</td>
<td valign="top">

-   Suggests accuracy that sizing can't deliver

-   Requires the highest efforts




</td>
</tr>
</table>

