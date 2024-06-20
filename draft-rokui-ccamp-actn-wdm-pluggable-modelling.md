---
title: "Modelling of Optical Pluggables in Packet Over Optical Network"
abbrev: "Modelling Optical Pluggables"
category: info

docname: draft-rokui-ccamp-actn-wdm-pluggable-modelling-latest
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
  latest: "https://italobusi.github.io/actn-wdm-pluggable-modelling/draft-rokui-ccamp-actn-wdm-pluggable-modelling.html"

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

  -
    ins: P. Manna
    fullname: Prasenjit Manna
    org: Cisco
    email: prmanna@cisco.com

  -
    ins: G. Galimberti
    fullname: Gabriele Galimberti
    org: Individual
    email: ggalimbe56@gmail.com
 
  -
    ins: H. Venkatraman
    fullname: Harish Venkatraman
    org: Infinera
    email: hvenkatraman@infinera.com

  -
    ins: G. Mishra
    fullname: Gyan Mishra
    org: Verizon
    email: gyan.s.mishra@verizon.com

normative:
  OIF-CMIS:
    title: "OIF Implementation Agreement (IA) Common Management Interface Specification (CMIS))"
    author:
      org: OIF Forum
    date: 27 April 2022
    seriesinfo: OIF CMIS IA
    target: https://www.oiforum.com/wp-content/uploads/OIF-CMIS-05.2.pdf

  OIF-400ZR:
    title: "Implementation Agreement 400ZR"
    author:
      org: OIF Forum
    date: 3 November 2022
    seriesinfo:
    target: https://www.oiforum.com/wp-content/uploads/OIF-400ZR-02.0.pdf

  G.698.2:
    title: "Amplified multichannel dense wavelength division multiplexing applications with single channel optical interfaces"
    author:
      org: ITU-T Recommendation G.698.2
    date: November 2018
    seriesinfo: 
    target: https://www.itu.int/rec/dologin_pub.asp?lang=e&id=T-REC-G.698.2-201811-I!!PDF-E&type=items

  SFF8024:
    title: "SFF Module Management Reference Code Tables"
    author:
      org: SNIA SFF Technology Affiliate (TA) Technical Work Group (TWG), Small Form Factor Technology Affiliate
    date: November 27, 2023
    seriesinfo: 
    target: https://members.snia.org/document/dl/26423
    
  Impairment:
    title: "A YANG Data Model for Optical Impairment-aware Topology"
    author:
      org: 
    date: 2024-03-04
    seriesinfo: 
    target: https://datatracker.ietf.org/doc/draft-ietf-ccamp-optical-impairment-topology-yang/


--- abstract

This draft outlines the modeling of optical pluggables within a host packet device in the context of a packet over optical network. The model encompasses all pertinent properties of the pluggable for various packet over optical use cases and is partitioned into three primary areas: the optical media interface, the electrical plug to host interconnect, and the physical equipment of the pluggable.

Included in the model are representations of configuration, states, and telemetry data, as well as of profiles and coherent plug capabilities. Emphasizing the importance of considering both vendor-agnostic and vendor-specific attributes in modeling coherent pluggables.

Drawing from existing models in IETF, OpenConfig, ITU-T, OIF, and TAPI, this model offers enhanced uniform structuring and naming. Additionally, it provides insight into the mapping to plug interface structures defined in CMIS.

This draft introduces the concpet of "Coherent Pluggable Manifest", where a represents the capabilities of a type&version of pluggable, maintained in a public repository of all pluggables. This document also covers gap analysis of current IETF drafts and other SDOs on coherent pluggables attributes and provides the complete lifecycle of a coherent pluggable from operators' approval through viability assessment to deployment.

--- middle

# Terminology

{::boilerplate bcp14-tagged}

The following terms abbreviations are used in this document:

- Optical Pluggable / Coherent Pluggable / Pluggable: A small form factor coherent optical module. This document uses these terms interchangeably

- O-PNC: The control functions specializing in management/control of optical and photonic functions (virtual or physical). See {{?RFC8453}}

- P-PNC: The control functions specializing in management/control of packet functions (virtual or physical). See {{?RFC8453}}

- CMIS: Content Management Interoperability Services developed by OIF is an open standard that allows different content management systems to inter-operate over the Internet

- xPonder: Short for Transponder and/or Muxponder

# Introduction

Packet traffic has been transmitted across optical networks for many years, leveraging the advantages of optical transmission and switching combined with packet switching. Traditionally, optical systems and packet systems have been distinct, each with their own dedicated devices.

In numerous network setups, packet and optical networks have been engineered, operated, and managed separately, leading to siloed operations that can be suboptimal and inefficient. The evolution of both packet and optical systems has largely been independent. Optical systems, in particular, have seen advancements in capacity, especially with the adoption of coherent optical techniques.

Advancements in optical component design have led to increased density, enabling entire coherent optical terminal systems that previously required multiple circuit packs to now fit into a single small form factor "coherent pluggable." Integrating coherent pluggables into devices with packet functions can result in reduced network costs, power consumption, and footprint, while also enhancing data transfer rates, reducing latency, and expanding capacity, although in some cases, separate packet and optical solutions may still be preferred due to other engineering and deployment considerations.

These trends, coupled with the desire to utilize the best components available, have given rise to open optical pluggables. These pluggables allow a plug from one vendor to be installed in a device from another vendor with packet functions. Communication between coherent pluggables and the packet device host occurs through the CMIS standard developed by OIF {{OIF-CMIS}}.

While standardized transmission modes like ZR can handle basic applications, proprietary modes from vendors are often necessary to achieve optimal performance.

This draft outlines the modeling of an optical pluggable within a host packet device in context of a packet over optical network. The model presented in this document consolidates various properties of optical pluggables into three key functional block:

- Photonic/Optical attributes: These attributes defines the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc., which do not directly affect the behavior of the host packet device.

- Host/Electrical attributes: These attributes defines the characteristics of interconnect between the host and the optical pluggable, such as lane count, FEC etc., which both the optical pluggable and the packet host must understand and act upon.

- Physical and functional aspects of the pluggable (i.e., equipment): This defines attributes of the optical pluggable itself, such as plug type, version, thermal characteristics, power consumption etc., which indirectly affect the packet host.

For each of these functional blocks, coherent pluggable model provides attributes in following areas:

