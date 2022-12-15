<!-- loio241382cd9f5f453c9591430355b7c74d -->

# Providing Read or Write Access to a Business Service Using Privileged Mode

With enablement of privileged mode for a business object, it's possible to consume the business object without the need for additional business authorizations.



<a name="loio241382cd9f5f453c9591430355b7c74d__section_awy_sjd_lvb"/>

## Use Case for Business Users

A typical use case for privileged mode is the execution of an application job. In the bonus calculation example used in this documentation, such an application job could be required to schedule calculations of the target bonus amounts of valid bonus calculations that haven't been calculated yet. For this purpose, you can enable privileged access for the *Bonus Calculation* business object.

As a result, the business user for which the bonus calculation job is scheduled doesn't require all the authorizations that a typical business user of the business service would need. So, there's no need to define an IAM app, a business catalog, and a business role for the authorization to calculate the bonus.



<a name="loio241382cd9f5f453c9591430355b7c74d__section_w2r_2ck_lvb"/>

## Use Case for Communication Users

During the execution of instance A of a business object X, write access might be needed to instance B of business object B. This is where privileged mode comes into play. Let's turn to a concrete example: You've created a custom business object for employees and a bonus business object. The employee business object has a performance indicator, such as *Exceeds Expectations*, *Consistently Exceeds Expectations*, and so on.

Now, when the bonus of the employee is calculated using the action *Calculate Bonus*, then the performance indicator of the employee is also updated at the same time, for example, using the action *Update Performance Indicator*. At this point, it makes sense to check whether the user \(human or machine\) has the authority to calculate the bonus. If so, then the system could also automatically update the performance indicator even if the user doesn't have a dedicated authority for it. What's more, the user might not even be allowed to display the information.

