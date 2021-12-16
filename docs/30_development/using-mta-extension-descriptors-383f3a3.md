<!-- loio383f3a3300ba4efb863f226acd5632e6 -->

# Using MTA Extension Descriptors

The parameters defined in the MTA can be adapted for the corresponding landscape using MTA extension descriptor files. These files extend the original MTA descriptor file \(mta.yaml\) and allow it to change certain values during deployment. The descriptor files end with “mtaext” and are used during the deployment \(e.g. using CF CLI with MultiApps plugin, see [https://github.com/cloudfoundry-incubator/multiapps-cli-plugin](https://github.com/cloudfoundry-incubator/multiapps-cli-plugin)\).

For more information on MTA extension descriptors, see:[Defining MTA Extension Descriptors](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/50df803465324d36851c79fd07e8972c.html). The extension descriptor files are usually in the folder “extensions” next to the mta.yaml.

