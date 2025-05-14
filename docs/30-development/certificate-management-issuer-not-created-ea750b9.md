<!-- loioea750b9de87f4a849663980d280c331d -->

# Certificate Management: Issuer Not Created



<a name="loioea750b9de87f4a849663980d280c331d__section_rmr_chv_s2c"/>

## Symptom

When you try to create an Issuer custom resource \(CR\) using `cert.gardener.cloud/v1alpha1`, the resource is not created. There are no logs in the `cert-management` controller.



<a name="loioea750b9de87f4a849663980d280c331d__section_aw4_dhv_s2c"/>

## Cause

The `cert-management` controller does not watch the namespace in which you created the Issuesr CR. By default, `cert-management` watches the `default` namespace for all Issuer CRs.



<a name="loioea750b9de87f4a849663980d280c331d__section_hfq_dhv_s2c"/>

## Solution

To make sure that you created the Issuer CR in the `default` namespace, run: `kubectl get issuers -A`. If you want to create the Issuer CR in a different namespace, adjust `cert-management` settings during the installation.

