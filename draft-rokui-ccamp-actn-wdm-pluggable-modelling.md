---
title: "Data Modelling and Gap Analysis of Optical Pluggables in Packet Over Optical Network"
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
    org: Nokia
    email: ggalimbe56@gmail.com

  -
    ins: H. Venkatraman
    fullname: Harish Venkatraman
    org: Nokia
    email: harish.venkatraman@nokia.com

  -
    ins: G. Mishra
    fullname: Gyan Mishra
    org: Verizon
    email: gyan.s.mishra@verizon.com

  -
    ins: S. Melin
    fullname: Stefan Melin
    org: Telia
    email: stefan.melin@teliacompany.com

  -
    ins: M. Hossein Poor
    fullname: Majid Hossein Poor
    org: Telstra
    email: majid.hosseinpoor@team.telstra.com

  -
    ins: D. Demeter
    fullname: Dacian Demeter
    org: Telus
    email: dacian.demeter@telus.com

normative:
  CMIS:
    title: "OIF Implementation Agreement (IA) Common Management Interface Specification (CMIS))"
    author:
      org: OIF Forum
    date: 4 September 2024
    seriesinfo: OIF CMIS IA
    target: https://www.oiforum.com/wp-content/uploads/OIF-CMIS-05.3.pdf

  OIF-400ZR:
    title: "Implementation Agreement 400ZR"
    author:
      org: OIF Forum
    date: 3 November 2022
    seriesinfo:
    target: https://www.oiforum.com/wp-content/uploads/OIF-400ZR-02.0.pdf

  G.698.1:
    title: "Multichannel DWDM applications with single-channel optical interfaces"
    author:
      org: ITU-T Recommendation G.698.1
    date: June 2005
    seriesinfo:
    target: https://www.itu.int/rec/dologin_pub.asp?lang=f&id=T-REC-G.698.1-200506-S!!PDF-E&type=items

  G.698.2:
    title: "Amplified multichannel dense wavelength division multiplexing applications with single channel optical interfaces"
    author:
      org: ITU-T Recommendation G.698.2
    date: November 2018
    seriesinfo:
    target: https://www.itu.int/rec/dologin_pub.asp?lang=e&id=T-REC-G.698.2-201811-I!!PDF-E&type=items

  G.695:
    title: "Optical interfaces for coarse wavelength division multiplexing applications"
    author:
      org: ITU-T Recommendation G.695
    date: May 2025
    seriesinfo:
    target: https://www.itu.int/rec/dologin_pub.asp?lang=e&id=T-REC-G.695-200402-S!!PDF-E&type=items

  G.959.1:
    title: "Optical transport network physical layer interfaces"
    date: 2012-02
    target: ITU-T Recommendation G.959.1
    seriesinfo:
    target: https://www.itu.int/rec/dologin_pub.asp?lang=e&id=T-REC-G.959.1-202401-I!!PDF-E&type=items

  OC-device:
    title: "Module to extend OpenConfig terminal device operational modes data"
    date: Version 0.2.0
    target: OpenConfig
    seriesinfo:
    target: https://openconfig.net/projects/models/schemadocs/yangdoc/openconfig-terminal-device-properties.html

  OC-platform:
    title: "Data model for representing a system component inventory"
    date: Version 0.31.0
    target: OpenConfig
    seriesinfo:
    target: https://openconfig.net/projects/models/schemadocs/yangdoc/openconfig-platform.html

  TAPI-2.5.0:
    title: "Linux Foundation Project Transport API (TAPI)"
    date: Version 2.5.0
    target: T-API
    seriesinfo:
    target: https://github.com/Open-Network-Models-and-Interfaces-ONMI/TAPI/tree/v2.5.0

  SFF8024:
    title: "SFF Module Management Reference Code Tables"
    author:
      org: SNIA SFF Technology Affiliate (TA) Technical Work Group (TWG), Small Form Factor Technology Affiliate
    date: November 27, 2023
    seriesinfo:
    target: https://members.snia.org/document/dl/26423

informative:

--- abstract

This draft outlines the pluggable module attributes within a host device. It includes representations of optical pluggable module capabilities, configuration, states, and telemetry data. These attributes draws from existing IETF standards and incorporates input from other industry forums and standards, such as ITU-T, OpenConfig, OIF and ONF TAPI, to ensure uniform structuring and consistent naming conventions. Note that the IETF terminology shall be given precedence wherever possible. In case there is a duplication of an attribute, this draft may describe how the attribute is named in the related document. Only if no attribute exists in IETF RFCs or IETF WG drafts, new attributes shall be introduced if they are needed.

This draft provides a gap analysis with respect to existing IETF work in the following areas:

* It provides an analysis of optical attributes in a set of IETF documents with specifications of other organizations to identify modeling gaps.
* It identifies modeling needs addressing the specific aspect of pluggability of transceiver modules. The authors recognize the fact that that not all pluggable modules are coherent, not all coherent pluggable modules are DWDM capable and not all DWDM capable interfaces are implemented as pluggable modules. This analysis identifies gaps to manage the lifecycle of an optical pluggable module, from operator approval and viability assessment, to deployment, monitoring and phase-out.

The lifecycle of an optical pluggable module, from operator approval and viability assessment to deployment and monitoring, is also addressed.

--- middle

# Terminology

{::boilerplate bcp14-tagged}

The following terms abbreviations are used in this document:

- Optical modules: short term for optical transceiver modules. Such module can be of fixed or pluggable module nature and provides the optical interface for communication.

- Pluggable modules: short term for pluggable optical transceiver module. Pluggable modules are a specific form of optical modules that are field replaceable. They pro

- Coherent module: short term for optical transceiver module providing coherent optical modulation capabilities.

- DWDM module: short term for coherent module supporting the use of a DWDM line system.

- Common Management Interface Specification (CMIS): The Common Management Interface Specification is an Implementation Agreement (IA) developed by the Optical Internet Forum (OIF) {{CMIS}}. This specification defines an interface for managing optical (and copper) modules in a standardized way while still permitting vendor-specific functionality. It eases the integration of modules supporting the CMIS interface into host platforms from different system vendors. It shall be noted that CMIS targets any module, not only coherent optical modules, which is the scope of this document. The CMIS interface is applicable to on-board module types (fixed optics) as well as pluggable modules types such as QSFP Double-Density (QSFP-DD), OSFP, COBO, QSFP and other module types.

- optical module media side:

- optical module host side:

- Monitored attributes: The optical module attributes which can be measured, monitored, estimated, or otherwise observed. The monitored attributes are the inputs to performance monitors which in turn provide real time samples, threshold crossing supervision, and sometimes sample statistics.



# Introduction

Packet traffic has been transmitted across optical networks for many years, leveraging the advantages of optical transmission and switching combined with packet switching. Traditionally, Optical Line Systems were fully integrated with DWDM Transponder modules in proprietary implementations while non-DWDM (aka. client) modules were integrated with their hosts. With the advent of open optical networking, also DWDM transponder modules are now hosted by sytems outside the Line System.

In numerous network setups, packet and optical networks have been engineered, operated, and managed separately, leading to siloed operations that can be suboptimal and inefficient. Advancements in optical component design have led to increased density, enabling entire coherent optical terminal systems that previously required multiple circuit packs to now fit into a single small form factor "coherent optical module." Integrating coherent optical modules into switching and routing devices can result in reduced network costs, power consumption, and footprint, while also enhancing data transfer rates, reducing latency, and expanding capacity, although in some cases, separate packet and optical solutions may still be preferred due to other engineering and deployment considerations.

These trends, coupled with the desire to utilize the best components available, have given rise to open optical pluggable modules. Communication between optical modules and the host occurs through the CMIS standard developed by OIF {{CMIS}}.

While standardized transmission modes like ZR can handle basic applications, proprietary modes from vendors are often necessary to achieve optimal performance.

This draft provides a gap analysis of optical pluggable modules in the context of a packet over optical network. The model presented in this document analyzes three key functional blocks:

- Photonic/Optical attributes: These attributes defines the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc.

- Host/Electrical attributes: These attributes defines the characteristics of interconnect between the host and the optical pluggable module, such as lane count, FEC etc., which both the optical pluggable module and the packet host must understand and act upon.

- Physical and functional aspects of the pluggable module (i.e., equipment): This defines attributes of the optical pluggable module itself, such as plug type, version, thermal characteristics, power consumption etc.

For each of these functional blocks, the model shall provide the necessary attributes in following areas:

- Capabilities: These attributes are read-only and defines the functional capabilities of the optical module. They are defined in a profile called "operational-mode" and contains attributes such as modulation, bit-rate, baud-rate, chromatic-dispersion, polarization, FEC etc. An optical module might support one or multiple operational-modes.

- Configurations: Since an optical module can support multiple operational-modes, these read-write attributes configure the module to be functional in one of those operational- modes. Example of configuration attributes are output power, central frequency and operational-mode.

- States and performance monitoring telemetry data: These read-only attributes will be generated by optical modules and represents various states and PM data of the optical modules such as channel input power, channel output power, central frequency, laser temperature, current OSNR, Link Up/Down State, Alarm State, Laser On/Off State etc. In most cases these attributes are changing with time and optical modules report current, average, min and max values. It is also possible to apply thresholds on each of these attributes to support threshold crossing alert (TCA).

Both vendor-agnostic and vendor-specific attributes are important considerations in the modeling of optical pluggable modules.

The document is divided into the following sections:

- {{optical-pluggable-in-device-packet-function}}: Optical pluggable module in a Device with Packet Functions

- {{building-blocks}}: Optical Module Functional Building Block

- {{data-model}}: Optical Modules Data Modeling

- {{google-sheet}}: Complete list of Optical Modules Attributes From Google Sheet

- {{gap-analysis}}: Optical Module Data Modeling Gap Analysis

- {{plug-lcm}}: Optical Pluggables Lifecycle Management

