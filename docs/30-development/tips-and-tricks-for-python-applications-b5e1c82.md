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




<a name="loiob5e1c8244e594f53936b6406905c7937__specify_python_bp_version"/>

## Specify a buildpack version in `manifest.yml`

At some point, you might need \(or decide\) to deploy your application with a particular buildpack version from the community [python-buildpack](https://github.com/cloudfoundry/python-buildpack) repository. For example, if this buildpack contains a Python version that is no longer supported by SAP BTP, Cloud Foundry.

Let's say, you want to pin version [1.8.4](https://github.com/cloudfoundry/python-buildpack/releases/tag/v1.8.4). To do that, proceed as follows:

1.  Open the **manifest.yml** file of your Python application.

2.  For the `buildpack` attribute, add the URL to version 1.8.4, like this:

    ```
    
    ---
    applications:
    - name: myapp
      random-route: true
      buildpack: https://github.com/cloudfoundry/python-buildpack.git#v1.8.4
      memory: 128M
    ```

3.  Redeploy your application by executing:

    ```
    cf push myapp
    ```


**Alternative way:**

If you don't want to make changes in your **manifest.yml** file, you can include the buildpack version in the `cf push` command.

-   To deploy just a single application with this particular buildpack version, execute:

    ```
    cf push myapp -b https://github.com/cloudfoundry/python-buildpack.git#v1.8.4
    ```

-   To pin this buildpack version for all applications running in your SAP BTP, Cloud Foundry subaccount, execute:

    ```
    cf push -b https://github.com/cloudfoundry/python-buildpack.git#v1.8.4
    ```




<a name="loiob5e1c8244e594f53936b6406905c7937__section_qqq_fv5_41b"/>

## Specify application memory in `manifest.yml`

When deploying an application in the Cloud Foundry environment without specifying the application memory requirements, the Cloud Foundry controller assigns the default \(1G of RAM currently\) for your application. Many Python applications require less memory and assigning the default is a waste of resources.

To save memory from your quota, specify the memory size in the deployment descriptor of your Cloud Foundry application – `manifest.yml`. For example:

```

---
applications:
- name: myapp
  memory: 128M
  buildpack: python_buildpack
...
```



<a name="loiob5e1c8244e594f53936b6406905c7937__section_opc_w5b_3sb"/>

## Additional Tips

-   The `cfenv` package provides access to the Cloud Foundry application environment settings by parsing all the relevant environment variables. The settings are returned as a class instance. See: [https://github.com/jmcarp/py-cfenv](https://github.com/jmcarp/py-cfenv)

-   When developing Python applications, it’s a good practice to use virtual environments. The most popular Python package providing such a functionality is `virtualenv`. See: [https://virtualenv.pypa.io/en/stable/](https://virtualenv.pypa.io/en/stable/)

-   The [PEP 8 Style Guide for Python](https://www.python.org/dev/peps/pep-0008/) will help you improve your applications.


