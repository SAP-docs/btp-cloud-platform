<!-- loio41ec2d3a18474743888bbffd05ee81f3 -->

# ABAP Service Instance URL



<a name="loio41ec2d3a18474743888bbffd05ee81f3__section_ky5_npq_hdc"/>

## Context

Previously, when creating a new ABAP Cloud project in ABAP development tools for Eclipse, a service key was necessary to connect to the SAP BTP, ABAP environment. In the window *Connection to an ABAP Service Instance*, there was a distinction between the connection to SAP S/4HANA Cloud Public Edition and SAP BTP, ABAP environment. From now on, only one option to paste in your ABAP service instance URL is available.



<a name="loio41ec2d3a18474743888bbffd05ee81f3__section_rhn_fqq_hdc"/>

## Connection to an ABAP Service Instance

1.  Select *Create a new ABAP cloud project*. This opens up a window called *Connection to an ABAP Service Instance*.

2.  Following, you can now choose two options to connect to your ABAP service instance listed below.

    1.  Insert the URL from the SAP Fiori launchpad of your system.

    2.  If you still have a service key available, you can extract the URL from it by clicking the link shown in the description text of the window you're in: **Do you have a service key? Extract the URL from the service key.**

        1.  In this case, a new window opens up where you can paste in your service key.

        2.  Next, choose *Copy to Clipboard*.

        3.  Now, you are in the *Connect to an ABAP Service Instance* window again and can paste in the service instance URL.

        4.  Choose *Copy logon URL to clipboard*.

        5.  Finally, you can paste the URL into your browser and log on to the system.

            The message shows *You have been successfully logged on* and ABAP development tools for Eclipse will pick up your project data.




