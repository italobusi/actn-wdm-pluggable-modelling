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

  G.698.2:
    title: "Amplified multichannel dense wavelength division multiplexing applications with single channel optical interfaces"
    author:
      org: ITU-T Recommendation G.698.2
    date: November 2018
    seriesinfo: 
    target: 

--- abstract

This draft outlines the modeling of optical pluggables within a host packet device within the context of a packet over optical network. The model encompasses all pertinent properties of the pluggable for various packet over optical use cases and is partitioned into three primary areas: the optical media interface, the electrical plug to host interconnect, and the physical equipment of the pluggable.

Included in the model are representations of configuration, states, and telemetry data, as well as profiles and coherent plug capabilities. Emphasizing the importance of considering both vendor-agnostic and vendor-specific attributes in modeling coherent pluggables.

Drawing from existing models in IETF, OpenConfig, ITU-T, OIF, and TAPI, this model offers enhanced uniform structuring and naming. Additionally, it provides insight into the mapping to plug interface structures defined in CMIS.

--- middle

# Terminology

{::boilerplate bcp14-tagged}

The following terms abbreviations are used in this document:

- Optical Plug / Coherent Pluggable / Pluggable: A small form factor coherent optical module

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

- {{plug-manifest}}: Optical Pluggables Capabilities (Pluggable Manifest)

- {{plug-manifest-example}}: Optical Pluggables Manifest Examples

- {{plug-lcm}}: Optical Pluggables Life Cycle Management

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
 
## Equipment 

The "Equipment functional block" in {{figure-optical-pluggable-building-blocks}} represents the coherent pluggable itself and has the following characteristics:

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
 | |                        Equipment                         | |
 | |----------------------------------------------------------| |
 |                                                              |
 |--------------------------------------------------------------|