{: #optical-pluggable-in-device-packet-function}
# Optical pluggable module in a Device with Packet Functions

{{figure-details-packet-optical-device}} shows a host packet device from vendor X, which is connected to optical device, equipped with optical pluggable modules from vendor X and Y. This figure exposes the following internal and external interfaces:

A. This interface provides the control of the host and all it's components. Note that the YANG data model addressing pluggable modules will be provided at interface (A), i.e., the management interface of the device. In general the HOST can be any devices (packet, OTN etc.) But in specific this draft addresses this when the Host is a packet device.

B. The CMIS {{CMIS}} defines the communication interface between host devices and optical modules.

C. The data flow between the optical pluggable module and the packet data function through this interface. This is electrical interface between optical pluggable module and the host. {{building-blocks}} will discuss this in more details.

D. Optical fiber connecting the optical devices to optical pluggable modules. This carries the flow of photonic signal from the optical device to the optical pluggable modules. {{building-blocks}} will discuss this in more details.

The model presented in {{data-model}} consolidates properties of optical pluggable module on interfaces (D) and (C) in {{figure-details-packet-optical-device}} where interface (D) provides the photonic/optical attributes and interface (C) provides the host/electrical attributes.

~~~~
                  |---------------|
                  |   P-PNC(s),   |
                  |   O-PNC(s),   |
                  |   MDSC        |
                  |---------------|
                          ^
                          |  (A)
      +-------------------|-------------------+
      |            |---------------|          |
      |            |Host Management|          |
      |            |---------------|          |
      |                   |                   |  Packet Device
      |                   V                   |  Vendor X
      |        |---------------------|        |  (i.e, Host)
      |        v                     v        |
      |  |-----------|          |----------|  |
      |  | Packet    |          | optical  |  |
      |  | Function  |..........| Plug     |  |
      |  | Data      |          | Data     |  |
      |  |-----------|          |----------|  |
      |        .                      .       |
      |        .                      . (B)   |
      |        .                      .       |
      |  |--------------|   (C)   |------------------|  (D)
      |  |Packet Device |<------->| optical Plug #1  |=======
      |  |Function      |<---|    | Vendor X         |
      |  |--------------|    |    |------------------|
      |                      |                |
      |                      |    |------------------|
      |                      |--->| optical Plug #2  |=======
      |                           | Vendor Y         |
      |                           |------------------|
      |                                       |
      +---------------------------------------+

  Legend
    (A) Packet device management interfaces
              (e.g., YANG, NETCONF, gNMI, etc.)
    (B) CMIS interface between Optical pluggable module and Host
    (C) Host side of coherent optical pluggable module (towards Host)
    (D) Media side of coherent optical pluggable module
              (towards Optical/Photonic network)

~~~~
{: #figure-details-packet-optical-device title="Packet device with optical pluggable modules"}

{: #building-blocks}
# Optical Module Functional Building Blocks

The functional building blocks of the optical modules of {{figure-details-packet-optical-device}} are shown in {{figure-optical-pluggable-building-blocks}} and has three major functions:

- Media side: This functional block represents all Photonic/Optical attributes of the optical modules (interface (D) in {{figure-details-packet-optical-device}}). These attributes define the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc., which do not directly affect the behavior of the host packet device. Note that the goal of this draft is to identify optical module capabilities, configuration, states, and telemetry data attributes from existing IETF standards and incorporates input from other industry forums and standards, such as ITU-T, OpenConfig, OIF and ONF TAPI and then perform the gap analysis to compare optical module attributes with current IETF drafts, identifying any modeling gaps. Eventually based on the identified gaps, the draft proposes solutions to address missing attributes, such as augmenting or updating existing IETF YANG models. Note that IETF terminology are given precedence wherever possible. In case there is a duplication of an attribute, this draft may describe how the attribute is named in the related document. Only if no attribute exists in IETF RFCs or IETF WG drafts, new attributes shall be introduced if they are needed.

- Host side: This functional block represents all Host/Electrical attributes of the coherent pluggables (interface (C) in {{figure-details-packet-optical-device}}). These attributes defines the characteristics of interconnect between the host and the optical pluggable, such as lane count, FEC etc., which both the optical pluggable and the packet host should understand and act upon. Note that the mapping between host and media might be one to many, i.e., a host logical channel might map to one or more media logical channel.

- Equipment attributes: These attributes represent all physical and functional aspects of the optical pluggable module such as plug type, software version, thermal characteristics, power consumption etc.

~~~~

  optical Pluggable Module
 |--------------------------------------------------------------|
 |                                                              |
 |  |--------------------------------------------------------|  |
 |  |                        Equipment                       |  |
 |  |--------------------------------------------------------|  |
 |                                                              |
 |           Host side                      Media side          |
 | |---------------------------|  |---------------------------| |
 | |                           |  |                           | |
 | | |---------|  |---------|  |  | |---------|  |---------|  | |(Tx)
-----| Elec.   |  | Host    |  |  | | Media   |  | Optical | ----->
-----| Channels|--| Logical |-------| Logical |--| Channel | <-----
-----|         |  | Channels|  |  | | Channels|  | (OTSi)  |  | |(Rx)
 | | |---------|  |---------|  |  | |---------|  |---------|  | |
 | |                           |  |                           | |
 | |---------------------------|  |---------------------------| |
 |                                                              |
 |--------------------------------------------------------------|

~~~~
{: #figure-optical-pluggable-building-blocks title="Optical pluggable module Building Blocks"}

The following sections are describing the details of optical pluggable module functional blocks in more details.

## Optical Channel/OTSi

The media side of the optical module is further divided into two functional blocks; Optical Channel/OTSi and Media Logical Channels. The characteristics of the Optical channel/OTSi are (See section 2.3.1 of {{?I-D.ietf-ccamp-optical-impairment-topology-yang}} and also section 3.2.4 {{G.959.1}}).

* This is the module interfaces facing the optical network.

* Represents the digital wrapper that transports services over a wavelength

* Represents the wavelength and the optical aspects of the signal modulated onto baud-rate, bit-rate, modulation scheme, frequency, tx-power, etc.

* Optical signal FEC termination/source, FEC characteristic information – configuration, if possible, Pre-FEC BER, Post-FEC BER, fail/degrade thresholds, raw corrected/uncorrected counts

* Provides configuration of the signal and monitoring capabilities

* Provides monitoring capabilities in the Tx (toward fiber/medium) and Rx (from fiber/medium) directions, Total optical power, optical channel power, optical statistics

## Media Logical Channels

The characteristics of the Media Logical Channels are:

* Logical representation of the hierarchical view of the digital framing layers used for transport of services over the wavelength

* Provides access to information for configuration and monitoring characteristics. For example, for 400ZR/OpenZR+ {{OIF-400ZR}}, it represents the 400ZR frame structure in which Ethernet services are mapped and for an OTN encapsulated signal, it represents the OTU, ODU, OPU frame structures, perhaps with a multi-layer multiplex structure, in which Ethernet and other types of services are mapped

## Host Logical Channels

The host side of the optical module is further divided into two functional blocks; Host Logical Channels and Electrical channels. The characteristics of the Host Logical Channels are:

* Logical representation of the hierarchical view of the digital framing layers for services carried on the electrical lanes of the device

* Provides information for configuration and monitoring characteristics of each service

* Represents each service carried over the media logical channel and optical interface/wavelength, e.g., 25GE, 50GE, 100GE, 200GE, 400GE, OTU4, OTUCn etc.

## Electrical Channels

The characteristics of the Electrical Channels are:

Note that the purpose of this section is to clarify the role of electrical channel in the optical module. This purpose of this draft is not to define the data model of the electrical channels.

* The host side lanes of the device forming the physical interface to the host platform data path device(s)

* Lanes grouped to support the type/format and bandwidth of the signal used for a service

* Provides information for configuration and monitoring characteristics of the signal for a service in the electrical domain, e.g., Interface-format, FEC, alarming thresholds, etc.

* Provides monitoring capabilities in the Tx (toward fiber) and Rx (from the fiber).

## Equipment

The "Equipment functional block" in {{figure-optical-pluggable-building-blocks}} represents the pluggable module itself and has the following characteristics:

* Provides manufacturer identification information for the device

* Advertises capabilities of the device including capabilities for the host/client side and the media/line side

* Provides monitoring capabilities of physical characteristics and health of the device, e.g., temperature, voltage, optical transmitter/receiver characteristics

* Provides for configuration where applicable – e.g., of device environmental thresholds

* Supports device level capabilities such as firmware installation, restarts, etc.


{: #data-model}
# Optical modules Data Modeling

\[Editor's notes: As part of Gap analysis, YANG reference/YANG code might be added to the data modeling section/subsections and that the current content shall be considered as placeholder for the model.]

The data modeling of each functional blocks provides attributes in following areas:

* {{plug-capabilities-attributes}}: optical module capability attributes (i.e., supported-modes)
* {{plug-config-attribute}}: optical module configuration attributes
* {{plug-pm-definition}}: optical module performance monitoring data (including State data)
* {{plug-threshold-definition}}: optical module threshold definition
* {{plug-alarm-definition}}: optical module alarm notifications
* {{plug-vendor-specific-attributes}}: Support of Opaque Attributes

{: #plug-capabilities-attributes}
## optical module Capability Attributes (aka, Supported-Modes)

Coherent optical modules have revolutionized optical networking by offering a powerful combination of high performance, flexibility, and ease of deployment. These modules support a broad range of capabilities, making them both efficient and versatile. Their extensive functional capabilities further enhance their effectiveness in diverse networking environments.

From a data modeling perspective, a set of attributes is grouped together and represented by a single identifier known as the "Operational Mode." In essence, each operational mode encapsulates a combination of properties, limitations and capabilities, such as modulation type, bit rate, baud rate, chromatic dispersion, polarization, FEC, and more. Some of these attributes limit value ranges (e.g., minimum and maximum). A optical module can support multiple operational modes, each of which can be defined by one of the following methods.

Note that this current draft adheres to the definitions provided in draft {{?I-D.ietf-ccamp-optical-impairment-topology-yang}}. See Section 2.6 of draft {{?I-D.ietf-ccamp-optical-impairment-topology-yang}} for:

* Standard Mode: This mode pertains to optical specifications developed by standards development organizations (SDOs), such as the ITU-T recommendation {{G.698.2}}.
* Organizational Mode: In this mode, optical interface specifications are defined by operators, industry forums (e.g., Optical Internetworking Forum (OIF) or OpenConfig), or equipment vendors. This allows for the utilization of optical module capabilities that extend beyond existing standards.
* Explicit Mode: This mode enables the explicit encoding of any subset of parameters (e.g., FEC type, modulation type) to facilitate interoperability checks by a controller entity through means not covered within this draft.

For more detailed information, please refer to draft {{?I-D.ietf-ccamp-optical-impairment-topology-yang}}.

{: #plug-config-attribute}
## optical module Configurations Attributes

Referring to {{figure-plug-config}}, optical modules support a set of read-write attributes which are configurable. Example of such configuration attributes are output power, central frequency and operational-mode. Note that as discussed in {{plug-capabilities-attributes}}, since optical modules may support multiple operational-modes, as part of these configuration attributes, operator should configure which of these operational-mode is desired and should be functional.

~~~~

 |-----------------------------------------------------------------|
 |  optical-channel  // OTSi channels                              |
 |      configuration // list of R/W plug configuration attributes |
 |           config-attribute-1                                    |
 |           config-attribute-2                                    |
 |           .....                                                 |
 |           config-attribute-m                                    |
 |-----------------------------------------------------------------|

~~~~
{: #figure-plug-config title="Data structure for optical module Configuration Attributes"}

{: #plug-pm-definition}
## optical optical module Performance Monitoring Data

{{figure-plug-pm}} shows the list of optical module Performance Monitoring (PM) and state data, which are critical components in optical networks, enabling network engineers to ensure optimal performance, identify issues, and maintain network reliability. Operators monitor a range of attributes on both the optical/photonic and electrical sides of optical modules, including channel input power, channel output power, central frequency, current Optical Signal-to-Noise Ratio (OSNR), Bit Error Rate (BER), chromatic dispersion, laser temperature, link status, and more. These parameters directly impact the quality and integrity of the transmitted data across both optical and electrical domains.

~~~~

 |-----------------------------------------------------------------|
 |  optical-channel  // OTSi channels                              |
 |      pm and states  // list of R/O pm and state attributes      |
 |                     // Note-1: Each pm-attribute might have     |
 |                     //         threshold definitions            |
 |                     // Note-2: For each monitored attributes,   |
 |                     //         one SCTG profile can be assigned |
 |           monitored-attribute-1                                 |
 |           monitored-attribute-2                                 |
 |           .....                                                 |
 |           monitored-attribute-p                                 |
 |-----------------------------------------------------------------|

~~~~
{: #figure-plug-pm title="Data structure for optical module PM Attributes"}

As coherent optical technology continues to gain traction, PM has evolved to include more advanced techniques, such as monitoring the quality of modulated signals and detecting impairments that could degrade performance over long distances. By leveraging these PM capabilities, engineers can ensure that the optical layer operates effectively, optimize the utilization of optical resources, and maintain high levels of service continuity and performance throughout the network.

It is important to note that the "monitored attributes" encompass parameters from the media side, host side, and hardware components of optical modules.

Performance Monitoring (PM) data is generated for various "monitored attributes" by optical modules, representing a range of real-time metrics, including current, average, minimum, and maximum values, as well as counters and states. The PM data can be categorized as follows:

* Basic Monitoring PM data: The analogue values which provide the "current values" of a "monitored attributes" such as laser temperature, eSNR (Effective Signal-to-Noise Ratio) at media input, eSNR at host input, laser frequency error, and more.
* Advanced Monitoring PM data: The analogue values which provide the "current, average, minimum, and maximum values" of "monitored attributes" such as transmit signal power, Bit Error Rate (BER), chromatic dispersion, etc.
* Up Counters: The discrete counter values of "monitored attributes" that only increment, such as Bit Error Count, FEC (Forward Error Correction) Uncorrected Errors, Loss of Signal (LOS) count, Loss of Frame (LOF) count, and others.
* Up/Down Counters: The discrete counter values of "monitored attributes" that can both incremented and decremented.
* Operational/Admin States: Represents the states of "monitored attributes" such as link up/down state, alarm state, laser on/off state, Automatic Power Control (APC) status, and more.

For "Up Counters" there might be two approaches:

* Continuous Increment: The counter value continuously increments without resetting upon read.
* Reset on Read: The counter value resets either on read or based on a predefined condition.

For "advanced monitoring performance management (PM) data", where current, average, minimum, and maximum values are provided by the optical module, a "windowing mechanism" is essential. Currently, this mechanism is implemented by the host platform, not the module itself. For instance, the host platform utilizes the windowing mechanism to segment the PM data collected by the optical module. Within each window, the host calculates the minimum, maximum, and average values of the PM data, enabling a granular and time-specific analysis of the module's performance.

A variety of performance monitoring metrics, including minimum, maximum, average, and instantaneous values, can be collected. These metrics offer a comprehensive view of performance fluctuations, allowing for precise monitoring and quicker response times to anomalies. Minimum and maximum values help identify the extremes of performance, while average values give a sense of typical performance levels. Instantaneous values, on the other hand, provide real-time insights, which are crucial for immediate issue detection and resolution. This multi-faceted approach ensures that network performance is consistently monitored and maintained at high standards.

{{plug-threshold-definition}} will discuss the collection type and how they are related to the above-mentioned PM data. It also covers the optical modules support for threshold crossing alerts (TCA) for all or a subset of monitored attributes.

{: #plug-threshold-definition}
## optical module Threshold Definition

As indicated in {{plug-pm-definition}}, optical modules are capable of providing the threshold crossing alert (TCA) for all or subset of "monitored attributes". In this situation, the optical module raises an alert which informs the host about operationally undesired situations or about critical threshold crossings of monitored attributes. The optical module raises an alert by setting an associated Flag on module memory-map that represents the alert.

As mentioned previously, the TCA might be supported for a subset of optical module monitored attributes. Since it is possible that the optical module has different capabilities to raise threshold for different monitored attributes, to provide a general solution for threshold definition on optical module monitored attributes, this draft introduces the concept of "Supported Collection and Threshold Group (SCTG)" shown in {{figure-plug-threshold-definition}} which defines the configurable threshold values and collection types (i.e., the collection of current value, average value, min/max value are supported).

In summary, as outlined in {{plug-pm-definition}} and {{plug-threshold-definition}}, each optical module PM/State attribute can have multiple Performance Monitoring (PM) values, such as current, average, minimum, and maximum, as well as multiple threshold levels, including warning, minor, major, and critical. To streamline this representation in a Google Sheet, each optical module PM/State attribute will be associated with a corresponding SCTG-Type reference.

For example, consider the optical module PM attribute "channel-input-power." Tthe optical module collects PM values for current, average, minimum, and maximum, while also supporting the configuration of threshold values for warning, minor, major, and critical levels. As illustrated in {{figure-plug-threshold-definition}}, the PM attribute "channel-input-power" is linked to "SCTG-Type-1" to simplify its representation in Google Sheet.

~~~~
         Supported-Collection-and-Threshold-Group (SCTG)
 |----------------------------------------------------------------|
 |   SCTG-Type-1:                                                 |
 |     Collection: current, average, min, max                     |
 |     Configured Threshold: warning, minor, major, critical      |
 |                                                                |
 |   SCTG-Type-2:                                                 |
 |     Collection: current                                        |
 |     Configured Threshold: warning, minor, major, critical      |
 |                                                                |
 |   SCTG-Type-3:                                                 |
 |     Collection: current, average, min, max                     |
 |   ...                                                          |
 |   SCTG-Type-n:                                                 |
 |----------------------------------------------------------------|
    // Note:
    // These are just a few examples. More SCTG can be defined
~~~~
{: #figure-plug-threshold-definition title="optical module Collection and Threshold Group Definition"}

To define the warning, minor, major, critical threshold values for a optical module monitored attribute, operator should set upper and lower limits that delineate acceptable performance ranges. This ensures that any deviations can be quickly identified and addressed. A rolling window between min-time and max-time should be employed to dynamically adjust these thresholds based on recent data trends, providing a more accurate reflection of current network conditions. By continuously updating the thresholds, network performance can be maintained within optimal parameters, reducing the risk of undetected issues.

Note that sometimes these thresholds are configurable and sometime they are hard-coded. It is also possible that a vendor can support a sub-set and super-set of monitored attributes (for super-set they need to augment the yang model).

{: #plug-alarm-definition}
## optical module Alarm Notifications

\[Editor's note: To be added in a later release.]

The optical modules might generate various alarm notifications due to the various reasons.

{: #google-sheet}
# Complete list of optical modules Attributes From Google Sheet

This draft was initiated to evaluate the completeness of existing IETF models related to optical modules by incorporating data models and insights from other industry forums and standards bodies, including ITU-T, OpenConfig, OIF, and ONF TAPI. In particular, the following documents are examined:

* IETF Common YANG Data Types for Layer 0 Networks {{?I-D.ietf-ccamp-rfc9093-bis}}
* IETF YANG  data model to manage configurable DWDM optical interfaces {{?I-D.ietf-ccamp-dwdm-if-param-yang}}
* IETF YANG Data Model for Optical Impairment-aware Topology  {{?I-D.ietf-ccamp-optical-impairment-topology-yang}}
* IETF YANG Data Model for WDM Tunnels {{?I-D.ietf-ccamp-wdm-tunnel-yang}}
* IETF YANG Data Models for requesting Path Computation in WDM Optical Networks {{?I-D.ietf-ccamp-optical-path-computation-yang}}
* Implementation Agreement 400ZR {{OIF-400ZR}}
* OpenConfig system component inventory{{OC-platform}}
* OpenConfig terminal device {{OC-device}}
* ITU-T Multichannel DWDM applications {{G.698.1}}
* ITU-T Amplified multichannel dense wavelength division multiplexing {{G.698.2}}
* ITU-T Optical interfaces for coarse wavelength division multiplexing {{G.695}}
* ITU-T Optical transport network physical layer interfaces {{G.959.1}}
* Linux Foundation Transport API project {{TAPI-2.5.0}}

The primary objective is to assess the properties and structures within these models that are relevant to coherent optical modules and to identify any missing elements or gaps. 

To support this ongoing analysis, relevant properties and structures from both IETF models and external organizations or standards bodies are being collected in Google Sheet. In {{gap-analysis}}, these properties will serve as the foundation for conducting a comprehensive gap analysis.

As discussed in {{plug-capabilities-attributes}}, {{plug-config-attribute}}, and {{plug-pm-definition}}, the google sheet provides the Capabilities, Configuration, and Performance Monitoring attributes for coherent pluggable. The google sheet includes various read-only capability attributes, read-write configuration attributes, and read-only performance monitoring attributes. For a comprehensive list of these attributes, refer to the accompanying optical module Google Sheet.

\[Editorial Note: The reference to the external Google Sheet is used to finalize the gap content, 
once all the info are incorporated in the draft, and in any case before publication, this link shall be removed. Please also note that the content of the google sheet is very important and shall be captured in draft as a table or something else in Appendix section]

You can [download the Google sheet](/Users/rrokui/Desktop/optical-pluggable-attributes-v00-GAP.xslx) to see all the details.


{: #gap-analysis}
# Optical Module Data Modeling Gap Analysis

\[Editorial Note: The “Optical Module Data Modeling Gap Analysis” section is still work in progress and the attributes listed in the 3 tables below are subject to change since some comments present in the original Google sheet have not been resolved and agreed yet]

To support gap analysis of optical pluggables in packet-over-optical networks, the Google Sheet referenced in {{google-sheet}} is utilized. The attributes listed in the sheet are systematically examined to determine their applicability to optical pluggables. For applicable attributes, a cross-check is performed to verify whether they are included in existing IETF data models. Attributes not present in the IETF models are identified as gaps. Where necessary, proposals for updates or modifications to the IETF models are developed to address these gaps or misalignments.

{: #gap-analysis-capabilities}
## List of Missing Optical Pluggable Capability Attributes Based on Gap Analysis

{{figure-gap-analysis-capabilities}} provides the missing capabilities attributes highlights important optical pluggable parameters and features that are defined by other standards development organizations (SDOs) and industry forums, but are currently absent from IETF YANG models. 

Note that the "Attribute Number" refers to numbering in Google Sheet.

Harmonizing these attributes between SDOs, and IETF models would support the evolution of open, programmable, and interoperable optical networks.

~~~~

For each Attribute Name, 
- First table displays the "Missing Capability Attributes" 
- Second table displays the "Summary Description of Missing  
  Capability Attributes"

| --------- | ------------------------------------------ | --------- |
| Attribute | Missing Capability Attributes              | source    |
| Number    |                                            |           |
| --------- | ------------------------------------------ | --------- |
| 4         | tag-id                                     | IETF      |
| 16        | Post FEC BER                               | oif       |
| 17        | pre-fec-ber                                |           |
| 18        | Target reach                               | oif/itu-t |
| 19        | Ripple                                     | oif/itu-t |
| 20        | max-bit-error-ratio                        | itu-t     |
| 22        | min-chromatic-dispersion                   | oif       |
| 36        | Polarization Rotation Speed                | oif/itu-t |
| 39        | min-tx-osnr                                | OpenConfg |
| 46        | pulse-shaping-type                         | OpenConfg |
| 53        | fec-coding                                 | OpenConfg |
| 68        | Minimum mean input power                   | itu-t     |
| 70        | Maximum mean total input power             | itu-t     |
| 71        | Maximum mean total output power            | itu-t     |
| 73        | Maximum channel power difference           | itu-t     |
| 79        | Minimum equivalent sensitivity             | itu-t     |
| 80        | Maximum reflectance of receiver            | itu-t     |
| 86        | max-laser-temperature                      | ietf      |
| 87        | grid-type                                  | OpenConfg |
|           |                                            | /tapi     |
| 88        | adjustment-granularity                     | OpenConfg |
|           |                                            | /tapi     |
| 91        | noise-figure                               | IETF/tapi |
| 92        | Maximum spectral excursion                 | itu-t     |
| 93        | Minimum side mode suppression ratio        | itu-t     |
| 95        | max-transmitter-residual-dispersion-osnr-  | itu-t     |
|           | penalty                                    |           |
| 107       | line-coding                                | itu-t     |
| 112       | max-central-wavelength-deviation           | itu-t     |
| 116       | max-duty-cycle                             | itu-t     |
| 117       | max-laser-linewidth                        | itu-t     |
| 121       | Maximum offset between the carrier and the | itu-t     |
|           | nominal central frequency                  |           |
| 123       | Maximum skew between the two polarizations | itu-t     |
| 125       | Maximum spectral power density             | itu-t     |
| 126       | Maximum TDECQ                              | itu-t     |
| 127       | Maximum I-Q offset                         | itu-t     |
| 157       | Laser frequency accuracy                   | oif       |
| 158       | Laser frequency noise                      | oif       |
| 159       | TX spectral Upper Mask & TX spectral Lower | oif       |
|           | Mask                                       |           |
| 160       | Laser RIN                                  | oif       |
| 161       | Tx clock phase noise (PN): Maximum PN mask | oif       |
|           | for low frequency PN                       |           |
| 162       | Tx clock phase noise (PN); Maximum total   | oif       |
|           | integrated RMS phase jitter between 10kHz  |           |
|           | and 10MHz                                  |           |
| 163       | Tx clock phase noise (PN)                  | oif       |
| 164       | Minimum Excess Bandwidth                   | oif       |
| 168       | Total output power with Tx disabled        | oif       |
| 169       | Total output power during wavelength       | oif       |
|           | switching                                  |           |
| 170       | Transmit output power stability            | oif       |
| 171       | Transmit output power control absolute     | oif       |
|           | accuracy                                   |           |
| 174       | Transmitter reflectance                    | oif       |
| 175       | Transmitter back reflection tolerance      | oif       |
| 176       | Transmitter polarization dependent power   | oif       |
| 177       | X-Y Skew                                   | oif       |
| 178       | DC I-Q offset (mean per polarization)      | oif       |
| 179       | I-Q instantaneous offset                   | oif       |
| 180       | Mean I-Q amplitude imbalance               | oif       |
| 181       | I-Q phase error                            | oif       |
| 182       | I-Q Skew                                   | oif       |
| 184       | Frequency offset between received carrier  | oif       |
|           | and LO                                     |           |
| 188       | Optical return loss                        | oif       |
| 195       | Tolerance to change in SOP                 | oif       |
| 196       | Optical input power transient tolerance    | oif       |
| 197       | Adjacent Channel Crosstalk OSNR Tolerance  | oif       |
|           | penalty                                    |           |
| 198       | Intra-Channel filtering penalty            | oif       |
| --------- | ------------------------------------------ | --------- |


| --------- | ------------------------------------------------------ |
| Attribute | Summary Description of                                 |
| Number    | Missing Capability Attributes                          |
| --------- | ------------------------------------------------------ |
| 4         | list of {tag-type, tag-value}                          |
| 16        | Refers to error rate measured after applying FEC       |
| 17        | Bit error rate measured before forward error           |
|           | correction decoding                                    |
| 18        | Max optical transmission distance that a coherent      |
|           | pluggable module can support                           |
| 19        | Peak-to-peak insertion loss difference within filter   |
|           | clear bandwidth of the Mux or Demux                    |
| 20        | Max acceptable bit error rate for a pluggable optical  |
|           | module                                                 |
| 22        | Min value of chromatic dispersion (CD) compensation    |
|           | range supported by an optical pluggable                |
| 36        | Max rate a coherent optical receiver can track and     |
|           | compensate for changes in polarization state of        |
|           | incoming optical signal                                |
| 39        | Min OSNR that the pluggable module's transmitter is    |
|           | capable of generating                                  |
| 46        | Digital filtering technique applied to electrical      |
|           | signal before it modulates optical carrier             |
| 53        | Forward error correction coding schema used in the     |
|           | transmission mode                                      |
| 68        | Min values of the average received power at point RS   |
| 70        | Highest allowable average power level that can be      |
|           | input into a system or component at a specified point  |
| 71        | Analogous to "Maximum mean total input power," but for |
|           | output direction                                       |
| 73        | max allowable difference in power levels between       |
|           | channels in a multi-channel optical transmission       |
| 79        | min optical power level that a receiver requires to    |
|           | decode incoming signals accurately                     |
| 80        | highest allowable level of optical reflectance from the|
|           | receiver within those components                       |
| 86        | highest laser temperature recorded or allowed for a    |
|           | laser                                                  |
| 87        | attribute that defines frequency grid used for optical |
|           | channels                                               |
| 88        | min spectrum separation between the central frequencies|
|           | of two adjacent optical channels                       |
| 91        | expressed as ratio of input SNR to output SNR.         |
|           | Quantifies how much noise a component adds to signal   |
| 92        | max acceptable difference between the nominal central  |
|           | frequency  and  signal power drops                     |
| 93        | A measure of how much the power of the main mode in a  |
|           | laser exceeds that of its side modes                   |
| 95        | An additional SNR penalty at lowest power with         |
|           | worst-case dispersion                                  |
| 107       | List of methods of encoding digital data into signal   |
|           | waveforms, ensuring proper timing and synchronization  |
| 112       | difference between the nominal central wavelength and  |
|           | the actual central wavelength                          |
| 116       | max percentage of time that a signal is in an active or|
|           | "ON" state within a given period                       |
| 117       | max allowable width of laser optical signal            |
| 121       | max allowed deviation between actual carrier frequency |
|           | of an optical signal and its nominal central frequency |
| 123       | max difference in timing or phase between signals      |
|           | transmitted on different polarizations                 |
| 125       | max allowable optical power per unit frequency or      |
|           | wavelength interval in a system                        |
| 126       | Transmitter Dispersion and Eye Closure Quaternary, a   |
|           | metric to evaluate performance of optical transmitters |
| 127       | max I-Q offset difference between in-phase (I) and     |
|           | quadrature (Q) of a modulated signal                   |
| 157       | max deviation of a laser's actual output frequency from|
|           | its nominal channel frequency                          |
| 158       | Describes the random fluctuations in the laser's output|
|           | frequency over time                                    |
| 159       | max allowable optical power limits at specific         |
|           | frequency offsets from the carrier wavelength          |
| 160       | Laser Relative Intensity Noise quantifies random       |
|           | fluctuations in laser’s optical power output           |
| 161       | refers to random fluctuations in the timing of the     |
|           | transmitted signal's clock                             |
| 162       | refers to the random fluctuations in timing of the     |
|           | transmitted signal's clock                             |
| 163       | refers to the random fluctuations in the timing of the |
|           | transmitted signal's clock                             |
| 164       | min spectral width beyond theoretical minimum required |
|           | by the signal's data rate                              |
| 168       | amount of optical power emitted by pluggable when      |
|           | transmitter is intentionally turned off                |
| 169       | optical power level of  pluggable transmitter during   |
|           | brief period when it is changing its output wavelength |
| 170       | ability of a transmitter to maintain a consistent      |
|           | optical output power level over time                   |
| 171       | how closely actual output power matches the desired or |
|           | configured output power level                          |
| 174       | amount of optical power reflected back from the        |
|           | transmitter into the optical fiber                     |
| 175       | Max amount of optical power reflected back towards     |
|           | transmitter without performance degradation            |
| 176       | variation in optical power emitted by a transmitter    |
|           | depending on the polarization state of the light       |
| 177       | timing skew between the X and Y polarization components|
|           | of an optical signal in a coherent system              |
| 178       | average DC offset In-phase (I) and Quadrature (Q)      |
|           | components of received signal for each polarization    |
| 179       | time-varying or dynamic offset between In-phase (I)    |
|           | and Quadrature (Q) components of received signal       |
| 180       | average difference in amplitude between In-phase (I)   |
|           | and Quadrature (Q) components of the received signal   |
| 181       | deviation from 90-degree phase relationship between    |
|           | In-phase (I) and Quadrature (Q) of received signal     |
| 182       | time delay or misalignment between In-phase (I) and    |
|           | Quadrature (Q) components of a signal                  |
| 184       | difference between frequency of incoming optical signal|
|           | and the local oscillator (LO) frequency                |
| 188       | total reflected light caused by discontinuities in an  |
|           | optical path, expressed as ratio of incident to        |
|           | reflected power                                        |
| 195       | ability of an optical receiver to maintain acceptable  |
|           | performance despite variations in State of Polarization|
|           | (SOP)                                                  |
| 196       | ability of an optical receiver to maintain acceptable  |
|           | performance when subjected to sudden changes in        |
|           | received optical power level                           |
| 197       | increase in required OSNR to maintain a specific BER   |
|           | due to interference caused by neighboring optical      |
|           | channels                                               |
| 198       | degradation in signal quality, measured as an increase |
|           | in required OSNR to achieve a target BER               |
| --------- | ------------------------------------------------------ |

Note: The "Attribute Number" refers to numbering in Google Sheet

~~~~
{: #figure-gap-analysis-capabilities title="List of Optical Pluggable Capability Attributes Based on Gap Analysis"}


{: #gap-analysis-config}
## List of Missing Optical Pluggable Configuration Attributes Based on Gap Analysis


{{figure-gap-analysis-Configuration}} identifies configuration attributes for optical pluggables defined by other standards development organizations (SDOs) and industry forums which may not be fully represented in IETF YANG models. 

Note that the "Attribute Number" refers to numbering in Google Sheet.

~~~~

For each Attribute Name, 
- First table displays the "Missing Configuration Attributes" 
- Second table displays the "Summary Description of Missing  
  Configuration Attributes"
  
| --------- | ------------------------------------------ | --------- |
| Attribute | Missing Configuration Attributes           | source    |
| Number    |                                            |           |
| --------- | ------------------------------------------ | --------- |
| 206       | admin-state                                |           |
| 210       | line-coding-bit-rate                       | tapi      |
| --------- | ------------------------------------------ | --------- |

| --------- | ------------------------------------------------------ |
| Attribute | Summary Description of                                 |
| Number    | Missing Configuration Attributes                       |
| --------- | ------------------------------------------------------ |
| 206       | This is pluggable admin state.                         |
| 210       | Identifies the line coding e.g. NRZ-10G and is drawn   |
|           | from G.698.2.                                          |
| --------- | ------------------------------------------------------ |

Note: The "Attribute Number" refers to numbering in Google Sheet

~~~~
{: #figure-gap-analysis-Configuration title="List of Optical Pluggable Configuration Attributes Based on Gap Analysis"}


{: #gap-analysis-pm}
## List of Missing Optical Pluggable PM/States Attributes Based on Gap Analysis

{{figure-gap-analysis-pm}} highlights missing Performance monitoring and States attributes for optical pluggables. Note that the "Attribute Number" refers to numbering in Google Sheet.

~~~~

For each Attribute Name, 
- First table displays the "Missing PM/States Attributes" 
- Second table displays the "Summary Description of Missing  
  PM/States Attributes"

| --------- | ------------------------------------------ | --------- |
| Attribute | Missing PM/States Attributes               | Source    |
| Number    |                                            |           |
| --------- | ------------------------------------------ | --------- |
| 216       | operational-state                          |           |
| 218       | central-frequency-offset                   | OpenConfg/|
|           |                                            | oif/t-api |
| 222       | chromatic-dispersion                       | OpenConfg/|
|           |                                            | oif/tapi  |
| 233       | supply-voltage                             | OpenConfg |
| 234       | laser-bias-current                         | OpenConfg |
| 235       | max-polarization-dependent-loss            | OpenConfg |
| 237       | modulation-error-ratio                     | OpenConfg |
| 238       | fec-uncorrectable-blocks                   | OpenConfg |
| 239       | q-value                                    | OpenConfg |
| 250       | EVMmax                                     | oif       |
| 251       | EVMrms                                     | oif       |
| 252       | MER                                        | oif       |
| 253       | eSNR                                       | OpenConfg/|
|           |                                            | oif       |
| 254       | SNR Margin                                 | oif       |
| 255       | CD-high granularity, short link            | oif       |
| 256       | CD-low granularity, long link              | oif       |
| 257       | DGD                                        | oif       |
| 258       | SOPMD                                      | OpenConfg/|
|           |                                            | oif       |
| 259       | PDL                                        | oif       |
| 260       | SOP ROC                                    | OpenConfg/|
|           |                                            | oif       |
| 261       | Tx Total Power                             | oif       |
| 264       | CFO                                        | oif       |
| 265       | Modulator Bias X/I                         | OpenConfg/|
|           |                                            | oif       |
| 266       | Modulator Bias X/Q                         | OpenConfg/|
|           |                                            | oif       |
| 267       | Modulator Bias Y/I                         | OpenConfg/|
|           |                                            | oif       |
| 268       | Modulator Bias Y/Q                         | OpenConfg/|
|           |                                            | oif       |
| 269       | Modulator Bias X Phase                     | OpenConfg/|
|           |                                            | oif       |
| 270       | Modulator Bias Y Phase                     | OpenConfg/|
|           |                                            | oif       |
| 271       | self-phase-modulation (SPM)                | itu-t     |
| 272       | cross-phase-modulation (XPM)               | itu-t     |
| 273       | Frequency offset between received carrier  | oif       |
|           | and LO                                     |           |
| 274       | total-channel-output-power                 | IETF      |
| --------- | ------------------------------------------ | --------- |

| --------- | ------------------------------------------------------ |
| Attribute | Summary Description of                                 |
| Number    | Missing PM/States Attributes                           |
| --------- | ------------------------------------------------------ |
| 216       | This is pluggable admin state.                         |
| 218       | Frequency difference between nominal and actual optical|
|           | carrier frequencies, causing phase rotation and        |
|           | requiring DSP compensation in coherent systems. It is  |
|           | a key parameter in OIF and T-API for channel alignment |
|           | and interoperability in DWDM networks.                 |
| 222       | Wavelength-dependent variation in light speed within an|
|           | optical fiber causing pulse broadening, expressed in   |
|           | ps/nm/km, and is a key factor limiting optical         |
|           | transmission performance as defined in ITU-T fiber     |
|           | standards                                              |
| 233       | Supply voltage to the transceiver in volts             |
| 234       | Current applied by the system to the transmit laser to |
|           | achieve the output power.                              |
| 235       | Maximum polarization-dependent-loss accumulated value, |
|           | supported by the optical channel associated to the     |
|           | associated transmission mode expressed in dB           |
| 237       | Modulation error ratio in dB with two decimal precision|
| 238       | Number of blocks or frames that were uncorrectable by  |
|           | the FEC                                                |
| 239       | Quality value (factor) in dB of a channel with two     |
|           | decimal precision.                                     |
| 250       | EVMmax (Error Vector Magnitude Mx) is a metric for     |
|           | evaluating maximum error vector magnitude in coherent  |
|           | optics, used for quality and impairment measurement in |
|           | coherent optical transceivers                          |
| 251       | Error Vector Magnitude normalized by RMS value of      |
|           | reference constellation points used to evaluate        |
|           | coherent optical signal quality                        |
| 252       | Modulation Error Ratio (MER) is a measure of how far   |
|           | received symbols deviate from their ideal constellation|
|           | position.                                              |
| 253       | Effective Signal-to-Noise Ratio, reflecting combined   |
|           | optical and electrical impairments.                    |
| 254       | The difference between the measured SNGR and the       |
|           | tolerable SNR that still allows acceptable BER and/or  |
|           | Q-factor.                                              |
| 255       | High-granularity chromatic dispersion measurement for  |
|           | short spans (media-side fiber estimate). DSP estimates |
|           | chromatic dispersion based on signal shape and         |
|           | compensation requirements.                             |
| 256       | Low-granularity chromatic dispersion measurement for   |
|           | longer spans (media-side fiber estimate). DSP estimates|
|           | chromatic dispersion based on signal shape and         |
|           | compensation requirements                              |
| 257       | Differential Group Delay - max delay between           |
|           | polarization modes. Transponder DSP measures           |
|           | Differential Group Delay as part of PMD compensation   |
| 258       | Second Order Polarization Mode Dispersion measured with|
|           | fine granularity                                       |
| 259       | Polarization Dependent Loss (affects coherent detection|
|           | DSP can estimate it dynamically                        |
| 260       | Rate of change of polarization state. Measured in      |
|           | real-time by tracking the speed of polarization state  |
|           | rotation at the Rx                                     |
| 261       | Total optical power emitted by the transmitter module, |
|           | critical for link budget and interoperability          |
| 264       | Central Frequency Offset is frequency mismatch between |
|           | transmitter and receiver oscillators causing phase     |
|           | errors and interference in coherent optical systems    |
| 265       | Bias on the in-phase (I) path of polarization X in a   |
|           | coherent optical modulator, expressed as a percentage  |
|           | with 2 decimal places, including statistical values    |
|           | (instant, avg, min, max)                               |
| 266       | Bias on the quadrature (Q) path of polarization X in a |
|           | coherent optical modulator, similarly expressed as a   |
|           | percentage with 2 decimal places, including the same   |
|           | set of statistical values (instant, avg, min, max)     |
| 267       | Bias on the in-phase (I) path of polarization Y in a   |
|           | coherent optical modulator, expressed as a percentage  |
|           | with 2 decimal places, including statistical values    |
|           | (instantaneous, average, min, max)                     |
| 268       | Bias on the quadrature (Q) path of polarization Y in a |
|           | coherent optical modulator, expressed as a percentage  |
|           | with 2 decimal places, including statistical values    |
|           | (instantaneous, average, min, max)                     |
| 269       | Bias on phase path of polarization X in a coherent     |
|           | optical modulator, expressed as a percentage with 2    |
|           | decimal places, including statistical values           |
|           | (instantaneous, average, min, max)                     |
| 270       | Bias on phase path of polarization Y in a coherent     |
|           | optical modulator, expressed as a percentage with 2    |
|           | decimal places, including statistical values           |
|           | (instantaneous, average, min, max)                     |
| 271       | A nonlinear optical effect where the phase of a light  |
|           | pulse is modulated by its own intensity due to the Kerr|
|           | effect, leading to a time-dependent phase shift and    |
|           | spectral broadening of the pulse as it propagates      |
|           | through an optical medium like a fiber                 |
| 272       | A nonlinear optical effect where the intensity of one  |
|           | light signal modulates the phase of another signal     |
|           | traveling through the same fiber, leading to inter-    |
|           | channel crosstalk and signal degradation in wavelength |
|           | division multiplexing (WDM) system                     |
| 273       | Estimated frequency offset is a key performance        |
|           | indicator that can be monitored to assess the health   |
|           | and stability of the link                              |
| 274       | The total output power of this interface               |
| --------- | ------------------------------------------------------ |

Note: The "Attribute Number" refers to numbering in Google Sheet

~~~~
{: #figure-gap-analysis-pm title="List of Optical Pluggable PM State Attributes Based on Gap Analysis"}


{: #gap-syntax}
## Coherent Pluggable Syntax Gaps

Addressing syntax gaps in coherent pluggable attributes is crucial for achieving consistent and interoperable management across different implementations. One key issue lies in establishing a standardized naming convention. There are some naming inconsistency on existing IETF drafts {{?I-D.ietf-ccamp-optical-impairment-topology-yang}}, {{?I-D.ietf-ccamp-rfc9093-bis}} and {{?I-D.ietf-ccamp-dwdm-if-param-yang}}. 

{{figure-gap-syntax}} shows a proposal for naming convention of optical pluggable attributes.  The current proposal, while illustrative, may need further refinement to ensure clarity and avoid ambiguity. Specifically, the prefixing of attributes with directions like "tx" or "rx" should be consistently applied to all relevant parameters to clearly identify the directionality of the signal. The example also shows the need to clearly define the value type associated with the attribute, such as min, max, current, or none, for a cohesive and standardized approach. Furthermore, the examples for attribute naming should be universally adopted to establish an attribute mapping that is aligned with IETF, improving the overall clarity and usability of the YANG models for managing coherent pluggables.

~~~~
Naming convention:
  direction [tx/rx/both/none]-
  [name of the attribute]-
  value [min / max / current / none]

Examples:
    for IETF attribute rx-channel-power-max, use
      rx-channel-power-max (no change)

    for ITU-T attribute "Min (residual) chromatic dispersion", use
       residual-chromatic-dispersion-min

    for IETF attribute "max-central-frequency", use
      central-frequency-max

    for IETF attribute "channel-output-power", use
       tx-channel-power
~~~~
{: #figure-gap-syntax title="Proposed naming convention for optical pluggable attribute names"}

{: #gap-analysis-next-steps}
## Next Steps on Optical Module Data Modeling Gap Analysis

Based on the results of the gap analysis, the next step will be to incorporate the identified pluggable attributes using one of the proposed approaches. It is important to note that this step represents the final phase of this draft, and its details will be provided in the next version of this draft.

* Augmentation of existing IETF YANG data model (e.g. augmentation of draft {{?I-D.ietf-ccamp-optical-impairment-topology-yang}})
* Extend the content of an existing IETF YANG model via "bis/update"

{: #plug-lcm}
# Optical pluggable modules Lifecycle Management

\[Editorial Note: it is under review.
It was agreed that this section is important. Having said that, there are a few potential solution to address this topic:

 * Keep it is this draft
* Talk to author of use-case draft to be included in that draft https://datatracker.ietf.org/doc/draft-ietf-ccamp-actn-poi-pluggable-usecases-gaps/
* Move it to other IETF draft]

This section discusses the complete lifecycle of an optical pluggable module as shown in {{figure-overview-lifecycle-pluggable}}. It includes discussion on the pre-purchase evaluation of pluggable modules through installation to the operation of a pluggable module in a live network.

Most of this lifecycle discussion applies to a majority of equipment types. Where the pluggable module is special, this is highlighted.

The figure below provides a high level flow. In a real environment, all stages will be running in parallel for various plug versions etc. and there may be feedback from any stage to a previous stage. For example, the research, evaluation and planning exercises are ongoing activities that continue as the network grows and changes and as new pluggable module type & versions are introduced by vendors and insight from deployment may feed back to the evaluation stage.

Throughout the lifecycle specific use cases and scenarios will be considered and applied. These will be developed during the early stages and applied in service design.

Note: The stages and the terminology used are not intended to reflect any specific operational practice. They are intended to be neutral with respect to any existing operator's processes, aligning with the essence of the processes.

~~~~
  Market research                   \
       |                            |
       v                            |
  Testing of pluggable module samples      | Refer to
       |                            | Section 9.1
       v                            |
  Trials & PoCs                     |
       |                            |
       v                            |
  Approve pluggable module type     /
       |                   ---------
       v                            \
  Service demand Analysis           |
       |                            |
       v                            | Refer to
  Network planning                  | Section 9.2
       |                            |
       v                            |
  Service type realization analysis |
       |                            |
       v                            |
  Purchase pluggable modules        /
       |                   ---------
       v                            \
  Optical infrastructure creation   |
       |                            |
       v                            |
  Service demand received           | Refer to
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
  Installation of pluggable modules etc.   |
       |                            | Refer to
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
{: #figure-overview-lifecycle-pluggable title="Lifecycle of a optical pluggable module"}


The following sub-sections discuss the overall flow of activities and then work through the lifecycle stages in some detail.

{: #approve-plug}
## Approving the pluggable module type and version

pluggable modules, like all equipment, are carefully chosen. A network operations company (the operator) will decide what pluggable modules to use in the network based upon research and an understanding of capabilities of the pluggable modules available in the marketplace. These capabilities will be considered against the specific applications, use cases and scenarios that are of relevance to the operator's business.

It is expected that these applications, use cases and scenarios will be developed through "Market research" and as pluggable modules etc. are assessed. The use cases and scenarios will be applied extensively in later stages.

The operator will acquire samples of each type & version of pluggable module of interest and probably test and then trial them. They will also probably carry out "type approval" considering each type&version of pluggable module for a particular set of applications (where those applications may be defined by the operator themselves or may be standardized definitions) etc. The full detail of the capability of each type & version of pluggable module is relevant at all of these stages (see {{express-capabilities}}). The capabilities are expected to be expressed in a Repository.

\[Editorial Note: As the main goal of this draft is to identify, we might want to move a portion of this section to an annex or separate draft].

{: #planning-network}
## Planning the network

Specific pluggable modules (type&version) will be purchased only after detailed planning of the network. To carry out this planning, full knowledge of each type&version of pluggable module will be required. The planning process will account for key pluggable module properties to explore viability and compatibility. The planning will use predictions of "service demand" (e.g., using a demand matrix) and hence infrastructure need to determine purchase volumes, phasing etc.

During the "Network planning" process different types of service relevant for the applications, use cases and scenarios (identified in {{approve-plug}}) will be explores and specific approaches to realizing each resulting type of service will be determined. This will result in design of specific "service realization" patterns and templates that will be used in later stages of the process. The approach to deploying each service type is defined for each operational context (application etc.)

As a result of the planning exercise, numbers of each pluggable module type&version required will be known and purchasing can be initiated. The purchased pluggable modules will be added to the inventory and spares holdings.

{: #service-demand}
## Dealing with service demand

The planning exercise leads to optical infrastructure requirements with some timetable for deployment. The "Optical infrastructure" is designed (using the patterns/templates designed in {{planning-network}}. The infrastructure will be deployed as appropriate based upon predicted and actual service demand etc.

When optical "services demand" is received, perhaps to provide underlay for the packet network or driven by a specific service contract, optical network analysis is carried out to evaluate how to efficiently and effectively achieve the specific service demanded. This analysis will consider the whole optical network including the plugs and ROADMs etc. In most cases this "Service design" will use patterns/templates constructed in {{planning-network}} in conjunction with relevant capability information for the pluggable module type&version.

Prior to progressing further it is important to note that pluggable modules are highly valuable, and correspondingly expensive. They are deployed in a controlled fashion. There are a range of policies for deployment of pluggable modules.

In some cases, at one extreme end of the range of policy choices, an operator may decide to fully populate a packet device with a selection of pluggable modules and may cable them to adjacent ROADMS. However, it is more likely that pluggable module deployment will be on a just-in-time basis, at the other end of the range of policy choices, so a pluggable module is not deployed (and hence is not cabled) until the solution to realization of the optical service has been determined.

Regardless of the deployment approach, the module capability will be accounted for in the optical network analysis activity. Where modules are present, the range of installed modules constrain the possible realizations, where pluggable module modules have not been deployed all approved pluggable module modules (type&version) could be considered during the analysis, although capability of the relevant packet devices to support specific pluggable module modules will also need to be considered, and this may eliminate some pluggable module modules. In addition, if there is some urgency, the availability of the type of pluggable modules to the installation engineer and/or in the local spares holding inventory may also be considered.

The optical design will be "validated" in terms of "viability" and compatibility prior to proceeding. This analysis takes into account the full definitions of the pluggable module type&versions of interest, where each is defined in a corresponding and referenced Repository.

{: #install-operate}
## Installing and operationalizing the pluggable module

Once the design is available, any necessary physical installation exercise (pluggable module installation, cabling etc.) is carried out, driven by "Work orders" that identify the type&version of pluggable module to instal etc.

On detection of the pluggable module instance, the control system will validate that the work order has been carried out correctly. To do this, the full type&version of the pluggable module is read and compared with the intent. Where there are discrepancies, either a work order is constructed to correct the installation error after the detected pluggable module type&version is evaluated for compatibility with the specific design. This evaluation is done using the Repository for that type&version. It is possible that the type&version may be acceptable although perhaps a little more expensive than the optimum choice etc.

Once the type&version of pluggable module has been confirmed, the cabling to the pluggable module will be validated and the service set up and validated. Depending upon the operator practices, there may be an extensive service test phase prior to handing over the service. The service may not be enabled immediately, but will be at some point after which the service will become operational.
From this point on, normal live service/equipment management/control will be active.

Beyond this point normal operational activities such as engineering works, restoration, upgrade, fault location etc. will be carried out. Clearly, there is also the reverse sequence which includes deactivating a service and removing the plug and there are also various edits and refinements that result from changes in demand and changes in understanding of the service needs etc. These steps have not been covered at this stage as the initial list above is sufficient to the develop a deep understanding of the control of the plugs. Further stages will be added in a future version of this document.

In addition, during transition towards a more automated future, there are processes related to discovery of existing network etc. In many of these processes the current state of the network is understood including the type&version of each pluggable module. Some degree of understanding of capability of pluggable modules (and any other equipment) is relevant.

{: #express-capabilities}
## Expressing capabilities

As highlighted above, prior to installation of an optical pluggable module in a device, various research, approval, planning and design activities must be carried out (as they would be for any hardware). All of these activities will require information on the capabilities of the pluggable module.

Detailed information on the capability of the pluggable module is required long before it is installed and operating. This points to the need for a model of capability (of a type of pluggable module) that is independent of the model of a running instance (and hence points to decoupling of the model of capability from the model of the operation of the pluggable module). This also suggest that discovery of capability detail from the pluggable module is not sufficient/appropriate for deployment (although it may be useful in a lab context).

A machine interpretable definition/specification for the pluggable module should be available (independent of the pluggable module instance) for each pluggable module type&version where the statement of type&version (complete type&version) used is to the degree sufficient to precisely identify the relevant (unique) definition/specification. The complete type&version may include hardware type&version, firmware type&version and software type&version details (where the firmware/software influences the operation/control of the pluggable module). This is essentially the type&version used when considering spares holding and like-for-like replacement in the field.

From this perspective, all that is required from a running pluggable module is to report the complete type&version detail so that this can be confirmed as the right type&version. The type&version can be used to reference the relevant unique specification.

It is important to clarify the definition of capability. In this document, the term capability means "A quality or facility that enables something to carry out some activity and/or take some role". In the context of an equipment, the term applies to its functional and physical properties.

Considering a pluggable module (as for many other equipments), this would include specification of capabilities such as:

- physical size, form factor and shape (the capability to fit in a particular type of location)
- connector type (the capability to physically interconnect with a compatible connector)
- bus architecture (the capability to communicate with a compatible component)
- optical termination characteristics (the functional capabilities emergent from the powered physical equipment, allowing interconnection with corresponding compatible functions)
- measurement opportunities (the functional capabilities to provide information to various control functions)

A capability statement may be a precise single value with no uncertainty, a range, a collection of related ranges and thresholds etc. Where some aspect has variability or is controllable, this is also required to be specified.

For an equipment to be understood and used by a control system, the detailed information on capabilities must be available in machine interpretable form (to the degree necessary for any particular function to be carried out). The machine interpretable statements may be in the form of software, but preferably should be in the form of data (information) that can be readily ingested by tooling and ideally in a standardized language.

Traditionally, the published statements of capability have been in somewhat ambiguous text that require interpretation and conversion into a machine interpretable form through a manual intermediate step (normally performed, with errors and performed many times for any particular device type etc.). It is suggested here that the best source of the machine interpretable data is the specifying authority (e.g., ITU-T for standard applications, the vendor for plug capabilities, an operator for non-standard applications).

# Appendix A - Coherent pluggable module Examples

Within this section, we present a few use-cases showcasing the practical application of the coherent pluggable repository.
In this section, we present several use cases that demonstrate the practical application of coherent pluggable life cycle management.

## Example-1: Coherent Pluggables Already Provisioned

The first example is illustrated in {{figure-optical-pluggable-repository-usage-1}}. This is a simple example where the packet over optical network has been already provisioned with both optical underlay and packet overlay services. The role of SDN controller is just to discover and manage the network. In other words, the SDN controller was not involved in various aspects of service provisioning and viability. The second example will come all these aspects in more detail.

~~~~

      <------------------ L3 service-1 ------------------->
       <------------------ TE-Tunnel-1 ------------------>
         <----------------- IP link-1 ----------------->
           <------------- L0 service-1 ------------->

   |------------|        |------------------|
   | Coherent   |        |                  |
   | Pluggable  |  <-->  |  SDN Controller  |
   | Repository |        |                  |
   |------------|        |------------------|
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
{: #figure-optical-pluggable-repository-usage-1 title="Coherent Pluggable Repository Example-1"}

In this example, all optical and IP/MPLS services had been already provisioned and deployed and the packet over optical network is fully functional.

Within packet devices R1 and R2, coherent pluggables p1 and p2, are installed, interfacing through ports port_a and port_b, respectively. Both coherent pluggables are provisioned for the following operational-mode (see section 3 YANG Model of {{?I-D.ietf-ccamp-optical-impairment-topology-yang}}):

- \[organization-identifier, operational-mode] = \[OIF, 0x3E]

A single photonic service is established between these pluggables and an IP link is mapped to this L0 photonic service. The overlay TE-Tunnel-1 and L3 service-1 had been also provisioned. The following steps outline the details of how this network is discovered and managed by SDN controllers (note that the SDN controller was not involved in provisioning):

- Packet devices (R1, R2), pluggables (p1, p2), and photonic devices (m1, m2, m3) are all discovered by SDN controllers.
- The SDN controller also discovers all underlay and overlay services, i.e., L0 service-1, IP link-1, TE-Tunnel-1 and L3 service-1.
- The SDN controller has the network inventory, including coherent pluggables p1 and p2. In particular for coherent pluggables, basic information such as pluggable type, vendor, manufacturer, serial number and software version will be provided by pluggables to SDN controller.
- The inventory of packet devices R1 and R2 contains the  configurations of pluggable attributes such as "configured operational-mode," "configured central frequency," and "configured output power".
- Specifically, using the basic information of pluggables p1 and p2 such as pluggable type, vendor, manufacturer, serial number and software version collected earlier from packet devices R1 and R2, the SDN controller can use the "Coherent Pluggable Repository," to access the entire information of both pluggables p1 and p2. This includes all supported operational-modes along with all attributes related to each supported operational-mode.
- The SDN controller can collect all PM telemetry data from the network (including pluggables).
- The SDN controller can collect all alarm notifications from the network (including pluggables).
- The SDN controller can further change, modify, optimize the network (if needed).

## Example-2: Coherent Pluggables Planning

The example in {{figure-optical-pluggable-repository-usage-2}} demonstrates the usage of the "Coherent Pluggable Repository" for entire lifecycle of photonic service from including service planning, viability, provisioning, collection of PM telemetry, collection of alarm notifications and optimization.

Note that the packet over optical network in {{figure-optical-pluggable-repository-usage-2}} is not created yet. The ports port_a and port_b of packet device R1 and R2 are empty and can accept coherent pluggables. In addition, ports port_a and port_b are not connected to the optical network yet, i.e., there is no connection between packet devices R1, R2 and optical network. The port_a and port_b of packet device R1 and R2 can be potentially connected to any photonic nodes m1, m2 or m3.

Operator's goal is to use the SDN controller to plan, provision and monitor an optimal IP link-2 between packet devices R1 and R2. Optionally they can also provision overlay TE-Tunnel-2 and L3 service-2. To achieve this, the SDN controller should first plan an optical service-2, perform the viability to make sure this photonic service is feasible, provision it and then map it to an IP link-2.

~~~~

      <------------------ L3 service-2 ------------------->
       <------------------ TE-Tunnel-2 ------------------>
         <----------------- IP link-2 ----------------->
           <------------- L0 service-2 ------------->

   |------------|        |------------------|
   | Coherent   |        |                  |
   | Pluggable  |  <-->  |  SDN Controller  |
   | Repository |        |                  |
   |------------|        |------------------|
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
{: #figure-optical-pluggable-repository-usage-2 title="Coherent Pluggable Repository Usage 2"}

Let's assume that the operator of this network has already purchased coherent pluggables from Vendor-X, which can support the following two operational-modes. Note that the detail information of these operational-modes including all optical and photonic attributes are already uploaded to "Coherent Pluggable Repository" by Vendor-X and OIF (see section 3 YANG Model of {{?I-D.ietf-ccamp-optical-impairment-topology-yang}}):

- \[organization-identifier, operational-mode] = \[OIF, 0x3E]
- \[organization-identifier, operational-mode] = \[Vendor-X, 0x22]

The following steps outline the details of how this network is planned, provisioned, discovered and managed by SDN controllers:

- At first, there are no coherent pluggables installed in the packet devices yet. There are also no connection between packet devices and optical network.
- All packet devices (R1, R2) and photonic devices (m1, m2, m3) are managed by the SDN controller.
- As a result, the SDN controller maintains an inventory of packet and photonic devices within the network (i.e., nodes R1, R2, m1, m2, m3).
- To create the IP link-2, the SDN controller should plan and then provision the optical service-2 between port_a and port_b.
- To this end, the SDN controller should first design an optical service and then performs the viability check to make sure the optical service is viable in this network.
- So, the SDN controller calculates the best optical path from port_a to port_b.
- Next, the SDN controller performs the viability on optical route to make sure the optical path is viable in the network.
- To do viability, the SDN controller checks all attributes of all operational-modes to find the most optimal operational-mode. To do this, the SDN controller connects to the "Coherent Pluggable Repository" and access all optical and photonic attributes of all operational-modes (such as chromatic dispersion, FEC, modulation, polarization mode dispersion etc.) and performs the viability.
- After performing the optical path calculation and optical viability, the SDN controller selects the best coherent pluggable to be installed on port_a and port_b and the best optical route from port_a to port_b.
- Upon completion of the photonic viability check, the SDN controller determines which photonic devices (m1, m2, m3) should be connected to ports port_a and port_b.
- The SDN controller informs the operator of the selected coherent pluggables for ports port_a and port_b and provides instructions on how to connect them to the respective photonic devices (m1, m2, m3).
- The operator installs the designated pluggables into ports port_a and port_b and connects them to the specified photonic devices.
- The SDN controller then manages the newly installed pluggables.
- As part of the photonic viability process, the SDN controller knows the specific attributes of the pluggables, including "configured operational mode," "configured central frequency," and "configured output power."
- As a result, the SDN controller configures these configurations to each pluggable on port_a and port_b
- The SDN controller should also configure optical nodes m1, m2, m3 with attributes such as output power.
- The SDN controller provisions the optical service_1 between two coherent pluggables on port_a and port_b.
- The SDN controller also provisions the IP link-2 between packet device R1 and R2.
- The SDN controller can collect all PM telemetry data from the network (including pluggables).
- The SDN controller can collect all alarm notifications from the network (including pluggables).
- The SDN controller can further change, modify, optimize the network (if needed).

{: #plug-vendor-specific-attributes}
# Appendix B - Support of Opaque Attributes

\[Editorial Note: This section in under review. The GihHub issue #14 addresses this].

In certain cases, a coherent pluggable may support attributes that are specific to a particular vendor. This draft refers to such attributes as "Opaque Attributes". Given that coherent pluggables encompass capability, configuration, and performance monitoring (PM)/state attributes, each category may contain opaque attributes. Consequently, the opaque attributes could include the following:

* Read-only opaque capability attributes
* Read-write opaque configuration attributes
* Read-only opaque PM/state attributes

As part of coherent pluggable work, we need to address this situation where a coherent pluggable contains some proprietary capability, configuration and PM/states attributes which are needed to be configured or accessed from coherent pluggables. In this situation we need to address how opaque attributes are treated by packet device host. This allows different coherent pluggables to be used in various multi-vendor hosts in plug-and-play fashion.

It is important to note that "opaque attributes" are not simply attributes that can be addressed through augmentation of the YANG data model. The reason for this is that the coherent pluggable is exposed to external systems via the host packet device northbound interface as shown in {{figure-details-packet-optical-device}}. If the host packet device does not recognize any of these "opaque attributes". it may prevent the discovery of the coherent pluggable.

When such opaque attributes exist, although the host packet device may not comprehend the semantics of these opaque attributes, it should function as a proxy and mediator between the coherent pluggable and the northbound SDN controller. Specifically, the host packet device should understand the syntax of the opaque attributes and facilitate communication between the coherent pluggable and the northbound SDN controller. To achieve plug-and-play functionality in a multi-vendor environment, the host packet device should be capable of supporting these opaque attributes. The rest of this section will provide details on how to achieve this.

Another consideration is the privacy of opaque attributes, i.e., there are situations where these attributes may be commercially sensitive. In these cases, it would be reasonable to assume that the opaque attributes are in encrypted format allowing them to be passed from coherent pluggable to northbound of the host without being observed or interpreted in any way by host.

To achieve this, the coherent pluggable YANG data model (the work done as part of this draft -  Google Sheet) should first be augmented with vendor proprietary capability, configuration or PM attributes. As noted above, it might be also necessary to define how these new attributes are mapped to the internal protocol between the host and the pluggable via CMIS protocol. A key consideration is that the host does not need to understand the semantics of these new attributes and may not even need to know their syntax.

There are multiple solutions to this problem which will be discussed below. To demonstrate these solutions, consider the host Vendor-X and pluggable Vendor-Y in {{figure-details-packet-optical-device}}. Let's assume:

* Vendor-Y has a new read-write proprietary configuration attributes "AA" which should be configured in pluggable (in addition to well-known attributes such as central-frequency, power and operational-mode). The value of attribute AA is 100 and its memory map in coherent pluggable is 0x1100.
* In addition, consider a new read-only proprietary capability attributes "CC" supported on pluggable in range of {CC-min, CC-max}={1.1,3.3}.

## Support of Opaque Capability Attributes

The coherent pluggable YANG data model is augmented with a list of new capability attributes. As demonstrated in {{solution-vs-cap-attributes}}, the YANG data model is augmented with the following information:

* ID of new capability proprietary attribute
* Name of new capability proprietary attribute
* Minimum value of new attribute
* Maximum value of new attribute

The {{solution-vs-cap-attributes}} shows an example of new capability attribute "CC" whose min and max values are 1.1 and 3.3, respectively.

~~~~
 +--ro opaque-capability-attribute-list* [cap-attribute-id]
     +--ro cap-attribute-id              uint32
     +--ro cap-attribute-name            string
     +--ro cap-min-value                 decimal64
     +--ro cap-max-value                 decimal64

<opaque-capability-attribute-list xmlns="urn:example:cc">
  <cap-attribute-id> 1 </cap-attribute-id >
  <cap-attribute-name> CC </cap-attribute-name>
  <cap-min-value> 1.1 </cap-min-value>
  <cap-max-value> 3.3 </cap-max-value>
</opaque-capability-attribute-list>
~~~~
{: #solution-vs-cap-attributes title="Support of Opaque Capability Attributes"}

## Support of Opaque Secret Capability Attributes

to be added

{: #opaque-config-solution-1}

## Support of Opaque Configuration Attributes (Solution-1)

To support the opaque configuration attributes, there are a few potential solutions which are discussed below. This approach is the simplest solution, as it requires no interpretation by the host platform. The coherent pluggable YANG data model is augmented with a list that directly maps the values of new configuration attributes to the corresponding memory-map locations on the pluggable device. In this solution, the memory-map locations must be known to the operator, potentially provided in the Coherent Pluggable Repository. The {{solution-1}} illustrates the coherent pluggable YANG data model, which has been augmented with the following information:

* ID of new proprietary configuration attribute
* Name of new proprietary configuration attribute
* Value of new proprietary attribute
* The memory map of new proprietary attribute (which is used in CMIS communication between host and pluggable)

For instance, consider a scenario where the operator intends to configure a new proprietary attribute, "AA," with a value of 100, and a memory-map location on the pluggable set to 0x1100. In this process, the host platform receives the attribute "AA" as defined in {{solution-1}}. The host platform then relays this information to the coherent pluggable via the CMIS protocol, without performing any interpretation. In other words, the host platform is not required to understand the syntax or semantics of these attributes; it functions merely as a conduit, transmitting the values from the NBI to the designated memory-map locations on the pluggable.

~~~~
 +--rw opaque-config-attribute-list* [conf-attribute-id]
     +--rw conf-attribute-id             uint32
     +--rw conf-attribute-name           string
     +--rw value                         decimal64
     +--rw memory-map                    decimal64

<opaque-config-attribute-list xmlns="urn:example:cc">
  <config-attribute-id> 1 </config-attribute-id >
  <config-attribute-name> AA </config-attribute-name>
  <value> 100 </value>
  <memory-map> 1100 </memory-map>
</opaque-config-attribute-list>
~~~~
{: #solution-1 title="Solution-1 for support of opaque config attributes"}

## Support of Opaque Configuration Attributes (Solution-2)

This approach is similar to {{solution-1}} but requires the host platform to implement lookup logic to determine the memory-map location on the pluggables. In this solution, the coherent pluggable YANG data model is augmented with the following new attributes, as shown in {{solution-2}}:

* ID of new proprietary configuration attribute
* Name of new proprietary configuration attribute
* Value of new proprietary attribute

The operator does not have visibility into the specific memory-map locations for these attributes on the coherent pluggable device. Instead, the memory-map for each new attribute is provided in the Coherent Pluggable Repository. In this scenario, the host platform must search the pluggable Repository to locate the corresponding memory-map location for each new attribute. These values are then communicated to the pluggable via the CMIS protocol for configuration. As in {{solution-1}}, the host platform does not need to understand the syntax or semantics of the new attributes; it only needs to search the pluggable Repository to identify the memory-map locations for the new attributes.

As illustrated in {{solution-2}}, the host platform receives the new attribute "AA" via its Northbound Interface (NBI), with a configuration value of 0x1100. The host then searches the coherent pluggable Repository to determine the memory-map location associated with this attribute and identifies it as 0x1100. Without interpreting the attribute's syntax or semantics, the host platform communicates this information to the coherent pluggable via the CMIS protocol. Essentially, the host platform functions as a proxy, transmitting the values from the NBI to the appropriate memory-map locations on the pluggable without needing to understand the meaning of the attributes.

~~~~
 +--rw opaque-config-attribute-list* [conf-attribute-id]
     +--rw conf-attribute-id             uint32
     +--rw conf-attribute-name           string
     +--rw value                         decimal64
     Note: The memory-map for each new attribute is provided in
           pluggable Repository.

<opaque-config-attribute-list xmlns="urn:example:cc">
  <config-attribute-id> 1 </config-attribute-id >
  <config-attribute-name> AA </config-attribute-name>
  <value> 1100 </value>
</opaque-config-attribute-list>

~~~~
{: #solution-2 title="Solution-2 for support of opaque config attributes"}

## Support of Opaque Configuration Attributes (Solution-3)

This solution represents an advanced approach when a new opaque configuration attribute is mapped to multiple memory-map locations on a pluggable device, or when multiple such attributes are mapped to a single memory-map location on pluggable. Similar to {{solution-2}}, the mapping between these new attributes and their corresponding memory-map locations should be detailed in the pluggable Repository. For each new opaque attribute, the host platform is required to perform a lookup in the pluggable Repository to identify the relevant memory-map locations. The platform then assembles the corresponding values, which are communicated to the pluggable device via the CMIS protocol.

Although this solution is included for completeness, it is not practical or desirable due to its complexity and the need for interpretation by the host software

## Support of Opaque Secret Configuration Attributes

There are situations where opaque configuration attributes are confidential, and the vendor wishes to conceal their meanings and values. When considering the interface from the pluggable device to the host via CMIS, it is crucial that the pluggable does not expose the meaning or value of these confidential attributes. Ideally, the pluggable device would encrypt the data. Within the context of CMIS, it may be sufficient to allocate an array of register locations to convey the property values. These registers would store an encrypted data blob for read-only properties and accept an encrypted blob for writable registers. The specific value might be set or read through different register positions on each read/write, depending on the encryption technique used.

It is important to note that since the pluggable device encrypts the data, mapping the data offers no additional benefit. The YANG model would simply convey the register values as requested. The properties are applied to the memory map in a manner that may appear disordered. The location values must always be read together and written as specified, potentially requiring multiple reads to retrieve all properties. This approach could be incorporated into the basic register-based option discussed in {{opaque-config-solution-1}}.

As an example, let's assume a vendor defines secret attribute "DD" for its coherent pluggable. Vendor first needs to augment IETF data model with a list of encrypted values and memory-maps shown in {{solution-4}}. This very similar to {{solution-1}} where essentially the host functions as a proxy, transmitting the values from the NBI to the appropriate memory-map locations on the pluggable without needing to understand the meaning and semantics of these attributes.

~~~~
 +--rw opaque-config-attribute-list* [conf-attribute-id]
     +--rw conf-attribute-id             uint32
     +--rw encrypted-attribute-name      string
     +--rw encrypted-attribute-value     string
     +--rw memory-map                    decimal64
~~~~
{: #solution-4 title="Solution-4 for support of opaque secret configuration attributes"}


{: #support-plug-vendor-pm}
## Support of Opaque Performance Monitoring Data

The host packet device is informed of the properties via YANG augments and appropriate mapping definitions. The mapping definitions tell the host that the related properties are related to performance monitoring data such that the host will periodically read the appropriate parts of the pluggable interface as for any other performance monitoring data. AS for all other performance monitoring data, the host does not need to understand the data. The client controller can carry out analysis or can propagate the measures transparently to some other controller etc.

# Appendix C - Coherent Pluggable Repository

\[Editor's note: Formerly Manifest. GitHub issue #15 covers this].

\[Editor's note: Based on CCAMP WG's suggestion, this section is moved to Appendix for now. It might be moved from this draft to an existing IETF draft or to a new draft. We need to align with draft https://datatracker.ietf.org/doc/draft-ietf-ccamp-actn-poi-pluggable-usecases-gaps/ as well]

Referring to {{plug-capabilities-attributes}}, the coherent pluggable capability attributes (i.e., supported-modes) are crucial aspects of coherent pluggables and should be easily accessible for various reasons and activities. Those might include:

- Network Engineers: Network engineers needs to know the capabilities and characteristics of any coherent pluggable whether the coherent pluggable is already deployed or will potentially be installed and deployed in their network
- SDN Controllers: The optical, packet or higher-layer SDN controllers need to have detailed knowledge of the coherent pluggables for various reasons such as network planning, viability assessment of the photonic services from plug-to-plug, configuration and performance monitoring collection, alarm notifications etc.
- Packet Device (e.g., Router): Optionally the host packet device need also access to coherent pluggable capabilities to provide details of coherent pluggables already installed in packet devices for example during the debugging and troubleshooting of pluggables.

To facilitate the utilization of coherent pluggable attributes, this draft introduces the concept of the "Coherent Pluggable Repository" The term serves as a comprehensive collection of information that is appropriately structured and interrelated, providing a detailed description of the capabilities of a pluggable device. In alternative terminology, the Coherent Pluggable Repository may also be referred to as a Specification, a Profile, or a Plug database, among other terms.

It should be noted that any equipment could have a repository describing its capabilities and it may be broken down into units that can be referenced and reused, i.e., the definition can be modular. To facilitate the stages, each vendor would be expected to provide this information for each pluggable type & version.

A pluggable type & version may offer a subset of standard capabilities. The subset is described by simply omitting definitions.

A pluggable type & version may offer a super-set. The super-set is detailed by adding definitions via "augmentation" to the set of standard definitions available for use in the Coherent Pluggable Repository. These capability augmentations relate to augmentations to the YANG model used at the interface to the host. Note that host has no need to understand the semantics of the augmented properties, but does need to know the mapping to the pluggable interface. This is discussed in more detail elsewhere in this document.

We should also consider the fact that some proprietary attributes and capabilities of the coherent pluggable might be commercially sensitive and hence confidential and a vendor might not want to provide it to publicly to everyone. In other words, some guidelines and restriction might be applicable to some portion of "Coherent Pluggable Repository". To provide more security, the access to the pluggable Repository could be restricted or password protected and potentially encrypted. It is also possible to provided restrict access to an operator or a team or group of people of an operator where there may also be a requirement for an NDA to enable access to the data. It is also possible that the encrypted section of the Repository might only be passed to a specific vendor control component (without being meaningfully observed by other control components from other vendors). The encrypted information may be passed via a special secure channel directly to a component authorized to decrypt the information into machine interpretable form and use it.

Considering the above, it appears reasonable that all pluggable capabilities whether they be proprietary or standard should be fully described in the Repository (considering that some portions of the Repository might have restrictions as previously described). This may be achieved by a reference to a standard that is itself fully defined in machine interpretable form. This approach would allow for a far more flexible and future-proofed control solution.

In summary, to facilitate easy access to coherent pluggable attributes, the details of coherent pluggable operational-modes are collected in a repository (access restriction might be applicable to some portions of this document), such as GitHub and SharePoint, called "Coherent Pluggable Repository". The Repository must be both human and machine-readable repository and can be read and interpreted easily by any SDN controller, operators, or other devices in the network. A Repository contains multiple records which are uniquely identified by tuple \[organization-identifier, operational-mode].

The Coherent Pluggable Repository contains four sections:

* Photonic/Optical capability section: This section contains all photonic/optical capabilities of the coherent pluggable and identifies all read-only attributes. It also allow augmentation of this section for vendor-specific attributes.


* Configuration attributes: This section contains all read-writer attributes which can be configured on coherent pluggable. It also allow augmentation of this section for vendor-specific configuration attributes.
* PM Collection style for monitored attributes: List of all read-only monitored attributes where the coherent pluggable can collect PM data. This section identifies if the collection of current, average, min and max values are possible.
* PM Threshold values: For all or a subset of read-only monitored attributes, this section contains the threshold settings for threshold crossing alerts (TCA) if applicable.

{{figure-optical-pluggable-repository}} illustrates the overall structure of the "Coherent Pluggable Repository". It contains several operational-mode records where each record includes all the capability attributes for tuple \[organization-identifier, operational-mode]. As discussed in {{plug-capabilities-attributes}}, "organization-identifier" refers to any authority that defines these attributes.

Each record in the coherent pluggable Repository is machine readable/interpretable and is uniquely identified by a tuple \[organization-identifier, operational-mode].

Using "Coherent Pluggable Repository", the format of all operational-modes are identical whether it is defined by for example ITU-T, OIF, OpenConfig, or defined by a vendor.

~~~~

   A record identified by
   tuple [organization-identifier, operational-mode]

  |--------------------------------------------------------|
  |                                                        |-|
  |  organization-identifier                               | |-|
  |  operational-mode                                      | | |
  |  version:                                              | | |
  |                                                        | | |
  |  Photonic/Optical capabilities attributes              | | |
  |  -----------------------------------------             | | |
  |  (i.e., Read-only attributes defined in                | | |
  |   operational-mode of this draft. For each attribute,  | | |
  |   min, max, default values might be available)         | | |
  |    - attribute A1                                      | | |
  |    - attribute A2                                      | | |
  |      ...                                               | | |
  |    - attribute An                                      | | |
  |    - List of vendor-specific capability attributes     | | |
  |      (augmented yang model)                            | | |
  |                                                        | | |
  |  Configuration attributes                              | | |
  |  --------------------------                            | | |
  |  ( The list of all read-write attributes where         | | |
  |   can be configured on coherent pluggables )           | | |
  |   are possible )                                       | | |
  |    - attribute C1                                      | | |
  |    - attribute C2                                      | | |
  |    ...                                                 | | |
  |    - attributeCWm                                      | | |
  |    - some vendor specific config attributes            | | |
  |      (augmented yang model)                            | | |
  |                                                        | | |
  |  Monitored attributes PM collection                    | | |
  |  ------------------------------------                  | | |
  |  (i.e., list of monitored attributes where             | | |
  |   coherent pluggable can collect PM data for           | | |
  |   current, average, min, max values)                   | | |
  |    - attribute M1                                      | | |
  |    - attribute M2                                      | | |
  |    ...                                                 | | |
  |    - attribute Mp                                      | | |
  |                                                        | | |
  |  Monitored attributes Threshold setting                | | |
  |  ---------------------------------------               | | |
  |  For all or some attribute M1,... Mp, define           | | |
  |    - threshold-for-warning-alert   (if applicable)     | | |
  |    - threshold-for-minor-alert     (if applicable)     | | |
  |    - threshold-for-major-alert     (if applicable)     | | |
  |    - threshold-for-critical-alert  (if applicable)     | | |
  |                                                        | | |
  |--------------------------------------------------------| | |
    |--------------------------------------------------------| |
      |--------------------------------------------------------|

 Coherent Pluggable Repository
   - Contains one or more operational-mode records
   - Each record for tuple [organization-identifier,operational-mode]
   - It is machine-readable/interpretable

~~~~
{: #figure-optical-pluggable-repository title="Coherent Pluggable Repository"}

Below are several examples that demonstrate the concept of the "Coherent Pluggable Repository." {{figure-optical-pluggable-repository-example_1}} illustrates the content of a Repository record for operational mode 0x3E, as defined by the OIF forum. This operational mode is widely recognized and supported by nearly all coherent pluggable devices. Detailed information regarding this operational mode can be found in {{SFF8024}}, Table 4-7.

~~~~
organization-identifier:  OIF
operational-mode: 0x3E
// Photonic/Optical capabilities attributes
list of attributes
      modulation: DP-16QAM
      bit-rate: 478.75 Gbps
      baud-rate: 59.84375 Gbd
      more attributes ...
// Configuration attributes
// Monitored attributes PM collection
// Monitored attributes Threshold setting
~~~~
{: #figure-optical-pluggable-repository-example_1 title="Coherent Pluggable repository Defined by OIF"}

{{figure-optical-pluggable-repository-example_2}} is anther repository record where the Vendor-X has defined the operational-mode 0x22. In this case, Vendor-X defines all the attributes related to this operational-mode, which might not be supported by other pluggable vendors.

~~~~
organization-identifier: Vendor-X
operational-mode: 0x22
// Photonic/Optical capabilities attributes
list of attributes
      modulation: 16-QAM
      bit-rate: 400 Gbps
      baud-rate: 56 GBd
      more attributes ...
// Configuration attributes
// Monitored attributes PM collection
// Monitored attributes Threshold setting
~~~~
{: #figure-optical-pluggable-repository-example_2 title="Coherent Pluggable repository Example-2"}

"{{figure-optical-pluggable-repository-example_3}}" presents an example where the Vendor-Y defined an operational-mode 0x22 as well. In this scenario, the organization associated with the pluggable module is Vendor-Y, which defined the same operational-mode 0x22 as "Vendor-X"

It is important to note that while the operational-modes in both {{figure-optical-pluggable-repository-example_2}} and {{figure-optical-pluggable-repository-example_3}} share the same values, they are defined by different vendors. Consequently, these operational-modes are not related and may differ significantly in their attributes. In other words, although the semantics of these modes are identical, their actual content might vary significantly. This is one of the reasons that any record in Coherent Pluggable Repository is uniquely identified by tuple \[organization-identifier, operational-mode].

~~~~
organization-identifier: Vendor-Y
operational-mode: 0x22
// Photonic/Optical capabilities attributes
type: NON-STANDARD
list of attributes
      modulation: QPSK
      bit-rate: 800 Gbps
      baud-rate: 96 GBd
      more attributes ...
// Configuration attributes
// Monitored attributes PM collection
// Monitored attributes Threshold setting
~~~~
{: #figure-optical-pluggable-repository-example_3 title="Coherent Pluggable repository Example-3"}

# Security Considerations

TODO Security

# IANA Considerations

This document has no IANA actions.

--- back

{:numbered="false"}

# Acknowledgments

TODO acknowledge.

module
