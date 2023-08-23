<!-- loio04053ddc096f4becb1be45355da2f70f -->

# Schedule a \(Recurring\) Stop/Start



You want put a system into hibernation at a specific time, choosing at what time it will be stopped, and when it will be started again. This planned hibernation can be scheduled to happen once, or it can be set up to recur regularly, e.g. on a daily or weekly basis. Here’s how to schedule a planned or recurring stop \(= recurrence\).

1.  Log into the *Landscape Portal* from your provider subaccount.
2.  In the *Systems* section, click on the*Manage System Hibernation* tile to open the app.
3.  On the left side, under *Systems*, you can see a list of all your systems, as well as their current status \(*Live* or *Stopped*\). *Live* systems are currently active, *Stopped* systems are in hibernation. Select one or more systems for which you want to schedule a planned stop, then click*Schedule Stop/Start* at the top.
4.  Fill in the information in the pop-up window, then click *Save*.
5.  Your scheduled stop will be added under *Scheduled Stops/Starts*. Click the arrow on the left to expand the panel and view more information on it.
6.  \(Optional\) You can delete a planned stop by clicking the respective icon to the right of it. This can be done as soon as the planned stop is active \(a few minutes after its creation\).




<a name="loio04053ddc096f4becb1be45355da2f70f__section_pf4_l3g_myb"/>

## Example

Let’s say you want a system to only be live from 6:00 to 20:00 on Mondays through Fridays. It should be stopped outside of working hours as well as on the weekends.

Here’s how you can set up this scenario in the app:

Create two recurrences. Recurrence 1 stops the system on weekdays over night \(from 20:00 to 6:00\). Recurrence 2 stops the system on the weekends \(from Friday night 20:00 until Monday morning 06:00\).

*Settings for Reccurence 1*:

![](images/MSH_Screenshot1_72b6ca9.png)

Starting today, the system will stop over night from Mondays to Fridays until the end of the year. Now let’s set the recurrence for the weekend stops.

*Settings for Reccurence 2*:

![](images/MSH_Screenshot2_fb3f29e.png)

With this recurrence, the system will stop every Friday night until Monday morning.

The two recurrences \(R1: daily overnight stop in purple; R2: weekend stop in green\) will make sure your system is only live from Mondays through Fridays from 06:00 to 20:00.

![](images/MSH_Screenshot3_c2e5d1c.png)

> ### Note:  
> Note that the end time you select \(06:00 in our example\) specifies when the system \(re\)start will be triggered. It might take a few minutes for the system to be available again.

