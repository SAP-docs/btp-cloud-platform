<!-- loiobb8c8cfad88d46b79ad4670bb5c8f5fa -->

# Enabling and Modifying Notifications

Control which notifications you receive and how they are delivered by configuring your notification settings for the services associated with your account.



## Context

Notification settings let you decide which events you are informed about and through which channels. The settings are organized in three levels, so you can control notifications broadly or fine-tune them for a single event:

-   **Categories** – Each category represents a service that is associated with your global account or subaccount. You see only the services that are available to you, so the list differs from account to account. You can enable or disable notifications for an entire service from this level.

-   **Events** – Within a service, individual events represent the specific situations that can trigger a notification. You can enable or disable each event separately.

-   **Delivery channels** – For each event, you choose how you are notified, for example through in-app notifications or e-mail.


At every level, a toggle switch turns notifications on or off, and a navigation arrow opens the next level of detail. The steps below describe the general process; Cloud Foundry is used as an example service.

> ### Note:  
> For now, only global account administrators can receive and modify notifications.



<a name="loiobb8c8cfad88d46b79ad4670bb5c8f5fa__steps_notif_settings"/>

## Procedure

1.  Open the *Settings* dialog in the user menu and choose *Notifications*.

    You will see the services that are associated with your account. Each row shows a toggle switch and a navigation arrow.

2.  To enable or disable notifications for an entire service, use the toggle switch of the corresponding category.

3.  To fine-tune the events of a service, select its navigation arrow, for example *Cloud Foundry*.

    The detail view for the selected service opens. A toggle at the top enables or disables all notifications for the service, and the individual events are listed below.

4.  Use the toggle switch of an event to enable or disable notifications for that event.

5.  To choose how you are notified about an event, select its navigation arrow.

    The event detail view opens and describes when the notification is sent.

6.  Use the event toggle to enable or disable the event, and under *Choose how you get notified*, enable or disable each delivery channel.

    Typical delivery channels are:

    -   *In-App notifications* – Delivered inside the SAP BTP cockpit.

    -   *E-mail* – Sent to your registered e-mail address.


7.  Choose *Save* to apply your changes, or *Cancel* to discard them.




<a name="loiobb8c8cfad88d46b79ad4670bb5c8f5fa__result_notif_settings"/>

## Results

Your notification preferences are saved. You are notified only about the services and events you enabled, through the delivery channels you selected. You can return to *Settings* at any time to modify these preferences.

