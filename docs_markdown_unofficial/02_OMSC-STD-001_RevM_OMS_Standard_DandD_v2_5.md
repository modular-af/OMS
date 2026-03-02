Open Mission Systems (OMS)

Definition And Documentation (D&D)

OMS Standard Version 2.5

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Executive Summary

Open Mission Systems (OMS) is a non-proprietary open architecture
standard for integrating Units of Replaceability (UoRs) such as OMS
Subsystems and OMS Services (hereafter referred to as “Subsystems” and
“Services”) into OMS Mission Packages (hereafter referred to as “Mission
Packages”). Figure 0.0-1 depicts the top-level view of the OMS Reference
Architecture.

<img src="media/image2.png" style="width:6.5in;height:4.63542in" />

<span id="_Toc219290684" class="anchor"></span>Figure 0.0-1 Top-Level
View of the OMS Reference Architecture

At its core, OMS promotes interoperability utilizing the OMS Reference
Architecture:

-   Mission Package – composed of OMS Architecture Elements including
    OMS Platform (hereafter referred to as “Platform”), Subsystems,
    Services, and OMS Isolators (hereafter referred to as “Isolators”)
    that are defined as UoRs

-   Platform – infrastructure (hardware and software) for the Mission
    Package including Abstract Service Bus (ASB), Critical Abstraction
    Layer (CAL), data storage, Open Computing Environment (OCE), and
    Other Mission Processing

-   Subsystem – payloads and sensors with dedicated hardware and
    software resources that provide unique capabilities (e.g., RADAR,
    EO/IR, ESM, etc.)

-   Service – software only (e.g., auto-router, tracker, fusion engine,
    task manager, etc.) that may provide unique capabilities

-   Isolator – isolation layer between Mission Package and an external
    system

-   OMS Data Exchanges – standardized information exchanges (OMS
    Messaging, OMS Data Transfer, Special Signals, and Security
    Information Exchanges) via Platform interconnecting Subsystems and
    Services.

OMS allows rapid integration of loosely coupled capabilities provided by
Subsystems and Services. This is accomplished through well-defined data
exchanges, which includes following a publish/subscribe paradigm for OMS
Messaging. OMS is not an all or nothing approach. A tiered compliance
structure allows new and existing programs to plan an orderly pathway to
full compliance while managing budget constraints and competing
pressures for new capabilities and technologies.

-   Tier 1 permits legacy adoption of key portions of OMS

-   Tier 2 builds upon Tier 1 and increases interoperability

-   Tier 3, full compliance, maximizes OMS benefits to the program

OMS is a living standard and it is possible gaps in the OMS Standard may
be discovered. The OACWG Governance Plan provides flexibility allowing
OMS Adopting Programs to submit a Change Request addressing the
identified gaps to mitigate impact on compliance and support the
Adopting Program’s schedule.

The OMS Definition and Documentation (D&D) includes the OMS Standard and
supporting OMS documents (e.g., Verification Cross Reference Matrix
(VCRM), standardized templates with instructions, compliance checklists
with instructions, etc.). Together these documents define requirements,
provide architecture definition and guidance, and specify compliance
assessment approaches that enable any Adopting Program to include OMS in
their acquisition specifications.

The business objectives driving the development of OMS include the need
to reduce acquisition and lifecycle costs as well as the need to reduce
the risks associated with development, sustainment, technology refresh,
and upgrades of mission systems. Balance of the OMS business objectives
occurs through design flexibility and standardized implementation.
Domain acquisition efficiencies are possible once balance is achieved.

The OMS Standard enables future technology upgrades providing
flexibility that allows providers of an OMS Platform, OMS Subsystem, and
OMS Service to offer innovative and competitive solutions to future
problems.

Revision Record

<table>
<thead>
<tr class="header">
<th>REVISION</th>
<th>DATE</th>
<th>DESCRIPTION</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>M</td>
<td>22 January 2026</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

This page is intentionally left blank.

Table of Contents

[1 Introduction 1](#introduction)

[1.1 Important Notice on Requirements in this Document
4](#important-notice-on-requirements-in-this-document)

[1.2 Business Objectives and Key Technical Attributes
4](#business-objectives-and-key-technical-attributes)

[1.3 OMS Approach 6](#oms-approach)

[2 Key Terms of the Standard 7](#key-terms-of-the-standard)

[2.1 Key Terms of the OMS Standard 7](#key-terms-of-the-oms-standard)

[3 Key Elements of OMS 8](#key-elements-of-oms)

[3.1 OMS Standard 8](#oms-standard)

[3.2 OMS Reference Architecture 8](#oms-reference-architecture)

[3.3 OMS Message Set and Schema 13](#oms-message-set-and-schema)

[3.4 Architectural Features and Support
14](#architectural-features-and-support)

[3.4.1 Position Information 14](#position-information)

[3.4.2 State and Status 14](#state-and-status)

[3.4.3 Time 14](#time)

[3.4.4 Open Computing Environment (OCE)
14](#open-computing-environment-oce)

[3.4.5 Critical Abstraction Layer (CAL)
15](#critical-abstraction-layer-cal)

[3.4.6 Isolation 15](#isolation)

[3.4.7 Data Storage 15](#data-storage)

[3.5 OACWG Governance Plan 15](#oacwg-governance-plan)

[3.6 OMS Cybersecurity Guide 16](#oms-cybersecurity-guide)

[4 Reserved 17](#reserved)

[5 References 18](#references)

[5.1 Related Standards 18](#related-standards)

[5.2 OMS D&D Documents 21](#oms-dd-documents)

[6 Architecture Elements and OMS Data Exchanges
24](#architecture-elements-and-oms-data-exchanges)

[6.1 Service 25](#service)

[6.1.1 Service State Transition Behaviors
27](#service-state-transition-behaviors)

[6.2 Subsystem 32](#subsystem)

[6.2.1 Subsystem State Transition Behaviors
34](#subsystem-state-transition-behaviors)

[6.2.2 Subsystem Startup 43](#subsystem-startup)

[6.2.3 Subsystem Erase 48](#subsystem-erase)

[6.2.3.1 Definitions of Specific Erase Processes
48](#definitions-of-specific-erase-processes)

[6.2.3.2 Subsystem Erase Processing While Staying in an Operational
State
49](#subsystem-erase-processing-while-staying-in-an-operational-state)

[6.2.4 Subsystem Shutdown 50](#subsystem-shutdown)

[6.2.4.1 Rules Pertaining to Proper Subsystem Shutdown
51](#rules-pertaining-to-proper-subsystem-shutdown)

[6.2.4.2 Case 1a: Subsystem Shutdown Processing without Erase from
OPERATE State
51](#case-1a-subsystem-shutdown-processing-without-erase-from-operate-state)

[6.2.4.3 Case 1b: Subsystem Shutdown Processing without Erase from Any
State Except OPERATE
53](#case-1b-subsystem-shutdown-processing-without-erase-from-any-state-except-operate)

[6.2.4.4 Case 2a: Subsystem Shutdown Processing with Erase from OPERATE
State
54](#case-2a-subsystem-shutdown-processing-with-erase-from-operate-state)

[6.2.4.5 Case 2b: Subsystem Shutdown Processing with Erase from Any
State Except OPERATE
56](#case-2b-subsystem-shutdown-processing-with-erase-from-any-state-except-operate)

[6.3 OMS Data Exchanges 58](#oms-data-exchanges)

[6.3.1 OMS Messaging 58](#oms-messaging)

[6.3.1.1 Message Definition 59](#message-definition)

[6.3.1.2 Approved and Unapproved OMS Messages
60](#approved-and-unapproved-oms-messages)

[6.3.1.3 OMS Message Sets for Compliance
61](#oms-message-sets-for-compliance)

[6.3.1.4 Tier 1 Messages 61](#tier-1-messages)

[6.3.1.4.1 Tier 1 Required Subsystem Message Set
61](#tier-1-required-subsystem-message-set)

[6.3.1.4.2 Tier 1 Minimum Message Set 62](#tier-1-minimum-message-set)

[6.3.1.5 Tier 2 Minimum Message Set 64](#tier-2-minimum-message-set)

[6.3.1.6 Tier 3 Message Set 64](#tier-3-message-set)

[6.3.2 Data Transfer 65](#data-transfer)

[6.3.2.1 Data Transfer Protocols and Data Formats
65](#data-transfer-protocols-and-data-formats)

[6.3.2.2 Non-OMS Data Transfer 73](#non-oms-data-transfer)

[6.3.2.3 Data Transfer of Very Large Products and High Performance
Transfers
78](#data-transfer-of-very-large-products-and-high-performance-transfers)

[6.3.2.4 Data Transfer Coordination 78](#data-transfer-coordination)

[6.3.2.4.1 Uniform Resource Identifier 79](#uniform-resource-identifier)

[6.3.2.4.2 Product Persistence 92](#product-persistence)

[6.3.2.4.3 Non-Streaming Data Transfers
92](#non-streaming-data-transfers)

[6.3.2.4.4 Non-Streaming Data Products via Sockets
93](#non-streaming-data-products-via-sockets)

[6.3.2.4.5 Streaming Data Products 95](#streaming-data-products)

[6.3.2.4.6 Remote Direct Memory Access Data Transfers
95](#remote-direct-memory-access-data-transfers)

[6.3.3 Special Signals 95](#special-signals)

[6.3.3.1 Discrete Signals 95](#discrete-signals)

[6.3.3.2 Time Reference Signals 101](#time-reference-signals)

[6.3.3.3 Frequency Reference, Shared Radio Frequency, and Intermediate
Frequency Signals
103](#frequency-reference-shared-radio-frequency-and-intermediate-frequency-signals)

[6.3.3.4 High-Speed Data Lines 103](#high-speed-data-lines)

[6.3.3.5 Other Signals 103](#other-signals)

[6.3.3.6 Non-OMS Special Signals Allowed in the OMS Standard
104](#non-oms-special-signals-allowed-in-the-oms-standard)

[6.3.3.7 Non-OMS Special Signals Superseded by OMS Messages
105](#non-oms-special-signals-superseded-by-oms-messages)

[6.3.4 Security Information Exchanges
109](#security-information-exchanges)

[6.4 Isolators 109](#isolators)

[6.4.1 External Standards 112](#external-standards)

[6.5 Platform 115](#platform)

[6.5.1 Abstract Service Bus (ASB) 116](#abstract-service-bus-asb)

[6.5.2 Critical Abstraction Layer (CAL)
117](#critical-abstraction-layer-cal-1)

[6.5.2.1 Language-Specific CAL 119](#language-specific-cal)

[6.5.2.2 Language-Agnostic CAL 119](#language-agnostic-cal)

[6.5.3 Mission Processing 120](#mission-processing)

[6.5.3.1 Open Computing Environment (OCE)
120](#open-computing-environment-oce-1)

[6.5.3.1.1 Façade-Based Approach 121](#façade-based-approach)

[6.5.3.1.2 Java-Based Approach 121](#java-based-approach)

[6.5.3.1.3 OCE General Requirements 121](#oce-general-requirements)

[6.5.3.1.4 OCE Façade Requirements 123](#oce-façade-requirements)

[6.5.3.1.5 OCE Java Requirements 123](#oce-java-requirements)

[6.5.3.1.6 Example OCE Architectures 123](#example-oce-architectures)

[6.5.3.2 Other Mission Processing 124](#other-mission-processing)

[6.5.4 Data Storage 124](#data-storage-1)

[6.5.5 Time Reference and Time Synchronization
124](#time-reference-and-time-synchronization)

[6.5.5.1 Time Reference 124](#time-reference)

[6.5.5.2 Time Synchronization 125](#time-synchronization)

[6.5.6 Position Information 127](#position-information-1)

[6.5.7 Cloud-Based Platforms 127](#cloud-based-platforms)

[6.6 Mission Package 128](#mission-package)

[7 Compliance 129](#compliance)

[7.1 Compliance Tiers 129](#compliance-tiers)

[7.1.1 Change Request Submission Guidelines
130](#change-request-submission-guidelines)

[7.2 Service Compliance 132](#service-compliance)

[7.2.1 Service Tier 1 Requirements 132](#service-tier-1-requirements)

[7.2.2 Service Tier 2 Requirements 134](#service-tier-2-requirements)

[7.2.3 Service Tier 3 Requirements 134](#service-tier-3-requirements)

[7.2.4 OCE-Hosted Services 135](#oce-hosted-services)

[7.3 Subsystem Compliance 135](#subsystem-compliance)

[7.3.1 Subsystem Tier 1 Requirements
135](#subsystem-tier-1-requirements)

[7.3.2 Subsystem Tier 2 Requirements
138](#subsystem-tier-2-requirements)

[7.3.3 Subsystem Tier 3 Requirements
138](#subsystem-tier-3-requirements)

[7.4 Platform Compliance 138](#platform-compliance)

[7.4.1 Platform Tier 1 Requirements 139](#platform-tier-1-requirements)

[7.4.2 Platform Tier 2 Requirements 140](#platform-tier-2-requirements)

[7.4.3 Platform Tier 3 Requirements 140](#platform-tier-3-requirements)

[7.5 Mission Package Compliance 140](#mission-package-compliance)

[7.5.1 Mission Package Tier 1 Requirements
140](#mission-package-tier-1-requirements)

[7.5.2 Mission Package Tier 2 Requirements
141](#mission-package-tier-2-requirements)

[7.5.3 Mission Package Tier 3 Requirements
142](#mission-package-tier-3-requirements)

[7.5.4 Service Capability List for Compliance
142](#service-capability-list-for-compliance)

[7.5.5 Subsystem List for Compliance
143](#subsystem-list-for-compliance)

[8 Requirements Verification Cross Reference Matrix
144](#requirements-verification-cross-reference-matrix)

[8.1 Compliance Verification Cross Reference Matrix (VCRM)
144](#compliance-verification-cross-reference-matrix-vcrm)

[9 OMS Compliance Assessment Approaches and Artifacts
218](#oms-compliance-assessment-approaches-and-artifacts)

[9.1 OMS Compliance Assessment Approaches
218](#oms-compliance-assessment-approaches)

[9.1.1 Government Assessment 218](#government-assessment)

[9.1.2 Prime/Contractor/Supplier Self-Assessment
218](#primecontractorsupplier-self-assessment)

[9.1.3 External Assessment 219](#external-assessment)

[9.2 Key Documents 219](#key-documents)

[9.3 Compliance Tailoring for Different Phases of a Program
219](#compliance-tailoring-for-different-phases-of-a-program)

[9.3.1 Proposal/Acquisition 219](#proposalacquisition)

[9.3.2 PDR/CDR 222](#pdrcdr)

[9.3.3 Final Test/System Test 224](#final-testsystem-test)

[10 Version of the D&D 225](#version-of-the-dd)

[10.1 Versioning Process 225](#versioning-process)

[11 List of Symbols, Abbreviations, and Acronyms
226](#list-of-symbols-abbreviations-and-acronyms)

[12 Glossary 227](#glossary)

[A Appendix A – OMS Implementation Patterns
228](#appendix-a-oms-implementation-patterns)

[A.1 A-1 Adapter Implementation Patterns
228](#a-1-adapter-implementation-patterns)

List of Figures

[Figure 0.0-1 Top-Level View of the OMS Reference Architecture
iii](#_Toc219290684)

[Figure 1.0-1 OMS D&D Document Tree 1](#_Toc219290685)

[Figure 1.0-2 Top-Level View of the OMS Reference Architecture
2](#_Toc219290686)

[Figure 1.0-3 Example OMS Architecture Implementation 3](#_Toc219290687)

[Figure 3.2-1 Example OMS Architecture Implementation 9](#_Toc219290688)

[Figure 3.2-2 Mission Package Worksheet 10](#_Toc219290689)

[Figure 3.2-3 Detailed Structure Diagram for the ASB 12](#_Toc219290690)

[Figure 6.1-1 Example Service Showing Service Boundary
26](#_Toc219290691)

[Figure 6.1-2 Service Status State Diagram 28](#_Toc219290692)

[Figure 6.1-3 Allowed State Transitions for OMS Service
29](#_Toc219290693)

[Figure 6.2-1 Example Subsystem showing Subsystem Boundary
33](#_Toc219290694)

[Figure 6.2-2 Subsystem State Diagram 36](#_Toc219290695)

[Figure 6.2-3 Allowed State Transitions for OMS Subsystem
37](#_Toc219290696)

[Figure 6.2-4 Notional Subsystem Startup Sequence Example (1 of 3)
45](#_Toc219290697)

[Figure 6.2-5 Notional Subsystem Startup Sequence Example (2 of 3)
46](#_Toc219290698)

[Figure 6.2-6 Notional Subsystem Startup Sequence Example (3 of 3)
47](#_Toc219290699)

[Figure 6.2-7 Subsystem Erase Processing While Staying in OPERATE State
Message Sequence Example 50](#_Toc219290700)

[Figure 6.2-8 Case 1a: Subsystem Shutdown Processing without Erase from
OPERATE State Message Sequence Example 52](#_Toc219290701)

[Figure 6.2-9 Case 1b: Subsystem Shutdown Processing without Erase from
Any State Except OPERATE Message Sequence Example 53](#_Toc219290702)

[Figure 6.2-10 Case 2a: Subsystem Shutdown Processing with Erase from
OPERATE State Message Sequence Example 55](#_Toc219290703)

[Figure 6.2-11 Case 2b: Subsystem Shutdown Processing with Erase from
Any State Except OPERATE Message Sequence Example 57](#_Toc219290704)

[Figure 6.3-1 OMS Data Exchanges 58](#_Toc219290705)

[Figure 6.3-2 Determining Approved and Unapproved OMS Messages
60](#_Toc219290706)

[Figure 6.3-3 Non-Streaming Data Products via Files 92](#_Toc219290707)

[Figure 6.3-4 Non-Streaming Data Products via Sockets
94](#_Toc219290708)

[Figure 6.4-1 Example Isolator Boundary between OMS Mission Package and
External Elements 110](#_Toc219290709)

[Figure 6.4-2 Driving Use Cases for External Standard Usage
114](#_Toc219290710)

[Figure 6.5-1 Detailed Structure Diagram for the ASB
116](#_Toc219290711)

[Figure 6.5-2 An OMS Platform’s ASB includes an OMS CAL
118](#_Toc219290712)

[Figure 6.5-3 Example 1 PPS Pulse Train with Corresponding OMS Messages
126](#_Toc219290713)

[Figure A.1-1 Platform-Hosted OMS Adaptation 228](#_Toc219290714)

[Figure A.1-2 Subsystem-Hosted OMS Adaptation 229](#_Toc219290715)

[Figure A.1-3 Standalone OMS Subsystem 230](#_Toc219290716)

This page is intentionally left blank.

List of Tables

[Table 5.1-1 Reference Standards 18](#_Toc219290717)

[Table 5.2-1 OMS D&D Documents 22](#_Toc219290718)

[Table 5.2-2 Other Documents 23](#_Toc219290719)

[Table 6.1-1 OMS Service State Definitions and Allowed Transitions
30](#_Toc219290720)

[Table 6.2-1 OMS Subsystem State Definitions and Allowed Transitions
38](#_Toc219290721)

[Table 6.3-1 Tier 1 Required Subsystem Message Set 61](#_Toc219290722)

[Table 6.3-2 Tier 1 Minimum Message Set 63](#_Toc219290723)

[Table 6.3-3 Tier 2 Minimum Message Set 64](#_Toc219290724)

[Table 6.3-4 Data Transfer Formats, APIs, and Protocols
67](#_Toc219290725)

[Table 6.3-5 Non-OMS Data Transfers 73](#_Toc219290726)

[Table 6.3-6 Data Transfer Protocols and APIs 74](#_Toc219290727)

[Table 6.3-7 OMS URI Formats 80](#_Toc219290728)

[Table 6.3-8 Data Formats and MIME Types 82](#_Toc219290729)

[Table 6.3-9 OMS Discrete and Voltage Reference Signals (Note 1)
96](#_Toc219290730)

[Table 6.3-10 OMS Discrete and Voltage Time Reference Signals
101](#_Toc219290731)

[Table 6.3-11 Other Signals Defined within OMS 103](#_Toc219290732)

[Table 6.3-12 Non-OMS Special Signals Allowed in the OMS Standard
104](#_Toc219290733)

[Table 6.3-13 Non-OMS Special Signals Superseded by OMS Messages
105](#_Toc219290734)

[Table 6.5-1 Approved Time Synchronization Protocols
125](#_Toc219290735)

[Table 6.5-2 High Fidelity Time Synchronization Mechanisms
125](#_Toc219290736)

[Table 8.1-1 Compliance Verification Cross Reference Matrix (VCRM)
145](#_Toc219290737)

[Table 9.3-1 Element Compliance Tailoring during Proposal or Acquisition
Phase 220](#_Toc219290738)

[Table 9.3-2 Element Compliance Tailoring at CDR/PDR
223](#_Toc219290739)

This page is intentionally left blank.

Introduction
============

Open Mission Systems (OMS) is a government owned architecture
specification, not an implementation specification. OMS does not contain
rules on how to implement a system, instead it focuses on the
Architecture Elements along with their interfaces and how information is
exchanged across those interfaces.

The OMS Standard is a living mission systems architecture defined by key
system interfaces between OMS Subsystems (i.e., payloads and sensors
with dedicated hardware and software resources that provide unique
capabilities) and OMS Services (i.e., software only) integrated with an
OMS Platform. These interfaces use open and standardized non-proprietary
interface definitions, but decouple the technical implementations from
the interfaces. This OMS Standard enables future technology upgrades
providing flexibility that allows Platform, Subsystem, and Service
providers to offer innovative and competitive solutions to future
problems.

The OMS Definition and Documentation (D&D) provides the information
needed to understand the open mission systems initiative and to use the
architecture it defines. The OMS Definition and Documentation includes
the documents shown in Figure 1.0-1, OMS D&D Document Tree:

<img src="media/image3.png" style="width:6.5in;height:4.03125in" />

<span id="_Toc219290685" class="anchor"></span>Figure 1.0-1 OMS D&D
Document Tree

The scope of OMS is bounded by the OMS Mission Package, the highest
level OMS construct. An implementation of an OMS Mission Package is
described in its Mission Package Worksheet (MPW), which delineates the
Units of Replaceability (UoRs) that constitute the Mission Package. The
Top-Level View of the OMS Reference Architecture (Figure 1.0-2, Top
Level View of the OMS Reference Architecture) depicts an OMS Mission
Package as an OMS Platform (i.e., common infrastructure such as
networking and computing resources) integrated with OMS Subsystems, OMS
Services, and OMS Isolators. Mission Package, Platform, Subsystem,
Service, and Isolator are the OMS Architecture Elements, and are also
OMS UoRs. Figure 1.0-2 also shows that OMS Architecture Elements are
interconnected using OMS Data Exchanges and are architecturally
isolated, using OMS Isolators, from the elements of the larger weapon
system into which it is integrated.

<img src="media/image2.png" style="width:6.5in;height:4.63542in" />

<span id="_Toc219290686" class="anchor"></span>Figure 1.0-2 Top-Level
View of the OMS Reference Architecture

While OMS Subsystems and OMS Services are the building blocks that
enable OMS mission functionality, the top-level system design of an OMS
Mission Package is largely defined by the OMS Platform, which is the
supportive infrastructure into which Subsystems, Services, and Isolators
are integrated. Figure 1.0-3, Example OMS Architecture Implementation,
depicts a notional implementation of an OMS Mission Package. It shows
that OMS Services can be contained in OMS Subsystems or integrated
directly with the OMS Platform, and depicts the elements the OMS
Platform provides, including an Abstract Service Bus (ASB), Critical
Abstraction Layer (CAL), mission processing (including an Open Computing
Environment (OCE) and Other Mission Processing), time reference/synch
and position information, and data storage).

OMS follows a publish/subscribe paradigm for OMS Messaging; the
publisher and subscriber are abstracted by the CAL to promote
interoperability and loose coupling. In other words, the CAL is the
mechanism to abstract any knowledge of source or destination from the
publishing or subscribing Subsystems, Services, and Isolators. The
knowledge of OMS Messages for Subsystems, Services, and Isolators is
limited to publishing and subscribing to topics. In the context of
publishing and subscribing, a topic is a named resource to which
messages are sent by publishers and received by subscribers. Therefore,
Subsystems, Services, and Isolators will focus on OMS Messages rather
than source or destination.

<img src="media/image4.png" style="width:6.5in;height:3.80208in" />

<span id="_Toc219290687" class="anchor"></span>Figure 1.0-3 Example OMS
Architecture Implementation

OMS supports the concept of Units of Replaceability (UoRs), which are
modular elements with well-documented interfaces and behaviors that can
be added/replaced, or upgraded with minimum impact on other elements.
OMS UoRs are the Mission Package, Platform, Subsystem(s), Service(s),
and Isolator(s). Ideally, OMS UoRs that are planned for future
upgrade/replacement, or are candidates for reuse in another OMS
implementation, are identified in the up-front stages of the acquisition
and development cycle, and are specified and developed accordingly.

Important Notice on Requirements in this Document
-------------------------------------------------

The OMS Standard identifies the requirements that an Adopting Program
must meet to achieve OMS compliance. The requirements are defined in the
form of RQMT statements throughout this document. Section 8 contains the
Verification Cross Reference Matrix (VCRM) that lists all of the
requirements and provides the Verification Requirements (VRs) and
Acceptance Criteria (ACs) for each requirement defined in this Standard.
The ACs identify how a requirement is satisfied from a compliance
perspective. Understanding the intent and meaning of the requirements is
best accomplished by reading the VCRM in conjunction with those sections
that define requirements. Ultimately, the VCRM, and the compliance
checklists derived from the VCRM, should be used when compliance
assessment is undertaken.

Business Objectives and Key Technical Attributes
------------------------------------------------

The open mission systems architecture defined by OMS is intended to meet
the following business objectives/goals with associated amplifying
information:

-   Promote adaptability, flexibility, and expandability supporting
    weapon systems design/goals

<!-- -->

-   Deliver capability at the speed of relevance

-   Expand OMS to meet the evolving needs of the DoD portfolio

<!-- -->

-   Support a variety of missions and domains

-   Enable data exchanges across weapons systems

<!-- -->

-   System-to-System, Machine-to-Machine data exchanges are critical to
    battlespace superiority in threat-dense, highly-contested
    environments

<!-- -->

-   Simplify integration

<!-- -->

-   Promote common understanding and use of OMS Message/Fields

-   Standardize suitable behaviors via Normalization

<!-- -->

-   Engage in future function information technology/advanced technology
    environments

-   Facilitate adoption of modern technologies

<!-- -->

-   Support additional programing languages, new capabilities, Model
    Based Systems Engineering (MBSE) tools and approaches

<!-- -->

-   Balance complexity to increase speed of adoption

<!-- -->

-   Balance between complexity and functionality

<!-- -->

-   Increasing complexity increases the understanding needed to
    implement functions

-   Need functionality to meet evolving warfighter needs and
    capabilities

<!-- -->

-   Limit multiple paths to accomplish same functionality

-   Increase OMS intuitiveness and reduce expertise needed to implement

<!-- -->

-   Reduce technical risk and overall cost of ownership of weapon system
    programs

-   Enable affordable technology refresh and capability evolution

<!-- -->

-   Identify clear upgrade pathways within the OMS framework

-   Investigate backward compatibility potential

<!-- -->

-   Enable reuse and portability of system elements across weapon
    systems

<!-- -->

-   DoD acquisition strategy includes acquiring capabilities deployable
    on multiple weapon systems

-   Promote portability of software from one Mission Package to another
    Mission Package

-   Migrate from “Plug and talk” to “Plug and play”

<!-- -->

-   Enable independent development and deployment of system elements as
    Units of Replaceability (UoRs)

-   Enable a range of cybersecurity approaches

<!-- -->

-   DoD is modernizing their cybersecurity approaches

-   DevSecOps software development strategy

-   Empower continuous-Authority To Operate (ATO) and Certificate to
    Field (CTF).

These business objectives are met via the following key technical
attributes:

-   Isolation of mission package from non-OMS system elements with the
    intent of avoiding impacts to elements that require costly
    certification and/or have safety implications

-   Simplified integration that reduces cost & technical risk (for both
    initial integration and future changes)

-   A Critical Abstraction Layer (CAL) interface that provides a defined
    abstraction while isolating the implementation of the Platform
    infrastructure from Subsystems and Services

-   Adaptability to both multi-level security (MLS) or cross-domain
    guard Cybersecurity approaches

-   Adoption of service-oriented design principles including loose
    coupling of services, service abstraction, composability,
    encapsulation, and documentation to describe information exchanges
    (e.g., Service Contracts)

-   Use of adaptable and expandable data bus technologies

-   Inclusion of an Open Computing Environment (OCE) that provides a
    known host environment for Services

-   Requiring functional and logical definition of the architecture by
    non-proprietary “ICDs” at key system interfaces

-   An Abstract Service Bus (ASB) formed by the combination of the
    service-oriented bus, communication middleware, and transport for
    Special Signals

-   Services that are location independent on the ASB.

OMS Approach
------------

The OMS Standard includes the descriptions, compliance requirements,
approaches, and guidance necessary for Adopting Programs to apply OMS
compliance as an acquisition requirement.

The management plan addressing the ongoing governance and sustainment of
OMS is called out in Section 3.5, OACWG Governance Plan. See the plan
for details on OACWG governance structure, OACWG organizational
relationships, and the OACWG change process.

Key Terms of the Standard
=========================

Key Terms of the OMS Standard
-----------------------------

The following is a set of key terms that a reader should be familiar
with prior to reading this document. The definition of these terms can
be found in OMSC-STD-002, Abbreviations and Glossary, which was built to
include terms that might have multiple meanings and terms where the
meaning has been customized for use in OMS.

-   Abstract Service Bus (ASB)

-   Adaptability

-   Adapter

-   Architecture Element

-   Capability

-   Critical Abstraction Layer (CAL)

-   Cybersecurity

-   Data Transfer

-   Flexibility

-   Isolator

-   Minimum Message Set (MMS)

-   Mission Package

-   Mission Package Worksheet (MPW)

-   OMS Data Exchanges

-   OMS Messages

-   OMS Message Set

-   OMS Messaging

-   OMS OS Façade

-   Open Computing Environment (OCE)

-   Platform

-   Provision

-   Security Information Exchange(s)

-   Service

-   Service Contract

-   Special Signals

-   Subsystem

-   Unit of Replaceability (UoR)

-   Use Case

Key Elements of OMS
===================

OMS has several key elements:

-   Open Mission System (OMS) Standard

-   OMS Reference Architecture

-   OMS Message Set

-   OACWG Governance Plan

-   OMS Cybersecurity Guide.

The following sections provide some additional identification of these
elements.

OMS Standard
------------

The OMS Definition & Documentation (D&D) is a set of documents as shown
in Figure 1.0-1, OMS D&D Document Tree.

The OMS Standard, OMSC-STD-001, describes:

-   Requirements for three tiers of OMS compliance

-   Requirements for the elements of the OMS Architecture

-   OMS compliance assessment approaches

-   Verification, acceptance criteria, and OMS compliance artifacts

-   Versioning of the OMS Standard.

OMS Reference Architecture
--------------------------

The OMS Reference Architecture, as discussed in Section 1, was created
early in the development of OMS and both informed the definition and
validated the utility of the Architecture Elements of the OMS Standard.
Service-oriented design patterns and principles were fundamental to the
development of the OMS Reference Architecture. The OMS Data Exchanges
are designed to drive implementations towards implementing loosely
coupled services that perform self-contained mission functions. The OMS
Message Set drives the level of granularity, at which the mission
functions are exposed, and provides a common data representation for the
business logic of mission execution. The design of the OMS Data
Exchanges also provides location transparency to the application level
service software. The OMS Data Exchanges allow the service software to
be abstracted from the specific implementation of the data exchange
network. The encapsulation of service functionality and abstraction from
Platform specific integration requirements supports the reusability of
OMS Subsystems.

Service-oriented design patterns and principles are re-enforced by the
documentation requirements placed on OMS Subsystems, Services, and
Isolators. They all must provide Service Contracts with required content
that ensures the data required for service composability is exposed.
Using the non-proprietary OMS Service Contracts, system engineers can
compose new Mission Packages by reusing existing OMS Subsystems and
Services. Their location independence and abstraction from the Platform
specific implementation of the data exchange network reduces the
integration time required. These service-oriented attributes of the OMS
Reference Architecture and OMS Standard are central to meeting the
business objectives of OMS. Figure 0.0-1, Top-Level View of the OMS
Reference Architecture, depicts an OMS Reference Architecture
implementation.

<img src="media/image4.png" style="width:6.5in;height:3.80208in" />

<span id="_Toc219290688" class="anchor"></span>Figure 3.2-1 Example OMS
Architecture Implementation

Whereas the Figure 3.2-1 depicts an example OMS Mission Package, the OMS
Mission Package Worksheet (MPW), OMSC-TMP-006, depicted in Figure 3.2-2
provides a powerful tool for describing details of the composition of an
OMS Mission Package throughout its lifecycle. The MPW provides top-level
information about the Mission Package and its constituent Platform,
Subsystems, Services, and Isolators, which are the Mission Package UoRs.
Identifying and documenting UoRs early, and keeping their documentation
up to date throughout the development lifecycle, emphasizes a key aspect
of OMS architecture, i.e., OMS’s standardized elements and interfaces
that enable independent acquisition and upgrades of UoRs as well as
their reuse/exchangeability between Mission Packages.

<img src="media/image5.png" style="width:6.5in;height:3.59375in" />

<span id="_Toc219290689" class="anchor"></span>Figure 3.2-2 Mission
Package Worksheet

A Mission Package, shown in the box outlined in blue in Figure 3.2-1,
Example OMS Architecture Implementation, is an OMS Architecture Element
and is the highest level OMS construct. A Mission Package consists of a
Platform, Subsystems, Services, and Isolators (all of which are also OMS
Architecture Elements).

A Service is an OMS Architecture Element that is only comprised of one
or more software components. A Service provides mission functions and/or
Capabilities. A Service is assessed in accordance with a prescribed
interface and predefined constraints and policies specified by a
non-proprietary Service Contract. Capabilities are typically tasked,
discovered, commanded, or any combination thereof, using OMS Messaging.
A Service may run in the OCE, Subsystems, or Other Mission Processing. A
Service communicates via an OMS Platform over the Abstract Service Bus
(ASB) using OMS Data Exchanges.

A Subsystem is an OMS Architecture Element that is comprised of one or
more hardware and software components. A Subsystem provides one or more
Capabilities. A Subsystem is assessed in accordance with a prescribed
interface and predefined constraints and policies specified by a
non-proprietary Service Contract and a non-proprietary Subsystem
Description Document. A Subsystem is not required to host or present a
Service. A Subsystem communicates via an OMS Platform over the Abstract
Service Bus (ASB) using OMS Data Exchanges.

Within the OMS architecture, there is a defined need to provide
isolation of the Mission Package from elements external to the OMS
Mission Package with the intent of avoiding impacts to elements that
require costly certification and/or have safety implications. There are
two methods by which Isolation is accomplished in the OMS architecture.
The first method uses an Isolator that limits the effects of change
between the Mission Package boundary and another system. The second
method is to provide physical isolation to ensure complete separation
from safety critical elements.

An OMS Platform is an OMS Architecture Element, which is itself a
composite architecture. A Platform includes the ASB, mission processing
(including an OCE), and typically provides the time reference, time
synchronization, and position information for the Mission Package.
Unlike Subsystems and Services, Platforms do not provide Capabilities.
The Platform is assessed in accordance with the non-proprietary Platform
Description Document (PDD). A Mission Package integrator integrates
Subsystems, Services, and Isolators with the Platform to provide the
mission capabilities required by the Mission Package.

A Platform may include non-OMS software that provides a measure of
robustness for the underlying infrastructure. An example might be
infrastructure software and settings necessary to protect information
passing through the ASB. Figure 3.2-3, Detailed Structure Diagram for
the ASB, provides a depiction of the ASB and its interactions with other
OMS Architecture Elements.

The Abstract Service Bus (ASB) is a composite Architecture Element that
encompasses all forms of OMS Data Exchanges. The ASB includes the
physical and/or virtual network layers that are the foundation of the
ASB’s other sub-elements. It is important to note that the ASB is a
logical construct, not a single physical element distinct from other OMS
elements. The ASB includes components hosted on Subsystems, the Open
Computing Environment (OCE), and Other Mission Processing elements. In
general, the design details of the network infrastructure are abstracted
by Data Transfer and the Critical Abstraction Layer (CAL).

OMS uses a standard Critical Abstraction Layer (CAL) interface to
isolate Subsystem/Service/Isolator application software from Platform
specific CAL implementations. Each ASB will include one or more CAL
implementations that allow Subsystems, Services, and Isolators to
communicate using OMS Messages. The CAL interface aids portability of
Subsystems and Services between OMS Mission Packages. The CAL allows
applications to interact with message objects regardless of the
underlying transport and routing implementation.

<img src="media/image6.png" style="width:6.5in;height:5.28125in" />

<span id="_Toc219290690" class="anchor"></span>Figure 3.2-3 Detailed
Structure Diagram for the ASB

OMS Data Exchanges consist of four types: OMS Messaging, Data Transfer,
Special Signals, and Security Information Exchanges.

OMS Messaging is the process of sending or receiving OMS Messages
between a Subsystem, Service, or Isolator and the Platform using a
Critical Abstraction Layer (CAL). For OMS Messaging, a CAL is required
to send a message from a Subsystem, Service, or Isolator to the
Platform. For OMS Messaging, a CAL is required to receive a message by a
Subsystem, Service, or Isolator from the Platform. An OMS Message is the
unit of information sent or received using an OMS CAL. The content and
structure of OMS Messages are defined using an XML Schema Definition
(XSD) specification that conforms to the UCI Schema Style and Design
Specification (OAC-SPC-001).

OMS follows a publish/subscribe paradigm for OMS Messaging; the
publisher and subscriber are abstracted by the CAL to promote
interoperability and loose coupling. In other words, the CAL is the
mechanism to abstract any knowledge of source or destination from the
publishing or subscribing Subsystems, Services, and Isolators. The
knowledge of OMS Messages for Subsystems, Services, and Isolators is
limited to publishing and subscribing to topics. In the context of
publishing and subscribing, a topic is a named resource to which
messages are sent by publishers and received by subscribers. Therefore,
Subsystems, Services, and Isolators will focus on OMS Messages rather
than source or destination.

Data Transfer directly interfaces with the ASB’s IP switched fabric. OMS
Data Transfer defines a set of allowed protocols and data formats to
move various types of data among Subsystems, Services, and storage
devices within a Mission Package. OMS Data Transfer is based on
standardized protocols and data formats. In addition, some of these
protocols and data formats are restricted in use because of overlap with
other OMS Data Exchanges, namely OMS Messaging. The intent is that when
there is overlap between OMS Messaging and Data Transfer, the preferred
solution is to encourage the use of OMS Messaging.

Special Signals are interfaces between Subsystems, Services, and the
Platform that do not easily fit into the other interface types (OMS
Messaging, Data Transfer, and Security Information Exchanges).

Security Information Exchanges directly interface with the ASB’s IP
switched fabric. OMS does not impose requirements on the security
analysis and security design approaches of Architecture Elements. OMS
Security Information Exchanges assume that the underlying security
posture of the data exchange endpoints is already in place. Security
Information Exchanges include exchanges needed to support the AT ICD as
well as Cybersecurity solutions.

This Standard provides a normative description of status, position
information, and time synchronization that enables Subsystem, Service,
and Isolator providers to understand which of these features are
available and how to use them.

OMS Message Set and Schema
--------------------------

An OMS Message Set is a collection of specific Approved and/or
Unapproved OMS Messages. The term OMS Message Set can be used in the
generic architectural sense. For example, an OMS Message Set starts as a
subset of the messages defined by a released UCI Standard and may be
modified. The term can also be used in a specific architectural sense.
For example, the set of OMS Messages supported by a CAL specific to a
Subsystem or the OMS Messages comprising the OMS Standard Tier 1 Minimum
Message Set. An OMS Message Set is based on the UCI Standard
(OAC-STD-001).

OMS Message Schema is a formal definition of OMS Messages.

Architectural Features and Support
----------------------------------

There are architectural features and support across OMS Mission Packages
that a Subsystem, Service, or Isolator developer may rely upon. These
items are highlighted here because they are typically found in
implementations of OMS Mission Packages.

### Position Information

Platforms that are a part of something that moves (i.e., an airplane, a
truck, a satellite, etc.) are required to provide position information
to any Subsystems, Services, or Isolators which may require it. This
information is distributed using **PositionReport** messages and
optionally the higher fidelity **PositionReportDetailed** messages. More
information on position information may be found in Section 6.5.6,
Position Information.

### State and Status

Within OMS, a state is defined as a condition or set of conditions that
exist at a specific point in time. States are deterministic and mutually
exclusive. A state must have a defined state transition such as trigger
(event causing transition), guard (condition that must be present for
transition), or an effect (function to be performed during transition).

Subsystems, Services, and Isolators within a Mission Package are
required to report their status on a regular interval. This status
includes information such as uptime, current state (e.g., operational,
degraded), and is reported using the applicable **ServiceStatus** or
**SubsystemStatus** message. More information about required status
reporting may be found in Section 6.1 Service, Section 6.2 Subsystem,
and Section 6.4 Isolators.

### Time

An OMS Platform is required to provide a time reference and a
standardized method for synchronizing that time across the Mission
Package. Section 6.5.5 Time Reference and Time Synchronization provides
details regarding Time Reference and Time Synchronization.

### Open Computing Environment (OCE)

An OMS Platform is required to provide an Open Computing Environment
(OCE). An OCE provides an OMS-defined environment in which Services may
execute. Section 6.5.3.1 Open Computing Environment describes the OCE in
detail.

### Critical Abstraction Layer (CAL)

An OMS Platform is required to provide one or more Critical Abstraction
Layer (CAL) implementations. A CAL provides an OMS-defined API for
creating, sending, and receiving OMS Messages. The internal processing
of the messages may differ across Platforms or CAL implementations, but
the API with which Subsystems, Services, and Isolators interact remains
the same across all CALs for a specific programming language. More
information about CALs may be found in Section 6.5.2 Critical
Abstraction Layer (CAL). In-depth information on using the CAL API may
be found in OMSC-SPC-001, CAL Specification. Language-specific CAL API
generation is defined in OMSC-SPC-007, Java CAL Interface Generation
Specification and OMSC-SPC-008, C++ CAL Interface Generation
Specification. Language-agnostic CAL API(s) are defined in OMSC-SPC-013,
Language-Agnostic CAL Specification.

### Isolation

Within the OMS architecture, there is a defined need to provide
isolation between OMS elements and other safety critical elements
external to the OMS Mission Package. Constraining the architecture to
bound/limit where and to what degree re-certification would be required
upon change helps to reduce the cost of updates because the changes are
limited to specific Services or is eliminated because of physical
isolation. There are two methods by which Isolation is accomplished in
the OMS architecture. The first method uses an OMS Isolator that limits
the effects of change between the OMS Mission Package boundary and
another system. The second method is to provide physical isolation to
ensure complete separation from safety critical elements.

Physical isolation provides the least risk of impacting certification or
causing issues with safety critical elements. Physical isolation, in
this context, focuses on the message and data interface of the mission
system. A system that shares a power bus, for example, could be
considered physically isolated if there is no mission data crossing the
OMS Mission Package architectural boundary.

### Data Storage

When required by a Mission Package, the Platform and/or Subsystem(s)
provide(s) the required data storage. This data storage may support
distribution of sensor products, storage of configuration files, etc.
Data storage is discussed in Section 6.5.4 Data Storage.

OACWG Governance Plan
---------------------

OMSC-PGM-0031, Management Plan: OACWG Governance Plan, defines the
change process used to make modifications to the Open Architecture
Management Standards (OAMS): OMS and UCI.

OMS Cybersecurity Guide
-----------------------

The Cybersecurity Guide (OMSC-GDE-003) defines the concepts, guidance,
and information that OMS Adopting Programs and system designers will
utilize to document the cybersecurity posture for OMS Architecture
Elements. The OMS Cybersecurity Guide is based on the Joint Chiefs of
Staff/J6 Cyber Survivability Endorsement Implementation Guide (CSEIG).
As part of program acquisition, cyber survivability is a key element
that must be considered as part of the System Survivability. The Cyber
Survivability Risk Category (CSRC) and Cyber Survivability Attributes
(CSAs) are defined for an acquisition per the CSEIG. When available, the
CSRC is provided by the Adopting Program as part of a system security
engineering process with tailored Cyber Survivability requirements, and
is applicable at the weapon system level. The OMS Mission Package, and
its constituent Architecture Elements, inherit the CSRC of the weapon
system. In OMS, the CSRC is documented in the Mission Package Worksheet
(MPW), which is referenced in the Mission Package Description Document
(MPDD). The CSRC defines the cybersecurity posture of the Mission
Package. In OMS, the CSAs are documented in the MPDD, Platform
Description Document (PDD), Subsystem Description Document (SDD), and
Service Contract. The CSAs describe the cybersecurity posture of the
Mission Package, Platform, Subsystem, Service, and Isolator.

Reserved
========

References
==========

Related Standards
-----------------

The documents listed in Table 5.1-1, Reference Standards, are cited
throughout this document. For dated references, only the edition cited
applies. For undated references, the latest edition of the referenced
document (including any amendments or corrigenda) applies. This table is
not used for OMS compliance.

<span id="_Toc219290717" class="anchor"></span>Table 5.1-1 Reference
Standards

<table>
<thead>
<tr class="header">
<th>Document Number</th>
<th>Document Title</th>
<th>Revision</th>
<th>Date</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td>Future Airborne Capability Environment (FACE™) Technical Standard</td>
<td>Version 1.0</td>
<td>26 January 2012</td>
</tr>
<tr class="even">
<td>0N481180</td>
<td>EKMS 308 Data Tagging and Delivery Standard [DS-101]</td>
<td>Revision F</td>
<td>16 April 2008</td>
</tr>
<tr class="odd">
<td>AMS GRA</td>
<td>Agile Mission Suite Government Reference Architecture (AMS GRA)</td>
<td>7.0</td>
<td>26 July 2022</td>
</tr>
<tr class="even">
<td>H.264</td>
<td>ISO/IEC 14496-10 – MPEG-4 Part 10, Advanced Video Coding</td>
<td></td>
<td>13 June 2019</td>
</tr>
<tr class="odd">
<td>ICD-GPS-060</td>
<td>Global Positioning System (GPS) User Equipment (Phase III) Interface Control Document (ICD) for the Precise Time and Time Interval (PTTI) Interface</td>
<td>Revision B</td>
<td>12 February 2002</td>
</tr>
<tr class="even">
<td>IEEE Std 1003.1-2008</td>
<td>IEEE Standard for Information Technology – Portable Operating System Interface (POSIX)</td>
<td></td>
<td>01 December 2008</td>
</tr>
<tr class="odd">
<td>IEEE Std 1003.1-2013</td>
<td>IEEE Standard for Information Technology – Portable Operating System Interface (POSIX)</td>
<td></td>
<td>19 April 2013</td>
</tr>
<tr class="even">
<td>IEEE Std 1278.1-2012</td>
<td>IEEE Standard for Distributed Interactive Simulation – Application Protocols Version 7</td>
<td>Version 7</td>
<td>December 2012</td>
</tr>
<tr class="odd">
<td>IEEE Std 1588-2008</td>
<td>IEEE Standard for a Precision Clock Synchronization Protocol for Networked Measurement and Control Systems (Precision Time Protocol PTP)</td>
<td></td>
<td>27 March 2008</td>
</tr>
<tr class="even">
<td>IEEE Std 1588-2019</td>
<td>IEEE Standard for a Precision Clock Synchronization Protocol for Networked Measurement and Control Systems (Precision Time Protocol PTP)</td>
<td></td>
<td>7 November 2019</td>
</tr>
<tr class="odd">
<td>IRIG 200-04</td>
<td>Inter Range Instrumentation Group (IRIG) Serial Time Code Formats</td>
<td></td>
<td>September 2004</td>
</tr>
<tr class="even">
<td>IISO/IEC 15444-1:2004</td>
<td>Information Technology - JPEG 2000 Image Coding System: Core coding system, 2004</td>
<td></td>
<td>September 2004</td>
</tr>
<tr class="odd">
<td></td>
<td>Linux</td>
<td>Kernel 2.6 or greater</td>
<td></td>
</tr>
<tr class="even">
<td>MIL-PRF-0089049 (NIMA)</td>
<td>Vector Product Format (VPF) Products, General Specification</td>
<td></td>
<td>24 November 1998</td>
</tr>
<tr class="odd">
<td>MIL-PRF-89012A</td>
<td>World Vector Shoreline (WVSPLUS) Draft Specification</td>
<td></td>
<td>24 August 1999</td>
</tr>
<tr class="even">
<td>MIL-PRF-89020B</td>
<td>Performance Specification: Digital Terrain Elevation Data (DTED)</td>
<td></td>
<td>23 May 2000</td>
</tr>
<tr class="odd">
<td>MIL-PRF-89034</td>
<td>Performance Specification: Digital Point Positioning Data Base (DPPDB)</td>
<td>Revision A</td>
<td>3 August 2018</td>
</tr>
<tr class="even">
<td>MIL-PRF-89038</td>
<td>Performance Specification: Compressed Arc Digitized Raster Graphics (CADRG)</td>
<td>w/Amendment 2</td>
<td>28 March 2000</td>
</tr>
<tr class="odd">
<td>MIL-PRF-89039</td>
<td>Vector Map Level 0</td>
<td>w/Amendment 2</td>
<td>27 June 2002</td>
</tr>
<tr class="even">
<td>MIL-PRF-89040A</td>
<td>Vector Product Interim Terrain Data</td>
<td></td>
<td>8 May 1996</td>
</tr>
<tr class="odd">
<td>MIL-STD-704</td>
<td>Aircraft Electric Power Characteristics</td>
<td>Revision F</td>
<td>12 March 2004</td>
</tr>
<tr class="even">
<td>MIL-STD-2411-2</td>
<td>Department of Defense Interface Standard: Integration of Raster Product Format Files into the Nation Imagery Transmission Format</td>
<td>w/Notice 1</td>
<td>31 March 2004</td>
</tr>
<tr class="odd">
<td>MIL-STD-2500C</td>
<td>National Imagery Transmission Format (NITF) Standard (NITFS)</td>
<td></td>
<td>01 May 2006</td>
</tr>
<tr class="even">
<td>MIL-STD-3011</td>
<td>Joint Range Extension Applications Protocol (JREAP)</td>
<td>Revision C</td>
<td>10 June 2016</td>
</tr>
<tr class="odd">
<td>MISB RP 0811.1</td>
<td>Motion Imagery Standards Board (MISB) Recommended Practice: JPIP Profile (Client/Server Functions)</td>
<td></td>
<td>23 October 2014</td>
</tr>
<tr class="even">
<td>MISP Version 6.4 [Deprecated]</td>
<td>Motion Imagery Standards Profile (MISP)</td>
<td>Version 6.4</td>
<td>04 October 2012</td>
</tr>
<tr class="odd">
<td>MISP Version 6.5 [Deprecated]</td>
<td>Motion Imagery Standards Profile (MISP)</td>
<td>Version 6.5</td>
<td>24 October 2013</td>
</tr>
<tr class="even">
<td>MISP Version 6.6 [Deprecated]</td>
<td>Motion Imagery Standards Profile (MISP)</td>
<td>Version 6.6</td>
<td>27 February 2014</td>
</tr>
<tr class="odd">
<td>MISP-2023.2</td>
<td>Motion Imagery Standards Profile (MISP)</td>
<td>2023.2</td>
<td>March 2023</td>
</tr>
<tr class="even">
<td>MORA</td>
<td>MORA Data Message VITA Radio Transport (VRT)</td>
<td>2.4</td>
<td>1 March 2021</td>
</tr>
<tr class="odd">
<td>OAC-STD-001</td>
<td>Universal Command and Control (C2) Interface (UCI) Standard</td>
<td>I</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OAC-STD-002</td>
<td>Universal Command and Control (C2) Interface (UCI) Schema</td>
<td>E</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OAC-SPC-001</td>
<td>Universal Command and Control (C2) Interface (UCI) Schema Style and Design Specification</td>
<td>E</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>Open Geospatial Consortium (OGC)</td>
<td>Open Geospatial Consortium (OGC) standards as mandated in the DoD Information Technology Standards Registry (DISR). Limited to OMS Map and Navigation data transfer formats</td>
<td>per the DISR</td>
<td>per the DISR</td>
</tr>
<tr class="odd">
<td>RFC 768</td>
<td>User Datagram Protocol (UDP)</td>
<td></td>
<td>28 August 1980</td>
</tr>
<tr class="even">
<td>RFC 791</td>
<td>Internet Protocol, DARPA Internet Program Protocol Specification (Internet Protocol IPv4)</td>
<td>IPv4</td>
<td>September 1981</td>
</tr>
<tr class="odd">
<td>RFC 793</td>
<td>Transmission Control Protocol (TCP), DARPA Internet Program Protocol Specification</td>
<td></td>
<td>September 1981</td>
</tr>
<tr class="even">
<td>RFC 959</td>
<td>File Transfer Protocol (FTP)</td>
<td></td>
<td>October 1985</td>
</tr>
<tr class="odd">
<td>RFC 1119</td>
<td>Network Time Protocol (NTP) (Version 2) Specification and Implementation</td>
<td>Version 2</td>
<td>September 1989</td>
</tr>
<tr class="even">
<td>RFC 1122</td>
<td>Requirements for Internet Hosts - Communication Layers, Section 4.2 Transmission Control Protocol (TCP)</td>
<td></td>
<td>October 1989</td>
</tr>
<tr class="odd">
<td>RFC 1350</td>
<td>The TFTP Protocol (Revision 2) [Trivial File Transfer Protocol]</td>
<td>Revision 2</td>
<td>July 1992</td>
</tr>
<tr class="even">
<td>RFC 1738</td>
<td>Uniform Resource Locators (URL)</td>
<td></td>
<td>December 1994</td>
</tr>
<tr class="odd">
<td>RFC 1813</td>
<td>Network Files System (NFS) Version 3 Protocol Specification</td>
<td>Version 3</td>
<td>June 1995</td>
</tr>
<tr class="even">
<td>RFC 2224</td>
<td>NFS URL Scheme</td>
<td></td>
<td>October 1997</td>
</tr>
<tr class="odd">
<td>RFC 2428</td>
<td>File Transfer Protocol (FTP) Extensions for IPv6 and Network Address Translating (NATs)</td>
<td></td>
<td>September 1998</td>
</tr>
<tr class="even">
<td>RFC 2460</td>
<td>Internet Protocol, Version 6 (IPv6) Specification (Internet Protocol IPv6)</td>
<td>IPv6</td>
<td>December 1998</td>
</tr>
<tr class="odd">
<td>RFC 2818</td>
<td>HTTP over TLS</td>
<td></td>
<td>May 2000</td>
</tr>
<tr class="even">
<td>RFC 3220</td>
<td>Transport Protocol for Real-Time Applications</td>
<td></td>
<td>July 2003</td>
</tr>
<tr class="odd">
<td>RFC 3530</td>
<td>Network Files System (NFS) Version 4 Protocol Specification</td>
<td>Version 4</td>
<td>April 2003</td>
</tr>
<tr class="even">
<td>RFC 3550</td>
<td>(Real-time Transport Protocol (RTP) and Real-time Transport Control Protocol (RTCP)) A Transport Protocol for Real-Time Applications</td>
<td></td>
<td>July 2003</td>
</tr>
<tr class="odd">
<td>RFC 3617</td>
<td>Uniform Resource Identifier (URI) Scheme and Applicability Statement for the Trivial File Transfer Protocol (TFTP)</td>
<td></td>
<td>October 2003</td>
</tr>
<tr class="even">
<td>RFC 4180</td>
<td>Common Format and MIME Type for Comma-Separated Values (CSV) Files</td>
<td></td>
<td>October 2005</td>
</tr>
<tr class="odd">
<td>RFC 4217</td>
<td>Securing FTP with TLS</td>
<td></td>
<td>October 2005</td>
</tr>
<tr class="even">
<td>RFC 5246</td>
<td>The Transport Layer Security (TLS) Protocol Version 1.2</td>
<td></td>
<td>August 2008</td>
</tr>
<tr class="odd">
<td>RFC 7230</td>
<td>Hypertext Transfer Protocol (HTTP/1.1): Message Syntax and Routing</td>
<td>Version 1.1</td>
<td>June 2014</td>
</tr>
<tr class="even">
<td>RFC 7530</td>
<td>Network Files System (NFS) Version 4 Protocol</td>
<td>Version 4</td>
<td>March 2015</td>
</tr>
<tr class="odd">
<td>SMPTE 292M</td>
<td>Bit-Serial Digital Interface for High Definition Television</td>
<td></td>
<td>1998</td>
</tr>
<tr class="even">
<td>SPD-STD-001</td>
<td>SPEAD High Speed Signaling</td>
<td>1.0</td>
<td>7 June 2022</td>
</tr>
<tr class="odd">
<td>STANAG 3456</td>
<td>Aircraft Electrical Power System Characteristics</td>
<td>Revision 6</td>
<td>20 October 1997</td>
</tr>
<tr class="even">
<td>STANAG 4607</td>
<td>NATO Ground Moving Target Indicator (GMTI) Format</td>
<td>Edition 1</td>
<td>March 2005</td>
</tr>
<tr class="odd">
<td>EIA-170</td>
<td>Electrical Performance Standards - Monochrome Television Studio Facilities [RS-170]</td>
<td>1957 Edition</td>
<td>November 1957</td>
</tr>
<tr class="even">
<td>TIA/EIA-422-B</td>
<td>Electrical Characteristics of Balanced Voltage Digital Interface Circuits [RS-422]</td>
<td>B</td>
<td>May 1994</td>
</tr>
<tr class="odd">
<td>TIA-485-A</td>
<td>Electrical Characteristics of Generators and Receivers for Use in Balanced Digital Multipoint Systems [RS-485]</td>
<td>Revision A</td>
<td>March 1998</td>
</tr>
<tr class="even">
<td>libfabric</td>
<td>OpenFabrics Alliance libfabric</td>
<td>Version 1.11.2</td>
<td>15 December 2020</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>Extensible Markup Language (XML) 1.0 (Fifth Edition)</td>
<td>1.0</td>
<td>26 November 2008</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>XML Schema Part 1: Structures Second Edition</td>
<td>1.0</td>
<td>28 October 2004</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>XML Schema Part 2: Datatypes Second Edition</td>
<td>1.0</td>
<td>28 October 2004</td>
</tr>
</tbody>
</table>

OMS D&D Documents
-----------------

The documents listed in Table 5.2-1, OMS D&D Documents, are the
documents, which along with this Standard, comprise the OMS Definition
and Documentation (D&D) set. Table 5.2-2, Other Documents, lists other
OMS and UCI documentation to assist in the understanding and
implementation of OMS.

<span id="_Toc219290718" class="anchor"></span>Table 5.2-1 OMS D&D
Documents

<table>
<thead>
<tr class="header">
<th>Document Number</th>
<th>Document Title</th>
<th>Revision</th>
<th>Date</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>OMSC-CHK-002</td>
<td>OMS Mission Package Checklist</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-CHK-003</td>
<td>OMS Platform Checklist</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-CHK-004</td>
<td>OMS Subsystem Checklist</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-CHK-005</td>
<td>OMS Service Checklist</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-CHK-006</td>
<td>OMS Isolator Checklist</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-GDE-003</td>
<td>Cybersecurity Guide</td>
<td>D</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-INS-001</td>
<td>Platform Description Document (PDD) Template Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-INS-002</td>
<td>Subsystem Description Document (SDD) Template Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-INS-003</td>
<td>Service Contract Template Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-INS-007</td>
<td>Mission Package Description Document (MPDD) Template Instructions</td>
<td>I</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-INS-008</td>
<td>OMS Mission Package Checklist Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-INS-009</td>
<td>OMS Platform Checklist Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-INS-010</td>
<td>OMS Subsystem Checklist Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-INS-011</td>
<td>OMS Service Checklist Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-INS-012</td>
<td>OMS Isolator Checklist Instructions</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-INS-013</td>
<td>Mission Package Worksheet (MPW) Instructions</td>
<td>H</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-SPC-001</td>
<td>Critical Abstraction Layer (CAL) Specification</td>
<td>L</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-SPC-005</td>
<td>Operating System Façade Specification</td>
<td>J</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-SPC-007</td>
<td>Java Critical Abstraction Layer (CAL) Interface Generation Specification</td>
<td>K</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-SPC-008</td>
<td>C++ Critical Abstraction Layer (CAL) Interface Generation Specification</td>
<td>K</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-SPC-013</td>
<td>Language-Agnostic (LA) Critical Abstraction Layer (CAL) Specification</td>
<td>B</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-STD-002</td>
<td>Abbreviations and Glossary</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-TMP-001</td>
<td>Platform Description Document (PDD) Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-TMP-002</td>
<td>Subsystem Description Document (SDD) Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-TMP-003</td>
<td>Service Contract Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-TMP-006</td>
<td>Mission Package Worksheet (MPW) Template</td>
<td>H</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-TMP-007</td>
<td>Mission Package Description Document (MPDD) Template</td>
<td>I</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-VDD-001</td>
<td>Version Description Document (VDD)</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>

<span id="_Toc219290719" class="anchor"></span>Table 5.2-2 Other
Documents

<table>
<thead>
<tr class="header">
<th>Document Number</th>
<th>Document Title</th>
<th>Revision</th>
<th>Date</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>OMSC-PGM-031</td>
<td>OACWG Governance Plan</td>
<td>J</td>
<td>05 June 2025</td>
</tr>
<tr class="even">
<td>OMSC-SPC-009</td>
<td>Anti-Tamper Interface Control Document (AT ICD)</td>
<td>v1.1d</td>
<td>15 December 2023</td>
</tr>
<tr class="odd">
<td>OMSC-SPC-012</td>
<td>C++ Data Transfer (DT) Application Programming Interface (API) Specification</td>
<td>B</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-SPC-011</td>
<td>Java Data Transfer (DT) Application Programming Interface (API) Specification</td>
<td>B</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>All Source Positioning and Navigation Interface Control Document (ASPN ICD)</td>
<td>Version 2.1</td>
<td>26 March 2018</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>Joint Interface Control Document (JICD) 4.2 Specification and Primer</td>
<td>Revision 1.0.0</td>
<td>30 September 2013</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>Cyber Survivability Endorsement Implementation Guide (CSEIG)</td>
<td>Version 3</td>
<td>July 2022</td>
</tr>
<tr class="even">
<td>N/A</td>
<td><p>Shared Aperture Information File (SAIF) “filename.xsd”.</p>
<p>This SAIF schema supersedes the following SAIF formats listed below:</p>
<p>SPEAD_Information_File_4.5, Antenna_Information_File_5.0, Platform_Information_File_4.0, and Signal_Processing_Information_Files_3.0.</p></td>
<td>Version 1.0</td>
<td>27 July 2023</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>SPEAD_Information_Files_4.5.xsd</td>
<td>Version 4.5</td>
<td>13 November 2019</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>Antenna_Information_Files_5.0.xsd</td>
<td>Version 5.0</td>
<td>June 2021</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>Platform_Information_Files_4.0.xsd</td>
<td>Version 4.0</td>
<td>June 2021</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>Signal_Processing_Information_Files_3.0.xsd</td>
<td>Version 3.0</td>
<td>August 2020</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>Open Design Specification for .dwg files</td>
<td>Version 5.4.1</td>
<td>2013</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>NCEP WMO GRIB2 Documentation</td>
<td>Version 29</td>
<td>20 May 2022</td>
</tr>
</tbody>
</table>

Architecture Elements and OMS Data Exchanges
============================================

The OMS Standard defines the Architecture Elements of the OMS
architecture. Specific OMS Architecture Elements, namely Mission
Package, Platform, Subsystems, and Services are assessed for OMS
compliance tiers. The OMS Mission Package provider is responsible for
integrating all of the Architecture Elements associated with an OMS
Mission Package.

The OMS Standard identifies the requirements that an Adopting Program
must meet to achieve OMS compliance. The requirements are defined in the
form of RQMT statements. RQMTs can be separated into two groups.

The first group of RQMTs pertain to OMS elements that are not directly
assessed for OMS tiered compliance (e.g., Isolator, ASB, OCE, CAL,
etc.). These requirements are fundamental and are associated with an OMS
Platform or OMS Mission Package. They are considered “Tier 1”
requirements, therefore the RQMT text does not contain any specific
compliance tier designations. The requirements text is of the form “An
OMS &lt;element&gt; shall …” and are found throughout this Section 6.

The second group of RQMTs pertain to OMS Architecture Elements that are
directly assessed for OMS tiered compliance (Mission Package, Platform,
Subsystems, and Services) and have compliance checklists to aid in
assessing compliance. Requirements associated with these Architecture
Elements have RQMT text with specific compliance tier designations in
the form of “{&lt;optional condition&gt;,} A Tier &lt;x&gt; OMS
&lt;Architecture Element&gt; shall …,” where x = 1, 2, or 3. These RQMTs
are found in Section 7.

Note that some requirements use the word “applicable”. The term
“applicable” has special meaning for OMS compliance. The intent of the
use of applicable is to not artificially manufacture additional derived
requirements where none exist. For example, a Service in a Mission
Package does not need to use all messages in the Tier 1 Minimum Message
Set, only those applicable to its functionality. This helps reduce
unnecessary testing costs and eliminates unnecessary attack vectors,
while still allowing for design flexibility and composability at the
Mission Package level.

OMS Architecture Elements have been defined and the requirements
generated with a view to Tier 3 or full compliance. The reader is
encouraged to view these requirements in parallel with the Verification
Cross-Reference Matrix (VCRM) section, which includes the verification
requirements and acceptance criteria for each requirement.

Service
-------

A Service is an OMS Architecture Element that is only comprised of one
or more software components. A Service provides mission functions and/or
Capabilities. A Service is assessed in accordance with a prescribed
interface and predefined constraints and policies specified by a
non-proprietary Service Contract. Capabilities are typically tasked,
discovered, commanded, or any combination thereof, using OMS Messaging.
To ensure loose coupling, OMS follows a publish/subscribe paradigm for
OMS Messaging abstracted by the CAL. The knowledge of OMS Messages for a
Service is limited to publishing and subscribing via topics. Therefore,
a Service will focus on OMS Messages rather than source or destination.

A Service may run in the OCE, Other Mission Processing, or Subsystems. A
Service communicates via an OMS Platform over the ASB using OMS Data
Exchanges. If an Adapter is included in the Service to provide
adaptation software to support OMS Data Exchanges, then that Adapter is
considered a part of the Service. If the Service is located within a
Subsystem, the Service must run independently of the physical
Subsystem’s functionality or behavior. If a Subsystem physically hosts
an OCE implementation for use by a Platform, the OCE is considered part
of the Platform and not part of the logical Subsystem. Services running
in that OCE are not within the boundary of the logical Subsystem because
the Services must run independently of the physical Subsystem since they
should also be able to be run in any Platform-provided OCE without
change. An Isolator is not allowed to be hosted in an OMS Subsystem
unless it is specifically hosted in the OCE provided by the physical
Subsystem.

A Service boundary is defined as where the Service communications (e.g.,
messages, data transfer, signals, etc.) enter or exit the Service. A
Service boundary delineates the extent of a Service. Inside the Service
boundary are all of the software elements of the Service to implement
its functionality and conform to OMS requirements. Outside the Service
boundary are all other system elements, such as other Subsystems,
Services, and Isolators. Refer to Figure 6.1-1, Example Service Showing
Service Boundary, for an illustration of an example Service with three
constituent parts and its boundary.

<img src="media/image7.png" style="width:6.5in;height:4.05208in" />

<span id="_Toc219290691" class="anchor"></span>Figure 6.1-1 Example
Service Showing Service Boundary

Services may contain software components that are shared with other
Services. For such implementations, these are still separate logical
Services where each must abide by the rules and requirements imposed by
the OMS Standard. This includes restricting communication between
Services to those permitted by the Standard (i.e., the Services cannot
communicate through the shared components). The intent is that there is
no implicit data sharing through the software components. Using
stateless software components is one way to mitigate such communication,
but if a stateful software component is used, it cannot share the state
generated by one Service with another Service. As an example, a shared
component can be deployed within a Mission Package as a single
executable even though it is shared by separate Services.

When a Service uses Platform resources (e.g., an OCE, Other Mission
Processing, data storage), the resource requirements needed by the
Service must be documented in its Service Contract. This includes any
use of the Platform ASB hardware to exchange information between
constituent parts of the Service. This is also applicable when a Service
uses Subsystem resources, such as a Subsystem’s OCE implementation; the
Subsystem resources needed by the Service must be documented in its
Service Contract.

In summary, all information exchanges that cross a Service boundary must
be fully documented in its non-proprietary Service Contract, except
direct information exchanges between constituent parts of a Service that
do not use any Platform resources.

### Service State Transition Behaviors

Note: The behaviors documented herein for Services make the assumption
that the host processing resource is in a steady-state operating
condition before a Service is instantiated.

This section defines the common definition of Service states and
transitions between the states. All Services are required to publish
periodic **ServiceStatus** messages and also report Service state in a
command/response pattern using the **ServiceStatusDataRequest** and
**ServiceStatusDataRequestStatus** messages. It is desirable to
configure the periodicity of the status reporting for each Service at
runtime through configuration. Messages and behavior for periodic
reporting, configuring the periodic update rate, and responding to a
request for status are provided in the Service Contract. If the service
configuration does not provide an initial startup value, a default value
will be used. Service states are not externally commandable via OMS
messaging.

Figure 6.1-2, Service Status State Diagram, illustrates the allowed
states and transitions for an OMS Service. Figure 6.1-3, Allowed State
Transitions for OMS Service, provides a summary of the allowed and
unallowed state transitions for an OMS Service. Table 6.1-1, OMS Service
State Definitions and Allowed Transitions, provides the normative
definition of the states and allowed transitions.

It is not a requirement for every Service to include every state on the
diagram. Nor is it a requirement to support every state to state
transition included in the diagram and table. However, when an OMS
Service includes these states and transitions, the Service will comply
with the definitions and methods in the table. An OMS Service will use
only transitions allowed in the table.

Existing legacy services adapted to OMS must map specialty states to
meet these definitions. This mapping should be documented in the Service
Contract.

The OMS Messages supported or not supported by each state should be
defined in individual Service Contracts.

<img src="media/image8.png" style="width:6.61452in;height:4.19767in" />

<span id="_Toc219290692" class="anchor"></span>Figure 6.1-2 Service
Status State Diagram

<img src="media/image9.png" style="width:4.89535in;height:5.4863in" />

<span id="_Toc219290693" class="anchor"></span>Figure 6.1-3 Allowed
State Transitions for OMS Service

<span id="_Toc219290720" class="anchor"></span>Table 6.1-1 OMS Service
State Definitions and Allowed Transitions

<table>
<thead>
<tr class="header">
<th>State</th>
<th>Definition</th>
<th>Conditions Required to Report that a Service is in this State</th>
<th>Functions Supported in this State</th>
<th>Allowed Transitions from this State</th>
<th>Allowed Triggers for the State Transition</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>INITALIZING</td>
<td>Service is starting up. Communication with ASB has begun, but Service startup is not complete (e.g., still loading configuration files). Initialization can’t complete (e.g., transition to another state) until the Service is able to send and receive OMS Messages.</td>
<td><ul>
<li><p>Connected to ASB</p></li>
<li><p>Can send OMS Messages</p></li>
</ul></td>
<td><ul>
<li><p>Network connection to ASB</p></li>
<li><p>Can send OMS Messages</p></li>
<li><p>May receive OMS Messages</p></li>
<li><p>Can perform Data Transfers</p></li>
<li><p>Initialization functions, including software loading, mission load processing, and loading configuration files</p></li>
<li><p>May establish secure communications</p></li>
<li><p>Commands accepted and status provided are defined in the Service Contract</p></li>
</ul></td>
<td>NORMAL</td>
<td>Automatic – occurs after initialization is complete</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic – occurs when conditions indicate Service is not fully operational</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PAUSED</td>
<td>Automatic – occurs after initialization is complete but not ready for its NORMAL state transition</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INOPERABLE</td>
<td><p>Upon receipt of <strong>ServiceLifecycleCommand</strong>(STOP)</p>
<p>-or-</p>
<p>Automatic - occurs when conditions indicate Service is not operational (e.g., issue with configuration files)</p></td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td>NORMAL</td>
<td>Service is functioning normally. Configuration files loaded. All functions can now be used.</td>
<td><ul>
<li><p>Connected to ASB</p></li>
<li><p>Can send OMS Messages</p></li>
</ul></td>
<td><ul>
<li><p>Network connection to ASB</p></li>
<li><p>Can send OMS Messages</p></li>
<li><p>May receive OMS messages</p></li>
<li><p>Can perform Data Transfer</p></li>
<li><p>Can perform defined Service functions</p></li>
<li><p>Reporting status</p></li>
<li><p>Commands accepted and status provided are defined in the Service Contract</p></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic – occurs when conditions indicate Service is not fully operational</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PAUSED</td>
<td>Upon receipt of <strong>ServiceLifecycleCommand</strong>(PAUSE)</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZING</td>
<td><p>Upon receipt of <strong>ServiceLifecycleCommand</strong>(RESTART)</p>
<p>Or</p>
<p>Automatic – occurs when conditions indicate Service requires re-initialization.</p></td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INOPERABLE</td>
<td><p>Upon receipt of <strong>ServiceLifecycleCommand</strong>(STOP)</p>
<p>-or-</p>
<p>Automatic - occurs when conditions indicate Service is not operational</p></td>
<td>Details defined in Service Contract</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th>State</th>
<th>Definition</th>
<th>Conditions Required to Report that a Service is in this State</th>
<th>Functions Supported in this State</th>
<th>Allowed Transitions from this State</th>
<th>Allowed Triggers for the State Transition</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>DEGRADED</td>
<td>Service is not functioning normally. Functions can be used, but there may be limitations. If applicable, communications with its Subsystem may be disrupted.</td>
<td><ul>
<li><p>Connected to ASB</p></li>
<li><p>Can send OMS Messages</p></li>
</ul></td>
<td><ul>
<li><p>Some defined Service functions may be available, but may not be relied upon due to degraded state of Service</p></li>
<li><p>Commands accepted and status provided are defined in the Service Contract</p></li>
</ul></td>
<td>NORMAL</td>
<td>Automatic – occurs when conditions indicate Service is back to full capacity and can perform its functions</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PAUSED</td>
<td>Upon receipt of <strong>ServiceLifecycleCommand</strong>(PAUSE)</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZING</td>
<td><p>Upon receipt of <strong>ServiceLifecycleCommand</strong>(RESTART)</p>
<p>Or</p>
<p>Automatic – occurs when conditions indicate Service requires re-initialization.</p></td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INOPERABLE</td>
<td><p>Upon receipt of <strong>ServiceLifecycleCommand</strong>(STOP)</p>
<p>-or-</p>
<p>Automatic - occurs when conditions indicate Service is not operational</p></td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td>PAUSED</td>
<td>Service is functioning properly, but has been paused (e.g., by operator interaction, because of dependency). Once resumed, the Service typically transitions back to the state it was in before it was PAUSED.</td>
<td><ul>
<li><p>Connected to ASB</p></li>
<li><p>Can send OMS Messages</p></li>
</ul></td>
<td><ul>
<li><p>Service sends at least one <strong>ServiceStatus</strong> message indicating Status=PAUSED</p></li>
<li><p>No Service functions can be performed except for those functions that can transition the Service out of its PAUSED state</p></li>
</ul></td>
<td>NORMAL</td>
<td>Upon receipt of <strong>ServiceLifecycleCommand</strong>(RESUME) and previous state was NORMAL</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZING</td>
<td>Upon receipt of <strong>ServiceLifecycleCommand</strong>(RESUME) and previous state was INITIALIZING</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Upon receipt of <strong>ServiceLifecycleCommand</strong>(RESUME) and previous state was DEGRADED</td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INOPERABLE</td>
<td><p>Upon receipt of <strong>ServiceLifecycleCommand</strong>(STOP)</p>
<p>-or-</p>
<p>Automatic - occurs when conditions indicate Service is not operational</p></td>
<td>Details defined in Service Contract</td>
</tr>
<tr class="odd">
<td>INOPERABLE</td>
<td><p>An end state where the Service is no longer capable of performing any mission functions.</p>
<p>Service is unusable. (Usually means Service is inactive.)</p></td>
<td><ul>
<li><p>Connected to ASB</p></li>
<li><p>May send OMS Messages</p></li>
</ul></td>
<td><ul>
<li><p>No functions are supported in this state</p></li>
<li><p>Does not receive or publish messages</p></li>
</ul></td>
<td>None</td>
<td>None</td>
<td>The Service may or may not be capable of sending a <strong>ServiceStatus</strong> message with INOPERABLE status prior to stopping operations, as defined in the Service Contract.</td>
</tr>
</tbody>
</table>

Note: Receipt of **ServiceLifecycleCommand**(RESET) doesn’t necessarily
cause a state change. For example, a Service in the PAUSED state can
receive a RESET command which means it resets its internal parameters
and remains in the PAUSED state. If the Service developer wishes to
publish the RESET enumeration outside of its Service (e.g., to a Service
Manager), the behavior should be documented in the Service Contract.

Subsystem
---------

A Subsystem is an OMS Architecture Element that is comprised of one or
more hardware and software components. A Subsystem provides mission
functions and/or Capabilities. A Subsystem is assessed in accordance
with a prescribed interface and predefined constraints and policies
specified by a non-proprietary Service Contract and a non-proprietary
Subsystem Description Document. Capabilities are typically tasked,
discovered, commanded, or any combination thereof, using OMS Messaging.
To ensure loose coupling, OMS follows a publish/subscribe paradigm for
OMS Messaging abstracted by the CAL. The knowledge of OMS Messages for a
Subsystem is limited to publishing and subscribing via topics.
Therefore, a Subsystem will focus on OMS Messages rather than source or
destination.

A Subsystem is not required to host or present a Service. An Isolator
cannot be an OMS Subsystem. Most Subsystems will operate solely using a
Subsystem State lifecycle and will not run on the Service lifecycle. An
OMS Subsystem will typically aggregate status on the hardware and
software components contained in that Subsystem. All Subsystems are
required to publish periodic **SubsystemStatus** messages and also
report Subsystem state in a command/response pattern using the
**SubsystemStatusDataRequest** and **SubsystemStatusDataRequestStatus**
messages. If Subsystems manage their own service lifecycles (i.e., their
internal software components are not uniquely visible to the rest of the
system), they may report status at an aggregate level (i.e., at the
Subsystem level). In addition, Subsystems must use one of the time
synchronization mechanisms provided by the Platform as outlined in
Section 6.5.5, Time Reference and Time Synchronization.

A Subsystem boundary is defined as where the Subsystem communications
(e.g., messages, data transfer, signals, etc.) enter or exit the
Subsystem. A Subsystem boundary delineates the extent of a Subsystem.
Inside the Subsystem boundary are all of the hardware and software
elements (including an Adapter) of the Subsystem to implement its
functionality and conform to OMS requirements. Outside the Subsystem
boundary are all other system elements, such as other Subsystems,
Services, and Isolators. Refer to Figure 6.2-1, Example Subsystem
showing Subsystem Boundary, for an illustration of an example Subsystem
with three constituent parts and its boundary.

<img src="media/image10.png" style="width:6.5in;height:4.03125in" />

<span id="_Toc219290694" class="anchor"></span>Figure 6.2-1 Example
Subsystem showing Subsystem Boundary

A Subsystem presents an OMS-facing interface to use OMS Data Exchanges
to interact with other OMS elements via the Platform ASB. If an Adapter
is included in the Subsystem to provide adaptation software and/or
hardware to support OMS Data Exchanges, then that Adapter is considered
a part of the Subsystem. An Adapter can operate on the Subsystem
hardware or in the Platform’s OCE or Other Mission Processing hardware.

A Platform-hosted Adapter is formally part of the Subsystem. Thus, the
Adapter to legacy subsystem interface (non-OMS-facing side) is an
internal Subsystem interface, but because of Adapter hosting
requirements, it is important for the Integrator to know about this
interface. Since the Adapter runs on non-subsystem hardware (possibly
the OCE), the launch and management of this software is very similar to
how Services are managed. The Adapter has no functionality on its own.
It requires the legacy subsystem to be operational to meet the
Subsystem’s Capabilities documented in its Service Contract. If a
Platform-hosted Adapter exists, it may publish the **SubsystemStatus**
message when the Subsystem is unable to report. Instances in which the
Adapter will publish the **SubsystemStatus** message on behalf of the
Subsystem are off, not installed, or unknown.

When a Subsystem uses Platform resources (e.g., an OCE, Other Mission
Processing, data storage), the resource requirements needed by the
Subsystem must be documented in the appropriate OMS documentation (i.e.,
Service Contract and/or SDD). This includes any use of the Platform ASB
hardware to exchange information between constituent parts of the
Subsystem, such as CPU and memory required for the Adapter, and network
bandwidth required for exchange of information between the Adapter and
the legacy subsystem. However, the format of the data exchanged between
the Adapter and the legacy subsystem does not need to be documented,
since it is a direct information exchange between constituent parts of
the Subsystem.

If a Subsystem physically hosts an OCE implementation for use by a
Platform, the OCE is considered part of the Platform and not part of the
logical Subsystem. Services running in that OCE are not within the
boundary of the logical Subsystem because the Services must run
independently of the physical Subsystem since they should also be able
to be run in any Platform-provided OCE without change. An Isolator is
not allowed to be hosted in an OMS Subsystem unless it is specifically
hosted in the OCE provided by the physical Subsystem. For example, a
Service with no ties to the Subsystem Capabilities, running in the OCE
provided by the physical Subsystem, will not be viewed as operating
within the boundary of the logical Subsystem. When an OCE is provided by
the physical Subsystem, the OCE specifications should be documented in
the Subsystem’s SDD.

In summary, all information exchanges that cross a Subsystem boundary
must be fully documented in the appropriate non-proprietary OMS
documentation (i.e., Service Contract or SDD), except direct information
exchanges between constituent parts of a Subsystem that do not use any
Platform resources.

### Subsystem State Transition Behaviors

This section defines the common definition of Subsystem operational
states, common triggers to transition between the states, and common
messages and definitions to report the status of the Subsystem state for
all OMS-compliant Subsystems.

Figure 6.2-2, Subsystem State Diagram, illustrates the allowed states
and transitions for an OMS Subsystem.

Figure 6.2-3, Allowed State Transitions for OMS Subsystem, provides a
summary of the allowed and unallowed state transitions for an OMS
Subsystem. Table 6.2-1, OMS Subsystem State Definitions and Allowed
Transitions, provides the normative definition of the states and
transitions.

It is not a requirement for every Subsystem to include every state on
the diagram. Nor is it a requirement to support every state-to-state
transition included in the diagram and table. A Subsystem will
automatically pass through any unused state to the next allowable
supported state. However, when an OMS Subsystem includes these states
and transitions, the Subsystem will comply with the definitions and
methods in the table and report those states in the **SubsystemStatus**
message as documented in the Service Contract. An OMS Subsystem will use
only transitions allowed in the table, including all modifications
resulting from the removal of unused states. There is an exception where
a Subsystem may transition to a state marked as “unallowed” if an
unexpected error or fault condition occurred. Note that SHUTDOWN is a
terminal state – no transition out of SHUTDOWN is allowed without
recycling power.

Existing legacy subsystems which are adapted to OMS must map specialty
states to meet these definitions. For example, a “Reload Mission Data
File” state can be considered as a form of INITIALIZATION, rather than a
separate state.

Note that the transitions to CALIBRATION and INITIATED\_BIT states are
only allowed with the state change commands. Subsystems which support
calibration and initiated BIT functions while in an OPERATE state can
use calibration and IBIT commands, without the state change command.

The OMS Messages supported and not supported by each state should be
defined in individual Service Contracts.

Note that the OMS Message Set uses the same state enumeration definition
in both uci:**SubsystemStateCommand** and uci:**SubsystemStatus**.
However, some of these command enumerations are not allowed in
uci:**SubsystemStateCommand** based on the allowed transitions in Figure
6.2-2, Subsystem State Diagram.

The allowed state transitions are defined for normal operations only.
Subsystem responses to fault conditions may invoke transitions not shown
in the figure and table. For example, a failure to successfully load a
Mission Data File (MDF) or communications waveform may move the
subsystem from INITIALIZATION back to PRE\_INITIALIZATION.

<img src="media/image11.png" style="width:7.68605in;height:5.43539in" />

<span id="_Toc219290695" class="anchor"></span>Figure 6.2-2 Subsystem
State Diagram

<img src="media/image12.png" style="width:6.5in;height:6.5in" />

<span id="_Toc219290696" class="anchor"></span>Figure 6.2-3 Allowed
State Transitions for OMS Subsystem

<span id="_Toc219290721" class="anchor"></span>Table 6.2-1 OMS Subsystem
State Definitions and Allowed Transitions

<table>
<thead>
<tr class="header">
<th>State</th>
<th>Definition</th>
<th>Conditions Required to Report that a Subsystem is in this State</th>
<th>Functions Supported in this State</th>
<th>Allowed Transitions from this State</th>
<th>Allowed Triggers for the State Transition</th>
<th>Notes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Unpowered</td>
<td>No electrical power is applied</td>
<td>N/A</td>
<td><ul>
<li><p>None - Inactive</p></li>
</ul></td>
<td>OFF</td>
<td>Application of Prime Power</td>
<td>Reporting of this state via messaging is not required</td>
</tr>
<tr class="even">
<td>OFF</td>
<td>Power is applied, but the Subsystem is not turned on</td>
<td>N/A</td>
<td><ul>
<li><p>None - Inactive</p></li>
</ul></td>
<td>Unpowered</td>
<td>Removal of Prime Power</td>
<td>Reporting of this state via messaging is not required. Per the Subsystem’s Service Contract, the Platform-hosted Adapter may report this state on behalf of the Subsystem. A Subsystem enters OFF when Prime Power is applied.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PRE_INITIALIZATION</td>
<td>Manual operation of an ON/OFF switch or receipt of a special signal to turn ON</td>
<td></td>
</tr>
<tr class="even">
<td>PRE_INITIALIZATION</td>
<td>The state where the Subsystem performs its Bootstrap and initial SW load processing.</td>
<td><ul>
<li><p>Power is applied</p></li>
<li><p>Messaging is available at a minimum level</p></li>
</ul></td>
<td><ul>
<li><p>Initial bootstrap</p></li>
<li><p>SW loading</p></li>
<li><p>Program Protection functions supporting initial SW loading</p></li>
</ul></td>
<td>INITIALIZATION</td>
<td>Automatic</td>
<td>A message-based transition out of a faulted PRE_INITIALIZATION state will be allowed if defined in the Service Contract.</td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>State</strong></th>
<th><strong>Definition</strong></th>
<th><strong>Conditions Required to Report that a Subsystem is in this State</strong></th>
<th><strong>Functions Supported in this State</strong></th>
<th><strong>Allowed Transitions from this State</strong></th>
<th><strong>Allowed Triggers for the State Transition</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>INITIALIZATION</td>
<td>The state where the Subsystem performs its Subsystem initialization and mission load processing.</td>
<td><ul>
<li><p>Pre-Initialization processing complete.</p></li>
</ul></td>
<td><ul>
<li><p>Initialization functions including memory sanitization</p></li>
<li><p>Mission load processing</p></li>
<li><p>Load configuration files</p></li>
<li><p>Startup Built-In Test (BIT)</p></li>
<li><p>Discover dependent Services</p></li>
<li><p>Establishes secure communications as needed</p></li>
<li><p>The commands that are accepted and status provided will be defined in the Service Contract.</p></li>
<li><p>May include capabilities publishing</p></li>
<li><p>May include a low power state</p></li>
<li><p>Program Protection functions associated with configuration and mission load file access</p></li>
<li><p>Program Protection functions supporting transition to Operational States (STANDBY, OPERATE*, CALIBRATION, MAINTENANCE, INITIATED_BIT)</p></li>
<li><p>Program Protection functions associated with transition to SHUTDOWN</p></li>
</ul></td>
<td>STANDBY</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(STANDBY)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>SHUTDOWN</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(SHUTDOWN)</td>
<td>Can be used if the system fails to properly initiate.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic</td>
<td></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>State</strong></th>
<th><strong>Definition</strong></th>
<th><strong>Conditions Required to Report that a Subsystem is in this State</strong></th>
<th><strong>Functions Supported in this State</strong></th>
<th><strong>Allowed Transitions from this State</strong></th>
<th><strong>Allowed Triggers for the State Transition</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>STANDBY</td>
<td>The state where the Subsystem is ready to transition to an Operational state (STANDBY, OPERATE*, CALIBRATION, MAINTENANCE, INITIATED_BIT).</td>
<td><ul>
<li><p>Initialization and Mission load processing completed</p></li>
<li><p>Startup BIT results reported</p></li>
<li><p>Fully ready to receive and execute operate commands</p></li>
</ul></td>
<td><ul>
<li><p>Reporting status and health</p></li>
<li><p>The commands that are accepted, and status provided, will be defined in the Service Contract.</p></li>
<li><p>May accept configuration and capability enabling commands in anticipation of an OPERATE* command</p></li>
<li><p>Cannot transmit or receive signals</p></li>
<li><p>May include a low power condition</p></li>
<li><p>Periodic BIT</p></li>
<li><p>Program Protection functions supporting maintenance of protection</p></li>
<li><p>Program Protection functions supporting enabling of additional operational capabilities</p></li>
<li><p>Program Protection functions associated with transition to SHUTDOWN</p></li>
</ul></td>
<td>OPERATE*</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(OPERATE*)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td><strong>I</strong>NITIATED_BIT</td>
<td><strong>SubsystemStateCommand</strong>(INITIATED_BIT)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>CALIBRATION</td>
<td><strong>SubsystemStateCommand</strong>(CALIBRATION)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>MAINTENANCE</td>
<td><strong>SubsystemStateCommand</strong>(MAINTENANCE)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PRE_INITIALIZATION</td>
<td><strong>SubsystemStateCommand</strong>(PRE_INITIALIZATION)</td>
<td>Equivalent to a RESET command</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZATION</td>
<td>Any command which requires a return to INITIALIZATION to execute, such as reloading Mission Data Files (MDFs)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>SHUTDOWN</td>
<td><strong>SubsystemStateCommand</strong>(SHUTDOWN), or induced by other commands or automated functions.</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic</td>
<td></td>
</tr>
<tr class="odd">
<td>OPERATE*</td>
<td>The state where the Subsystem performs its primary mission functions</td>
<td><ul>
<li><p>Performing the specified operating functions, capabilities and activities</p></li>
<li><p>Ready for subsequent state and other C2 commands</p></li>
</ul></td>
<td><ul>
<li><p>Per the specification and Service Contract</p></li>
<li><p>Program Protection functions supporting maintenance of protection</p></li>
<li><p>Program Protection functions supporting enabling of additional operational capabilities</p></li>
<li><p>Program Protection functions associated with transition to SHUTDOWN</p></li>
</ul></td>
<td>STANDBY</td>
<td><strong>SubsystemStateCommand</strong>(STANDBY)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>OPERATE*</td>
<td>To be defined in the Service Contract</td>
<td>Transitions between the various OPERATE* substates are defined in the Service Contract.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIATED_BIT</td>
<td><strong>SubsystemStateCommand</strong>(INITIATED_BIT)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>CALIBRATION</td>
<td><strong>SubsystemStateCommand</strong>(CALIBRATION)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>MAINTENANCE</td>
<td><strong>SubsystemStateCommand</strong>(MAINTENANCE)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PRE_INITIALIZATION</td>
<td><strong>SubsystemStateCommand</strong>(PRE_INITIALIZATION)</td>
<td>Equivalent to a RESET command</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZATION</td>
<td>Any command which requires a return to INITIALIZATION to execute, such as reloading Mission Data Files (MDFs)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>SHUTDOWN</td>
<td><strong>SubsystemStateCommand</strong>(SHUTDOWN), or induced by other commands or automated functions.</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic</td>
<td></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>State</strong></th>
<th><strong>Definition</strong></th>
<th><strong>Conditions Required to Report that a Subsystem is in this State</strong></th>
<th><strong>Functions Supported in this State</strong></th>
<th><strong>Allowed Transitions from this State</strong></th>
<th><strong>Allowed Triggers for the State Transition</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>INITIATED_BIT</td>
<td>A separate testing state to perform initiated built in tests</td>
<td><ul>
<li><p>Initiated BIT testing begun and still in process</p></li>
</ul></td>
<td><ul>
<li><p>Per the specification and Service Contract.</p></li>
<li><p>Typically does not include execution of any mission functions</p></li>
<li><p>Program Protection functions supporting maintenance of protection</p></li>
<li><p>Program Protection functions supporting enabling of additional operational capabilities</p></li>
<li><p>Program Protection functions associated with transition to SHUTDOWN</p></li>
</ul></td>
<td>STANDBY</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(STANDBY)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>OPERATE*</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(OPERATE*)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>CALIBRATION</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(CALIBRATION)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>MAINTENANCE</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(MAINTENANCE)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PRE_INITIALIZATION</td>
<td><strong>SubsystemStateCommand</strong>(PRE_INITIALIZATION)</td>
<td>Equivalent to a RESET command</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZATION</td>
<td>Any command which requires a return to INITIALIZATION to execute, such as reloading Mission Data Files (MDFs)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>SHUTDOWN</td>
<td><strong>SubsystemStateCommand</strong>(SHUTDOWN), or induced by other commands or automated functions.</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic</td>
<td></td>
</tr>
<tr class="odd">
<td>CALIBRATION</td>
<td>A separate state to perform a calibration which cannot be done while in a normal operating state</td>
<td><ul>
<li><p>Calibration testing begun and still in process</p></li>
</ul></td>
<td><ul>
<li><p>Per the specification and Service Contract.</p></li>
<li><p>Typically does not include execution of any mission functions</p></li>
<li><p>Program Protection functions supporting maintenance of protection</p></li>
<li><p>Program Protection functions supporting enabling of additional operational capabilities</p></li>
<li><p>Program Protection functions associated with transition to SHUTDOWN</p></li>
</ul></td>
<td>STANDBY</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(STANDBY)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>OPERATE*</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(OPERATE*)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIATED_BIT</td>
<td><p>Automatic or upon receipt of</p>
<p><strong>SubsystemStateCommand</strong>(INITIATED_BIT)</p></td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>MAINTENANCE</td>
<td>Automatic or upon receipt of <strong>SubsystemStateCommand</strong>(MAINTENANCE)</td>
<td>Auto vs. commanded transition will be defined in the Service Contract.</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PRE_INITIALIZATION</td>
<td><strong>SubsystemStateCommand</strong>(PRE_INITIALIZATION)</td>
<td>Equivalent to a RESET command</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZATION</td>
<td>Any command which requires a return to INITIALIZATION to execute, such as reloading Mission Data Files (MDFs)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>SHUTDOWN</td>
<td><strong>SubsystemStateCommand</strong>(SHUTDOWN), or induced by other commands or automated functions.</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>DEGRADED</td>
<td>Automatic</td>
<td></td>
</tr>
<tr class="odd">
<td>MAINTENANCE</td>
<td>A state where dedicated maintenance functions can be performed in an operational environment</td>
<td><ul>
<li><p>Maintenance functions started</p></li>
</ul></td>
<td><ul>
<li><p>None required</p></li>
</ul></td>
<td>To be defined in the Service Contract</td>
<td>To be defined in the Service Contract</td>
<td></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th><strong>State</strong></th>
<th><strong>Definition</strong></th>
<th><strong>Conditions Required to Report that a Subsystem is in this State</strong></th>
<th><strong>Functions Supported in this State</strong></th>
<th><strong>Allowed Transitions from this State</strong></th>
<th><strong>Allowed Triggers for the State Transition</strong></th>
<th><strong>Notes</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>SHUTDOWN</td>
<td>An end state where the Subsystem is no longer capable of performing any mission functions.</td>
<td><ul>
<li><p>Shutdown complete</p></li>
</ul></td>
<td><ul>
<li><p>Shutdown processing is defined in the Service Contract.</p></li>
<li><p>Typically accepts no other commands nor provides status after reporting <strong>SubsystemStatus</strong> (State=SHUTDOWN)</p></li>
</ul></td>
<td>None</td>
<td>None</td>
<td>The Subsystem may or may not be required to send a message with SHUTDOWN status prior to stopping operations, as defined in the Service Contract.</td>
</tr>
<tr class="even">
<td>NOT_INSTALLED</td>
<td>The Subsystem is not currently installed in the platform.</td>
<td>N/A</td>
<td><ul>
<li><p>None - Inactive</p></li>
</ul></td>
<td>N/A</td>
<td>N/A</td>
<td><p>This enumeration is included to support system-level status reporting, and is not expected to be reported by a Subsystem.</p>
<p>Installation status of individual components can be reported using <strong>ComponentState</strong>.</p></td>
</tr>
<tr class="odd">
<td>DEGRADED</td>
<td><p>A Subsystem is considered degraded when a non-critical anomaly is encountered restricting the Subsystem from performing the mission in its entirety but is still able to perform at least one use case within the mission. The following is a non-exhaustive list of examples that could cause a Subsystem to enter a DEGRADED state:</p>
<ul>
<li><p>Redundant component failed Subsystem is still operational.</p></li>
<li><p>Decline in quality of service and/or functionality.</p></li>
<li><p>Mismatch of discretes.</p></li>
<li><p>Subset of components has failed however; some functionality is still available.</p></li>
</ul>
<p>DEGRADED is a non-command-able state, instead, a Subsystem enters a DEGRADED state automatically. Reference the Subsystem state transition matrix and Subsystem’s Service Contract.</p></td>
<td><ul>
<li><p>Subsystem automatically transitioned into a DEGRADED state</p></li>
</ul></td>
<td><ul>
<li><p>Per the specification and Service Contract</p></li>
<li><p>Program Protection functions associated with transition to SHUTDOWN</p></li>
<li><p>Program Protection functions supporting enabling of additional operational capabilities</p></li>
<li><p>Program Protection functions supporting maintenance of protection</p></li>
<li><p>Reporting status and health</p></li>
<li><p>Periodic BIT</p></li>
</ul></td>
<td>OPERATE*</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(OPERATE*)</td>
<td>Reference the Subsystem’s Service Contract for additional details and/or requirements on transitioning out of DEGRADED to OPERATE*.</td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>STANDBY</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(STANDBY)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIATED_BIT</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(INITIATED_BIT)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>CALIBRATION</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(CALIBRATION)</td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>MAINTENANCE</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(MAINTENANCE)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>PRE_INITIALIZATION</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(PRE_INITIALIZATION)</td>
<td>Equivalent to a RESET command</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>INITIALIZATION</td>
<td>Any command which requires a return to INITIALIZATION to execute, such as reloading Mission Data Files (MDFs)</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td><ul>
<li></li>
</ul></td>
<td><ul>
<li></li>
</ul></td>
<td>SHUTDOWN</td>
<td>Upon receipt of <strong>SubsystemStateCommand</strong>(SHUTDOWN)</td>
<td></td>
</tr>
</tbody>
</table>

Note: Any state will transition to an unpowered state when power is
removed.

Note: **OPERATE**\* represents any of the Operate states: **OPERATE**,
**OPERATE\_RX\_ONLY**, or **OPERATE\_TX\_ONLY**.

### Subsystem Startup

Figures 6.2-4, 6.2-5, and 6.2-6, Notional Subsystem Startup Sequence
Examples (Parts 1, 2 and 3), depict the Subsystem startup sequence from
powering up including any pre-boot to its initial operational state.
Figure 6.2-4, Notional Subsystem Startup Sequence Example (1 of 3)
illustrates the Pre-Initialization sequence from power on to retrieving
its configuration files. Upon applying power to the Subsystem, the
Subsystem runs its Power-on Self Test, loads the bootloader file which
contains the location of the Subsystem’s initial configuration file, and
optionally performs an integrity check with the Platform. The Subsystem
now has access to file systems on the Platform. The Subsystem bootloader
has been configured with the known location of its initial configuration
file as specified in the PDD. A bootloader parameter is recommended for
this file location. Subsystem will then have the ability to access a
file system in order to pull its initial configuration file.

Upon receiving its initial configuration file from the file system, the
Subsystem may optionally perform authentication, decryption, or security
audit processing on the newly acquired initial configuration file.

In Figure 6.2-5 Notional Subsystem Startup Sequence Example (2 of 3) the
Subsystem parses the initial configuration file. A Subsystem’s initial
configuration file is created by the Subsystem a priori, where it must
contain at least its service identifier (used to initialize the CAL),
and may contain one or more of the following items: software application
version, software application file location(s), Mission Data File (MDF)
location(s), other file locations, etc.

If the Subsystem does not possess a resident software application, it
must obtain its location from its initial configuration file and then
retrieve its application from the file system.

The Subsystem may then optionally perform authentication, decryption, or
security audit processing on its software whether it was resident or
newly acquired. The Subsystem loads its software application, and then
initializes its CAL with its known service identifier string.

Figure 6.2-6 Notional Subsystem Startup Sequence Example (3 of 3)
continues with the transition to the INITIALIZATION state. Once the CAL
is running, the Subsystem transitions out of its PRE\_INITIALIZATION
state into its INITIALIZATION state. If operating normally,
communications to the Platform begin with **SubsystemStatus**,
**ServiceStatus** (optional), and **SubsystemConfiguration** (optional)
messages. These messages will be sent periodically and/or upon message
content change until the Subsystem shuts down. Note that individual
message rates may vary. The Subsystem may optionally report status of
**SubsystemBIT\_Status** before and after running Start-Up BIT.

The Subsystem may then optionally retrieve its MDFs and other files from
the file system. There are three options for obtaining these files:

1\. MDF file location(s) stored in the Subsystem’s initial configuration
file.

2\. The Platform sends an unsolicited **FileLocation** message to the
Subsystem with the location of the MDF(s).

3\. The Subsystem sends **QueryDataRequest** messages with
**FileLocation** message as a parameter. In response, the Subsystem
receives **FileLocation** messages, which contain the names and
locations of MDF(s) and other files, as applicable.

Once an MDF location is known, the Subsystem retrieves the MDF from the
file system using one of the allowed data transfer protocols. The
Subsystem may then perform any combination of authentication,
decryption, or security audit processing on the newly acquired MDF.

The PDD will include the relative root directory locations for all of
the Subsystems on the Platform. The SDD will include the Subsystem’s
directory file structure for its initial configuration file, OFP(s) (if
applicable), MDF(s), and security file(s) that will exist at its
assigned relative root. Upon completion of loading the MDF or other
files, the Subsystem is in its STANDBY or OPERATE\* state and is ready
to be commanded in accordance with a Service Contract.

<img src="media/image13.png" style="width:7.12416in;height:5.66279in" />

<span id="_Toc219290697" class="anchor"></span>Figure 6.2-4 Notional
Subsystem Startup Sequence Example (1 of 3)

<img src="media/image14.png" style="width:8.74553in;height:5.80233in" />

<span id="_Toc219290698" class="anchor"></span>Figure 6.2-5 Notional
Subsystem Startup Sequence Example (2 of 3)

<img src="media/image15.png" style="width:6.96503in;height:5.84884in" />

<span id="_Toc219290699" class="anchor"></span>Figure 6.2-6 Notional
Subsystem Startup Sequence Example (3 of 3)

### Subsystem Erase

A Subsystem may be capable of performing erase processing while staying
in one of its Operational states, independent of shutdown processing. In
this case, the Subsystem would receive a **SubsystemEraseCommand** to
perform specific erase processing and would remain in its Operational
state while accomplishing this command. Thus, the
**SubsystemEraseCommand** should not be used to transition the Subsystem
to another state. For those Subsystems that require a state transition
to SHUTDOWN to perform its erase processing, please refer to Section
6.2.4, Subsystem Shutdown.

The definitions pertaining to Subsystem erase processing are listed in
Section 6.2.3.1, Definitions of Specific Erase Processes. The Erase
Processing scenario showing proper Subsystem erase processing
independent of Subsystem shutdown is defined in Section 6.2.3.2,
Subsystem Erase Processing Staying in Operational State.

#### Definitions of Specific Erase Processes

The following definitions apply to the CommandType field enumerations
used in the **SubsystemEraseCommand**, and the EraseParameter field
enumerations used in the **SubsystemStateCommand** message:

-   CLASSIFIED\_DATA\_ERASE – Removes all classified data created during
    Subsystem operation, returning “the subsystem to its
    default/native/base classification level”. Depending on a
    Subsystem’s design, the Classified Data Erase (CDE) process can be
    commanded as a part of the Subsystem shutdown command (likely the
    normal use), or could be invoked during normal Subsystem operation.
    A Subsystem will document its support for CLASSIFIED\_DATA\_ERASE in
    its SDD and/or Service Contract. Restoring power to a Subsystem
    shutdown with CDE restarts the Subsystem to normal operation. See
    also potentially related terms: ZEROIZE and DISABLE

-   ZEROIZE – Overwrites cryptographic keys and associated classified
    data in a Subsystem with zeros. Requires organizational maintenance
    to reload keys. Depending on the chosen interpretation of the term
    “and associated classified data,” the ZEROIZE by itself (i.e.,
    without CDE) may either be interpreted to remove all classified data
    and return the Subsystem to its default classification level or
    remove only the portion of the classified data “associated” with the
    crypto data (and may not, in that case, return the Subsystem to its
    base classification level). In this second interpretation, CDE
    processing should be combined with ZEROIZE (See CDE\_AND\_ZEROIZE).
    In either case, an organizational maintenance action will be
    required to enable the Subsystem to return to normal operation. A
    Subsystem will document its support for ZEROIZE in its SDD and/or
    Service Contract. See also potentially related terms:
    CLASSIFIED\_DATA\_ERASE and DISABLE

-   CDE\_AND\_ZEROIZE – Used to perform both CDE and ZEROIZE erase
    processing in a Subsystem. See CLASSIFIED\_DATA\_ERASE and ZEROIZE
    definitions

-   DISABLE – Invokes Subsystem-specific action requiring Original
    Equipment Manufacturer (OEM) or depot level maintenance to return
    the Subsystem to normal operation. DISABLE optionally may be
    interpreted to include the actions of ZEROIZE and
    CLASSIFIED\_DATA\_ERASE. If it does not, it could be required to
    invoke CLASSIFIED\_DATA\_ERASE and/or ZEROIZE in addition to DISABLE
    in order to address all classified data. A Subsystem will document
    its support for DISABLE in its SDD and/or Service Contract. See also
    potentially related terms: CLASSIFIED\_DATA\_ERASE and ZEROIZE.

#### Subsystem Erase Processing While Staying in an Operational State

In this scenario, the Subsystem is operating in one of its operational
states (i.e., STANDBY, OPERATE, OPERATE\_TX\_ONLY, OPERATE\_RX\_ONLY,
INITIATED\_BIT, CALIBRATION, MAINTENANCE, or DEGRADED) and erase
processing is commanded. The Subsystem remains in its current
operational state while performing erase processing. Figure 6.2-7,
Subsystem Erase Processing While Staying in OPERATE State Message
Sequence Example, shows the case where the Subsystem is in its OPERATE
state when commanded to perform erase processing.

1\. The Subsystem receives a **SubsystemEraseCommand** via the Platform
with CommandType set to one of its valid enumerations
(CLASSIFIED\_DATA\_ERASE, ZEROIZE, DISABLE, or CDE\_AND\_ZEROIZE).

2\. The Subsystem responds with **SubsystemEraseCommandStatus**
accepting the command and begins its commanded erase processing.

3\. The Subsystem remains in an Operational state while performing its
erase processing and periodically reports EraseStatus=PROCESSING in the
**SubsystemStatus** message until erase processing is complete.

4\. Once erase processing is complete, the Subsystem sends another
**SubsystemStatus** with EraseStatus=COMPLETED.

<img src="media/image16.png" style="width:7.29312in;height:4.54651in" />

<span id="_Toc219290700" class="anchor"></span>Figure 6.2-7 Subsystem
Erase Processing While Staying in OPERATE State Message Sequence Example

### Subsystem Shutdown

A Subsystem is commanded into a terminal shutdown condition to safely
power off the Subsystem. Upon receiving a command to shutdown, the
subsystem halts all processes, stops sending out status, and closes all
active connections to the ASB. Local logging and auditing functions may
continue where feasible. As there is no recovery method following a
command to shutdown, a power cycle is required.

Upon receiving a **SubsystemStateCommand** to transition to its SHUTDOWN
state, the Subsystem can be optionally tasked with performing other
security related functions that are to be performed before transitioning
to the SHUTDOWN state. Subsystem Shutdown processing can occur with or
without erase processing.

After a Subsystem completes CDE processing during shutdown and power is
removed, the Subsystem is rendered to its default/native/base
classification level and can usually resume normal processing when power
is reapplied without maintenance or intervention.

After a Subsystem completes Zeroize processing during shutdown and power
is removed, the Subsystem may require maintenance action or intervention
before normal processing can be resumed. Subsystem Shutdown behavior
with regard to applicable erase processing and the final state of the
Subsystem following shutdown processing should be explicitly defined in
the Service Contract and possibly the SDD.

Note that a Subsystem can also be commanded to perform erase processing
independent of its shutdown process using the **SubsystemEraseCommand**,
as described in Section 6.2.3, Subsystem Erase. This command should not
be used to transition a Subsystem into its SHUTDOWN state.

The rules pertaining to proper Subsystem Shutdown are listed in the
following section. Subsequent sections include scenarios showing proper
Subsystem Shutdown without erase processing (Case 1a and Case 1b) and
proper Subsystem Shutdown with erase processing (Case 2a and Case 2b).

####  Rules Pertaining to Proper Subsystem Shutdown

The following rules pertain to proper Subsystem Shutdown processing:

1\. It is recommended, but not required, to first command a Subsystem
operating in one of its Operational states to transition to its STANDBY
state before sending the **SubsystemStateCommand**(SHUTDOWN) to the
Subsystem to transition to its SHUTDOWN state.

2\. When a Subsystem is operating in one of its Operational states and
is commanded to transition to its SHUTDOWN state, the Subsystem may
transition to its STANDBY state and remain in its STANDBY state,
periodically reporting STANDBY as its current state (along with
indicators that shutdown processing is active and optionally erase
processing is active) in the **SubsystemStatus** message until shutdown
processing is complete.

3\. The SHUTDOWN state is a terminal state, therefore a Subsystem should
only report its CurrentState=SHUTDOWN in the **SubsystemStatus** message
once and only once after shutdown processing is complete.

4\. Once a Subsystem transitions to the SHUTDOWN state, at minimum, its
power must be recycled. Additional maintenance may be required for the
Subsystem to be operational again if any destructive
CLASSIFIED\_DATA\_ERASE or ZEROIZE functions were performed during
shutdown processing.

5\. **ServiceStatus** reports the status of the OMS Service associated
with the OMS Subsystem and **SubsystemStatus** reports the state of the
OMS Subsystem. Therefore, Platform-hosted and Subsystem-hosted Adapters
may self-terminate or continue reporting **ServiceStatus** after its
associated Subsystem shuts down.

#### Case 1a: Subsystem Shutdown Processing without Erase from OPERATE State

In this scenario, Subsystem is operating in its OPERATE state and
shutdown processing is commanded without erase processing, as shown in
Figure 6.2-8, Case 1a: Subsystem Shutdown Processing without Erase from
OPERATE State Message Sequence Example.

1\. The Subsystem receives a **SubsystemStateCommand** via the Platform
with CommandedState=SHUTDOWN.

2\. The Subsystem responds with a **SubsystemStateCommandStatus**
message accepting the command and begins its shutdown processing.

3\. The Subsystem remains in its OPERATE state while performing its
shutdown processing and periodically reporting OPERATE as its current
state (along with indicator that shutdown processing is active) in the
**SubsystemStatus** message until shutdown processing is complete.

4\. Once shutdown processing is complete, the Subsystem sends its final
**SubsystemStatus** with SubsystemState=SHUTDOWN.

<img src="media/image17.png" style="width:6.5in;height:5.71875in" />

<span id="_Toc219290701" class="anchor"></span>Figure 6.2-8 Case 1a:
Subsystem Shutdown Processing without Erase from OPERATE State Message
Sequence Example

#### Case 1b: Subsystem Shutdown Processing without Erase from Any State Except OPERATE

In this scenario, the Subsystem is in any state except OPERATE and
shutdown processing is commanded without erase processing, as shown in
Figure 6.2-9, Case 1b: Subsystem Shutdown Processing without Erase from
Any State Except OPERATE Message Sequence Example.

1\. The Subsystem receives a **SubsystemStateCommand** via the Platform
with CommandedState=SHUTDOWN.

2\. The Subsystem responds with a **SubsystemStateCommandStatus**
message accepting the command, stays in its current state, and begins
its shutdown processing.

3\. The Subsystem remains in its current state while performing its
shutdown processing and periodically reporting as its current state
(along with indicator that shutdown processing is active) in the
**SubsystemStatus** message until shutdown processing is complete.

4\. Once shutdown processing is complete, the Subsystem sends its final
**SubsystemStatus** with SubsystemState=SHUTDOWN.

<img src="media/image18.png" style="width:6.2907in;height:4.8894in" />

<span id="_Toc219290702" class="anchor"></span>Figure 6.2-9 Case 1b:
Subsystem Shutdown Processing without Erase from Any State Except
OPERATE Message Sequence Example

#### Case 2a: Subsystem Shutdown Processing with Erase from OPERATE State

In this scenario, the Subsystem is operating in its OPERATE state and
shutdown processing is commanded with erase processing, as shown in
Figure 6.2-10, Case 2a: Subsystem Shutdown Processing with Erase from
OPERATE State Message Sequence Example.

1\. The Subsystem receives a **SubsystemStateCommand** via the Platform
with CommandedState=SHUTDOWN with EraseParameter set to one of its valid
enumerations (CLASSIFIED\_DATA\_ERASE, ZEROIZE, DISABLE, or
CDE\_AND\_ZEROIZE).

2\. The Subsystem responds with a **SubsystemStateCommandStatus**
message accepting the command and begins its shutdown processing.

3\. The Subsystem remains in its OPERATE state while performing erase
and shutdown processing and periodically reporting OPERATE as its
current state, along with indicators that shutdown processing is active
(e.g., StateTransitionStatus=SHUTTING\_DOWN) and erase processing is
active or completed (e.g., EraseStatus=PROCESSING,
EraseStatus=COMPLETED), in the **SubsystemStatus** message until
shutdown processing is complete.

4\. Once shutdown processing is complete, the Subsystem sends its final
**SubsystemStatus** with SubsystemState=SHUTDOWN and EraseStatus=
COMPLETED.

<img src="media/image19.png" style="width:6.5in;height:6.61458in" />

<span id="_Toc219290703" class="anchor"></span>Figure 6.2-10 Case 2a:
Subsystem Shutdown Processing with Erase from OPERATE State Message
Sequence Example

#### Case 2b: Subsystem Shutdown Processing with Erase from Any State Except OPERATE

In this scenario, the Subsystem is operating in any state except OPERATE
and shutdown processing is commanded with erase processing, as shown in
Figure 6.2-11, Case 2b: Subsystem Shutdown Processing with Erase from
Any State Except OPERATE Message Sequence Example.

1\. The Subsystem receives a **SubsystemStateCommand** via the Platform
with CommandedState=SHUTDOWN with EraseParameter set to one of its valid
enumerations (CLASSIFIED\_DATA\_ERASE, ZEROIZE, DISABLE, or
CDE\_AND\_ZEROIZE).

2\. The Subsystem responds with a **SubsystemStateCommandStatus**
message accepting the command and begins its shutdown processing.

3\. The Subsystem remains in its current state while performing erase
and shutdown processing and periodically reporting its current state,
along with indicators that shutdown processing is active (e.g.,
StateTransitionStatus**=**SHUTTING\_DOWN) and erase processing is active
or completed (e.g., EraseStatus=PROCESSING, EraseStatus=COMPLETED), in
the **SubsystemStatus** message until shutdown processing is complete.

4\. Once shutdown processing is complete, the Subsystem transitions to
its SHUTDOWN state and sends its final **SubsystemStatus** with
SubsystemState=SHUTDOWN and EraseStatus=COMPLETED.

<img src="media/image20.png" style="width:6.5in;height:5.125in" />

<span id="_Toc219290704" class="anchor"></span>Figure 6.2-11 Case 2b:
Subsystem Shutdown Processing with Erase from Any State Except OPERATE
Message Sequence Example

OMS Data Exchanges
------------------

OMS Data Exchanges consist of four types: OMS Messaging, Data Transfer,
Special Signals, and Security Information Exchanges as depicted in
Figure 6.3-1, OMS Data Exchanges.

<img src="media/image21.png" style="width:6.5in;height:3.13542in" />

<span id="_Toc219290705" class="anchor"></span>Figure 6.3-1 OMS Data
Exchanges

OMS Messaging is the exchange of OMS Messages between a Subsystem,
Service, or Isolator and the Platform using a Critical Abstraction
Layer. Data Transfer and Security Information Exchanges directly
interface with the ASB’s IP switched fabric. Special Signals are
interfaces between Subsystems, Services, and the Platform that do not
easily fit into the other interface types (OMS Messaging, Data Transfer,
and Security Information Exchanges). The following sections define these
types and identify their requirements.

### OMS Messaging

OMS Messaging is the process of sending or receiving OMS Messages
between a Subsystem, Service, or Isolator and the Platform using a CAL.
A CAL is required for a Subsystem, Service, or Isolator to send an OMS
Message. A CAL is also required for a Subsystem, Service, or Isolator to
receive an OMS Message. An OMS Message is the unit of information sent
or received using an OMS CAL.

OMS promotes the use of standardized messages for message-based
exchanges between Subsystems, Services, and Isolators. OMS Messaging
uses a CAL Implementation and the OMS Message Set(s) from which the CAL
is generated. OMS Messaging primarily provides Command and Control (C2)
oriented exchanges inside of a Mission Package that coordinate key
mission functionality, technical capabilities, and operational behaviors
between a Subsystem, Service, or Isolator and the Platform.

C2 in the context of OMS is a type of information data exchange utilized
within a Mission Package to perform its mission and generate usable
products. In OMS, C2 is typically accomplished using the OMS Messaging
Data Exchange. However, data exchanges that require very low latency
performance may choose to utilize OMS Data Transfer or OMS Special
Signal Data Exchanges.

This section defines the OMS Message Set used for all operational
message exchanges. OMS Messaging is strongly recommended as the OMS Data
Exchange best suited for the purposes of commanding and controlling
Subsystems, Services, and Isolators within a Mission Package. The use of
a loosely coupled publish/subscribe paradigm for OMS Messaging improves
interoperability and portability of Subsystems, Services, and Isolators.
The knowledge of OMS Messages for a Subsystem, Service, and Isolator is
limited to publishing and subscribing to topics via the CAL. Therefore,
the Subsystems, Services, and Isolators will focus on the OMS Messages
rather than the source or destination.

An OMS Message Schema is a formal definition of OMS Messages.

The compatible OMS Message Schema for this version of the Standard is
the UCI Schema listed in Table 5.1-1, Reference Standards.

The UCI Schema is an eXtensible Markup Language (XML) 1.0 Schema
Definition (XSD) based message set. Rigorous definition of W3C XML
Schema Definition Language (XSD) 1.0 (Part 1: Structures and Part 2:
Datatypes) upon which the UCI messages are based, is referenced in Table
5.1-1, Referenced Standards.

Development of new messages, message extensions, or message
modifications must be done in accordance with the requirements and
guidance provided in OAC-SPC-001, UCI Schema Style and Design
Specification. The UCI Schema (OAC-STD-002) is the data model that
defines UCI Messages using XML Schema Definition (XSD). The XSD ‘schema’
files describe the UCI Messages.

A Non-OMS Message is a discrete unit of information exchanged in a
messaging pattern (as opposed to a Data Transfer, Special Signal, or
Security Information Exchange) that does not use an OMS CAL. The use of
Non-OMS Messages are not allowed. Any Subsystem, Service, or Isolator
using Non-OMS Messages will not be OMS compliant at any tier. If a
Non-OMS Message is used, then the Subsystem or Service is not OMS
compliant at any tier. Consider using a Data Transfer until the Non-OMS
Message can be added to a future baseline UCI Schema using an UCI Change
Request, so it will go through a CAL.

#### Message Definition

An OMS Message is a unit of information sent or received using an OMS
CAL. The content and structure of OMS Messages are defined using an XML
Schema Definition (XSD) specification that conforms to the UCI Schema
Style and Design Specification (OAC-SPC-001).

OMS Messages are primarily C2-oriented exchanges used inside of a
Mission Package to coordinate key mission functionality, technical
capabilities, and operational behaviors of the Architecture Elements
(Platform, Subsystems, Services, and Isolators).

The Subsystems, Services, and Isolators exchange OMS Messages using the
CAL Application Programming Interface (API). The over-the-wire protocol
for messages passed over the ASB is not part of this message definition.
The representation of the message that is passed across the CAL API is
defined by the OMS Message Set.

#### Approved and Unapproved OMS Messages

An Approved OMS Message is an unchanged message from the referenced UCI
Schema. An Approved OMS Message can also be a new message or
modification of an existing message that has been approved at the formal
OACWG change process. An Unapproved OMS Message is a new or changed
message from the referenced UCI Schema that has not been approved at the
formal OACWG change process. Figure 6.3-2, Determining Approved and
Unapproved OMS Messages, provides an illustration of how to determine if
an OMS Message is approved or unapproved.

<img src="media/image22.png" style="width:6.90051in;height:4.03488in" alt="Diagram AI-generated content may be incorrect." />

<span id="_Toc219290706" class="anchor"></span>Figure 6.3-2 Determining
Approved and Unapproved OMS Messages

#### OMS Message Sets for Compliance

OMS Minimum Message Sets have been created to identify the baseline
interactions required for Subsystems and Services to interoperate. OMS
Minimum Message Sets support interoperability at a common tier level for
compliance. The Tier 1 Minimum Message Set is focused on Subsystem and
Service interactions and the Tier 2 Minimum Message Set is focused on
mission level interactions. To meet a compliance qualification, any OMS
Message in a Minimum Message Set whose definition has been modified must
have the modification approved by the OACWG as defined in the OACWG
Governance Plan (i.e., An Unapproved OMS Message in a Minimum Message
Sets is not OMS compliant).

At Tier 3, all messages may apply.

#### Tier 1 Messages

##### Tier 1 Required Subsystem Message Set

The Tier 1 messages in Table 6.3-1, Tier 1 Required Subsystem Message
Set, listed below designate mandatory Subsystem messages. Mandatory, in
this context, means that if a Subsystem provides a Capability, its
corresponding set of **\*\_Capability**, **\*\_CapabilityStatus,
\*\_Command, \*\_CommandStatus,** and **\*\_Activity** messages are
typically required to be implemented for that Capability (where \*
represents a specific capability, such as, AO, EA, ESM, etc.). The
**SubsystemStatus** message is mandatory for all Subsystems.

<span id="_Toc219290722" class="anchor"></span>Table 6.3-1 Tier 1
Required Subsystem Message Set

<table>
<thead>
<tr class="header">
<th>AMTI_Activity</th>
<th>EA_Capability</th>
<th>SAR_Capability</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AMTI_Capability</td>
<td>EA_CapabilityStatus</td>
<td>SAR_CapabilityStatus</td>
</tr>
<tr class="even">
<td>AMTI_CapabilityStatus</td>
<td>EA_Command</td>
<td>SAR_Command</td>
</tr>
<tr class="odd">
<td>AMTI_Command</td>
<td>EA_CommandStatus</td>
<td>SAR_CommandStatus</td>
</tr>
<tr class="even">
<td>AMTI_CommandStatus</td>
<td>ESM_Activity</td>
<td>SMTI_Activity</td>
</tr>
<tr class="odd">
<td>AO_Activity</td>
<td>ESM_Capability</td>
<td>SMTI_Capability</td>
</tr>
<tr class="even">
<td>AO_Capability</td>
<td>ESM_CapabilityStatus</td>
<td>SMTI_CapabilityStatus</td>
</tr>
<tr class="odd">
<td>AO_CapabilityStatus</td>
<td>ESM_Command</td>
<td>SMTI_Command</td>
</tr>
<tr class="even">
<td>AO_Command</td>
<td>ESM_CommandStatus</td>
<td>SMTI_CommandStatus</td>
</tr>
<tr class="odd">
<td>AO_CommandStatus</td>
<td>PO_Activity</td>
<td>StrikeActivity</td>
</tr>
<tr class="even">
<td>COMINT_Activity</td>
<td>PO_Capability</td>
<td>StrikeCapability</td>
</tr>
<tr class="odd">
<td>COMINT_Capability</td>
<td>PO_CapabilityStatus</td>
<td>StrikeCapabilityStatus</td>
</tr>
<tr class="even">
<td>COMINT_CapabilityStatus</td>
<td>PO_Command</td>
<td>StrikeCommand</td>
</tr>
<tr class="odd">
<td>COMINT_Command</td>
<td>PO_CommandStatus</td>
<td>StrikeCommandStatus</td>
</tr>
<tr class="even">
<td>COMINT_CommandStatus</td>
<td>SAR_Activity</td>
<td>SubsystemStatus</td>
</tr>
<tr class="odd">
<td>EA_Activity</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

##### Tier 1 Minimum Message Set

The messages in Table 6.3-2, Tier 1 Minimum Message Set, are required to
be implemented if the message is applicable to the Subsystem or Service.
Tier 1 Required Subsystem Message Set messages are repeated in this list
for those Subsystems or Services that may need to treat those messages
as applicable messages. If Tier 1 Required Subsystem messages are not
repeated in this list, then Services are not required to respond to
those messages (for example, COMINT\*) even though the Tier 1 COMINT
Subsystem is capable of producing the applicable COMINT\* messages to be
OMS compliant. The term “applicable” has special meaning for OMS
compliance as defined in Section 6.

<span id="_Toc219290723" class="anchor"></span>Table 6.3-2 Tier 1
Minimum Message Set

<table>
<thead>
<tr class="header">
<th>AMTI_Activity</th>
<th>ESM_CommandStatus</th>
<th>SMTI_CapabilityStatus</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>AMTI_Capability</td>
<td>ESM_ConsentRequest</td>
<td>SMTI_Command</td>
</tr>
<tr class="even">
<td>AMTI_CapabilityStatus</td>
<td>ESM_ConsentRequestStatus</td>
<td>SMTI_CommandStatus</td>
</tr>
<tr class="odd">
<td>AMTI_Command</td>
<td>ESM_SettingsCommand</td>
<td>SMTI_SettingsCommand</td>
</tr>
<tr class="even">
<td>AMTI_CommandStatus</td>
<td>ESM_SettingsCommandStatus</td>
<td>SMTI_SettingsCommandStatus</td>
</tr>
<tr class="odd">
<td>AMTI_SettingsCommand</td>
<td>FileLocation</td>
<td>StrikeActivity</td>
</tr>
<tr class="even">
<td>AMTI_SettingsCommandStatus</td>
<td>FileMetadata</td>
<td>StrikeCapability</td>
</tr>
<tr class="odd">
<td>AO_Activity</td>
<td>NavigationReport</td>
<td>StrikeCapabilityStatus</td>
</tr>
<tr class="even">
<td>AO_Capability</td>
<td>PO_Activity</td>
<td>StrikeCommand</td>
</tr>
<tr class="odd">
<td>AO_CapabilityStatus</td>
<td>PO_Capability</td>
<td>StrikeCommandStatus</td>
</tr>
<tr class="even">
<td>AO_Command</td>
<td>PO_CapabilityStatus</td>
<td>StrikeConsentRequest</td>
</tr>
<tr class="odd">
<td>AO_CommandStatus</td>
<td>PO_Command</td>
<td>StrikeConsentRequestStatus</td>
</tr>
<tr class="even">
<td>AO_ConsentRequest</td>
<td>PO_CommandStatus</td>
<td>StrikeSettingsCommand</td>
</tr>
<tr class="odd">
<td>AO_ConsentRequestStatus</td>
<td>PO_SettingsCommand</td>
<td>StrikeSettingsCommandStatus</td>
</tr>
<tr class="even">
<td>AO_SettingsCommand</td>
<td>PO_SettingsCommandStatus</td>
<td>SubsystemEraseCommand</td>
</tr>
<tr class="odd">
<td>AO_SettingsCommandStatus</td>
<td>PositionReport</td>
<td>SubsystemEraseCommandStatus</td>
</tr>
<tr class="even">
<td>EA_Activity</td>
<td>ProductLocation</td>
<td>SubsystemSettingsCommand</td>
</tr>
<tr class="odd">
<td>EA_Capability</td>
<td>ProductMetadata</td>
<td>SubsystemSettingsCommandStatus</td>
</tr>
<tr class="even">
<td>EA_CapabilityStatus</td>
<td>SAR_Activity</td>
<td>SubsystemStateCommand</td>
</tr>
<tr class="odd">
<td>EA_Command</td>
<td>SAR_Capability</td>
<td>SubsystemStateCommandStatus</td>
</tr>
<tr class="even">
<td>EA_CommandStatus</td>
<td>SAR_CapabilityStatus</td>
<td>SubsystemStatus</td>
</tr>
<tr class="odd">
<td>EA_ConsentRequest</td>
<td>SAR_Command</td>
<td>SubsystemStatusDataRequest</td>
</tr>
<tr class="even">
<td>EA_ConsentRequestStatus</td>
<td>SAR_CommandStatus</td>
<td>SubsystemStatusDataRequestStatus</td>
</tr>
<tr class="odd">
<td>EA_SettingsCommand</td>
<td>SAR_SettingsCommand</td>
<td>SystemStatus</td>
</tr>
<tr class="even">
<td>EA_SettingsCommandStatus</td>
<td>SAR_SettingsCommandStatus</td>
<td>Task</td>
</tr>
<tr class="odd">
<td>Entity</td>
<td>ServiceStatus</td>
<td>TaskCancelCommand</td>
</tr>
<tr class="even">
<td>ESM_Activity</td>
<td>ServiceStatusDataRequest</td>
<td>TaskCancelCommandStatus</td>
</tr>
<tr class="odd">
<td>ESM_Capability</td>
<td>ServiceStatusDataRequestStatus</td>
<td>TaskCommand</td>
</tr>
<tr class="even">
<td>ESM_CapabilityStatus</td>
<td>SMTI_Activity</td>
<td>TaskCommandStatus</td>
</tr>
<tr class="odd">
<td>ESM_Command</td>
<td>SMTI_Capability</td>
<td>TaskStatus</td>
</tr>
</tbody>
</table>

#### Tier 2 Minimum Message Set

The messages in Table 6.3-3, Tier 2 Minimum Message Set, are required to
be implemented if the message is applicable to the Subsystem or Service.
The term “applicable” has special meaning for OMS compliance.
Applicability in this context is determined collaboratively by the
Subsystem/Service/Isolator provider, the Mission Package
provider/integrator, and the Government program representative.

<span id="_Toc219290724" class="anchor"></span>Table 6.3-3 Tier 2
Minimum Message Set

<table>
<thead>
<tr class="header">
<th>ActivityMetrics</th>
<th>MissionPlanCommandStatus</th>
<th>RouteActivityPlanApprovalStatus</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ActivityPlan</td>
<td>MissionPlanExecutionStatus</td>
<td>RouteActivityPlanCommand</td>
</tr>
<tr class="even">
<td>ActivityPlanApprovalStatus</td>
<td>MissionPlanMetricsReport</td>
<td>RouteActivityPlanStatus</td>
</tr>
<tr class="odd">
<td>ActivityPlanCommand</td>
<td>MissionPlanStatus</td>
<td>RouteActivityPlanExecutionStatus</td>
</tr>
<tr class="even">
<td>ActivityPlanCommandStatus</td>
<td>OrbitActivityPlan</td>
<td>RouteMetrics</td>
</tr>
<tr class="odd">
<td>ActivityPlanExecutionStatus</td>
<td>OrbitActivityPlanApprovalStatus</td>
<td>RoutePlan</td>
</tr>
<tr class="even">
<td>ActivityPlanStatus</td>
<td>OrbitActivityPlanCommand</td>
<td>RoutePlanApprovalStatus</td>
</tr>
<tr class="odd">
<td>ApprovalAuthority</td>
<td>OrbitActivityPlanCommandStatus</td>
<td>RoutePlanCommand</td>
</tr>
<tr class="even">
<td>ApprovalAuthorityRequest</td>
<td>OrbitActivityPlanExecutionStatus</td>
<td>RoutePlanCommandStatus</td>
</tr>
<tr class="odd">
<td>ApprovalAuthorityRequestStatus</td>
<td>OrbitActivityPlanStatus</td>
<td>RoutePlanExecutionStatus</td>
</tr>
<tr class="even">
<td>ApprovalPolicy</td>
<td>OrbitMetrics</td>
<td>RoutePlanStatus</td>
</tr>
<tr class="odd">
<td>ApprovalRequest</td>
<td>OrbitPlan</td>
<td>TaskExecutionApprovalStatus</td>
</tr>
<tr class="even">
<td>ApprovalRequestStatus</td>
<td>OrbitPlanApprovalStatus</td>
<td>TaskPlan</td>
</tr>
<tr class="odd">
<td>MissionPlan</td>
<td>OrbitPlanCommand</td>
<td>TaskPlanApprovalStatus</td>
</tr>
<tr class="even">
<td>MissionPlanActivationCommand</td>
<td>OrbitPlanCommandStatus</td>
<td>TaskPlanCommand</td>
</tr>
<tr class="odd">
<td>MissionPlanActivationCommandStatus</td>
<td>OrbitPlanExecutionStatus</td>
<td>TaskPlanCommandStatus</td>
</tr>
<tr class="even">
<td>MissionPlanActivationStatus</td>
<td>OrbitPlanStatus</td>
<td>TaskPlanExecutionStatus</td>
</tr>
<tr class="odd">
<td>MissionPlanApprovalStatus</td>
<td>RequirementMetrics</td>
<td>TaskPlanningStatus</td>
</tr>
<tr class="even">
<td>MissionPlanCommand</td>
<td>RouteActivityPlan</td>
<td>TaskPlanStatus</td>
</tr>
</tbody>
</table>

#### Tier 3 Message Set

A Tier 3 Message Set is an OMS Message Set where all OMS Messages are
unmodified from the applicable UCI Schema, or if modified have been
approved by the OACWG as defined in the OACWG Governance Plan (i.e., no
Unapproved OMS Messages are allowed). Achieving Tier 3 compliance
requires meeting the objective of full OMS compliance interactions and
messages implemented using OMS Data Exchanges and all the OMS
Architecture Elements being fully compliant.

### Data Transfer

OMS Data Transfer defines a set of allowed protocols and data formats to
move various types of data between Subsystems, Services, Isolators, and
storage devices within a Mission Package. OMS Data Transfer is based on
standardized protocols and data formats. Based on specific
implementation circumstances, OMS Data Transfer is strongly recommended
as the OMS Data Exchange best suited for the purposes of moving data
products or data files within a Mission Package. This may improve
overall system performance and bus throughput metrics.

It is recognized that some very large or otherwise high-performance data
transfers may need to be accommodated by an OMS Mission Package.
Provisions have been made for this by allowing the use of OpenFabrics
Alliance libfabric.

OMS Data Transfer does not address databases, persistent data stores, or
any other mechanism for preserving data products.

#### Data Transfer Protocols and Data Formats

The OACWG has identified the types of data most often exchanged between
Subsystems, Services, Isolators, and data storage devices on an OMS
Platform. For each data type, one or more formats and one or more
protocols have been identified to transfer that data. Table 6.3-4, Data
Transfer Formats, APIs, and Protocols, provides the data formats and
protocols allowed within an OMS Mission Package for each identified data
type. In addition, some of these data types are restricted in use
because of overlap with other OMS Data Exchanges, namely OMS Messaging.
The intent is that when there is overlap between OMS Messaging and Data
Transfer, the preferred solution is to encourage the use of OMS
Messaging. The following restrictions apply for all OMS Data Transfer
combinations: 1) does not overlap with OMS Messages, 2) does not overlap
with any other OMS Data Exchanges, and 3) does not transfer external
standards second hand. OMS Data Transfers are non-compliant if the Data
Transfer fails one or more of these restrictions. The “Max Assessed
Tier” column indicates the compliance restrictions determined for each
data type combination. See “External Standards” section for further
information regarding use of external standards.

Additionally, the OACWG recognizes the intended shared use and access of
data should be considered as well. There are multiple sharing patterns
for the exchange of data:

-   An “exclusive use” sharing pattern is where data is exchanged
    to/from Mission Package resources such as data storage by a
    Subsystem, Service, or Isolator for its internal use only; the data
    is not shared with other Subsystems, Services, or Isolators

-   A “shared read-only” sharing pattern is where one or more
    Subsystems, Services, and/or Isolators perform read-only operations
    on the shared data

-   A “shared read/modify” sharing pattern is where Subsystems,
    Services, and/or Isolators perform read and modify operations on the
    shared data.

In order to facilitate interoperability, the preferred solution is to
minimize use of custom data formats. Use of custom data formats may
cause limits on the maximum assessed level of compliance. In the
“exclusive use” sharing pattern, all custom data formats are allowed
because the data is not shared and Mission Package resources are used
only for storage/transmission. The data formats are non-proprietary and
documented to facilitate interoperability.

<span id="_Toc219290725" class="anchor"></span>Table 6.3-4 Data Transfer
Formats, APIs, and Protocols

<table>
<thead>
<tr class="header">
<th>A) Data Type</th>
<th>B) Data Formats</th>
<th>C) Exclusive Use Protocols/APIs</th>
<th>D) Shared Read-Only Protocols/APIs</th>
<th>E) Shared Read/Modify Protocols/APIs*</th>
<th>F) Max Assessed Tier</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Video (includes embedded Audio)</td>
<td>Motion Imagery Standards Profile (MISP) specified formats</td>
<td>MISP specified protocols, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>MISP specified protocols, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>MISP specified protocols, NFS, FTP, HTTP, HTTPS, libfabric, DTAL</td>
<td>3</td>
</tr>
<tr class="even">
<td>Audio</td>
<td>Waveform Audio File (WAV), Audio File (AU), Pulse Code Modulation (PCM), MPEG Audio Layer-3 (MP3), Windows Media Audio(WMA), MPEG Audio Layer-4 (MP4), MPEG-4 Audio (M4A)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>RTP (as specified in MISP), NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>UDP, libfabric, RTP, RTP with RTCP, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Imagery (raster, vector, etc.)</td>
<td>The National Imagery Transmission Format (NITF), Joint Photographic Experts Group (JPEG) 2000 (JP2)</td>
<td>JPIP, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>JPIP, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>TCP, UDP, libfabric, JPIP, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="even">
<td>MTI Detections</td>
<td>Standardization Agreement (STANAG) 4607</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>TCP, UDP, libfabric, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Operational Flight Programs (OFPs)</td>
<td>Custom/binary</td>
<td>NFS, FTP, FTPS, HTTP, HTTPS, TFTP, DTAL</td>
<td>Not Allowed</td>
<td>Not Allowed</td>
<td>3</td>
</tr>
<tr class="even">
<td>Mission Data Files (MDFs)</td>
<td>Custom/binary/text</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>Not Allowed</td>
<td>Not Allowed</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Mission Data Files (MDFs)</td>
<td>Custom/binary/text</td>
<td>Does Not Apply</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>Not Allowed</td>
<td>2</td>
</tr>
<tr class="even">
<td>Mission Data Files (MDFs)</td>
<td>Custom/binary/text</td>
<td>Does Not Apply</td>
<td>Does Not Apply</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>1</td>
</tr>
<tr class="odd">
<td>Configuration, Log, Intermediate, or Checkpoint Files</td>
<td>Custom/binary/text</td>
<td>NFS, FTP, FTPS, HTTP, HTTPS, DTAL</td>
<td>Not Allowed</td>
<td>Not Allowed</td>
<td>3</td>
</tr>
<tr class="even">
<td>Map and Navigation Data</td>
<td>Digital Terrain Elevation Data (DTED), Digital Feature Analysis Data (DFAD), Digital Point Positioning Database (DPPDB), Open Geospatial Consortium (OGC), Arc-second raster chart/map (ARC) Digitized Raster Graphics (ADRG), Compressed ADRG (CADRG), Controlled Image Base (CIB), Vector Product Format (VPF), Shapefile (Shape), Geographic Tagged Image File Format (GeoTIFF), General Regularly-distributed Information in Binary form (GRIB)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>TCP, UDP, libfabric, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Complex Sensor Data</td>
<td>Custom/binary (Header and Real and Imaginary number pairs)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>Not Allowed</td>
<td>Not Allowed</td>
<td>3</td>
</tr>
<tr class="even">
<td>Complex Sensor Data</td>
<td>Custom/binary (Header and Real and Imaginary number pairs)</td>
<td>Does Not Apply</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>TCP, UDP, libfabric, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>2</td>
</tr>
<tr class="odd">
<td>Pass-Through Data Link Messages (see definition below)</td>
<td>Joint Range Extension Applications Protocol (JREAP) Messages</td>
<td>Not Allowed</td>
<td>JREAP-C, TCP (JREAP Application Header with X1.0 message), UDP (JREAP Application Header with X1.0 message)</td>
<td>Not Allowed</td>
<td>3</td>
</tr>
<tr class="even">
<td>Alternative Navigation Data</td>
<td>Binary (based on All Source Positioning and Navigation (ASPN) ICD)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>TCP, UDP, libfabric, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Opaque Data (see definition below)</td>
<td>Binary based on Joint Interface Control Document (JICD)</td>
<td>Not Allowed</td>
<td>Not Allowed</td>
<td>TCP, UDP</td>
<td>3</td>
</tr>
<tr class="even">
<td>Computer Aided Design (CAD)</td>
<td>3D Studio (3DS), LightWave 3D Object (LWO), Material Template Library (MTL), Wavefront 3D Viewer (OBJ), STandard for the Exchange of Product data (STEP), AutoCAD Drawing (DWG), AutoCAD Drawing Exchange (DXF), Microstation Design (DGN), Standard Tessellation Language (STL), Keyhole Markup Language (KML), Keyhole Markup Language Zipped (KMZ), Naming Standards Model (NSM)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>TCP, NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Simulation Data (see definition below)</td>
<td>Distributed Interactive Simulation (DIS) Protocol Data Unit (PDU)</td>
<td>Not Allowed</td>
<td>Not Allowed</td>
<td>TCP, UDP</td>
<td>3</td>
</tr>
<tr class="even">
<td>Shared Aperture Information Files (see definition below)</td>
<td>Approved files documented as an Extensible Markup Language (XML) Schema Definition (XSD)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Shared Aperture Digital Data Streams (see definition below)</td>
<td><p>Modular Open RF Architecture (MORA) Data Message VITA Radio Transport (VRT), Agile Mission Suite Government Reference Architecture (AMS GRA)**</p>
<p>(non-proprietary)</p>
<p>(See limitations below)</p></td>
<td>N/A</td>
<td>TCP, UDP, libfabric</td>
<td>TCP, UDP, libfabric</td>
<td>3</td>
</tr>
<tr class="even">
<td>Shared Aperture RF Distribution Data</td>
<td>Scalable Payload for Electronic Attack Development (SPEAD) High Speed Signaling</td>
<td>N/A</td>
<td>VITA 17.3, libfabric</td>
<td>VITA 17.3, libfabric</td>
<td>3</td>
</tr>
<tr class="odd">
<td>Files for Human Consumption (see definition below)</td>
<td>Text, Portable Data Format (PDF), Comma Separated Values (CSV), Tab Separated Values (TSV), Office Open XML (OOXML)</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>NFS, FTP, HTTP, HTTPS, DTAL</td>
<td>3</td>
</tr>
<tr class="even">
<td><p>Note: * - TCP, UDP, and libfabric applies to any pairwise combination of Subsystems, Services, or Isolators</p>
<p>Note: ** - Only the pertinent data formats to support this data transfer defined in the AMS GRA are applicable.</p>
<p>Note: The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Note: For data transfer combinations not appearing in this table, see Table 6.3-5, Non-OMS Data Transfers.</p></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Pass-Through Data Link Messages are restricted to messages whose source
and destination reside external to the OMS Mission Package. Pass-Through
is limited to Relay (retransmission of a Data Link message from one
network to another network of the same Data Link protocol) and
Forwarding (receiving a message via one Data Link protocol and sending
the message, using the proper format and link protocols, on a different
Data Link protocol). JREAP Messages are used for moving Pass-Through
Data Link Messages and their associated header information through the
OMS Mission Package. The Pass-Through definition prohibits OMS Services
or Subsystems within the OMS Mission Package from processing the Data
Link message, with the exception of Comm Subsystem(s) and/or Isolator(s)
for the sole purpose of performing the Relay/Forwarding function (as
defined in the Service Contract). The Comm Subsystem(s) and/or
Isolator(s) may include data logging as part of the Relay/Forwarding
function.

Opaque Data conforms to the Joint Interface Control Document (JICD) in a
format that is opaque during transmission (e.g., encrypted). The Opaque
Data Transfer is restricted to usage by: 1) Subsystems and/or Services
that provide an Opaque Capability, or 2) Subsystems, Services, and/or
Isolators that exchange Opaque Data with a Subsystem and/or Service that
provides an Opaque Capability. This data transfer is only intended to
support Opaque Capabilities and not general use of JICD messages between
non-Opaque Subsystems, Services, and Isolators.

Simulation Data is composed of DIS Protocol Data Units (PDUs) as defined
by the IEEE Std 1278.1-2012 and is not to be used in place of OMS Data
Exchanges beyond simulation. The DIS Standard provides PDUs for time
management. The current DIS release does not include a desired element
of time management, specifically, the ability to change the time rate. A
future release of the DIS standard will incorporate this desired
functionality. Until the next DIS version is available, recommended use
details are provided in the Service Contract Template Instructions to
support consistent simulation and simulation time management operations
across OMS Subsystems, Services, and Isolators for future operations and
planning activities.

A Shared Aperture Information File (SAIF) provides data to the
Subsystems and Services participating in aperture sharing including the
following: 1) shared apertures, 2) Multi-Function Subsystems/Services
that transmit and/or receive data using the shared apertures, 3)
Resource Management (RM) functions that allocate and/or
arbitrate/schedule the shared apertures, and 4) system connectivity,
such as the Radio Frequency (RF) distribution connections when RF
apertures are supported. The participating Subsystems and Services need
the information files at initialization (start-up/re-start), reading
them in by file transfer from data storage. There is no intent for this
file to be updated by a Service/Subsystem post-initialization or used in
a manner other than what is provided in the previous statement. Each
Shared Aperture Information File provides enough description to other
Subsystems such that there is a common understanding of related
capability. For example, the shared aperture information file describes
antenna resource instances which can be requested and allocated along
with their performance characteristics, as well as the
conflicts/simultaneity between antenna resource instances. The format
description documents are described in an XML Schema Definition (XSD)
file and those that have been approved are listed in Table 5.2-2 Other
Documents.

Many current files shared amongst Subsystems, Service and/or Isolators
are identified as being documents that are created by and for operators
to share. Items, like Special Instructions (SPINS) fall into this
category. These files are textual in nature and do not follow a strictly
defined format. For items such as this we use a data type called “Files
for Human Consumption.” “Files for Human Consumption” are files intended
for use by a human, not for machine parsing. Some of these data file
formats may have dual usage (e.g., comma separated values). If machine
parsing and taking action is the intent, “Files for Human Consumption”
should not be used.

All Shared Aperture Digital Data Streams are considered a data transfer.
Shared Aperture Digital Data Streams refer to the low latency interfaces
between OMS Capabilities (e.g., EA, ESM) and the digital apertures they
share. The digital data RF streams include the digitized RF data (“IQ”
data), pulse descriptor words (PDWs), and associated signaling for set
up and usage of the digital aperture resources. The Modular Open RF
Architecture (MORA) standard establishes a packet utilization structure
for the interfaces between back ends and apertures.

The Scalable Payload for Electronic Attack Development (SPEAD) high
speed interfaces between RF back end Subsystems and analog shared RF
apertures (RF data on coax cables through an RF switch matrix) include
interoperability and RF Distribution Data exchanges on high speed serial
ports (VITA 17.3) for low latency aperture access by the sharing
Subsystems and resource management. SPEAD High Speed Signaling data
formats are described further in SPD-STD-001 SPEAD High Speed Signaling.

#### Non-OMS Data Transfer

Non-OMS Data Transfer deals with file and product exchanges that fall
outside the OMS Data Transfer defined data types and their allowed data
formats, transfer protocols/APIs, and sharing patterns described by the
OMS Standard. Non-OMS Data Transfers are typically restricted to OMS
compliance Tier 1. However, when an OACWG-approved Change Request is
identified, then the Non-OMS Data Transfer will be assessed at the
maximum allowed Tier specified by the OACWG.

For additional detail, see Table 6.3-5 Non-OMS Data Transfers.

<span id="_Toc219290726" class="anchor"></span>Table 6.3-5 Non-OMS Data
Transfers

<table>
<thead>
<tr class="header">
<th>A) Data Type</th>
<th>B) Data Format</th>
<th>C) Exclusive Use Protocols/APIs</th>
<th>D) Shared Read-Only Protocols/APIs</th>
<th>E) Shared Read/Modify Protocols/APIs</th>
<th>F) Max Assessed Tier</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>New - not listed in Table 6.3-4</td>
<td>No restrictions</td>
<td>No restrictions</td>
<td>No restrictions</td>
<td>No restrictions</td>
<td>1*</td>
</tr>
<tr class="even">
<td>Any listed in Table 6.3-4</td>
<td>New - not listed in Table 6.3-4 for the corresponding existing data type</td>
<td>No restrictions</td>
<td>No restrictions</td>
<td>No restrictions</td>
<td>1*</td>
</tr>
<tr class="odd">
<td>Note:* - Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, the max assessed Tier will be determined by OACWG approval of the Change Request.</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Table 6.3-6, Data Transfer Protocols and APIs, describes the protocols,
APIs, and their specifications that are allowed for Data Transfer and
data storage as identified in Table 6.3-4. Only versions identified in
the “Specification” column are acceptable to use.

<span id="_Toc219290727" class="anchor"></span>Table 6.3-6 Data Transfer
Protocols and APIs

<table>
<thead>
<tr class="header">
<th>Allowed Protocols and APIs</th>
<th>Abbreviation</th>
<th>Specification</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Transmission Control Protocol</td>
<td>TCP</td>
<td>RFC 793</td>
<td>TCP is one of the main protocols in TCP/IP networks. Whereas the IP protocol deals only with packets, TCP enables two hosts to establish a connection and exchange streams of data. TCP guarantees delivery of data and also guarantees that packets will be delivered in the same order in which they were sent.</td>
</tr>
<tr class="even">
<td>User Datagram Protocol</td>
<td>UDP</td>
<td>RFC 768</td>
<td>The User Datagram Protocol (UDP) is one of the core members of the Internet protocol suite. The protocol was designed by David P. Reed in 1980 and formally defined in RFC 768. UDP uses a simple connectionless transmission model with a minimum of protocol mechanism.</td>
</tr>
<tr class="odd">
<td>File Transfer Protocol</td>
<td>FTP</td>
<td><p>RFC 959</p>
<p>RFC 2428</p></td>
<td>The File Transfer Protocol (FTP) is a standard network protocol used to transfer computer files from one host to another host over a TCP-based network, such as the Internet. FTP is built on a client-server architecture and uses separate control and data connections between the client and the server.</td>
</tr>
<tr class="even">
<td>File Transfer Protocol Secure</td>
<td>FTPS</td>
<td>RFC 4217</td>
<td>FTPS is an extension to the commonly used File Transfer Protocol (FTP) that adds support for the Transport Layer Security (TLS) cryptographic protocols. TLS version 1.2 (RFC 5246) at a minimum.</td>
</tr>
<tr class="odd">
<td>Hypertext Transfer Protocol</td>
<td>HTTP</td>
<td>RFC 7230</td>
<td>The Hypertext Transfer Protocol (HTTP) is an application protocol for distributed, collaborative, hypermedia information systems. HTTP is the foundation of data communication for the World Wide Web. Hypertext is structured text that uses logical links (hyperlinks) between nodes containing text. Refer to OMS URI Formats table for restrictions on the use of this protocol.</td>
</tr>
<tr class="even">
<td>Hypertext Transfer Protocol Secure</td>
<td>HTTPS</td>
<td>RFC 2818</td>
<td>Hypertext Transfer Protocol Secure (HTTPS) is an extension of the Hypertext Transfer Protocol (HTTP). It is used for secure communication over a computer network and is widely used on the Internet. In HTTPS, the communication protocol is encrypted using Transport Layer Security (TLS) and is also referred to as HTTP over TLS. TLS version 1.2 (RFC 5246) at a minimum. Refer to OMS URI Formats table for restrictions on the use of this protocol.</td>
</tr>
<tr class="odd">
<td>Network File System</td>
<td>NFS</td>
<td><p>RFC 1813</p>
<p>RFC 3530</p></td>
<td>Network File System (NFS) is a distributed file system protocol originally developed by Sun Microsystems in 1984, allowing a user on a client computer to access files over a network much like local storage is accessed.</td>
</tr>
<tr class="even">
<td>Trivial File Transfer Protocol</td>
<td>TFTP</td>
<td>RFC 1350</td>
<td>Trivial File Transfer Protocol (TFTP) is a simple, lock-step, file transfer protocol which allows a client to get from or put a file onto a remote host. One of its primary uses is in the early stages of nodes booting from a Local Area Network.</td>
</tr>
<tr class="odd">
<td>JPEG 2000 Interactive Protocol</td>
<td>JPIP</td>
<td>MISB RP 0811.1</td>
<td>JPIP (JPEG 2000 Interactive Protocol) is a compression streamlining protocol that works with JPEG 2000 to produce an image using the least bandwidth required. JPIP has the capacity to download only the requested part of a picture, saving bandwidth, computer processing on both ends, and time. It allows for the relatively quick viewing of a large image in low resolution, as well as a higher resolution part of the same image. Using JPIP, it is possible to view large images (1 gigapixel) on relatively light weight hardware such as PDAs.</td>
</tr>
<tr class="even">
<td>Motion Imagery Standards Profile Specified Protocols</td>
<td>MISP</td>
<td><p>MISP Versions 6.4, 6.5, 6.6 [Deprecated]</p>
<p>MISP-2023.2</p></td>
<td>The Motion Imagery Standards Profile (MISP) defines the formats, protocols and dissemination mechanisms that govern motion imagery for the DoD. The OACWG has adopted MISP based standards as the approved method for transferring motion imagery within an OMS Mission Package (MP). The MISP defines the standards, engineering guidelines and recommended practices that are allowed for data transfer within an OMS-compliant system.</td>
</tr>
<tr class="odd">
<td>Real-Time Transport Protocol</td>
<td>RTP</td>
<td>RFC 3550</td>
<td>The Real-time Transport Protocol (RTP) is a network protocol for delivering audio and video over IP networks. RTP typically runs over User Datagram Protocol (UDP). RTP is used in conjunction with the RTP Control Protocol (RTCP). While RTP carries the media streams (e.g., audio and video), RTCP is used to monitor transmission statistics and quality of service (QoS) and aids synchronization of multiple streams. RTP is one of the technical foundations of Voice over IP and in this context is often used in conjunction with a signaling protocol such as the Session Initiation Protocol (SIP) which establishes connections across the network.</td>
</tr>
<tr class="even">
<td>Real-Time Transport Control Protocol</td>
<td>RTCP</td>
<td>RFC 3550</td>
<td><p>The RTP Control Protocol (RTCP) is a sister protocol of the Real-time Transport Protocol (RTP). Its basic functionality and packet structure is defined in RFC 3550. RTCP provides out-of-band statistics and control information for an RTP session. It partners with RTP in the delivery and packaging of multimedia data but does not transport any media data itself.</p>
<p>The primary function of RTCP is to provide feedback on the quality of service (QoS) in media distribution by periodically sending statistics information such as transmitted octet and packet counts, packet loss, packet delay variation, and round-trip delay time to participants in a streaming multimedia session.</p></td>
</tr>
<tr class="odd">
<td>libfabric</td>
<td>libfabric</td>
<td>libfabric 1.11.2</td>
<td>Libfabric is a core component of OpenFabrics Interfaces (OFI), which is a framework focused on exporting fabric communication services to applications. Libfabric is the library that defines and exports the user-space API of OFI, and is typically the only software that applications deal with directly. It works in conjunction with provider libraries, which are often integrated directly into libfabric. (<span class="underline">https://ofiwg.github.io/libfabric/</span>)</td>
</tr>
<tr class="even">
<td>Joint Range Extension Applications Protocol Appendix C</td>
<td>JREAP-C</td>
<td>MIL-STD-3011</td>
<td>MIL-STD-3011 Joint Range Extension Applications Protocol allows for the transmission of Data Link messages over an IP based network. JREAP-C represents the full MIL-STD-3011 Protocol being implemented as an OMS Data Transfer.</td>
</tr>
<tr class="odd">
<td>VITA 17.3 Serial Front Panel Data Port (sFPDP) Gen 3.0</td>
<td>VITA 17.3</td>
<td>VITA 17.3, 2018</td>
<td>The VITA 17.3 “Serial FPDP Gen 3.0” (sFPDP) Standard defines a high-speed serial communications interface. Included in the definition are various user data framing methods, supported system configurations, and the Link Layer Protocol.</td>
</tr>
<tr class="even">
<td>Data Transfer API Library</td>
<td>DTAL</td>
<td><p>OMSC-SPC-012_RevB_CxxDTAPISpec_DandD_v2_5</p>
<p>&amp;</p>
<p>OMSC-SPC-011_RevB_JavaDTAPISpec_DandD_v2_5</p></td>
<td>The Data Transfer API Library (DTAL) provides support for transferring data to and from endpoints that are identified in either the <strong>ProductLocation</strong> or <strong>FileLocation</strong> messages. Providing a DTAL is at the discretion of the Mission Package provider.</td>
</tr>
</tbody>
</table>

#### Data Transfer of Very Large Products and High Performance Transfers

For those OMS Mission Packages that have Subsystems that produce large
products or have other requirements that necessitate high performance or
high bandwidth networks, the use of the libfabric APIs from the
OpenFabrics Alliance is permitted for data transfer. The term “large” is
applied to sensor products greater than three hundred megabytes in size.
A high performance or high bandwidth network is defined as a network
that provides a minimum of ten gigabits per second per channel. An
example would be InfiniBand, which supports Remote Direct Memory Access
(RDMA).

The libfabric API enables data products to be transferred using RDMA
which is directly built into many high performance network adapters. The
RDMA transfer of data products across the data fabric yields the highest
performance available, typically ninety-eight (98) percent of the
theoretical maximum bandwidth. RDMA enabled fabrics may also support IP,
which means that all of the data types can use the high performance or
high bandwidth network for all data transfer and realize the improved
performance. For those transfers that utilize RDMA for the data fabric,
the formats specified in Table 6.3-6, Data Transfer Protocols and APIs,
are still required. The use of RDMA transfers requires a specific
initialization sequence that is covered in Section 6.3.2.4.6, Remote
Direct Memory Access Data Transfers.

#### Data Transfer Coordination

Two OMS messages used to coordinate the transfer of data products among
Subsystems, Services, and Isolators within an OMS Mission Package are
the **ProductLocation** and **ProductMetadata** messages. These messages
define the location and content of products, respectively, for use by
Subsystems, Services, and Isolators. For most of these data transfers,
these two messages are adequate. Additional UCI messages are available
for product classification, dissemination, download, and processing.

Likewise, two OMS messages used to coordinate the transfer of data files
for use by Subsystems, Services, and Isolators within an OMS Mission
Package are the **FileLocation** and **FileMetadata** messages. These
messages define the location and content of files, respectively, for use
by Subsystems, Services, and Isolators, and are the only two UCI
messages that pertain to files.

Aspects of data transfer are documented in several locations. The
Platform Description Document (PDD) captures all file servers
implemented by the platform and their configuration. The Service
Contract captures all data transfers supported by the Service along with
the protocols and data formats. The combination of Subsystem Description
Document (SDD) and Service Contract capture all data transfers supported
by the Subsystem along with the protocols and data formats. The Mission
Package Description Document (MPDD) captures the data transfer flows,
ports, and protocols used in a Mission Package.

##### Uniform Resource Identifier

Subsystems, Services, and Isolators will need to specify the appropriate
URI to send or receive various types of data within an OMS Mission
Package. The URI can specify the transfer protocol and product location.
Table 6.3-7, OMS URI Formats, defines the content and format of URIs
that may be used for the protocols allowed within a Mission Package for
transferring data products.

<span id="_Toc219290728" class="anchor"></span>Table 6.3-7 OMS URI
Formats

<table>
<thead>
<tr class="header">
<th>Transfer Type</th>
<th>URI Format</th>
<th>URI Scheme Reference</th>
<th>Example and/or Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>TCP</td>
<td>tcp://&lt;host&gt;:&lt;port&gt;/</td>
<td>None</td>
<td>tcp://172.25.50.49:1024/</td>
</tr>
<tr class="even">
<td>UDP</td>
<td>udp://&lt;host&gt;:&lt;port&gt;/</td>
<td><p>Provisional</p>
<p>http://www.iana.org/assignments/uri-schemes/prov/udp</p></td>
<td>udp://172.25.50.49:1024/</td>
</tr>
<tr class="odd">
<td>FTP</td>
<td>ftp://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>RFC 1738, Section 3.2</td>
<td>ftp://172.25.50.49/path/to/file.ext</td>
</tr>
<tr class="even">
<td>FTPS</td>
<td>ftps://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>RFC 1738, Section 3.2</td>
<td>ftps://172.25.50.49/path/to/file.ext</td>
</tr>
<tr class="odd">
<td>HTTP</td>
<td>http://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>RFC 7230, Section 2.7.1</td>
<td><p><span class="underline">http://172.25.50.49/path/to/file.ext</span></p>
<p>Note that the Query and Fragment (#) fields are not shown here. Their use is not permitted by the OMS Standard for Data Transfers since the contents of these fields are not standardized. A Service should not expose an HTTP server to the ASB that expects these fields to be used by another Service.</p></td>
</tr>
<tr class="even">
<td>HTTPS</td>
<td>https://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>RFC 2818</td>
<td><p><span class="underline">https://172.25.50.49/path/to/file.ext</span></p>
<p>Note that the Query and Fragment (#) fields are not shown here. Their use is not permitted by the OMS Standard for Data Transfers since the contents of these fields are not standardized. A Service should not expose an HTTP server to the ASB that expects these fields to be used by another Service.</p></td>
</tr>
<tr class="odd">
<td>NFS</td>
<td>nfs://&lt;host&gt;[:&lt;port&gt;]/&lt;url-path&gt;</td>
<td>RFC 2224</td>
<td>nfs://172.25.50.49/path/to/file.ext</td>
</tr>
<tr class="even">
<td>TFTP</td>
<td>tftp://&lt;host&gt;/path</td>
<td>RFC 3617</td>
<td>tftp://172.25.50.49/path/to/file.ext</td>
</tr>
<tr class="odd">
<td>JPIP</td>
<td>jpip://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>None</td>
<td>jpip://172.25.50.49/path/to/file.ext</td>
</tr>
<tr class="even">
<td>RTP</td>
<td>rtp://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>RFC 3550</td>
<td>rtp://172.25.50.49/path/to/stream</td>
</tr>
<tr class="odd">
<td>RTP with RTCP</td>
<td>rtp://&lt;host&gt;[:&lt;port&gt;]/path</td>
<td>RFC 3550</td>
<td>rtp://172.25.50.49/path/to/stream</td>
</tr>
<tr class="even">
<td>RDMA</td>
<td>rdma://&lt;host&gt;:&lt;offset&gt;:&lt;size&gt;/ [&lt;publisher_endpoint&gt;]</td>
<td>None</td>
<td><p>Identifies the host, offset to the start of the data product in memory host has registered for RDMA, and size of the data product.</p>
<p>The optional field is used to define the endpoint that the subscribers use on the publisher to get the data.</p></td>
</tr>
</tbody>
</table>

Table 6.3-8, Data Formats and MIME types, describes the data formats
that are allowed for Data Transfer and data storage as identified in
Table 6.3-4. For data products shared between Subsystems, Services, and
Isolators, whether via a file system or not, the **ProductMetadata**
message must contain a product format. The format should be specified as
an Internet media type, commonly known as a Multipurpose Internet Mail
Extensions (MIME) type. In general, MIME types are taken from the
Internet Assigned Numbers Authority (IANA) and the MIME types listed in
Table 6.3-8 are recommended. When formats do not have an IANA registered
MIME type, OMS has adopted the ‘x-‘ scheme for unregistered but
coordinated exchanges and created an OMS specific label and described
the intended contents. MIME types are documented in the Service Contract
with the associated data transfer format.

Available specifications for these file formats are listed in either
Table 5.1-1, Reference Standards, or Table 5.2-2, Other Documents.

<span id="_Toc219290729" class="anchor"></span>Table 6.3-8 Data Formats
and MIME Types

<table>
<thead>
<tr class="header">
<th>Allowed Formats</th>
<th>Typical File Extension(s)</th>
<th>MIME Type</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>3DS</td>
<td>3ds</td>
<td><p>application/x-oms.3ds</p>
<p>image/x-oms.3ds</p></td>
<td>A 3D Studio (3DS) file is a 3D image format used by Autodesk 3D Studio. It contains mesh data, material attributes, bitmap references, smoothing group data, viewport configurations, camera locations, and lighting information. 3DS files may also include object animation data.</td>
</tr>
<tr class="even">
<td>ADRG</td>
<td><p>.gen</p>
<p>.thf</p>
<p>.img</p></td>
<td>model/x-oms.adrg</td>
<td>Arc-second raster chart/map (ARC) Digitized Raster Graphics (ADRG) are digitized replicas of hard copy source maps transformed into a specific georegistration framework and accompanied by ASCII encoded support files.</td>
</tr>
<tr class="odd">
<td>ASPN ICD</td>
<td></td>
<td>application/x-oms.aspnbin</td>
<td>The All Source Positioning Navigation (ASPN) program was intended to mitigate dependence on GPS by creating a standardized set of data from common navigation sensors in multiple quantities, on multiple platforms, and in multiple scenarios. The ASPN ICD is the basis for data standards for positioning, navigation, and timing (PNT) systems.</td>
</tr>
<tr class="even">
<td>AU</td>
<td><p>.au</p>
<p>.snd</p></td>
<td>audio/basic</td>
<td>The Audio (AU) file format is a file format for storing digital audio data on a computer system.</td>
</tr>
<tr class="odd">
<td>Binary</td>
<td>.bin</td>
<td>application/x-oms.bin</td>
<td>Any custom binary file.</td>
</tr>
<tr class="even">
<td>CADRG</td>
<td><p>.ccz</p>
<p>.lgd</p>
<p>.ovr</p>
<p>.toc</p></td>
<td>model/x-oms.cadrg</td>
<td>Compressed ADRG (CADRG) is a general purpose product, comprising computer-readable digital map and chart images. It supports various weapons, C3I theater battle management, mission planning, and digital moving map systems.</td>
</tr>
<tr class="odd">
<td>CIB</td>
<td></td>
<td>model/x-oms.cib</td>
<td>Controlled Image Base (CIB) is a dataset of orthophotos, made from rectified grayscale aerial images, produced to support mission planning and command, control, communications, and intelligence systems that are compressed and reformatted to conform to the raster product format standard. The files are physically formatted within the National Imagery Transmission Format (NITF) message.</td>
</tr>
<tr class="even">
<td>CSV</td>
<td>.csv</td>
<td>text/csv</td>
<td>A Comma Separated Values (CSV) file is a delimited text file that uses a comma to separate values. Each line of the file is a data record. Each record consists of one or more fields, separated by commas.</td>
</tr>
<tr class="odd">
<td>Custom</td>
<td></td>
<td>application/x-oms.custom</td>
<td>Custom refers to a format that is proprietary in nature.</td>
</tr>
<tr class="even">
<td>DFAD</td>
<td></td>
<td>model/x-oms.dfad</td>
<td>Digital Feature Analysis Data (DFAD) is a military vector format, originally developed for radar applications.</td>
</tr>
<tr class="odd">
<td>DGN</td>
<td>.dgn</td>
<td>model/x-oms.dgn</td>
<td>A MicroStation Design (DGN) file is a 2D/3D drawing created by various construction CAD software, such as MicroStation and Intergraph’s Interactive Graphics Design System CAD programs.</td>
</tr>
<tr class="even">
<td>DIS PDU</td>
<td></td>
<td>application/x-oms.dispdu</td>
<td>Distributed Interactive Simulation (DIS) IEEE 1278 is a standard for conducting real-time platform-level wargaming across multiple host computers and is used worldwide, especially by military organizations. Systems communicate and exchange information via protocol data units (PDUs).</td>
</tr>
<tr class="odd">
<td>DPPDB</td>
<td></td>
<td>model/x-oms.dppdb</td>
<td>Digital Point Positioning Database (DPPDB) is a stereo image based product that consists of parametric support data, compressed reference graphics, and high resolution national imagery stereo pair sets covering a nominal 60 nautical mile (NM) by 60 NM area.</td>
</tr>
<tr class="even">
<td>DTED</td>
<td><p>.dt2,</p>
<p>.dted,</p>
<p>.dt0,</p>
<p>.dt1</p></td>
<td>model/x-oms.dted</td>
<td>Digital Terrain Elevation Data (DTED) is a standard of digital datasets which consists of a matrix of terrain elevation values, i.e., a Digital Elevation Model.</td>
</tr>
<tr class="odd">
<td>DWG</td>
<td>.dwg</td>
<td>image/vnd.dwg</td>
<td>AutoCAD Drawing (DWG) is a proprietary binary file format used for storing two- and three- dimensional design data and metadata. It is the native format for several CAD packages including DraftSight, AutoCAD, BricsCAD, IntelliCAD (and its variants), Caddie and Open Design Alliance compliant applications.</td>
</tr>
<tr class="even">
<td>DXF</td>
<td>.dxf</td>
<td>image/vnd.dxf</td>
<td>AutoCAD Drawing Exchange (DXF) is a universal file format type for storing Computer-Aided Design (CAD) models.</td>
</tr>
<tr class="odd">
<td>GeoTIFF</td>
<td>.tif</td>
<td>image/tiff</td>
<td>Geographic Tagged Image File Format (GeoTIFF) is a public domain metadata standard that allows georeferencing information to be embedded within a TIFF file. It defines a set of TIFF tags to describe all "Cartographic" information associated with TIFF imagery that originates from satellite imaging systems, scanned aerial photography, scanned maps, digital elevation models, or as a result of geographic analyses.</td>
</tr>
<tr class="even">
<td>GRIB</td>
<td>.grb</td>
<td>application/x-grib</td>
<td>General Regularly-distributed Information in Binary form (GRIB) is a file format for the storage and transport of gridded meteorological data, such as Numerical Weather Prediction model output.</td>
</tr>
<tr class="odd">
<td>JICD</td>
<td></td>
<td>application/x-oms.jicdbin</td>
<td>Joint Interface Control Document (JICD) 4.2 is a standard which provides defense with the necessary components to rapidly integrate ISR capabilities in the delivery of new Electromagnetic Environment Concept of Operations. The JICD binary is a stream transport of the JICD 4.2 specification messages.</td>
</tr>
<tr class="even">
<td>JP2</td>
<td>.jpf</td>
<td>image/jp2</td>
<td>JPEG 2000 (JP2), ISO standard ISO/IEC 15444-1, is an image compression standard and coding system created by the Joint Photographic Experts Group (JPEG) committee.</td>
</tr>
<tr class="odd">
<td>JREAP Message</td>
<td></td>
<td>data/x-oms.jreap</td>
<td>Joint Range Extension Applications Protocol (JREAP) is the protocol and message structure for the transmission and reception of pre-formatted messages over communications media other than those for which these messages were designed. It enables tactical data messages to be transmitted over long-distance networks, e.g., satellite links, thereby extending the range of Tactical Data Links (TDLs).</td>
</tr>
<tr class="even">
<td>KML</td>
<td>.kml</td>
<td>application/vnd.google-earth.kml+xml</td>
<td>Keyhole Markup Language (KML) is an XML notation for expressing geographic annotation and visualization within two-dimensional maps and three-dimensional Earth browsers. KML was developed for use with Google Earth.</td>
</tr>
<tr class="odd">
<td>KMZ</td>
<td>.kmz</td>
<td>application/vnd.google-earth.kmz</td>
<td>Keyhole Markup Language Zipped (KMZ) is a file extension for a placemark file used by Google Earth. KMZ stands for Keyhole Markup language Zipped. It is a compressed version of a KML (Keyhole Markup Language) file.</td>
</tr>
<tr class="even">
<td>LWO</td>
<td>.lwo</td>
<td>model/x-oms.lwo</td>
<td>LightWave 3D Object (LWO) is an object file format used by LightWave. LightWave is a program used for 3-D modeling, animation, and rendering. LWO files contain objects stored as meshes, and include polygons, points, and surfaces that describe the model's appearance. They also might reference image files for textures.</td>
</tr>
<tr class="odd">
<td>M4A</td>
<td>.m4a</td>
<td>audio/MP4A-LATM</td>
<td>M4A is an audio data file based on MP4 formats which uses the Advanced Audio Coding (AAC) or Apple Lossless (ALAC) formats.</td>
</tr>
<tr class="even">
<td>MISP</td>
<td></td>
<td>video/x-oms.MISP</td>
<td>The Motion Imagery Standards Profile (MISP) provides requirements and general guidance of Motion Imagery Standards for the ISR community to achieve interoperability in both the communication and functional use of Motion Imagery Data.</td>
</tr>
<tr class="odd">
<td>MORA VRT</td>
<td></td>
<td>application/x-oms.vrt</td>
<td>Modular Open RF Architecture (MORA) Data Message VITA Radio Transport (VRT) is the U.S. Army's CCDC (Combat Capabilities Development Command) C5ISR Center's new architecture of open radio frequency interfaces for ground vehicles. MORA uses the VMEbus International Trade Association (VITA) Radio Transport (VRT) within its MORA Data Message for control and context of analog and digital signal streams.</td>
</tr>
<tr class="even">
<td>MP3</td>
<td>.mp3</td>
<td>audio/mpeg</td>
<td>MPEG-1 or MPEG-2 Audio Layer III, more commonly referred to as MP3, is an audio coding format for digital audio which uses a form of lossy data compression.</td>
</tr>
<tr class="odd">
<td>MP4</td>
<td>.mp4</td>
<td>audio/mp4</td>
<td>The MP4 file format specification was based on the QuickTime format specification, and supports audio only</td>
</tr>
<tr class="even">
<td>MPEG-2</td>
<td>.mp2</td>
<td>video/MP2T</td>
<td>MPEG-2 (aka H.222/H.262 as defined by the ITU) is a standard for “the generic coding of moving pictures and associated audio information.” While MPEG-2 is not as efficient as newer standards such as H.264, backwards compatibility with existing hardware and software means it is still widely used.</td>
</tr>
<tr class="odd">
<td>MPEG-4</td>
<td>.h264</td>
<td>video/H264</td>
<td>H.264 or MPEG-4 Part 10, Advanced Video Coding (MPEG-4 AVC) is an ITU standard for a video compression format that is currently one of the most commonly used formats for the recording, compression, and distribution of video content.</td>
</tr>
<tr class="even">
<td>MTL</td>
<td>.mtl</td>
<td>model/mtl</td>
<td>Material Template Library (MTL) file format is a companion file format to .OBJ, defined by Wavefront Technologies, that describes surface shading (material) properties of objects within one or more .OBJ files.</td>
</tr>
<tr class="odd">
<td>NITF</td>
<td>.nitf</td>
<td>application/vnd.nitf</td>
<td>The National Imagery Transmission Format (NITF) Standard (NITFS), MIL-STD-2500C, is the default format for interchange between systems, though DoD policy allows other image formats to be used internally within a single system. NITFS provides a package containing information about the image, the image itself, and optional overlay graphics.</td>
</tr>
<tr class="even">
<td>NSM</td>
<td></td>
<td>model/x-oms.nsm</td>
<td>Naming Standards Model (NSM) defines naming conventions. If an NSM file is required in support of one of the other file types, the originator of the data transfer must transfer the NSM file and the associated file.</td>
</tr>
<tr class="odd">
<td>OBJ</td>
<td>.obj</td>
<td>model/obj</td>
<td>The Wavefront 3D Viewer (OBJ) file format is a simple data-format that represents 3D geometry alone – namely, the position of each vertex, the UV position of each texture coordinate vertex, vertex normals, and the faces that make each polygon defined as a list of vertices, and texture vertices.</td>
</tr>
<tr class="even">
<td>OGC</td>
<td></td>
<td></td>
<td>The Open Geospatial Consortium (OGC) is an international consortium of more than 500 businesses, government agencies, research organizations, and universities driven to make geospatial (location) information and services FAIR - Findable, Accessible, Interoperable, and Reusable. The OGC provides over 30 standards and data format specifications to promote geospatial information interoperability.</td>
</tr>
<tr class="odd">
<td>OOXML</td>
<td><p>.docx</p>
<p>.dotx</p>
<p>.pptx</p>
<p>.xlsx</p></td>
<td><p>application/vnd.openxmlformats-officedocument.wordprocessingml.document (.docx)</p>
<p>application/vnd.openxmlformats-officedocument.wordprocessingml.template (.dotx)</p>
<p>application/vnd.openxmlformats-officedocument.presentationml.presentation (.pptx)</p>
<p>application/vnd.openxmlformats-officedocument.spreadsheetml.sheet (.xlsx)</p></td>
<td>The Office Open XML (OOXML) file formats are a set of file formats that can be used to represent electronic office documents.</td>
</tr>
<tr class="even">
<td>PCM</td>
<td>.pcm</td>
<td>audio/x-oms.pcm</td>
<td>Pulse-code modulation (PCM) is a method used to digitally represent sampled analog signals. In a PCM stream, the amplitude of the analog signal is sampled regularly at uniform intervals, and each sample is quantized to the nearest value within a range of digital steps.</td>
</tr>
<tr class="odd">
<td>PDF</td>
<td>.pdf</td>
<td>application/pdf</td>
<td>Portable Document Format (PDF) is a standard for representing documents and other reference material in a format that is independent of application software, hardware or operating system.</td>
</tr>
<tr class="even">
<td>Shape</td>
<td><p>.shp</p>
<p>.shx</p>
<p>.dbf</p></td>
<td><p>application/vnd.shp,</p>
<p>application/vnd.shx,</p>
<p>application/vnd.dbf</p></td>
<td>A Shapefile is an Open Source vector data storage format developed and regulated by the Environmental Systems Research Institute (ESRI. Shapefiles are used for storing the location, shape, and attributes of geographic features using points, lines, and polygons, representing, for example, water wells, rivers, and lakes.</td>
</tr>
<tr class="odd">
<td>SPEAD High Speed Signaling</td>
<td></td>
<td>application/x-oms.spead</td>
<td>Scalable Payload Electronic Attack Demonstration (SPEAD) is a standard for analog Electronic Warfare (EW) systems to share antenna resources using the OMS Standard for high level command and control (C2) and resource management.</td>
</tr>
<tr class="even">
<td>STANAG 4607</td>
<td></td>
<td>application/x-oms.stanag4607</td>
<td>Detection data as defined by STANAG 4607 the NATO Ground Moving Target Indicator (GMTI) file format. It defines a standard for the data content and format for the products of ground moving target indicator radar systems.</td>
</tr>
<tr class="odd">
<td>STEP</td>
<td><p>.p21,</p>
<p>.step,</p>
<p>.stp</p></td>
<td>application/octet-stream</td>
<td>Standard for the Exchange of Product Data (STEP) is a file extension for a 3-D graphic file used by CAD software. STP files are used to store 3D image data in an ASCII format.</td>
</tr>
<tr class="even">
<td>STL</td>
<td>.stl</td>
<td>model/stl</td>
<td>Standard Tessellation Language (STL) is also called StereoLithography. STL is a file format native to the stereolithography CAD software created by 3D Systems. The STL file format is an openly documented format for describing the surface of an object as a triangular mesh, that is, as a representation of a 3-dimensional surface in triangular facets.</td>
</tr>
<tr class="odd">
<td>Text</td>
<td>.txt</td>
<td>text/plain</td>
<td>A file with .txt extension represents a text document that contains plain text in the form of lines. All the text contained in such a file is in human-readable format and represented by sequence of characters.</td>
</tr>
<tr class="even">
<td>TSV</td>
<td>.tsv</td>
<td>text/tab-separated-values</td>
<td>A Tab Separated Value (TSV) file is a text format whose primary function is to store data in a table structure where each record in the table is recorded as one line of the text file. The field’s values in the record are separated by tab characters.</td>
</tr>
<tr class="odd">
<td>VPF</td>
<td></td>
<td>model/x-oms.vpf</td>
<td>The Vector Product Format (VPF) is a standard format, structure, and organization for large geographic databases.</td>
</tr>
<tr class="even">
<td>WAV</td>
<td>.wav</td>
<td>audio/wav</td>
<td>The Waveform Audio (WAV) file format was originally standardized by Microsoft and IBM. It can be compressed, but is typically used uncompressed, and usually is encoded with a linear pulse-code modulation (PCM) format.</td>
</tr>
<tr class="odd">
<td>WMA</td>
<td>.wma</td>
<td>audio/x-ms-wma</td>
<td>The Windows Media Audio (WMA) format was standardized by Microsoft. It refers both to a file format and audio codec (a device or computer program capable of coding or decoding a digital data stream of audio).</td>
</tr>
<tr class="even">
<td>XML</td>
<td>.xml</td>
<td>text/xml</td>
<td>Extensible Markup Language (XML) is a markup language and common file format for storing, transmitting, and reconstructing arbitrary data.</td>
</tr>
<tr class="odd">
<td>XSD</td>
<td>.xsd</td>
<td>application/xml</td>
<td>An Extensible Markup Language (XML) Schema Definition (XSD) describes and validates the structure and content of an XML document. It is primarily used to define the elements, attributes and data types the document can contain.</td>
</tr>
</tbody>
</table>

##### Product Persistence

The producer of the data product publishes an expiration time (in
Coordinated Universal Time (UTC) format) as part of the
**ProductLocation** message. Subscribers have no guarantee that the
product will be available after that time. In the case of a stored
product, the Producer may delete the product even if a Consumer has it
open.

##### Non-Streaming Data Transfers

This section describes the method of transferring non-streaming data
products via a file system. The file system may support NFS, FTP, FTPS,
HTTP, HTTPS or JPIP, but does not interact with Subsystems, Services, or
Isolators using OMS messages. Publishers generate data products and then
notify interested parties via two OMS messages that those products are
available for retrieval: **ProductMetadata** and **ProductLocation**.
Figure 6.3-3, Non-Streaming Data Products via Files, illustrates the
sequence of steps and the relationship between OMS Messaging and the
Data Transfer Protocols being used.

<img src="media/image23.png" style="width:6.79221in;height:3.88593in" />

<span id="_Toc219290707" class="anchor"></span>Figure 6.3-3
Non-Streaming Data Products via Files

Once a Subsystem, Service, or Isolator produces a data product that is
of interest to other Subsystems, Services, and Isolators in the Mission
Package, it stores the data on a file server and publishes the
**ProductMetadata** and **ProductLocation** messages on an agreed upon
topic. When Subsystems, Services, or Isolators that have subscribed to
that topic and are interested in that data product see these messages,
they then retrieve the data product using the information stored in
these messages. The **ProductLocation** message has an expiration field
in it that indicates the product will be available until that time.
After the indicated time has passed, there is no guarantee that the
product will remain available.

A Subsystem can host an internal file server that it exposes to the ASB
for transferring data products to other Subsystems, Services, or
Isolators. The interface between this Subsystem and its internal file
server is not controlled by the OMS Standard and any method of moving
data between is allowed. However, the interface between this
Subsystem-hosted file server and other Subsystems, Services, or
Isolators is controlled by the OMS Standard as Data Transfers. This file
server must adhere to the same requirements for the file servers
provided by the Platform.

##### Non-Streaming Data Products via Sockets

This section describes the method of transferring a data product
directly between any two Subsystems, Services, or Isolators, without
using a file system as an intermediary. Publishers notify interested
parties via two OMS messages when data products are available:
**ProductMetadata** and **ProductLocation**. Figure 6.3-4, Non-Streaming
Data Products via Sockets, illustrates the sequence of steps and the
relationship between OMS Messaging and the Data Transfer Protocols being
used. Although the example shown is specific to TCP, the general pattern
applies to UDP as well.

<img src="media/image24.png" style="width:6.5in;height:3.58333in" />

<span id="_Toc219290708" class="anchor"></span>Figure 6.3-4
Non-Streaming Data Products via Sockets

Once a Subsystem, Service, or Isolator has a data product to share, it
sends out the **ProductMetadata** and **ProductLocation** messages on an
agreed upon topic. If the Publisher has chosen to make the data product
available via TCP as in the example in Figure 6.3-4, Non-Streaming Data
Products via Sockets, the **ProductLocation** message will contain a TCP
URI including a hostname and port number. When Subsystems, Services, or
Isolators that have subscribed to that topic see these messages, they
realize the data product should be transferred using TCP and the
provided host name or IP address and port number. The
**ProductLocation** message has an expiration field in it that indicates
the product will be available until a given time. After the indicated
time has passed, there is no guarantee that the product will remain
available.

OMS allows a lightweight protocol for data transfer via raw TCP sockets.
The protocol is simply for the Publisher to stream the data product
associated with a TCP host and port to any subsystem or service that
connects to the specified host and port. Since there is no indication of
how large the data product is, the Publisher must terminate the
connection when it has finished sending. Upon seeing this, the
Subscriber knows that the data product has been fully received and it
must also close the connection from its side.

##### Streaming Data Products

Some data products can be transferred between Subsystems, Services, and
Isolators using data streaming, such as STANAG 4607 detections and MISP
video and audio. The associated formats include packets or frames that
enable a Subscriber to process a (partial) data product that they begin
consuming mid-stream. There is no requirement for Publishers to store or
buffer streaming data products. This means that for streaming data
products, a Subscriber might not receive the part of the stream produced
in the past.

##### Remote Direct Memory Access Data Transfers

When using RDMA, there are a series of initialization or setup messages
that will need to be exchanged before the transfers can begin. Once the
initialization has been completed, data movement is accomplished via a
call to a libfabric API that specifies the appropriate information about
the data product for both the source and destination memories. The two
messages used to coordinate the transfer of data products within the OMS
Mission Package are **RDMA\_Initialize** and **RDMA\_InitializeSetup**.
The **RDMA\_Initialize** represents a publisher connection ready for
connection by a subscriber, while the **RDMA\_InitializeSetup**
represents a subscriber’s request to open an RDMA connection and may
include an **RDMA\_Initialize** response in agreement to establish the
connection. For most RDMA data transfers, these two messages are
adequate for connection establishment. Other messages, such as
**FileLocation** and/or **ProductLocation**, can be used to coordinate
the location of the desired product and drive the need/parameters of the
RDMA connection.

### Special Signals

This section specifies the definition of and required signal
characteristics for all normative non-message-based signals that are
sent outside the boundary of a given Subsystem for inclusion as part of
the Platform's logical ASB. These signals are used where performance
(e.g., latency) or safety/security concerns preclude the use of OMS
messaging. The OMS Message set includes the data required to accomplish
some functionality formerly provided by special signals in many legacy
subsystems. These signals have been specifically identified in Table
6.3-13, Non-OMS Special Signals Superseded by OMS Messages, and should
be replaced by OMS Message-based interactions. Finally, Table 6.3-12,
Non-OMS Special Signals Allowed in the OMS Standard, lists a set of
signals that have been reviewed and explicitly limited to Tier 2 in the
OMS Standard.

#### Discrete Signals

Discrete signals communicate a Boolean or continuous range of analog
values through some measurement of voltage (open, short to ground,
2-line differential, ground referenced value, etc.) Table 6.3-9, OMS
Discrete and Voltage Reference Signals, provides the standard Discrete
and Voltage Reference Signals identified for all OMS Subsystems.

<span id="_Toc219290730" class="anchor"></span>Table 6.3-9 OMS Discrete
and Voltage Reference Signals (Note 1)

<table>
<thead>
<tr class="header">
<th>#</th>
<th>Signal Name</th>
<th>Description</th>
<th>Examples of Usage/ Other Signal Name</th>
<th>General Use</th>
<th>Signal Definition</th>
<th>Source/Destination</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>1</td>
<td>Subsystem Present</td>
<td>This discrete is used to tell the vehicle management software that the Subsystem is installed.</td>
<td>Equipment present</td>
<td><p>-Signal shorted if Subsystem is installed.</p>
<p>-Signal “1” or “0”. Can be a voltage level or Gnd.</p></td>
<td><p>1) Open/short - signal shorted to ground if Subsystem installed/present; open circuit indicates Subsystem not present</p>
<p>2) +28V per MIL-STD-704 or NATO STANAG 3456 indicates Subsystem present; 0V indicates not present. if used in this way, also indicates that the Subsystem has power applied; 0V indicates Subsystem not present or not powered</p></td>
<td>From Subsystem to Platform exec (vehicle management)</td>
</tr>
<tr class="even">
<td>2</td>
<td>Subsystem On</td>
<td>This signal is used to tell the Subsystem to turn ON. This is separate to the input power pins.</td>
<td>Radar On</td>
<td><p>-Operator physically turning Subsystem on - power applied. Typically used for legacy subsystems.</p>
<p>-Signal represents the application of power to a Subsystem automatically or via a switch or circuit breaker.</p>
<p>-Signal used for systems and power initialization sequences and/or resets.</p></td>
<td>1) +28V per MIL-STD-704 or NATO STANAG 3456 will command the Subsystem to turn ON. 0V commands the Subsystem to turn OFF. This is a low current interface and is separate from the main power input.</td>
<td>From operator interface to Subsystem</td>
</tr>
<tr class="odd">
<td>3</td>
<td>Emergency Mode</td>
<td>This signal is used to tell the Subsystem to continue to operate in the presence of faults or warnings (such as over temperature)</td>
<td><p>Emergency mode</p>
<p>Battle override</p></td>
<td>-Operator physically configuring Subsystem to emergency mode to force continued operation</td>
<td>1) +28V per MIL-STD-704 or NATO STANAG 3456 will command the Subsystem to continue operating. 0V allows the Subsystem to react normally.</td>
<td>From operator interface to Subsystem</td>
</tr>
<tr class="even">
<td>4</td>
<td>Safety Interlock</td>
<td>This signal provides the Subsystem with state data to inhibit Subsystem operation for safety reasons, such as weight on wheels.</td>
<td>Weight on Wheels</td>
<td><p>-Inhibits operation. Examples: weight on wheels, Laser Safe/Arm, Laser Enable, Laser Fire.</p>
<p>-Signal represents a safety lock mechanism used to ensure a Subsystem does not enter a (potentially) hazardous system state by accident or mistake.</p>
<p>-Note that Subsystem safety is not to be confused with Mission Critical (e.g., Safety of Flight).</p></td>
<td><p>1) Open/short</p>
<p>A signal shorted to ground indicates that potentially hazardous Subsystem operations are permitted. An open signal indicates that potentially hazardous Subsystem operations are not permitted.</p>
<p>2) +28V per MIL-STD-704 or NATO STANAG 3456.</p>
<p>A +28V signal indicates that potentially hazardous Subsystem operations are permitted. A 0V or open signal indicates that potentially hazardous Subsystem operations are not permitted.</p></td>
<td>From hazardous condition sensor(s) to Subsystem</td>
</tr>
<tr class="odd">
<td>5</td>
<td>Data Load</td>
<td>This signal is used by the Subsystem to know when it is allowed to load external data.</td>
<td>MDF Switch</td>
<td>-Allows data (ex. OFP, MDF) to be loaded. Subsystem will stop current operation</td>
<td><p>1) RS-422 differential (positive differential is true and allows loading, negative is false)</p>
<p>2) Low-Voltage Transistor-Transistor Logic (LVTTL)</p>
<p>(3V or 3.3V is true and allows loading, 0V is false)</p>
<p>3) Open/short - signal shorted to ground is true and allows loading; open circuit indicates FALSE</p></td>
<td>From Data Loader (Support Equipment) to Subsystem</td>
</tr>
<tr class="even">
<td>6</td>
<td>Zeroize/Erase</td>
<td><p>This signal is used by the Subsystem to invoke a sanitization of data within the Subsystem.</p>
<p>(It may also be part of messaging or supplemented by messaging.)</p></td>
<td><p>Zeroize/Erase, Classified Data Erase</p>
<p>Sanitize</p></td>
<td><p>-Erase sensitive data</p>
<p>-Signal represents the erasing of data in memory locations.</p></td>
<td><p>1) Open/short</p>
<p>A signal shorted to ground enables the erase command.</p>
<p>2) +28V per MIL-STD-704 or NATO STANAG 3456.</p>
<p>A +28V signal enables the erase command.</p></td>
<td>Platform to Subsystem</td>
</tr>
<tr class="odd">
<td>7</td>
<td>Blanking Pulse</td>
<td>This signal identifies when a Subsystem is transmitting. There may be multiple blanking pulses per Subsystem.</td>
<td>Radio Frequency (RF) interference pulse, Interference Blanker(s), Link 16 Pulse Blanker, Rotor Blade Sensor</td>
<td>-Signal represents an interruption of transmission or reception in frequency, band or timing to avoid interference or saturation.</td>
<td><p>1) 2-line differential - Logical true: (Line A - Line B) &gt; 2.5V, Logical false: (Line A - Line B) &lt; -2.5V</p>
<p>2) RS-485 differential - logical true is positive</p>
<p>3) Open/short - signal shorted to ground is true; open circuit indicates false</p></td>
<td><p>Transmitting Subsystem to other Subsystems</p>
<p>Platform to Subsystem (if centrally controlled)</p></td>
</tr>
<tr class="even">
<td>8</td>
<td>Transmit Override/ Inhibit</td>
<td>This signal requests that a Subsystem transmission be inhibited while the signal is active</td>
<td>Jam Look Thru Request</td>
<td>-Subsystem transmit operation is superseded.</td>
<td><p>1) 2-line differential - Logical true: (Line A - Line B) &gt; 2.5V, Logical false: (Line A - Line B) &lt; -2.5V</p>
<p>2) RS-485 differential - logical true is positive</p></td>
<td><p>Platform to Subsystem</p>
<p>Subsystem to Subsystem</p></td>
</tr>
<tr class="odd">
<td>9</td>
<td>Receive Override/ Inhibit</td>
<td>This signal tells a Subsystem to stop receiving operations</td>
<td></td>
<td>-Subsystem receive operation is superseded.</td>
<td>1) 2-line differential - Logical true: (Line A - Line B) &gt; 2.5V, Logical false: (Line A - Line B) &lt; -2.5V</td>
<td><p>Platform to Subsystem</p>
<p>Subsystem to Subsystem</p></td>
</tr>
<tr class="even">
<td>10</td>
<td>Platform ID</td>
<td>This set of discretes provides information about a unique id number of the platform (e.g., aircraft) that the Subsystem is installed in.</td>
<td></td>
<td>-Signal represents the unique ID of the host platform</td>
<td>1) Open/short - signal shorted to ground to provide a series of bits to identify the ID</td>
<td>From Platform to Subsystem, or in the harness itself.</td>
</tr>
<tr class="odd">
<td>11</td>
<td>Subsystem Configuration</td>
<td>This discrete or set of discretes is used to provide configuration data for the role or location of the Subsystem. Examples: left/right side.</td>
<td></td>
<td>-Reconfigures Subsystem.</td>
<td><p>1) Open/short - signal shorted to ground to provide a series of bits to provide configuration data</p>
<p>2) Jumpers between pins</p></td>
<td>From Platform to Subsystem</td>
</tr>
<tr class="even">
<td>12</td>
<td>Expendable Enable</td>
<td>This signal enables an expendable.</td>
<td>Expendable Enable</td>
<td>-Provides enable for expendable use.</td>
<td><p>1) a conditioned 5v (Transistor-Transistor Logic (TTL) Signal), with 5V being true</p>
<p>2) 28V, per MIL-STD-704</p></td>
<td>Subsystem to expendable</td>
</tr>
<tr class="odd">
<td>13</td>
<td>Expendable Jettison/ Launch</td>
<td>This signal commands the launch of an expendable</td>
<td>Weapon launch</td>
<td>-Jettison/Launch command signal used by radar to know when an expendable has been launched</td>
<td><p>2-line differential</p>
<p>1– True (logic 1) – launch initiate</p>
<p>0 – False (logic 0)- no launch</p>
<p>True: (Line A - Line B) &gt; 2.0V</p>
<p>False: (Line A - Line B) &lt; -2.0V</p></td>
<td>Subsystem to expendable, also Service to Subsystem</td>
</tr>
<tr class="even">
<td>14</td>
<td>Rotor Blade Sensor</td>
<td>This signal provides a synchronization pulse for the phase of the rotor to be used to deconflict modulation artifacts.</td>
<td></td>
<td></td>
<td>1) 2-line differential - Logical true: (Line A - Line B) &gt; 2.5V, Logical false: (Line A - Line B) &lt; -2.5V</td>
<td>Platform to Subsystem</td>
</tr>
<tr class="odd">
<td>15</td>
<td>Shared Aperture Available</td>
<td>This discrete indicates when a shared aperture is available. May require more than one discrete. May also use a high speed data bus.</td>
<td>Link 16 Advanced Slot Notification</td>
<td>-Notifies master system when shared aperture available for use.</td>
<td>1) RS-422</td>
<td>Subsystem to Subsystem</td>
</tr>
</tbody>
</table>

Note 1: The signals listed in this table are normative signals - this
interface is standard for all OMS implementations.

#### Time Reference Signals

Please see Section 6.5.5, Time Reference and Time Synchronization, for
definition of time synchronization messages and signals. See also Table
6.3-10, OMS Discrete and Voltage Time Reference Signals.

<span id="_Toc219290731" class="anchor"></span>Table 6.3-10 OMS Discrete
and Voltage Time Reference Signals

<table>
<thead>
<tr class="header">
<th>Signal Name</th>
<th>Description</th>
<th>Example of Usage/Other Signal Name</th>
<th>General Use</th>
<th>Signal Definition</th>
<th>Source/Destination</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IRIG B</td>
<td>IRIG B is part of the IRIG Serial Time Codes family of formats that use coded bits sent within an established time frame to simultaneously synchronize time and send time data. Time code B sends 100 bits of information within a 1 second time frame and contains time-of-year and year information in a BCD format, and time-of-day information in SBS.</td>
<td>Time Synchronization and date/time information</td>
<td>Used by Subsystems for high precision time synchronization while providing date and time information.</td>
<td>In accordance with IRIG 200-04, September 2004. Latest IRIG Format standard is 200-16, August 2016.</td>
<td>Platform to Subsystem</td>
</tr>
<tr class="even">
<td>1 Pulse Per Second (1 PPS)</td>
<td>This signal, along with the <strong>SystemTimeAtReference</strong> OMS Message, provides a precision time synchronization between Subsystems and the navigation and/or GPS systems.</td>
<td>Time Rollover Pulse</td>
<td>The <strong>SystemTimeAtReference</strong> message indicates the time at the leading edge of the previous 1 PPS pulse.</td>
<td><p>Twisted shielded pair, 50 ohm, +5V to +12V pulse</p>
<p>Differential pair (such as RS-485)</p>
<p>Coax signal</p>
<p>ICD-GPS-060, Rev. B.</p></td>
<td>Platform to Subsystem</td>
</tr>
<tr class="odd">
<td>BCD Time Code</td>
<td>This signal provides a Binary Coded Decimal (BCD) time message to be used in association with the 1 PPS signal.</td>
<td>Time Information</td>
<td>This signal is used by the subsystems which connect directly to the GPS or other time source which does not support a <strong>SystemTimeAtReference</strong> OMS message.</td>
<td>A Binary Coded Decimal (BCD) message consisting of time of day (UTC), day of year, and Time Figure of Merit (TFOM) signal, as defined in ICD-GPS-060, Rev. B.</td>
<td>From Navigation or GPS system to Subsystem</td>
</tr>
<tr class="even">
<td>Time Fault Discrete</td>
<td>This signal provides fault information associated with the 1 PPS and BCD time code implementations.</td>
<td>Fault Information</td>
<td>This signal supplements the implementation of the 1 PPS using the BCD Time Code interface.</td>
<td>A discrete signal as defined in ICD-GPS-060, Rev. B.</td>
<td>From Navigation or GPS system to Subsystem</td>
</tr>
</tbody>
</table>

#### Frequency Reference, Shared Radio Frequency, and Intermediate Frequency Signals

There are no normative frequency references, Radio Frequency (RF), or
Intermediate Frequency (IF) signals defined within OMS. These signals
are nearly always Platform and application specific with the only common
parameter being 50 Ohm impedance.

#### High-Speed Data Lines

High-speed data lines are used to move data quickly between subsystems
when latency or bandwidth requirements exceed the capacity of the
message-based network.

There are no normative high speed/low latency Special Signals within OMS
due to the rapid evolution of these types of signals. These are
application specific, and their use will be defined by the system
integrator.

#### Other Signals

Table 6.3-11, Other Signals Defined within OMS, identifies other signals
that are defined within OMS.

<span id="_Toc219290732" class="anchor"></span>Table 6.3-11 Other
Signals Defined within OMS

<table>
<thead>
<tr class="header">
<th>#</th>
<th>Signal Name</th>
<th>Description</th>
<th>Examples of Usage/Other Signal Name</th>
<th>General Use</th>
<th>Signal Definition</th>
<th>Source/Destination</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>33</td>
<td>Key Fill</td>
<td>Standard Key Fill</td>
<td></td>
<td></td>
<td>Per DS-101 EKMS 308</td>
<td>External Device to Subsystem</td>
</tr>
</tbody>
</table>

#### Non-OMS Special Signals Allowed in the OMS Standard

Table 6.3-12, Non-OMS Special Signals Allowed in the OMS Standard,
identifies the signals considered outside the bounds of OMS
standardization. However, these signals are allowed but OMS compliance
will be restricted to no more than Tier 2. It is highly recommended that
these signals be replaced by other OMS Data Exchanges, specifically Data
Transfer that includes digital Video and Audio data types, as documented
in Table 6.3-4, Data Transfer Formats, APIs, and Protocols. For example,
legacy analog audio and video signals that use A/D converters will
likely use Data Transfers, so Table 6.3-12 would not apply.

<span id="_Toc219290733" class="anchor"></span>Table 6.3-12 Non-OMS
Special Signals Allowed in the OMS Standard

<table>
<thead>
<tr class="header">
<th>#</th>
<th>Signal Name</th>
<th>Type</th>
<th>Description and Reason for Limiting OMS Compliance</th>
<th>General Use</th>
<th>Signal Definition</th>
<th>Source/Destination</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>35</td>
<td>Legacy Analog Video</td>
<td>IF Signal (Video Signal)</td>
<td><p>This signal provides analog video, typically for displays.</p>
<p>Note that digital video can be treated as a Subsystem data product, not as an OMS Message. Otherwise, digital video data transfers can be used.</p></td>
<td>Display</td>
<td>EIA-170, among others</td>
<td>Subsystem to Platform</td>
</tr>
<tr class="even">
<td>36</td>
<td>High Definition Video</td>
<td>High-Speed Data (Video Signal)</td>
<td><p>This signal provides digital video, typically for displays.</p>
<p>Note that digital video can be treated as a Subsystem data product, not as an OMS Message. Otherwise, digital video data transfers can be used.</p></td>
<td>Display or Image Auto Tracking</td>
<td>SMPTE 292M, among others</td>
<td>Subsystem to Platform</td>
</tr>
<tr class="odd">
<td>26</td>
<td>Analog Audio</td>
<td>Discrete</td>
<td><p>This signal provides analog audio, used as warnings and cautions, as well as voice, tones and other modulations.</p>
<p>Note that digital audio can be treated as a Subsystem data product, not as an OMS Message. Otherwise, digital audio data transfers can be used.</p></td>
<td>Demodulated audio, warnings, cautions, and voice</td>
<td>Analog, with application specific peak-to-peak voltages and impedances</td>
<td><p>Subsystem to Platform</p>
<p>Subsystem to Subsystem</p></td>
</tr>
</tbody>
</table>

#### Non-OMS Special Signals Superseded by OMS Messages

Table 6.3-13, Non-OMS Special Signals Superseded by OMS Messages,
identifies signals that are not supported by the OMS Standard because
OMS Messages are highly recommended for these functions. However, the
use of these signals are allowed but OMS compliance assessment will be
restricted to no more than Tier 2.

<span id="_Toc219290734" class="anchor"></span>Table 6.3-13 Non-OMS
Special Signals Superseded by OMS Messages

<table>
<thead>
<tr class="header">
<th>#</th>
<th>Signal Name</th>
<th>Type</th>
<th>Description and Reason for not being included in the Standard</th>
<th>General Use</th>
<th>Signal Definition</th>
<th>Source/Destination</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>37</td>
<td>Reset</td>
<td>Hardwired Discrete</td>
<td><p>This signal is used by the Subsystem to invoke a soft reset of the Central Processing Unit (CPU).</p>
<p>This signal is frequently present as an external Input/Output (I/O) for Subsystems, but does not need to be included in the OMS Standard since it is uncommon to be part of the Platform interface.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system. For example, use the <strong>SubsystemStateCommand</strong> message with CommandedState set to PRE_INITIALIZATION.</p></td>
<td><p>-Resets Subsystem operation</p>
<p>-Different signals represent different levels of reset such as Line Replaceable Unit (LRU) power, SW, etc.</p>
<p>-May also be a short to ground or voltage.</p></td>
<td><p>1) RS-422 differential (positive differential is true and activates a reset, negative is false)</p>
<p>2) RS-485 differential (positive differential is true and activates a reset, negative is false)</p>
<p>3) Discrete voltage (5V, 3V or 3.3V) is true and activates a reset, 0V is false)</p>
<p>4) Open/short - signal shorted to ground is true and activates a reset; open circuit indicates FALSE</p></td>
<td>Platform to Subsystem</td>
</tr>
<tr class="even">
<td>38</td>
<td>Subsystem Ready</td>
<td>Hardwired Discrete</td>
<td><p>This discrete is used to tell the vehicle management software that the Subsystem is powered up and is not in the OFF mode.</p>
<p>This is a non-normative signal.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system.</p>
<p>For example, use the <strong>SubsystemStatus</strong> message and check the value of SubsystemState.</p></td>
<td><p>-Signal set to false if Subsystem is not operating. Used for built in test (BIT) and Fault Detection/Fault Isolation (FD/FI).</p>
<p>-Signal represents Subsystem “Stand-by” condition or mode.</p>
<p>-Signal represents presence of power discrete used for Initiated BIT (IBIT), Power-on BIT (PBIT), and Continuous BIT (CBIT).</p>
<p>-Signal can be used as the end state of System Initialization and/or Reset.</p></td>
<td><p>1) Open/short - signal shorted to ground if Subsystem is powered up; may also be used to indicate successful initialization and passage of BIT; open circuit indicates no power or failure to initialize</p>
<p>2) +28V per MIL-STD-704 or NATO STANAG 3456 indicates Subsystem present; 0V indicates not present. If used in this way, also indicates that the Subsystem has power applied; 0V indicates no power or failure to initialize</p>
<p>3) 2-line differential signal. Logical true: (Line A - Line B) &gt; 2.5V; Logical false: (Line A - Line B) &lt; -2.5V</p></td>
<td><p>From Subsystem to Platform exec</p>
<p>From Subsystem to Operator Interface</p></td>
</tr>
<tr class="odd">
<td>39</td>
<td>Subsystem Operate</td>
<td>Hardwired Discrete</td>
<td><p>This signal is used to tell the Subsystem to change to one of the operating states.</p>
<p>This is a non-normative signal.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system. For example, use the <strong>SubsystemStatus</strong> message and check the value of SubsystemState.</p></td>
<td><p>-Operator physically configuring Subsystem for operation. Typically used for legacy subsystems.</p>
<p>-May also be implemented as a digital signal.</p></td>
<td>1) +28V per MIL-STD-704 or NATO STANAG 3456 will command the Subsystem to go into the desired state. 0V allows the signal to return to another state.</td>
<td>From operator interface to Subsystem</td>
</tr>
<tr class="even">
<td>40</td>
<td>Subsystem On Status</td>
<td>Hardwired Discrete</td>
<td><p>This discrete is used to tell the vehicle management software what state the Subsystem is in.</p>
<p>This is a non-normative signal.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system. For example, use the <strong>SubsystemStatus</strong> message and check the value of SubsystemState.</p></td>
<td><p>-Confirmation Subsystem is operating.</p>
<p>-May also be implemented as a digital signal.</p></td>
<td>Traditionally discrete voltages, from 5 V TTL to 28 VDC</td>
<td>Subsystem to Platform</td>
</tr>
<tr class="odd">
<td>41</td>
<td>Data Select</td>
<td>Hardwired Discrete</td>
<td><p>This signal is used by the Subsystem to select the data file it should be using.</p>
<p>This is a non-normative signal.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system. For example, use the <strong>*CapabilitySettingsCommand</strong> and <strong>*CapabilitySettingsCommandStatus</strong> messages.</p></td>
<td>-Select data file. Ex. MDF Select.</td>
<td></td>
<td>From Platform to Subsystem</td>
</tr>
<tr class="even">
<td>42</td>
<td>Fault Detection / Fault Isolation (FD/FI)</td>
<td>Hardwired Discrete</td>
<td><p>This signal indicates the presence of a fault. There may be multiple lines to define different faults.</p>
<p>This is a non-normative signal.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system. For example, use the <strong>Fault</strong> and/or <strong>SubsystemBIT_Status</strong> messages.</p></td>
<td><p>-Provides additional insight into BIT failures. Typically used for legacy subsystems.</p>
<p>-Fault Detection/Fault Isolation signals may also be digital messages.</p></td>
<td><p>1) Open/short - signal shorted to ground is a fault open circuit indicates FALSE</p>
<p>2) RS-422, positive voltage is a fault</p>
<p>3) Data Bus, -1553 or ARINC-like</p></td>
<td>From Subsystem to Platform</td>
</tr>
<tr class="odd">
<td>43</td>
<td>Navigation</td>
<td>Various</td>
<td><p>This signal represents legacy navigation inputs into Subsystems.</p>
<p>This is a non-normative signal.</p>
<p>It is preferred that this signal information be provided by messaging in an OMS system. For example, use the <strong>PositionReport</strong> or <strong>PositionReportDetailed</strong> messages.</p></td>
<td><p>-Navigation &amp; Altimeter information. Typically used for legacy subsystems.</p>
<p>-Signal may also be conveyed on a digital bus.</p></td>
<td></td>
<td><p>Subsystem to Subsystem</p>
<p>Platform to Subsystem</p></td>
</tr>
</tbody>
</table>

### Security Information Exchanges

OMS Security Information Exchanges do not impose requirements on the
security analysis and security design approaches of Architecture
Elements. OMS Security Information Exchanges assume that the underlying
security posture of the data exchange endpoints is already in place.
Security Information Exchanges provide a mechanism for trusted
information exchanges to supplement the Program Protection capabilities
of the OMS Architecture Elements and facilitate the Mission Package
security architecture. Security Information Exchanges include exchanges
needed to support Anti-Tamper (AT) and Cybersecurity solutions.

Security Information Exchanges have been standardized in the AT
Interface Control Document (AT ICD), OMSC-SPC-009. OMS Cybersecurity
Security Information Exchanges have not been standardized beyond what is
inherent in the UCI Schema. OMS requires that the element’s security
implementation be documented in the MPDD and PDD as appropriate.
Specific requirements pertaining to Security Information Exchanges can
be found in Section 7, Compliance.

Isolators
---------

An Isolator is an OMS Architecture Element that is only comprised of one
or more software components. An Isolator operates between an OMS Mission
Package and elements external to the OMS Mission Package; its OMS-facing
interface and predefined constraints and policies are specified by a
non-proprietary Service Contract. An Isolator separates OMS Data
Exchanges on the OMS Platform from elements external to the OMS Mission
Package with the express purpose of preventing unwanted interactions and
cross-coupling interference, while at the same time providing the means
for the OMS Architecture Elements of an OMS Mission Package to interact
with external elements. In some cases, an Isolator, which is a Service
with OMS interfaces on one side and safety critical interfaces (for
example, flight safety) on the other, may be required to be certified.
In other cases, if the safety critical interfaces themselves are well
defined and their use is certified already, an Isolator that uses these
certified interfaces may not require certification. Although Figure
3.2-1, Example OMS Architecture Implementation, depicts Isolators being
entirely contained within OMS (highlighted in the figure by being
contained within blue rectangular outline labeled “OMS Mission
Package”), there may exist complementary portions on the non-OMS side of
the isolation layer that provide the data necessary to cross the
isolation boundary.

An Isolator solely performs a data management process, which may include
message format conversion, message protocol conversion, and
implementation of specific rules and business logic to satisfy the
Isolator’s interface to the external system to accomplish isolation
between the Platform and other elements external to the Mission Package.
An Isolator by itself does not provide an OMS Capability, however an
Isolator can advertise a Capability for an external system as an OMS
Capability for use inside the OMS Mission Package.

An Isolator is a special Service that can be hosted in the OCE or Other
Mission Processing. An Isolator is not allowed to be hosted in an OMS
Subsystem unless it is specifically hosted in the OCE provided by the
physical Subsystem since that OCE is considered part of the Platform and
not part of the logical Subsystem. An Isolator will report status via
the **ServiceStatus** message for the OMS-facing side of the Isolator as
previously described in Section 6.1.1, Service State Transition
Behaviors. To ensure loose coupling, OMS follows a publish/subscribe
paradigm for OMS Messaging abstracted by the CAL. The knowledge of OMS
Messages for an Isolator is limited to publishing and subscribing via
topics. Therefore, the OMS-facing side of an Isolator will focus on OMS
Messages rather than source or destination.

An Isolator cannot be an OMS Subsystem. If the Isolator runs on
specialized hardware, that hardware may be considered part of the
Platform as Other Mission Processing.

An Isolator boundary is defined as where the Isolator communications
(e.g., messages, data transfer, signals, etc.) enter or exit the
Isolator. An Isolator boundary delineates the extent of an Isolator.
Inside the Isolator boundary are all of the hardware and software
elements of the Isolator to implement its functionality and conform to
OMS requirements. Figure 6.4-1, Example Isolator Boundary between OMS
Mission Package and External Elements, shows how an Isolator interfaces
a Platform to elements external to a Mission Package. The OMS Data
Exchanges shown in this figure interface to the OMS-facing side of the
Isolator. External elements interface to the non-OMS-facing side of the
Isolator as indicated by the black line.

<img src="media/image25.png" style="width:6.5in;height:3.41667in" />

<span id="_Toc219290709" class="anchor"></span>Figure 6.4-1 Example
Isolator Boundary between OMS Mission Package and External Elements

When an Isolator uses Platform resources, such as an OCE, Other Mission
Processing, or data storage, those resource requirements needed by the
Isolator must be documented in the appropriate OMS documentation (i.e.,
Service Contract). This includes any use of the Platform ASB hardware to
exchange information between constituent parts of the Isolator.

In summary, all information exchanges that cross an Isolator boundary
must be fully documented in the appropriate OMS documentation (i.e.,
Service Contract), with the following exceptions:

-   Information exchanges that cross the Isolator boundary facing
    elements external to the OMS Mission Package do not need to be
    documented in OMS documentation.

-   Direct information exchanges between internal, constituent parts of
    an Isolator do not need to be documented in OMS documentation,
    except for any Platform resource requirements as stated above.

> RQMT STD-000427 \[An OMS Isolator shall be documented in a
> non-proprietary Service Contract, in accordance with the OMS Service
> Contract Template, for its interfaces that cross the OMS-facing
> Isolator boundary.\]
>
> RQMT STD-000431 \[An OMS Isolator shall use the OMS CAL, for its
> interfaces that cross the OMS-facing Isolator boundary, to send and/or
> receive OMS Messages over the OMS ASB.\]
>
> RQMT STD-006939 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator
> shall select from the corresponding data formats in column B of the
> “Data Transfer Formats, APIs, and Protocols” table for data transfers
> that cross the OMS-facing Isolator boundary.\]
>
> RQMT STD-006940 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator
> shall select from the corresponding protocols/APIs in column C of the
> “Data Transfer Formats, APIs, and Protocols” table for exclusive use
> data transfers that cross the OMS-facing Isolator boundary.\]
>
> RQMT STD-010121 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator
> shall select from the corresponding protocols/APIs in column D of the
> “Data Transfer Formats, APIs, and Protocols” table for shared
> read-only data transfers that cross the OMS-facing Isolator
> boundary.\]
>
> RQMT STD-006941 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator
> shall select from the corresponding protocols/APIs in column E of the
> “Data Transfer Formats, APIs, and Protocols” table for shared
> read/modify data transfers that cross the OMS-facing Isolator
> boundary.\]
>
> RQMT STD-006942 \[An OMS Isolator shall use the URI formats, as
> specified in the “OMS URI formats” table, for data transfers that
> cross the OMS-facing Isolator boundary.\]
>
> RQMT STD-008664 \[An OMS Isolator shall report status in accordance
> with the “Required Functions” section of the OMS Service Contract
> Template.\]
>
> RQMT STD-008665 \[An OMS Isolator shall implement configurable
> periodicity for reporting status.\]
>
> RQMT STD-008666 \[An OMS Isolator shall implement a configurable range
> for periodic update rate from 1 to 600 seconds in 1 second
> increments.\]
>
> RQMT STD-009707 \[An OMS Isolator shall document its cybersecurity
> posture in accordance with the “Cybersecurity Posture” Section of the
> OMS Service Contract Template.\]

The OMSC-GDE-003, Cybersecurity Guide, defines concepts and guidance for
OMS Adopting Programs and system designers to utilize for documenting
the OMS Architecture Element cybersecurity posture.

### External Standards

In the context of this section, the term “external standard” refers to a
MIL-STD, DoD Standard, Commercial Standard, STANAG, or similar document
that describes non-OMS data.

Data from external standards entering a Mission Package through an
Isolator are documented in the Data Transfer Formats, APIs, and
Protocols table to denote their use as allowable OMS Data Transfers.
Some of these data types are restricted in use because of overlap with
other OMS Data Exchanges, namely OMS Messaging. If an external standard
has overlap with existing OMS Messaging, the preferred solution is to
use OMS Messaging versus introducing the External Standard as a new Data
Transfer. The intent is that when there is overlap between OMS Messaging
and Data Transfer, the preferred solution is to encourage the use of OMS
Messaging.

For internal-to-internal exchanges, if there is overlap between an
external standard and OMS Messaging, the use of an OMS Data Transfer may
be approved for data types using the non-overlapping portion of the
external standard. An example of this is the approval of using STANAG
4607 formatted MTI detection data, which does not overlap with OMS
Messaging, as an OMS Data Transfer.

For exchanges between internal endpoints and external endpoints, the
external standard may “pass through” an Isolator to/from a
Service/Subsystem. However, that Service/Subsystem may not forward the
information in the format of the external standard internal to the
Mission Package. In these cases, a Change Request (defined in Section
7.1.1, Change Request Submission Guidelines) may approve the external
standard to be added to the Data Transfer Formats, APIs, and Protocols
table, but limited to a maximum assessed compliance level of Tier 2. As
part of the approval process to add this external standard to the Data
Transfer Formats, APIs, and Protocols table, a valid Information
Exchange Requirement (IER) for an adopting program is required.

In the following examples, the term “ExtStd” represents the format of
data from an external standard. Although an Isolator may not physically
transform the ExtStd data, the Isolator logically transforms the data
from an external standard to an OMS Data Transfer. In Figure 6.4-2,
“PipedExtStd” depicts this logical transformation and represents a data
type and format approved for Data Transfer.

Use case “A” of Figure 6.4-2 is an example of an internal-to-internal
transfer of an external standard. The Tracker chooses to send ExtStd
messages to Fusion Service within the Mission Package. Furthermore,
ExtStd has overlap with the Tier 1 Minimum Message Set. Overlap between
the external standard and OMS Messaging precludes the use of ExtStd as a
Data Transfer for internal-to-internal communications.

Use case “B” of Figure 6.4-2 is one of three examples of data exchange
between internal endpoints and external endpoints where an established
Information Exchange requirement (IER) identifies the use of ExtStd both
internally and externally to the Mission Package. In this case, the
Tracker Service sends ExtStd formatted data to External Systems. While
ExtStd does overlap with OMS Messaging, the destination of the Data
Transfer is external to the Mission Package. In this case, ExtStd could
be allowed as a Data Transfer in the Data Transfer Formats, APIs, and
Protocols table that is limited to a maximum assessed compliance level
of Tier 2.

Use case “C” of Figure 6.4-2 is the second example of data exchange
between internal endpoints and external endpoints. In this case, the
Data Transfer is bi-directional. While ExtStd overlaps with OMS
Messaging, the established IER makes this a candidate for a Data
Transfer that is limited to a maximum assessed compliance level of Tier
2.

Use case “D” of Figure 6.4-2 is the third example of data exchange
between internal endpoints and external endpoints. In this case,
multiple internal endpoints receive ExtStd data. However, the data is
not forwarded internally in ExtStd format. Note that Display and Fusion
may each produce an OMS Message from the ExtStd data and system
engineering may be required to address any conflicts this may cause in
the Mission Package. A documented IER makes this a candidate for a Data
Transfer that is limited to a maximum assessed compliance level of Tier
2.

Lastly, use case “E” of Figure 6.4-2 depicts the case where only part of
an external standard is allowed. STANAG 4607 not only includes a format
for MTI detection data but also provides other data that has overlap
with OMS Messaging. In this case, MTI detection data is allowed in the
format of STANAG 4607. No other STANAG 4607 format data is allowed, thus
eliminating any overlap with OMS Messaging.

<img src="media/image26.png" style="width:6.5in;height:6.89583in" />

<span id="_Toc219290710" class="anchor"></span>Figure 6.4-2 Driving Use
Cases for External Standard Usage

Platform
--------

An OMS Platform is an OMS Architecture Element, which is itself a
composite architecture. A Platform includes the ASB, mission processing
(including an OCE), and typically provides the time reference, time
synchronization mechanism(s), and position information for the Mission
Package. Unlike Subsystems and Services, Platforms do not provide
Capabilities. The Platform is assessed in accordance with the
non-proprietary Platform Description Document (PDD).

A Platform reflects, and documents in its PDD, the results of
significant top-level architecture/design trades and systems
implementation decisions, including:

-   The system-level security architecture, which may include:

<!-- -->

-   Identity

-   Endpoints (Node Processing)

-   Application

-   Data (Data in Motion, Data at Rest)

-   Network

-   Infrastructure

-   Etc.

<!-- -->

-   Externally visible implementation details of the ASB, including:

<!-- -->

-   Implementation(s) of the CAL

-   Transport implementations

-   Etc.

<!-- -->

-   Data Storage provisions

-   Provisioning of a time reference

-   Provisioning for time synchronization mechanism(s)

-   Provisioning for position information.

A Platform will include software that is not part of an OMS Service.
This software provides a measure of robustness for the underlying
infrastructure. One example is infrastructure software and settings
necessary to protect information passing through the ASB. A second
example is software that manages the underlying infrastructure such as
the network that forms the ASB, the processing elements that form
mission processing (including the OCE), and data storage.

The following subsections describe the architecture features provided as
a part of an OMS Platform.

### Abstract Service Bus (ASB)

The Abstract Service Bus (ASB) is a composite element that supports all
forms of OMS Data Exchanges. The ASB includes the physical layer that is
the foundation of the ASB’s other sub-elements. It is important to note
that the ASB is a logical construct, not a single physical element
distinct from other OMS elements, and is defined and provided as a part
of an OMS Platform. The ASB (and therefore the Platform) includes
components hosted on Subsystems, the Open Computing Environment (OCE),
and Other Mission Processing elements. Figure 6.5-1, Detailed Structure
Diagram for the ASB, provides a depiction of the ASB and its interaction
with other OMS elements.

<img src="media/image27.png" style="width:6.5in;height:5.29167in" />

<span id="_Toc219290711" class="anchor"></span>Figure 6.5-1 Detailed
Structure Diagram for the ASB

In general, the design details of the network infrastructure are
abstracted by the Critical Abstraction Layer. However, some commonly
used commercial standards for infrastructure management may extend above
the OMS abstraction layers and thus appear to be in conflict with OMS
messaging. One such example is the Simple Network Management Protocol
(SNMP) when used to control the state of subsystem and other
network-attached mission processing hardware. The OMS Standard intends
for SNMP to be allowable for use in any OMS-compliant system. Other
standards and methods for infrastructure management that extend beyond
the OMS abstraction layers have not been reviewed. Adopting Programs
using any such protocols should document their usage and submit them for
consideration as additional standards intended for use by an
OMS-compliant Platform. All standards used for infrastructure management
that require support from subsystems integrating with the ASB should be
called out in the Platform Description Document. In addition, support
for these standards should also be addressed in the Subsystem
Description Document for each Subsystem.

The OMS Data Exchanges provide common interfaces for data exchange while
maintaining large design flexibility in the implementation. There are,
however, some limitations and requirements placed on the ASB. For
example, the ASB must provide an Internet Protocol (IP) switched fabric
for use by the Data Transfer and Security Information Exchange elements.

> RQMT STD-000144 \[An OMS ASB shall support Internet Protocols IPv4 or
> IPv6.\]
>
> RQMT STD-000146 \[An OMS ASB shall provide the OMS CAL.\]
>
> RQMT STD-009706 \[An OMS ASB shall provide OMS Security Information
> Exchanges.\]

The physical transport for OMS Special Signals is included as part of
the ASB. The requirements for Special Signals are specified in the
Section 6.3.3, Special Signals.

### Critical Abstraction Layer (CAL)

A Critical Abstraction Layer (CAL) is an OMS architecture concept and
approach supporting the standardized OMS Messaging between the OMS
Platform and the Subsystems, Services, and Isolators that are part of an
OMS Mission Package. A CAL is realized by a CAL Implementation that
supports the CAL API used by Subsystems, Services, and Isolators.

The CAL API is the interface that Subsystems, Services, and Isolators
use to access the capabilities supported by a CAL (e.g., the exchanges
of OMS Messages). CAL APIs are designed to guarantee commonality of the
CAL API across CALs for the same OMS version for that language.

A CAL Implementation is a manifestation and fulfillment of the CAL API
that adheres to the requirements defined in the applicable CAL
Specification(s). One or more CAL Implementations serve as an integral
component of an OMS Platform Abstract Service Bus (ASB) and are provided
by the OMS Platform.

The CAL separates Subsystem, Service, and Isolator application software
from Platform specific CAL implementations (see Figure 6.5-2, An OMS
Platform’s ASB includes an OMS CAL). This separation includes, but is
not limited to, networks, messaging transports and protocols, and
message security (e.g., confidentiality, integrity, non-repudiation,
etc.). A Platform will include one or more CAL Implementations that
allow Subsystems, Services, and Isolators to communicate using OMS
Messages. The CAL API aids portability of Subsystems, Services, and
Isolators among OMS Mission Packages. The CAL allows applications to
interact (get, set, send, receive, etc.) with message objects regardless
of the underlying object implementation.

There are two families of OMS CALs: Language-Specific (C++ and Java) and
Language-Agnostic. A Language-Specific CAL provides a developer
standardized libraries derived from the OMS Message Set to interface
with the OMS Platform. A Language-Agnostic CAL uses a well-defined
representation of the OMS Message Set and defined protocols to interface
with the OMS Platform.

> RQMT STD-000190 \[An OMS CAL implementation shall be developed.\]

See OMSC-SPC-001, CAL Specification for details.

<img src="media/image28.png" style="width:6.5in;height:4.59375in" />

<span id="_Toc219290712" class="anchor"></span>Figure 6.5-2 An OMS
Platform’s ASB includes an OMS CAL

Note that the term “CAL” is commonly used to refer to both the ‘concept’
of a CAL, the generic ‘CAL Implementation” that is a fundamental part of
every OMS Platform architecture, as well as the specific CAL
Implementation corresponding to a particular OMS Platform.

#### Language-Specific CAL

A Language-Specific CAL Implementation (and generically, a CAL) is
composed of the following:

-   A language-specific set of interfaces to message objects that can be
    passed across CAL interface methods. These message interfaces are
    generated directly from the OMS Message Set

-   A set of interface methods for reading and writing OMS Messages

-   A set of interface methods for interacting with the ASB.

A set of Platform-specific and language-specific message interfaces are
generated from the OMS Message Set corresponding to a Platform. These
interfaces provide the defined way that all applications interact with
the CAL message objects. A set of “CAL Generation Tools” are maintained
that parse OMS Message Sets and produce the normative interface files
for all message objects in each supported language. These interface
files are what OMS Subsystems, Services, and Isolators compile against
to create, read, and write OMS Messages, as well as set and access the
fields in each message. Note that it is the intent of the OMS Standard
to ensure that Services which are built with various language bindings
(e.g., C++, Java) and for different operating environments (e.g.,
Windows, Linux) on the same OMS Platform will be able to interact as
documented in the Mission Package implementation design. The ASB
provider is responsible for generating the libraries that implement the
message object interfaces. The ASB provider may select any desired
process and tool chain with which to generate the message library,
including using the CAL Generation Tools with custom ASB generators.

The CAL Generation Tools generate the interface for the ASB, factories,
readers, writers, and message objects.

#### Language-Agnostic CAL

The Language-Agnostic CAL is composed of the following:

-   At least one approved protocol used for establishing a connection to
    and interacting with the Platform

-   A compatible message format identified by the protocol for
    publishing and receiving OMS Messages

-   At least one Platform hosted endpoint for each implemented protocol
    and message format pair

A language-agnostic CAL is not a requirement of the Platform nor is it a
replacement of language-specific CALs. If applicable, the Platform can
provide a language-agnostic CAL in addition to the language-specific
CAL. The language-agnostic CAL enables the use of modern programming
languages and provides a non-proprietary interface for cloud-based
systems to communicate with other CAL Clients on a Platform by means of
a connection. A connection is a communication link established between
CAL Client endpoint and the Platform hosted endpoint (via the ASB). The
OMSC-SPC-013, Language-Agnostic CAL Specification, identifies approved
protocols for establishing a connection as well as required behaviors
and interactions.

### Mission Processing

Within an OMS Mission Package, there is typically mission processing
(e.g., physical processors) present in order to meet mission needs. The
choice of where in the Mission Package the mission processing is
accomplished is dependent upon a full weapon system design. OMS
recognizes that mission processing can take many forms, but also
specifies that an Open Computing Environment (OCE) must be present in an
OMS Mission Package.

An OMS Platform is responsible for providing an OCE for its Mission
Package. The Platform must provide at least one OCE implementation.
Subsystems may provide additional OCE implementation(s) in the Mission
Package. OCE implementations that occur in the Platform’s mission
processing must be documented in the Platform Description Document
(PDD). If an OCE implementation is also provided by a Subsystem, it must
be documented in its Subsystem Description Document (SDD). The Mission
Package Description Document (MPDD) will reference the Platform and any
Subsystem(s) providing OCE implementations within the Mission Package.

#### Open Computing Environment (OCE)

The Open Computing Environment (OCE) defines a computing environment on
which OMS Services can run, but are not required to run. The intent of
the OMS OCE is to provide an environment that enables hardware or
software to be modified independently without cascading change through
the other elements and promotes reduced cost of sustainment and
modernization through the appropriate isolation and use of open
standards. The key OMS goals that relate to OCE properties include:

-   Enabling Service portability across Weapons Systems

-   Enabling rapid hardware upgrades with minimum Service
    re-integration.

In support of these overall OMS goals, an OMS OCE must enable system
architectures that support the isolation of mission systems from safety
critical elements of a mission system, enable hardware or software to be
modified independently without cascading change through the other
elements, and allow reduced cost of sustainment and modernization
through the appropriate isolation and use of open standards.

The OCE definition consists of two main themes. The first theme is the
requirements for the Open Computing Environment platform such as hosting
the OMS CAL and Data Transfer implementations. The second theme is the
requirements for the portability techniques an OMS OCE can provide and
requirements a Service must adhere to in order to meet Service
portability goals across different OCE implementations and future
upgrades. The OMS OCE portability approaches are summarized in the
following sections.

##### Façade-Based Approach

This approach specifies a subset of OS calls a Service must utilize. The
OMS OS Façade is a subset of OS calls allowed to be used by an
OCE-hosted Service to support Service portability across different OCE
OS and HW implementations. It is based on POSIX calls derived from IEEE
Std. (POSIX) 1003.1-2008 and IEEE Std. (POSIX) 1003.1-2013 with select
calls restricted from use, which is consistent with the Future Airborne
Capability Environment (FACE™) OS segment general purpose profile which
avoids the use of deprecated or unsafe functions. The OMS OS Façade is
defined in OMSC-SPC-005, Operating System Façade Specification.

##### Java-Based Approach

Java is designed to solve many of the same issues being addressed by the
OMS OCE. It enables software portability and reuse by allowing all
software implemented in Java to run on any platform that supports a Java
Virtual Machine (JVM). In general, hardware and software upgrade costs
can be reduced because the JVM is maintained and upgraded by the
commercial industry.

##### OCE General Requirements

This section defines the normative architecture requirements for an OMS
Open Computing Environment (OCE). The actual implementation of the
mission computing resources that satisfy the normative OCE requirements
are specific to OCE providers.

> RQMT STD-000350 \[An OMS OCE shall host a C++ OMS CAL
> implementation.\]
>
> RQMT STD-000351 \[An OMS OCE shall host a Java OMS CAL
> implementation.\]
>
> RQMT STD-000352 \[An OMS OCE shall be capable of hosting at least one
> Service.\]

Notes: An OMS OCE is not limited in the number of services that can be
hosted. An OMS-compliant Service is not limited to running only in the
OCE.

> RQMT STD-000354 \[An OMS OCE shall synchronize system clock using an
> industry standard protocol identified in the “Approved Time
> Synchronization Protocols” table.\]
>
> RQMT STD-000355 \[An OMS OCE shall provide time to OCE-hosted Services
> through operating system interfaces.\]

Note: Use of a programming language call that uses an operating system
interface meets the above requirement.

OMS OCE implementations are identified in the MPDD. The implementation
details of an OCE hosted by the Platform are documented in the PDD. If
an OCE is hosted in a Subsystem, the implementation details are
documented in the SDD. An OMS OCE should satisfy program protection
requirements commensurate with the suite of Services to be hosted. Note
that the degree of protection necessary in an OMS OCE is dependent upon
the suite of Services it hosts. It is quite possible to build an OCE and
discover the protection it provides is inadequate to host a new Service
whose protection requirements had not been previously considered.

An OMS OCE is not required to support Special Signals.

> RQMT STD-000360 \[An OMS OCE shall provide a Linux operating system
> with a minimum kernel version of 2.6.\]

An OMS OCE is Linux based to enable OMS Service portability from one OCE
to another.

> RQMT STD-000362 \[An OMS OCE shall provide a 64 bit Linux operating
> system when the OCE is hosted on a 64 bit processing board.\]

When an OMS OCE is hosted on 32 bit hardware then a 32 bit Linux
operating system may be used that is compatible with the same minimum
kernel version of 2.6.

An OMS OCE can be provided either directly via a Linux operating system
hosted on a processing board or virtually via a virtual machine.

> RQMT STD-000365 \[An OMS OCE shall provide a Façade implementation.\]
>
> RQMT STD-008663 \[An OMS OCE shall provide a Java implementation.\]

An OMS OCE provides a Linux OS that must include support for both a
Façade implementation (C++ based execution environment) and a Java
implementation. Note: An OMS OCE will provide a Java implementation if
it is not against system policy.

###### OCE Guidelines

-   The OCE concepts were developed to support operation in an embedded
    Platform. Note: Does not preclude use for other environments.

-   An OMS OCE may consist of one or multiple processing nodes. One or
    more processing nodes, including Subsystems, may host an OCE.

-   Other than security implications on the processor architecture, the
    OCE utilizes general purpose processor architecture (no specialized
    hardware).

-   An OMS OCE does not require a specific implementation (e.g.,
    processing chip set, virtual machine, compiler, etc.) – recommended
    standards are provided in a later section.

-   An OMS OCE provides for future innovation and improvement in its
    implementation.

-   An OMS OCE should leverage existing open and/or consensus-based
    standards and implementations.

-   An OMS OCE minimizes the unintentional impact of one Service on
    another Service.

-   An OMS OCE allows for Platform upgrades with minimal support from
    the Service provider (e.g., recompilation, porting, does not imply
    binary compatibility).

-   An OMS OCE allows for redeployment of the Service within a single
    Platform with no support from the Service provider.

-   An OMS OCE allows for versioned Service upgrades with minimal
    support from the OCE provider, assuming the resource utilization of
    the Service has not changed.

-   The use of Façade or Java approaches does not preclude use of
    virtualization as an underlying architectural approach.

-   If Java is prohibited due to system security policy, then only the
    C++ CAL implementation would be applicable for the OMS OCE.

##### OCE Façade Requirements

An OMS OCE will adhere to the following requirement:

> RQMT STD-000381 \[An OMS OCE shall implement all allowed interfaces
> defined by the Operating System Façade Specification.\]

##### OCE Java Requirements

An OMS OCE hosts a Java-based implementation that supports a Java
environment and associated Java CAL. The Java Native Interface (JNI) is
part of the Java specification, and it is a mandatory part of all Java
implementations. The Java-based Open Computing Environment will adhere
to the following requirements:

> RQMT STD-000385 \[An OMS OCE Java-based implementation shall provide a
> Java environment that is compliant with the Java specification.\]

##### Example OCE Architectures

The OCE requirements section above defines the properties an OCE
provider must meet in order to have an OMS-compliant OCE. Examples of
solutions employing the portability techniques are provided here for
information.

Example OCE minimum implementation features for a Façade implementation
include:

-   Network: Internet Protocol-based communication

-   OS: Linux kernel version 2.6 or later

-   H/W: x86-64 bit processing boards

-   Toolset: GNU Compiler Collection (GCC) compiler option –std=c++03.

Example OCE minimum implementation features for a Java implementation
include:

-   Network: Internet Protocol-based communication

-   OS: Linux kernel version 3.0.x or later

-   H/W: Power-PC 32 bit processing boards

-   Toolset: Oracle Java Development Kit (JDK) 11.

#### Other Mission Processing

In some cases, specific weapons systems designs may drive that non-OCE
processing be used to host some OMS Services. For example, there may
exist a specific processor and operating system combination that has
been certified for use in accomplishing specific mission requirements
and the OCE has not reached that level of certification. Also, by
allowing non-OCE mission processing, legacy programs can reap the
benefits of adoption as they migrate towards full OMS adoption without
having to require a potentially expensive processing upgrade and
conversion of mission software.

### Data Storage

Within an OMS Mission Package, there must be data storage available in
order to store software applications, such as an Operational Flight
Program (OFP), as well as configuration files and data products, as
applicable. Many of these can be implemented and designed in various
manners. For example, an OMS Subsystem could use local data storage that
contains its software executables as well as its initial configuration
file used by the boot loader. In other instances, an OMS Mission Package
can be designed with network storage that is accessed via Data Transfer
protocols to retrieve the configuration file and/or software
executables. While OMS recognizes that storage must exist in some
fashion (whether network drive, flash memory, etc.), there are no direct
requirements for its existence. Data storage will be available as a
consequence of designing to meet the Adopting Program’s requirements for
a full weapon system implementation.

### Time Reference and Time Synchronization

The Platform is responsible for providing a time reference for time
synchronization by Architecture Elements within the Mission Package. A
Platform utilizes one or more time sources, which may be internal or
external to the Mission Package, to provide a time reference. The time
reference and its time sources are documented in the PDD.

#### Time Reference

The time reference is generated from the source of time for
synchronization within the Mission Package. The accuracy and precision
of the time reference will be documented in the Platform Description
Document.

#### Time Synchronization

Time is propagated from the time reference to the endpoints across the
ASB within the Mission Package to provide for time synchronization. The
time synchronization protocols (i.e., NTP and PTP) apply only to the
boundaries of the OCE, Other Mission Processing, Subsystems, and
applicable Isolators (with dedicated Isolator hardware) where they are
connected to the ASB. It is intended that the ASB supports these
protocols at the OCE, Other Mission Processing, Subsystem, and
applicable Isolator endpoints such that the time is synchronized at all
endpoints.

The Standard provides a list of approved industry standards for time
synchronization for OMS. This list is identified in Table 6.5-1,
Approved Time Synchronization Protocols. The OACWG realizes that there
is some lag time before some standards can be utilized in closed
environments. Since IEEE-1588 2019 is backwards-compatible with
IEEE-1588 2008, the OACWG expects that at some time in the future the
2008 version will be deprecated.

<span id="_Toc219290735" class="anchor"></span>Table 6.5-1 Approved Time
Synchronization Protocols

<table>
<thead>
<tr class="header">
<th>Protocol</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IEEE 1588-2008 PTP</td>
<td>Precision Time Protocol (PTP) IEEE 1588 is designed for local systems requiring accuracies beyond those attainable using NTP. It is also designed for applications that cannot bear the cost of a GPS receiver at each node, or for which GPS signals are inaccessible. It achieves clock accuracy in the sub-microsecond range making it suitable for measurement and control systems.</td>
</tr>
<tr class="even">
<td>IEEE 1588-2019 PTP</td>
<td>Precision Time Protocol (PTP) IEEE 1588 is designed for local systems requiring accuracies beyond those attainable using NTP. It is also designed for applications that cannot bear the cost of a GPS receiver at each node, or for which GPS signals are inaccessible. It achieves clock accuracy in the sub-microsecond range making it suitable for measurement and control systems.</td>
</tr>
<tr class="odd">
<td>RFC 1119 NTP</td>
<td>Network Time Protocol available over packet-switched, variable latency networks. NTP can usually achieve one-millisecond accuracy in local area networks under ideal conditions.</td>
</tr>
</tbody>
</table>

In addition to the approved time synchronization protocols, this
Standard recognizes that there may be Subsystems, Services, and
Isolators that desire or require a higher fidelity synchronization. This
Standard provides guidance on options that may be provided by a Platform
for a higher fidelity time reference. In order to limit the
permutations, this Standard provides a set of higher fidelity options
from which to choose. These options are identified in Table 6.5-2, High
Fidelity Time Synchronization Mechanisms. Note that some of these
options may require a special signal in conjunction with a standard
message.

<span id="_Toc219290736" class="anchor"></span>Table 6.5-2 High Fidelity
Time Synchronization Mechanisms

<table>
<thead>
<tr class="header">
<th>Mechanisms</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IRIG B</td>
<td>Time code B has a time frame of 1 second with an index count of 10 milliseconds and contains time-of-year and year information in a BCD format, and seconds-of-day in SBS</td>
</tr>
<tr class="even">
<td>1 PPS</td>
<td>The 1 Pulse Per Second (PPS) protocol supports high precision time distribution down to the nanosecond level by coordinating a <strong>SystemTimeAtReference</strong> message with the leading edge of a pulse on a Special Signal input.</td>
</tr>
<tr class="odd">
<td>Precise Time and Time Interval (PTTI)</td>
<td>Two-way digital interface that provides precise time synchronization between GPS users with Coordinated Universal Time (UTC).</td>
</tr>
</tbody>
</table>

The IRIG B protocol requires an IRIG B Special Signal as defined in
Section 6.3.3.2, Time Reference Signals. Time code words and Control
Functions (CFs) presented within the 100 bit frame are presented
according to IRIG 200-16. The optional Straight Binary Seconds (SBS)
code word contains time-of-day (TOD) information. CFs within the time
code enable encoding of various functions, however, there is no
standardized coding system as these are optional. If CFs are used, the
coding system will need to be documented in the SDD and/or PDD.
Consideration for additional performance requirements may be needed.

The 1 PPS protocol requires a 1 PPS Special Signal as defined in Section
6.3.3.2, Time Reference Signals, followed by a corresponding
**SystemTimeAtReference** message. The OMS Platform is required to
provide the 1 PPS Special Signal and document the implemented
performance characteristics in the PDD. A Subsystem utilizing this 1 PPS
Special Signal must also document in the SDD the implemented performance
characteristics expected for the 1 PPS Special Signal. Consideration for
additional performance requirements, for example delivery latency of the
**SystemTimeAtReference** message, may be needed as shown in Figure
6.5-3, Example 1 PPS Pulse Train with Corresponding OMS Messages.

The PTTI is a two-way digital interface that receives a BCD Time Code
Special Signal, Time Fault Discrete Special Signal, and 1 PPS Special
Signal, as defined in Section 6.3.3.2, Time Reference signals. The PTTI
may receive any of the aforementioned signals as inputs. The PTTI may
provide any of the following output signals: 1 PPS synchronized with the
UTC second rollover, 1 PPM synchronized with the UTC minute rollover,
the BCD Time Code consisting of time of day (UTC), day of year, and
TFOM, and the Time Fault Discrete signal.

<img src="media/image29.png" style="width:6.5in;height:2.29167in" />

<span id="_Toc219290713" class="anchor"></span>Figure 6.5-3 Example 1
PPS Pulse Train with Corresponding OMS Messages

### Position Information

Lower fidelity position information is provided through the
**PositionReport** message. This message is intended to report position
information to Subsystems, Services, and Isolators on the ASB that do
not require high fidelity position as well as for off-board consumers of
the Platform’s position. A Platform provides lower fidelity position
information by publishing the **PositionReport** message at one of the
following nominal rates:

-   0.001 Hz

-   0.5 Hz

-   1 Hz.

While a 1 Hz rate is typical for Platforms that move, lower rates are
applicable to a stationary Platform (e.g., a ground station) where the
higher rate is not needed and may cause processing and/or network impact
if the **PositionReport** message is sent to a large number of
consumers.

In addition to the lower fidelity position information, this Standard
recognizes that there may be Subsystems, Services, and Isolators that
require a higher fidelity position information reference.

When a Platform requires a high rate and/or high fidelity position
information reference, the following approach must be used. Utilize the
**PositionReportDetailed** message with the Quality of Service (QoS)
settings listed below and provide it at one or more of the optional
rates.

-   Time Based Filter: unspecified could be used to provide lower rate
    (filtered) reporting on a specific topic.

-   Reliability: BEST\_EFFORT

-   Lifespan: 0 (unset)

-   Destination Order: BY\_SOURCE\_TIMESTAMP

-   History Depth: depth=1

-   Publish Rate Options: 1 Hz, 5 Hz, 10 Hz, 20 Hz, 50 Hz, 100 Hz

### Cloud-Based Platforms

A cloud infrastructure is the collection of hardware and software that
contains both a physical layer and an abstraction layer. The physical
layer consists of the hardware resources such as the server, storage and
network components. The abstraction layer consists of the software
developed across the physical layer. An OMS Platform utilizing a
cloud-hosted environment may consist of the following layers that should
be documented in the PDD:

-   Platform as a Service (PaaS). The capability to deploy Subsystem
    software, OMS Services, Isolators, or Platform software onto the
    cloud infrastructure

-   Infrastructure as a Service (IaaS). The capability to provision and
    configure processing, storage, networks, and other fundamental
    computing resources required by Subsystem software, OMS Services,
    Isolators, or Platform software.

Mission Package
---------------

An OMS Mission Package is the highest level OMS construct and typically
consists of a Platform, one or more Subsystems, one or more Services,
and any necessary Isolators. The Architecture Elements contained within
the Mission Package are identified in the OMS Mission Package Worksheet,
and the Mission Package details are documented in the Mission Package
Description Document. It is possible for a weapon system to contain an
OMS Mission Package that addresses only part of the entire weapon
system.

Compliance
==========

OMS compliance is defined by key elements of the architecture and
documented in the OMS D&D. The following paragraphs introduce these
Architecture Elements and the applicable section of the Standard where
further definition may be found, a description of the compliance tiers
for these elements, as well as impacts of modifying messages at a given
tier.

Compliance Tiers
----------------

In order to provide a consistent measure for Adopting Programs to
initially adopt OMS and progress toward full compliance by providing
concrete points that can be used to develop a plan to achieve full
compliance, a set of compliance tiers has been defined. The OMS
compliance tiers provide for specific levels of compliance along the
path to full compliance, which is Tier 3. OMS compliance provides the
means to tailor the compliance in targeted areas such as specific
Subsystems, Services, and security.

In developing this tier structure, a couple of key tenets were used. In
order to achieve some minimum interoperability between subsystems and
services of a particular tier, a minimum message set for the tiers has
been identified. This is the subset of the OMS Message Set that must be
implemented by a particular Subsystem, Service or Platform in order to
claim compliance at that tier. Certain Subsystems and Services are more
likely to be reused in other Mission Packages on other Platforms than
other Subsystems and Services. These are the subsystems and services
that acquiring program offices are most likely going to designate for
OMS compliance. Early identification of these subsystems and services
allows industry to begin planning OMS implementation roadmaps for these
subsystems and services.

The degree of OMS compliance has been quantified by three tiers of
compliance. The first tier, Tier 1, sets the standard for initial
interoperability between Subsystems and Services to ensure that a
minimum capability is achieved and introduces a minimum OMS Message Set.
In addition, Tier 1 establishes the basic OMS Platform infrastructure
that allows for easier integration of subsystems and services. See
Section 1.3, OMS Approach, for more information on the mapping of OMS
Business Goals. This means that Adopting Programs can expect to realize
significant benefit by achieving Tier 1 compliance because it sets the
stage for further compliance in the future.

Likewise, Tier 2 increases interoperability by expanding the minimum OMS
Message set with additional mission management capability.

Tier 3 then takes the provider to the objective of full OMS compliance
with all data exchanges using OMS Data Exchanges (OMS Messaging, Data
Transfer, Special Signals, and Security Information Exchanges) and all
elements of the OMS architecture being fully compliant. At Tier 3, all
OMS Messages used in an OMS Message Set must have been approved at the
formal OACWG change process (i.e., they are Approved OMS Messages).
Achieving Tier 3 compliance maximizes the OMS business goals by
maximizing the benefit to the program in the future.

The use of Non-OMS Messages are not allowed. Any Subsystem, Service, or
Isolator using Non-OMS Messages will not be OMS compliant at any tier.
If a Non-OMS Message is used, then the Subsystem or Service is not OMS
compliant at any tier. Consider using a Data Transfer until the Non-OMS
Message can be added to a future baseline UCI Schema using an UCI Change
Request, so it will go through a CAL.

The primary purpose of defining a tiered structure is to allow new and
existing programs to plan an orderly pathway to compliance while
managing the natural budget constraints and competing pressures for new
capabilities and technologies.

In the following sections, requirements are subdivided into the
appropriate compliance tier for each of the major OMS Architecture
Elements (Mission Package, Platform, Subsystems, and Services) for which
OMS compliance is assessed. Each tier builds on lower tiers, so that by
Tier 3, the mission system is fully compliant to all the objectives of
Open Mission Systems. All RQMTs in this section contain tier
designations within the requirements text, e.g., “A Tier 1 OMS Service
shall …”.

### Change Request Submission Guidelines

As an Adopting Program works to develop an OMS-compliant Mission
Package, it is possible that gaps in the OMS Standard may be discovered.
It is anticipated that the majority of the gaps will pertain to OMS Data
Exchanges. The definitions of the OMS Data Exchanges have been developed
with the goal of meeting system application needs across the community.
If a gap exists that prevents an Adopting Program from being assessed at
the targeted compliance tier, a Change Request addressing the identified
gaps may be submitted in order to address the gap and be assessed at the
targeted compliance tier. A Change Request identifies proposed changes
to the OMS Standard and/or UCI Standard according to the change process
defined in the OACWG Governance Plan.

It is critical that any proposed change meets the needs of the Adopting
Program, satisfies the broader needs of the community, and successfully
completes the change process (Change Request approved through OACWG).
Prior to submitting a Change Request, the Adopting Program should review
the latest released OMS Standard to ensure the gap still exists. If the
gap does not exist in the latest released OMS Standard and the solution
meets the requirements of the Adopting Program, a Change Request is not
warranted. The Adopting Program should identify the approved Change
Request(s) associated with the gap and integrate the Change Request(s)
into the program baseline.

If the gap exists or the implemented solution does not meet the
requirements of the Adopting Program, a Change Request is warranted.

The Adopting Program should plan to follow the change process as
outlined in the OACWG Governance Plan. This process includes the
following steps:

1\) Submit a Change Request based on latest formal OMS D&D release that
describes the required changes.

2\) Work with the OACWG and interested parties with the goal of reaching
consensus on the proposed change.

3\) Receive approval by OACWG for the Change Request where the following
artifacts for the Change Request were reviewed:

1.  Full definition of any Data Exchanges proposed to be
    changed/added/deleted, such as a new or modified OMS Message(s)
    (including updates to messages in the Minimum Message Set), new Data
    Transfer protocols and/or formats, new Special Signal definitions,
    or new Security Information Exchanges.

2.  Red-lined versions of all Standard documentation affected by the
    change.

3.  Test plan that shows testing or use of these Data Exchanges and any
    progress.

4\) Initiate, if desired, the Appeals Process as outlined in the OACWG
Governance Plan if the Change Request is rejected by OACWG or the
solution approved by OACWG does not meet the Adopting Program’s needs.

These steps are considered to be the minimum effort expected of an
Adopting Program or change proposer. Compliance is assessed against a
specific version of the OMS Standard. By following these steps, a
program will be able to achieve the desired compliance tier for the
target version of the Standard. Programs are strongly encouraged to
follow their proposals through acceptance to minimize impact when a
future version of the Standard is adopted.

Programs may also have identified gaps in the standard related to a
Minimum Message Set (MMS) which, when implemented, will adversely affect
achieving the targeted tier compliance. A modification or extension that
extends messages in either of the MMSs may temporarily cause an
Architecture Element using these messages not to be OMS compliant at the
intended Tier for the specific OMS release version. Note that asserting
or proving compliance will change as a program evolves from a
proposal/acquisition phase (e.g., initial compliance assessments) to a
program after final testing (e.g., final compliance assessments).

Here are examples of how modifying existing messages may affect tier
compliance of an Architecture Element:

-   Tier 1 Example: A Subsystem modifies the **SubsystemStatus** Tier 1
    MMS message

Modification to an OMS Tier 1 MMS or a Tier 1 Required Subsystem Message
Set makes the Subsystem not compliant at OMS Tier 1 until the
modification is approved by OACWG.

-   Tier 2 Example: A Service modifies the **MissionPlan** Tier 2 MMS
    message

Modification to an OMS Tier 2 MMS makes the Service not compliant at OMS
Tier 2 until the modification is approved by OACWG. If all other Tier 1
compliance requirements are met, Tier 1 compliance could be achieved.

-   Tier 3 Example: A Subsystem modified the
    **SubsystemCalibrationStatus** message

Modification to any OMS message not in any Tier 1 or Tier 2 Minimum
Message Set makes the Subsystem not compliant at OMS Tier 3 until the
modification is approved by OACWG. If all other Tier 2 compliance
requirements are met, Tier 2 compliance could be achieved.

Service Compliance
------------------

A Service is an OMS Architecture Element that is only comprised of one
or more software components. A Service provides mission functions and/or
Capabilities. A Service is assessed in accordance with a prescribed
interface and predefined constraints and policies specified by a
non-proprietary Service Contract. A Service may run in the OCE,
Subsystems, or Other Mission Processing. A Service communicates via an
OMS Platform over the Abstract Service Bus (ASB) using OMS Data
Exchanges.

### Service Tier 1 Requirements

> RQMT STD-000042 \[A Tier 1 OMS Service shall be documented in a
> non-proprietary Service Contract in accordance with the OMS Service
> Contract Template.\]
>
> RQMT STD-000043 \[A Tier 1 OMS Service shall use the OMS CAL to send
> and/or receive OMS Messages over the OMS ASB.\]
>
> RQMT STD-000044 \[A Tier 1 OMS Service shall use the applicable Tier 1
> Minimum Message Set messages.\]

The term “applicable” has special meaning for OMS compliance. The intent
of the use of applicable is to not artificially manufacture additional
derived requirements where none exist. For example, a Service in a
Mission Package does not need to use all messages in the Tier 1 Minimum
Message Set, only those applicable to its functionality. This helps
reduce unnecessary testing costs and eliminates unnecessary attack
vectors, while still allowing for design flexibility and composability
at the Mission Package level.

> RQMT STD-004998 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Service shall select from the corresponding data formats in column B
> of the “Data Transfer Formats, APIs, and Protocols” table for data
> transfers that cross the Service boundary.\]
>
> RQMT STD-004999 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Service shall select from the corresponding protocols/APIs in column C
> of the “Data Transfer Formats, APIs, and Protocols” table for
> exclusive use data transfers that cross the Service boundary.\]
>
> RQMT STD-010122 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Service shall select from the corresponding protocols/APIs in column D
> of the “Data Transfer Formats, APIs, and Protocols” table for shared
> read-only data transfers that cross the Service boundary.\]
>
> RQMT STD-005000 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Service shall select from the corresponding protocols/APIs in column E
> of the “Data Transfer Formats, APIs, and Protocols” table for shared
> read/modify data transfers that cross the Service boundary.\]
>
> RQMT STD-005001 \[A Tier 1 OMS Service shall use the URI formats, as
> specified in the “OMS URI Formats” table, for its data transfers that
> cross the Service boundary.\]

The definition of a Service boundary can be found in Section 6.1,
Service.

> RQMT STD-000319 \[A Tier 1 OMS Service shall report status in
> accordance with the “Service Status” section in the OMS Service
> Contract Template.\]
>
> RQMT STD-000320 \[A Tier 1 OMS Service shall implement configurable
> periodicity for reporting status.\]
>
> RQMT STD-000321 \[A Tier 1 OMS Service shall implement a configurable
> range for periodic update rate from 1 to 600 seconds in 1 second
> increments.\]
>
> RQMT STD-000872 \[A Tier 1 OMS Service shall have a NORMAL state.\]
>
> RQMT STD-000873 \[A Tier 1 OMS Service shall use applicable state
> transitions defined in the “Allowed State Transitions for OMS Service”
> figure.\]
>
> RQMT STD-009708 \[A Tier 1 OMS Service shall document its
> cybersecurity posture in accordance with the “Cybersecurity Posture”
> section in the OMS Service Contract Template.\]

The OMSC-GDE-003, Cybersecurity Guide, defines concepts and guidance for
OMS Adopting Programs and system designers to utilize for documenting
the OMS Architecture Element cybersecurity posture.

### Service Tier 2 Requirements

> RQMT STD-000050 \[A Tier 2 OMS Service shall meet Tier 1 Service
> requirements.\]
>
> RQMT STD-000051 \[A Tier 2 OMS Service shall use the applicable Tier 2
> Minimum Message Set messages.\]

### Service Tier 3 Requirements

> RQMT STD-000053 \[A Tier 3 OMS Service shall meet Tier 2 Service
> requirements.\]
>
> RQMT STD-000054 \[A Tier 3 OMS Service shall use applicable OMS
> Special Signals as listed in the “Special Signals” section.\]
>
> RQMT STD-000055 \[A Tier 3 OMS Service shall use the applicable
> messages in the OMS Message Set.\]

### OCE-Hosted Services

OCE-hosted Services are OMS Services that fully comply with the
OMSC-SPC-005, Operating System (OS) Façade Specification. Complying with
the OS Façade Specification facilitates portability from one OCE to
another. An OMS Service running in a Façade-based OCE should only use
the Operating System (OS) calls allowed by the OS Façade Specification.

An OMS Service and the libraries (non-OCE provided) supporting a
Façade-based OCE should use the Façade for Operating System (OS) calls.

The OMS Service provider should take the following guidelines into
consideration when developing the OMS Service:

-   Avoid use of OS-specific \#ifdefs; there should be no expectation
    that a particular OS will be used to implement the Façade.

-   Develop processor endian tolerant code; the Service should avoid
    assumptions about the endianness of the processor that will be used
    to execute the code (example: defining a C++ union with different
    data types and assuming how a particular processor will map those
    data types).

A Java-based OCE-hosted Service that uses the Java Native Interface
(JNI) should follow the requirements set forth by the Façade for the C++
portion of the implementation.

A Java-based OCE-hosted Service should be compliant with the OMS OCE
specified Java specification.

It is possible for a Service that does not comply with the OS Façade
Specification to run in an OCE depending on the OS calls included in the
OCE implementation. However, the Service would not be considered an
OCE-hosted Service.

Subsystem Compliance
--------------------

A Subsystem is an OMS Architecture Element that is comprised of one or
more hardware and software components. A Subsystem provides mission
functions and/or Capabilities. A Subsystem is assessed in accordance
with a prescribed interface and predefined constraints and policies
specified by a non-proprietary Service Contract and a non-proprietary
Subsystem Description Document. A Subsystem is not required to host or
present a Service. A Subsystem communicates via an OMS Platform over the
Abstract Service Bus (ASB) using OMS Data Exchanges.

### Subsystem Tier 1 Requirements

> RQMT STD-000059 \[A Tier 1 OMS Subsystem shall be documented in a
> non-proprietary Subsystem Description Document in accordance with the
> OMS Subsystem Description Document Template.\]

If an OMS Subsystem implements security exchanges, the security
exchanges will be documented in the Subsystem Description Document.

> RQMT STD-000060 \[A Tier 1 OMS Subsystem shall be documented in a
> non-proprietary Service Contract in accordance with the OMS Service
> Contract Template.\]
>
> RQMT STD-000061 \[A Tier 1 OMS Subsystem shall use the OMS CAL to send
> and/or receive OMS Messages over the OMS ASB.\]
>
> RQMT STD-000063 \[A Tier 1 OMS Subsystem shall use the Tier 1 Required
> Subsystem Message Set messages that are associated with the
> capabilities provided.\]
>
> RQMT STD-000064 \[A Tier 1 OMS Subsystem shall use the applicable Tier
> 1 Minimum Message Set messages.\]
>
> RQMT STD-006935 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Subsystem shall select from the corresponding data formats in column B
> of the “Data Transfer Formats, APIs, and Protocols” table for data
> transfers that cross the Subsystem boundary.\]
>
> RQMT STD-006936 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Subsystem shall select from the corresponding protocols/APIs in column
> C of the “Data Transfer Formats, APIs, and Protocols” table for
> exclusive use data transfers that cross the Subsystem boundary.\]
>
> RQMT STD-010123 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Subsystem shall select from the corresponding protocols/APIs in column
> D of the “Data Transfer Formats, APIs, and Protocols” table for shared
> read-only data transfers that cross the Subsystem boundary.\]
>
> RQMT STD-006937 \[For each data type identified in column A of the
> “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS
> Subsystem shall select from the corresponding protocols/APIs in column
> E of the “Data Transfer Formats, APIs, and Protocols” table for shared
> read/modify data transfers that cross the Subsystem boundary.\]
>
> RQMT STD-006938 \[A Tier 1 OMS Subsystem shall use the URI formats, as
> specified in the “OMS URI Formats” table, for its data transfers that
> cross the Subsystem boundary.\]

The definition of a Subsystem boundary can be found in Section 6.2,
Subsystem.

> RQMT STD-010007 \[When required, a Tier 1 OMS Subsystem shall use
> applicable lower fidelity position information using the specified OMS
> Message at one of the nominal rates specified in the “Position
> Information” section.\]
>
> RQMT STD-010008 \[When required, a Tier 1 OMS Subsystem shall use
> applicable high fidelity position information using the specified OMS
> Message and Quality of Service (QoS) settings at one or more of the
> nominal rates as specified in the “Position Information” section.\]
>
> RQMT STD-008667 \[A Tier 1 OMS Subsystem shall accomplish time
> synchronization using an industry standard protocol identified in the
> “Approved Time Synchronization Protocols” table.\]
>
> RQMT STD-008668 \[When required, a Tier 1 OMS Subsystem shall
> accomplish high fidelity time synchronization using an industry
> standard protocol identified in the “High Fidelity Time
> Synchronization Mechanisms” table.\]
>
> RQMT STD-006944 \[A Tier 1 OMS Subsystem shall report status in
> accordance with the “Subsystem Status” section of the OMS Service
> Contract Template.\]
>
> RQMT STD-008669 \[A Tier 1 OMS Subsystem shall implement configurable
> periodicity for reporting status.\]
>
> RQMT STD-008670 \[A Tier 1 OMS Subsystem shall implement a
> configurable range for periodic update rate from 1 to 600 seconds in 1
> second increments.\]
>
> RQMT STD-000414 \[A Tier 1 OMS Subsystem shall have an OPERATE
> state.\]
>
> RQMT STD-000415 \[A Tier 1 OMS Subsystem shall use applicable state
> transitions defined in the “Allowed State Transitions for OMS
> Subsystem” figure.\]
>
> RQMT STD-000416 \[A Tier 1 OMS Subsystem shall use applicable state
> transition triggers defined in the “OMS Subsystem State Definitions
> and Allowed Transitions” table.\]
>
> RQMT STD-010179 \[A Tier 1 OMS Subsystem shall document its
> cybersecurity posture in accordance with the “Cybersecurity Posture”
> section in the OMS Subsystem Description Document Template.\]
>
> RQMT STD-009710 \[A Tier 1 OMS Subsystem shall document its
> cybersecurity posture in accordance with the “Cybersecurity Posture”
> section in the OMS Service Contract Template.\]

The OMSC-GDE-003, Cybersecurity Guide, defines concepts and guidance for
OMS Adopting Programs and system designers to utilize for documenting
the OMS Architecture Element cybersecurity posture.

### Subsystem Tier 2 Requirements

> RQMT STD-000069 \[A Tier 2 OMS Subsystem shall meet Tier 1 Subsystem
> requirements.\]
>
> RQMT STD-000070 \[A Tier 2 OMS Subsystem shall use the applicable Tier
> 2 Minimum Message Set messages.\]

### Subsystem Tier 3 Requirements

> RQMT STD-000072 \[A Tier 3 OMS Subsystem shall meet Tier 2 Subsystem
> requirements.\]
>
> RQMT STD-000073 \[A Tier 3 OMS Subsystem shall use applicable OMS
> Special Signals as listed in the “Special Signals” section.\]
>
> RQMT STD-000074 \[A Tier 3 OMS Subsystem shall use the applicable
> messages in the OMS Message Set.\]

Platform Compliance
-------------------

An OMS Platform is an OMS Architecture Element, which is itself a
composite architecture. A Platform includes the ASB, mission processing
(including an OCE), and typically provides time reference, time
synchronization, and position information for the Mission Package.
Unlike Subsystems and Services, Platforms do not provide Capabilities.
The Platform is assessed in accordance with the non-proprietary Platform
Description Document (PDD). A Platform may include non-OMS software that
provides a measure of robustness for the underlying infrastructure. One
example is infrastructure software and settings necessary to protect
information passing through the ASB. A second example is software that
manages the underlying infrastructure such as the network that forms the
ASB, the processing elements that form mission processing (including the
OCE), and data storage.

### Platform Tier 1 Requirements

> RQMT STD-000082 \[A Tier 1 OMS Platform shall provide an OMS ASB.\]
>
> RQMT STD-000083 \[A Tier 1 OMS Platform shall provide an OMS OCE.\]
>
> RQMT STD-000085 \[A Tier 1 OMS Platform shall be documented in a
> non-proprietary Platform Description Document in accordance with the
> OMS Platform Description Document Template.\]
>
> RQMT STD-000086 \[A Tier 1 OMS Platform shall provision for applicable
> OMS Special Signals as listed in the “Special Signals” section.\]

The term “provision” has special meaning for OMS compliance. The meaning
is further discussed in OMSC-STD-002, Abbreviations and Glossary.

> RQMT STD-005002 \[A Tier 1 OMS Platform shall provide an Internet
> Protocol (IP) based network to support the allowed protocols
> identified in the “Data Transfer Formats, APIs, and Protocols”
> table.\]

If an OMS Platform implements security exchanges, the security exchanges
will be documented in the Platform Description Document.

> RQMT STD-000303 \[A Tier 1 OMS Platform shall provide the time
> reference for time synchronization across the ASB.\]
>
> RQMT STD-000307 \[A Tier 1 OMS Platform shall accomplish time
> synchronization using an industry standard protocol identified in the
> “Approved Time Synchronization Protocols” table.\]
>
> RQMT STD-000314 \[When required, a Tier 1 OMS Platform shall
> accomplish high fidelity time synchronization using an industry
> standard protocol identified in the “High Fidelity Time
> Synchronization Mechanisms” table.\]
>
> RQMT STD-000325 \[When required, a Tier 1 OMS Platform shall provide
> lower fidelity position information using the specified PositionReport
> message at one of the nominal rates specified in the “Position
> Information” section.\]
>
> RQMT STD-000334 \[When required, a Tier 1 OMS Platform shall provide
> high fidelity position information using the specified
> PositionReportDetailed message and Quality of Service (QoS) settings
> at one or more of the nominal publish rates as specified in the
> “Position Information” section.\]
>
> RQMT STD-009712 \[A Tier 1 OMS Platform shall document its
> cybersecurity posture in accordance with the “Cybersecurity Posture”
> section in the OMS Platform Description Document Template.\]

The OMSC-GDE-003, Cybersecurity Guide, defines concepts and guidance for
OMS Adopting Programs and system designers to utilize for documenting
the OMS Architecture Element cybersecurity posture.

### Platform Tier 2 Requirements

> RQMT STD-000088 \[A Tier 2 OMS Platform shall meet Tier 1 Platform
> requirements.\]

### Platform Tier 3 Requirements

> RQMT STD-000095 \[A Tier 3 OMS Platform shall meet Tier 2 Platform
> requirements.\]
>
> RQMT STD-000096 \[A Tier 3 OMS Platform shall provide for applicable
> OMS Special Signals as listed in the “Special Signals” section.\]

Applicability in this context is determined collaboratively by the
Platform provider/integrator and the Government program representative.

Mission Package Compliance
--------------------------

A Mission Package is the highest level OMS construct that typically
consists of a Platform, one or more Subsystems, one or more Services,
and any necessary Isolators, as identified in the OMS Mission Package
Worksheet. Mission Package details are documented in a non-proprietary
Mission Package Description Document.

An OMS Mission Package can only achieve an assessment Tier that is no
higher than the lowest tier of the following assessed Architecture
Elements in the Mission Package: Platform, Subsystems, and Services. For
example, if the Mission Package has one Subsystem assessed at Tier 1
compliance, then the Mission Package will be assessed at Tier 1
compliance regardless of higher tier assessments achieved by the other
assessed Architecture Elements in the Mission Package.

### Mission Package Tier 1 Requirements

> RQMT STD-000101 \[A Tier 1 OMS Mission Package shall provide an OMS
> Platform assessed to at least Tier 1 compliance.\]
>
> RQMT STD-009208 \[A Tier 1 OMS Mission Package shall contain only OMS
> Architecture Elements assessed to at least Tier 1 compliance.\]

Architecture Elements assessed for compliance in the Mission Package are
defined as a Platform, Services, and Subsystems.

> RQMT STD-000102 \[A Tier 1 OMS Mission Package shall provide at least
> one applicable Tier 1 compliant Service Capability from the “Service
> Capability List for Compliance” section.\]
>
> RQMT STD-000103 \[A Tier 1 OMS Mission Package shall provide at least
> one applicable Tier 1 compliant Subsystem from the “Subsystem List for
> Compliance” section.\]
>
> RQMT STD-000104 \[A Tier 1 OMS Mission Package shall provide at least
> one Isolator if applicable.\]
>
> RQMT STD-005004 \[A Tier 1 OMS Mission Package shall provide NFS
> and/or FTP support for the allowed protocols identified in the “Data
> Transfer Formats, APIs, and Protocols” table.\]
>
> RQMT STD-009924 \[A Tier 1 OMS Mission Package shall document its
> Units of Replaceability in a non-proprietary Mission Package Worksheet
> in accordance with the OMS Mission Package Worksheet Template.\]
>
> RQMT STD-008124 \[A Tier 1 OMS Mission Package shall be documented in
> a non-proprietary Mission Package Description Document in accordance
> with the OMS Mission Package Description Document Template.\]
>
> RQMT STD-010180 \[A Tier 1 OMS Mission Package shall document its
> cybersecurity posture in accordance with the OMS Mission Package
> Worksheet Template.\]
>
> RQMT STD-009714 \[A Tier 1 OMS Mission Package shall document its
> cybersecurity posture in accordance with the “Cybersecurity Posture”
> section in the OMS Mission Package Description Document Template.\]

The OMSC-GDE-003, Cybersecurity Guide, defines concepts and guidance for
OMS Adopting Programs and system designers to utilize for documenting
the OMS Architecture Element cybersecurity posture.

### Mission Package Tier 2 Requirements

> RQMT STD-008675 \[A Tier 2 OMS Mission Package shall meet Tier 1
> Mission Package requirements.\]
>
> RQMT STD-000107 \[A Tier 2 OMS Mission Package shall provide an OMS
> Platform assessed to at least Tier 2 compliance.\]
>
> RQMT STD-009210 \[A Tier 2 OMS Mission Package shall contain only OMS
> Architecture Elements assessed to at least Tier 2 compliance.\]

Architecture Elements assessed for compliance in the Mission Package are
defined as a Platform, Services, and Subsystems.

> RQMT STD-000108 \[A Tier 2 OMS Mission Package shall provide all
> applicable Service capabilities from the “Service Capability List for
> Compliance” section at the Tier 2 compliance level.\]
>
> RQMT STD-000109 \[A Tier 2 OMS Mission Package shall provide all
> applicable Subsystems from the “Subsystem List for Compliance” section
> at the Tier 2 compliance level.\]

### Mission Package Tier 3 Requirements

> RQMT STD-008676 \[A Tier 3 OMS Mission Package shall meet Tier 2
> Mission Package requirements.\]
>
> RQMT STD-000112 \[A Tier 3 OMS Mission Package shall provide an OMS
> Platform assessed at Tier 3 compliance.\]
>
> RQMT STD-009212 \[A Tier 3 OMS Mission Package shall contain only OMS
> Architecture Elements assessed at Tier 3 compliance.\]

Architecture Elements assessed for compliance in the Mission Package are
defined as a Platform, Services, and Subsystems.

### Service Capability List for Compliance

Given the frequency that some Service capabilities are included in
mission systems packages, the following list of Service capabilities is
used to create a tier-compliant Mission Package. This list is not meant
to be all-inclusive but as a set of commonly used Service capabilities.
Acquisition Program Offices may designate additional mission system
Service capabilities to be OMS compliant. The customer designated
additional Service capabilities do not change this list when measuring
the tier level of the Mission Package. Service capabilities may be
decomposed into a variety of Services at different levels of complexity.
The intent of this list is targeted toward the overall Service
Capability that may result in one or more Services.

-   Automatic Route Generation Capability

<!-- -->

-   Generates new routes & mission plans

<!-- -->

-   Task Allocation Capability

<!-- -->

-   Allocates resources across a domain

-   Assigns tasks for activities such as collection, strike, package
    protection

<!-- -->

-   Task/Subsystem/Resource/Sensor Management Capability

<!-- -->

-   Can be specific to a certain type of task or capability, such as a
    specific subsystem, or mission operation

-   Interacts and manages Subsystems/tasks

<!-- -->

-   Fusion/Correlation Capability

<!-- -->

-   Correlates & fuses tracks

-   Manages track files and Electronic Order of Battle (EOB)

### Subsystem List for Compliance

Given the frequency that some subsystems are included in mission systems
packages, the following list of subsystems is used to create a
tier-compliant Mission Package. This list is not meant to be
all-inclusive but a set of commonly-used subsystems. Acquisition Program
Offices may designate additional mission subsystems to be OMS compliant.
The customer designated additional Subsystems do not change this list
when measuring the tier level of the Mission Package.

-   Electro-Optical/Infrared Subsystems

-   Radar Subsystems

-   Radar Warning Receiver Subsystems

-   Electronic Attack Subsystems

-   Electronic Support Measures Subsystems

Requirements Verification Cross Reference Matrix
================================================

The Verification Cross Reference Matrix (VCRM) section contains all of
the requirements and associated Verification Requirements (VRs) and
Acceptance Criteria (AC) for compliance to the OMS Standard. These
requirements are typically verified either by inspection of specific
documents, analysis of test results, or demonstration of specific
Services or programs that prove that something has been implemented
properly.

One of the goals of proving OMS compliance is to leverage existing test
plan artifacts and not to generate duplicate testing. It is expected
that Subsystem, Service, and Isolator providers will generate test
artifacts and associated analysis reports that may be called out for
inspection when proving compliance at a Subsystem, Service, or Mission
Package tier level.

Service providers are expected to generate and maintain an accurate
Service Contract for each Service. The Service provider is responsible
for establishing confidence in the Service Contract via testing of OMS
Message actions, verifying sequence diagrams, etc. Once confidence is
established then the Service Contract can be inspected and relied upon
from a compliance perspective.

Subsystem providers are expected to generate and maintain an accurate
Service Contract and Subsystem Description Document (SDD) for each
Subsystem. The Subsystem provider is responsible for establishing
confidence in the Service Contract via testing of OMS Message actions,
verifying sequence diagrams, etc. Once confidence is established then
the Service Contract can be inspected and relied upon from a compliance
perspective.

Platform providers are expected to generate and maintain an accurate
Platform Description Document (PDD) for a given Platform.

In some cases specific test Services are called out such as an OMS
Reference Service or CAL Reference Service. These test demonstration
Services could be an existing Service that contains sufficient
functionality to demonstrate a required capability. These test Services
could in fact be a single Service that performs the required
demonstrations called out for by the OMS Reference Service and CAL
Reference Service. Additionally, it is expected over time that the OACWG
will define and provide commonly used test Services for proving specific
functionality called out for in the VCRM.

Compliance Verification Cross Reference Matrix (VCRM)
-----------------------------------------------------

Table 8.1-1 is the Compliance Verification Cross Reference Matrix (VCRM)
for the OMS Standard.

<span id="_Toc219290737" class="anchor"></span>Table 8.1-1 Compliance
Verification Cross Reference Matrix (VCRM)

<table>
<thead>
<tr class="header">
<th><strong>Subsection</strong></th>
<th><strong>Requirement Text</strong></th>
<th><strong>Clarification</strong></th>
<th><strong>Subordinate Requirements</strong></th>
<th><strong>VR Tier</strong></th>
<th><strong>Allocation</strong></th>
<th><strong>VR#</strong></th>
<th><strong>Verification Requirement (VR)</strong></th>
<th><strong>Acceptance Criteria (AC)</strong></th>
<th><strong>Guidance</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-000427 (-1): This requirement is verified by inspection of the delivered Service Contract for the Isolator showing that the Service Contract is complete and complies with the current version of the Service Contract Template, OMSC-TMP-003; inspection results are recorded in the [[Service Contract]] tab of the Isolator Checklist, OMSC-CHK-006.</td>
<td>STD-000427 (-1)_1: The [[Service Contract]] tab of the Isolator Checklist shows that the delivered Service Contract is complete and complies with the current version of the Service Contract Template.</td>
<td>“Current Version” in this context refers to the version of the Service Contract Template specified in the OMS Standard against which compliance is being measured.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-000427 (-2): This requirement is verified by inspection of the delivered Service Contract for the Isolator for proprietary labels.</td>
<td>STD-000427 (-2)_1: The delivered Service Contract for the Isolator has no proprietary labels applied to any of its pages.</td>
<td>Although a Service Contract may contain references to proprietary documentation, the Service Contract itself must be non-proprietary.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-3</td>
<td>STD-000427 (-3): This requirement is verified by inspection of the Service Contract for the Isolator showing that each “messaging” data exchange that crosses the OMS-facing Isolator boundary and is implemented by the Isolator, is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-000427 (-3)_1: The [[OMS Msgs]] tab of the Isolator Checklist has been completed for each OMS Message crossing the OMS-facing Isolator boundary and documented in the delivered Service Contract.</p>
<p>STD-000427 (-3)_2: The [[Non-OMS Msgs]] tab of the Isolator Checklist has been completed for each Non-OMS Message crossing the OMS-facing Isolator boundary and documented in the delivered Service Contract.</p></td>
<td><p>OMS defines four types of data exchanges: (1) messaging, (2) data transfer, (3) special signals, and (4) security information exchanges. The intent is that each OMS Data Exchange and non-OMS data exchange that crosses the OMS-facing Isolator boundary is documented in the Service Contract. Security information exchanges are not applicable to an OMS Isolator.</p>
<p>This VR verifies that the “messaging” data exchanges are documented in the Service Contract. Inspection results are documented in the Isolator Checklist; OMS Messages in the [[OMS Msgs]] tab and Non-OMS Messages in the [[Non-OMS Msgs]] tab.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-4</td>
<td>STD-000427 (-4): This requirement is verified by inspection of the [[Non-OMS Msgs]] tab of the Isolator Checklist showing that there are no Non-OMS Messages crossing the OMS-facing Isolator boundary.</td>
<td><p>STD-000427 (-4)_1: If the [[Non-OMS Msgs]] tab of the Isolator Checklist shows there are no Non-OMS Messages crossing the OMS-facing Isolator boundary; then this VR is satisfied.</p>
<p>STD-000427 (-4)_2: If the [[Non-OMS Msgs]] tab of the Isolator Checklist documents any Non-OMS Messages crossing the OMS-facing Isolator boundary, the entry for each message includes the name of the Non-OMS Message, and supporting information/rationale as to why the Non-OMS Message could not be implemented as an OMS Message as defined in the OMS Standard.</p></td>
<td>The use of Non-OMS Messages are not OMS compliant.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-5</td>
<td>STD-000427 (-5): This requirement is verified by inspection of the Service Contract for the Isolator showing that each “data transfer” data exchange, that crosses the OMS-facing boundary and is implemented by the Isolator, is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-000427 (-5)_1: The [[OMS Data Transfer]] tab of the Isolator Checklist has been completed for each OMS Data Transfer crossing the OMS-facing Isolator boundary and documented in the delivered Service Contract.</p>
<p>STD-000427 (-5)_2: The [[Non-OMS Data Transfer]] tab of the Isolator Checklist has been completed for each Non-OMS Data Transfer crossing the OMS-facing Isolator boundary and documented in the delivered Service Contract.</p></td>
<td>This VR verifies that the “data transfer” data exchanges are documented in the Service Contract. Inspection results are documented in the Isolator Checklist; OMS Data Transfers in the [[OMS Data Transfer]] tab and Non-OMS Data Transfers in the [[Non-OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-6</td>
<td>STD-000427 (-6): This requirement is verified by inspection of the Service Contract for the Isolator showing that each “special signal” data exchange, that crosses the OMS-facing Isolator boundary and is implemented by the Isolator, is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-000427 (-6)_1: The [[OMS Special Signals]] tab of the Isolator Checklist has been completed for each OMS Special Signal crossing the OMS-facing Isolator boundary and documented in the delivered Service Contract.</p>
<p>STD-000427 (-6)_2: The [[Non-OMS Special Signals]] tab of the Isolator Checklist has been completed for each non-OMS special signal crossing the OMS-facing Isolator boundary and documented in the delivered Service Contract.</p></td>
<td>This VR verifies that the “special signals” data exchanges are documented in the Service Contract. Inspection results are documented in the Isolator Checklist; OMS Special Signals are documented in the [[OMS Special Signals]] tab and non-OMS special signals are documented in the [[Non-OMS Special Signals]] tab of the Isolator Checklist.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-7</td>
<td>STD-000427 (-7): This requirement is verified by inspection of the Service Contract for the Isolator showing that the ports and protocols the Isolator can use for data transfer are documented.</td>
<td><p>STD-000427 (-7)_1: If no ports or protocols are used for data transfer, then this VR is satisfied.</p>
<p>STD-000427 (-7)_2: The ports and protocols for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Ports and Protocols” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-8</td>
<td>STD-000427 (-8): This requirement is verified by inspection of the Service Contract for the Isolator showing that the confidentiality mechanism(s) the Isolator can use for data transfer are documented.</td>
<td><p>STD-000427 (-8)_1: If confidentiality for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000427 (-8)_2: The confidentiality mechanism(s) for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Confidentiality Mechanisms” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-9</td>
<td>STD-000427 (-9): This requirement is verified by inspection of the Service Contract for the Isolator showing that the integrity mechanism(s) the Isolator can use for data transfer are documented.</td>
<td><p>STD-000427 (-9)_1: If integrity for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000427 (-9)_2: The integrity mechanism(s) for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Integrity Mechanisms” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-000427 [An OMS Isolator shall be documented in a non-proprietary Service Contract, in accordance with the OMS Service Contract Template, for its interfaces that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-10</td>
<td>STD-000427 (-10): This requirement is verified by inspection of the Service Contract for the Isolator showing that the failure behavior(s) the Isolator can use for data transfer are documented.</td>
<td><p>STD-000427 (-10)_1: If failure behavior for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000427 (-10)_2: The failure behavior(s) for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Failure Behaviors” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-000431 [An OMS Isolator shall use the OMS CAL, for its interfaces that cross the OMS-facing Isolator boundary, to send and/or receive OMS Messages over the OMS ASB.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-000431 (-1): This requirement is verified by inspection of the Service Contract for the Isolator and the associated functional test results showing that each OMS Message used by the Isolator as an input/output message has successfully passed through a CAL between the Isolator and a test harness. The [[OMS Msgs]] tab of the Isolator Checklist, OMSC-CHK-006 is completed by listing each OMS Message used by the Isolator and documenting the location of the functional test results.</td>
<td><p>STD-000431 (-1)_1: The [[OMS Msgs]] tab of the Isolator Checklist has been completed and identifies each OMS Message used by the Isolator and the location of the associated functional test results for each OMS Message.</p>
<p>STD-000431 (-1)_2: The functional test results for the Isolator show that each OMS Message used by the Isolator and identified as an input/output message in the Service Contract, has been tested and has successfully passed through a CAL between the Isolator and a test harness.</p></td>
<td><p>Data exchanges over the OMS ASB that are not made using the OMS Message Schema are fully identified and documented in the Service Contract. Proprietary data exchanges over the OMS ASB are not OMS compliant.</p>
<p>Isolators connected to the OMS ASB may have some non-OMS interactions, but these non-OMS interactions will impact the OMS Tier level for the Mission Package.</p>
<p>Isolators do not need to be hosted in an OCE to be compliant. It is entirely possible for an Isolator to be hosted inside an OMS-compliant Subsystem.</p>
<p>Additionally, Isolators that have special requirements may be hosted outside of the OCE. Regardless of where Isolators are hosted, all OMS-compliant Isolators use the OMS CAL when communicating across the ASB.</p>
<p>The Starter Kit CAL or a CAL from another program is sufficient for testing this requirement.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-006939 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-006939 (-1): This requirement is verified by inspection of the Service Contract for the Isolator for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the data format per column B is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006939 (-1)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the data format in column B corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-006939 (-1)_2: Each data transfer using a data type/data format combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006939 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006939 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-006939 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-006939 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the data format per column B are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td>STD-006939 (-2)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the data format in column B corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-006939 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-3</td>
<td>STD-006939 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type/data format combination listed in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006939 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006939 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006939 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>Submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any Data Transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Isolator is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-006940 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-006940 (-1): This requirement is verified by inspection of the Service Contract for the Isolator for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the protocol/API per column C is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006940 (-1)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the protocol/API in column C corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-006940 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006940 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006940 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-006940 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-006940 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the protocols/APIs per column C are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td>STD-006940 (-2)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the protocol/API in column C corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-006940 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-3</td>
<td>STD-006940 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006940 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006940 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006940 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>Submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any Data Transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Isolator is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-010121 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-010121 (-1): This requirement is verified by inspection of the Service Contract for the Isolator for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the protocol/API per column D is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-010121 (-1)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the protocol/API in column D corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-010121 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-010121 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-010121 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-010121 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-010121 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the protocols/APIs per column D are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td>STD-010121 (-2)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the protocol/API in column D corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-010121 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-3</td>
<td>STD-010121 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-010121 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-010121 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-010121 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>Submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any Data Transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Isolator is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-006941 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-006941 (-1): This requirement is verified by inspection of the Service Contract for the Isolator for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the protocol/API for per column E is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006941 (-1)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the protocol/API in column E corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-006941 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006941 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006941 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-006941 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-006941 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the OMS-facing Isolator boundary; the data type per column A and the protocol/API per column E are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td>STD-006941 (-2)_1: If, for each data transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the protocol/API per column E corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-006941 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, an OMS Isolator shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Isolator</td>
<td>-3</td>
<td>STD-006941 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006941 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006941 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006941 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>Submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any Data Transfer formats, protocols, and APIs proposed to be changed/added/deleted</p>
<p>2. Red-lined versions of all Standard documentation affected by the change</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Isolator is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-006942 [An OMS Isolator shall use the URI formats, as specified in the “OMS URI formats” table, for data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-006942 (-1): This requirement is verified by inspection of the Service Contract for the Isolator for each data transfer that crosses the OMS-facing Isolator boundary; the URI format is identified for each data transfer and compared to the permitted formats listed in the “OMS URI Formats” table; the inspection results are recorded in the appropriate tabs of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006942 (-1)_1: If, for each Data Transfer crossing the OMS-facing Isolator boundary, the [[OMS Data Transfer]] tab of the Isolator Checklist shows that the Isolator uses the URI formats specified in the “OMS URI Formats” table, then this VR is satisfied.</p>
<p>STD-006942 (-1)_2: Each data transfer using a URI format that is not specified in the “OMS URI Formats” table is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006942 (-1)_3: A description of the URI format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006942 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a URI format specified in the “OMS URI Formats” table.</p></td>
<td><p>Data transfers that use one of the URI formats per the “OMS URI Formats” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted URI formats are recorded in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist.</p>
<p>If the URI formats listed in the “OMS URI Formats” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary URI format that is not represented in the “OMS URI Formats” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-006942 [An OMS Isolator shall use the URI formats, as specified in the “OMS URI formats” table, for data transfers that cross the OMS-facing Isolator boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-006942 (-2): This requirement is verified by inspection of the Change Request documentation which adds each URI format listed in the [[Non-OMS Data Transfer]] tab of the Isolator Checklist, OMSC-CHK-006.</td>
<td><p>STD-006942 (-2)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006942 (-2)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and the required changes to the “OMS URI Formats” table to add the URI formats to the OMS Standard has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006942 (-2)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>Submission of a Change Request is required to add a URI format not listed in the “OMS URI Formats” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any URI formats proposed to be changed/added/deleted</p>
<p>2. Red-lined versions of all Standard documentation affected by the change</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Isolator is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-008664 [An OMS Isolator shall report status in accordance with the “Required Functions” section of the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-008664 (-1): This requirement is verified by inspection of the delivered Service Contract for the Isolator that shows the status reporting is documented in accordance with the “Required Functions” section of the Service Contract Template, OMSC-TMP-003.</td>
<td>STD-008664 (-1)_1: The Service Contract for the Isolator documents the status reporting behavior in accordance with the “Required Functions” section of the service Contract template. A comparison of the delivered Service Contract to the template shows no significant differences.</td>
<td></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-008664 [An OMS Isolator shall report status in accordance with the “Required Functions” section of the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-008664 (-2): This requirement is verified by inspection of functional test results for the Isolator showing that the status messages are published in accordance with the required behavior as documented in the Service Contract.</td>
<td><p>STD-008664 (-2)_1: The functional test results for the Isolator show that that the <strong>ServiceStatus</strong> message is published by the Isolator.</p>
<p>STD-008664 (-2)_2: The functional test results for the Isolator show that the Isolator sends the <strong>ServiceStatusDataRequestStatus</strong> message in response to the <strong>ServiceStatusDataRequest</strong> message.</p></td>
<td>This information is typically provided in the “Service Status” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-008665 [An OMS Isolator shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-008665 (-1): This requirement is verified by inspection of the Service Contract for the Isolator showing that the status reporting is configurable.</td>
<td>STD-008665 (-1)_1: The Service Contract documents that the parameters for reporting status are configurable.</td>
<td>This information is typically provided in the “Required Functions” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-008665 [An OMS Isolator shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-2</td>
<td>STD-008665 (-2): This requirement is verified by inspection of the Service Contract for the Isolator showing that the mechanism used to configure status reporting is documented.</td>
<td>STD-008665 (-2)_1: The Service Contract documents the mechanism used to configure status reporting.</td>
<td>This information is typically provided in the “Required Functions” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-008665 [An OMS Isolator shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-3</td>
<td>STD-008665 (-3): This requirement is verified by inspection of the functional test results for the Isolator that show the status reporting can be configured for the Isolator and that the Isolator reports status in accordance with the configuration setting.</td>
<td><p>STD-008665 (-3)_1: The functional test results for the Isolator show that the periodicity of status reporting can be configured.</p>
<p>STD-008665 (-3)_2: The functional test results for the Isolator show that the Isolator reports status in accordance with the configuration setting.</p></td>
<td></td>
</tr>
<tr class="odd">
<td>Isolators</td>
<td>RQMT STD-008666 [An OMS Isolator shall implement a configurable range for periodic update rate from 1 to 600 seconds in 1 second increments.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-008666 (-1): This requirement is verified by inspection of the Service Contract for the Isolator showing that the parameters for status reporting are configurable with an acceptable range of 1 to 600 seconds in 1 second increments.</td>
<td>STD-008666 (-1)_1: The Service Contract documents that the configuration parameters for status reporting support the range of 1 to 600 seconds in 1 second increments.</td>
<td>This information is typically provided in the “Required Functions” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Isolators</td>
<td>RQMT STD-009707 [An OMS Isolator shall document its cybersecurity posture in accordance with the “Cybersecurity Posture” Section of the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Isolator</td>
<td>-1</td>
<td>STD-009707 (-1): This requirement is verified by inspection of the Service Contract “Cybersecurity Posture” Section showing that the Isolator cybersecurity posture is documented.</td>
<td><p>STD-009707 (-1)_1: If there is no program-assigned Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-009707 (-1)_2: The Isolator cybersecurity posture is documented in the Service Contract “Cybersecurity Posture” section.</p></td>
<td><p>The cybersecurity posture as defined by the CSRC and described by the CSAs denotes what an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The “Cybersecurity Posture” section describes the implementation of the cybersecurity posture by the Isolator and provides additional, unclassified, and/or non-proprietary details relating to the security of the OMS Isolator.</p>
<p>The provided OMSC-GDE-003, Cybersecurity Guide, defines the concepts, guidance, and information that OMS Adopting Programs and system designers will utilize to document the cybersecurity posture.</p></td>
</tr>
<tr class="odd">
<td>Abstract Service Bus (ASB)</td>
<td>RQMT STD-000144 [An OMS ASB shall support Internet Protocols IPv4 or IPv6.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000144 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that data exchanges using either IPv4 or IPv6 protocols are supported.</td>
<td>STD-000144 (-1)_1: The PDD documents that the transmission of data packets over either an IPv4 or IPv6 network is supported by the ASB.</td>
<td>This requirement is intended to show that UDP and TCP packet transfers over an IP network are fully supported by the ASB; this information is included in the “Abstract Service Bus” section of the PDD.</td>
</tr>
<tr class="even">
<td>Abstract Service Bus (ASB)</td>
<td>RQMT STD-000146 [An OMS ASB shall provide the OMS CAL.]</td>
<td></td>
<td>STD-000190</td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000146 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-000146 have been met.</td>
<td>STD-000146 (-1)_1: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000146 have been met for each applicable CAL implementation.</td>
<td><p>The OCE should have C++ and Java CAL implementations and optionally Language-Agnostic CAL implementations. Each distinct implementation of the CAL should meet this RQMT.</p>
<p>If Java is prohibited due to system security policy, then only a C++ CAL implementation would be required for the OCE.</p>
<p>The OMS Platform should provide Other Mission Processing elements in addition to those that host the OCE.</p></td>
</tr>
<tr class="odd">
<td>Abstract Service Bus (ASB)</td>
<td>RQMT STD-009706 [An OMS ASB shall provide OMS Security Information Exchanges.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-009706 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OMS ASB is capable of transmitting the OMS security information exchanges in accordance with the “Security Information Exchanges” section.</td>
<td>STD-009706 (-1)_1: The PDD, or the PDD Security Addendum, identifies the means for transmitting the OMS security information exchanges in accordance with the “Security Information Exchanges” section.</td>
<td><p>This information is documented in the Security Addendum for the PDD.</p>
<p>The Security Addendum is identified in the “Security Addendum” section of the PDD.</p></td>
</tr>
<tr class="even">
<td>Critical Abstraction Layer (CAL)</td>
<td>RQMT STD-000190 [An OMS CAL implementation shall be developed.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000190 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that a language-specific CAL implementation has been developed.</td>
<td>STD-000190 (-1)_1: The PDD documents that a language-specific CAL implementation has been developed.</td>
<td><p>Each distinct language-specific CAL implementation, C++ and Java, must adhere to the CAL Specification.</p>
<p>If an OMS Platform has additional mission processing elements outside of the OCE, then those additional CAL implementations will need to adhere as well.</p>
<p>This requirement may be satisfied by using the CAL Schema Compiler tool to generate the CAL API.</p></td>
</tr>
<tr class="odd">
<td>Critical Abstraction Layer (CAL)</td>
<td>RQMT STD-000190 [An OMS CAL implementation shall be developed.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-2</td>
<td>STD-000190 (-2): This requirement is verified by inspection of the CAL-VTS test results documenting the successful demonstration of the applicable language-specific CAL API and any requirement that is untestable by CAL-VTS is verified by inspection of the Platform Description Document (PDD) showing that the generated CAL API has been shown to be equivalent to the API generated by the CAL Schema Compiler.</td>
<td><p>STD-000190 (-2)_1: If all applicable language-specific CAL Specification CERTs are tested successfully by CAL-VTS, then this VR is satisfied.</p>
<p>STD-000190 (-2)_2: The PDD documents that the generated language-specific CAL API is equivalent with the API generated by the CAL Schema Compiler tool associated with the appropriate programming language interface generation specification.</p></td>
<td><p>Each distinct language-specific CAL implementation, C++ and Java, must adhere to the CAL Specification.</p>
<p>If an OMS Platform has additional mission processing elements outside of the OCE, then those additional CAL implementations will need to adhere as well.</p>
<p>This requirement may be satisfied by using CAL-VTS to evaluate the API.</p>
<p>In the context of this VR equivalence is defined as follows: A generated CAL API is “equivalent” to the API generated by the Schema Compiler if a Service that compiles against the Schema Compiler output API compiles against the generated CAL API with no change.</p></td>
</tr>
<tr class="even">
<td>Critical Abstraction Layer (CAL)</td>
<td>RQMT STD-000190 [An OMS CAL implementation shall be developed.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-3</td>
<td>STD-000190 (-3): This requirement is verified by inspection of the Platform Description Document (PDD) showing that provided language-agnostic CAL implementations have been developed.</td>
<td><p>STD-000190 (-3)_1: If a language-agnostic CAL implementation is not provided, then this VR is satisfied.</p>
<p>STD-000190 (-3)_2: The PDD documents that provided language-agnostic CAL implementations have been developed.</p></td>
<td><p>Each distinct language-agnostic CAL implementation must adhere to the Language-Agnostic CAL Specification.</p>
<p>A language-agnostic CAL implementation is not required; however, a Platform may choose to provide one or more implementations. All information needed to interact with each provided language-agnostic CAL implementation is provided in the PDD.</p></td>
</tr>
<tr class="odd">
<td>Critical Abstraction Layer (CAL)</td>
<td>RQMT STD-000190 [An OMS CAL implementation shall be developed.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-4</td>
<td>STD-000190 (-4): This requirement is verified by inspection of the functional test results documenting the provided language-agnostic CAL implementation(s) adhere to the Language-Agnostic CAL Specification.</td>
<td><p>STD-000190 (-4)_1: If a language-agnostic CAL implementation is not provided, then this VR is satisfied.</p>
<p>STD-000190 (-4)_2: The PDD documents the functional test results indicating provided language-agnostic CAL implementations adhere to the Language-Agnostic CAL Specification.</p></td>
<td><p>Each distinct language-agnostic CAL implementation must adhere to the Language-Agnostic CAL Specification.</p>
<p>A language-agnostic CAL implementation is not required; however, a Platform may choose to provide one or more implementations. All information needed to interact with each provided language-agnostic CAL implementation is provided in the PDD.</p>
<p>For each language-agnostic CAL implementation, functional test results show the language-agnostic CAL’s API has been implemented.</p></td>
</tr>
<tr class="even">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000350 [An OMS OCE shall host a C++ OMS CAL implementation.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000350 (-1): This requirement is verified by inspection of the functional test results documenting the successful demonstration of an OMS Reference Service running in the OCE under test and communicating through a C++ CAL implementation.</td>
<td>STD-000350 (-1)_1: The functional test results show that during the successful demonstration, an OMS Reference Service ran in the OCE under test and communicated through a C++ CAL implementation.</td>
<td></td>
</tr>
<tr class="odd">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000351 [An OMS OCE shall host a Java OMS CAL implementation.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000351 (-1): This requirement is verified by inspection of the functional test results documenting the successful demonstration of an OMS Reference Service running in the OCE under test and communicating through a Java CAL implementation.</td>
<td><p>STD-000351 (-1)_1: If Java is prohibited due to system security policy, then this VR is satisfied.</p>
<p>STD-000351 (-1)_2: The functional test results show that during the successful demonstration, an OMS Reference Service ran in the OCE under test and communicated through a Java CAL implementation.</p></td>
<td>If Java is prohibited due to system security policy, then only the C++ CAL implementation would be applicable for the OCE. </td>
</tr>
<tr class="even">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000352 [An OMS OCE shall be capable of hosting at least one Service.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000352 (-1): This requirement is verified by inspection of the functional test results documenting the successful demonstration of an OMS Reference Service running in the OCE under test and communicating through the CAL implementation.</td>
<td>STD-000352 (-1)_1: The functional test results show that during the successful demonstration, an OMS Reference Service successfully executed in the OCE and communicated through the CAL implementation.</td>
<td></td>
</tr>
<tr class="odd">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000354 [An OMS OCE shall synchronize system clock using an industry standard protocol identified in the “Approved Time Synchronization Protocols” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000354 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that time synchronization is supported by the OCE.</td>
<td>STD-000354 (-1)_1: The PDD documents the time synchronization mechanism(s) for the OCE.</td>
<td>This information is documented in the “Time Reference and Time synchronization” section of the PDD.</td>
</tr>
<tr class="even">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000355 [An OMS OCE shall provide time to OCE-hosted Services through operating system interfaces.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000355 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OCE system clock is accessed through operating system interfaces.</td>
<td>STD-000355 (-1)_1: The PDD identifies the operating system functions that can access the system clock.</td>
<td>This information is documented in the “Time Reference and Time Synchronization” section of the PDD.</td>
</tr>
<tr class="odd">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000360 [An OMS OCE shall provide a Linux operating system with a minimum kernel version of 2.6.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000360 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OCE provides a Linux operating system with kernel version equal to or greater than 2.6.</td>
<td>STD-000360 (-1)_1: The PDD documents that the kernel version of the OCE Linux operating system is equal to or greater than version 2.6.</td>
<td><p>This information is documented in the “OCE Processor Types, Operating Systems, and Configuration” section of the PDD.</p>
<p>The following is a mechanism to determine the kernel version to populate the PDD.</p>
<p>Run the “uname –a” command or similar that identifies the kernel version of the Linux operating system for the OCE.</p>
<p>The value of this command displays the kernel version and if it is equal to or greater than 2.6 then this requirement is satisfied.</p></td>
</tr>
<tr class="even">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000362 [An OMS OCE shall provide a 64 bit Linux operating system when the OCE is hosted on a 64 bit processing board.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000362 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that an OCE hosted on a 64 bit processing board provides a 64 bit Linux operating system.</td>
<td><p>STD-000362 (-1)_1: If the OCE is not hosted on a 64 bit processing board, then this VR is satisfied.</p>
<p>STD-000362 (-1)_2: The PDD documents that the OCE provides a 64 bit Linux operating system.</p></td>
<td><p>This requirement is only applicable when the OCE is hosted on 64 bit processing board.</p>
<p>This information is documented in the “OCE Processor Types, Operating Systems, and Configuration” section of the PDD.</p></td>
</tr>
<tr class="odd">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000365 [An OMS OCE shall provide a Façade implementation.]</td>
<td></td>
<td>STD-000381</td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000365 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-000365 have been met.</td>
<td>STD-000365 (-1)_1: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000365 have been met.</td>
<td></td>
</tr>
<tr class="even">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-008663 [An OMS OCE shall provide a Java implementation.]</td>
<td></td>
<td>STD-000385</td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-008663 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-008663 have been met.</td>
<td><p>STD-008663 (-1)_1: If Java is prohibited due to system security policy, then this VR is satisfied.</p>
<p>STD-008663 (-1)_2: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-008663 have been met.</p></td>
<td>If Java is prohibited due to system security policy, then only the C++ CAL implementation would be applicable for the OCE.</td>
</tr>
<tr class="odd">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000381 [An OMS OCE shall implement all allowed interfaces defined by the Operating System Façade Specification.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000381 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the Façade implementation provides, at a minimum, the allowed interfaces defined in the Operating System Façade Specification, OMSC-SPC-005.</td>
<td>STD-000381 (-1)_1: The PDD documents that the Façade implementation provides the allowed interfaces defined in the Operating System Façade Specification.</td>
<td><p>This information is documented in the “Isolation Layer” section of the PDD.</p>
<p>The OCE can provide interfaces other than those interfaces identified as allowed in the Operating System Façade Specification.</p>
<p>Specifically, it is discouraged, but permissible, for an OCE to provide the restricted interfaces.</p></td>
</tr>
<tr class="even">
<td>Open Computing Environment (OCE)</td>
<td>RQMT STD-000385 [An OMS OCE Java-based implementation shall provide a Java environment that is compliant with the Java specification.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000385 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OCE provides a Java environment that is compatible with a Long-Term Support (LTS) version of the Java specifications and is compatible with the Operating System (OS).</td>
<td><p>STD-000385 (-1)_1: If Java is prohibited due to system security policy, then this VR is satisfied.</p>
<p>STD-000385 (-1)_2: The PDD documents that the OCE provides a Java environment compatible with the OS.</p>
<p>STD-000385 (-1)_3: The PDD documents that the OCE provides a Java environment that is capable of running Java SE 11 compatible bytecode.</p></td>
<td><p>This information is documented in the “Build Environment and Tool Chain” section for the Java Environment in the PDD.</p>
<p>If Java is prohibited due to system security policy, then only the C++ CAL implementation would be applicable for the OCE.</p>
<p>The Java version may be considered for update as newer LTS versions become available.</p>
<p>Services should provide any required libraries that are not provided by the Platform under the current Java language specification.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000042 (-1): This requirement is verified by inspection of the delivered Service Contract showing that the Service Contract is complete and complies with the current version of the Service Contract Template, OMSC-TMP-003; inspection results are recorded in the [[Service Contract]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td>STD-000042 (-1)_1: The [[Service Contract]] tab of the Service Checklist shows that the delivered Service Contract is complete and complies with the current version of the Service Contract Template.</td>
<td>“Current Version” in this context refers to the version of the Service Contract Template specified in the OMS Standard against which compliance is being measured.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-2</td>
<td>STD-000042 (-2): This requirement is verified by inspection of the delivered OMS Service Contract for proprietary labels.</td>
<td>STD-000042 (-2)_1: The delivered Service Contract for the Service has no proprietary labels applied to any of its pages.</td>
<td>Although a Service Contract may contain references to proprietary documentation, the Service Contract itself must be non-proprietary.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-3</td>
<td>STD-000042 (-3): This requirement is verified by inspection of the Service Contract showing that each “messaging” data exchange that crosses the Service boundary and is implemented by the Service, is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000042 (-3)_1: The [[OMS Msgs]] tab of the Service Checklist has been completed for each OMS Message used by the Service and documented in the delivered Service Contract.</p>
<p>STD-000042 (-3)_2: The [[Non-OMS Msgs]] tab of the Service Checklist has been completed for each Non-OMS Message used by the Service and documented in the delivered Service Contract.</p></td>
<td><p>OMS defines four types of data exchanges: (1) messaging, (2) data transfer, (3) special signals, and (4) security information exchanges. The intent is that each OMS Data Exchange and non-OMS data exchange that crosses the Service boundary is documented in the Service Contract. Security information exchanges are not applicable to an OMS Service.</p>
<p>This VR verifies that the “messaging” data exchanges are documented in the Service Contract. Inspection results are documented in the Service Checklist; OMS Messages in the [[OMS Msgs]] tab and Non-OMS Messages in the [[Non-OMS Msgs]] tab.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-4</td>
<td>STD-000042 (-4): This requirement is verified by inspection of the [[Non-OMS Msgs]] tab of the Service Checklist showing that there are no Non-OMS Messages used by the Service.</td>
<td><p>STD-000042 (-4)_1: If the [[Non-OMS Msgs]] tab of the Service Checklist shows there are no Non-OMS Messages used by the Service, then this VR is satisfied.</p>
<p>STD-000042 (-4)_2: If the [[Non-OMS Msgs]] tab of the Service Checklist documents any Non-OMS Messages used by the Service, the entry for each message includes the name of the Non-OMS Message, and supporting information/rationale as to why the Non-OMS Message could not be implemented as an OMS Message as defined in the OMS Standard.</p></td>
<td>The use of Non-OMS Messages are not OMS compliant.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-5</td>
<td>STD-000042 (-5): This requirement is verified by inspection of the Service Contract showing that each “data transfer” data exchange that crosses the Service boundary and is implemented by the Service, is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000042 (-5)_1: The [[OMS Data Transfer]] tab of the Service Checklist has been completed for each OMS Data Transfer used by the Service and documented in the delivered Service Contract.</p>
<p>STD-000042 (-5)_2: The [[Non-OMS Data Transfer]] tab of the Service Checklist has been completed for the Non-OMS Data Transfers used by the Service and documented in the delivered Service Contract.</p></td>
<td>This VR verifies that the “data transfer” data exchanges are documented in the Service Contract; the OMS Data Transfers are listed in the [[OMS Data Transfer]] tab and the Non-OMS Data Transfers in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-6</td>
<td>STD-000042 (-6): This requirement is verified by inspection of the Service Contract showing that the ports and protocols the Service can use for data transfer are documented.</td>
<td><p>STD-000042 (-6)_1: If no ports or protocols are used for data transfer, then this VR is satisfied.</p>
<p>STD-000042 (-6)_2 : The ports and protocols for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Ports and Protocols” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-7</td>
<td>STD-000042 (-7): This requirement is verified by inspection of the Service Contract showing that the confidentiality mechanism(s) the Service can use for data transfer are documented.</td>
<td><p>STD-000042 (-7)_1: If confidentiality for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000042 (-7)_2: The confidentiality mechanism(s) for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Confidentiality Mechanisms” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-8</td>
<td>STD-000042 (-8): This requirement is verified by inspection of the Service Contract showing that the integrity mechanism(s) the Service can use for data transfer are documented.</td>
<td><p>STD-000042 (-8)_1: If integrity for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000042 (-8)_2: The integrity mechanism(s) for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Integrity Mechanisms” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000042 [A Tier 1 OMS Service shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-9</td>
<td>STD-000042 (-9): This requirement is verified by inspection of the Service Contract showing that the failure behavior(s) the Service can use for data transfer are documented.</td>
<td><p>STD-000042 (-9)_1: If failure behavior for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000042 (-9)_2: The failure behavior(s) for data transfer are documented in the Service Contract.</p></td>
<td>This information is typically provided in the “Data Transfer Failure Behaviors” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000043 [A Tier 1 OMS Service shall use the OMS CAL to send and/or receive OMS Messages over the OMS ASB.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000043 (-1): This requirement is verified by inspection of the Service Contract and the associated Service functional test results showing that each OMS Message used by the Service as an input/output message has successfully passed through a CAL between the Service and a test harness. The [[OMS Msgs]] tab of the Service Checklist, OMSC-CHK-005 is completed by listing each OMS Message used by the Service and documenting the location of the functional test results.</td>
<td><p>STD-000043 (-1)_1: The [[OMS Msgs]] tab of the Service Checklist has been completed and identifies each OMS Message used by the Service and the location of the associated Service functional test results for each OMS Message.</p>
<p>STD-000043 (-1)_2: The functional test results for the Service show that each OMS Message used by the Service and identified as an input/output message in the Service Contract, has been tested and has successfully passed through a CAL between the Service and a test harness.</p></td>
<td><p>Data exchanges over the OMS ASB that are not made using the OMS Message Schema are fully identified and documented in the Service Contract. Proprietary data exchanges over the OMS ASB are not OMS compliant.</p>
<p>Services connected to the OMS ASB may have some non-OMS interactions, but these non-OMS interactions will impact the OMS Tier level for the Service.</p>
<p>Services do not need to be hosted in an OCE to be compliant. It is entirely possible for a Service to be hosted inside an OMS-compliant Subsystem.</p>
<p>Additionally, Services that have special requirements may be hosted outside of the OCE. Regardless of where Services are hosted, all OMS-compliant Services use the OMS CAL when communicating across the ASB.</p>
<p>The Starter Kit CAL or a CAL from another program is sufficient for testing this requirement.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000044 [A Tier 1 OMS Service shall use the applicable Tier 1 Minimum Message Set messages.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the Tier 1 MMS that have similar content to messages the Service implements.</td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000044 (-1): This requirement is verified by inspection of the Service Contract showing that each Tier 1 Minimum Message Set (MMS) message that is applicable for this Service is used by the Service and is documented in the Service Contract; inspection results are recorded in the [[OMS Msgs]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000044 (-1)_1: The “Tier 1 MMS Compliant” column of the [[OMS Msgs]] tab shows that the Service uses each applicable message from the Tier 1 MMS.</p>
<p>STD-000044 (-1)_2: The entry for each Tier 1 MMS Message marked “Not Applicable” or “N/A” in the “Used” column of the [[OMS Msgs]] tab includes the rationale for the Service not implementing the message.</p>
<p>STD-000044 (-1)_3: A Change Request documenting each modified OMS message identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000044 (-1)_4: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>If a Service does not support a message in the MMS, then it does not have to implement that message.</p>
<p>For example, if an auto-routing Service does not support publishing product data, then it would not implement the <strong>ProductLocation</strong> message from the Tier 1 MMS.</p>
<p>If for example, this same auto-routing Service took as an input messages containing task information, then the <strong>Task</strong> message would be applicable from the Tier 1 MMS.</p>
<p>Any used message from the Tier 1 MMS marked “YES WITH MODIFICATION” and missing Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-004998 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-004998 (-1): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the data format per column B are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-004998 (-1)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that the data format in column B corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-004998 (-1)_2: Each data transfer using a data type/data format combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-004998 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-004998 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-004998 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-004998 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the data format per column B are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td>STD-004998 (-2)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that the data format in column B corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-004998 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-3</td>
<td>STD-004998 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type/data format combination listed in the [[Non-OMS Data Transfer]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-004998 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-004998 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-004998 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-004999 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-004999 (-1): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the protocol/API per column C are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-004999 (-1)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that the protocol/API in column C corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-004999 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfer” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-004999 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-004999 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-004999 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-004999 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the protocols/APIs per column C are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td>STD-004999 (-2)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that protocol/API in column C corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-004999 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-3</td>
<td>STD-004999 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-004999 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-004999 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-004999 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-010122 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-010122 (-1): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the protocol/API per column D are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-010122 (-1)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that the protocol/API in column D corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-010122 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfer” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-010122 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-010122 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-010122 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-010122 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the protocols/APIs per column D are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td>STD-010122 (-2)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that protocol/API in column D corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-010122 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-3</td>
<td>STD-010122 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-010122 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-010122 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-010122 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-005000 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-005000 (-1): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the protocol/API per column E are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-005000 (-1)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that the protocol/API in column E corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-005000 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfer” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-005000 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-005000 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-005000 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-005000 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the data type per column A and the protocol/API per column E are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td>STD-005000 (-2)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that protocol/API per column E corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-005000 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Service shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-3</td>
<td>STD-005000 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-005000 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-005000 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-005000 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted</p>
<p>2. Red-lined versions of all Standard documentation affected by the change</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-005001 [A Tier 1 OMS Service shall use the URI formats, as specified in the “OMS URI Formats” table, for its data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-005001 (-1): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Service boundary; the URI format is identified for each data transfer and compared to the permitted formats listed in the “OMS URI Formats” table; the inspection results are recorded in the appropriate tabs of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-005001 (-1)_1: If, for each data transfer crossing the Service boundary, the [[OMS Data Transfer]] tab of the Service Checklist shows that the Service uses the URI formats specified in the “OMS URI Formats” table, then this VR is satisfied.</p>
<p>STD-005001 (-1)_2: Each data transfer using a URI format that is not specified in the “OMS URI Formats” table is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-005001 (-1)_3: A description of the URI format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-005001 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a URI format specified in the “OMS URI Formats” table.</p></td>
<td><p>Data transfers that use one of the URI formats per the “OMS URI Formats” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted URI formats are recorded in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</p>
<p>If the URI formats listed in the “OMS URI Formats” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary URI format that is not represented in the “OMS URI Formats” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-005001 [A Tier 1 OMS Service shall use the URI formats, as specified in the “OMS URI Formats” table, for its data transfers that cross the Service boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-005001 (-2): This requirement is verified by inspection of the Change Request documentation which adds each URI format listed in the [[Non-OMS Data Transfer]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-005001 (-2)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-005001 (-2)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and the required changes to the “OMS URI Formats” table to add the URI formats to the OMS Standard has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-005001 (-2)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to add a URI format not listed in the “OMS URI Formats” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any URI formats proposed to be changed/added/deleted</p>
<p>2. Red-lined versions of all Standard documentation affected by the change</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000319 [A Tier 1 OMS Service shall report status in accordance with the “Service Status” section in the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000319 (-1): This requirement is verified by inspection of the delivered Service Contract that shows the status reporting is documented in accordance with the “Service Status” section of the Service Contract Template, OMSC-TMP-003.</td>
<td>STD-000319 (-1)_1: The Service Contract documents the status reporting behavior in accordance with the “Service Status” section of the Service Contract template. A comparison of the delivered Service Contract to the template shows no significant differences.</td>
<td>This information is typically provided in the “Service Status” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000319 [A Tier 1 OMS Service shall report status in accordance with the “Service Status” section in the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-2</td>
<td>STD-000319 (-2): This requirement is verified by inspection of functional test results showing that the Status messages are published in accordance with the required behavior as documented in the Service Contract.</td>
<td><p>STD-000319 (-2)_1: The functional test results for the Service show that that the <strong>ServiceStatus</strong> message is published by the Service.</p>
<p>STD-000319 (-2)_2: The functional test results for the Service show that the Service sends the <strong>ServiceStatusDataRequestStatus</strong> message in response to the <strong>ServiceStatusDataRequest</strong> message.</p></td>
<td></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000320 [A Tier 1 OMS Service shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000320 (-1): This requirement is verified by inspection of the Service Contract showing that the status reporting is configurable.</td>
<td>STD-000320 (-1)_1: The Service Contract documents that the parameters for reporting status are configurable.</td>
<td>This information is typically provided in the “Service Status” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000320 [A Tier 1 OMS Service shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-2</td>
<td>STD-000320 (-2): This requirement is verified by inspection of the Service Contract showing that the mechanism used to configure status reporting is documented.</td>
<td>STD-000320 (-2)_1: The Service Contract documents the mechanism used to configure status reporting.</td>
<td></td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000320 [A Tier 1 OMS Service shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-3</td>
<td>STD-000320 (-3): This requirement is verified by inspection of the functional test results for the Service that show the status reporting can be configured for the Service and that the Service reports status in accordance with the configuration setting.</td>
<td><p>STD-000320 (-3)_1: The functional test results for the Service show that the periodicity of status reporting can be configured.</p>
<p>STD-000320 (-3)_2: The functional test results for the Service show that the Service reports status in accordance with the configuration setting.</p></td>
<td></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000321 [A Tier 1 OMS Service shall implement a configurable range for periodic update rate from 1 to 600 seconds in 1 second increments.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000321 (-1): This requirement is verified by inspection of the Service Contract showing that the parameters for status reporting are configurable with an acceptable range of 1 to 600 seconds in 1 second increments.</td>
<td>STD-000321 (-1)_1: The Service Contract documents that the configuration parameters for status reporting support the range of 1 to 600 seconds in 1 second increments.</td>
<td>This information is typically provided in the “Service Status” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000872 [A Tier 1 OMS Service shall have a <strong>NORMAL</strong> state.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000872 (-1): This requirement is verified by inspection of the Service Contract showing that the Service has a <strong>NORMAL</strong> state.</td>
<td>STD-000872 (-1)_1: The Service Contract documents that the Service has a <strong>NORMAL</strong> state which indicates that the Service is functioning normally, configuration files are loaded, and all functions are usable.</td>
<td><p>The <strong>NORMAL</strong> state is defined in the “OMS Service State Definitions and Allowed Transitions” table.</p>
<p>This information is typically provided in the “Allowed States and Transitions” section of the Service Contract.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-000873 [A Tier 1 OMS Service shall use applicable state transitions defined in the “Allowed State Transitions for OMS Service” figure.]</td>
<td>In the context of this requirement the term “applicable” means those state transitions that are required or used by the Service.</td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000873 (-1): This requirement is verified by inspection of the Service Contract that shows the state transitions of the Service are in accordance with the “Allowed State Transitions for OMS Service” figure in the OMS Standard.</td>
<td>STD-000873 (-1)_1: The Service Contract documents that the Service enters and exits each state only through permissible state transitions as identified in the “Allowed State Transitions for OMS Service” figure.</td>
<td>This information is typically provided in a state diagram for the Service included in the “Allowed States and Transitions” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Service Tier 1 Requirements</td>
<td>RQMT STD-009708 [A Tier 1 OMS Service shall document its cybersecurity posture in accordance with the “Cybersecurity Posture” section in the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-009708 (-1): This requirement is verified by inspection of the Service Contract “Cybersecurity Posture” section showing that the Service cybersecurity posture is documented.</td>
<td><p>STD-009708 (-1)_1: If there is no program-assigned Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-009708 (-1)_2: The Service cybersecurity posture is documented in the Service Contract “Cybersecurity Posture” section.</p></td>
<td><p>The cybersecurity posture as defined by the CSRC and described by the CSAs denotes what an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The “Cybersecurity Posture” section describes the implementation of the cybersecurity posture by Service and provides additional, unclassified, and/or non-proprietary details relating to the security of the Service.</p>
<p>The provided OMSC-GDE-003, Cybersecurity Guide, defines the concepts, guidance, and information that OMS Adopting Programs and system designers will utilize to document the cybersecurity posture.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 2 Requirements</td>
<td>RQMT STD-000050 [A Tier 2 OMS Service shall meet Tier 1 Service requirements.]</td>
<td></td>
<td><p>STD-000042</p>
<p>STD-000043</p>
<p>STD-000044</p>
<p>STD-000319</p>
<p>STD-000320</p>
<p>STD-000321</p>
<p>STD-000872</p>
<p>STD-000873</p>
<p>STD-004998</p>
<p>STD-004999</p>
<p>STD-005000</p>
<p>STD-005001</p>
<p>STD-009708</p>
<p>STD-010122</p></td>
<td>2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000050 (-1): This requirement is verified by the inspection of the [[Service RQMT Checklist]] tab of the Service Checklist, OMSC-CHK-005, that shows the subordinate requirements for RQMT STD-000050 have been met.</td>
<td>STD-000050 (-1)_1: The [[Service RQMT Checklist]] tab of the Service Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000050 have been met.</td>
<td>Tier 2 OMS Services must meet all Tier 1 OMS Service requirements.</td>
</tr>
<tr class="even">
<td>Service Tier 2 Requirements</td>
<td>RQMT STD-000051 [A Tier 2 OMS Service shall use the applicable Tier 2 Minimum Message Set messages.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the Tier 2 MMS that have similar content to messages the Service implements.</td>
<td></td>
<td>2, 3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000051 (-1): This requirement is verified by inspection of the Service Contract showing that each Tier 2 Minimum Message Set (MMS) message that is applicable for this Service is used by the Service and is documented in the Service Contract; inspection results are recorded in the [[OMS Msgs]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000051 (-1)_1: The “Tier 2 MMS Compliant” column of the [[OMS Msgs]] tab shows that the Service uses each applicable message from the Tier 2 MMS.</p>
<p>STD-000051 (-1)_2: The entry for each Tier 2 MMS Message marked “Not Applicable” or “N/A” in the “Used” column of the [[OMS Msgs]] tab includes the rationale for the Service not implementing the message.</p>
<p>STD-000051 (-1)_3: A Change Request documenting each modified OMS message identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000051 (-1)_4: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>If a Service does not support a message in the MMS, then it does not have to implement that message.</p>
<p>For example, if an auto-routing Service does not support publishing approval authority data, then it would not implement the <strong>ApprovalAuthority</strong> message from the Tier 2 MMS.</p>
<p>If for example, this same auto-routing Service took as an input, messages containing mission plan information, then the <strong>MissionPlan</strong> message would be applicable from the Tier 2 MMS.</p>
<p>Any used message from the Tier 2 MMS marked “YES WITH MODIFICATION” and missing Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 3 Requirements</td>
<td>RQMT STD-000053 [A Tier 3 OMS Service shall meet Tier 2 Service requirements.]</td>
<td></td>
<td><p>STD-000050</p>
<p>STD-000051</p></td>
<td>3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000053 (-1): This requirement is verified by the inspection of the [[Service RQMT Checklist]] tab of the Service Checklist, OMSC-CHK-005, that shows the subordinate requirements for RQMT STD-000053 have been met.</td>
<td>STD-000053 (-1)_1: The [[Service RQMT Checklist]] tab of the Service Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000053 have been met.</td>
<td>Tier 3 OMS Services must meet all Tier 1 and Tier 2 OMS Service requirements.</td>
</tr>
<tr class="even">
<td>Service Tier 3 Requirements</td>
<td>RQMT STD-000054 [A Tier 3 OMS Service shall use applicable OMS Special Signals as listed in the “Special Signals” section.]</td>
<td><p>In the context of this requirement the term “applicable” means that any special signals implemented by the Service are in accordance with the “Special Signals” section.</p>
<p>A Service is not required to implement any special signals if they are not applicable, and the Service can still be considered OMS compliant.</p></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000054 (-1): This requirement is verified by inspection of the Service Contract showing that each special signal implemented by the Service is in accordance with the “Special Signals” section; inspection results for OMS Special Signals are documented in the [[OMS Special Signals]] tab, and non-OMS special signals are documented in the [[Non-OMS Special Signals]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000054 (-1)_1: If the Service does not implement any special signals, then this VR is satisfied.</p>
<p>STD-000054 (-1)_2: The [[OMS Special Signals]] tab and the [[Non-OMS Special Signals]] tab of the Service Checklist have been completed and document each special signal implemented by the Service as described in the Service Contract.</p>
<p>STD-000054 (-1)_3: The [[OMS Special Signals]] tab shows that each OMS Special Signal implemented by the Service is in accordance with the appropriate table in the OMS Standard; i.e., the “OMS Discrete and Voltage Reference Signals” table, or the “OMS Discrete and Voltage Time Reference Signals” table, or the “Other Signals Defined within OMS” table.</p>
<p>STD-000054 (-1)_4: Each non-OMS special signal implemented by the Service that is listed in the “Non-OMS Special Signals Allowed in the OMS Standard” table is identified in the top section of the [[Non-OMS Special Signals]] tab. Note that OMS compliance assessment will be restricted to no more than Tier 2.</p>
<p>STD-000054 (-1)_5: Each non-OMS special signal implemented by the Service that is not listed in the “Non-OMS Special Signals Superseded by OMS Messages” table is identified in the middle section of the [[Non-OMS Special Signals]] tab. Note that OMS compliance assessment will be restricted to no more than Tier 2.</p>
<p>STD-000054 (-1)_6: Each non-OMS special signal implemented by the Service that is not listed in the “Non-OMS Special Signals Superseded by OMS Messages” table is identified in the bottom section of the [[Non-OMS Special Signals]] tab. Note that there must be an OACWG-approved Change Request Identifier listed in order to be OMS compliant.</p></td>
<td><p>This information is typically provided in the “Special Signals” section of the Service Contract.</p>
<p>The “Non-OMS Special Signals Allowed in the OMS Standard” table identifies the signals considered outside the bounds of OMS standardization. However, these signals are allowed but OMS compliance assessment will be restricted to no more than Tier 2.</p>
<p>However, special signals that have been replaced by OMS Messages are identified in the “Non-OMS Special Signals Superseded by OMS Messages” table, and in these cases, the OMS Message should be used in place of the special signal for the Service to be OMS compliant at Tier 3.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 3 Requirements</td>
<td>RQMT STD-000054 [A Tier 3 OMS Service shall use applicable OMS Special Signals as listed in the “Special Signals” section.]</td>
<td><p>In the context of this requirement the term “applicable” means that any special signals implemented by the Service are in accordance with the “Special Signals” section.</p>
<p>A Service is not required to implement any special signals if they are not applicable, and the Service can still be considered OMS compliant.</p></td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-000054 (-2): This requirement is verified by inspection of the Change Request documentation which adds any non-OMS special signals documented in the [[Non-OMS Special Signals]] tab of the Service Checklist, OMSC-CHK-005 that are not listed in the “Non-OMS Special Signals Superseded by OMS Messages” table.</td>
<td><p>STD-000054 (-2)_1: If the [[Non-OMS Special Signals]] tab shows that there are no non-OMS special signals implemented by the Service, or that the only non-OMS special signals implemented by the Service are listed in the “Other Non-OMS Special Signal” table, then this VR is satisfied.</p>
<p>STD-000054 (-2)_2: A Change Request documenting each non-OMS special signal identified in the [[Non-OMS Special Signals]] tab, that is listed in the “Other Non-OMS Special Signal” table, has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000054 (-2)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Special Signals]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request to add a non-OMS special signal will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any special signals proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these special signals and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Service Tier 3 Requirements</td>
<td>RQMT STD-000055 [A Tier 3 OMS Service shall use the applicable messages in the OMS Message Set.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the OMS Standard, that have similar content to messages the Service implements.</td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-1</td>
<td>STD-000055 (-1): This requirement is verified by comparing the Service Contract to the Service Checklist and showing that each message crossing the Service boundary has been recorded in the appropriate tab of the Service Checklist, OMSC-CHK-005; OMS Messages in the [[OMS Msgs]] tab.</td>
<td>STD-000055 (-1)_1: Each message crossing the Service boundary and documented in the Service Contract is listed in the [[OMS Msgs]] tab of the Service Checklist.</td>
<td><p>If a Service does not support a message in the OMS Standard then it does not have to implement that message.</p>
<p>However if, for example, a sensor controller Service takes as an input, messages containing weather information then the appropriate OMS weather message would be applicable.</p>
<p>At Tier 3, an OMS Service is required to implement each applicable OMS Message from the Tier 1 and Tier 2 Minimum Message Sets.</p>
<p>Any additional messages used by a Tier 3 OMS Service are required to be OMS Messages or are submitted in a Change Request and approved by OACWG.</p></td>
</tr>
<tr class="odd">
<td>Service Tier 3 Requirements</td>
<td>RQMT STD-000055 [A Tier 3 OMS Service shall use the applicable messages in the OMS Message Set.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the OMS Standard, that have similar content to messages the Service implements.</td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-2</td>
<td>STD-000055 (-2): This requirement is verified by inspection of the Change Request documentation which adds any new OMS messages documented in the [[OMS Msgs]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000055 (-2)_1: If the [[OMS Msgs]] tab of the Service Checklist shows there are no new OMS messages used by the Service; then this VR is satisfied.</p>
<p>STD-000055 (-2)_2: A Change Request documenting each new OMS message identified in the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000055 (-2)_3: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of the updated OMS Message Schema proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these messages and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the messages approved by the OACWG for the Change Request and using the CAL for passing the messages.</p>
<p>Any new message used without Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="even">
<td>Service Tier 3 Requirements</td>
<td>RQMT STD-000055 [A Tier 3 OMS Service shall use the applicable messages in the OMS Message Set.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the OMS Standard, that have similar content to messages the Service implements.</td>
<td></td>
<td>3</td>
<td>Service</td>
<td>-3</td>
<td>STD-000055 (-3): This requirement is verified by inspection of the Change Request documentation which adds any modified OMS messages documented in the [[OMS Msgs]] tab of the Service Checklist, OMSC-CHK-005.</td>
<td><p>STD-000055 (-3)_1: If the Service Checklist shows there are no modified OMS messages identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab, then this VR is satisfied.</p>
<p>STD-000055 (-3)_2: A Change Request documenting each modified OMS message identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000055(-3)_3: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of the updated OMS Message Schema proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these messages and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the messages approved by the OACWG for the Change Request and using the CAL for passing the messages.</p>
<p>Any used message marked “YES WITH MODIFICATION” and missing Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000059 (-1): This requirement is verified by inspection of the delivered Subsystem Description Document (SDD) showing that SDD is complete and complies with the current version of the SDD Template, OMSC-TMP-002; inspection results are recorded in the [[SDD]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-000059 (-1)_1: The [[SDD]] tab of the Subsystem Checklist shows that the delivered SDD is complete and complies with the current version of the SDD Template.</td>
<td>“Current Version” in this context refers to the version of the SDD Template specified in the OMS Standard against which compliance is being measured.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-000059 (-2): This requirement is verified by inspection of the delivered Subsystem Description Document (SDD) showing that the document does not include proprietary labels; and that the Security Information Exchanges implemented by the Subsystem are documented in the SDD.</td>
<td><p>STD-000059 (-2)_1: The delivered SDD for the Subsystem has no proprietary labels applied to any of its pages.</p>
<p>STD-000059 (-2)_2: The SDD, or the SDD Security Addendum, documents the Security Information Exchanges implemented by the Subsystem.</p></td>
<td><p>Although an SDD may contain references to proprietary documentation, the SDD itself must be non-proprietary.</p>
<p>The “Security Addendum” section of the SDD identifies the unclassified and non-proprietary name of the Security Addendum document. The Security Addendum may be both classified and proprietary.</p>
<p>The Security Addendum describes the Security Information Exchanges implemented by the Subsystem and provides additional, classified, and/or proprietary details relating to the security of the Subsystem.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-000059 (-3): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the ports and protocols for data transfer for the Subsystem are documented.</td>
<td><p>STD-000059 (-3)_1: If no ports or protocols are used for data transfer, then this VR is satisfied.</p>
<p>STD-000059 (-3)_2: The ports and protocols for data transfer are documented in the SDD.</p></td>
<td>This information is typically provided in the “Open Ports and Protocols” section of the SDD.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-4</td>
<td>STD-000059 (-4): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the mechanism for restricting the ports and protocols for data transfers for the Subsystem is documented.</td>
<td><p>STD-000059 (-4)_1: If restricting ports or protocols for data transfers is not required, then this VR is satisfied.</p>
<p>STD-000059 (-4)_2: The mechanism for restricting the ports and protocols for data transfers is documented in the SDD.</p></td>
<td>This information is typically provided in the “Open Ports and Protocols” section of the SDD.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-5</td>
<td>STD-000059 (-5): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the access control mechanisms for data storage for the Subsystem are documented.</td>
<td><p>STD-000059 (-5)_1: If access control for data storage is not required, then this VR is satisfied.</p>
<p>STD-000059 (-5)_2: The access control mechanisms for data storage are documented in the SDD.</p></td>
<td>This information is typically provided in the “Data Storage Access Controls” section of the SDD.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-6</td>
<td>STD-000059 (-6): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the confidentiality mechanisms for data storage for the Subsystem are documented.</td>
<td><p>STD-000059 (-6)_1: If confidentiality for data storage is not required, then this VR is satisfied.</p>
<p>STD-000059 (-6)_2: The confidentiality mechanisms for data storage are documented in the SDD.</p></td>
<td>This information is typically provided in the “Data Storage Confidentiality Mechanisms” section of the SDD.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-7</td>
<td>STD-000059 (-7): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the integrity mechanisms for data storage for the Subsystem are documented.</td>
<td><p>STD-000059 (-7)_1: If integrity for data storage is not required, then this VR is satisfied.</p>
<p>STD-000059 (-7)_2: The integrity mechanisms for data storage are documented in the SDD.</p></td>
<td>This information is typically provided in the “Data Storage Integrity Mechanisms” section of the SDD.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-8</td>
<td>STD-000059 (-8): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the confidentiality mechanisms for data transfer for the Subsystem are documented.</td>
<td><p>STD-000059 (-8)_1: If confidentiality for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000059 (-8)_2: The confidentiality mechanisms for data transfer are documented in the SDD.</p></td>
<td>This information is typically provided in the “Data Transfer Confidentiality Mechanisms for Data Storage” section of the SDD.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-9</td>
<td>STD-000059 (-9): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the integrity mechanisms for data transfer for the Subsystem are documented.</td>
<td><p>STD-000059 (-9)_1: If integrity for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000059 (-9)_2: The integrity mechanisms for data transfer are documented in the SDD.</p></td>
<td>This information is typically provided in the “Data Transfer Integrity Mechanisms for Data Storage” section of the SDD.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000059 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Subsystem Description Document in accordance with the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-10</td>
<td>STD-000059 (-10): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that the identification and authentication mechanisms the Subsystem can use for data transfer are documented.</td>
<td><p>STD-000059 (-10)_1: If identification and authentication for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000059 (-10)_2: The identification and authentication mechanisms for data transfer are documented in the SDD.</p></td>
<td>This information is typically provided in the “Data Transfer Configuration for Data Storage” section of the SDD.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000060 (-1): This requirement is verified by inspection of the delivered Service Contract for the Subsystem showing that the Service Contract is complete and complies with the current version of the Service Contract Template, OMSC-TMP-003; inspection results are recorded in the [[Service Contract]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-000060 (-1)_1: The [[Service Contract]] tab of the Subsystem Checklist shows that the delivered Service Contract is complete and complies with the current version of the Service Contract Template.</td>
<td>“Current Version” in this context refers to the version of the Service Contract Template specified in the OMS Standard against which compliance is being measured.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-000060 (-2): This requirement is verified by inspection of the delivered Service Contract for the Subsystem for proprietary labels.</td>
<td>STD-000060 (-2)_1: The delivered Service Contract for the Subsystem has no proprietary labels applied to any of its pages.</td>
<td>Although a Service Contract may contain references to proprietary documentation, the Service Contract itself must be non-proprietary.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-000060 (-3): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each “messaging” data exchange that crosses the Subsystem boundary and is implemented by the Subsystem, is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000060 (-3)_1: The [[OMS Msgs]] tab of the Subsystem Checklist has been completed for each OMS Message used by the Subsystem and documented in the delivered Service Contract.</p>
<p>STD-000060 (-3)_2: The [[Non-OMS Msgs]] tab of the Subsystem Checklist has been completed for each Non-OMS Message used by the Subsystem and documented in the delivered Service Contract.</p></td>
<td><p>The intent is that all OMS Data Exchanges (except Security Information Exchanges) and non-OMS data exchanges that cross the Subsystem boundary are documented in the Service Contract.</p>
<p>Security Information Exchanges are documented in the SDD.</p>
<p>The term “Data Exchanges” with capitalization refers to the four defined types of OMS Data Exchanges (OMS Messaging, Data Transfer, Special Signals, and Security Information Exchanges), whereas “data exchanges” without capitalization refers to any OMS or non-OMS data exchange.</p>
<p>This VR verifies that the “messaging” data exchanges are documented; OMS Messages in the [[OMS Msgs]] tab and Non-OMS Messages in the [[Non-OMS Msgs]] tab.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-4</td>
<td>STD-000060 (-4): This requirement is verified by inspection of the [[Non-OMS Msgs]] tab of Subsystem Checklist showing that there are no Non-OMS Messages used by the Subsystem.</td>
<td><p>STD-000060 (-4)_1: If the [[Non-OMS Msgs]] tab of the Subsystem Checklist shows there are no Non-OMS Messages used by the Subsystem, then this VR is satisfied.</p>
<p>STD-000060 (-4)_2: If the [[Non-OMS Msgs]] tab of the Subsystem Checklist documents any Non-OMS Messages used by the Subsystem, the entry for each message includes the name of the Non-OMS Message, and supporting information/rationale as to why the Non-OMS Message could not be implemented as an OMS Message as defined in the OMS Standard.</p></td>
<td>The use of Non-OMS Messages are not OMS compliant.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-5</td>
<td>STD-000060 (-5): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each “data transfer” data exchange that crosses the Subsystem boundary and is implemented by the Subsystems is documented in the delivered Service Contract; the inspection results are recorded in the appropriate tabs in the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000060 (-5)_1: The [[OMS Data Transfer]] tab of the Subsystem Checklist has been completed for each OMS Data Transfer used by the Subsystem and documented in the delivered Service Contract.</p>
<p>STD-000060 (-5)_2: The [[Non-OMS Data Transfer]] tab of the Subsystem Checklist has been completed for each Non-OMS Data Transfer used by the Subsystem and documented in the delivered Service Contract.</p></td>
<td><p>The intent is that all OMS Data Exchanges (except Security Information Exchanges) and non-OMS data exchanges that cross the Subsystem boundary are documented in the Service Contract.</p>
<p>The term “Data Exchanges” with capitalization refers to the four defined types of OMS Data Exchanges (OMS Messaging, Data Transfer, Special Signals, and Security Information Exchanges), whereas “data exchanges” without capitalization refers to any OMS or non-OMS data exchange.</p>
<p>This VR verifies that the “data transfer” data exchanges are documented; OMS Data Transfer in the [[OMS Data Transfer]] tab and Non-OMS Data Transfer in the [[Non-OMS Data Transfer]] tab.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-6</td>
<td>STD-000060 (-6): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the ports and protocols the Subsystem can use for data transfer are documented.</td>
<td><p>STD-000060 (-6)_1: If no ports or protocols are used for data transfer, then this VR is satisfied.</p>
<p>STD-000060 (-6)_2 : The ports and protocols for data transfer are documented in the Service Contract.</p></td>
<td><p>This information is typically provided in the “Data Transfer Ports and Protocols” section of the Service Contract.</p>
<p>If the information for this Subsystem is provided in the Subsystem Description Document (SDD), a cross reference to the SDD will satisfy this requirement.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-7</td>
<td>STD-000060 (-7): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the confidentiality mechanism(s) the Subsystem can use for data transfer are documented.</td>
<td><p>STD-000060 (-7)_1: If confidentiality for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000060 (-7)_2: The confidentiality mechanism(s) for data transfer are documented in the Service Contract.</p></td>
<td><p>This information is typically provided in the “Data Transfer Confidentiality Mechanisms” section of the Service Contract.</p>
<p>If the information for this Subsystem is provided in the Subsystem Description Document (SDD), a cross reference to the SDD will satisfy this requirement.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-8</td>
<td>STD-000060 (-8): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the integrity mechanism(s) the Subsystem can use for data transfer are documented.</td>
<td><p>STD-000060 (-8)_1: If integrity for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000060 (-8)_2: The integrity mechanism(s) for data transfer are documented in the Service Contract.</p></td>
<td><p>This information is typically provided in the “Data Transfer Integrity Mechanisms” section of the Service Contract.</p>
<p>If the information for this Subsystem is provided in the Subsystem Description Document (SDD), a cross reference to the SDD will satisfy this requirement.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000060 [A Tier 1 OMS Subsystem shall be documented in a non-proprietary Service Contract in accordance with the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-9</td>
<td>STD-000060 (-9): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the failure behavior(s) the Subsystem can use for data transfer are documented.</td>
<td><p>STD-000060 (-9)_1: If failure behavior for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000060 (-9)_2: The failure behavior(s) for data transfer are documented in the Service Contract.</p></td>
<td><p>This information is typically provided in the “Data Transfer Failure Behaviors” section of the Service Contract.</p>
<p>If the information for this Subsystem is provided in the Subsystem Description Document (SDD), a cross reference to the SDD will satisfy this requirement.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000061 [A Tier 1 OMS Subsystem shall use the OMS CAL to send and/or receive OMS Messages over the OMS ASB.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD 000061 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem and the associated functional test results showing that each OMS Message used by the Subsystem as an input/output message has successfully passed through a CAL between the Subsystem and a test harness. The [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004 is completed by listing each OMS Message used by the Subsystem and documenting the location of the functional test results.</td>
<td><p>STD-000061 (-1)_1: The [[OMS Msgs]] tab of the Subsystem Checklist has been completed and identifies each OMS Message used by the Subsystem and the location of the associated functional test results for each OMS Message.</p>
<p>STD-000061 (-1)_2: The functional test results for the Subsystem show that each OMS Message used by the Subsystem and identified as an input/output message in the Service Contract, has been tested and has successfully passed through a CAL between the Subsystem and a test harness.</p></td>
<td><p>OMS-compliant Subsystems pass OMS Messages via the CAL either directly or via an Adapter. Both of these integration patterns are valid and deemed compliant, as long as the messaging goes through the CAL.</p>
<p>A Subsystem Adapter may have proprietary data exchanges between the Adapter and the Subsystem.</p>
<p>Data exchanges over the OMS ASB that are not made using the OMS Message Schema will be fully identified and documented in the Service Contract.</p>
<p>Proprietary data exchanges over the OMS ASB are not OMS compliant.</p>
<p>Subsystems connected to the OMS ASB may have some non-OMS interactions, but these non-OMS interactions will impact the OMS Tier level for the Subsystem.</p>
<p>Subsystem Adapters should be tested either with the actual Subsystem or a representative emulator.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000063 [A Tier 1 OMS Subsystem shall use the Tier 1 Required Subsystem Message Set messages that are associated with the capabilities provided.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000063 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each Tier 1 Required Subsystem Message Set message that is applicable for this Subsystem is used by the Subsystem and is documented in the Service Contract for each capability implemented by the Subsystem; inspection results are recorded in the [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000063 (-1)_1: The “Tier 1 Required Subsystem Compliant” column of the [[OMS Msgs]] tab shows that the Subsystem uses each applicable message from the Tier 1 Required Subsystem Set.</p>
<p>STD-000063 (-1)_2: The entry for each Tier 1 Required Subsystem Message marked “Not Applicable” or “N/A” in the “Used” column of the [[OMS Msgs]] tab includes the rationale for the Subsystem not implementing the message.</p></td>
<td><p>For each capability (e.g., AMTI, AO, Comm, EA, ESM, PO, SAR, SMTI, Strike) the required message set includes:</p>
<p><strong>&lt;capability&gt;_Capability</strong></p>
<p><strong>&lt;capability&gt;_CapabilityStatus</strong></p>
<p><strong>&lt;capability&gt;_Command</strong></p>
<p><strong>&lt;capability&gt;_CommandStatus</strong></p>
<p><strong>&lt;capability&gt;_Activity</strong>.</p>
<p>The <strong>&lt;capability&gt;_Command</strong> is received as an input; the remaining messages are published as outputs.</p>
<p>Some OMS Subsystems do not have any commanded capabilities, such as an autonomous Subsystem. In this case the Subsystem only has to provide:</p>
<p><strong>&lt;capability&gt;_Capability</strong></p>
<p><strong>&lt;capability&gt;_CapabilityStatus</strong>.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000064 [A Tier 1 OMS Subsystem shall use the applicable Tier 1 Minimum Message Set messages.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the Tier 1 MMS that have similar content to messages the Subsystem implements.</td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000064 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each Tier 1 Minimum Message Set (MMS) message that is applicable for this Subsystem is used by the Subsystem and is documented in the Service Contract; inspection results are recorded in the [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000064 (-1)_1: The “Tier 1 MMS Compliant” column of the [[OMS Msgs]] tab shows that the Subsystem uses each applicable message from the Tier 1 MMS.</p>
<p>STD-000064 (-1)_2: The entry for each Tier 1 MMS Message marked “Not Applicable” or “N/A” in the “Used” column of the [[OMS Msgs]] tab includes the rationale for the Subsystem not implementing the message.</p>
<p>STD-000064 (-1)_3: A Change Request documenting each modified OMS message identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000064 (-1)_4: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>If the Subsystem does not implement a capability that is represented by a message in the MMS, then the Subsystem does not have to implement that message.</p>
<p>For example, if an optical Subsystem does not support publishing tracks, then it would not implement the Entity message.</p>
<p>Any used message from the Tier 1 MMS marked “YES WITH MODIFICATION” and missing Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006935 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-006935 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem for each data transfer that crosses the Subsystem boundary; the data type per column A and the data format per column B is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006935 (-1)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab shows that the data format in column B corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-006935 (-1)_2: Each data transfer using a data type/data format combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006935 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006935 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006935 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-006935 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Subsystem boundary; the data type per column A and the data format per column B are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-006935 (-2)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that the data format in column B corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006935 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding data formats in column B of the “Data Transfer Formats, APIs, and Protocols” table for data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-006935 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type/data format combination listed in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006935 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006935 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006935 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Subsystem is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006936 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-006936 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem for each data transfer that crosses the Subsystem boundary; the data type per column A and the protocol/API per column C is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006936 (-1)_1: If, for each data transfer crossing the subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that the protocol/API in column C corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-006936 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006936 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006936 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006936 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-006936 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Subsystem boundary; the data type per column A and the protocols/APIs per column C are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-006936 (-2)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that protocol/API in column C corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006936 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column C of the “Data Transfer Formats, APIs, and Protocols” table for exclusive use data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-006936 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006936 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006936 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006936 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Subsystem is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-010123 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-010123 (-1): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Subsystem boundary; the data type per column A and the protocol/API per column D are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-010123 (-1)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that the protocol/API in column D corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-010123 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-010123 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-010123 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Service Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-010123 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-010123 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Subsystem boundary; the data type per column A and the protocols/APIs per column D are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-010123 (-2)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that protocol/API in column D corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-010123 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column D of the “Data Transfer Formats, APIs, and Protocols” table for shared read-only data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-010123 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-010123 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-010123 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-010123 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006937 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-006937 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem for each data transfer that crosses the Subsystem boundary; the data type per column A and the protocol/API per column E is identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006937 (-1)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that the protocol/API in column E corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table, including conforming to specified restrictions, then this VR is satisfied.</p>
<p>STD-006937 (-1)_2: Each data transfer using a data type/protocol or API combination that is not listed in the “Data Transfer Formats, APIs, and Protocols” table, but is covered by the “Non-OMS Data Transfers” table, is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006937 (-1)_3: A description of the data format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006937 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] tab explaining why the data transfer could not be implemented using a permitted combination per the “Data Transfer Formats, APIs, and Protocols” table.</p></td>
<td><p>Data transfers that use one of the permitted combinations per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted combinations are recorded in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist.</p>
<p>If the protocols, APIs, and/or formats listed in the “Data Transfer Formats, APIs, and Protocols” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary protocol, data format, or API that is not represented in the “Data Transfer Formats, APIs, and Protocols” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p>
<p>The following restrictions apply for all OMS Data Transfer combinations: 1) does not overlap with OMS Messages, 2) does not overlap with any other OMS Data Exchanges, and 3) does not transfer external standards second hand.</p>
<p>Non-OMS Data Transfers are typically restricted to OMS compliance Tier 1. However, when an OACWG-approved Change Request is identified, then the Non-OMS Data Transfer will be assessed at the maximum allowed Tier specified by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006937 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-006937 (-2): This requirement is verified by inspection of the Service Contract documentation for each data transfer that crosses the Subsystem boundary; the data type per column A and the protocol/API per column E are identified for each data transfer and compared to the permitted combinations listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-006937 (-2)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that protocol/API per column E corresponds to the data type per column A as listed in the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3, then this VR is satisfied.</td>
<td>Data transfers that use one of the permitted combinations for Max Assessed Tier of 3 per the “Data Transfer Formats, APIs, and Protocols” table are recorded in the [[OMS Data Transfer]] tab.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006937 [For each data type identified in column A of the “Data Transfer Formats, APIs, and Protocols” table, a Tier 1 OMS Subsystem shall select from the corresponding protocols/APIs in column E of the “Data Transfer Formats, APIs, and Protocols” table for shared read/modify data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-006937 (-3): This requirement is verified by inspection of the Change Request documentation which adds each data type and protocol/API combination listed in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006937 (-3)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006937 (-3)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and adding the required changes to the “Data Transfer Formats, APIs, and Protocols” table where the Max Assessed Tier value in column F is 3 has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006937 (-3)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to:</p>
<p>1. Add a format, protocol, or API, or</p>
<p>2. Use an existing OMS format, protocol, or API to transfer a type of data not covered by the “Data Transfer Formats, APIs, and Protocols” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any data transfer formats, protocols, and APIs proposed to be changed/added/deleted</p>
<p>2. Red-lined versions of all Standard documentation affected by the change</p>
<p>3. Test plan that shows testing or use of these data transfer formats and any progress should be included</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Subsystem is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006938 [A Tier 1 OMS Subsystem shall use the URI formats, as specified in the “OMS URI Formats” table, for its data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-006938 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem for each data transfer that crosses the Subsystem boundary; the URI format is identified for each data transfer and compared to the permitted formats listed in the “OMS URI Formats” table; the inspection results are recorded in the appropriate tabs of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006938 (-1)_1: If, for each data transfer crossing the Subsystem boundary, the [[OMS Data Transfer]] tab of the Subsystem Checklist shows that the Subsystem uses the URI formats specified in the “OMS URI Formats” table, then this VR is satisfied.</p>
<p>STD-006938 (-1)_2: Each data transfer using a URI format that is not specified in the “OMS URI Formats” table is identified in the [[Non-OMS Data Transfer]] tab.</p>
<p>STD-006938 (-1)_3: A description of the URI format is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] Tab.</p>
<p>STD-006938 (-1)_4: A rationale is provided for each Non-OMS Data Transfer listed in the [[Non-OMS Data Transfer]] Tab explaining why the data transfer could not be implemented using a URI format specified in the “OMS URI Formats” table.</p></td>
<td><p>Data transfers that use one of the URI formats per the “OMS URI Formats” table are recorded in the [[OMS Data Transfer]] tab; data transfers not using one of the permitted URI formats are recorded in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist.</p>
<p>If the URI formats listed in the “OMS URI Formats” table are not sufficient, an explanation as to why that is so should be captured in the “Data Transfer” section of the Service Contract.</p>
<p>Details of any non-proprietary URI format that is not represented in the “OMS URI Formats” table should be fully documented (or provide corresponding reference(s)) in the “Data Transfer” section of the Service Contract.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006938 [A Tier 1 OMS Subsystem shall use the URI formats, as specified in the “OMS URI Formats” table, for its data transfers that cross the Subsystem boundary.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-006938 (-2): This requirement is verified by inspection of the Change Request documentation which adds each URI format listed in the [[Non-OMS Data Transfer]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-006938 (-2)_1: If there are no Non-OMS Data Transfers listed in the [[Non-OMS Data Transfer]] tab, then this VR is satisfied.</p>
<p>STD-006938 (-2)_2: A Change Request documenting each Non-OMS Data Transfer identified in the [[Non-OMS Data Transfer]] tab and the required changes to the “OMS URI Formats” table to add the URI formats to the OMS Standard has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-006938 (-2)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Data Transfer]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request is required to add a URI format not listed in the “OMS URI Formats” table.</p>
<p>This Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any URI formats proposed to be changed/added/deleted</p>
<p>2. Red-lined versions of all Standard documentation affected by the change</p>
<p>3. Test plan that shows testing or use of these Data Transfer formats and any progress should be included</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Subsystem is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-010007 [When required, a Tier 1 OMS Subsystem shall use applicable lower fidelity position information using the specified OMS Message at one of the nominal rates specified in the “Position Information” section.]</td>
<td><p>In the context of this standard the term “applicable” means if the Subsystem requires low fidelity position information to perform its functions.</p>
<p>In the context of this requirement the term “use” means to receive position information.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-010007 (-1): If low fidelity position information is applicable, this requirement is verified by inspection of the Service Contract for the Subsystem showing that the Subsystem subscribes to the <strong>PositionReport</strong> message.</td>
<td><p>STD-010007 (-1)_1: If the Subsystem does not require position information, then this VR is satisfied.</p>
<p>STD-010007 (-1)_2: If the Subsystem requires the lower fidelity position information, the Service Contract documents the <strong>PositionReport</strong> message as an input.</p></td>
<td><p>This VR verified the applicable requirements for lower fidelity position information.</p>
<p>If the Subsystem requires low fidelity position data, the Service Contract for the Subsystem should include the <strong>PositionReport</strong> message as an input for one or more of the Subsystem functions.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-010008 [When required, a Tier 1 OMS Subsystem shall use applicable high fidelity position information using the specified OMS Message and Quality of Service (QoS) settings at one or more of the nominal rates as specified in the “Position Information” section.]</td>
<td><p>In the context of this standard the term “applicable” means if the Subsystem requires high fidelity position information to perform its functions.</p>
<p>In the context of this requirement the term “use” means to receive position information.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-010008 (-1): If high fidelity position information is applicable, this requirement is verified by inspection of the Service Contract for the Subsystem showing that the Subsystem subscribes to the <strong>PositionReportDetailed</strong> message.</td>
<td><p>STD-010008 (-1)_1: If the Subsystem does not require high fidelity position information, then this VR is satisfied.</p>
<p>STD-010008 (-1)_2: If the Subsystem requires higher fidelity position information, the Service Contract documents the <strong>PositionReportDetailed</strong> message as an input.</p></td>
<td><p>This VR verified the applicable requirements for high fidelity position information.</p>
<p>If the Subsystem requires high fidelity position data, the Service Contract for the Subsystem should include the <strong>PositionReportDetailed</strong> message as an input for one or more of the Subsystem functions.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-008667 [A Tier 1 OMS Subsystem shall accomplish time synchronization using an industry standard protocol identified in the “Approved Time Synchronization Protocols” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-008667 (-1): This requirement is verified by inspection of the Subsystem Description Document (SDD) showing that time synchronization for the Subsystem in accordance with the protocols identified in the “Approved Time Synchronization Protocols” table.</td>
<td>STD-008667 (-1)_1: The SDD documents the presence of the protocol(s) in accordance with the “Approved Time Synchronization Protocols” table.</td>
<td>This information is typically provided in the “Subsystem Time Synchronization” section of the Subsystem Description Document.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-008668 [When required, a Tier 1 OMS Subsystem shall accomplish high fidelity time synchronization using an industry standard protocol identified in the “High Fidelity Time Synchronization Mechanisms” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-008668 (-1): If high fidelity time synchronization is needed by the Subsystem, this requirement is verified by inspection of the Subsystem Description Document (SDD) showing that high fidelity time synchronization for the Subsystem is in accordance with the protocols identified in the “High Fidelity Time Synchronization Mechanisms” table.</td>
<td><p>STD-008668 (-1)_1: If the Subsystem does not require high fidelity time synchronization, then this requirement is satisfied.</p>
<p>STD-008668 (-1)_2: The SDD documents the presence of the protocol(s) in accordance with the “High Fidelity Time Synchronization Mechanisms” table.</p></td>
<td>This information is typically provided in the “Subsystem Time Synchronization” section of the Subsystem Description Document.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006944 [A Tier 1 OMS Subsystem shall report status in accordance with the “Subsystem Status” section of the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-006944 (-1): This requirement is verified by inspection of the delivered Service Contract for the Subsystem that shows the status reporting is documented in accordance with the “Subsystem Status” section of the Service Contract Template, OMSC-TMP-003</td>
<td>STD-006944 (-1)_1: The delivered Service Contract documents the status reporting behavior in accordance with the “Subsystem Status” section of the Service Contract template. A comparison of the delivered Service Contract to the template shows no significant differences.</td>
<td>This information is typically provided in the “Subsystem Status” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-006944 [A Tier 1 OMS Subsystem shall report status in accordance with the “Subsystem Status” section of the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-006944 (-2): This requirement is verified by inspection of functional test results for the Subsystem showing that the Status messages are published in accordance with the required behavior as documented in the Service Contract.</td>
<td><p>STD-006944 (-2)_1: The functional test results for the Subsystem show that the <strong>SubsystemStatus</strong> message is published by the Subsystem.</p>
<p>STD-006944 (-2)_2: The functional test results for the Subsystem show that the Subsystem sends the <strong>SubsystemStatusDataRequestStatus</strong> message in response to the <strong>SubsystemStatusDataRequest</strong> message.</p></td>
<td>This information is typically provided in the “Subsystem Status” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-008669 [A Tier 1 OMS Subsystem shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-008669 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the status reporting is configurable.</td>
<td>STD-008669 (-1)_1: The Service Contract documents that the parameters for reporting status are configurable.</td>
<td></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-008669 [A Tier 1 OMS Subsystem shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD 008669 (-2): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the mechanism used to configure status reporting is documented.</td>
<td>STD-008669 (-2)_1: The Service Contract documents the mechanism used to configure status reporting.</td>
<td></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-008669 [A Tier 1 OMS Subsystem shall implement configurable periodicity for reporting status.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-008669 (-3): This requirement is verified by inspection of the functional test results that show the status reporting can be configured for the Subsystem and that the Subsystem reports status in accordance with the configuration setting.</td>
<td><p>STD-008669 (-3)_1: The functional test results for the Subsystem show that the periodicity of status reporting can be configured.</p>
<p>STD 008669 (-3)_2: The functional test results for the Subsystem show that the Subsystem reports status in accordance with the configuration setting.</p></td>
<td></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-008670 [A Tier 1 OMS Subsystem shall implement a configurable range for periodic update rate from 1 to 600 seconds in 1 second increments.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-008670 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that the parameters for status reporting are configurable with an acceptable range of 1 to 600 seconds in 1 second increments.</td>
<td>STD-008670 (-1)_1: The Service Contract documents that the configuration parameters for status reporting support the range of 1 to 600 seconds in 1 second increments</td>
<td>This information is typically provided in the “Subsystem Status” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000414 [A Tier 1 OMS Subsystem shall have an <strong>OPERATE</strong> state.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000414 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that Subsystem has an <strong>OPERATE</strong> state.</td>
<td>STD-000414 (-1)_1: The Service Contract documents that the Subsystem has an <strong>OPERATE</strong> state as described in the “OMS Subsystem State Definitions and Allowed Transitions” table.</td>
<td><p>The <strong>OPERATE</strong> state is defined in the “OMS Subsystem State Definitions and Allowed Transitions” table.</p>
<p>This information is typically provided in the “Allowed States and Transitions” section of the Service Contract.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000415 [A Tier 1 OMS Subsystem shall use applicable state transitions defined in the “Allowed State Transitions for OMS Subsystem” figure.]</td>
<td>In the context of this requirement the term “applicable” means those state transitions that are required or used by the Subsystem.</td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000415 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem that shows the state transitions of the Subsystem are in accordance with the “Allowed State Transitions for OMS Subsystem” figure in the OMS Standard.</td>
<td>STD-000415 (-1)_1: The Service Contract documents that the Subsystem enters and exits each state only through permissible state transitions as identified in the “Allowed State Transitions for OMS Subsystem” figure.</td>
<td>This information is typically provided in a state diagram for the Subsystem included in the “Allowed States and Transitions” section of the Service Contract.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-000416 [A Tier 1 OMS Subsystem shall use applicable state transition triggers defined in the “OMS Subsystem State Definitions and Allowed Transitions” table.]</td>
<td>In the context of this requirement the term “applicable” means those state transitions triggers that are required or used by the Subsystem.</td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD 000416 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem that shows the state transition triggers for the Subsystem are in accordance with the “OMS Subsystem State Definitions and Allowed Transitions” table in the OMS Standard.</td>
<td>STD-000416 (-1)_1: The Service Contract documents that the Subsystem uses the permissible state transition triggers as identified in the “OMS Subsystem State Definitions and Allowed Transitions” table.</td>
<td>This information is typically provided in a state diagram for the Subsystem included in the “Allowed States and Transitions” section of the Service Contract.</td>
</tr>
<tr class="even">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-010179 [A Tier 1 OMS Subsystem shall document its cybersecurity posture in accordance with the “Cybersecurity Posture” section in the OMS Subsystem Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-010179 (-1): This requirement is verified by inspection of the Subsystem Description Document (SDD) “Cybersecurity Posture” section showing that the Subsystem hardware-related cybersecurity posture is documented.</td>
<td><p>STD-010179 (-1)_1: If there is no program-assigned hardware-related Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-010179 (-1)_2: The Subsystem hardware-related cybersecurity posture is documented in the SDD “Cybersecurity Posture” section.</p></td>
<td><p>The cybersecurity posture as defined by the CSRC and described by the CSAs denotes what an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The “Cybersecurity Posture” section describes the implementation of the cybersecurity posture by the Subsystem and provides additional, unclassified, and/or non-proprietary details relating to the security of Subsystem.</p>
<p>The provided OMSC-GDE-003, Cybersecurity Guide, defines the concepts, guidance, and information that OMS Adopting Programs and system designers will utilize to document the cybersecurity posture.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 1 Requirements</td>
<td>RQMT STD-009710 [A Tier 1 OMS Subsystem shall document its cybersecurity posture in accordance with the “Cybersecurity Posture” section in the OMS Service Contract Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-009710 (-1): This requirement is verified by inspection of the Service Contract “Cybersecurity Posture” section showing that the Subsystem software-related cybersecurity posture is documented.</td>
<td><p>STD-009710 (-1)_1: If there is no program-assigned software-related Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-009710 (-1)_2: The Subsystem software-related cybersecurity posture is documented in the Service Contract “Cybersecurity Posture” section.</p></td>
<td><p>The Cybersecurity posture as characterized by the CSRC denotes the “what” an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The “Cybersecurity Posture” section describes the implementation of the cybersecurity posture by the Subsystem and provides additional, unclassified, and/or non-proprietary details relating to the security of Subsystem.</p>
<p>The provided OMSC-GDE-003, Cybersecurity Guide, defines the concepts, guidance, and information that OMS Adopting Programs and system designers will utilize to document the cybersecurity posture.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 2 Requirements</td>
<td>RQMT STD-000069 [A Tier 2 OMS Subsystem shall meet Tier 1 Subsystem requirements.]</td>
<td></td>
<td><p>STD-000059</p>
<p>STD-000060</p>
<p>STD-000061</p>
<p>STD-000063</p>
<p>STD-000064</p>
<p>STD-000414</p>
<p>STD-000415</p>
<p>STD-000416</p>
<p>STD-006935</p>
<p>STD-006936</p>
<p>STD-006937</p>
<p>STD-006938</p>
<p>STD-006944</p>
<p>STD-008667</p>
<p>STD-008668</p>
<p>STD-008669</p>
<p>STD-008670</p>
<p>STD-009710</p>
<p>STD-010007</p>
<p>STD-010008</p>
<p>STD-010123</p>
<p>STD-010179</p></td>
<td>2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000069 (-1): This requirement is verified by the inspection of the [[Subsystem RQMT Checklist]] tab of the Subsystem Checklist, OMSC-CHK-004, that shows the subordinate requirements for RQMT STD-000069 have been met</td>
<td>STD-000069 (-1)_1: The [[Subsystem RQMT Checklist]] tab of the Subsystem Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000069 have been met.</td>
<td>Tier 2 OMS Subsystems must meet all Tier 1 OMS Subsystem requirements.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 2 Requirements</td>
<td>RQMT STD-000070 [A Tier 2 OMS Subsystem shall use the applicable Tier 2 Minimum Message Set messages.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the Tier 2 MMS that have similar content to messages the Subsystem implements.</td>
<td></td>
<td>2, 3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000070 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each Tier 2 Minimum Message Set (MMS) message that is applicable for this Subsystem is used by the Subsystem and is documented in the Service Contract; inspection results are recorded in the [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000070 (-1)_1: The “Tier 2 MMS Compliant” column of the [[OMS Msgs]] tab shows that the Subsystem uses each applicable message from the Tier 2 MMS.</p>
<p>STD-000070 (-1)_2: The entry for each Tier 2 MMS Message marked “Not Applicable” or “N/A” in the “Used” column of the [[OMS Msgs]] tab includes the rationale for the Subsystem not implementing the message.</p>
<p>STD-000070 (-1)_3: A Change Request documenting each modified OMS message identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000070 (-1)_4: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>If a Subsystem does not implement a capability that is represented by a message in the MMS, then it does not have to implement that message.</p>
<p>For example, if an optical Subsystem does not support publishing approval authority data, then it would not implement the OMS <strong>ApprovalAuthority</strong> message from the Tier 2 MMS.</p>
<p>Any used message from the Tier 1 MMS marked “YES WITH MODIFICATION” and missing Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 3 Requirements</td>
<td>RQMT STD-000072 [A Tier 3 OMS Subsystem shall meet Tier 2 Subsystem requirements.]</td>
<td></td>
<td><p>STD-000069</p>
<p>STD-000070</p></td>
<td>3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000072 (-1): This requirement is verified by the inspection of the [[Subsystem RQMT Checklist]] tab of the Subsystem Checklist, OMSC-CHK-004, that shows the subordinate requirements for RQMT STD-000072 have been met.</td>
<td>STD-000072 (-1)_1: The [[Subsystem RQMT Checklist]] tab of the Subsystem Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000072 have been met.</td>
<td>Tier 3 OMS Subsystems must meet all Tier 1 and Tier 2 OMS Subsystem requirements.</td>
</tr>
<tr class="odd">
<td>Subsystem Tier 3 Requirements</td>
<td>RQMT STD-000073 [A Tier 3 OMS Subsystem shall use applicable OMS Special Signals as listed in the “Special Signals” section.]</td>
<td><p>In the context of this requirement the term “applicable” means that any special signals used by the Subsystem are implemented in accordance with the “Special Signals” section.</p>
<p>A Subsystem is not required to implement any special signals if they are not applicable; a Subsystem can be OMS compliant without implementing any special signals.</p></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000073 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each special signal implemented by the Subsystem is in accordance with the “Special Signals” section; OMS Special Signals are documented in the [[OMS Special Signals]] tab, and non-OMS special signals are documented in the [[Non-OMS Special Signals]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000073 (-1)_1: If the Subsystem does not implement any special signals, then this VR is satisfied.</p>
<p>STD-000073 (-1)_2: The [[OMS Special Signals]] tab and the [[Non-OMS Special Signals]] tab of the Subsystem Checklist have been completed and document each special signal implemented by the Subsystem as described in the Service Contract.</p>
<p>STD-000073 (-1)_3: The [[OMS Special Signals]] tab shows that each OMS Special Signal implemented by the Subsystem is in accordance with the appropriate table in the OMS Standard; i.e., the “OMS Discrete and Voltage Reference Signals” table, or the “OMS Discrete and Voltage Time Reference Signals” table, or the “Other Signals Defined within OMS” table.</p>
<p>STD-000073 (-1)_4: Each non-OMS special signal implemented by the Subsystem that is listed in the “Non-OMS Special Signals Allowed in the OMS Standard” table is identified in the top section of the [[Non-OMS Special Signals]] tab. Note that OMS compliance assessment will be restricted to no more than Tier 2.</p>
<p>STD-000073 (-1)_5: Each non-OMS special signal implemented by the Subsystem that is listed in the “Non-OMS Special Signals Superseded by OMS Messages” table is identified in the middle section of the [[Non-OMS Special Signals]] tab. Note that OMS compliance assessment will be restricted to no more than Tier 2.</p>
<p>STD-000073 (-1)_6: Each non-OMS special signal implemented by the Service that is not listed in the “Non-OMS Special Signals Superseded by OMS Messages” table is identified in the bottom section of the [[Non-OMS Special Signals ]] tab Note that there must be an OACWG-approved Change Request Identifier listed in order to be OMS compliant.</p></td>
<td><p>This information is typically provided in the “Special Signals” section of the Service Contract.</p>
<p>The “Non-OMS Special Signals Allowed in the OMS Standard” table identifies the special signals considered outside the bounds of OMS standardization. However, these signals are allowed but OMS compliance assessment will be restricted to no more than Tier 2.</p>
<p>However, special signals that have been replaced by OMS Messages are identified in the “Non-OMS Special Signals Superseded by OMS Messages” table, and in these cases, the OMS Message should be used in place of the special signal for the Subsystem to be OMS compliant at Tier 3.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 3 Requirements</td>
<td>RQMT STD-000073 [A Tier 3 OMS Subsystem shall use applicable OMS Special Signals as listed in the “Special Signals” section.]</td>
<td><p>In the context of this requirement the term “applicable” means that any special signals used by the Subsystem are implemented in accordance with the “Special Signals” section.</p>
<p>A Subsystem is not required to implement any special signals if they are not applicable; a Subsystem can be OMS compliant without implementing any special signals.</p></td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-000073 (-2): This requirement is verified by inspection of the Change Request documentation which adds any non-OMS special signals documented in the [[Non-OMS Special Signals]] tab of the Subsystem Checklist, OMSC-CHK-005 that are not listed in the “Non-OMS Special Signals Superseded by OMS Messages” table.</td>
<td><p>STD-000073 (-2)_1: If the [[Non-OMS Special Signals]] tab shows that there are no non-OMS special signals implemented by the Subsystem, or that the only non-OMS special signals implemented by the Subsystem are listed in the “Other Non-OMS Special Signal” table, then this VR is satisfied.</p>
<p>STD-000073 (-2)_2: A Change Request documenting each non-OMS special signal identified in the [[Non-OMS Special Signals]] tab that is listed in the “Other Non-OMS Special Signal” table has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000073 (-2)_3: The Change Request ID of the Change Request has been documented in the [[Non-OMS Special Signals]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request to add a non-OMS special signal will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of any special signals proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these special signals and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Subsystem is using the Change Request update as approved by the OACWG.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 3 Requirements</td>
<td>RQMT STD-000074 [A Tier 3 OMS Subsystem shall use the applicable messages in the OMS Message Set.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the OMS Standard, that have similar content to messages the Subsystem implements.</td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-1</td>
<td>STD-000074 (-1): This requirement is verified by inspection of the Service Contract for the Subsystem showing that each OMS Message that is applicable for this Subsystem is used by the Subsystem and is documented in the Service Contract; inspection results are recorded in the [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td>STD-000074 (-1)_1: Each message crossing the Subsystem boundary and documented in the Service Contract is listed in the [[OMS Msgs]] tab of the Subsystem Checklist.</td>
<td><p>If a Subsystem does not support a message in the OMS Standard, then it does not have to implement that message.</p>
<p>However if, for example, a Subsystem takes as an input, messages containing weather information, then the appropriate OMS weather message would be applicable.</p>
<p>At Tier 3, an OMS Subsystem is required to implement each applicable OMS Message from the Tier 1 Required Subsystem Message Set and the Tier 1 and Tier 2 Minimum Message Sets.</p>
<p>Any additional messages used by a Tier 3 OMS Subsystem are required to be OMS Messages or are required to be submitted in a Change Request and approved by the OACWG.</p></td>
</tr>
<tr class="even">
<td>Subsystem Tier 3 Requirements</td>
<td>RQMT STD-000074 [A Tier 3 OMS Subsystem shall use the applicable messages in the OMS Message Set.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the OMS Standard, that have similar content to messages the Subsystem implements.</td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-2</td>
<td>STD-000074 (-2): This requirement is verified by inspection of the Change Request documentation which adds any new OMS messages documented in the [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000074 (-2)_1: If the [[OMS Msgs]] tab of the Subsystem Checklist shows there are no new OMS messages used by the Subsystem; then this VR is satisfied.</p>
<p>STD-000074 (-2)_2: A Change Request documenting each new OMS message identified in the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000074 (-2)_3: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of the updated OMS Message Schema proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these messages and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Subsystem is using the messages approved by the OACWG for the Change Request and using the CAL for passing the messages.</p>
<p>Any new message used without a Change Request identified will cause this requirement to not be met.</p></td>
</tr>
<tr class="odd">
<td>Subsystem Tier 3 Requirements</td>
<td>RQMT STD-000074 [A Tier 3 OMS Subsystem shall use the applicable messages in the OMS Message Set.]</td>
<td>In the context of this requirement, the term “applicable” means those messages in the OMS Standard, that have similar content to messages the Subsystem implements.</td>
<td></td>
<td>3</td>
<td>Subsystem</td>
<td>-3</td>
<td>STD-000074 (-3): This requirement is verified by inspection of the Change Request documentation which adds any modified OMS messages documented in the [[OMS Msgs]] tab of the Subsystem Checklist, OMSC-CHK-004.</td>
<td><p>STD-000074 (-3)_1: If the Subsystem Checklist shows there are no modified OMS messages identified with “YES WITH MODIFICATION” in the “Used” column in the [[OMS Msgs]] tab, then this VR is satisfied.</p>
<p>STD-000074 (-3)_2: A Change Request documenting each modified OMS message identified with “YES WITH MODIFICATION” in the “Used” column of the [[OMS Msgs]] tab has been submitted to and approved by the OACWG for the Change Request.</p>
<p>STD-000074(-3)_3: The Change Request ID of the Change Request has been documented in the [[OMS Msgs]] tab.</p></td>
<td><p>At Tier 3, submission of a Change Request will be considered part of compliance verification and validation.</p>
<p>The following artifacts should be reviewed as part of the Change Request during the OACWG change process:</p>
<p>1. Full definition of the updated OMS Message Schema proposed to be changed/added/deleted.</p>
<p>2. Red-lined versions of all Standard documentation affected by the change.</p>
<p>3. Test plan that shows testing or use of these messages and any progress should be included.</p>
<p>4. Response to any issues where this material is presented.</p>
<p>It is the expectation that the Service is using the messages approved by the OACWG for the Change Request and using the CAL for passing the messages.</p>
<p>Any used message marked “YES WITH MODIFICATION” and missing Change Request identification will cause this requirement to not be met.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000082 [A Tier 1 OMS Platform shall provide an OMS ASB.]</td>
<td></td>
<td><p>STD-000144</p>
<p>STD-000146</p>
<p>STD-009706</p></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000082 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-000082 have been met.</td>
<td>STD-000082 (-1)_1: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000082 have been met.</td>
<td></td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000083 [A Tier 1 OMS Platform shall provide an OMS OCE.]</td>
<td></td>
<td><p>STD-000350</p>
<p>STD-000351</p>
<p>STD-000352</p>
<p>STD-000354</p>
<p>STD-000355</p>
<p>STD-000360</p>
<p>STD-000362</p>
<p>STD-000365</p>
<p>STD-008663</p></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000083 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-000083 have been met.</td>
<td>STD-000083 (-1)_1: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000083 have been met.</td>
<td><p>A Platform provides an OCE for a Mission Package. The Mission Package Description Document (MPDD) identifies the Platform and any Subsystem(s) providing OCE implementation(s) in the Mission Package.</p>
<p>An OCE will provide a Java implementation if it is not against system security policy.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000085 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the PDD is complete and complies with the current version of the PDD Template, OMSC-TMP-001; inspection results are recorded in the [[PDD]] tab of the Platform Checklist, OMSC-CHK-003.</td>
<td>STD-000085 (-1)_1: The [[PDD]] tab of the Platform Checklist shows that the PDD is complete and complies with the current version of the PDD Template.</td>
<td>“Current Version” in this context refers to the version of the PDD Template specified in the OMS Standard against which compliance is being measured.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-2</td>
<td>STD-000085 (-2): This requirement is verified by inspection of the delivered Platform Description Document (PDD) showing that the document does not include proprietary labels; that the PDD includes a Platform Network diagram; and that the Security Information Exchanges implemented by the Platform are documented in the PDD.</td>
<td><p>STD-000085 (-2)_1: The delivered PDD has no proprietary labels applied to any of its pages.</p>
<p>STD-000085 (-2)_2: The “Network” section of the PDD contains a Platform network diagram that shows the network architecture implementation; including the physical connections, the interface speeds, and any network limitations.</p>
<p>STD-000085 (-2)_3: The PDD, or the PDD Security Addendum, documents the Security Information Exchanges implemented by the Platform.</p></td>
<td><p>Although the PDD may contain references to proprietary documentation, the PDD itself must be non-proprietary.</p>
<p>The “Security Addendum” section of the PDD identifies the unclassified and non-proprietary name of the Security Addendum document. The Security Addendum may be both classified and proprietary.</p>
<p>The Security Addendum describes the Security Information Exchanges implemented by the Platform and provides additional, classified, and/or proprietary details relating to the security of the Platform.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-3</td>
<td>STD-000085 (-3): This requirement is verified by inspection of the Platform Description Document (PDD) showing the ports and protocols the Platform can use for data transfer are documented.</td>
<td><p>STD-000085 (-3)_1: If no ports or protocols are used for data transfer, then this VR is satisfied.</p>
<p>STD-000085 (-3)_2: The PDD documents the ports and protocols used for data transfer.</p></td>
<td><p>The PDD should provide instructions on how to configure data transfer capabilities.</p>
<p>This information is documented in the “Ports &amp; Protocols” section of the PDD.</p></td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-4</td>
<td>STD-000085 (-4): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the mechanism for restricting the ports and protocols for data transfers is documented.</td>
<td><p>STD-000085 (-4)_1: If restricting ports or protocols for data transfers is not required, then this VR is satisfied.</p>
<p>STD-000085 (-4)_2: The PDD documents the mechanism for restricting the ports and protocols for data transfers.</p></td>
<td>This information is documented in the “Ports &amp; Protocols” section of the PDD.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-5</td>
<td>STD-000085 (-5): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the access control mechanism(s) the Platform can use for data storage are documented.</td>
<td><p>STD-000085 (-5)_1: If access control for data storage is not required, then this VR is satisfied.</p>
<p>STD-000085 (-5)_2: The PDD documents the access control mechanism(s) for data storage.</p></td>
<td>This information is documented in the “Data Storage Access Controls” section of the PDD.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-6</td>
<td>STD-000085 (-6): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the identification and authentication mechanism(s) the Platform can use for data transfer are documented.</td>
<td><p>STD-000085 (-6)_1: If identification and authentication for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000085 (-6)_2: The PDD documents the identification and authentication mechanism(s) for data transfer.</p></td>
<td>This information is typically provided in the “Data Transfer Configuration” section of the PDD.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-7</td>
<td>STD-000085 (-7): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the confidentiality mechanism(s) the Platform can use for data storage are documented.</td>
<td><p>STD-000085 (-7)_1: If confidentiality for data storage is not required, then this VR is satisfied.</p>
<p>STD-000085 (-7)_2: The PDD documents the confidentiality mechanism(s) for data storage.</p></td>
<td>This information is documented in the “Data Storage Confidentiality Mechanisms” section of the PDD.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-8</td>
<td>STD-000085 (-8): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the confidentiality mechanism(s) the Platform can use for data transfer are documented.</td>
<td><p>STD-000085 (-8)_1: If confidentiality for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000085 (-8)_2: The PDD documents the confidentiality mechanism(s) for data transfer.</p></td>
<td>This information is documented in the “Data Transfer Confidentiality Mechanisms” section of the PDD.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-9</td>
<td>STD-000085 (-9): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the integrity mechanism(s) the Platform can use for data storage are documented.</td>
<td><p>STD-000085 (-9)_1: If integrity for data storage is not required, then this VR is satisfied.</p>
<p>STD-000085 (-9)_2: The PDD documents the integrity mechanism(s) for data storage.</p></td>
<td>This information is documented in the “Data Storage Integrity Mechanisms” section of the PDD.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000085 [A Tier 1 OMS Platform shall be documented in a non-proprietary Platform Description Document in accordance with the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-10</td>
<td>STD-000085 (-10): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the integrity mechanism(s) the Platform can use for data transfer are documented.</td>
<td><p>STD-000085 (-10)_1: If integrity for data transfer is not required, then this VR is satisfied.</p>
<p>STD-000085 (-10)_2: The PDD documents the integrity mechanism(s) for data transfer.</p></td>
<td>This information is documented in the “Data Transfer Integrity Mechanisms” section of the PDD.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000086 [A Tier 1 OMS Platform shall provision for applicable OMS Special Signals as listed in the “Special Signals” section.]</td>
<td><p>In the context of this requirement, the term “provision” means that the current architecture and design will support these applicable signals at a future date without hardware modification.</p>
<p>In the context of this requirement the term “applicable” means those signals that an OMS Platform is required to support for future growth.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000086 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OMS Platform has provisioned for applicable Special Signals in accordance with the “OMS Discrete and Voltage Reference Signals” table, the “OMS Discrete and Voltage Time Reference Signals” table, and the “Other Signals Defined within OMS” table.</td>
<td><p>STD-000086 (-1)_1: If no special signals have been identified as “applicable” by the adopting program, then this VR is satisfied.</p>
<p>STD-000086 (-1)_2: The PDD identifies the means for the provisioning of the applicable Special Signals in accordance with the “OMS Discrete and Voltage Reference Signals” table, the “OMS Discrete and Voltage Time Reference Signals” table, and the “Other Signals Defined within OMS” table.</p></td>
<td><p>The intent is that the adopting program will identify the subset of Special Signals anticipated for future growth.</p>
<p>The tables listed in the VR are in the “Special Signals” section of the OMS Standard.</p>
<p>This information is documented in the “Special Signals” section of the PDD.</p></td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-005002 [A Tier 1 OMS Platform shall provide an Internet Protocol (IP) based network to support the allowed protocols identified in the “Data Transfer Formats, APIs, and Protocols” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-005002 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OMS Platform provides an IP based network.</td>
<td>STD-005002 (-1)_1: The PDD documents that the Platform implements either an IP based network, or an IP based stack on a non-IP network.</td>
<td><p>An IP based stack would satisfy this requirement. For example, an IP based stack on a non-IP network (such as switched fabric) would satisfy this requirement.</p>
<p>An adopting program would make the PDD available to those entities that need it.</p>
<p>This information is documented in the “Network” section of the PDD.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000303 [A Tier 1 OMS Platform shall provide the time reference for time synchronization across the ASB.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000303 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that time synchronization is implemented.</td>
<td>STD-000303 (-1)_1: The PDD identifies the presence of a time reference and documents the method(s) of time synchronization implemented by the Platform.</td>
<td><p>For this requirement, the accuracy and precision of time is not a concern.</p>
<p>This information is documented in the “Time Reference and Time Synchronization” section of the PDD.</p></td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000307 [A Tier 1 OMS Platform shall accomplish time synchronization using an industry standard protocol identified in the “Approved Time Synchronization Protocols” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000307 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the Platform implements time synchronization in accordance with one of the protocols identified in the “Approved Time Synchronization Protocols” table.</td>
<td>STD-000307 (-1)_1: The PDD documents that the Platform implements time synchronization in accordance with one of the protocols identified in the “Approved Time Synchronization Protocols” table.</td>
<td>The Platform should identify the time synchronization method(s) available.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000314 [When required, a Tier 1 OMS Platform shall accomplish high fidelity time synchronization using an industry standard protocol identified in the “High Fidelity Time Synchronization Mechanisms” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000314 (-1): If high fidelity time synchronization is provided by the OMS Platform, this requirement is verified by inspection of the Platform Description Document (PDD) showing that the Platform implements high fidelity time synchronization in accordance with one of the protocols identified in the “High Fidelity Time Synchronization Mechanisms” table.</td>
<td><p>STD-000314 (-1)_1: If high fidelity time synchronization is not provided, then this VR is satisfied.</p>
<p>STD-000314 (-1)_2: The PDD documents that the Platform implements high fidelity time synchronization in accordance with one of the protocols identified in the “High Fidelity Time Synchronization Mechanisms” table.</p></td>
<td>High fidelity time synchronization is an option for an OMS Platform. The Platform should identify the time synchronization method(s) available.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000325 [When required, a Tier 1 OMS Platform shall provide lower fidelity position information using the specified <strong>PositionReport</strong> message at one of the nominal rates specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000325 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) that identifies the Subsystem, Service, or Isolator that provides the <strong>PositionReport</strong> message for the Platform.</td>
<td><p>STD-000325 (-1)_1: If position information is not required, then this VR is satisfied.</p>
<p>STD-000325 (-1)_2: If the Platform provides the <strong>PositionReport</strong> directly (without using a Subsystem, Service, or Isolator), then this VR is satisfied.</p>
<p>STD-000325 (-1)_3: The PDD identifies the Subsystem, Service, or Isolator that provides the <strong>PositionReport</strong> message for the Platform.</p></td>
<td>This covers the case when a Subsystem, Service, or Isolator publishes the <strong>PositionReport</strong> message on behalf of the Platform. This information is documented in the “Position Information” section of the PDD.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000325 [When required, a Tier 1 OMS Platform shall provide lower fidelity position information using the specified <strong>PositionReport</strong> message at one of the nominal rates specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-2</td>
<td>STD-000325 (-2): This requirement is verified by inspection of the Service Contract for the Subsystem, Service, or Isolator that provides the <strong>PositionReport</strong> message for the Platform, showing that the <strong>PositionReport</strong> message is published at a nominal rate specified in the “Position Information” section.</td>
<td><p>STD-000325 (-2)_1: If position information is not required, then this VR is satisfied.</p>
<p>STD-000325 (-2)_2: If the Platform provides the <strong>PositionReport</strong> directly (without using a Subsystem, Service, or Isolator), then this VR is satisfied.</p>
<p>STD-000325 (-2)_3: The Service Contract documents that the <strong>PositionReport</strong> message is being published at a nominal rate specified in the “Position Information” section.</p></td>
<td>This covers the case when a Subsystem, Service, or Isolator publishes the <strong>PositionReport</strong> message on behalf of the Platform. The intent here is that no statistical analysis is required to verify the specified rate.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000325 [When required, a Tier 1 OMS Platform shall provide lower fidelity position information using the specified <strong>PositionReport</strong> message at one of the nominal rates specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-3</td>
<td>STD-000325 (-3): This requirement is verified by inspection of the Platform Description Document (PDD) that documents the <strong>PositionReport</strong> fields and characteristics provided by the Platform.</td>
<td><p>STD-000325 (-3)_1: If position information is not required, then this VR is satisfied.</p>
<p>STD-000325 (-3)_2: If position information is provided by a Subsystem, Service, or Isolator, then this VR is satisfied.</p>
<p>STD-000325 (-3)_3: The PDD documents the <strong>PositionReport</strong> fields and characteristics provided by the Platform in the “Position Information” section.</p></td>
<td>This covers the case when a Platform directly publishes the <strong>PositionReport</strong> message. This information is documented in the “Position Information” section of the PDD.</td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000325 [When required, a Tier 1 OMS Platform shall provide lower fidelity position information using the specified <strong>PositionReport</strong> message at one of the nominal rates specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-4</td>
<td>STD-000325 (-4): This requirement is verified by inspection of the PDD showing that the <strong>PositionReport</strong> message provided by the Platform is published at a nominal rate specified in the “Position Information” section.</td>
<td><p>STD-000325 (-4)_1: If position information is not required, then this VR is satisfied.</p>
<p>STD-000325 (-4)_2: If position information is provided by a Subsystem, Service, or Isolator, then this VR is satisfied.</p>
<p>STD-000325 (-4)_3: The PDD documents the <strong>PositionReport</strong> message provided by the Platform is being published at a nominal rate specified in the “Position Information” section.</p></td>
<td>This covers the case when a Platform directly publishes the <strong>PositionReport</strong> message. The intent here is that no statistical analysis is required to verify the specified rate.</td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000334 [When required, a Tier 1 OMS Platform shall provide high fidelity position information using the specified <strong>PositionReportDetailed</strong> message and Quality of Service (QoS) settings at one or more of the nominal publish rates as specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000334 (-1): If high fidelity position information is indirectly provided by the OMS Platform, then this requirement is verified by inspection of the Platform Description Document (PDD) that identifies the Subsystem, Service, or Isolator that provides the <strong>PositionReportDetailed</strong> message for the Platform.</td>
<td><p>STD-000334 (-1)_1: If high fidelity position information is not required, then this VR is satisfied.</p>
<p>STD-000334 (-1)_2: If high fidelity position information is directly provided by the Platform, this VR is satisfied.</p>
<p>STD-000334 (-1)_3: The PDD identifies the Subsystem, Service, or Isolator that produces the <strong>PositionReportDetailed</strong> message for the Platform.</p></td>
<td><p>This covers the case when a Subsystem, Service, or Isolator publishes the <strong>PositionReportDetailed</strong> message for the Platform.</p>
<p>High fidelity position information is an option for an OMS Platform.</p>
<p>The Platform should identify the navigation method(s) available.</p>
<p>This information is documented in the “Position Information” section of the PDD.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000334 [When required, a Tier 1 OMS Platform shall provide high fidelity position information using the specified <strong>PositionReportDetailed</strong> message and Quality of Service (QoS) settings at one or more of the nominal publish rates as specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-2</td>
<td>STD-000334 (-2): If high fidelity position information is indirectly provided by the OMS Platform, then this requirement is verified by inspection of the Service Contract for the Subsystem, Service, or Isolator that provides the <strong>PositionReportDetailed</strong> message for the Platform. Inspection must show that the <strong>PositionReportDetailed</strong> message is published at one or more of the nominal publish rates and Quality of Service (QoS) settings as specified in the “Position Information” section.</td>
<td><p>STD-000334 (-2)_1: If high fidelity position information is not required, then this VR is satisfied.</p>
<p>STD-000334 (-2)_2: If high fidelity position information is directly provided by the Platform, this VR is satisfied.</p>
<p>STD-000334 (-2)_3: The Service Contract documents that the <strong>PositionReportDetailed</strong> message is being published at one or more of the nominal publish rates and Quality of Service (QoS) settings as specified in the “Position Information” section.</p></td>
<td><p>This covers the case when a Subsystem, Service, or Isolator publishes the <strong>PositionReportDetailed</strong> message for the Platform.</p>
<p>High fidelity position information is an option for an OMS Platform.</p>
<p>The intent here is that no statistical analysis is required to verify the specified rates.</p></td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000334 [When required, a Tier 1 OMS Platform shall provide high fidelity position information using the specified <strong>PositionReportDetailed</strong> message and Quality of Service (QoS) settings at one or more of the nominal publish rates as specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-3</td>
<td>STD-000334 (-3): If high fidelity position information is directly provided by the OMS Platform, then this requirement is verified by inspection of the Platform Description Document (PDD) that documents the <strong>PositionReportDetailed</strong> fields and characteristics provided by the Platform.</td>
<td><p>STD-000334 (-3)_1: If high fidelity position information is not required, then this VR is satisfied.</p>
<p>STD-000334 (-3)_2: If high fidelity position information is provided by a Subsystem, Service, or Isolator, then this VR is satisfied.</p>
<p>STD-000334 (-3)_3: The PDD documents the <strong>PositionReportDetailed</strong> fields and characteristics provided by the Platform.</p></td>
<td><p>This covers the case when the Platform directly publishes the <strong>PositionReportDetailed</strong> message.</p>
<p>High fidelity position information is an option for an OMS Platform.</p>
<p>The system architecture should identify the navigation method(s) available.</p>
<p>This information is documented in the “Position Information” section of the PDD.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-000334 [When required, a Tier 1 OMS Platform shall provide high fidelity position information using the specified <strong>PositionReportDetailed</strong> message and Quality of Service (QoS) settings at one or more of the nominal publish rates as specified in the “Position Information” section.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-4</td>
<td>STD-000334 (-4): If high fidelity position information is directly provided by the OMS Platform, then this requirement is verified by inspection of the Platform Description Document (PDD) that the <strong>PositionReportDetailed</strong> message is published at one or more of the nominal publish rates and Quality of Service (QoS) settings as specified in the “Position Information” section.</td>
<td><p>STD-000334 (-4)_1: If high fidelity position information is not required, then this VR is satisfied.</p>
<p>STD-000334 (-4)_2: If high fidelity position information is provided by a Subsystem, Service, or Isolator, then this VR is satisfied.</p>
<p>STD-000334 (-4)_3: The PDD documents that the <strong>PositionReportDetailed</strong> message is being published at one or more of the nominal publish rates and Quality of Service (QoS) settings as specified in the “Position Information” section.</p></td>
<td><p>This covers the case when the Platform directly publishes the <strong>PositionReportDetailed</strong> message.</p>
<p>High fidelity position information is an option for an OMS Platform.</p>
<p>The intent here is that no statistical analysis is required to verify the specified rates.</p></td>
</tr>
<tr class="odd">
<td>Platform Tier 1 Requirements</td>
<td>RQMT STD-009712 [A Tier 1 OMS Platform shall document its cybersecurity posture in accordance with the “Cybersecurity Posture” section in the OMS Platform Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-009712 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) “Cybersecurity Posture” section showing that the Platform Cybersecurity posture is documented.</td>
<td><p>STD-009712 (-1)_1: If there is no program-assigned Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-009712 (-1)_2: The Platform cybersecurity posture is documented in the PDD “Cybersecurity Posture” section.</p></td>
<td><p>The cybersecurity posture as defined by the CSRC and described by the CSAs denotes what an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The “Cybersecurity Posture” section describes the implementation of the cybersecurity posture by the Platform and provides additional, unclassified, and/or non-proprietary details relating to the security of the Platform.</p>
<p>The provided OMSC-GDE-003, Cybersecurity Guide, defines the concepts, guidance, and information that OMS Adopting Programs and system designers will utilize to document the cybersecurity posture.</p></td>
</tr>
<tr class="even">
<td>Platform Tier 2 Requirements</td>
<td>RQMT STD-000088 [A Tier 2 OMS Platform shall meet Tier 1 Platform requirements.]</td>
<td></td>
<td><p>STD-000082</p>
<p>STD-000083</p>
<p>STD-000085</p>
<p>STD-000086</p>
<p>STD-000303</p>
<p>STD-000307</p>
<p>STD-000314</p>
<p>STD-000325</p>
<p>STD-000334</p>
<p>STD-005002</p>
<p>STD-009712</p></td>
<td>2, 3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000088 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-000088 have been met.</td>
<td>STD-000088 (-1)_1: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000088 have been met.</td>
<td>Tier 2 OMS Platforms must meet all Tier 1 Platform requirements.</td>
</tr>
<tr class="odd">
<td>Platform Tier 3 Requirements</td>
<td>RQMT STD-000095 [A Tier 3 OMS Platform shall meet Tier 2 Platform requirements.]</td>
<td></td>
<td>STD-000088</td>
<td>3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000095 (-1): This requirement is verified by the inspection of the [[Platform RQMT Checklist]] tab of the Platform Checklist, OMSC-CHK-003, that shows the subordinate requirements for RQMT STD-000095 have been met.</td>
<td>STD-000095 (-1)_1: The [[Platform RQMT Checklist]] tab of the Platform Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-000095 have been met.</td>
<td>Tier 3 OMS Platforms must meet all Tier 1 and Tier 2 Platform requirements.</td>
</tr>
<tr class="even">
<td>Platform Tier 3 Requirements</td>
<td>RQMT STD-000096 [A Tier 3 OMS Platform shall provide for applicable OMS Special Signals as listed in the “Special Signals” section.]</td>
<td>In the context of this requirement the term “applicable” means those signals that an OMS Platform is required to support.</td>
<td></td>
<td>3</td>
<td>Platform</td>
<td>-1</td>
<td>STD-000096 (-1): This requirement is verified by inspection of the Platform Description Document (PDD) showing that the OMS Platform has implemented the applicable special signals in accordance with the “OMS Discrete and Voltage Reference Signals” table, the “OMS Discrete and Voltage Time Reference Signals” table, and the “Other Signals Defined within OMS” table.</td>
<td><p>STD-000096 (-1)_1: If no special signals have been identified as “applicable” by the adopting program, then this VR is satisfied.</p>
<p>STD-000096 (-1)_2: The PDD identifies the means for the providing the applicable special signals in accordance with the “OMS Discrete and Voltage Reference Signals” table, the “OMS Discrete and Voltage Time Reference Signals” table, and the “Other Signals Defined within OMS” table.</p></td>
<td><p>The intent is that the adopting program will identify the subset of Special Signals anticipated for future growth.</p>
<p>The tables listed in the VR are in the “Special Signals” section of the OMS Standard.</p>
<p>This information is documented in the “Special Signals” section of the PDD.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-000101 [A Tier 1 OMS Mission Package shall provide an OMS Platform assessed to at least Tier 1 compliance.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000101 (-1): This requirement is verified by inspection of compliance artifacts showing that the OMS Mission Package includes an OMS Platform assessed to at least Tier 1 compliance.</td>
<td><p>STD-000101 (-1)_1: The MPDD documents that the OMS Mission Package includes an OMS Platform that is at least Tier 1 compliant.</p>
<p>STD-000101 (-1)_2: The OMS Platform listed in the MPDD has a Platform Checklist that indicates the Platform is assessed to at least Tier 1 compliance, which is recorded in the [[Tier Compliance]] tab of the Platform Checklist.</p></td>
<td>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-009208 [A Tier 1 OMS Mission Package shall contain only OMS Architecture Elements assessed to at least Tier 1 compliance.]</td>
<td>In this context, OMS Architecture Elements assessed for compliance in the Mission Package are defined as a Platform, Services, and Subsystems.</td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-009208 (-1): This requirement is verified by inspection of compliance artifacts showing that each Platform, Subsystem, and Service included in the OMS Mission Package is assessed to at least Tier 1 compliance.</td>
<td><p>STD-009208 (-1)_1: The MPDD documents that each OMS Architecture Element (Platform, Subsystem, and Service) included in the OMS Mission Package is at least Tier 1 compliant.</p>
<p>STD-009208 (-1)_2: Each OMS Architecture Element (Platform, Subsystem, and Service) listed in the MPDD has a corresponding checklist that indicates the OMS Architecture Element is assessed to at least Tier 1 compliance, which is recorded in the [[Tier Compliance]] tab of each checklist.</p></td>
<td><p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</p>
<p>An OMS Mission Package can only achieve an assessment Tier that is no higher than the lowest tier of the following assessed Architecture Elements in the Mission Package: Platform, Subsystems, and Services.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-000102 [A Tier 1 OMS Mission Package shall provide at least one applicable Tier 1 compliant Service Capability from the “Service Capability List for Compliance” section.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Services that are identified as an OMS Service in the Mission Package Worksheet for a program, that are described in the “Service Capability List for Compliance.”</p>
<p>If the Mission Package Worksheet for a program does not include any Services that are described in this list, then there are no “applicable” Services and the requirement is satisfied.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000102 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that the OMS Mission Package includes one or more Services, described in the “Service Capability List for Compliance,” that are at least Tier 1 compliant.</td>
<td><p>STD-000102 (-1)_1: If the adopting program does not require any Services that are described in the “Service Capability List for Compliance,” then this VR is satisfied.</p>
<p>STD-000102 (-1)_2: The MPDD documents that the OMS Mission Package includes at least one Service from the “Service Capability List for Compliance” that is at least Tier 1 compliant.</p></td>
<td><p>It is possible that a Tier 1 OMS Mission Package does not include any Services that are described in the “Service Capability List for Compliance.”</p>
<p>If the Mission Package Worksheet provided by the adopting program does not require any Services that are described in the “Service Capability List for Compliance,” then there are no “applicable” Services and the requirement is satisfied.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-000102 [A Tier 1 OMS Mission Package shall provide at least one applicable Tier 1 compliant Service Capability from the “Service Capability List for Compliance” section.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Services that are identified as an OMS Service in the Mission Package Worksheet for a program, that are described in the “Service Capability List for Compliance.”</p>
<p>If the Mission Package Worksheet for a program does not include any Services that are described in this list, then there are no “applicable” Services and the requirement is satisfied.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-2</td>
<td>STD-000102 (-2): If the Mission Package Worksheet per OMSC-TMP-006 from the adopting program requires additional or specific Service capabilities to be at least Tier 1 compliant, then this requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that each additional program-specified Service is at least Tier 1 compliant.</td>
<td><p>STD-000102 (-2)_1: If the adopting program does not require additional or specific Services to be Tier 1 compliant, then this VR is satisfied.</p>
<p>STD-000102 (-2)_2: The MPDD shows that each additional Service required by the program to be Tier 1 compliant is documented as being at least Tier 1 compliant.</p></td>
<td><p>An adopting program may require additional Services from the “Service Capability List for Compliance” to be Tier 1 compliant.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-000103 [A Tier 1 OMS Mission Package shall provide at least one applicable Tier 1 compliant Subsystem from the “Subsystem List for Compliance” section.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Subsystems that are identified as an OMS Subsystem in the Mission Package Worksheet for a program, that are described in the “Subsystem List for Compliance.”</p>
<p>If the Mission Package Worksheet for a program does not include any Subsystems that are described in this list, then there are no “applicable” Subsystems and the requirement is satisfied.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000103 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that the OMS Mission Package includes one or more Subsystems described in the “Subsystem List for Compliance” that are at least Tier 1 compliant.</td>
<td><p>STD-000103 (-1)_1: If the adopting program does not require any Subsystems described in the “Subsystem List for Compliance,” then this VR is satisfied.</p>
<p>STD-000103 (-1)_2: The MPDD documents that the OMS Mission Package includes at least one Subsystem from the “Subsystem List for Compliance” that is at least Tier 1 compliant.</p></td>
<td><p>It is possible that a Tier 1 OMS Mission Package does not include any Subsystems that are described in the “Subsystem List for Compliance.”</p>
<p>If the Mission Package Worksheet provided by the adopting program does not include any Subsystems that are described in the “Subsystem List for Compliance,” then there are no “applicable” Subsystems and the requirement is satisfied.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-000103 [A Tier 1 OMS Mission Package shall provide at least one applicable Tier 1 compliant Subsystem from the “Subsystem List for Compliance” section.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Subsystems that are identified as an OMS Subsystem in the Mission Package Worksheet for a program, that are described in the “Subsystem List for Compliance.”</p>
<p>If the Mission Package Worksheet for a program does not include any Subsystems that are described in this list, then there are no “applicable” Subsystems and the requirement is satisfied.</p></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-2</td>
<td>STD-000103 (-2): If the Mission Package Worksheet per OMSC-TMP-006 from the adopting program requires additional or specific Subsystems to be at least Tier 1 compliant, then this requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that each additional program-specified Subsystem is at least Tier 1 compliant.</td>
<td><p>STD-000103 (-2)_1: If the adopting program does not require additional or specific Subsystems to be Tier 1 compliant, then this VR is satisfied.</p>
<p>STD-000103 (-2)_2: The MPDD shows that each additional Subsystem required by the program to be Tier 1 compliant is documented as being at least Tier 1 compliant.</p></td>
<td><p>An adopting program may require additional Subsystems from the “Subsystem List for Compliance” to be Tier 1 compliant.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-000104 [A Tier 1 OMS Mission Package shall provide at least one Isolator if applicable.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000104 (-1): This requirement is verified by inspection of Mission Package Description Document (MPDD), showing that the OMS Mission Package includes one or more Isolators.</td>
<td><p>STD-000104 (-1)_1: If the Mission Package does not require isolation, then this VR is satisfied.</p>
<p>STD-000104 (-1)_2: The MPDD documents that the OMS Mission Package includes at least one Isolator.</p></td>
<td><p>Not all Mission Packages require isolation. Ground stations, Roll-on/Roll-off systems, ground stations, and lab configurations may not require isolation.</p>
<p>Isolation is required to enforce Safety of Flight, Nuclear, and other flight certifications.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-005004 [A Tier 1 OMS Mission Package shall provide NFS and/or FTP support for the allowed protocols identified in the “Data Transfer Formats, APIs, and Protocols” table.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-005004 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD), showing where the NFS and/or FTP servers are located within the OMS Mission Package.</td>
<td><p>STD-005004 (-1)_1: The MPDD documents the location of the NFS and/or FTP servers for the Mission Package.</p>
<p>STD-005004 (-1)_2: The MPDD identifies the PDD for the Platform or the SDD for the Subsystem that provides the NFS and/or FTP servers for the OMS Mission Package.</p></td>
<td><p>This requirement is allocated to the OMS Mission Package to allow for either the OMS Platform or an OMS Subsystem to provide the NFS and/or FTP servers.</p>
<p>The servers are then documented in the Platform Description Document (PDD) or the Subsystem Description Document (SDD) as appropriate.</p>
<p>The MPDD documents the location of the servers and cross references the applicable PDD or SDD.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-009924 [A Tier 1 OMS Mission Package shall document its Units of Replaceability in a non-proprietary Mission Package Worksheet in accordance with the OMS Mission Package Worksheet Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-009924 (-1): This requirement is verified by inspection of the Mission Package Worksheet (MPW) showing that the MPW is complete and complies with the current version of the MPW Template, OMSC-TMP-006, and that the delivered MPW does not include proprietary labels.</td>
<td><p>STD-009924 (-1)_1: The Mission Package Worksheet referenced in the MPDD is complete and complies with the current version of the MPW Template.</p>
<p>STD-009924 (-1)_2: The delivered MPW has no proprietary labels applied to any of its pages.</p></td>
<td><p>The MPW documents the contents of the Mission Package, including the Mission Package itself as well as every OMS Subsystem, OMS Service, and OMS Isolator in the Mission Package.</p>
<p>“Current Version” in this context refers to the version of the MPW Template specified in the OMS Standard against which compliance is being measured.</p>
<p>Although the MPW may contain references to proprietary documentation, the MPW itself must be non-proprietary.</p>
<p>The MPW documents CSRCs, which are typically assigned by the program. If the Mission Package does not have a program-assigned Cybersecurity requirement, “N/A” is a valid assignment in the CSRC field.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-008124 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the MPDD is complete and complies with the current version of the MPDD Template, OMSC-TMP-007 and that the delivered MPDD does not include proprietary labels; inspection results are recorded in the [[MPDD]] tab of the Mission Package Checklist, OMSC-CHK-002.</td>
<td><p>STD-008124 (-1)_1: The [[MPDD]] tab of the Mission Package Checklist shows that the MPDD is complete and complies with the current version of the MPDD Template.</p>
<p>STD-008124 (-1)_2: The delivered MPDD has no proprietary labels applied to any of its pages.</p></td>
<td><p>“Current Version” in this context refers to the version of the MPDD Template specified in the OMS Standard against which compliance is being measured.</p>
<p>Although the MPDD may contain references to proprietary documentation, the MPDD itself must be non-proprietary.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-2</td>
<td>STD-008124 (-2): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the access control implementation(s) for data transfer are documented.</td>
<td><p>STD-008124 (-2)_1: If access control for data transfer is not required, then this VR is satisfied.</p>
<p>STD-008124 (-2)_2: The MPDD documents the access control implementation(s) for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Access Controls” section of the MPDD.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-3</td>
<td>STD-008124 (-3): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the information flow control implementation(s) for data transfer are documented.</td>
<td><p>STD-008124 (-3)_1: If information flow control for data transfer is not required, then this VR is satisfied.</p>
<p>STD-008124 (-3)_2: The MPDD documents the information flow control implementation(s) for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Flow, Ports and Protocols Restriction Policy” section of the MPDD.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-4</td>
<td>STD-008124 (-4): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the ports and protocols used for data transfer are documented.</td>
<td><p>STD-008124 (-4)_1: If ports or protocols for data transfer are not required, then this VR is satisfied.</p>
<p>STD-008124 (-4)_2: The MPDD documents the ports and protocols used for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Flow, Ports and Protocols Restriction Policy” section of the MPDD.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-5</td>
<td>STD-008124 (-5): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that that the mechanism for restricting the ports and protocols for data transfer is documented.</td>
<td><p>STD-008124 (-5)_1: If restricting ports or protocols for data transfer is not required, then this VR is satisfied.</p>
<p>STD-008124 (-5)_2: The MPDD documents the mechanism for restricting the ports and protocols for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Flow, Ports and Protocols Restriction Policy” section of the MPDD.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-6</td>
<td>STD-008124 (-6): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the identification and authentication implementation(s) for data transfer are documented.</td>
<td><p>STD-008124 (-6)_1: If identification and authentication for data transfer is not required, then this VR is satisfied.</p>
<p>STD-008124 (-6)_2: The MPDD documents the identification and authentication implementation(s) for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Identification &amp; Authentication Implementation(s)” section of the MPDD.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-7</td>
<td>STD-008124 (-7): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the confidentiality implementation(s) for data transfer are documented.</td>
<td><p>STD-008124 (-7)_1: If confidentiality for data transfer is not required, then this VR is satisfied.</p>
<p>STD-008124 (-7)_2: The MPDD documents the confidentiality implementation(s) for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Confidentiality Implementation(s)” section of the MPDD.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-008124 [A Tier 1 OMS Mission Package shall be documented in a non-proprietary Mission Package Description Document in accordance with the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-8</td>
<td>STD-008124 (-8): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that the integrity implementation(s) for data transfer are documented.</td>
<td><p>STD-008124 (-8)_1: If integrity for data transfer is not required, then this VR is satisfied.</p>
<p>STD-008124 (-8)_2: The MPDD documents the integrity implementation(s) for data transfer for the Mission Package.</p></td>
<td><p>The MPDD documents the “as built” cybersecurity implementation details.</p>
<p>Each VR focuses on a different aspect of cybersecurity.</p>
<p>This information is documented in the “Cybersecurity Integrity Implementation(s)” section of the MPDD</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-010180 [A Tier 1 OMS Mission Package shall document its cybersecurity posture in accordance with the OMS Mission Package Worksheet Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-010180 (-1): This requirement is verified by inspection of the Mission Package Worksheet (MPW) is complete and complies with the current version of the MPW Template, OMSC-TMP-006, and identifies the CSRC assigned to the Mission Package.</td>
<td><p>STD-010180 (-1)_1: If there is no program-assigned Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-010180 (-1)_2: The Mission Package cybersecurity posture is documented in the MPW.</p></td>
<td><p>The cybersecurity posture as defined by the CSRC and described by the CSAs denotes what an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The MPW documents the CSRC, which is typically assigned by the program. If the Mission Package does not have a program-assigned Cybersecurity requirement, “N/A” is a valid assignment in the CSRC field.</p>
<p>“Current Version” in this context refers to the version of the MPW Template specified in the OMS Standard against which compliance is being measured.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 1 Requirements</td>
<td>RQMT STD-009714 [A Tier 1 OMS Mission Package shall document its cybersecurity posture in accordance with the “Cybersecurity Posture” section in the OMS Mission Package Description Document Template.]</td>
<td></td>
<td></td>
<td>1, 2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-009714 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD) “Cybersecurity Posture” section showing that the Mission Package cybersecurity posture is documented.</td>
<td><p>STD-009714 (-1)_1: If there is no program-assigned Cybersecurity requirement, this VR is satisfied.</p>
<p>STD-009714 (-1)_2: The Mission Package cybersecurity posture is documented in the MPDD “Cybersecurity Posture” section.</p></td>
<td><p>The cybersecurity posture as defined by the CSRC and described by the CSAs denotes what an OMS Architecture Element achieves as one element within a cyber-contested environment.</p>
<p>The “Cybersecurity Posture” section describes the implementation of the cybersecurity posture by OMS Architecture Element and provides additional, unclassified, and/or non-proprietary details relating to the security of the OMS Architecture Element.</p>
<p>The provided OMSC-GDE-003, Cybersecurity Guide, defines the concepts, guidance, and information that OMS Adopting Programs and system designers will utilize to document the cybersecurity posture.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-008675 [A Tier 2 OMS Mission Package shall meet Tier 1 Mission Package requirements.]</td>
<td></td>
<td><p>STD-000101</p>
<p>STD-000102</p>
<p>STD-000103</p>
<p>STD-000104</p>
<p>STD-005004</p>
<p>STD-008124</p>
<p>STD-009208</p>
<p>STD-009714</p>
<p>STD-009924</p>
<p>STD-010180</p></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-008675 (-1): This requirement is verified by the inspection of compliance artifacts showing the subordinate requirements for RQMT STD-008675 have been met.</td>
<td>STD-008675 (-1)_1: The [[Mission Package RQMT Checklist]] tab of the Mission Package Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-008675 have been met.</td>
<td>Tier 2 OMS Mission Packages must meet all Tier 1 OMS Mission Package requirements.</td>
</tr>
<tr class="odd">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-000107 [A Tier 2 OMS Mission Package shall provide an OMS Platform assessed to at least Tier 2 compliance.]</td>
<td></td>
<td></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000107 (-1): This requirement is verified by inspection of compliance artifacts showing that the OMS Mission Package includes an OMS Platform assessed to at least Tier 2 compliance.</td>
<td><p>STD-000107 (-1)_1: The MPDD documents that the OMS Mission Package includes an OMS Platform that is at least Tier 2 compliant.</p>
<p>STD-000107 (-1)_2: The OMS Platform listed in the MPDD has a Platform Checklist that indicates the Platform is assessed to at least Tier 2 compliance, which is recorded in the [[Tier Compliance]] tab of the Platform Checklist.</p></td>
<td>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD showing the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</td>
</tr>
<tr class="even">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-009210 [A Tier 2 OMS Mission Package shall contain only OMS Architecture Elements assessed to at least Tier 2 compliance.]</td>
<td>In this context, OMS Architecture Elements assessed for compliance in a Mission Package are defined as a Platform, Services, and Subsystems.</td>
<td></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-009210 (-1): This requirement is verified by inspection of compliance artifacts showing that each Platform, Subsystem, and Service included in the OMS Mission Package is assessed to at least Tier 2 compliance.</td>
<td><p>STD-009210 (-1)_1: The MPDD documents that each Platform, Subsystem, and Service included in the OMS Mission Package is at least Tier 2 compliant.</p>
<p>STD-009210 (-1)_2: Each OMS Architecture Element (Platform, Subsystem, and Service) listed in the MPDD has a corresponding checklist that indicates the OMS Architecture Element is assessed to at least Tier 2 compliance, which is recorded in the [[Tier Compliance]] tab of each checklist.</p></td>
<td><p>A complete "as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD showing the Tier compliance of the OMS Mission Package and each Platform, Subsystem, Service, and Isolator in the OMS Mission Package.</p>
<p>An OMS Mission Package can only achieve an assessment Tier that is no higher than the lowest tier of the following assessed Architecture Elements in the Mission Package: Platform, Subsystems, and Services.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-000108 [A Tier 2 OMS Mission Package shall provide all applicable Service capabilities from the “Service Capability List for Compliance” section at the Tier 2 compliance level.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Services that are identified as an OMS Service in the Mission Package Worksheet for the adopting program, that are described in the “Service Capability List for Compliance.”</p>
<p>If an adopting program does not include any Services that are described in this list, then there are no “applicable” Services and the requirement is satisfied.</p></td>
<td></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000108 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that each Service described in the “Service Capability List for Compliance” that is included in the OMS Mission Package is at least Tier 2 compliant.</td>
<td><p>STD-000108 (-1)_1: If the adopting program does not require any Services that are described in the “Service Capability List for Compliance,” then this VR is satisfied.</p>
<p>STD-000108 (-1)_2: The MPDD documents that each Service described in the “Service Capability List for Compliance” that is included in the OMS Mission Package is at least Tier 2 compliant.</p></td>
<td><p>It is possible that a Tier 2 OMS Mission Package does not include any Services that are described in the “Service Capability List for Compliance”</p>
<p>Some Services described in the list may not be applicable to a given Mission Package and are not included.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of each Architecture Element in the OMS Mission Package.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-000108 [A Tier 2 OMS Mission Package shall provide all applicable Service capabilities from the “Service Capability List for Compliance” section at the Tier 2 compliance level.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Services that are identified as an OMS Service in the Mission Package Worksheet for the adopting program, that are described in the “Service Capability List for Compliance.”</p>
<p>If an adopting program does not include any Services that are described in this list, then there are no “applicable” Services and the requirement is satisfied.</p></td>
<td></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-2</td>
<td>STD-000108 (-2): If the Mission Package Worksheet per OMSC-TMP-006 from the adopting program requires additional and/or specific Services to be at least Tier 2 compliant, then this requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that each additional program-specified Service is at least Tier 2 compliant.</td>
<td><p>STD-000108 (-2)_1: If the adopting program does not require additional or specific Services to be Tier 2 compliant, then this VR is satisfied.</p>
<p>STD-000108 (-2)_2: The MPDD shows that each additional Service required by the program to be Tier 2 compliant is documented as being at least Tier 2 compliant.</p></td>
<td><p>An adopting program may require additional or specific Services to be Tier 2 compliant.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of each Architecture Element in the OMS Mission Package.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-000109 [A Tier 2 OMS Mission Package shall provide all applicable Subsystems from the “Subsystem List for Compliance” section at the Tier 2 compliance level.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Subsystems that are identified as an OMS Subsystem in the Mission Package Worksheet for the adopting program, that are described in the “Subsystem List for Compliance.”</p>
<p>If an adopting program does not include any Subsystems that are described in this list, then there are no “applicable” Subsystems and the requirement is satisfied.</p></td>
<td></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000109 (-1): This requirement is verified by inspection of the Mission Package Description Document (MPDD) showing that each Subsystem described in the “Subsystem List for Compliance” that is included in the OMS Mission Package is at least Tier 2 compliant.</td>
<td><p>STD-000109 (-1)_1: If the adopting program does not require any Subsystems that are described in the “Subsystem List for Compliance,” then this VR is satisfied.</p>
<p>STD-000109 (-1)_2: The MPDD documents that each Subsystem described in the “Subsystem List for Compliance” that is included in the OMS Mission Package is at least Tier 2 compliant.</p></td>
<td><p>It is possible that a Tier 2 OMS Mission Package does not include any Subsystems that are described in the “Subsystem List for Compliance.”</p>
<p>Some Subsystems described in the list may not be applicable to a given Mission Package and are not included.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of each Architecture Element in the OMS Mission Package.</p></td>
</tr>
<tr class="even">
<td>Mission Package Tier 2 Requirements</td>
<td>RQMT STD-000109 [A Tier 2 OMS Mission Package shall provide all applicable Subsystems from the “Subsystem List for Compliance” section at the Tier 2 compliance level.]</td>
<td><p>In the context of this requirement, the term “applicable” means those Subsystems that are identified as an OMS Subsystem in the Mission Package Worksheet for the adopting program, that are described in the “Subsystem List for Compliance.”</p>
<p>If an adopting program does not include any Subsystems that are described in this list, then there are no “applicable” Subsystems and the requirement is satisfied.</p></td>
<td></td>
<td>2, 3</td>
<td>Mission Package</td>
<td>-2</td>
<td>STD-000109 (-2): If the Mission Package Worksheet per OMSC-TMP-006 from the adopting program requires additional and/or specific Subsystems to be at least Tier 2 compliant, then this requirement is verified by inspection of the Mission Package Description Document (MPDD), showing that each additional program-specified Subsystem is at least Tier 2 compliant.</td>
<td><p>STD-000109 (-2)_1: If the adopting program does not require additional or specific Subsystems to be Tier 2 compliant, then this VR is satisfied.</p>
<p>STD-000109 (-2)_2: The MPDD shows that each additional Subsystem required by the program to be Tier 2 compliant is documented as being at least Tier 2 compliant.</p></td>
<td><p>An adopting program may require additional or specific Subsystems to be Tier 2 compliant.</p>
<p>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD and documents the Tier compliance of each Architecture Element in the OMS Mission Package.</p></td>
</tr>
<tr class="odd">
<td>Mission Package Tier 3 Requirements</td>
<td>RQMT STD-008676 [A Tier 3 OMS Mission Package shall meet Tier 2 Mission Package requirements.]</td>
<td></td>
<td><p>STD-000107</p>
<p>STD-000108</p>
<p>STD-000109</p>
<p>STD-008675</p>
<p>STD-009210</p></td>
<td>3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-008676 (-1): This requirement is verified by the inspection of compliance artifacts showing the subordinate requirements for RQMT STD-008676 have been met.</td>
<td>STD-008676 (-1)_1: The [[Mission Package RQMT Checklist]] tab of the Mission Package Checklist shows that the subordinate requirements listed in the “Subordinate Requirements” column for RQMT STD-008676 have been met.</td>
<td>Tier 3 OMS Mission Packages must meet all Tier 1 and Tier 2 OMS Mission Package requirements.</td>
</tr>
<tr class="even">
<td>Mission Package Tier 3 Requirements</td>
<td>RQMT STD-000112 [A Tier 3 OMS Mission Package shall provide an OMS Platform assessed at Tier 3 compliance.]</td>
<td></td>
<td></td>
<td>3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-000112 (-1): This requirement is verified by inspection of compliance artifacts showing that the OMS Mission Package includes an OMS Platform assessed at Tier 3 compliance.</td>
<td><p>STD-000112 (-1)_1: The MPDD documents that the OMS Mission Package includes an OMS Platform that is Tier 3 compliant.</p>
<p>STD-000112 (-1)_2: The OMS Platform listed in the MPDD has a Platform Checklist that indicates the Platform is assessed at Tier 3 compliance, which is recorded in the [[Tier Compliance]] tab of the Platform Checklist.</p></td>
<td>A complete “as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD showing the Tier compliance of each Architecture Element in the OMS Mission Package.</td>
</tr>
<tr class="odd">
<td>Mission Package Tier 3 Requirements</td>
<td>RQMT STD-009212 [A Tier 3 OMS Mission Package shall contain only OMS Architecture Elements assessed at Tier 3 compliance.]</td>
<td>In this context, OMS Architecture Elements assessed for compliance in the Mission Package are defined as a Platform, Services, and Subsystems.</td>
<td></td>
<td>3</td>
<td>Mission Package</td>
<td>-1</td>
<td>STD-009212 (-1): This requirement is verified by inspection of compliance artifacts showing that each Platform, Subsystem, and Service included in the OMS Mission Package is assessed at Tier 3 compliance.</td>
<td><p>STD-009212 (-1)_1: The MPDD documents that each OMS Architecture Element (Platform, Subsystem, and Service) included in the OMS Mission Package is Tier 3 compliant.</p>
<p>STD-009212 (-1)_2: Each OMS Architecture Element (Platform, Subsystem, and Service) listed in the MPDD has a corresponding checklist that indicates the OMS Architecture Element is assessed at Tier 3 compliance, which is recorded in the [[Tier Compliance]] tab of each checklist.</p></td>
<td><p>A complete "as built” version of the information in the Mission Package Worksheet (MPW) per OMSC-TMP-006, is referenced by the “Mission Package Description” section of the MPDD showing the Tier compliance of each Architecture Element in the OMS Mission Package.</p>
<p>An OMS Mission Package can only achieve an assessment Tier that is no higher than the lowest tier of the following assessed Architecture Elements in the Mission Package: Platform, Subsystems, and Services.</p></td>
</tr>
</tbody>
</table>

OMS Compliance Assessment Approaches and Artifacts
==================================================

OMS Compliance Assessment Approaches
------------------------------------

There are several OMS compliance assessment approaches (Government,
Prime/Contractor/Supplier, or External) available for OMS Adopting
Programs, which will be determined for a specific AP by the government
customer in conjunction with the AP’s program management team. These
approaches range from self-assessments to external for both preliminary
and final compliance assessments.

OMS compliance assessment is intended to leverage existing program
requirements testing. OMS compliance verification is reliant on
self-assessment and self-disclosure of the underlying nature of reported
Non-OMS Messages or the use of an extension schema for the provided
program’s CAL. The assessment process depends on the completeness and
accuracy of the provider’s self-assessment (via compliance checklists)
of Mission Package Worksheets, Mission Package Description Documents,
Platform Description Documents, Subsystem Description Documents, and
Service Contracts, as applicable. Ultimately, the VCRM, and the
compliance checklists derived from the VCRM, should be used when
compliance assessment is undertaken.

### Government Assessment

A Government Program Office may elect to complete the OMS compliance
assessment process internally or may contract with another government
office to complete the OMS compliance assessment process. The Government
assumes responsibility for the OMS compliance assessment process and may
also request the AP’s program management team to perform compliance
assessments of all/most/some of the OMS Architecture Elements in the
AP’s Mission Package. The government can use self-assessments from the
providers of the various OMS Architecture Elements or use a third party
to perform and/or verify OMS compliance.

### Prime/Contractor/Supplier Self-Assessment

OMS compliance self-assessments are verified through established tools
and functional testing that OMS requirements are met. Self-assessments
occur at all levels performed by any combination of the AP’s Prime,
Contractors, and Suppliers, which may include contracting a third party
to perform self-assessment(s).

Self-assessments can be performed during multiple phases of a contract,
specifically at the time of the AP’s Proposal/Acquisition, AP’s PDR/CDR,
and AP’s Final Test/System Test. When self-assessments are performed
during the proposal/acquisition process or the PDR/CDR timeframe, then
the compliance assessments are considered preliminary. When
self-assessments are performed as part of the AP’s Final Test/System
Test phase at the end of the program, then the compliance assessments
are considered final for that AP.

### External Assessment

The Government Program Office can specify OMS compliance be assessed by
an independent third party. The third party may produce the compliance
assessments with or without existing self-assessments provided by the
OMS Architecture Elements providers.

Key Documents
-------------

Key documents for assessing OMS compliance include:

-   Mission Package Worksheet (MPW)

-   Mission Package Description Document (MPDD)

-   Platform Description Document (PDD)

-   Subsystem Description Document (SDD)

-   Service Contract

In general, the goal of these key documents is that they are structured
to support non-proprietary information to the maximum extent possible.
Currently the Mission Package Description Document, Platform Description
Document, Subsystem Description Document, and Service Contract are
required to be non-proprietary, but may reference some proprietary
documentation. Guidance is found in the checklists, templates,
instructions, and specifications, as seen in Figure 1.0-1, OMS D&D
Document Tree, and detailed in Table 5.2-1, OMS D&D Documents.

Compliance Tailoring for Different Phases of a Program
------------------------------------------------------

Asserting or proving compliance will change as a program evolves from a
proposal/acquisition phase to a program after final testing. The
following subsections describe the tailoring that may be used for
asserting or proving compliance at these different phases.

### Proposal/Acquisition

At the Proposal/Acquisition time frame there may not be draft versions
of Service Contracts, Subsystem Description Documents, and Platform
Description Documents. Functional testing or demonstration has not been
started and is not required for compliance. High level architecture
diagrams showing OMS elements exist.

During this phase, compliance may be claimed by stating that it is the
intention to develop OMS-compliant Subsystems and Services, along with
plans to create Service Contracts, Subsystem Description Documents, and
Platform Description Documents, perform testing, and collect the
appropriate artifacts. Some details about the OMS Platform and Mission
Package are required along with statements that assert the intended
compliance tier for the OMS Subsystems, OMS Services, and OMS Platform.

Table 9.3-1, Element Compliance Tailoring during Proposal or Acquisition
Phase, identifies acceptable tailoring for satisfying Verification
Requirements (VR) and Acceptance Criteria (AC) during a proposal or
acquisition phase.

<span id="_Toc219290738" class="anchor"></span>Table 9.3-1 Element
Compliance Tailoring during Proposal or Acquisition Phase

<table>
<thead>
<tr class="header">
<th>Element</th>
<th>Tailoring</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Service Contract</td>
<td><p>If a VR or AC calls out for inspection, comparison, or analysis of a Service Contract, compliance may be satisfied by the following:</p>
<ul>
<li><p>A statement declaring the Service Contract Document preliminary draft has been created and will be updated for the given OMS Service or OMS Subsystem prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement with justification declaring any required inspections or analysis of the Service Contract will be performed prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Functional Test Results</td>
<td><p>If a VR or AC calls out for inspection, comparison, or creation of Functional Test Results, compliance may be satisfied by the following:</p>
<ul>
<li><p>A statement with justification declaring the Functional Test Results will be collected for the given OMS Architecture Element prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement with justification declaring any required inspections or analysis of the Functional Test Results will be performed prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Analysis Report</td>
<td><p>If a VR or AC calls out for inspection or creation of an Analysis Report, compliance may be satisfied by the following:</p>
<ul>
<li><p>A statement with justification declaring the Analysis Report will be created for the given OMS Architecture Element prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement with justification declaring any required inspections of the Analysis Report will be performed prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Subsystem Description Document</td>
<td><p>If a VR or AC calls out for inspection or creation of a Subsystem Description Document, compliance may be satisfied by the following:</p>
<ul>
<li><p>A statement with justification declaring the Subsystem Description Document will be created or updated for the given OMS Subsystem prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement with justification declaring any required inspections of the Subsystem Description Document will be performed prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Platform Description Document</td>
<td><p>If a VR or AC calls out for inspection or creation of a Platform Description Document, compliance may be satisfied by the following:</p>
<ul>
<li><p>A statement with justification declaring the Platform Description Document preliminary draft has been created and will be updated for the given OMS Platform prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement with justification declaring any required inspections of the Platform Description Document will be performed prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A high level description of the CAL that identifies the transport mechanism that will be implemented.</p></li>
<li><p>Statements that an OMS-compliant ASB and CAL will be provided. If the ASB or CAL is re-used then information on the re-used elements should be provided.</p></li>
<li><p>Identification of which Data Transfer methods will be provided.</p></li>
<li><p>Identification of which OCE methods will be provided or provisioned.</p></li>
<li><p>Identification of which Special Signals will be provisioned or provided.</p></li>
<li><p>Description of the mission processing including which types of processors will be provided.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Demonstration of Specific Services</p>
<p>Inspection of Demonstration Results</p></td>
<td><p>If a VR or AC calls out for demonstration of specific Services or inspection of demonstration results, compliance may be satisfied by the following:</p>
<ul>
<li><p>A statement with justification declaring the specific Service will be executed and demonstrated prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement that declares that any required inspections of the demonstration results will be performed prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Mission Package Compliance</p>
<p>This tailoring is for all Mission Package Requirements.</p></td>
<td><p>Compliance for a Mission Package may be satisfied by the following:</p>
<ul>
<li><p>A Mission Package architecture diagram showing the following:</p></li>
</ul>
<ul>
<li><p>OMS-compliant Subsystems connected to the ASB.</p></li>
<li><p>OMS-compliant Services connected to the ASB.</p></li>
<li><p>An OMS-compliant Platform, with mission processing, and OCE types identified.</p></li>
<li><p>OMS-compliant Isolators connected to the ASB providing connectivity to non-OMS systems.</p></li>
</ul>
<ul>
<li><p>Preliminary draft of the top-level requirements of the Mission Package Checklist showing the following:</p></li>
</ul>
<ul>
<li><p>A matrix listing of all OMS-compliant Services, OMS-compliant Subsystems that identify the Tier level for the Subsystem or Service, and if the Subsystem or Service is on the Service Capabilities or Subsystems List for Compliance.</p></li>
<li><p>Identification of the Tier level for the OMS Platform that will be provided.</p></li>
<li><p>A statement with justification declaring that the Tier level for the Mission Package that will be provided.</p></li>
<li><p>A statement with justification declaring the Mission Package Description Document preliminary draft, if applicable, has been created and will be updated for the given OMS Mission Package prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
</tbody>
</table>

### PDR/CDR

At the Preliminary Design Review (PDR) and Critical Design Review (CDR)
time frame, there should be draft versions of Service Contracts,
Subsystem Description Documents, Platform Description Documents, and
Mission Package Description Documents (if applicable). Functional
testing or demonstration has not been started and is not required for
compliance. Architecture diagrams showing OMS elements exist.

During this phase, compliance may be claimed by stating that it is the
intention to develop OMS-compliant Subsystems and Services, along with
plans to perform testing and collect the appropriate artifacts. Some
inspection of the Service Contracts, Subsystem Description Documents,
Platform Description Documents, and Mission Package Description
Documents (if applicable) may be performed. Some details about the OMS
Platform and Mission Package are required along with statements that
assert the intended compliance Tier for the OMS Subsystems, OMS
Services, and OMS Platform.

Table 9.3-2, Element Compliance Tailoring at CDR/PDR, identifies
acceptable tailoring for satisfying Verification Requirements (VR) and
Acceptance Criteria (AC) during a CDR or PDR phase.

<span id="_Toc219290739" class="anchor"></span>Table 9.3-2 Element
Compliance Tailoring at CDR/PDR

<table>
<thead>
<tr class="header">
<th>Element</th>
<th>Tailoring</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Service Contract</td>
<td><p>If a VR or AC calls out for inspection, comparison, or analysis of a Service Contract, compliance may be claimed by the following:</p>
<ul>
<li><p>Perform the inspection, comparison, or analysis on the draft or updated draft Service Contract.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Functional Test Results</td>
<td><p>If a VR or AC calls out for inspection, comparison, or creation of Functional Test Results, compliance may be claimed by the following:</p>
<ul>
<li><p>A statement that declares that the Functional Test Results will be collected for the given OMS Architecture Element prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement that declares that any required inspections or analysis of the Functional Test Results will be performed prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>If some Functional Test Results exist then the inspection of those existing Functional Test results may be performed.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Analysis Report</td>
<td><p>If a VR or AC calls out for inspection or creation of an Analysis Report, compliance may be claimed by the following:</p>
<ul>
<li><p>A statement that declares that the Analysis Report will be created for the given OMS Architecture Element prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement that declares that any required inspections of the Analysis Report will be performed prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>If an Analysis Report exists then inspection of that Analysis Report may be performed.</p></li>
</ul></td>
</tr>
<tr class="even">
<td>Subsystem Description Document</td>
<td><p>If a VR or AC calls out for inspection or creation of a Subsystem Description Document, compliance may be claimed by the following:</p>
<ul>
<li><p>Perform the inspection, on the draft or updated draft Subsystem Description Document.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td>Platform Description Document</td>
<td><p>If a VR or AC calls out for inspection or creation of a Platform Description Document, compliance may be claimed by the following:</p>
<ul>
<li><p>Perform the inspection, on the draft or updated draft Platform Description Document.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Demonstration of Specific Services</p>
<p>Inspection of Demonstration Results</p></td>
<td><p>If a VR or AC calls out for demonstration of specific Services or inspection of demonstration results, compliance may be claimed by the following:</p>
<ul>
<li><p>A statement that declares that the specific Service will be executed and demonstrated prior to program completion as part of achieving OMS compliance.</p></li>
<li><p>A statement that declares that any required inspections of the demonstration results will be performed prior to program completion as part of achieving OMS compliance.</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>Mission Package Compliance</p>
<p>This tailoring is for all Mission Package Requirements.</p></td>
<td><p>Compliance for a Mission Package may be claimed by the following:</p>
<ul>
<li><p>A Mission Package architecture diagram showing the following:</p></li>
</ul>
<ul>
<li><p>OMS-compliant Subsystems connected to the ASB.</p></li>
<li><p>OMS-compliant Services connected to the ASB.</p></li>
<li><p>An OMS-compliant Platform, with mission processing, and OCE types identified.</p></li>
</ul>
<ul>
<li><p>A matrix listing of all OMS-compliant Services, OMS-compliant Subsystems that identify the Tier level for the Subsystem or Service, and if the Subsystem or Service is on the Service Capabilities or Subsystems List for Compliance.</p></li>
<li><p>Identification of the Tier level for the OMS Platform that will be provided.</p></li>
<li><p>A statement that declares the Tier level for the Mission Package that will be provided.</p></li>
<li><p>Perform an inspection on the draft or updated draft Platform Description Document.</p></li>
<li><p>Perform an inspection of the draft Mission Package Description Document (if applicable) or updated preliminary draft for the given OMS Mission Package.</p></li>
</ul></td>
</tr>
</tbody>
</table>

### Final Test/System Test

At the time of final test/system test it is assumed that the AP is
proving compliance to all OMS requirements. At this time, the entire
VCRM should be verified as written and compliance tailoring is not
applicable.

Version of the D&D
==================

Versioning Process
------------------

The OMS approach to versioning is to assign release numbers using 2
integers separated by a decimal point (i.e., X.Y) where the X is
increased as determined by the OMS authorities based on their belief
that the release is a significant change, and the Y is either set to
zero (when the X is incremented) or incremented (for non-significant
releases). The release number is not indicative of impact to an
individual program nor backwards compatibility with a previous release.
Each OMS release has the OMS Standard X.Y (i.e., Overall OMS Standard
Document X.Y, CAL Specification X.Y, and all other supporting
documentation X.Y) and a Version Description Document (VDD).

Each AP must analyze the impact of changes to the Standard based upon
their own implementation and determine the appropriate timing for moving
to a new version of the Standard release.

Each release of OMS is accompanied by a VDD that records the overall
version of the Standard and the revision letter of each constituent
document. Each document has a revision letter that is incremented each
time that document incorporates changes and includes an associated
change history table that describes the scope of the change.

List of Symbols, Abbreviations, and Acronyms
============================================

For the list of acronyms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.

Glossary
========

For the glossary of terms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.

Appendix A – OMS Implementation Patterns
========================================

A-1 Adapter Implementation Patterns
-----------------------------------

Both OMS Subsystems and Services can be implemented by using OMS
Adapters to bring the data exchanges of a non-OMS subsystem or non-OMS
service into full OMS compliance (i.e., to adapt non-OMS data exchanges
into OMS Data Exchanges).

The following figures depict multiple allowable integration patterns
that may be considered (using Subsystem adaptation as an example, but
Service adaptation can follow the same patterns):

1\. Figure A.1-1, Platform-Hosted OMS Adaptation, depicts where a
Platform-hosted Adapter provides OMS compliance to an otherwise non-OMS
subsystem

<img src="media/image30.png" style="width:6.5in;height:3.5625in" />

<span id="_Toc219290714" class="anchor"></span>Figure A.1-1
Platform-Hosted OMS Adaptation

2\. Figure A.1-2, Subsystem-Hosted OMS Adaptation, depicts where a
Subsystem-hosted Adapter provides OMS compliance.

<img src="media/image31.png" style="width:6.5in;height:4.02083in" />

<span id="_Toc219290715" class="anchor"></span>Figure A.1-2
Subsystem-Hosted OMS Adaptation

3\. Figure A.1-3, Standalone OMS Subsystem, depicts where a Subsystem is
OMS compliant without requiring adaptation.

<img src="media/image32.png" style="width:6.5in;height:3.82292in" />

<span id="_Toc219290716" class="anchor"></span>Figure A.1-3 Standalone
OMS Subsystem

It should be noted that the OMS Standard only levies requirements on
Platform-hosted Subsystem and/or Service adaptation, requiring
documentation of the Adapter-Platform interaction in the SDD (in the
case of Platform-hosted Subsystem adaptation), Service Contract (in the
case of Platform-hosted Service adaptation), and PDD.
Subsystem/Service-hosted OMS adaptation and OMS integrated
Subsystem/Service implementation patterns are wholly contained within
the Subsystem/Service boundaries and are indistinguishable from outside
the Subsystem/Service, making them outside the scope of the OMS
Standard.
