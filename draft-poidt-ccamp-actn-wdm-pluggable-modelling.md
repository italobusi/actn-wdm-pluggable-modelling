---
title: "Modelling of Optical Pluggables in Packet Over Optical Network"
abbrev: "Modelling Optical Pluggables"
category: info

docname: draft-poidt-ccamp-actn-wdm-pluggable-modelling-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: "Routing"
workgroup: "Common Control and Measurement Plane"
keyword:
 - next generation
 - unicorn
 - sparkling distributed ledger
venue:
  group: "Common Control and Measurement Plane"
  type: "Working Group"
  mail: "ccamp@ietf.org"
  arch: "https://mailarchive.ietf.org/arch/browse/ccamp/"
  github: "italobusi/actn-wdm-pluggable-modelling"
  latest: "https://italobusi.github.io/actn-wdm-pluggable-modelling/draft-poidt-ccamp-actn-wdm-pluggable-modelling.html"

author:
  -
    ins: R. Rokui
    fullname: Reza Rokui
    organization: Ciena
    email: rrokui@ciena.com

  -
    ins: A. Guo
    fullname: Aihua Guo
    organization: Futurewei Technologies
    email: aihuaguo.ietf@gmail.com

  -
    ins: P. Bedard
    fullname: Phil Bedard
    organization: Cisco
    email: phbedard@cisco.com

  -
    ins: B. Swamynathan
    fullname: B Swamynathan
    organization: Nokia
    email: swamynathan.b@nokia.com

  -
    ins: G. Grammel
    fullname: Gert Grammel
    organization: Juniper
    email: ggrammel@juniper.net

contributor:
  -
    ins: N. Davis
    name: Nigel Davis
    org: Ciena
    email: ndavis@ciena.com

  -
    ins: I. Busi
    fullname: Italo Busi
    org: Huawei Technologies
    email: italo.busi@huawei.com

  -
    ins: S. Belotti
    fullname: Sergio Belotti
    org: Nokia
    email: sergio.belotti@nokia.com

  -
    ins: D. Beller
    fullname: Dieter Beller
    org: Nokia
    email: dieter.beller@nokia.com

  -
    ins: R. Manzotti
    fullname: Roberto Manzotti
    org: Cisco
    email: rmanzott@cisco.com

normative:
  OIF-CMIS:
    title: "OIF Implementation Agreement (IA) Common Management Interface Specification (CMIS))"
    author:
      org: OIF Forum
    date: 27 April 2022
    seriesinfo: OIF CMIS IA
    target: https://www.oiforum.com/wp-content/uploads/OIF-CMIS-05.2.pdf

--- abstract

This draft outlines the modeling of optical pluggables within a host packet device within the context of a packet over optical network. The model encompasses all pertinent properties of the pluggable for various packet over optical use cases and is partitioned into three primary areas: the optical media interface, the electrical plug to host interconnect, and the physical equipment of the pluggable.

Included in the model are representations of configuration, states, and telemetry data, as well as profiles and coherent plug capabilities. Emphasizing the importance of considering both vendor-agnostic and vendor-specific attributes in modeling coherent pluggables.

Drawing from existing models in IETF, OpenConfig, ITU-T, OIF, and TAPI, this model offers enhanced uniform structuring and naming. Additionally, it provides insight into the mapping to plug interface structures defined in CMIS.

--- middle

# Terminology
The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT"
"SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in the
document are to be interpreted as described in {{!RFC2119}}.

The following terms abbreviations are used in this document:

* Optical Plug / Coherent Pluggables / Pluggable: A small form factor coherent optical module
* O-PNC: The control functions specializing in management/control of optical and photonic functions (virtual or physical). See {{?RFC8453}}
* P-PNC: The control functions specializing in management/control of packet functions (virtual or physical). See {{?RFC8453}}
* CMIS: Content Management Interoperability Services developed by OIF is an open standard that allows different content management systems to inter-operate over the Internet
* xPonder: Short for Transponder and/or Muxponder

# Introduction

Packet traffic has been transmitted across optical networks for many years, leveraging the advantages of optical transmission and switching combined with packet switching. Traditionally, optical systems and packet systems have been distinct, each with their own dedicated devices.

In numerous network setups, packet and optical networks have been engineered, operated, and managed separately, leading to siloed operations that can be suboptimal and inefficient. The evolution of both packet and optical systems has largely been independent. Optical systems, in particular, have seen advancements in capacity, especially with the adoption of coherent optical techniques.

Advancements in optical component design have led to increased density, enabling entire coherent optical terminal systems that previously required multiple circuit packs to now fit into a single small form factor "coherent pluggable." Integrating coherent pluggables into devices with packet functions can result in reduced network costs, power consumption, and footprint, while also enhancing data transfer rates, reducing latency, and expanding capacity, although in some cases, separate packet and optical solutions may still be preferred due to other engineering and deployment considerations.

