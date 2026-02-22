# ASN.1 modules used for NEXO internal RPC

Declarative definitions of protocol messages between FAST and SCAP. Other
subsystems are yet to be defined.

Uses layered approach, wrapper is different per transport for example:
`Scapi.asn1` defines all messages between FAST and SCAP, but `ScapiNngClient.asn1`
defines a wrapper message with additional metadata for [NNG](https://nng.nanomsg.org/)
delivery mechanism.
