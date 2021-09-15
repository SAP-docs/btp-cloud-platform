<!-- loio825942f8db9f4523b4d0cd6a807e89d2 -->

# Example: Authorizations for a Bonus Calculation Service

Let’s assume that you have a bonus calculation service, which, in the example used here, is represented by an active service binding. You want to model authorizations for this service.



<a name="loio825942f8db9f4523b4d0cd6a807e89d2__section_tks_crn_5mb"/>

## The Bonus Calculation Service

The bonus calculation service is part of a sales bonus program where the sales revenues that sales reps were able to generate are used as the basis for their bonus plan. In the ABAP RESTful Application Programming Model \(RAP\), the bonus plan is modeled as a business object *Bonus Calculation* of type managed.

With the bonus calculation service, users, for example, managers in sales, can create, update, display, and delete bonus calculations. As part of a bonus calculation, users enter an employee name, a bonus variant and validity period can be set, and the bonus be calculated. In the example used in this guide, the available bonus variants are based on *Rate* or *Amount*, that is, the bonus recipient either gets a bonus based on a rate or a fixed amount.

The service can be consumed either by business users via a user interface \(UI\) or by technical communication users as an API. For both consumption types access has to be provided at least for nondevelopment systems because this access isn't automatically available in such systems.



<a name="loio825942f8db9f4523b4d0cd6a807e89d2__section_bgc_zrq_qpb"/>

## Consumption in a UI for Business Users

If the business service is consumed by a UI, the available UI enables business users easily, depending on their authorizations, to set data or to execute the actions the service is offering. For example, a UI for managers lets them perform activities on bonus calculations. The UI wraps the underlying service calls for the business users into intuitive UI elements. Changes that the business user isn't authorized for can either be made unavailable on the UI or their corresponding service call is done and an appropriate error returned from the service. The UI can act as a kind of authorization filter. This kind of service consumption always requires business user action.



<a name="loio825942f8db9f4523b4d0cd6a807e89d2__section_hrb_kxw_3pb"/>

## Consumption as API with a Communication User

If the business service is consumed as API, no UI wraps the allowed changes to the business service. Instead, the service caller can try to change all data and execute all actions directly and always gets errors if there are missing authorizations to do it.

In the example used here, the bonus calculation is an inbound business service that business users use to create new bonus calculations. There's no dedicated bonus calculation in the HR system, but instead, the HR business service calls the bonus calculation business service in the ABAP environment to set data and execute actions.

Where you work with an API business service \(inbound or outbound\) from or into the ABAP environment, you need to provide authorizations to technical users, so-called communication users, instead of business users. This service consumption can be performed automatically without any user action.

