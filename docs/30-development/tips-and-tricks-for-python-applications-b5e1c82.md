<!-- loiob5e1c8244e594f53936b6406905c7937 -->

# Tips and Tricks for Python Applications



<a name="loiob5e1c8244e594f53936b6406905c7937__section_emv_pf1_m1b"/>

## Get to Know the Python Buildpack for the Cloud Foundry Environment

Check the following Cloud Foundry documentation: [Python Buildpack](https://docs.cloudfoundry.org/buildpacks/python/index.html)



<a name="loiob5e1c8244e594f53936b6406905c7937__section_x5h_ssb_3sb"/>

## Vendor Application Dependencies

Sometimes, productive Cloud Foundry applications might need to be deployed as self-contained. That means, they need to carry all of their dependencies so that the staging process does not require any network calls. For more information, see: [Vendor App Dependencies](https://docs.cloudfoundry.org/buildpacks/python/index.html#vendoring) 

Depending on the region where the application is deployed:

-   Running on the China \(Shanghai\) region: it is **mandatory** for the application to be deployed as self-contained

-   Running on the AWS, Azure, or GCP regions: it is only **recommended** but not mandatory for the application to be deployed as self-contained.




<a name="loiob5e1c8244e594f53936b6406905c7937__section_opc_w5b_3sb"/>

## Additional Tips

-   The `cfenv` package provides access to the Cloud Foundry application environment settings by parsing all the relevant environment variables. The settings are returned as a class instance. See: [https://github.com/jmcarp/py-cfenv](https://github.com/jmcarp/py-cfenv)

-   When developing Python applications, it’s a good practice to use virtual environments. The most popular Python package providing such a functionality is `virtualenv`. See: [https://virtualenv.pypa.io/en/stable/](https://virtualenv.pypa.io/en/stable/)

-   The [PEP 8 Style Guide for Python](https://www.python.org/dev/peps/pep-0008/) will help you improve your applications.


