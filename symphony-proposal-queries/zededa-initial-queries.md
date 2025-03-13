These feedback questions were received via email from Erik.

Initial questions on my list are:
-	The demo showed several "cert*" containers and the docs have an empty page about the cert management. What assumptions does Symphony make about the use of certificates and CAs?

  [Haishi] When deployed on Kuberentes, Symphony Helm chart deploys https://cert-manager.io/ for certificate management. It can act as either root CA or intermediate CA, which Symphony is configured to trust.
  
-	How does the Symphony fleet manager uniquely identify a particular device? (Using a name? A uuid? A client certificate? Something else?)

  [Haishi] A device that can host payloads is called Target in Symphony. It has an unique name in the system. When a Target is configured with a Symphony agent, it's requested to have a bootstrap certificate (baked during device manufacture, for instance) and Symphony bootstrapping (still in a separate branch) will use the bootstrap certificate to exchange for a working certificate with trusted CA.
  
-	Some issues such as ```https://github.com/eclipse-symphony/symphony/issues/47``` refer to Azure for JWT. Are there assumptions that Azure is used in the overall system?

  [Haishi] No. Symphony adopts claims-based architecture where a external trusted IdP (Identity provider) issues security token to Symphony. You can also have multiple token issuers, such as authentication as well as device attestation.
  
  -	Is this use of attestation for the fleet manager side, for the device, or both?

  [Haishi] If you mean device attestation it refers to attest the device hardware and software stack to ensure nothing is tempered. 
  
-	symphony contains logic for both what we call fleet manager and agent in Margo, but it is hard to tell the two apart in symphony. For instance, do the cert* containers run on both?

  [Haishi] What you see on on Kubernetes all belong to the Symphony control plane. The agent is a separate installation. We are currently working on a new agent version with enhanced security (and bootstrapping like mentioned above).