These trends, coupled with the desire to utilize the best components available, have given rise to open optical pluggables. These pluggables allow a plug from one vendor to be installed in a device from another vendor with packet functions. Communication between coherent pluggables and the packet device host occurs through the CMIS standard developed by OIF {{OIF-CMIS}}.

While standardized transmission modes like ZR can handle basic applications, proprietary modes from vendors are often necessary to achieve optimal performance.

This draft outlines the modeling of an optical pluggable within a host packet device within the context of a packet over optical network. The model presented in this document consolidates various properties of optical pluggables into three key areas:

* Optical media interface: This defines the characteristics of the optical solution such as spectrum, polarization, and dispersion, which do not directly affect the behavior of the host packet device.
* Electrical plug-to-host interconnect: This defines the characteristics of the bus interconnect between the host and the plug, such as lane count and FEC, which both the optical pluggable and the packet host must understand and act upon.
* Physical and functional aspects of the pluggable: This defines attributes of the optical pluggable itself, such as plug type, version, thermal characteristics, and power consumption, which indirectly affect the packet host.

The coherent pluggable model provides representations for capabilities, profiles, configurations, and states and telemetry data. Capabilities are defined in profiles related to operational modes, with some capabilities potentially being proprietary Configurations include attributes for optical settings, monitoring capabilities, and test capabilities, while state and telemetry data include dynamic properties such as performance monitoring collections and alarm notifications.

Both vendor-agnostic and vendor-specific attributes are important considerations in the modeling of coherent pluggables.

The document is divided into the following sections:

* Section 3: Packet over optical converged network context
* Section 4: Coherent Pluggables Building Blocks
* Section 5: Coherent Pluggables Data Modeling
* Section 6: Coherent Pluggables Yang Model


# Packet over optical converged network context

~~~~
                  |---------------|
                  |   P-PNC(s),   |
                  |   O-PNC(s),   |
                  |   MDSC        |
                  |---------------|
                          ^
                          |  (A)
      +-------------------|-------------------+
      |                   |                   |  Packet Device
      |                   V                   |  Vendor X
      |        |---------------------|        |  (i.e, Host)
      |        |                     |        |
      |        v                     v        |
      |  |-----------|          |----------|  |
      |  | Packet    |          | Coherent |  |
      |  | Function  |..........| Plug     |  |
      |  | Data      |          | Data     |  |
      |  |-----------|          |----------|  |
      |        .                      .       |
      |        .                      . (B)   |
      |        .                      .       |
      |  |--------------|   (C)   |------------------|  (D)
      |  |Packet Device |<------->| Coherent Plug #1 |=======
      |  |Function      |<---|    | Vendor X         |
      |  |--------------|    |    |------------------|
      |                      |                |
      |                      |    |------------------|
      |                      |--->| Coherent Plug #2 |=======
      |                           | Vendor Y         |
      |                           |------------------|
      |                                       |
      +---------------------------------------+

  Legend
    (A) Packet device management interfaces (e.g., YANG, NETCONF, gNMI, etc.)
    (B) CMIS interface between Optical pluggable and Host
    (C) Host side of the optical pluggable (towards the Host)
    (D) Media side of the optical pluggable (towards Optical/Photonic network)

~~~~
{: #figure-details-packet-optical-device title="Packet device with optical pluggables"}


# Optical Pluggable Building Blocks

~~~~

     Optical Pluggable
     |--------------------------------------------------------------------------|
     |                                                                          |
     |                Host side                         Media side              |
     | |---------------------------------|  |---------------------------------| |
     | |                                 |  |                                 | |
     | | |-----------|    |-----------|  |  | |-----------|    |-----------|  | |
  -------| Electrical|    | Host      |  |  | | Media     |    | Optical   | -----> (Tx)
  -------| Channel   |----| Logical   |-------| Logical   |....| Channel   | <----- (Rx)
  -------|           |    | Channels  |  |  | | Channels  |    | (OTSI)    |  | |
     | | |-----------|    |-----------|  |  | |-----------|    |-----------|  | |
     | |                                 |  |                                 | |
     | |---------------------------------|  |---------------------------------| |
     |                                                                          |
     | |----------------------------------------------------------------------| |
     | |                            Equipment/inventory                       | |
     | |----------------------------------------------------------------------| |
     |                                                                          |
     |--------------------------------------------------------------------------|

~~~~
{: #figure-optical-pluggable-building-blocks title="Optical Pluggable Building Blocks"}


# Optical Pluggables Data Modeling

# Optical Pluggables Yang Model

# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Security Considerations

TODO Security


# IANA Considerations

This document has no IANA actions.


--- back

{:numbered="false"}

# Acknowledgments

TODO acknowledge.
