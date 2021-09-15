<!-- loio18c1edcc125740f98856dcf1392112d8 -->

# Asynchronous Upload Using the HTML5 Application Deployer

You can specify that the upload of content is performed asynchronously by adding the environment variable `ASYNC_UPLOAD` to the `manifest.yaml` or `mta.yaml` files.

The asynchronous upload is especially useful, if you want to trigger the upload of service instances with a large content \(more than 10 MB\). A synchronous upload of service instances with a large content can result in health check errors or a connection timeout during the upload. You can avoid this by using the asynchronous upload.

During an asynchronous upload, the html5 applications content is handled synchronously to the HTML5 Application Repository, while the internal file validation and processing is performed asynchronously. To verify that the upload has completed successfully, you have to check the HTML5 Application Deployer logs.

