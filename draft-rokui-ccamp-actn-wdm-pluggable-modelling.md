---
title: "Data Modelling and Gap Analysis of Optical Pluggables in Packet Over Optical Network"
abbrev: "Modelling Optical Pluggables"
category: info

docname: draft-rokui-ccamp-actn-wdm-pluggable-modelling-02
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
  OIF-CMIS:
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

informative:

   ietf-impairment-yang:
     title: "A YANG Data Model for Optical Impairment-aware Topology"
     date: 2025-01-06 
     target: https://datatracker.ietf.org/doc/draft-ietf-ccamp-optical-impairment-topology-yang/

   ietf-layer0-yang:
     title: "Common YANG Data Types for Layer 0 Networks"
     date: 2025-01-26 
     target: https://datatracker.ietf.org/doc/draft-ietf-ccamp-rfc9093-bis/

   ietf-optical-interface-yang:
     title: "A YANG model to manage the optical interface parameters for an external transponder in a WDM network"
     date: 2025-01-06 
     target: https://datatracker.ietf.org/doc/draft-ietf-ccamp-dwdm-if-param-yang/

  

--- abstract

This draft outlines the modeling of optical pluggables within a host packet device in the context of a packet over optical network. The model encompasses all pertinent properties of the pluggable for various packet over optical use cases and is partitioned into three primary areas: the optical media side, the electrical plug to host interconnect, and the physical equipment of the pluggable.

Included in the model are representations of configuration, states, and telemetry data, as well as of profiles and coherent plug capabilities. Emphasizing the importance of considering both vendor-agnostic and vendor-specific attributes in modeling coherent pluggables.

Drawing from existing IETF models and potentially complementing that with input from other standard or industrial forum models (ITU-T, OpenConfig , ONF TAPI etc.) , this model offers enhanced uniform structuring and naming.

This draft introduces the concept of "Coherent Pluggable Manifest", where it represents the capabilities of pluggable, maintained in a repository. This document also covers gap analysis of current IETF drafts and other SDOs on coherent Pluggable attributes and provides the complete lifecycle of a coherent pluggable from operators' approval through viability assessment to deployment.

This document also covers an analysis of the gap between current IETF drafts and the corresponding works in other standards bodies and industry. The lifecycle of a coherent pluggable from operators' approval, viability assessment to deployment and monitoring is also covered.

--- middle

# Terminology

{::boilerplate bcp14-tagged}

The following terms abbreviations are used in this document:

- Optical Pluggable / Coherent Pluggable / Pluggable: A small form factor coherent optical module. This document uses these terms interchangeably

- O-PNC: The control functions specializing in management/control of optical and photonic functions (virtual or physical). See {{?RFC8453}}

- P-PNC: The control functions specializing in management/control of packet functions (virtual or physical). See {{?RFC8453}}

- CMIS: The Common Management Interface Specification is an OIF Implementation Agreement (IA) which provides a well-defined mechanism to initialize and manage optical (and copper) modules in a standard way, while still providing the capability to provide custom functionality. This commonality makes integration into different host platforms easier for both the host and module vendors.

- optical pluggable media side:

- optical pluggable host side:

- Monitored attributes: The Coherent Pluggable attributes which can be measured, monitored, estimated, or otherwise observed. The monitored attributes are the inputs to performance monitors which in turn provide real time samples, threshold crossing supervision, and sometimes sample statistics. 


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

- States and performance monitoring telemetry data: These read-only attributes will be generated by optical pluggables and represents various states and PM data of the optical pluggable such as channel input power, channel output power, central frequency, laser temperature, current OSNR, Link Up/Down State, Alarm State, Laser On/Off State etc. In most cases these attributes are changing with time and pluggable reports current, average, min and max values. It is also possible to apply thresholds on each of these attributes to support thershold crossing alert (TCA).

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

{{figure-details-packet-optical-device}} shows a host packet device from vendor X, which is connected to optical device, equipped with optical pluggables from vendor X and Y. This figure exposes the following internal and external interfaces:

A. This interface provides the control of host packet functions and optical functions. It provides these functions which can be decoupled such that there is no overlap between the optical and packet control functions.

B. The CMIS communication interface between host packet devices) and optical pluggables.

C. The data flow between the coherent pluggable and the packet data function through this interface. This is electrical interface between coherent pluggable and the host. {{building-blocks}} will discuss this in more details.

D. Optical fiber connecting the optical devices to optical pluggables. This carries the flow of photonic signal from the optical device to the coherent pluggables. {{building-blocks}} will discuss this in more details.

"The model presented in in {{data-model}} consolidates properties of coherent pluggable on interfaces (D) and (C) in {{figure-details-packet-optical-device}} where interface (D) provides the photonic/optical attributes and interface (C) provides the host/electrical attributes."

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
    (A) Packet device management interfaces 
              (e.g., YANG, NETCONF, gNMI, etc.)
    (B) CMIS interface between Optical pluggable and Host
    (C) Host side of coherent pluggable (towards the Host)
    (D) Media side of coherent pluggable 
              (towards Optical/Photonic network)

