<!-- loiob5e1c8244e594f53936b6406905c7937 -->

# Tips and Tricks for Python Applications

-   Running on the China \(Shanghai\) region: it is mandatory for Cloud Foundry applications deployed in SAP, is for them to be deployed as self-contained – they need to carry all of their dependencies so that the staging process does not require any network calls.

    Running on the AWS, Azure, or GCP regions: the overall recommendation for Cloud Foundry applications deployed in SAP, is for them to be deployed as self-contained – they need to carry all of their dependencies so that the staging process does not require any network calls.

    See [https://docs.cloudfoundry.org/buildpacks/python/index.html\#vendoring](https://docs.cloudfoundry.org/buildpacks/python/index.html#vendoring)

-   The cfenv package provides access to Cloud Foundry application environment settings by parsing all the relevant environment variables. The settings are returned as a class instance. See [https://github.com/jmcarp/py-cfenv](https://github.com/jmcarp/py-cfenv).

-   While developing Python applications \(whether in the Cloud or not\) it’s a very good idea to use virtual environments. The most famous Python package providing such a functionality is `virtualenv`. See [https://virtualenv.pypa.io/en/stable/](https://virtualenv.pypa.io/en/stable/)

-   The PEP 8 style guide for Python applications - [https://www.python.org/dev/peps/pep-0008/](https://www.python.org/dev/peps/pep-0008/), will help you improve your applications.


