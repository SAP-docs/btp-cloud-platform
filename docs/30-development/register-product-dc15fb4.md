<!-- loiodc15fb4ebab5453fa4641b98190b1f85 -->

# Register Product

The *Register Product* app provides information about which global accounts are already registered for an available product and enables you, as a provider, to:

-   create new products

-   register your global accounts for your existing products.




<a name="loiodc15fb4ebab5453fa4641b98190b1f85__section_umt_xqz_1tb"/>

## Prerequisites

You need to have the “LandscapePortalAdmin” user role assigned to your user account to access this app.



<a name="loiodc15fb4ebab5453fa4641b98190b1f85__section_vzk_yqz_1tb"/>

## Creating a product in the Register Product app

1.  Log into the *Landscape Portal*.

2.  In the *Product* section, click on the *Register Product* tile to open the app.

3.  A list of all your products, including their product ID, namespace and registration status, is displayed. The registration status indicates whether a product has already been registered to the global account you are currently logged in to.

    Possible registration statuses:

    -   Current global account already registered. \(green indicator\)
    -   Current global account can be registered. \(orange indicator\)
    -   Pending… \(orange indicator\)
    -   Registration not triggered \(orange indicator\)
    -   Error \(red indicator\)

4.  Click the *Create* button in the top right corner.

5.  Enter the name of the product you want to create and confirm with *Create*. Your request for creation has been sent and the registration status of the product changes to “Pending…”. The namespace is automatically determined from the product name you entered, and the product ID is generated as part of the creation process.

6.  Refresh the page to view the progress. Once the creation is complete, the registration status of the product changes to “Current global account can be registered”. Your product has now been created and you can register your global account for it.


> ### Note:  
> If the registration status changes to “Error” or "Registration not triggered", or if it remains in status “Pending…” over a longer period of time, please restart the creation process using the same product name. The process will start again; namespace and product ID will stay the same. Should the error remain, please open a ticket.



<a name="loiodc15fb4ebab5453fa4641b98190b1f85__section_ezp_pwz_1tb"/>

## Registering a global account for a product using the Register Product app

1.  In the *Register Product* app, select the product that you want to register your global account for.

2.  Under *Global Accounts*, you can see a list of all your global accounts. The global account that you are currently logged in to will be displayed at the top of the list. Different colored bars indicate which global accounts are already registered for the product \(green\), are not yet registered for the product \(red\), or can now be registered for the product \(orange\). It is only possible to register the global account that you are currently logged in to.

3.  To register the global account you are currently logged in to, click the *Register* button in the top right corner. Once the registration is complete, the registration status changes to “Current global account already registered” \(green\) and the list of accounts will display who the account was registered by \(email address\) as well as the date of registration.