~~~~
{: #figure-optical-pluggable-building-blocks title="Optical Pluggable Building Blocks"}


{: #data-model}
# Optical Pluggables Data Modeling

The attributes of all functional building block of a coherent pluggable in {{figure-optical-pluggable-building-blocks}} will be exposed to external packet and optical controllers via host interface (1) shown in {{figure-details-packet-optical-device}}. To this end, we need to model the coherent pluggable building blocks described in {{building-blocks}}.

The data modelling of each functional blocks provides attributes in four areas:

1. Coherent pluggable capabilities
2. Coherent pluggable configurations
3. Coherent pluggable states
4. Coherent pluggable alarm notifications

## Coherent pluggable capabilities attributes

The capability attributes are read-only which defines the functional capabilities of the optical pluggables. These attributes are grouped together in a profile called "operational-mode" which contains attributes such as modulation, bit-rate, baud-rate, chromatic-dispersion, polarization, FEC etc. 

The coherent pluggable capabilities are described by a set of operational-modes it supports, i.e., an optical pluggable might support multiple opeational-modes, where each "operational-mode" can be defined by a standard body or by a vendor. These operational-modes are called "standard-operational-modes" and "custom-operational-modes", respectively. The "standard-operational-modes" are well-define modes which are defined by a standard bodies such as ITU-T {{G.698.2}} whereas the ""custom-operational-modes" are defined by a vendor and might not be supported by all other vendors. 

{{plug-manifest}} discusses the concept of the "coherent pluggable manifest", which is a repository for all "standard-operational-modes" or "custom-operational-modes". It also outlines the benefit of such repository.

## Coherent pluggable configurations attributes

The coherent pluggables support a set of read-write attributes which are configurable. Example of such configuration attributes are output power, central frequency and operational-mode. Note that since a coherent pluggable may support multiple operational-modes (standard or custom), the read-write operational-mode attribute programs the coherent pluggable to be functional in one of those operational-modes.

## Coherent pluggable states and PM telemetry data attributes

These read-only attributes will be generated by optical pluggables and represents various states of the optical pluggable such as channel input power, channel output power, central frequency, laser temperature, current OSNR etc. In most cases these attributers are temporal and coherent pluggable reports values such as instantaneous, min, max and average.

## Coherent plug alarm notifications

The coherent pluggables might generate various alarm notifications due to the various reasons.

{: #yang-model}
# Optical Pluggables Yang Model


{: #plug-manifest}
# Optical Pluggables Capabilities (Plug Manifest)

Details of optical pluggable operational-mode and host-operational-mode are in a public repository such as GitHub, SharePoint which can easily be read/interpreted by any SDN controller. Using this approach, usage of standard and custom operational modes are identical as will be shown later on this section. All attributes associated to operational-mode and host-operational-mode are defined by IETF as part of this draft.

~~~~

  Optical Pluggable Manifest
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
{: #figure-optical-pluggable-manifest title="Optical Pluggable Manifest"}

This following is an example for standard mode defined by ITU-T

~~~~
organization: ITU-T
operational-mode: 0x3E
list of attributes
      modulation: 16QUM
      bit-rate: 478.75 Gb/s
      baud-rate: 59.84375
      more ...

organization: ITU-T
host-operational-mode: 0x11
list of attributes
      number of line: 8
      modulation: PAM4
      application-bit-rate: 425.00 Gb/s
      more ...
~~~~

The following is an example for vendor-specific mode defined by vendor "Vendor-X"

~~~~
organization: Vendor-X
operational-mode: 0x22
list of attributes
      modulation: ...
      bit-rate: ...
      baud-rate: ...
      more ...

organization: Vendor-X
host-operational-mode: ox33
list of attributes
      number of line: ...
      modulation: ...
      application-bit-rate: ...
      more ...
~~~~

The following is an example for vendor-specific mode defined by vendor "Vendor-Y". Note that although both Vendor-X and Vendor-Y define operational-mode 0x22, the content for each one is unique and as a result these two operation-modes might be different.

~~~~
organization: Vendor-Y
operational-mode: 0x22
list of attributes
      modulation: ...
      bit-rate: ...
      baud-rate: ...
      more ...

organization: Vendor-Y
host-operational-mode: ox44
list of attributes
      number of line: ...
      modulation: ...
      application-bit-rate: ...
      more ...
~~~~

As the above examples show, using the coherent pluggable manifest allows us to have identical usage for both standard and vendor-defined operational-mode and host-operational-mode. The concept of "optical pluggable manifest" significantly simplifies the definition and usage of both "operational-mode" and "host-operational-mode"


{: #plug-manifest-example}
# Optical Pluggables Manifest Examples

~~~~
   |----------|        |------------------|
   | Coherent |        | Packet, optical, |
   | Pluggable|  <-->  | higher layer     |
   | Manifest |        | controllers      |
   |----------|        |------------------|
                                ^
                                |
                                v
                      |------------------|
                      |                  |
     |------| p1    |------|             |
     |  R1 ++-\     |  m1  |             |  
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
    R1, R2:     Router
    m1, m2, m3: ROADM                      

~~~~
{: #figure-optical-pluggable-manifest-example-1 title="Coherent Pluggable Manifest Example 1"}



{: #plug-lcm}
# Optical Pluggables Life Cycle Management

[Editor's note: Some of the material in this section may be better places in earlier sections, in some cases there should be references to earlier sections and some text has implications on earlier sections. This will be dealt with in the second version of this document.]

This section discusses the complete lifecycle of a pluggable. It includes discussion on the pre-purchase evaluation of pluggables through installation to the operation of a pluggable in a live network. 

Some of the terminology is local to this document. where this is the case the terms are clarified in the definitions section.

## Deployment of a pluggable in context

Prior to installation of a pluggable in a packet device, various resarch, approval, planning, design and viability activities must have been carried out. All of these activities will require detailed information on the capabilities of the pluggable. This points to the need for a strong separation between the model of operation of the pluggable and the model of capability (as detailed information on the capability of the pluggable is required long before it is installed and operational). This analysis shows that discovery of capability detail from the pluggable is unnecessary. Instead, all that is required to be reported by the pluggable is a complete statement of type and version to the degree sufficient to precisely identify the definition/specification of the plug capability by reference (capability is per type). As will be discussed, this complete statement of type and version is also fundamentally necessary for the coordination of spares.

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

In this document, the term Manifest is used for the collection of information, appropriately structured and interrelated, that describes the capabilities of a pluggable. In other terminology spaces the Manifest may be considered to be a Specification, a profile,etc.

It should be noted that any equipment could have a Manifest describing its capabilities and the manifest may be broken down into units that can be referenced and reused, i.e., the definition can be modular. 

## Overview of lifecycle of a pluggable

[Editor's note: This section needs to be broken into sub-sections. This will be dealt with in the second version of this document.]

Most of this lifecycle discussion applies to a majority equipment types. Where the pluggable is special, this is highlighted.

Pluggables, like all equipmemt are carefully chosen. A network operations company (the operator) will decide what pluggables to use in the network based upon research and an understanding of capabilities of the plugs available in the marketplace. The operator will acquire instances of each type of pluggable of interest and trial them. They will also carry out "type approval" considering each type of pluggable for a particular application etc. The full detail of the Manifest for each type of pluggable is relevant at all of these stages.

Specific types of pluggable will be purchased only after detailed planning of the network. To carry out this planning, full knowledge of each type of pluggable will be required. The planning will use predictions of service demand and hence infrastructure need. The exercise may result in identification of several types of pluggable that can be interchanged for a particular specific purpose. Again, during this stage of the lifecycle the full detail of the Manifest for each type of pluggable is relevant.

The research, evaluation and planning exercise is an ongoing activity as the network grows and changes and as new plug types are introduced by vendors and to facilitate this each vendor will provide a Manifest for each plug type.

When optical services are demanded,perhaps to provide underlay for the packet network, optical network analysis (viability etc.) is carried out to evaluate how to efficiently and effectively achieve the specific service demanded. This analysis will consider the plugs.

Prior to progressing further it is important to note that pluggables are highly valuable, and correspondingly expensive. They are deployed in a controlled fashion. There are a range of policies for deployment of pluggables.

In some cases, at one extreme end of the range of policy choices, an operator may choose to fully populate a packet device with a range of plugs and may cable them to adjacent ROADMS. However, it is more likely that pluggable deployment will be on a just-in-time basis, at the other extreme end of the range of policy choices, so the pluggable is not deployed (and hence is not cabled until the solution to realization of the optical service has been determined.

Regardless of the pluggable deployment approach, the pluggable capability must be accounted for in the optical network analysis activity. Where the pluggable is present, the range of installed pluggables constrain the possible realizations, where the pluggables have not been deployed all approved pluggables could be considered during the analysis, although packet device capability to support pluggables will need to be considered and this may eliminate some pluggables. In addition, if there is some urgency, the availablility of the type of pluggable to the installation engineer and/or in the local spares holding inventory must also be considered.

So, the optical network analysis takes into account the full definitions of the pluggables of interest where each is defined in a corresponding and referenced manifest.

Once the design is available, any necessary physical installation exercise is carried out, driven by work orders that identify the type of pluggable to instal. 

On detection of the pluggable, the control system will validate that the work order has been carried out correctly. To do this, the full type/version of the pluggable is read and compared with the intent. Where there are discrepancies, either a work order is constructed to correct the installation error, or the detected pluggable type/version is evaluated for compatibility with the specific design. This is donu using the Manifest for that type/version. It is possible that the type/version may be acceptable although perhaps a little more expensive than the optimum choice etc.

Where the pluggable Manifest identifies proprietary capabilities, it is possible that there are proprietary properties available from the pluggable control interface to the packet device. These properties may be expressed in proprietary YANG on the device interface to the controller. For the packet device to be able to express the proprietary properties it needs the YANG augment files, the pluggable control interface definition and a mapping definition. 

In an ideal realization of the control solution, the controller could provide the packet device with the YANG augment definition, and the mapping definition in such a way that this could be run by generic software on the packet device requiring no change to the software of the packet device. 

This approach could also be taken to cater for enhancements to the standard YANG including mappings from proprietary properties on the pluggable and new standard properties in the decice interface to the controller.

Considering the above, it appears that all pluggable capabilities whether they be proprietary or standard should be fully described in the Manifest. This may be achieved by a reference to a standard that is itself fully defined in machine interpretable form. This approach would allow for a far more flexible and future-proofed control solution.

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
