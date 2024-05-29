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

--- abstract

This draft outlines a modeling approach of optical pluggables within a host packet device within the context of a packet over optical network. The model encompasses all pertinent properties of the pluggable for various packet over optical use cases and is partitioned into three primary areas: the optical media interface, the electrical plug to host interconnect, and the physical equipment of the pluggable.

Included in the model are representations of configuration, states, PM and telemetry data, as well as profiles and coherent plug capabilities. Emphasizing the importance of considering both vendor-agnostic and vendor-specific attributes in modeling coherent pluggables.

Drawing from existing models in IETF, OpenConfig, ITU-T, OIF, and TAPI, this model offers enhanced uniform structuring and naming. Additionally, it provides insight into the mapping to plug interface structures defined in CMIS.

--- middle

# Terminology

{::boilerplate bcp14-tagged}

The following terms abbreviations are used in this document:

- Optical Pluggable / Coherent Pluggable / Pluggable: A small form factor coherent optical module. This document uses these terms interchangeably

- O-PNC: The control functions specializing in management/control of optical and photonic devices (virtual or physical). See {{?RFC8453}}

- P-PNC: The control functions specializing in management/control of packet devices (virtual or physical). See {{?RFC8453}}

- CMIS: Content Management Interoperability Services developed by OIF is an open standard that allows different host systems to inter-operate with Optical Pluggables.

- xPonder: Short for Transponder and/or Muxponder

# Introduction

Packet traffic has been transmitted across optical networks for many years, leveraging the advantages of optical transmission and switching combined with packet switching. Packet systems featuring optical pluggables are used since many years but those pluggables were rarely connected to optical line systems. What's new is that DWDM capable pluggables (aka. coherent modules) can now be hosted directly by Packet switching devices but are connected to an actively managed DWDM line system. Traditionally, optical line systems DWDM pluggable devices have been controlled by O-PNCs while packet systems have been controlled by P-PNCs. The integration of DWDM interfaces into packet systems requires to reconsider the scope of O-PNC capabilities and necessitates a communication betweeen O/P-PNC controllers.

In numerous network setups, packet and optical line systems have been engineered, operated, and managed separately, leading to siloed operations that can be suboptimal and inefficient. The evolution of both packet and optical systems has largely been independent. Optical systems, and packet systems have seen advancements in capacity, especially with the adoption of coherent optical techniques.

Advancements in optical component design have led to increased density, enabling entire coherent optical terminal systems that previously required multiple circuit packs to now fit into a single small form factor "coherent pluggable." Integrating coherent pluggables into devices with packet functions can result in reduced network costs, power consumption, and footprint, while also enhancing data transfer rates, reducing latency, and expanding capacity, although in some cases, separate packet and optical solutions may still be preferred due to other engineering and deployment considerations.

These trends, coupled with the desire to utilize the best components available, have given rise to open optical pluggables. These pluggables adhere to optical interoperability standards allow a plugs of different vendors to operate across an  optical line system. Furthermore, CMIS standardization by OIF {{OIF-CMIS}} allows to install pluggables from any pluggable vendor in a device from any host. 

While standardized transmission modes like ZR can handle basic applications, proprietary modes from vendors could achieve better performance.

This draft outlines the modeling of an optical pluggable within a host in context of a packet over optical network. The model presented in this document consolidates various properties of optical pluggables into three key functional block:

- Photonic/Optical attributes: These attributes defines the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc.

- Host/Electrical attributes: These attributes defines the characteristics of interconnect between the host and the optical pluggable, such as lane count, FEC etc., which both the optical pluggable and the host must implement and act upon.

- Physical and functional aspects of the pluggable (i.e., equipment): This defines attributes of the optical pluggable itself, such as plug type, version, thermal characteristics, power consumption etc., which indirectly affect the host.

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

- {{plug-manifest-example}}: Utilization of Coherent Pluggables Manifest

- {{plug-lcm}}: Optical Pluggables Life Cycle Management

