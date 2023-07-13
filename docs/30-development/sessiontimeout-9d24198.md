<!-- loio9d24198eed554793b7eb279657f17971 -->

# sessionTimeout

Define the amount of time \(in minutes\) for which a session can remain inactive before it closes automatically \(times out\); the default time out is 15 minutes.



> ### Note:  
> The `sessionTimeout` property is no longer available; to set the session time out value, use the environment variable *<SESSION\_TIMEOUT\>*[SESSION\_TIMEOUT](environment-variables-ba52705.md#loioba527058dc4d423a9e0a69ecc67f4593__section_blz_hgn_mv).

> ### Sample Code:  
> ```
> {
>   "sessionTimeout": 40
> }
> ```

With the configuration in the example above, a session timeout will be triggered after 40 minutes and involves central log out.

A session timeout triggers a central log out with the following consequences:

-   Deletes the user session
-   Requests the log out paths for all your back-end services \(if you provided these paths in the `destinations` and `service` properties\).

