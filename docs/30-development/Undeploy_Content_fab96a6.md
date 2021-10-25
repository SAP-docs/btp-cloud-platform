<!-- loiofab96a603a004bd992822c83d4b01370 -->

# Undeploy Content

To undeploy content you need to delete the content from the repository and delete the `app-host` service plan instance.



## Procedure

1.  Open the Cloud Foundry command line interface \(CLI\).

2.  Undeploy the `*.mtar` file using the CLI command: `cf undeploy` and add the `--delete-services --delete-service-keys` option.

    Example: `cf undeploy html5.repo.deployer.myHTML5App --delete-services --delete-service-keys`

    -   Use the `–delete-services` option, to delete the `app-host` service plan instance and the application content from HTML5 application repository.

    -   For the `cf undeploy` command, you need the `mta id`. To get the `mta id`, do one of the following:

        -   Call `cf mtas`.

        -   Check the `mtad.yaml ID`.



    > ### Note:  
    > If you do not want to use the `–delete-services` option, you can delete the `app-host` service plan instance manually using the CLI command: `cf delete-service SERVICE-NAME`.