{: #optical-pluggable-in-device-packet-function}

# Optical Pluggable in a Device with Packet Functions

{{figure-details-packet-optical-device}} shows a packet device from vendor X, which is connected to optical device, equipped with optical pluggables from vendor X and Y. This figure exposes the following internal and external interfaces:

1. These interfaces provide the control of packet devices and optical devices. These functions are decoupled and appropriate interfaces need to be identified.
   (1a) The host controller controls all router components via proprietary internal management interfaces and providing all necessary data to the host controller to represent the host in YANG format to its PNC.
2. The optical controller has read/write access to the optical network

3. The CMIS (content management interoperability services) communication interface between hosts (e.g., packet devices) and optical pluggable inside the host. We only show the subset of DWDM optical pluggables of the host but recognize that non-DWDM pluggables are managed by the host via CMIS too.

4. The data flow between the coherent pluggable and the packet data function through this interface. This is electrical interface between coherent pluggable and the host. {{building-blocks}} will discuss this in more details.

5. Optical fiber connecting the optical devices to optical pluggables. This carries the flow of photonic signal from the optical device to the coherent pluggables. {{building-blocks}} will discuss this in more details.

This draft presents the DWDM-optical pluggable such as #1 and #2 in {{figure-details-packet-optical-device}} within a host packet device. The model presented in {{data-model}} consolidates properties of coherent pluggable on interfaces (4) and (5) where interface (5) provides the photonic/optical attributes and interface provides the host/electrical attributes.

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
   |            +---------------+          |                 |
   |           /|host controller|\         |                 |
   |          / +---------------+ \        |                 |
   |         /       (1a)          \       |                 |
   |        |                      |       |                 |
   |        |                      |       |                 | 
   |        v                      v       |                 |
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

The functional building blocks of the coherent pluggables of {{figure-details-packet-optical-device}} are shown in {{figure-optical-pluggable-building-blocks}} and has four major functions:

- Media side: This functional block represents all Photonic/Optical attributes of the coherent pluggables (interface (5) in {{figure-details-packet-optical-device}}). These attributes define the characteristics of the optical and photonic properties such as spectrum, polarization, dispersion etc., which do not directly affect the behavior of the host packet device.

- Host side: This functional block represents all Host/Electrical attributes of the coherent pluggables (interface (4) in {{figure-details-packet-optical-device}}). These attributes defines the characteristics of interconnect between the host and the optical pluggable, such as lane count, FEC etc., which both the optical pluggable and the packet host should understand and act upon.

- Equipment attributes: These attributes represent all physical and functional aspects of the coherent pluggable such as plug type, software version, thermal characteristics, power consumption etc.

- Performance related attributes and alarms: These attributes are related to performance parameters of the optical pluggable needed to operate the system. This includes PM counters, Thresholds, and telemetry data.

The following sections are describing the details of coherent pluggable functional blocks in more details.

## Optical Channel/OTSI

The media side of the coherent pluggable is further divided into two functional blocks; Optical Channel/OTSI and Media Logical Channels. The characterises of the Optical channel/OTSI are:

* This is the optical network facing interfaces

* Represents the wavelength and the coherent aspects of the signal modulated onto it baud-rate, modulation scheme, frequency, tx-power, etc.

* Provides monitoring capabilities in the Tx (toward fiber/medium) and Rx (from fiber/medium) directions, Total optical power, optical channel power, Coherent statistics

## Digital Channels

The characterises of the Digital Channels are:

* Logical representation of the hierarchical view of the digital framing layers used for transport of services over the wavelength

* Provides access to information for configuration and monitoring characteristics. For example for 400ZR/OpenZR+, it represents the 400ZR frame structure in which Ethernet services are mapped and for an OTN encapsulated signal, it represents the OTU, ODU, OPU frame structures, perhaps with a multi-layer multiplex structure, in which Ethernet and other types of services are mapped

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

## Ethernet Layer Interface
* Ethernet MAC and PHY layer and their mapping to electrical and logical channels.  
* provides Ethernet monitoring, alarming, PM, configuration, FEC (optional) etc.
  
## Pluggable 

The "Pluggable functional block" in {{figure-optical-pluggable-building-blocks}} represents the coherent pluggable itself and has the following characteristics:

* Provides manufacturer identification information for the device

* Advertises capabilities of the device including capabilities for the host/client interface and the media/line interface

* Provides monitoring capabilities of physical characteristics and health of the device, e.g., temperature, voltage, coherent transmitter/receiver characteristics

* Provides for configuration where applicable – e.g., of device environmental thresholds

* Supports device level capabilities such as firmware installation, restarts, etc.

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
 | |                       Pluggable                          | |
 | |----------------------------------------------------------| |
 |                                                              |
 |--------------------------------------------------------------|

~~~~
{: #figure-optical-pluggable-building-blocks title="Optical Pluggable Building Blocks"}


{: #data-model}
# Optical Pluggables Data Modeling

The attributes of all functional building block of a coherent pluggable in {{figure-optical-pluggable-building-blocks}} will be exposed to external controllers via the host interface (1) shown in {{figure-details-packet-optical-device}}. To this end, we need to model the coherent pluggable building blocks described in {{building-blocks}}.

The data modelling of each functional blocks provides attributes in these areas:

1. Coherent pluggable capabilities
2. Coherent pluggable configurations
3. Coherent pluggable states and performance monitoring data
4. Coherent pluggable threshold definition
5. Coherent pluggable alarm notifications
6. Coherent pluggable Ethernet/OTN capabilities
7. Coherent pluggable Ethernet/OTNconfigurations
8. Coherent pluggable Ethernet/OTNstates and performance monitoring data
9. Coherent pluggable Ethernet/OTNthreshold definition
10. Coherent pluggable Ethernet/OTNalarm notifications

{: #plug-capabilities-attributes}
## Coherent pluggable capabilities attributes

The capability attributes are read-only which defines the functional capabilities of the optical pluggables. These attributes are grouped together in a profile called "operational-mode" which contains attributes in all areas defined above.

The coherent pluggable capabilities are described by a set of operational-modes it supports, i.e., an optical pluggable might support multiple operational-modes, where each "operational-mode" can be defined by a standard body, operator, system vendor or module vendor. These operational-modes are called "standard-operational-modes" and "custom-operational-modes", respectively. The "standard-operational-modes" are well-define modes which are defined by a standard bodies such as ITU-T {{G.698.2}} whereas the ""custom-operational-modes" are defined by an organization and might not be supported by all pluggable implementations. 

{{plug-manifest}} discusses the concept of the "coherent pluggable manifest", which is a repository for all "standard-operational-modes" or "custom-operational-modes". It also outlines the benefit of such repository.

## Coherent pluggable configurations attributes

The coherent pluggables support a set of read-write attributes which are configurable as well as status control attributes.  Example of such configuration attributes are output power, central frequency and operational-mode or in case of status control admin-up/down. Note that since a coherent pluggable may support multiple operational-modes (standard or custom), the read-write operational-mode attribute programs the coherent pluggable to be functional in one of those operational-modes.

Refer to {{OIF-400ZR}}.

## Coherent pluggable states and performance monitoring data 

These read-only attributes will be generated by optical pluggables and represents various states and performance monitoring data of the optical pluggable such as channel input power, channel output power, central frequency, laser temperature, current OSNR etc. In most cases these attributers are temporal and coherent pluggable reports values such as instantaneous, min, max and average. A "supported threshold profile (STP) can be assigned to each performance monitoring data (see {{plug-threshold-definition}}). the presence of performance monitors needs to be provisioned.

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


To define the upper and lower thresholds for performance monitoring telemetry data, operator should set upper and lower limits that delineate acceptable performance ranges which can vary depending on which operational mode is chosen. This ensures that any deviations can be quickly identified and addressed. A rolling window between min-time and max-time should be employed to dynamically adjust these thresholds based on recent data trends, providing a more accurate reflection of current network conditions. By continuously updating the thresholds, network performance can be maintained within optimal parameters, reducing the risk of undetected issues.

A variety of performance monitoring metrics, including minimum, maximum, average, and instantaneous values, can be collected. These metrics offer a comprehensive view of performance fluctuations, allowing for precise monitoring and quicker response times to anomalies. Minimum and maximum values help identify the extremes of performance, while average values give a sense of typical performance levels. Instantaneous values, on the other hand, provide real-time insights, which are crucial for immediate issue detection and resolution. This multi-faceted approach ensures that network performance is consistently monitored and maintained at high standards.

For each performance monitoring state data, one STP should be assigned.

## Coherent plug alarm notifications

The coherent pluggables might generate various alarm notifications due to the various reasons. [Editor's note: More will be added.]

{: #yang-model}
# Optical Pluggables Yang Model

[Editor's note: This section will be addressed in second version of this document.]


{: #pluggable-gap-analysis}
# Coherent pluggable data modelling gap analysis 

[Editor's note: This section will be added.]

{: #plug-manifest}
# Coherent Pluggable Manifest

Referring to {{plug-capabilities-attributes}}, the coherent pluggable capability attributes are crucial aspects of pluggables and should be easily accessible for various activities, including:

- Network Engineers: When they need to know the capabilities and characteristics of any coherent pluggables.
- Optical Controllers: During the assessment of the viability of any photonic services.
- Optionally, Host Packet Devices: To provide details of coherent pluggables already installed in packet devices.
- more ...

To facilitate easy access to these attributes, the details of coherent pluggable operational-modes and host-operational-modes are collected in a public repository, such as GitHub or SharePoint, called the "Coherent Pluggable Manifest." This machine-readable repository can be read or interpreted easily by any SDN controller, operator, or other devices in the network.

{{figure-optical-pluggable-manifest}} illustrates the overall architecture of the Coherent Pluggable Manifest. It contains several "Operational-mode records" or "Host-operational-mode records," where each record includes all the capability attributes for a pair of [organization, operational-mode] or [organization, host-operational-mode]. The "organization" refers to any standardization body that defines standard operational-modes/host-operational-modes (such as ITU-T {{G.698.2}} or {{OIF-400ZR}}) or any vendor that defines custom operational-modes/host-operational-modes.

Each record in the coherent pluggable manifest is uniquely identified by a tuple [organization, operational-mode] or [organization, host-operational-mode].

~~~~

  Coherent Pluggable Manifest = 
          One or more Operational-mode records +
          One or more Host-0perational-mode records +

  Operational-mode records
  |--------------------------------------------|
  |   For each pair of                         |-|
  |     [organization, operational-mode]       | |-|
  |                                            | | |
  |  organization: X                           | | |
  |  operational-mode: Y                       | | |
  |  list of attributes:                       | | |
  |     attribute 1: ...                       | | |
  |     attribute 2: ...                       | | |
  |     ...                                    | | |
  |     attribute n: ...                       | | |
  |                                            | | |
  |--------------------------------------------| | |
    |--------------------------------------------| |
      |--------------------------------------------|

  Host-Operational-mode records
  |--------------------------------------------|
  |   For each pair of                         |-|
  |     [organization, host-operational-mode]  | |-|
  |                                            | | |
  |  organization: X                           | | |
  |  host-operational-mode: Z                  | | |
  |  list of attributes:                       | | |
  |     attribute 1: ...                       | | |
  |     attribute 2: ...                       | | |
  |     ...                                    | | |
  |     attribute m: ...                       | | |
  |                                            | | |
  |--------------------------------------------| | |
    |--------------------------------------------| |
      |--------------------------------------------|

~~~~
{: #figure-optical-pluggable-manifest title="Coherent Pluggable Manifest"}

With this approach, the utilization of both standard and custom modes is rendered uniform and shall be structured such that interoperable modes can easily be identified to limit the complexity of dealing with organization-specific codes. Note that all attributes pertaining to operational-modes and host-operational-modes are defined by this IETF document. To exemplify, {{figure-optical-pluggable-manifest-example_1}} illustrates an instance of standard operational-mode 0x3E and host-operational-mode 0x11 as defined by OIF. In this scenario, the associated organization is the OIF.

~~~~
Organization: OIF (see SFF 8024 Table 4-7 SMF media interface IDs)
Operational-mode: 0x3E
list of attributes
      modulation: DP-16QAM
      bit-rate: 478.75 Gb/s
      baud-rate: 59.84375
      lane signaling rate: 59.84375 GBd
      more ...

organization: OIF (see SFF 8024 Table 4-5 Host Electrical Interface IDs)
host-operational-mode: 0x11
list of attributes
      number of line: 8
      modulation: PAM4
      application-bit-rate: 425.00 Gb/s
      lane signaling rate: 26.5625 GBd
      more ...
~~~~
{: #figure-optical-pluggable-manifest-example_1 title="Coherent Pluggable Manifest Example-1"}

{{figure-optical-pluggable-manifest-example_2}} is an example where vendor "Vendor-X" has a coherent pluggable with custom defined operational-mode and host-operational-mode 0x22 and 0x33, respectively. In this case the organization is "Vendor-x". 

~~~~

organization: Vendor-X
operational-mode: 0x22
list of attributes
      modulation: ...
      bit-rate: ...
      baud-rate: ...
      more ...

organization: Vendor-X
host-operational-mode: 0x33
list of attributes
      number of line: ...
      modulation: ...
      application-bit-rate: ...
      more ...
~~~~
{: #figure-optical-pluggable-manifest-example_2 title="Coherent Pluggable Manifest Example-2"}

"{{figure-optical-pluggable-manifest-example_3}}" presents an example where the vendor "Vendor-Y" has a coherent pluggable module with custom-defined operational-mode and host-operational-mode values of 0x22 and 0x44, respectively. In this scenario, the organization associated with the pluggable module is "Vendor-Y."

It is important to note that while the operational-modes in both {{figure-optical-pluggable-manifest-example_2}} and {{figure-optical-pluggable-manifest-example_3}} share the same values, they are defined by different organizations. These operational-modes may or may-not differ significantly in their implementation. In other words, although the semantics of these modes are identical, their actual content might vary.

~~~~

organization: Vendor-Y
operational-mode: 0x22
list of attributes
      modulation: ...
      bit-rate: ...
      baud-rate: ...
      more ...

organization: Vendor-Y
host-operational-mode: 0x44
list of attributes
      number of line: ...
      modulation: ...
      application-bit-rate: ...
      more ...
~~~~
{: #figure-optical-pluggable-manifest-example_3 title="Coherent Pluggable Manifest Example-3"}

In essence, leveraging the coherent pluggable manifest facilitates uniform utilization of both standard and vendor-defined operational-modes and host-operational-modes and their compatibility. The introduction of the "Coherent pluggable manifest" concept substantially streamlines the definition and application of these modes, encompassing both standard and vendor-specific modes.

{: #plug-manifest-example}
# Utilization of Coherent Pluggables Manifest

Within this section, we present a few examples showcasing the practical application of the coherent pluggable manifest.

{{figure-optical-pluggable-manifest-usage-1}}" illustrates a packet over optical network. Within packet devices R1 and R2, coherent pluggables p1 and p2, are installed, interfacing through ports port_a and port_b, respectively. "m" photonic services is established between these pluggables. As a result of configuring these photonic services, coherent pluggables p1 and p2 are configured with following modes. 

- pluggable p1: "operational-mode" [OIF, 0x3E] and "host-operational-mode" [OIF, 0x11]
- pluggable p2: "operational-mode" [Vendor_Z, 0x33] and "host-operational-mode" [Vendor_Z, 0x44]

This means that during the optical viability for each of "m" photonic services, the SDN controller utilized the "Coherent Pluggable Manifest" to determine the selection of these specific pluggables and their respective modes for optimal performance. The following steps outline the details of how this network is managed by SDN controllers,


- Packet devices (R1, R2), pluggables (p1, p2), and photonic devices (m1, m2, m3) are under the management of SDN controllers
- The SDN controller has comprehensive knowledge of the network inventory, encompassing coherent pluggables p1 and p2
- Specifically, leveraging the "Coherent Pluggable Manifest," the P-PNC is equipped with detailed information regarding the inventories of pluggables p1 and p2. This includes data such as pluggable type, manufacturer, serial number, software version, as well as all operational modes and host operational modes supported by them.
- The inventory of packet devices R1 and R2 incorporates configurations pertaining to pluggable attributes, such as "configured operational mode," "configured central frequency," and "configured output power"
- During the viability of "m" optical services, the O-PNC communicates with the P-PNC to obtain the "coherent pluggable manifest" to get the comprehensive list of attributes supported by pluggables p1 and p2. This encompasses all attributes associated with each operational-mode and host-operational-mode supported by the pluggables. Operators can also access these attributes to obtain a complete overview of network devices across the entire packet optical network, including optical pluggables.

~~~~

            <------- L0 photonic service_1 ------->                 
            <------- L0 photonic service_2 ------->  
                          ........               
            <------- L0 photonic service_m ------->    
           
   |----------|        |------------------|
   | Coherent |        |                  |
   | Pluggable|  <-->  |        P-PNC     |
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

Another usage of the "Coherent Pluggable Manifest" is depicted in {{figure-optical-pluggable-manifest-usage-2}}". The following steps outline the details of how this network is managed:

- Currently, there are no coherent pluggables installed in the network.
- The ports port_a and port_b on packet devices R1 and R2 are unpopulated and do not have coherent pluggables installed. Once the photonic viability check is completed, the SDN controller will select and configure the appropriate pluggables for each port.
- The ports port_a and port_b on packet devices R1 and R2 are not yet connected to photonic nodes m1, m2, and m3. Following the photonic viability check, the O-PNC will determine the optimal connections between the router ports and the photonic nodes. At that point, the operator can proceed to connect the router ports to the specified photonic nodes.
- All packet devices (R1, R2) and photonic devices (m1, m2, m3) are managed by P-PNC.
- The orchestrator maintains a comprehensive inventory of packet and photonic devices within the network.
- With access to the "Coherent Pluggable Manifest," the Orchestrator has detailed knowledge of all potential coherent pluggables available for network deployment.
- The operator has decided to establish a new photonic service_1 between packet devices R1 and R2.
- The Orchstrator with help from O-PNC and P-PNC calculates the optimal route for photonic service_1 between R1 and R2.
- The O-PNC initiates the photonic viability check and utilizes the "Coherent Pluggable Manifest" to select suitable coherent pluggables that meet the required viability criteria for ports port_a and port_b.
- Upon completing the photonic viability check, the O-PNC determines which photonic devices (m1, m2, m3) should be connected to ports port_a and port_b on the packet devices.
- The O-PNC informs the operator of the selected coherent pluggables for ports port_a and port_b and provides instructions on how to connect them to the respective photonic devices (m1, m2, m3).
- The operator installs the designated pluggables into ports port_a and port_b and connects them to the specified photonic devices.
- The P-PNC then manages the newly installed pluggables.
- As part of the photonic viability process, the O-PNC knows the specific attributes of the pluggables, including "configured operational mode," "configured central frequency," and "configured output power."
- The P-PNC applies these configurations to each pluggable on port_a and port_b
- The photonic service_1 will be established. The P-PNC manages the photonic service_1.

~~~~

            <------- L0 photonic service_1 ------->                    
           
   |----------|        |------------------|
   | Coherent |        |                  |
   | Pluggable|  <-->  |      P-PNC       |
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
    service_1   L0 service which does not exist in the network
                and will be created
~~~~
{: #figure-optical-pluggable-manifest-usage-2 title="Coherent Pluggable Manifest Usage 2"}


{: #plug-lcm}
# Optical Pluggables Life Cycle Management

[Editor's note: Some of the material in this section may be better places in earlier sections, in some cases there should be references to earlier sections and some text has implications on earlier sections. This will be dealt with in the second version of this document.]

This section discusses the complete lifecycle of an optical pluggable. It includes discussion on the pre-purchase evaluation of pluggables through installation to the operation of a pluggable in a live network. 

Some of the terminology is local to this document. where this is the case the terms are clarified in the definitions section.

## Deployment of an optical pluggable in context

In case it is planned to connect to an opticalline system, prior to installation of a DWDM optical pluggable in a packet device, various research, approval, planning, design and viability activities must have been carried out. All of these activities will require detailed information on the capabilities of the pluggable. This points to the need for a strong separation between the model of operation of the pluggable and the model of capability (as detailed information on the capability of the pluggable is required long before it is installed and operational). 

Following sub-sections discuss the overall flow of activities and then work through the lifecycle stages in some detail.

## Capabilities of a pluggable

Prior to discussion on lifecycle, it is important to clarify the definition of capability. In this document, the term capability means "A quality or facility that enables something to carry out some activity and/or take some role". In the context of an equipment, the term applies to its functional and physical properties.

Considering a pluggable (as for many other equipments), this would include specification of:

- physical size
- connector type
- bus architecture
- optical termination characteristics
- measurement opportunities

The capability may be a precise statement with no uncertainty or a range. Where some aspect has variability or is controllable, this is also required to be specified.

For an equipment to be understood and used by a control system, the detailed information on capabilities must be in machine interpretable statements (to the degree necessary for any particular function to be carried out). These machine interpretable statements may be in the form of software, but preferably should be in the form of data (information) and ideally in a standardised language.

In this document, the term Manifest is used for the collection of information, appropriately structured and interrelated, that describes the capabilities of a pluggable. In other terminology spaces the Manifest may be considered to be a Specification, a profile, etc.

It should be noted that any equipment could have a Manifest describing its capabilities and the manifest may be broken down into units that can be referenced and reused, i.e., the definition can be modular. 

## Overview of lifecycle of a pluggable

[Editor's note: This section needs to be broken into sub-sections. This will be dealt with in the second version of this document.]

Most of this lifecycle discussion applies to a majority equipment types. Where the pluggable is special, this is highlighted.

~~~~

           (place holder for a simple picture for pluggable life cycle)                      

~~~~
{: #figure-overview-lifecycle-pluggable title="Lifecycle of a coherent pluggable"}

Pluggables, like all equipment are carefully chosen. A network operations company (the operator) will decide which mix of pluggables to use in the network based upon research and an understanding of capabilities of the plugs available in the marketplace. The operator will acquire instances of each type of pluggable of interest and trial them. They will also carry out "type approval" considering each type of pluggable for a particular application etc. The full detail of the Manifest for each type of pluggable is relevant at all of these stages.

Specific types of pluggable will be purchased only after detailed planning of the network. To carry out this planning, full knowledge of each type of pluggable will be required. The planning will use predictions of service demand and hence infrastructure need. The exercise may result in identification of several types of pluggable that can be interchanged for a particular specific purpose. Again, during this stage of the lifecycle the full detail of the Manifest for each type of pluggable is relevant.

The evaluation and planning exercise is an ongoing activity as the network grows and changes and as new plug types are introduced by vendors and to facilitate this each vendor will provide a Manifest for each plug type that need to be sufficiently detailed to determine interoperability between new and deployed pluggables.

When optical services are demanded, perhaps to provide underlay for the packet network, optical network analysis (viability etc.) is carried out to evaluate how to efficiently and effectively achieve the specific service demanded. This analysis will consider existing and new pluggables.

In some cases, at one extreme end of the range of policy choices, an operator may choose to fully populate a packet device with a range of plugs and may cable them to adjacent ROADMS. Else, pluggable deployment can be on a just-in-time basis, at the other extreme end of the range of policy choices, so the pluggable is not deployed (and hence is not cabled until the solution to realization of the optical service has been determined. In practice, a mix of both options is likely. Pluggables may already be deployed and stay in the host after de-commissioning but can be re-used to establish new services leveraging ROADM flexibility. 

Regardless of the pluggable deployment approach, the pluggable capability must be accounted for in the optical network analysis activity. Where the pluggable is present, the range of installed pluggables constrain the possible realizations, where the pluggables have not been deployed all approved pluggables could be considered during the analysis, although packet device capability to support pluggables will need to be considered and this may eliminate some pluggables. In addition, if there is some urgency, the availability of the type of pluggable to the installation engineer and/or in the local spares holding inventory must also be considered.

So, the optical network analysis takes into account the full definitions of the pluggables of interest where each is defined in a corresponding and referenced manifest.

Once the design is available, any necessary physical installation exercise is carried out, driven by work orders that identify the type of pluggable to instal. 

On detection of the pluggable, the control system will validate that the work order has been carried out correctly. To do this, the full type/version of the pluggable is read and compared with the intent. Where there are discrepancies, either a work order is constructed to correct the installation error, or the detected pluggable type/version is evaluated for compatibility with the specific design. This is done using the Manifest for that type/version. It is possible that the type/version may be acceptable although perhaps a little more expensive than the optimum choice etc.

Where the pluggable Manifest identifies proprietary capabilities, it is possible that there are proprietary properties available from the pluggable control interface to the packet device. These properties may be expressed in proprietary YANG on the device interface to the controller. For the packet device to be able to express the proprietary properties it needs the YANG augment files, the pluggable control interface definition and a mapping definition. 

In an ideal realization of the control solution, the P-PNC could provide the packet device with the YANG augment definition, and the mapping definition in such a way that this could be run by generic software on the packet device requiring no change to the software of the packet device. 

This approach could also be taken to cater for enhancements to the standard YANG including mappings from proprietary properties on the pluggable and new standard properties in the device interface to the controller.

Considering the above, it appears that all pluggable capabilities whether they be proprietary or standard should be fully described in the Manifest. This may be achieved by a reference to a standard that is itself fully defined in machine interpretable form. This approach would allow for a far more flexible and future-proofed control solution.

[Note: I doubt that the following statement is subject to a standard]
Finally, some proprietary capability statements required in the Manifest may be commercially sensitive. It would be quite reasonable to encrypt these property statements allowing for them to pass to a specific vendor control component without being snooped or interpreted in any way by other control components (from other vendors).

## Overall lifecycle stages in detail

In this document, the lifecycle is broken down into the following stages:

- Design deployment patterns
- Design specific deployments
- Purchase inventory
- Install infrastructure
- Design services over infrastructure
- Install plugs, connect cables and validate
- Configure and turn up service
- Operate service

These stages are not intended to reflect any specific operational practice and are intended to be neutral with respect to any existing operator.

Clearly, there is also the reverse sequence which includes deactivating a service and removing the plug and there are also various edits and refinements that result from changes in demand and changes in understanding of the service needs etc. These steps have been omitted at this stage as the initial list above is sufficient to the develop a deep understanding of the control of the plugs. Further stages will be added in a future version of this document.

### Design deployment patterns

### Design specific deployments

### Purchase inventory

### Install infrastructure

### Design services over infrastructure

### Install plugs, connect cables and validate

### Configure and turn up service

### Operate service

## High level interaction sequence

The following section provides an interaction sequence within a stylized control architecture.

### The stylized control architecture

### The interaction sequence
 

# Security Considerations

TODO Security

# IANA Considerations

This document has no IANA actions.

--- back

{:numbered="false"}

# Acknowledgments

TODO acknowledge.
