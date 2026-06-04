# Which tags to use in ASN.1 modules?

## Context

There is a decision to be made, so almost all tags have an assigned
private number by nexo in this case it is 0xCE which can be encoded:

    serviceId [PRIVATE 14] IMPLICIT ServiceIdentifier

 * Use context specific tag 0 with explicit encoding:
     - Easy, works with TCL asn module, interpretable by generic
       tools because value is wrapped in a universal tag
     - Doesn't use nexo defined value – which makes it less discoverable
       if you want to compare it with the specification
 * Use private tag with implicit encoding:
     - Slightly more verbose, I need to convert every hex number from
       the spec to correct syntax.
     - Doesn't work with TCL asn module, I need to write custom
       asnPrivate proc, also if tags has more then 6 bits I should
       construct it using asnTag proc.
     - Isn't readily interpretable by generic tools, because type of
       the value is not encoded
     - Very easy to cross-reference with the specification, because
       every tag will have exactly the same value.
     - Code can be reused to parse Nexo compliant configuration tables.
 * Use private tag with explicit encoding:
     - Can't encode exact hex value from the specification, because
       they defined all tags to be primitive

## Decision

The decision was to use 6-bit context specific explicit tags:

  - Original tags aren't used consistently across this module

## Consequences

Mapping or commentary is required for every data item to the specification.
