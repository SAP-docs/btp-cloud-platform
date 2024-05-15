<!-- loioe6105bbbd3084ef194fc5f7db8ab931a -->

# Secure Communication

SAP BTP, ABAP environment offers secure communication features for securing both machine-to-machine communication \(server communication security\) as well as communication between systems and end-user UIs \(frontend communication security\).

Communication security is maintained on multiple levels.



<a name="loioe6105bbbd3084ef194fc5f7db8ab931a__section_clj_rss_2bc"/>

## Establishing the Communication Channel to a Host

The connection is initiated by a client calling a host to set up a cryptographically secured communication channel. This is known as a TLS \(or SSL\) handshake. During the handshake, the host proves its identity by presenting a server certificate. The client validates the server certificate to gain assurance that the connected host coincides with the host the client intended to call. This prevents man-in-the-middle attacks.

In case of a web UI, the validation of server certificates is done in the browser using a list of trusted root certificates provided by the browser or the operating system.

The certificate of your system is signed by DigiCert Global Root CA.

In other cases, the client may also be a backend server talking to another backend server. Here, the server initiating the connection takes the role of the client and the other one is the host.



<a name="loioe6105bbbd3084ef194fc5f7db8ab931a__section_kp1_wss_2bc"/>

## Authentication of the Client/User

After the communication channel is established, the application on the host side may verify the caller's identity if the application requires authentication. The most common method for this is still basic authentication \(user/password\). A more secure option is certificate-based authentication \(mTLS\). Here, the client presents an X.509 certificate to the application to prove its identity.



<a name="loioe6105bbbd3084ef194fc5f7db8ab931a__section_lfy_yss_2bc"/>

## Additional Protection of Web Clients

For web clients, there are additional mechanisms protecting the user from attacks like cross site scripting \(XSS\) or redirect attacks. These mechanisms are defined by the server, but enforced in the user's client.

