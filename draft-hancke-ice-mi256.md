---
title: "An ICE Option for MESSAGE-INTEGRITY-SHA256"
abbrev: "ICE-MI256"
category: info

docname: draft-hancke-ice-mi256-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
workgroup: WG Working Group
keyword:
area: AREA
workgroup: Transport and Services Working Group
keyword:
 - stun
 - ice
venue:
  group: WG
  type: Working Group
  mail: tsvwg@ietf.org
  arch: https://datatracker.ietf.org/wg/tsvwg/
  github: fippo/mimi
  latest: https://fippo.github.io/mimi/draft-tsvwg-hancke-ice-mi256.html

author:
 -
  fullname: Philipp Hancke
  organization:
  email: philipp.hancke@googlemail.com
 -
  fullname: Roman Shpount
  organisation:
  email: rshpount@gmail.com

normative:

informative:

--- abstract

This document defines a new ICE option "mi256" that enables the use of
MESSAGE-INTEGRITY-SHA256 for STUN short-term authentication in ICE.
This is a usage specific negotiation method which lets ICE agents
use the SHA-256 variant of the message-integrity attribute in favor of
SHA-1.

--- middle

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Introduction

Interactive Connectivity Establishment (ICE) {{!RFC8445}} uses STUN
{{!RFC8489}} with short-term credentials for connectivity checks.
However, ICE assumes a single MESSAGE-INTEGRITY algorithm (SHA-1) and
does not provide a mechanism for hash agility.

STUN defines a mechanism for hash agility and requires usages
to define their own negotiation method as described in {{RFC8489, Section 16.3}}.

This document updates ICE by defining an ICE option "mi256" that signals
support for MESSAGE-INTEGRITY-SHA256 and specifies how it is used for
connectivity checks.

# ICE Option

This document defines a new ICE option "mi256" following the procedures
in {{!RFC8839}} which indiciates support for the comprehension-required
MESSAGE-INTEGRITY-SHA256 STUN attribute.

When the "mi256" ice-option is supported by both agents,
any STUN message using short-term authentication

* MUST include the MESSAGE-INTEGRITY-SHA256 attribute and
* MUST NOT include the MESSAGE-INTEGRITY attribute.

Truncation is not permitted.

# Security Considerations

This document improves the security of ICE by enabling the use of
SHA-256 instead of SHA-1 for message integrity.

# IANA Considerations

This document requests that IANA make the following registrations:

## ICE Option Registration

IANA is requested to add the following value to the
"Interactive Connectivity Establishment (ICE) Options" registry:

ICE Option name: `mi256`

Description: The ICE option indicates that the ICE agent supports the
  MESSAGE-INTEGRITY-SHA256 STUN attribute.

--- back
