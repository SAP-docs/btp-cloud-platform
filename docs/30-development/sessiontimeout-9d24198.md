<!-- loio9d24198eed554793b7eb279657f17971 -->

# sessionTimeout

Define the amount of time \(in minutes\) for which a session can remain inactive before it closes automatically \(times out\); the default time out is 15 minutes.



> ### Note:  
> The `sessionTimeout` property is no longer available; to set the session time out value, use the environment variable *<SESSION\_TIMEOUT\>*.

> ### Sample Code:  
> ```
> {
>   "sessionTimeout": 40
> }
> ```

With the configuration in the example above, a session timeout will be triggered after 40 minutes and involves central log out.