- Capabilities: These attributes are read-only and defines the functional capabilities of the optical pluggables. They are defined in a profile called "operational-mode" and contains attributes such as modulation, bit-rate, baud-rate, chromatic-dispersion, polarization, FEC etc. Generally an optical pluggable might support multiple operational-modes.

- Configurations: Since an optical pluggable can support multiple operational-modes, these read-write attributes configure the pluggables to be functional in one of those operational- modes. Example of configuration attributes are output power, central frequency and operational-mode.

- States and performance monitoring telemetry data: These read-only attributes will be generated by optical pluggables and represents various states of the optical pluggable such as channel input power, channel output power, central frequency, laser temperature, current OSNR etc. In most cases these attributers are changing with time and pluggable reports instantaneous, min , max, average values.

- Alarm notifications

Both vendor-agnostic and vendor-specific attributes are important considerations in the modeling of coherent pluggables.

The document is divided into the following sections:

- {{optical-pluggable-in-device-packet-function}}: Optical Pluggable in a Device with Packet Functions

- {{building-blocks}}: Coherent Pluggables Building Blocks

- {{data-model}}: Coherent Pluggables Data Modeling

- {{yang-model}}: Coherent Pluggables Yang Model

- {{pluggable-gap-analysis}}: Coherent pluggable Gap Analysis 

- {{plug-manifest}}: Coherent Pluggables Manifest

- {{plug-lcm}}: Optical Pluggables Lifecycle Management

- {{architecture-implications}}: Functional Architecture Implications

- {{plug-manifest-usage}}: Usage of Coherent Pluggables Manifest


