<!-- loioccbc023469094329ab81b7d8cd7c7b33 -->

# Trusted Network Zones



<a name="loioccbc023469094329ab81b7d8cd7c7b33__section_wm5_hzs_2bc"/>

## Redirection Attacks

The primary use of trusted network zones is to prevent redirection attacks.

In a redirection attack, the attacker tricks the victim into sending a specially crafted request to the server. The server then redirects the request to a malicious website based on the information in the request.

This is used for phishing. The victim might not be aware of the redirect because the initial request was sent to a trustworthy system and the malicious site might be built to resemble the trustworthy system.

The configuration of trusted network zones prevents such attacks by limiting which URLs the server can redirect to.



<a name="loioccbc023469094329ab81b7d8cd7c7b33__section_vky_yys_2bc"/>

## Upload Limitation

The trusted network zones configuration also restricts uploads defined by URL.

Where file upload is possible by specifying a URL rather than a file on the filesystem, the entered URL is checked against the trusted network zones list. Note that host, port, and scheme of the URL must be maintained in*Trusted Network Zones* for the upload to be permitted.

**Related Information**  


[Maintain Protection Allowlists](maintain-protection-allowlists-81aed02.md "With this app you can maintain a list of trusted hosts or URL patterns.")

