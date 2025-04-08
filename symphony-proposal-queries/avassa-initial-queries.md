# Queries on the Symphony proposal

As mentioned in [previous write-up](https://github.com/margo/woa-interfaces-wg/blob/main/shared_experience/avassa-configuration-plane-experience.md) we suggest an option based on the separation of the call-home process from the protocol operations. And we suggest a bottom-up approach to validate the fundamental protocol interactions between the agent and the orchestrator in various real-world conditions to test and verify the applicability and fundamental functions.

Looking at the documented [Symphony Deployment Topologies](https://github.com/eclipse-symphony/symphony/blob/main/docs/symphony-book/agent/_overview.md) this suggestion may introduce a new `Agent` type (likely starting from the `Poll Agent`) and a new `Provider` type, resembling the `Staged Provider`.

Our suggestion is to extend the agent capabilities to support a process comprising the following steps:

- An initial REST call from the Agent to the orchestrator over HTTPS (optionally mTLS if there is a CA configured on the host) containing a unique host-identifier string and other meta-data that may be of interest to the orchestrator (e.g. agent software version, host IP addresses)
- The response depends on the configuration of the orchestrator, but will use HTTP response status codes to signal either success or failure depending on e.g. if the host-id is known to the orchestrator and associated behaviour
- A successful response will contain a certificate to use in next steps
- A QUIC or mTLS session is created initialized from the agent using the certificate provided by the orchestrator in the previous step
- The session is cofigured to use TCP SO_KEEPALIVE (in the mTLS case) or PING frames (in the QUIC case) to keep the session alive
- The sessions can then be actively terminated by either side, or timed out.

This process covers the call home-separated option and should give the Margo community a good understanding of the benefits and potential shortcomings of the approach.