~~~~
{: #figure-details-packet-optical-device title="Packet device with optical pluggables"}



{: #building-blocks}

# Coherent Pluggable Functional Building Blocks 

The functional building blocks of the coherent pluggables of {{figure-details-packet-optical-device}} are shown in {{figure-optical-pluggable-building-blocks}} and has three major functions:

- Media side: This functional block represents all Photonic/Optical attributes of the coherent pluggables (interface (5) in {{figure-details-packet-optical-device}}). These attributes define the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc., which do not directly affect the behavior of the host packet device. Note that the goal of this draft is to eventually provide the YANG data model with these specific paramters which can be exposed in the model towards the controllers.

- Host side: This functional block represents all Host/Electrical attributes of the coherent pluggables (interface (4) in {{figure-details-packet-optical-device}}). These attributes defines the characteristics of interconnect between the host and the optical pluggable, such as lane count, FEC etc., which both the optical pluggable and the packet host should understand and act upon.

- Equipment attributes: These attributes represent all physical and functional aspects of the coherent pluggable such as plug type, software version, thermal characteristics, power consumption etc.

~~~~

  Coherent Pluggable
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
-----|         |  | Channels|  |  | | Channels|  | (OTSI)  |  | |(Rx)
 | | |---------|  |---------|  |  | |---------|  |---------|  | |
 | |                           |  |                           | |
 | |---------------------------|  |---------------------------| |
 |                                                              |
 |--------------------------------------------------------------|

~~~~
{: #figure-optical-pluggable-building-blocks title="Optical Pluggable Building Blocks"}

The following sections are describing the details of coherent pluggable functional blocks in more details.

## Optical Channel/OTSI

The media side of the coherent pluggable is further divided into two functional blocks; Optical Channel/OTSI and Media Logical Channels. The characterises of the Optical channel/OTSI are:

* This is the pluggable interfaces facing the optical network.

* Represents the digital wrapper that transports services over a wavelength

* Represents the wavelength and the coherent aspects of the signal modulated onto it baud-rate, bit-rate, modulation scheme, frequency, tx-power, etc.

* Optical signal FEC termination/source, FEC characteristic information – configuration, if possible, Pre-FEC BER, Post-FEC BER, fail/degrade thresholds, raw corrected/uncorrected counts

* Provides configuration of the signal and monitoring capabilities

* Provides monitoring capabilities in the Tx (toward fiber/medium) and Rx (from fiber/medium) directions, Total optical power, optical channel power, Coherent statistics

## Media Logical Channels

The characteristics of the Media Logical Channels are:

* Logical representation of the hierarchical view of the digital framing layers used for transport of services over the wavelength

* Provides access to information for configuration and monitoring characteristics. For example, for 400ZR/OpenZR+, it represents the 400ZR frame structure in which Ethernet services are mapped and for an OTN encapsulated signal, it represents the OTU, ODU, OPU frame structures, perhaps with a multi-layer multiplex structure, in which Ethernet and other types of services are mapped

## Host Logical Channels

The host side of the coherent pluggable is further divided into two functional blocks; Host Logical Channels and Electrical channels. The characteristics of the Host Logical Channels are:

* Logical representation of the hierarchical view of the digital framing layers for services carried on the electrical lanes of the device

* Provides information for configuration and monitoring characteristics of each service

* Represents each service carried over the media logical channel and optical interface/wavelength, e.g., 25GE, 50GE, 100GE, 200GE, 400GE, OTU4, OTUCn etc.

## Electrical Channels

The characteristics of the Electrical Channels are:

Note that the purpose of this section is to clarify the role of electrical channel in the coherent pluggable. This purpose of this draft is not to define the data model of the electrical channels.

* The host side lanes of the device forming the physical interface to the host platform data path device(s)

* Lanes grouped to support the type/format and bandwidth of the signal used for a service

* Provides information for configuration and monitoring characteristics of the signal for a service in the electrical domain, e.g., Interface-format, FEC, alarming thresholds, etc.

* Provides monitoring capabilities in the Tx (toward fiber) and Rx (from the fiber). 
 
## Equipment 

The "Equipment functional block" in {{figure-optical-pluggable-building-blocks}} represents the coherent pluggable itself and has the following characteristics:

* Provides manufacturer identification information for the device

* Advertises capabilities of the device including capabilities for the host/client side and the media/line side

* Provides monitoring capabilities of physical characteristics and health of the device, e.g., temperature, voltage, coherent transmitter/receiver characteristics

* Provides for configuration where applicable – e.g., of device environmental thresholds

* Supports device level capabilities such as firmware installation, restarts, etc.


{: #data-model}
# Optical Pluggables Data Modeling

The attributes of all functional building block of a coherent pluggable in {{figure-optical-pluggable-building-blocks}} will be exposed to external packet and optical controllers via host interface (1) shown in {{figure-details-packet-optical-device}}. To this end, we need to model the coherent pluggable building blocks described in {{building-blocks}}.

The data modeling of each functional blocks provides attributes in following areas:

* {{plug-capabilities-attributes}}: Coherent pluggable capability attributes (i.e., supported-modes)
* {{plug-config-attribute}}: Coherent pluggable configuration attributes
* {{plug-pm-definition}}: Coherent pluggable performance monitoring data (including State data)
* {{plug-threshold-definition}}: Coherent pluggable threshold definition
* {{plug-alarm-definition}}: Coherent pluggable alarm notifications
* {{plug-vendor-specific-attributes}}: Support of Opaque Attributes

{: #plug-capabilities-attributes}
## Coherent Pluggable Capability Attributes (aka, Supported-Modes)

Coherent pluggable have revolutionized optical networking by offering a powerful combination of high performance, flexibility, and ease of deployment. These modules support a broad range of capabilities, making them both efficient and versatile. Their extensive functional capabilities further enhance their effectiveness in diverse networking environments.

From a coherent pluggable data modeling perspective, a set of attributes is grouped together and represented by a single identifier known as the "Supported Mode." In essence, each supported mode encapsulates a combination of functional capabilities for coherent pluggables, such as modulation type, bit rate, baud rate, chromatic dispersion, polarization, FEC, and more. Some of these attributes may also include value ranges (e.g., minimum and maximum). A coherent pluggable can support multiple supported modes, each of which can be defined by one of the following methods:

* Method 1: Defined by a Standards Developing Organization (SDO) such as ITU-T
* Method 2: Defined by a forum such as Optical Internetworking Forum (OIF), a group of operators (OpenConfig) or by an individual vendor

These methods define a namespace for the authority that specified the particular supported mode, whether it be a standards body, an association, a group of operators, or an individual vendor. For example, the supported modes in method 1 are well-known capabilities established by standards bodies such as the ITU-T {{G.698.2}}. These modes are recognized and supported by coherent pluggables, routers, and SDN controllers. This draft also supports the work of other Standards Development Organizations (SDOs), forums, or individual vendors as their specifications become available. In contrast, the supported-modes in method 2 are capabilities specified by forums such as OIF {{OIF-400ZR}}, OpenConfig, or by individual vendors. These supported-modes might not be supported by all coherent-pluggables, routers or SDN controllers. In specific, the supported-modes defined by an individual vendor might be not be recognized and supported by any routers and SDN controllers.

It is important to note that, from a functional perspective of coherent pluggables, the authority that defined the supported modes is less critical than the specific attributes associated with each supported mode. The key consideration is the list of attributes defined by these supported modes.

As illustrated in {{figure-plug-supported-mode}}, this document utilizes a consistent data structure for defining supported modes, irrespective of the authority that specified them. It includes:

* supported-mode-id: Identification of the supported mode
* organization-id: This provides a name space for an authority who defines the supported-mode, i.e., the authority that defines the supported-mode, such as ITU-T, OIF, OpenConfig, or a vendor
* tags: Optional multiple tags that can be used for various purposes, mainly for future extensibility. For example, these tags can map the supported-mode to CMIS Media-ID (if they are not the same). Other potential uses of this tag are reserved for future developments.
* operational-mode: This is the main part of this document which contains a list of capability attributes supported by the coherent pluggable.

{{plug-manifest}} discusses the concept of the "coherent pluggable manifest", which is a repository for all supported-modes". It also outlines the benefit of such repository and various use-cases.
Some details of supported modes can be found in IETF draft {{Impairment}}.

~~~~ 

 |-----------------------------------------------------------------|
 |  supported-mode*    // list of supported-modes                  |
 |      supported-mode-id                                          |
 |      organization-id (e.g., ITU-T, OIF, OpenConfig or Vendor)   |
 |      tag* // Optional. It has various usage in future           |
 |      operational-mode                                           |
 |              capability-attribute-1                             |
 |              capability-attribute-2                             |
 |              ....                                               |
 |              capability-attribute-n                             |
 |-----------------------------------------------------------------|

~~~~
{: #figure-plug-supported-mode title="Data structure for Coherent pluggable supported-modes"}

As an example, the operational-mode 0x3E introduced by OIF contains the following read-only capability attributes. Notes that in general a coherent pluggable can support multiple operational modes.

~~~~
organization-id:  OIF 
operational-mode: 0x3E
      modulation: DP-16QAM
      bit-rate: 478.75 Gbps
      baud-rate: 59.84375 Gbd
      more attributes ...
~~~~


{: #plug-config-attribute}
## Coherent Pluggable Configurations Attributes

Referring to {{figure-plug-config-pm}}, the coherent pluggables support a set of read-write attributes which are configurable. Example of such configuration attributes are output power, central frequency and operational-mode. Note that as discussed in {{plug-capabilities-attributes}}, since a coherent pluggable may support multiple operational-modes, as part of these configuration attributes, operator should configure which of these operational-mode is desired and should be functional.

~~~~ 

 |-----------------------------------------------------------------|
 |  optical-channel  // OTSI channels                              |
 |      configuration // list of R/W plug configuration attributes |
 |           config-attribute-1                                    |
 |           config-attribute-2                                    |
 |           .....                                                 |
 |           config-attribute-m                                    |
 |      pm and states  // list of R/O pm and state attributes      |
 |                     // Note-1: Each pm-attribute might have     |
 |                     //         threshold definitions            |
 |                     // Note-2: For each monitored attributes,   |
 |                     //         one SCTP profile can be assigned |
 |           monitored-attribute-1                                 |
 |           monitored-attribute-2                                 |
 |           .....                                                 |
 |           monitored-attribute-p                                 |
 |-----------------------------------------------------------------|

~~~~
{: #figure-plug-config-pm title="Data structure for Coherent pluggable Configuration and PM Attributes"}

{: #plug-pm-definition}
## Coherent Pluggable Performance Monitoring Data 

{{figure-plug-config-pm}} shows the list of pluggable Performance Monitoring (PM) and state data, which are critical components in optical networks, enabling network engineers to ensure optimal performance, identify issues, and maintain network reliability. Operators monitor a range of attributes on both the optical/photonic and electrical sides of coherent pluggables, including channel input power, channel output power, central frequency, current Optical Signal-to-Noise Ratio (OSNR), Bit Error Rate (BER), chromatic dispersion, laser temperature, link status, and more. These parameters directly impact the quality and integrity of the transmitted data across both optical and electrical domains.

As coherent optical technology continues to gain traction, PM has evolved to include more advanced techniques, such as monitoring the quality of modulated signals and detecting impairments that could degrade performance over long distances. By leveraging these PM capabilities, engineers can ensure that the optical layer operates effectively, optimize the utilization of optical resources, and maintain high levels of service continuity and performance throughout the network.

It is important to note that the "monitored attributes" encompass parameters from the media side, host side, and hardware components of coherent pluggables.

Performance Monitoring (PM) data is generated for various "monitored attributes" by optical pluggables, representing a range of real-time metrics, including current, average, minimum, and maximum values, as well as counters and states. The PM data can be categorized as follows:

* Basic Monitoring PM data: The analogue values which provide the "current values" of a "monitored attributes" such as laser temperature, eSNR (Effective Signal-to-Noise Ratio) at media input, eSNR at host input, laser frequency error, and more.
* Advanced Monitoring PM data: The analogue values which provide the "current, average, minimum, and maximum values" of "monitored attributes" such as transmit signal power, Bit Error Rate (BER), chromatic dispersion, etc.
* Up Counters: The discrete counter values of "monitored attributes" that only increment, such as Bit Error Count, FEC (Forward Error Correction) Uncorrected Errors, Loss of Signal (LOS) count, Loss of Frame (LOF) count, and others. 
* Up/Down Counters: The discrete counter values of "monitored attributes" that can both incremented and decremented.
* Operational/Admin States: Represents the states of "monitored attributes" such as link up/down state, alarm state, laser on/off state, Automatic Power Control (APC) status, and more.

For "Up Counters" there might be two approaches:

* Continuous Increment: The counter value continuously increments without resetting upon read.
* Reset on Read: The counter value resets either on read or based on a predefined condition.

For "advanced monitoring performance management (PM) data", where current, average, minimum, and maximum values are provided by the coherent pluggable, a "windowing mechanism" is essential. Currently, this mechanism is implemented by the host platform, not the pluggable itself. For instance, the host platform utilizes the windowing mechanism to segment the PM data collected by the coherent pluggable. Within each window, the host calculates the minimum, maximum, and average values of the PM data, enabling a granular and time-specific analysis of the pluggable's performance.

A variety of performance monitoring metrics, including minimum, maximum, average, and instantaneous values, can be collected. These metrics offer a comprehensive view of performance fluctuations, allowing for precise monitoring and quicker response times to anomalies. Minimum and maximum values help identify the extremes of performance, while average values give a sense of typical performance levels. Instantaneous values, on the other hand, provide real-time insights, which are crucial for immediate issue detection and resolution. This multi-faceted approach ensures that network performance is consistently monitored and maintained at high standards.

{{plug-threshold-definition}} will discuss the collection type and how they are related to the above-mentioned PM data. It also covers the coherent pluggables support for threshold crossing alerts (TCA) for all or a subset of monitored attributes. 

{: #plug-threshold-definition}
## Coherent Pluggable Threshold Definition

As indicated in {{plug-pm-definition}}, coherent pluggables are capable of providing the threshold crossing alert (TCA) for all or subset of "monitored attributes". In this situation, the coherent pluggable raises an alert which informs the host about operationally undesired situations or about critical threshold crossings of monitored attributes. The coherent pluggable raises an alert by setting an associated Flag on pluggable memory-map that represents the alert.

As mentioned previously, the TCA might be supported for a subset of coherent pluggable monitored attributes. Since it is possible that the coherent pluggable has different capabilities to raise threshold for different monitored attributes, to provide a general solution for threshold definition on coherent pluggable monitored attributes, this draft introduces the concept of "Supported Collection and Threshold Profile (SCTP)" shown in {{figure-plug-threshold-definition}} which defines the configurable threshold values and collection types (i.e., the collection of current value, average value, min/max value are supported). The SCTP types will be used in list of coherent pluggables Sheet.

To define the warning, minor, major, critical threshold values for a coherent pluggable monitored attribute, operator should set upper and lower limits that delineate acceptable performance ranges. This ensures that any deviations can be quickly identified and addressed. A rolling window between min-time and max-time should be employed to dynamically adjust these thresholds based on recent data trends, providing a more accurate reflection of current network conditions. By continuously updating the thresholds, network performance can be maintained within optimal parameters, reducing the risk of undetected issues.

Note that sometimes these thresholds are configurable and sometime they are hard-coded. It is also possible that a vendor can support a sub-set and super-set of monitored attributes (for super-set they need to augment the yang model). 




~~~~
         Supported-Collection-and-Threshold-Profile (SCTP)
 |----------------------------------------------------------------|
 |   SCTP-Type-1:                                                 |
 |     Collection: current, average, min, max                     |
 |     Configured Threshold: warning, minor, major, critical      |
 |                                                                |
 |   SCTP-Type-2:                                                 |
 |     Collection: current                                        |
 |     Configured Threshold: warning, minor, major, critical      |
 |                                                                |
 |   SCTP-Type-3:                                                 |
 |     Collection: current, average, min, max                     |
 |   ...                                                          |
 |   SCTP-Type-n:                                                 |
 |----------------------------------------------------------------|
    // Note: These are just a few examples. More SCTP profile 
    //       can be defined
~~~~
{: #figure-plug-threshold-definition title="Coherent pluggable Collection and Threshold Profile Definition"}


{: #plug-alarm-definition}
## Coherent Pluggable Alarm Notifications

[Editor's note: To be added in a later release.]

The coherent pluggables might generate various alarm notifications due to the various reasons.

{: #plug-vendor-specific-attributes}
## Support of Opaque Attributes

[Editorial Note: This section in under Revision and Review.]

In certain cases, a coherent pluggable may support attributes that are specific to a particular vendor. This draft refers to such attributes as "Opaque Attributes". Given that coherent pluggables encompass capability, configuration, and performance monitoring (PM)/state attributes, each category may contain additional opaque attributes. Consequently, the opaque attributes could include the following:

* Read-only opaque capability attributes
* Read-write opaque configuration attributes
* Read-only opaque PM/state attributes

As part of coherent pluggable work, we need to address this situation where a coherent pluggable contains some proprietary capability, configuration and PM/states attributes which are needed to be configured or accessed from coherent pluggables. In this situation we need to address how these attributes are treated by packet device host. This allows different coherent pluggables to be used in various multi-vendor hosts in plug-and-play fashion.

When such opaque attributes exist, although the host packet device may not comprehend the semantics of these opaque attributes, it should function as a proxy and mediator between the coherent pluggable and the northbound SDN controller. Specifically, the host packet device should understand the syntax of the opaque attributes and facilitate communication between the coherent pluggable and the northbound SDN controller. To achieve plug-and-play functionality in a multi-vendor environment, the host packet device should be capable of supporting these opaque attributes. The rest of this section will provide details on how to achieve this.

Another consideration is the privacy of opaque attributes, i.e., there are situations where these attributes may be commercially sensitive. In these cases, it would be reasonable to assume that the opaque attributes are in encrypted format allowing them to be passed from coherent pluggable to northbound of the host without being observed or interpreted in any way by host. 

To achieve this, the coherent pluggable YANG data model (the work done as part of this draft -  Google Sheet) should first be augmented with vendor proprietary capability, configuration or PM attributes. As noted above, it might be also necessary to define how these new attributes are mapped to the internal protocol between the host and the pluggable via CMIS protocol. A key consideration is that the host does not need to understand the semantics of these new attributes and may not even need to know their syntax.



There are multiple solutions to this problem which will be discussed below. To demonstrate these solutions, consider the host Vendor-X and pluggable Vendor-Y in {{figure-details-packet-optical-device}}. Let's assume: 

* Vendor-Y has a new read-write proprietary configuration attributes "AA" which should be configured in pluggable (in addition to well-known attributes such as central-frequency, power and operational-mode). The value of attribute AA is 100 and its memory map in coherent pluggable is 0x1100. 
* In addition, consider a new read-only proprietary capability attributes "CC" supported on pluggable in range of {CC-min, CC-max}={1.1,3.3}.

### Vendor-Specific Capability Attributes

The coherent pluggable YANG data model is augmented with a list of new capability attributes. As demonstrated in {{solution-vs-cap-attributes}}, the YANG data model is augmented with the following information:

* ID of new capability proprietary attribute
* Name of new capability proprietary attribute
* Minimum value of new attribute
* Maximum value of new attribute

The {{solution-vs-cap-attributes}} shows an example of new capability attribute "CC" whose min and max values are 1.1 and 3.3, respectively.

~~~~ 
 +--ro vendor-specific-capability-attribute-list* [cap-attribute-id]
     +--ro cap-attribute-id              uint32
     +--ro cap-attribute-name            string
     +--ro cap-min-value                 decimal64
     +--ro cap-max-value                 decimal64

<vendor-specific-cap-attribute-list xmlns="urn:example:cc">
  <cap-attribute-id> 1 </cap-attribute-id >
  <cap-attribute-name> CC </cap-attribute-name>
  <cap-min-value> 1.1 </cap-min-value>
  <cap-max-value> 3.3 </cap-max-value>
</vendor-specific-cap-attribute-list>
~~~~
{: #solution-vs-cap-attributes title="Support of Vendor-Specific Capability Attributes"}

To support the vendor-specific configuration attributes, there are a few potential solutions which are discussed below.

{: #vendor-specfic-config-solution-1}

### Vendor-Specific Configuration Attributes (Solution-1)

This approach is the simplest solution, as it requires no interpretation by the host platform. The coherent pluggable YANG data model is augmented with a list that directly maps the values of new configuration attributes to the corresponding memory-map locations on the pluggable device. In this solution, the memory-map locations must be known to the operator, potentially provided in the Coherent Pluggable Manifest. The {{solution-1}} illustrates the coherent pluggable YANG data model, which has been augmented with the following information:

* ID of new proprietary configuration attribute
* Name of new proprietary configuration attribute
* Value of new proprietary attribute
* The memory map of new proprietary attribute (which is used in CMIS communication between host and pluggable)

For instance, consider a scenario where the operator intends to configure a new proprietary attribute, "AA," with a value of 100, and a memory-map location on the pluggable set to 0x1100. In this process, the host platform receives the attribute "AA" as defined in {{solution-1}}. The host platform then relays this information to the coherent pluggable via the CMIS protocol, without performing any interpretation. In other words, the host platform is not required to understand the syntax or semantics of these attributes; it functions merely as a conduit, transmitting the values from the NBI to the designated memory-map locations on the pluggable.

~~~~ 
 +--rw vendor-specific-config-attribute-list* [conf-attribute-id]
     +--rw conf-attribute-id             uint32
     +--rw conf-attribute-name           string
     +--rw value                         decimal64
     +--rw memory-map                    decimal64

<vendor-specific-config-attribute-list xmlns="urn:example:cc">
  <config-attribute-id> 1 </config-attribute-id >
  <config-attribute-name> AA </config-attribute-name>
  <value> 100 </value>
  <memory-map> 1100 </memory-map>
</vendor-specific-config-attribute-list>
~~~~
{: #solution-1 title="Solution-1 for support of vendor proprietary config attributes"}

### Vendor-Specific Configuration Attributes (Solution-2)

This approach is similar to {{solution-1}} but requires the host platform to implement lookup logic to determine the memory-map location on the pluggables. In this solution, the coherent pluggable YANG data model is augmented with the following new attributes, as shown in {{solution-2}}:

* ID of new proprietary configuration attribute
* Name of new proprietary configuration attribute
* Value of new proprietary attribute

The operator does not have visibility into the specific memory-map locations for these attributes on the coherent pluggable device. Instead, the memory-map for each new attribute is provided in the Coherent Pluggable Manifest. In this scenario, the host platform must search the pluggable manifest to locate the corresponding memory-map location for each new attribute. These values are then communicated to the pluggable via the CMIS protocol for configuration. As in {{solution-1}}, the host platform does not need to understand the syntax or semantics of the new attributes; it only needs to search the pluggable manifest to identify the memory-map locations for the new attributes.

As illustrated in {{solution-2}}, the host platform receives the new attribute "AA" via its Northbound Interface (NBI), with a configuration value of 0x1100. The host then searches the coherent pluggable manifest to determine the memory-map location associated with this attribute and identifies it as 0x1100. Without interpreting the attribute's syntax or semantics, the host platform communicates this information to the coherent pluggable via the CMIS protocol. Essentially, the host platform functions as a proxy, transmitting the values from the NBI to the appropriate memory-map locations on the pluggable without needing to understand the meaning of the attributes.

~~~~ 
 +--rw vendor-specific-config-attribute-list* [conf-attribute-id]
     +--rw conf-attribute-id             uint32
     +--rw conf-attribute-name           string
     +--rw value                         decimal64
     Note: The memory-map for each new attribute is provided in
           pluggable Manifest.

<vendor-specific-config-attribute-list xmlns="urn:example:cc">
  <config-attribute-id> 1 </config-attribute-id >
  <config-attribute-name> AA </config-attribute-name>
  <value> 100 </value>
</vendor-specific-config-attribute-list>

~~~~
{: #solution-2 title="Solution-2 for support of vendor proprietary config attributes"}

### Vendor-Specific Configuration Attributes (Solution-3)

This solution represents an advanced approach when a new vendor-specific proprietary configuration attribute is mapped to multiple memory-map locations on a pluggable device, or when multiple such attributes are mapped to a single memory-map location on pluggable. Similar to {{solution-2}}, the mapping between these new attributes and their corresponding memory-map locations should be detailed in the pluggable manifest. For each new vendor-specific attribute, the host platform is required to perform a lookup in the pluggable manifest to identify the relevant memory-map locations. The platform then assembles the corresponding values, which are communicated to the pluggable device via the CMIS protocol.

Although this solution is included for completeness, it is not practical or desirable due to its complexity and the need for interpretation by the host software

### Vendor-Specific Secret Capability Attributes

to be added

### Vendor-Specific Secret Configuration Attributes

There are situations where vendor-specific configuration attributes are confidential, and the vendor wishes to conceal their meanings and values. When considering the interface from the pluggable device to the host via CMIS, it is crucial that the pluggable does not expose the meaning or value of these confidential attributes. Ideally, the pluggable device would encrypt the data. Within the context of CMIS, it may be sufficient to allocate an array of register locations to convey the property values. These registers would store an encrypted data blob for read-only properties and accept an encrypted blob for writable registers. The specific value might be set or read through different register positions on each read/write, depending on the encryption technique used.

It is important to note that since the pluggable device encrypts the data, mapping the data offers no additional benefit. The YANG model would simply convey the register values as requested. The properties are applied to the memory map in a manner that may appear disordered. The location values must always be read together and written as specified, potentially requiring multiple reads to retrieve all properties. This approach could be incorporated into the basic register-based option discussed in {{vendor-specfic-config-solution-1}}.

As an example, let's assume a vendor defines secret attribute "DD" for its coherent plggable. Vendor first needs to augment IETF data model with a list of encrypted values and memory-maps shown in {{solution-4}}. This very similar to {{solution-1}} where essentially the host functions as a proxy, transmitting the values from the NBI to the appropriate memory-map locations on the pluggable without needing to understand the meaning and semantics of these attributes.

~~~~ 
 +--rw vendor-specific-config-attribute-list* [conf-attribute-id]
     +--rw conf-attribute-id             uint32
     +--rw encrypted-attribute-name      string
     +--rw encrypted-attribute-value     string
     +--rw memory-map                    decimal64
~~~~
{: #solution-4 title="Solution-4 for support of vendor secret attributes"}


{: #support-plug-vendor-pm}
### Support of Vendor-Specific Performance Monitoring Data

As with any vendor-specific/proprietary property, the additional support is defined in the manifest. The host is informed of the properties via YANG augments and appropriate mapping definitions. The mapping definitions tell the host that the related properties are related to performance monitoring data such that the host will periodically read the appropriate parts of the pluggable interface as for any other performance monitoring data. AS for all other performance monitoring data, the host does not need to understand the data. The client controller can carry out analysis or can propagate the measures transparently to some other controller etc.

{: #yang-model}
# Coherent Pluggables Yang Data Model

As discussed in the sections on capabilities, configuration, and performance monitoring in {{plug-capabilities-attributes}}, {{plug-config-attribute}}, and {{plug-pm-definition}}, the coherent pluggable module includes various read-only capability attributes, read-write configuration attributes, and read-only performance monitoring attributes. For a comprehensive list of these attributes, refer to the accompanying coherent pluggable Google Sheet (Q: how can we incorporate the Google Sheet?).

Considering the next step involves converting the Coherent Pluggable Google Sheet into the 'Coherent Pluggable YANG data model', this draft proposes utilizing the methodology outlined in {{plug-yang-method}} for each attribute within the Google Sheet. The primary objective of this approach is to categorize the attributes associated with coherent pluggables. These attributes may fall under supported capabilities, configuration, or performance monitoring (PM) attributes. Here are a few examples:

* The read-write attributes "channel-output-power" and "central-frequency" are supported attributes that can be configured, and the coherent pluggable can collect PM data and assign PM thresholds to them.
* The read-only attribute "chromatic-dispersion", which is solely part of the supported capabilities and PM attributes. This attribute cannot be configured on coherent pluggables.
* The read-only attribute "supply-voltage" could be considered, which is exclusively part of the PM attributes. It neither falls under supported capabilities nor is it a configurable attribute.

~~~~

// To convert the "Coherent Pluggable Google Sheet" to 
// "Coherent Pluggable Yang Data Model", apply the following 
// methodology to all attributes in "Coherent Pluggable Google Sheet" 

// Note: This example uses attribute "channel-output-power" just 
//       as an example.
//       This methodology provided is applicable to any attributes.

    channel-output-power{    
        is-capability-attributes = (TRUE or FALSE)
        {
          // if "TRUE", the following needed to be added
          ro min-channel-output-power = ...   
          ro max-channel-output-power = ...
          ro default-channel-output-power = ... 
        }

        is-configurable = (TRUE or FALSE)
        {
          // if "TRUE", this is R/W attribute
          rw channel-output-power = ...
        }

        is-monitorable = (TRUE or FALSE)
        {
          // if "TRUE", following PM data from pluggable might 
          // be available and can be read
          ro current-channel-output-power (if applicable)
          ro average-channel-output-power (if applicable)
          ro min-channel-output-power     (if applicable)
          ro max-channel-output-power     (if applicable)
        }

        is-threshold-available = (TRUE or FALSE)
        {
          // if "TRUE", following PM thresholds might be configurable
          rw threshold-for-warning-alert  (if applicable)
          rw threshold-for-minor-alert    (if applicable)
          rw threshold-for-major-alert    (if applicable)
          rw threshold-for-critical-alert (if applicable
        }
    }

~~~~
{: #plug-yang-method title="Coherent pluggable Data Yang Model"}


{: #pluggable-gap-analysis}
# Coherent Pluggable Data Modeling Gap Analysis 

This draft on "coherent pluggable data model and gap analysis" was initiated to examine existing IETF models related to pluggables for "completeness" to assess existing IETF properties/structures which are relevant to coherent pluggables and also to look for missing properties/structures. The goal of current work is to achieve best positioning of the IETF work with respect to the other related activities in the industry.

To carry out this ongoing examination, properties/structures from relevant external bodies are collected and compared with properties/structures present in IETF models related to coherent pluggables. Where properties/structures differ the differences are examined and justifications considered and justification provided for changes to the IETF models these are proposed.

The following items are identified as gap related to coherent pluggables:

* Syntax gaps: Naming inconsistency on existing IETF drafts {{ietf-impairment-yang}}, {{ietf-layer0-yang}} and {{ietf-optical-interface-yang}}. As an example, the capability attribute "max-channel-input-power" is also referred to as "rx-channel-power-max". We need to fix this. This draft proposes the following structure (note that there will be multiple valid proposals). 

~~~~
Naming convention:
  direction [tx/rx/both/none]-
  [name of the attribute]-
  value [min / max / current / none]

Examples:
    for IETF attribute rx-channel-power-max, use 
      rx-channel-power-max (no change)
    
    for ITU-T attribute "Minimum (residual) chromatic dispersion", use
       residual-chromatic-dispersion-min 

    for IETF attribute "max-central-frequency", use
      central-frequency-max 

    for IETF attribute "channel-output-power", use
       tx-channel-power
~~~~

* Semantic gaps: For a complete solution for coherent pluggable, the capabilities, configuration, PM attributes and PM thresholds supported by IETF coherent pluggable should be consistent with coherent pluggable attributes supported by {{OIF-CMIS}}. This needs fuhrer investigation.

* Statement of Capability: For any attribute defined in IETF drafts {{ietf-impairment-yang}}, {{ietf-layer0-yang}} and {{ietf-optical-interface-yang}} which is configurable or is measurable and threshold can be set, we need a capability statement.

* [Editor's note: More to be added .]


{: #plug-manifest}
# Coherent Pluggable Manifest

Referring to {{plug-capabilities-attributes}}, the coherent pluggable capability attributes (i.e., supported-modes) are crucial aspects of coherent pluggables and should be easily accessible for various reasons and activities. Those might include:

- Network Engineers: Network engineers needs to know the capabilities and characteristics of any coherent pluggable whether the coherent pluggable is already deployed or will potentially be installed and deployed in their network
- SDN Controllers: The optical, packet or higher-layer SDN controllers need to have detailed knowledge of the coherent pluggables for various reasons such as network planning, viability assessment of the photonic services from plug-to-plug, configuration and performance monitoring collection, alarm notifications etc.
- Packet Device (e.g., Router): Optionally the host packet device need also access to coherent pluggable capabilities to provide details of coherent pluggables already installed in packet devices for example during the debugging and troubleshooting of pluggables.

To facilitate the utilization of coherent pluggable attributes, this draft introduces the concept of the "Coherent Pluggable Manifest." The manifest serves as a comprehensive collection of information that is appropriately structured and interrelated, providing a detailed description of the capabilities of a pluggable device. In alternative terminology, the manifest may also be referred to as a Specification, a Profile, or a Plug database, among other terms.

It should be noted that any equipment could have a Manifest describing its capabilities and the Manifest may be broken down into units that can be referenced and reused, i.e., the definition can be modular. To facilitate the stages, each vendor would be expected to provide a Manifest for each pluggable type & version.

A pluggable type & version may offer a subset of standard capabilities. The subset is described by simply omitting definitions. 

A pluggable type & version may offer a super-set. The super-set is detailed by adding definitions via "augmentation" to the set of standard definitions available for use in the matiest. These capability augmentations relate to augmentations to the YANG model used at the interface to the host. Note that host has no need to understand the semantics of the augmented properties, but does need to know the mapping to the pluggable interface. This is discussed in more detail elsewhere in this document.

We should also consider the fact that some proprietary attributes and capabilities of the coherent pluggable might be commercially sensitive and hence confidential and a vendor might not want to provide it to publicly to everyone. In other words, some guidelines and restriction might be applicable to some portion of "Coherent Pluggable Manifest". To provide more security, the access to the pluggable manifest could be restricted or password protected and potentially encrypted. It is also possible to provided restrict access to an operator or a team or group of people of an operator where there may also be a requirement for an NDA to enable access to the data. It is also possible that the encrypted section of the Manifest might only be passed to a specific vendor control component (without being meaningfully observed by other control components from other vendors). The encrypted information may be passed via a special secure channel directly to a component authorized to decrypt the information into machine interpretable form and use it.

Considering the above, it appears reasonable that all pluggable capabilities whether they be proprietary or standard should be fully described in the Manifest (considering that some portions of the Manifest might have restrictions as previously described). This may be achieved by a reference to a standard that is itself fully defined in machine interpretable form. This approach would allow for a far more flexible and future-proofed control solution.

In summary, to facilitate easy access to coherent pluggable attributes, the details of coherent pluggable operational-modes are collected in a repository (access restriction might be applicable to some portions of this document), such as GitHub and SharePoint, called "Coherent Pluggable Manifest". The manifest must be both human and machine-readable repository and can be read and interpreted easily by any SDN controller, operators, or other devices in the network. A manifest contains multiple records which are uniquely identified by tuple [organization-id, operational-mode].

The manifest contains four sections:

* Photonic/Optical capability section: This section contains all photonic/optical capabilities of the coherent pluggable and identifies all read-only attributes. It also allow augmentation of this section for vendor-specific attributes.


* Configuration attributes: This section contains all read-writer attributes which can be configured on coherent pluggable. It also allow augmentation of this section for vendor-specific configuration attributes.
* PM Collection style for monitored attributes: List of all read-only monitored attributes where the coherent pluggable can collect PM data. This section identifies if the collection of current, average, min and max values are possible. 
* PM Threshold values: For all or a subset of read-only monitored attributes, this section contains the threshold settings for threshold crossing alerts (TCA) if applicable.

{{figure-optical-pluggable-manifest}} illustrates the overall structure of the "Coherent Pluggable Manifest". It contains several operational-mode records where each record includes all the capability attributes for tuple [organization-id, operational-mode]. As discussed in {{plug-capabilities-attributes}}, "organization-id" refers to any authority that defines these attributes such as ITU-T {{G.698.2}} or {{OIF-400ZR}}) or an individual vendor.

Each record in the coherent pluggable manifest is machine readable/interpretable and is uniquely identified by a tuple [organization-id, operational-mode].

Using "Coherent Pluggable Manifest", the format of all operational-modes are identical whether it is defined by for example ITU-T, OIF, OpenConfig, or defined by a vendor.

~~~~
 
   A record identified by 
   tuple [organization-id, operational-mode]
   
  |--------------------------------------------------------|
  |                                                        |-|
  |  organization-id:  (e.g., ITU-T, OIF or Vendor)        | |-|
  |  operational-mode: (described in this draft)           | | |
  |                    (see also Google Sheet)             | | |
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

 Coherent Pluggable Manifest
   - Contains one or more operational-mode records 
   - Each record for tuple [organization-id, operational-mode]
   - It is machine-readable/interpretable

~~~~
{: #figure-optical-pluggable-manifest title="Coherent Pluggable Manifest"}

Below are several examples that demonstrate the concept of the "Coherent Pluggable Manifest." {{figure-optical-pluggable-manifest-example_1}} illustrates the content of a manifest record for operational mode 0x3E, as defined by the OIF forum. This operational mode is widely recognized and supported by nearly all coherent pluggable devices. Detailed information regarding this operational mode can be found in {{SFF8024}}, Table 4-7.

~~~~
organization-id:  OIF 
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
{: #figure-optical-pluggable-manifest-example_1 title="Coherent Pluggable Manifest Defined by OIF"}

{{figure-optical-pluggable-manifest-example_2}} is anther manifest record where the Vendor-X has defined the operational-mode 0x22. In this case, Vendor-X defines all the attributes related to this operational-mode, which might not be supported by other pluggable vendors.

~~~~
organization: Vendor-X
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
{: #figure-optical-pluggable-manifest-example_2 title="Coherent Pluggable Manifest Example-2"}

"{{figure-optical-pluggable-manifest-example_3}}" presents an example where the Vendor-Y defined an operational-mode 0x22 as well. In this scenario, the organization associated with the pluggable module is Vendor-Y, which defined the same operational-mode 0x22 as "Vendor-X"

It is important to note that while the operational-modes in both {{figure-optical-pluggable-manifest-example_2}} and {{figure-optical-pluggable-manifest-example_3}} share the same values, they are defined by different vendors. Consequently, these operational-modes are not related and may differ significantly in their attributes. In other words, although the semantics of these modes are identical, their actual content might vary significantly. This is one of the reasons that any record in Coherent Pluggable Manifest is uniquely identified by tuple [organization-id, operational-mode].

~~~~
organization: Vendor-Y
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
  Testing of pluggable samples      | Refer to
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
       v                            | Refer to
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
  Installation of pluggables etc.   |
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

{: #architecture-implications}
# Implications for the Functional Control Architecture

[Editor's note: To be added in a later release.]

The following section considers the interaction sequence, resulting from the pluggable lifecycle analysis, within the functional control architecture and highlights resulting adjustments to the control functionality. Note that this section does not deal with the physical realization of the control components of the functional architecture other than those dependent on the device and pluggable physical boundaries.

{: #plug-manifest-usage}
# Usage of Coherent Pluggables Manifest

Within this section, we present a few use-cases showcasing the practical application of the coherent pluggable manifest.

## Example-1: Coherent Pluggables Manifest 

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

## Example-2: Coherent Pluggables Manifest

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