{: #optical-pluggable-in-device-packet-function}

# Optical Pluggable in a Device with Packet Functions

{{figure-details-packet-optical-device}} shows a packet device from vendor X, which is connected to optical device, equipped with optical pluggables from vendor X and Y. This figure exposes the following internal and external interfaces:

1. This interface provides the control of packet device packet and optical functions. It provides these functions which can be decoupled such that there is no overlap between the optical and packet control functions.

2. The optical controller has read/write access to the optical network

3. The CMIS (content management interoperability services) communication interface between hosts (e.g., packet devices) and optical pluggable

4. The data flow between the coherent pluggable and the packet data function through this interface. This is electrical interface between coherent pluggable and the host. {{building-blocks}} will discuss this in more details.

5. Optical fiber connecting the optical devices to optical pluggables. This carries the flow of photonic signal from the optical device to the coherent pluggables. {{building-blocks}} will discuss this in more details.

This draft presents the modeling of the coherent pluggable such as #1 and #2 in {{figure-details-packet-optical-device}} within a host packet device. The model presented in {{data-model}} consolidates properties of coherent pluggable on interfaces (4) and (5) where interface (5) provides the photonic/optical attributes and interface provides the host/electrical attributes.

~~~~

              |--------------------|
              |  packet, optical,  |
              |  and higher layer  |
              |  controllers       |
              |--------------------|
                       ^ ^
                       | |
                   (1) | |-----------------------------------|
   +-------------------|-------------------+                 |
   |                   v                   |                 |
   |        |---------------------|        |                 |
   |        |                     |        |                 | 
   |        v                     v        |                 |
   |  |-----------|          |----------|  |                 |
   |  | Packet    |          | Coherent |  |                 |
   |  | Function  |..........| Plug     |  |                 |
   |  | Data      |          | Data     |  |                 |
   |  |-----------|          |----------|  |                 |
   |        .                      .       |                 |
   |        .                      . (3)   |            (2)  |
   |        .                      .       |                 v
   |  |--------------|   (4)   |------------------|  (5) |---------|
   |  |Packet Device |<------->| Coherent Plug #1 |======| Optical |
   |  |Function      |<---|    | Vendor X         |      | Device  |
   |  |--------------|    |    |------------------|      |---------|
   |                      |                |  
   |                      |    |------------------|      |---------|
   |                      |--->| Coherent Plug #2 |======| Optical |
   |                           | Vendor Y         |      | Device  |
   |                           |------------------|      |---------|
   |                                       | 
   +---------------------------------------+
    Host Vendor X 
     (e.g., Router)     

~~~~
{: #figure-details-packet-optical-device title="Packet device with optical pluggables"}



{: #building-blocks}

# Coherent Pluggable Functional Building Blocks 

The functional building blocks of the coherent pluggables of {{figure-details-packet-optical-device}} are shown in {{figure-optical-pluggable-building-blocks}} and has three major functions:

- Media side: This functional block represents all Photonic/Optical attributes of the coherent pluggables (interface (5) in {{figure-details-packet-optical-device}}). These attributes define the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc., which do not directly affect the behavior of the host packet device.

- Host side: This functional block represents all Host/Electrical attributes of the coherent pluggables (interface (4) in {{figure-details-packet-optical-device}}). These attributes defines the characteristics of interconnect between the host and the optical pluggable, such as lane count, FEC etc., which both the optical pluggable and the packet host should understand and act upon.

- Equipment attributes: These attributes represent all physical and functional aspects of the coherent pluggable such as plug type, software version, thermal characteristics, power consumption etc.

~~~~

Optical Pluggable
 |--------------------------------------------------------------|
 |                                                              |
 |           Host side                      Media side          |
 | |---------------------------|  |---------------------------| |
 | |                           |  |                           | |
 | | |---------|  |---------|  |  | |---------|  |---------|  | |(Tx)
-----| Elec.   |  | Host    |  |  | | Media   |  | Optical | -----> 
-----| Channels|--| Logical |-------| Logical |--| Channel | <----- 
-----|         |  | Channels|  |  | | Channels|  | (OTSI)  |  | |(Rx)
 | | |---------|  |---------|  |  | |---------|  |---------|  | |
 | |                           |  |                           | |
 | |---------------------------|  |---------------------------| |
 |                                                              |
 | |----------------------------------------------------------| |
 | |                        Equipment                         | |
 | |----------------------------------------------------------| |
 |                                                              |
 |--------------------------------------------------------------|

~~~~
{: #figure-optical-pluggable-building-blocks title="Optical Pluggable Building Blocks"}

The following sections are describing the details of coherent pluggable functional blocks in more details.

## Optical Channel/OTSI

The media side of the coherent pluggable is further divided into two functional blocks; Optical Channel/OTSI and Media Logical Channels. The characterises of the Optical channel/OTSI are:

* This is the optical network facing interfaces

* Represents the digital wrapper that transports services over a wavelength

* Represents the wavelength and the coherent aspects of the signal modulated onto it baud-rate, bit-rate, modulation scheme, frequency, tx-power, etc.

* Optical signal FEC termination/source, FEC characteristic information – configuration, if possible, Pre-FEC BER, Post-FEC BER, fail/degrade thresholds, raw corrected/uncorrected counts

* Provides configuration of the signal and monitoring capabilities

* Provides monitoring capabilities in the Tx (toward fiber/medium) and Rx (from fiber/medium) directions, Total optical power, optical channel power, Coherent statistics

## Media Logical Channels

The characterises of the Media Logical Channels are:

* Logical representation of the hierarchical view of the digital framing layers used for transport of services over the wavelength

* Provides access to information for configuration and monitoring characteristics. For example, for 400ZR/OpenZR+, it represents the 400ZR frame structure in which Ethernet services are mapped and for an OTN encapsulated signal, it represents the OTU, ODU, OPU frame structures, perhaps with a multi-layer multiplex structure, in which Ethernet and other types of services are mapped

## Host Logical Channels

The host side of the coherent pluggable is further divided into two functional blocks; Host Logical Channels and Electrical channels. The characteristics of the Host Logical Channels are:

* Logical representation of the hierarchical view of the digital framing layers for services carried on the electrical lanes of the device

* Provides information for configuration and monitoring characteristics of each service

* Represents each service carried over the media logical channel and optical interface/wavelength, e.g., 25GE, 50GE, 100GE, 200GE, 400GE, OTU4, OTUCn etc.

## Electrical Channels

The characteristics of the Electrical Channels are:

* The host interface lanes of the device forming the physical interface to the host platform data path device(s)

* Lanes grouped to support the type/format and bandwidth of the signal used for a service

* Provides information for configuration and monitoring characteristics of the signal for a service in the electrical domain, e.g., Interface-format, FEC, alarming thresholds, etc.

* Provides monitoring capabilities in the Tx (toward fiber) and Rx (from the fiber)
 
## Equipment 

The "Equipment functional block" in {{figure-optical-pluggable-building-blocks}} represents the coherent pluggable itself and has the following characteristics:

* Provides manufacturer identification information for the device

* Advertises capabilities of the device including capabilities for the host/client interface and the media/line interface

* Provides monitoring capabilities of physical characteristics and health of the device, e.g., temperature, voltage, coherent transmitter/receiver characteristics

* Provides for configuration where applicable – e.g., of device environmental thresholds

* Supports device level capabilities such as firmware installation, restarts, etc.


{: #data-model}
# Optical Pluggables Data Modeling

The attributes of all functional building block of a coherent pluggable in {{figure-optical-pluggable-building-blocks}} will be exposed to external packet and optical controllers via host interface (1) shown in {{figure-details-packet-optical-device}}. To this end, we need to model the coherent pluggable building blocks described in {{building-blocks}}.

The data modelling of each functional blocks provides attributes in five areas:

1. Coherent pluggable capabilities (aka supported-modes)
2. Coherent pluggable configurations
3. Coherent pluggable states and performance monitoring data
4. Coherent pluggable threshold definition
5. Coherent pluggable alarm notifications

{: #plug-capabilities-attributes}

## Coherent pluggable capabilities (i.e., supported-modes)

The supported-modes are read-only capability attributes that define the functional capabilities of coherent pluggables. In other words, the coherent pluggable functional capabilities are described by a set of supported-modes, which includes read-only attributes such as modulation, bit rate, baud rate, chromatic dispersion, polarization, and FEC. For some attributes it includes value range (min. max) as well. A coherent pluggable may support multiple supported-modes, where each mode can be defined by one of the following methods:

* STANDARD: Defined by a Standards Developing Organization (SDO) such as ITU-T
* NON-STANDARD: Defined by a forum such as Optical Internetworking Forum (OIF), OpenConfig or by an individual vendor or by an operator

The STANDARD defined supported-modes are well-known capabilities established by standard bodies such as ITU-T {{G.698.2}}. These modes are recognized and supported by coherent pluggables, routers, and SDN controllers. While the current specification references ITU-T {{G.698.2}}, this document will support the work of other Standards Development Organizations (SDOs) as their specifications become available.

In contrast, the NON-STANDARD defined supported-modes are capabilities specified by forums such as OIF {{OIF-400ZR}}, OpenConfig, or by individual vendors. These supported-modes might not be supported by all coherent-pluggables, routers or SDN controllers. In specific, the supported-modes defined by an individual vendor might be not be recognized and supported by any routers and SDN controllers.

As illustrated in {{figure-plug-supported-mode}}," this document employs a consistent data structure for defining STANDARD and NON-STANDARD supported-modes where each supported-mode contains:

* supported-mode-id: ID of the supported mode.
* organization-id: The authority that defines the supported-mode, such as ITU-T, OIF, OpenConfig, or a vendor. This provides a name space for an authority who defines the supported-mode.
* supported-mode-type: The type of supported-mode which is STANDARD or NON-STANDARD
* multiple tags: Optional tags that can be used for various purposes, mainly for future extensibility. For example, these tags can map the supported-mode to CMIS Media-ID. Other potential uses of this tag are reserved for future developments.
* operational-mode: This is the main part of this document which contains a list of capability attributes supported by the coherent pluggable.

Some details of supported modes can be found in IETF draft {{Impairment}}.

{{plug-manifest}} discusses the concept of the "coherent pluggable manifest", which is a repository for all supported-modes" either STANDARD or NON-STANDARD. It also outlines the benefit of such repository and various use-cases.

~~~~ 

 |-----------------------------------------------------------------|
 |                                                                 |
 |  supported-mode*    // list of supported-modes                  |
 |                                                                 |
 |      supported-mode-id                                          |
 |      organization-id (e.g., ITU-T, OIF, OpenConfig or Vendor)   |
 |      supported-mode-type (e.g. STANDARD, NON-STANDARD)          |
 |      tag* (has various usage. Also support future use)          |
 |      operational-mode                                           |
 |              supported-attribute-1                              |
 |              supported-attribute-2                              |
 |              ....                                               |
 |              supported-attribute-n                              |
 |                                                                 |
 |-----------------------------------------------------------------|

~~~~
{: #figure-plug-supported-mode title="Data structure for Coherent pluggable supported-modes"}

## Coherent pluggable configurations attributes

The coherent pluggables support a set of read-write attributes which are configurable. Example of such configuration attributes are output power, central frequency and operational-mode. Note that since a coherent pluggable may support multiple operational-modes (standard or custom), the read-write operational-mode attribute programs the coherent pluggable to be functional in one of those operational-modes.

## Coherent pluggable states and performance monitoring data 

These read-only attributes will be generated by optical pluggables and represents various states and performance monitoring data of the optical pluggable such as channel input power, channel output power, central frequency, laser temperature, current OSNR etc. In most cases these attributers are temporal and coherent pluggable reports values such as instantaneous, min, max and average. A "supported threshold profile (STP) can be assigned to each performance monitoring data (see {{plug-threshold-definition}}).

{: #plug-threshold-definition}
## Coherent pluggable threshold definition

 To provide a general solution for threshold definition of coherent pluggable performance monitoring data,  the concept of "Supported Threshold Profile (STP)" is introduced. As shown in  {{figure-plug-threshold-definition}}, each STP defines upper and lower threshold levels, threshold style and variety of PM metrics such as minimum, maximum and average values.

~~~~

                SUPPORTED-THRESHOLD-PROFILE (STP)

 |----------------------------------------------------------------|
 |   STP-Type-1:                                                  |
 |     Threshold value: upper, lower                              |
 |     Threshold style: Rolling window of [min-time, max-time]    |
 |     Collection: min, max, ave, instant, ....                   |
 |                                                                |
 |   STP-Type-2:                                                  |
 |     Threshold value: upper, lower                              |
 |     Threshold style: Rolling window of [min-time, max-time]    |
 |     Collection: instant                                        |
 |                                                                |
 |   STP-Type-3:                                                  |
 |     Collection: min, max, instant                              |
 |                                                                |
 |   ...                                                          |
 |   STP-Type-n:                                                  |
 |     ...                                                        |
 |----------------------------------------------------------------|

  (Note: these are just a few examples)   

~~~~
{: #figure-plug-threshold-definition title="Coherent pluggable threshold definition"}


To define the upper and lower thresholds for performance monitoring telemetry data, operator should set upper and lower limits that delineate acceptable performance ranges. This ensures that any deviations can be quickly identified and addressed. A rolling window between min-time and max-time should be employed to dynamically adjust these thresholds based on recent data trends, providing a more accurate reflection of current network conditions. By continuously updating the thresholds, network performance can be maintained within optimal parameters, reducing the risk of undetected issues.

A variety of performance monitoring metrics, including minimum, maximum, average, and instantaneous values, can be collected. These metrics offer a comprehensive view of performance fluctuations, allowing for precise monitoring and quicker response times to anomalies. Minimum and maximum values help identify the extremes of performance, while average values give a sense of typical performance levels. Instantaneous values, on the other hand, provide real-time insights, which are crucial for immediate issue detection and resolution. This multi-faceted approach ensures that network performance is consistently monitored and maintained at high standards.

For each performance monitoring state data, one STP should be assigned.

## Coherent plug alarm notifications

[Editor's note: To be added in a later release.]

The coherent pluggables might generate various alarm notifications due to the various reasons.

{: #yang-model}
# Optical Pluggables Yang Model

[Editor's note: To be added in a later release.]

{: #pluggable-gap-analysis}
# Coherent pluggable data modelling gap analysis 

[Editor's note: To be added in a later release.]

This activity was initiated to examine existing IETF models related to pluggables for "completeness":

* To assess existing properties/structures
* To look for missing properties/structures

It is recognized that there is uncompleted work on properties in other bodies so this activity will be ongoing. The aim is to achieve best positioning of the IETF work with respect to the other related activities in the industry.

To carry out this ongoing examination, Properties/structures from relevant external bodies are collected and compared with properties/structures present in IETF models related to pluggables. Where properties/structures differ the differences are examined and justifications considered. Where there is justification for changes to the IETF models these are proposed.

{: #plug-manifest}
# Coherent Pluggable Manifest

Referring to {{plug-capabilities-attributes}}, the coherent pluggable capability attributes (i.e., supported-modes) are crucial aspects of coherent pluggables and should be easily accessible by anyone for various activities, including:

- Network Engineers: Need to know the capabilities and characteristics of any coherent pluggable whether the coherent pluggable is already deployed or will potentially be installed and deployed in their network
- SDN Controllers: The optical, packet or higher-layer SDN controllers need to have detailed knowledge of the coherent pluggables for various reasons such as the assessment of the viability of any photonic services from plug-to-plug, configuration and fulfilment of the coherent pluggables and others.
- Packet Device (e.g., Router): Optionally the host packet device can also access the "coherent pluggable manifest" to provide details of coherent pluggables already installed in packet devices.

The term "Coherent Pluggable Manifest" is used for the collection of information, appropriately structured and interrelated, that describes the capabilities of a pluggable. In other terminology spaces the Manifest may be considered to be a Specification, a Profile, etc.

It should be noted that any equipment could have a Manifest describing its capabilities and the Manifest may be broken down into units that can be referenced and reused, i.e., the definition can be modular. 

To facilitate the stages, each vendor would be expected to provide a Manifest for each pluggable type & version.

Considering the above, it appears reasonable that all pluggable capabilities whether they be proprietary or standard should be fully described in the Manifest. This may be achieved by a reference to a standard that is itself fully defined in machine interpretable form. This approach would allow for a far more flexible and future-proofed control solution.

To facilitate easy access to coherent pluggable attributes, the details of coherent pluggable operational-modes are collected in a public repository, such as GitHub and SharePoint, called "Coherent Pluggable Manifest". This machine-readable repository can be read and interpreted easily by any SDN controller, operator, or other devices in the network.

{{figure-optical-pluggable-manifest}} illustrates the overall structure of the "Coherent Pluggable Manifest". It contains several operational-mode records where each record includes all the capability attributes for a pair of [organization-id, operational-mode]. As discussed in {{plug-capabilities-attributes}}, "organization-id" refers to any authority that defines them such as ITU-T {{G.698.2}} or {{OIF-400ZR}}) or a vendor.

Each record in the coherent pluggable manifest is machine readable/interpretable and is uniquely identified by a tuple [organization-id, operational-mode].

Using "Coherent Pluggable Manifest", the format and usage of STANDARD or NON-STANDARD operational-modes is the same. Note that all attributes pertaining to operational-modes are defined by this IETF document. 

~~~~
 
  |-------------------------------------------------------|
  |  For tuple [organization-id, operational-mode]        |-|
  |                                                       | |-| 
  |  organization-id:  X1 (e.g., ITU-T, OIF or Vendor)    | | |
  |  operational-mode: Y1                                 | | |
  |  version: y.y                                         | | |
  |  formally approved: Y/N                               | | |
  |  type (e.g. STANDARD, NON-STANDARD)                   | | |  
  |  list of attributes:                                  | | |
  |     attribute 1: ...                                  | | |
  |     attribute 2: ...                                  | | |
  |     ...                                               | | |
  |     attribute n: ...                                  | | |
  |                                                       | | |
  |-------------------------------------------------------| | |
    |-------------------------------------------------------| |
      |-------------------------------------------------------|

 Coherent Pluggable Manifest
   - Contains one or more operational-mode records 
   - Each record for tuple [organization-id, operational-mode]
   - It is machine-readable/interpretable

~~~~
{: #figure-optical-pluggable-manifest title="Coherent Pluggable Manifest"}

In essence, the introduction of the concept of "Coherent pluggable manifest" substantially streamlines the definition and application of these modes, encompassing both STANDARD and NON-STANDARD operational-mode.

Below a few examples are provided to demonstrate the concept of the "Coherent Pluggable Manifest". {{figure-optical-pluggable-manifest-example_1}} illustrates the content of a manifest record for NON-STANDARD operational-mode 0x3E which is defined by OIF forum. In practice this operational mode is supported by almost all coherent pluggables. The detail information for this operational-mode can be found at {{SFF8024}} Table 4-7.

~~~~

organization-id:  OIF 
operational-mode: 0x3E
type: NON-STANDARD
list of attributes
      modulation: DP-16QAM
      bit-rate: 478.75 Gbps
      baud-rate: 59.84375 Gbd
      more attributes ...
~~~~
{: #figure-optical-pluggable-manifest-example_1 title="Coherent Pluggable Manifest Defined by OIF"}

{{figure-optical-pluggable-manifest-example_2}} is anther manifest record where the Vendor-X has defined a NON-STANDARD operational-mode 0x22. In this case, Vendor-X defines all the attributes related to operational-mode 0x22 which might not be supported by other pluggable vendors.

~~~~

organization: Vendor-X
operational-mode: 0x22
type: NON-STANDARD
list of attributes
      modulation: 16-QAM
      bit-rate: 400 Gbps
      baud-rate: 56 GBd
      more attributes ...
~~~~
{: #figure-optical-pluggable-manifest-example_2 title="Coherent Pluggable Manifest Example-2"}

"{{figure-optical-pluggable-manifest-example_3}}" presents an example where the Vendor-Y has a coherent pluggable module with NON-STANDARD operational-mode 0x22 as well. In this scenario, the organization associated with the pluggable module is Vendor-Y, which defined the same operational-mode 0x22 as "Vendor-X"

It is important to note that while the operational-modes in both {{figure-optical-pluggable-manifest-example_2}} and {{figure-optical-pluggable-manifest-example_3}} share the same values, they are defined by different vendors. Consequently, these operational-modes are not related and may differ significantly in their attributes. In other words, although the semantics of these modes are identical, their actual content might vary significantly. This is one of the reasons that any record in Coherent Pluggable Manifest is uniquely identified by tuple [organization-id, operational-mode].

~~~~

organization: Vendor-Y
operational-mode: 0x22
type: NON-STANDARD
list of attributes
      modulation: QPSK
      bit-rate: 800 Gbps
      baud-rate: 96 GBd
        more attributes ...
~~~~
{: #figure-optical-pluggable-manifest-example_3 title="Coherent Pluggable Manifest Example-3"}

{: #plug-lcm}
# Optical Pluggables Lifecycle Management

This section discusses the complete lifecycle of an optical pluggable as shown in {{figure-overview-lifecycle-pluggable}}. It includes discussion on the pre-purchase evaluation of pluggables through installation to the operation of a pluggable in a live network. 

Most of this lifecycle discussion applies to a majority of equipment types. Where the pluggable is special, this is highlighted.

The figure below provides a high level flow. In a real environment, all stages will be running in parallel for various plug versions etc. and there may be feedback from any stage to a previous stage. For example, the research, evaluation and planning exercises are ongoing activities that continue as the network grows and changes and as new pluggable type & versions are introduced by vendors and insight from deployment may feed back to the evaluation stage. 

Throughout the lifecycle specific use cases and scenarios will be considered and applied. These will be developed during the early stages and applied in service design.

Note: The stages and the terminology used are not intended to reflect any specific operational practice. They are intended to be neutral with respect to any existing operator's processes, aligning with the essence of the processes.

~~~~
  Market research                   \
       |                            |
       v                            |
  Testing of pluggable samples      | See
       |                            | Section 9.1
       v                            |
  Trials & PoCs                     |
       |                            |
       v                            |
  Approve pluggable type            /
       |                   ---------
       v                            \ 
  Service demand Analysis           | 
       |                            |
       v                            | See
  Network planning                  | Section 9.2
       |                            |
       v                            |
  Service type realization analysis |
       |                            |
       v                            |
  Purchase pluggables               /
       |                   ---------
       v                            \  
  Optical infrastructure creation   |
       |                            |
       v                            |
  Service demand received           | See
       |                            | Section 9.3
       v                            |
  Design service                    |
       |                            |
       v                            |
  Validate optical design           /
       |                   ---------
       v                            \ 
  Work Order (physical)             |
       |                            |
       v                            |
  Installation of pluggables etc.   |
       |                            | See
       v                            | Section 9.4
  Service configuration             |
       |                            |
       v                            |
  Service validation & test         |
       |                            |
       v                            |
  Enable Service                    |
       |                            |
       v                            |
  Operate service                   /
~~~~
{: #figure-overview-lifecycle-pluggable title="Lifecycle of a coherent pluggable"}


The following sub-sections discuss the overall flow of activities and then work through the lifecycle stages in some detail.

{: #approve-plug}
## Approving the pluggable type and version

Pluggables, like all equipment, are carefully chosen. A network operations company (the operator) will decide what pluggables to use in the network based upon research and an understanding of capabilities of the pluggables available in the marketplace. These capabilities will be considered against the specific applications, use cases and scenarios that are of relevance to the operator's business.

It is expected that these applications, use cases and scenarios will be developed through "Market research" and as pluggables etc. are assessed. The use cases and scenarios will be applied extensively in later stages.

The operator will acquire samples of each type & version of pluggable of interest and probably test and then trial them. They will also probably carry out "type approval" considering each type&version of pluggable for a particular set of applications (where those applications may be defined by the operator themselves or may be standardized definitions) etc. The full detail of the capability of each type & version of pluggable is relevant at all of these stages (see {{express-capabilities}}). The capabilities are expected to be expressed in a Manifest (see {{plug-manifest}}).

The market analysis will lead to Service type design (some of which will be innovative) and will lead to an understanding of potential revenue. This revenue prediction will be considered when evaluating price and compatibility such that initial sketches of use can be constructed. 

{: #planning-network}
## Planning the network

Specific pluggables (type&version) will be purchased only after detailed planning of the network. To carry out this planning, full knowledge of each type&version of pluggable will be required. The planning process will account for key pluggable properties to explore viability and compatibility. The planning will use predictions of "service demand" (e.g., using a demand matrix) and hence infrastructure need to determine purchase volumes, phasing etc.

The exercise may result in identification of several type & versions of pluggable that can be interchanged for a particular specific purpose. Clearly, pluggable pricing will also be accounted for in this phase. Again, during this stage of the lifecycle the full detail of the Manifest for each type & version of pluggable is relevant.

During the "Network planning" process different types of service relevant for the applications, use cases and scenarios (identified in {{approve-plug}}) will be explores and specific approaches to realizing each resulting type of service will be determined. This will result in design of specific "service realization" patterns and templates that will be used in later stages of the process. The approach to deploying each service type is defined for each operational context (application etc.)

As a result of the planning exercise, numbers of each pluggable type&version required will be known and purchasing can be initiated. The purchased pluggables will be added to the inventory and spares holdings.

{: #service-demand}
## Dealing with service demand

The planning exercise leads to optical infrastructure requirements with some timetable for deployment. The "Optical infrastructure" is designed (using the patterns/templates designed in {{planning-network}}. The infrastructure will be deployed as appropriate based upon predicted and actual service demand etc. 

When optical "services demand" is received, perhaps to provide underlay for the packet network or driven by a specific service contract, optical network analysis is carried out to evaluate how to efficiently and effectively achieve the specific service demanded. This analysis will consider the whole optical network including the plugs and ROADMs etc. In most cases this "Service design" will use patterns/templates constructed in {{planning-network}} in conjunction with relevant capability information for the pluggable type&version.

Prior to progressing further it is important to note that pluggables are highly valuable, and correspondingly expensive. They are deployed in a controlled fashion. There are a range of policies for deployment of pluggables.

In some cases, at one extreme end of the range of policy choices, an operator may decide to fully populate a packet device with a selection of pluggables and may cable them to adjacent ROADMS. However, it is more likely that pluggable deployment will be on a just-in-time basis, at the other end of the range of policy choices, so a pluggable is not deployed (and hence is not cabled) until the solution to realization of the optical service has been determined.

Regardless of the pluggable deployment approach, the pluggable capability will be accounted for in the optical network analysis activity. Where pluggables are present, the range of installed pluggables constrain the possible realizations, where the pluggables have not been deployed all approved pluggables (type&version) could be considered during the analysis, although capability of the relevant packet devices to support specific pluggables will also need to be considered, and this may eliminate some pluggables. In addition, if there is some urgency, the availability of the type of pluggable to the installation engineer and/or in the local spares holding inventory may also be considered.

The optical design will be "validated" in terms of "viability" and compatibility prior to proceeding. This analysis takes into account the full definitions of the pluggable type&versions of interest, where each is defined in a corresponding and referenced manifest.

{: #install-operate}
## Installing and operationalising the pluggable

Once the design is available, any necessary physical installation exercise (pluggable installation, cabling etc.) is carried out, driven by "Work orders" that identify the type&version of pluggable to instal etc. 

On detection of the pluggable instance, the control system will validate that the work order has been carried out correctly. To do this, the full type&version of the pluggable is read and compared with the intent. Where there are discrepancies, either a work order is constructed to correct the installation error after the detected pluggable type&version is evaluated for compatibility with the specific design. This evaluation is done using the Manifest for that type&version. It is possible that the type&version may be acceptable although perhaps a little more expensive than the optimum choice etc.

Once the type&version of pluggable has been confirmed, the cabling to the pluggable will be validated and the service set up and validated. Depending upon the operator practices, there may be an extensive service test phase prior to handing over the service. The service may not be enabled immediately, but will be at some point after which the service will become operational. 
From this point on, normal live service/equipment management/control will be active.

Beyond this point normal operational activities such as engineering works, restoration, upgrade, fault location etc. will be carried out. Clearly, there is also the reverse sequence which includes deactivating a service and removing the plug and there are also various edits and refinements that result from changes in demand and changes in understanding of the service needs etc. These steps have not been covered at this stage as the initial list above is sufficient to the develop a deep understanding of the control of the plugs. Further stages will be added in a future version of this document.

In addition, during transition towards a more automated future, there are processes related to discovery of existing network etc. In many of these processes the current state of the network is understood including the type&version of each pluggable. Some degree of understanding of capability of pluggables (and any other equipment) is relevant. The approach using manifests appears appropriate to gain this understanding.

{: #express-capabilities}
## Expressing capabilities

As highlighted above, prior to installation of an optical pluggable in a device (with packet functions etc.), various research, approval, planning and design activities must be carried out (as they would be for any hardware). All of these activities will require information on the capabilities of the pluggable. 

Detailed information on the capability of the pluggable is required long before it is installed and operating. This points to the need for a model of capability (of a type of pluggable) that is independent of the model of a running instance (and hence points to decoupling of the model of capability from the model of the operation of the pluggable). This also suggest that discovery of capability detail from the pluggable is not sufficient/appropriate for deployment (although it may be useful in a lab context). 

A machine interpretable definition/specification for the pluggable should be available (independent of the pluggable instance) for each pluggable type&version where the statement of type&version (complete type&version) used is to the degree sufficient to precisely identify the relevant (unique) definition/specification. The complete type&version may include hardware type&version, firmware type&version and software type&version details (where the firmware/software influences the operation/control of the pluggable). This is essentially the type&version used when considering spares holding and like-for-like replacement in the field.

From this perspective, all that is required from a running pluggable is to report the complete type&version detail so that this can be confirmed as the right type&version. The type&version can be used to reference the relevant unique specification.

It is important to clarify the definition of capability. In this document, the term capability means "A quality or facility that enables something to carry out some activity and/or take some role". In the context of an equipment, the term applies to its functional and physical properties.

Considering a pluggable (as for many other equipments), this would include specification of capabilities such as:

- physical size, form factor and shape (the capability to fit in a particular type of location)
- connector type (the capability to physically interconnect with a compatible connector)
- bus architecture (the capability to communicate with a compatible component)
- optical termination characteristics (the functional capabilities emergent from the powered physical equipment, allowing interconnection with corresponding compatible functions)
- measurement opportunities (the functional capabilities to provide information to various control functions)

A capability statement may be a precise single value with no uncertainty, a range, a collection of related ranges and thresholds etc. Where some aspect has variability or is controllable, this is also required to be specified.

For an equipment to be understood and used by a control system, the detailed information on capabilities must be available in machine interpretable form (to the degree necessary for any particular function to be carried out). The machine interpretable statements may be in the form of software, but preferably should be in the form of data (information) that can be readily ingested by tooling and ideally in a standardised language. 

Traditionally, the published statements of capability have been in somewhat ambiguous text that require interpretation and conversion into a machine interpretable form through a manual intermediate step (normally performed, with errors and performed many times for any particular device type etc.). It is suggested here that the best source of the machine interpretable data is the specifying authority (e.g., ITU-T for standard applications, the vendor for plug capabilities, an operator for non-standard applications).

{: #proprietary-capabilities}
## Dealing with proprietary capabilities

Where the pluggable offers proprietary capabilities, it is possible that there are proprietary properties available from the pluggable control interface to the packet device. These properties may be expressed, on the device interface to the controller, in data conforming to a proprietary definition stated in YANG. For the packet device to be able to express the proprietary properties it needs the YANG augment files, the pluggable control interface definition and a mapping definition (where that provides the details of the transforms necessary to generate the exposed property from the information provided by the pluggable). 

In an ideal realization of the control solution, the controller could provide the packet device with the YANG augment definition, and the mapping definition in such a way that this could be run by generic software on the packet device requiring no change to the software of the packet device. 

This approach could also be taken to cater for enhancements to the standard YANG including mappings from proprietary properties on the pluggable and new standard properties in the device interface to the controller.

Some proprietary capability statements may be commercially sensitive. It would be quite reasonable to encrypt the related capability statements allowing for them to be passed to a specific vendor control component without being observed or interpreted in any way by other control components (from other vendors). There may be a requirement for an NDA to enable access to the data. This NDA can be used to gate the delivery of this commercially sensitive encrypted information. The encrypted information may be passed via a special secure channel directly to a component authorized to decrypt the information into machine interpretable form and use it.

{: #architecture-implications}
# Implications for the Functional Control Architecture

[Editor's note: To be added in a later release.]

The following section considers the interaction sequence, resulting from the pluggable lifecycle analysis, within the functional control architecture and highlights resulting adjustments to the control functionality. Note that this section does not deal with the physical realization of the control components of the functional architecture other than those dependent on the device and pluggable physical boundaries.

{: #plug-manifest-usage}
# Usage of Coherent Pluggables Manifest

Within this section, we present a few use-cases showcasing the practical application of the coherent pluggable manifest.

## Coherent Pluggables Manifest Example-1

The first example is illustrated in {{figure-optical-pluggable-manifest-usage-1}}. This is a simple example where the packet over optical network has been already provisioned with both optical underlay and packet overlay services. The role of SDN controller is just to discover and manage the network. In other words, the SDN controller was not involved in various aspects of service provisioning and viability. The second example will come all these aspects in more detail. 

~~~~

      <------------------ L3 service-1 ------------------->
       <------------------ TE-Tunnel-1 ------------------>
         <----------------- IP link-1 ----------------->
           <------------- L0 service-1 -------------> 
 
   |----------|        |------------------|
   | Coherent |        |                  |
   | Pluggable|  <-->  |  SDN Controller  |
   | Manifest |        |                  |
   |----------|        |------------------|
                                ^
                                |
                                v
                      |------------------|
         port_a       |                  |
     |------| p1    |------|             |
     |  R1 ++-\     |  m1  |             |       port_b
     |------|  \    |------|          |------|  p2 |------|
                \      |              |  m3  |-----++ R2  |
                 \  |------|          |------|     |------|
                  \-|  m2  |             |
                    |------|             |
                      |                  | 
                      |------------------|

  Legend:
    ----        Optical fibers
    ++ p1,p2    Coherent pluggables
    R1, R2      Packet device (i.e., Router)
    m1, m2, m3  Photonic node (ROADM) 

~~~~
{: #figure-optical-pluggable-manifest-usage-1 title="Coherent Pluggable Manifest Usage 1"}

In this example, all optical and IP/MPLS services had been already provisioned and deployed and the packet over optical network is fully functional.

Within packet devices R1 and R2, coherent pluggables p1 and p2, are installed, interfacing through ports port_a and port_b, respectively. Both coherent pluggables are provisioned for the following operational-mode. 

- [organization-id, operational-mode] = [OIF, 0x3E]

A single photonic service is established between these pluggables and an IP link is mapped to this L0 photonic service. The overlay TE-Tunnel-1 and L3 service-1 had been also provisioned. The following steps outline the details of how this network is discovered and managed by SDN controllers (note that the SDN controller was not involved in provisioning):

- Packet devices (R1, R2), pluggables (p1, p2), and photonic devices (m1, m2, m3) are all discovered by SDN controllers.
- The SDN controller also discovers all underlay and overlay services, i.e., L0 service-1, IP link-1, TE-Tunnel-1 and L3 servcie-1. 
- The SDN controller has the network inventory, including coherent pluggables p1 and p2. In particular for coherent pluggables, basic information such as pluggable type, vendor, manufacturer, serial number and software version will be provided by pluggables to SDN controller.
- The inventory of packet devices R1 and R2 contains the  configurations of pluggable attributes such as "configured operational-mode," "configured central frequency," and "configured output power".
- Specifically, using the basic information of pluggables p1 and p2 such as pluggable type, vendor, manufacturer, serial number and software version collected earlier from packet devices R1 and R2, the SDN controller can use the "Coherent Pluggable Manifest," to access the entire information of both pluggables p1 and p2. This includes all supported operational-modes along with all attributes related to each supported operational-mode.
- The SDN controller can collect all PM telemetry data from the network (including pluggables).
- The SDN controller can collect all alarm notifications from the network (including pluggables).
- The SDN controller can further change, modify, optimize the network (if needed).

## Coherent Pluggables Manifest Example-2

The example in {{figure-optical-pluggable-manifest-usage-2}} demonstrates the usage of the "Coherent Pluggable Manifest" for entire lifecycle of photonic service from including service planning, viability, provisioning, collection of PM telemetry, collection of alarm notifications and optimization. 

Note that the packet over optical network in {{figure-optical-pluggable-manifest-usage-2}} is not created yet. The ports port_a and port_b of packet device R1 and R2 are empty and can accept coherent pluggables. In addition, ports port_a and port_b are not connected to the optical network yet, i.e., there is no connection between packet devices R1, R2 and optical network. The port_a and port_b of packet device R1 and R2 can be potentially connected to any photonic nodes m1, m2 or m3.

Operator's goal is to use the SDN controller to plan, provision and monitor an optimal IP link-2 between packet devices R1 and R2. Optionally they can also provision overlay TE-Tunnel-2 and L3 service-2. To achieve this, the SDN controller should first plan an optical service-2, perform the viability to make sure this photonic service is feasible, provision it and then map it to an IP link-2.

~~~~

      <------------------ L3 service-2 ------------------->
       <------------------ TE-Tunnel-2 ------------------>
         <----------------- IP link-2 ----------------->
           <------------- L0 service-2 -------------> 
           
   |----------|        |------------------|
   | Coherent |        |                  |
   | Pluggable|  <-->  |  SDN Controller  |
   | Manifest |        |                  |
   |----------|        |------------------|
                                ^
                                |
                                v
                      |------------------|
         port_a       |                  |
     |------|       |------|             |
     |  R1 .........|  m1  |             |       port_b
     |------|  .    |------|          |------|     |------|
                .     |               |  m3  |....... R2  |
                 .  |------|          |------|     |------|
                  ..|  m2  |             |
                    |------|             |
                      |                  | 
                      |------------------|

  Legend:
    .....       Packet device can be potentially 
                connected to photonic nodes m1, m2, m3
    R1, R2:     Packet device (i.e., Router)
    m1, m2, m3  Photonic node (ROADM) 
    port_a      Router R1 port which is empty and can 
                potentially populated by coherent pluggables
    port_b      Router R2 port which is empty and can 
                potentially populated by coherent pluggables

~~~~
{: #figure-optical-pluggable-manifest-usage-2 title="Coherent Pluggable Manifest Usage 2"}

Let's assume that the operator of this network has already purchased coherent pluggables from Vendor-X, which can support the following two operational-modes. Note that the detail information of these operational-modes including all optical and photonic attributes are already uploaded to "Coherent Pluggable Manifest" by Vendor-X and OIF.

- [organization-id, operational-mode] = [OIF, 0x3E]
- [organization-id, operational-mode] = [Vendor-X, 0x22]

The following steps outline the details of how this network is planned, provisioned, discovered and managed by SDN controllers:

- At first, there are no coherent pluggables installed in the packet devices yet. There are also no connection between packet devices and optical network.
- All packet devices (R1, R2) and photonic devices (m1, m2, m3) are managed by the SDN controller.
- As a result, the SDN controller maintains an inventory of packet and photonic devices within the network (i.e., nodes R1, R2, m1, m2, m3).
- To create the IP link-2, the SDN controller should plan and then provision the optical service-2 between port_a and port_b. 
- To this end, the SDN controller should first design an optical service and then performs the viability check to make sure the optical service is viable in this network. 
- So, the SDN controller calculates the best optical path from port_a to port_b. 
- Next, the SDN controller performs the viability on optical route to make sure the optical path is viable in the network.
- To do viability, the SDN controller checks all attributes of all operational-modes to find the most optimal operational-mode. To do this, the SDN controller connects to the "Coherent Pluggable Manifest" and access all optical and photonic attributes of all operational-modes (such as chromatic dispersion, FEC, modulation, polarization mode dispersion etc.) and performs the viability.
- After performing the optical path calculation and optical viability, the SDN controller selects the best coherent pluggable to be installed on port_a and port_b and the best optical route from port_a to port_b.
- Upon completion of the photonic viability check, the SDN controller determines which photonic devices (m1, m2, m3) should be connected to ports port_a and port_b.
- The SDN controller informs the operator of the selected coherent pluggables for ports port_a and port_b and provides instructions on how to connect them to the respective photonic devices (m1, m2, m3).
- The operator installs the designated pluggables into ports port_a and port_b and connects them to the specified photonic devices.
- The SDN controller then manages the newly installed pluggables.
- As part of the photonic viability process, the SDN controller knows the specific attributes of the pluggables, including "configured operational mode," "configured central frequency," and "configured output power."
- As a result, the SDN controller configures these configurations to each pluggable on port_a and port_b
- The SDN controller should also configure optical nodes m1, m2, m3 with attributes such as output power.
- The SDN controller provisions the optical service_1 between two conheret pluggables on port_a and port_b.
- The SDN controller also provisions the IP link-2 between packet device R1 and R2.
- The SDN controller can collect all PM telemetry data from the network (including pluggables).
- The SDN controller can collect all alarm notifications from the network (including pluggables).
- The SDN controller can further change, modify, optimize the network (if needed).


# Security Considerations

TODO Security

# IANA Considerations

This document has no IANA actions.

--- back

{:numbered="false"}

# Acknowledgments

TODO acknowledge.
