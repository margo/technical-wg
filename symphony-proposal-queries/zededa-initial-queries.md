These feedback questions were received via email from Erik.

Notes:
-	FWIW this is not the topics that matter to me. I want to make sure that
Symphony does not make assumptions about the overall system and
environment which might make hard to fit Margo into Symphony.

Examples questions on my list are:
-	The demo showed several "cert*" containers and the docs have an empty page about the cert management. What assumptions does Symphony make about the use of certificates and CAs?
-	How does the Symphony fleet manager uniquely identify a particular device? (Using a name? A uuid? A client certificate? Something else?)
-	Some issues such as 
  - https://github.com/eclipse-symphony/symphony/issues/47
  - refer to Azure for JWT. Are there assumptions that Azure is used in the overall system?
-	Is this use of attestation for the fleet manager side, for the device, or both?
-	symphony contains logic for both what we call fleet manager and agent in Margo, but it is hard to tell the two apart in symphony. For instance, do the cert* containers run on both?
