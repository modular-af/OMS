Open Mission Systems (OMS)

Definition And Documentation (D&D)

Platform Description Document (PDD) Template

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

&lt;REQUIRED: Platform Description Document Title&gt;

&lt;OPTIONAL: Organizational Logo&gt;

&lt;REQUIRED: Date as DD Month YYYY&gt;

&lt;OPTIONAL: Other labeling as appropriate&gt;

Prepared by:

&lt;REQUIRED: Organization&gt;

&lt;OPTIONAL: Address&gt;

&lt;OPTIONAL: Approval Signatures&gt;

This page is intentionally left blank.

Abstract

Required: Insert program specific abstract summary details here.

Open Mission Systems (OMS) is a non-proprietary open architecture for
integrating subsystems and services into mission packages.

This Platform Description Document (PDD) complies with the Platform
Description Document (PDD) Template, OMSC-TMP-001, Revision M, dated 22
January 2026.

The template is prescribed by the OMS Standard Version 2.5,
OMSC-STD-001, Revision M, dated 22 January 2026.

This page is intentionally left blank.

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
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

This page is intentionally left blank.

Table of Contents

[1 Overview 1](#overview)

[1.1 References 1](#references)

[2 Platform 2](#platform)

[2.1 Platform Licenses 2](#platform-licenses)

[2.2 Platform Software Dependencies 2](#platform-software-dependencies)

[3 Abstract Service Bus (ASB) 3](#abstract-service-bus-asb)

[3.1 OMS Message Set 3](#oms-message-set)

[3.2 Network 3](#network)

[3.2.1 Network Interconnect Diagram 3](#network-interconnect-diagram)

[3.2.2 Ports & Protocols 3](#ports-protocols)

[3.2.3 Network Address Information 4](#network-address-information)

[4 Data Transfer 5](#data-transfer)

[4.1 Data Storage 5](#data-storage)

[4.1.1 Data Storage Access Controls 5](#data-storage-access-controls)

[4.1.2 Data Storage Confidentiality Mechanisms
6](#data-storage-confidentiality-mechanisms)

[4.1.3 Data Storage Integrity Mechanisms
6](#data-storage-integrity-mechanisms)

[4.2 Data Transfer Confidentiality Mechanisms
6](#data-transfer-confidentiality-mechanisms)

[4.3 Data Transfer Integrity Mechanisms
6](#data-transfer-integrity-mechanisms)

[4.4 Data Transfer Configuration 7](#data-transfer-configuration)

[4.4.1 Data Transfer Protocol Details
7](#data-transfer-protocol-details)

[5 Mission Processing 8](#mission-processing)

[5.1 Open Computing Environment (OCE)
8](#open-computing-environment-oce)

[5.1.1 OCE Processor Types, Operating Systems, and Configuration
8](#oce-processor-types-operating-systems-and-configuration)

[5.1.2 General Environment 8](#general-environment)

[5.1.2.1 Build Environment and Tool Chain
8](#build-environment-and-tool-chain)

[5.1.2.2 Isolation Layer 8](#isolation-layer)

[5.1.2.3 Time 8](#time)

[5.1.3 Java Environment 8](#java-environment)

[5.1.3.1 Build Environment and Tool Chain
8](#build-environment-and-tool-chain-1)

[5.1.3.2 Java Data Transfer 8](#java-data-transfer)

[5.1.3.3 Time 9](#time-1)

[5.1.4 Service Deployment 9](#service-deployment)

[5.2 Other Mission Processing 9](#other-mission-processing)

[5.2.1 Other Mission Processor Types, Configuration and Interfaces
9](#other-mission-processor-types-configuration-and-interfaces)

[5.2.2 Other Mission Processing Tool Chain Description
9](#other-mission-processing-tool-chain-description)

[5.2.3 OMS Attributes for Other Mission Processing
9](#oms-attributes-for-other-mission-processing)

[5.2.4 Service Deployment 9](#service-deployment-1)

[6 Time and Position Information 10](#time-and-position-information)

[6.1 Time Reference and Time Synchronization
10](#time-reference-and-time-synchronization)

[6.2 Position Information 12](#position-information)

[6.2.1 Position Information Indirectly Provided for the Platform
12](#position-information-indirectly-provided-for-the-platform)

[6.2.2 Position Information Directly Provided by Platform
12](#position-information-directly-provided-by-platform)

[7 Critical Abstraction Layer (CAL) Implementation
14](#critical-abstraction-layer-cal-implementation)

[7.1 CAL Available Implementations 14](#cal-available-implementations)

[7.2 CAL Required Libraries / Licenses
14](#cal-required-libraries-licenses)

[7.3 CAL Implementation Processing Architecture
15](#cal-implementation-processing-architecture)

[7.3.1 Language-Specific CAL 15](#language-specific-cal)

[7.3.1.1 \[CAL Identifier\] 15](#cal-identifier)

[7.3.1.1.1 \[CAL Identifier\] CAL Configuration
15](#cal-identifier-cal-configuration)

[7.3.1.1.2 \[CAL Identifier\] CAL Externalizer Implementation
15](#cal-identifier-cal-externalizer-implementation)

[7.3.1.1.3 \[CAL Identifier\] CAL Operational Attributes
15](#cal-identifier-cal-operational-attributes)

[7.3.2 Language Agnostic CAL 16](#language-agnostic-cal)

[7.3.2.1 \[CAL Identifier\] 16](#cal-identifier-1)

[7.3.2.1.1 \[CAL Identifier\] Language-Agnostic CAL Configuration
16](#cal-identifier-language-agnostic-cal-configuration)

[8 Virtualization Environments 17](#virtualization-environments)

[8.1 Virtualization Environment - &lt;&lt;Name&gt;&gt;
17](#virtualization-environment---name)

[8.1.1 Processor Virtualization 17](#processor-virtualization)

[8.1.2 Memory Virtualization 17](#memory-virtualization)

[8.1.3 Network Virtualization 17](#network-virtualization)

[8.1.4 Virtualization Environment Deployment
17](#virtualization-environment-deployment)

[8.1.5 Service Deployment 17](#service-deployment-2)

[8.1.6 Time 17](#time-2)

[8.1.7 Virtualization Environment Configuration
17](#virtualization-environment-configuration)

[9 Configuration Data 18](#configuration-data)

[10 Special Signals 19](#special-signals)

[10.1 Provided Special Signals 19](#provided-special-signals)

[10.2 Provisioned Special Signals 19](#provisioned-special-signals)

[11 Cybersecurity Posture 20](#cybersecurity-posture)

[11.1 Cyber Survivability Attributes (CSAs)
20](#cyber-survivability-attributes-csas)

[11.1.1 Prevent CSAs 20](#prevent-csas)

[11.1.2 Mitigate CSAs 20](#mitigate-csas)

[11.1.3 Recover CSA 20](#recover-csa)

[11.1.4 Adapt CSA 20](#adapt-csa)

[12 Security Addendum 21](#security-addendum)

[A Appendix A Acronyms And Abbreviations
22](#appendix-a-acronyms-and-abbreviations)

[B Appendix B Glossary 24](#appendix-b-glossary)

[C Appendix C Message Details 26](#appendix-c-message-details)

List of Figures

[Figure 3.2-1 Network Interconnect Diagram 3](#_Toc219294652)

This page is intentionally left blank.

List of Tables

[Table 1.1-1 Reference Documents 1](#_Toc219294653)

[Table 2.1-1 Platform Licenses 2](#_Toc219294654)

[Table 2.2-1 Platform Software Dependencies 2](#_Toc219294655)

[Table 3.1-1 OMS Message Set 3](#_Toc219294656)

[Table 3.2-1 Network Segmentation 3](#_Toc219294657)

[Table 3.2-2 Open Ports and Protocols 4](#_Toc219294658)

[Table 3.2-3 Product/Data and Data Transfer Servers 4](#_Toc219294659)

[Table 3.2-4 Networking Information 4](#_Toc219294660)

[Table 4.1-1 Platform Data Storage Details 5](#_Toc219294661)

[Table 4.1-2 Data Storage Access Control Mechanisms 5](#_Toc219294662)

[Table 4.1-3 Data Storage Confidentiality 6](#_Toc219294663)

[Table 4.1-4 Data Storage Integrity 6](#_Toc219294664)

[Table 4.2-1 Data Transfer Confidentiality Mechanisms 6](#_Toc219294665)

[Table 4.3-1 Data Transfer Integrity Mechanisms 6](#_Toc219294666)

[Table 4.4-1 Platform Data Transfer Configuration 7](#_Toc219294667)

[Table 6.1-1 Time Synchronization Protocols 10](#_Toc219294668)

[Table 6.1-2 High Fidelity Time Reference and Time Synchronization
Mechanisms 10](#_Toc219294669)

[Table 6.1-3 SystemTimeAtReference Inputs and Outputs
11](#_Toc219294670)

[Table 6.2-1 Source Providing Position Information 12](#_Toc219294671)

[Table 6.2-2 Position Information Processing Inputs and Outputs
13](#_Toc219294672)

[Table 7.1-1 CAL Versions Available 14](#_Toc219294673)

[Table 7.1-2 CAL Interaction Limitations 14](#_Toc219294674)

[Table 7.2-1 CAL Licenses & Libraries 15](#_Toc219294675)

[Table 7.3-1 CAL Externalizer Version Information 15](#_Toc219294676)

[Table 7.3-2 SOAC-1 16](#_Toc219294677)

[Table 7.3-3 Language-Agnostic CAL Access Information
16](#_Toc219294678)

[Table 9.0-1 Configuration Data 18](#_Toc219294679)

[Table 10.1-1 Provided Special Signals 19](#_Toc219294680)

[Table 10.2-1 Provisioned Special Signals 19](#_Toc219294681)

[Table 11.1-1 Applicable System Survivability KPP Prevent CSAs
20](#_Toc219294682)

[Table 11.1-2 Applicable System Survivability KPP Mitigate CSAs
20](#_Toc219294683)

[Table A.0-1 List of Acronym and Abbreviation Definitions
22](#_Toc219294684)

[Table B.0-1 List of Term Definitions 24](#_Toc219294685)

This page is intentionally left blank.

Overview
========

Proprietary Notice: This document contains only non-proprietary
information. Referenced documents conform to the Proprietary Notice
statement for each major subsection.

This section identifies the OMS Platform that is incorporated into a
Weapon System or Test Configuration which is in a software
integration/test facility.

References
----------

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

This section lists all the referenced documents that are required to
support the integration of this Platform as shown in Table 1.1-1,
Reference Documents.

<span id="_Toc219294653" class="anchor"></span>Table 1.1-1 Reference
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
<td>OMSC-SPC-005</td>
<td>Operating System Façade Specification</td>
<td>J</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-STD-001</td>
<td>OMS Standard Version 2.5</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-TMP-001</td>
<td>Platform Description Document (PDD) Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>

1.  Platform
    ========

    1.  Platform Licenses
        -----------------

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section identifies the licenses required in order to operate the
Platform, including the OCE, Other Mission Processing hardware,
software, or infrastructure as shown in Table 2.1-1, Platform Licenses.

<span id="_Toc219294654" class="anchor"></span>Table 2.1-1 Platform
Licenses

<table>
<thead>
<tr class="header">
<th>License Name</th>
<th>Provider</th>
<th>Version</th>
<th>Purpose</th>
<th>License Type</th>
<th>License URI</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Platform Software Dependencies
------------------------------

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

This section identifies all software (first, second, and third party)
that are required to run the Platform even if a license is not required
as shown in Table 2.2-1, Platform Software Dependencies.

<span id="_Toc219294655" class="anchor"></span>Table 2.2-1 Platform
Software Dependencies

<table>
<thead>
<tr class="header">
<th>Name</th>
<th>Provider</th>
<th>Version</th>
<th>Purpose</th>
<th>OS</th>
<th>OCE/Non-OCE/Subsystem/Platform</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Abstract Service Bus (ASB)
==========================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section documents the Platform’s network infrastructure and data
exchanges.

OMS Message Set
---------------

This section identifies the ASB Identifier, Baseline OMS Message Schema,
and the Extension Schema as shown in Table 3.1-1, OMS Message Set.

<span id="_Toc219294656" class="anchor"></span>Table 3.1-1 OMS Message
Set

<table>
<thead>
<tr class="header">
<th>ASB Identifier</th>
<th>Baseline OMS Message Schema</th>
<th>Extension Schema(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Network
-------

This section identifies details of the network(s) such as the bandwidth
and network routing/switching.

### Network Interconnect Diagram

This section describes the endpoint connections, interface speeds, and
any limitations of the Platform network architecture.

Figure 3.2-1, Network Interconnect Diagram, is a representation of the
Platform’s network.

&lt;&lt;INSERT FIGURE HERE. SEE ACCOMPANYING INSTRUCTIONS FOR AN
EXAMPLE&gt;&gt;

<span id="_Toc219294652" class="anchor"></span>Figure 3.2-1 Network
Interconnect Diagram

Table 3.2-1, Network Segmentation, lists the network segments, the
method used for segmentation and a description.

<span id="_Toc219294657" class="anchor"></span>Table 3.2-1 Network
Segmentation

<table>
<thead>
<tr class="header">
<th>Network Segment</th>
<th>Segmentation Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Ports & Protocols

This section identifies the ports and protocols that are in use and
accessible on the ASB network or bus.

Table 3.2-2, Open Ports and Protocols, identifies the ports and
protocols on the Mission Package.

<span id="_Toc219294658" class="anchor"></span>Table 3.2-2 Open Ports
and Protocols

<table>
<thead>
<tr class="header">
<th>Port</th>
<th>TCP or UDP</th>
<th>Protocol</th>
<th>Process/Service</th>
<th>Address</th>
<th>Purpose</th>
<th>Restriction Mechanism</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Table 3.2-3, Product/Data and Data Transfer Servers, identifies the
products being sent or received by Data Transfer server.

<span id="_Toc219294659" class="anchor"></span>Table 3.2-3 Product/Data
and Data Transfer Servers

<table>
<thead>
<tr class="header">
<th>Client Address</th>
<th>Product/Data</th>
<th>Format</th>
<th>Send/Receive</th>
<th>Data Transfer Server</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Network Address Information

This section identifies the network segment, IP Address Space (& network
mask), IP Gateways and method for assigning IP addresses as shown in
Table 3.2-4, Networking Information.

<span id="_Toc219294660" class="anchor"></span>Table 3.2-4 Networking
Information

<table>
<thead>
<tr class="header">
<th>Network Segment</th>
<th>Gateway</th>
<th>DNS Server</th>
<th>IP Address Assignment</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Data Transfer
=============

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section details the Platform’s data storage; data transfer
integrity and confidentiality as well as the data transfer
configuration.

Data Storage
------------

This section identifies the Platform’s data storage capability that can
be utilized by properly authenticated OMS Services and Subsystems as
shown in Table 4.1-1, Platform Data Storage Details.

<span id="_Toc219294661" class="anchor"></span>Table 4.1-1 Platform Data
Storage Details

<table>
<thead>
<tr class="header">
<th>Data Store Address</th>
<th>Data Store Label</th>
<th>Shared Directories</th>
<th>Storage Capacity</th>
<th>Non-Volatile Storage (Yes/No)</th>
<th>Protection In Place (No/C/I/CI)</th>
<th>Data Transfer Protocol(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

No – Neither confidentiality nor integrity mechanisms are in place

C – Confidentiality mechanisms are in place

I – Integrity mechanisms are in place

CI – Confidentiality and Integrity mechanisms are in place

### Data Storage Access Controls

This section identifies the methods for identification authentication,
access restrictions, and audit logging as shown in Table 4.1-2, Data
Storage Access Control Mechanisms.

<span id="_Toc219294662" class="anchor"></span>Table 4.1-2 Data Storage
Access Control Mechanisms

<table>
<thead>
<tr class="header">
<th>Mechanism</th>
<th>Implementation Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Identification</td>
<td></td>
</tr>
<tr class="odd">
<td>Authentication</td>
<td></td>
</tr>
<tr class="even">
<td>Access Control</td>
<td></td>
</tr>
<tr class="odd">
<td>Audit Logging</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Identification</td>
<td></td>
</tr>
<tr class="even">
<td>Authentication</td>
<td></td>
</tr>
<tr class="odd">
<td>Access Control</td>
<td></td>
</tr>
<tr class="even">
<td>Audit Logging</td>
<td></td>
</tr>
</tbody>
</table>

### Data Storage Confidentiality Mechanisms

This section identifies the specific mechanisms provided for Data
storage as shown in Table 4.1-3, Data Storage Confidentiality.

<span id="_Toc219294663" class="anchor"></span>Table 4.1-3 Data Storage
Confidentiality

<table>
<thead>
<tr class="header">
<th>Data Store Label</th>
<th>Protected Data</th>
<th>Confidentiality Mechanism</th>
<th>Implementation Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Data Storage Integrity Mechanisms

This section identifies the specific integrity mechanisms provided for
Data Storage as shown in Table 4.1-4, Data Storage Integrity.

<span id="_Toc219294664" class="anchor"></span>Table 4.1-4 Data Storage
Integrity

<table>
<thead>
<tr class="header">
<th>Data Store Label</th>
<th>Protected Data</th>
<th>Integrity Mechanism</th>
<th>Implementation details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Data Transfer Confidentiality Mechanisms
----------------------------------------

This section identifies the confidentiality mechanisms the Platform
supports for data transfers as shown in Table 4.2-1, Data Transfer
Confidentiality Mechanisms.

<span id="_Toc219294665" class="anchor"></span>Table 4.2-1 Data Transfer
Confidentiality Mechanisms

<table>
<thead>
<tr class="header">
<th>Protected Data</th>
<th>Confidentiality Mechanism</th>
<th>Implementation Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Data Transfer Integrity Mechanisms
----------------------------------

This section identifies the integrity mechanisms the Platform supports
for data transfers as shown in Table 4.3-1, Data Transfer Integrity
Mechanisms.

<span id="_Toc219294666" class="anchor"></span>Table 4.3-1 Data Transfer
Integrity Mechanisms

<table>
<thead>
<tr class="header">
<th>Protected Data</th>
<th>Integrity Mechanism</th>
<th>Implementation Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Data Transfer Configuration
---------------------------

This section identifies the Data Transfer methods provided by this
Platform and the configuration details associated with the Data Transfer
methods.

### Data Transfer Protocol Details

This section identifies the Data Transfer methods provided by this
Platform and the configuration details associated with the Data Transfer
methods as shown in Table 4.4-1, Platform Data Transfer Configuration.

<span id="_Toc219294667" class="anchor"></span>Table 4.4-1 Platform Data
Transfer Configuration

<table>
<thead>
<tr class="header">
<th>Data Transfer Server</th>
<th>Data Transfer Protocol</th>
<th>Version</th>
<th>Configuration Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Mission Processing
==================

This section documents the Platform’s mission processing architecture
including both the required Open Computing Environment (OCE) and Other
Mission Processing.

Open Computing Environment (OCE)
--------------------------------

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section documents the Platform’s OCE OMS mission processing
architecture and describes specific tool chains for building in the
various OCE environments.

### OCE Processor Types, Operating Systems, and Configuration

This section documents the processor architecture/type, processor
memory, processor quantity, and operating systems (type and 32 or 64
bit) for each processor in the OCE.

### General Environment

This section documents the general environment provided by the OCE.

#### Build Environment and Tool Chain

This section documents the specific build environment for an OCE.

#### Isolation Layer

This section documents the implemented Façade interfaces for this
Platform as defined in the OMS OS Façade Specification.

#### Time

This section documents how time synchronization is supported by the OCE.

### Java Environment

This section documents the specific Java environment provided by the
Java-based OCE.

#### Build Environment and Tool Chain

This section documents the specific build environment for a Java-based
OCE and how a Service is compiled for an OCE target implementation.

#### Java Data Transfer

This section documents the C/C++ libraries (if any) that are provided as
part of the Java-based OCE and that the Java environment is reliant upon
in order to perform data transfer operations.

#### Time 

This section documents how time synchronization is supported by the
Java-based OCE.

### Service Deployment

This section documents how Services are deployed and managed within the
OCE.

Other Mission Processing
------------------------

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section documents any Platform non-OCE Other Mission Processing
architecture and describes specific tool chains for building in the
Other Mission Processing environments.

### Other Mission Processor Types, Configuration and Interfaces

This section documents the architecture, type, memory, and quantity of
processors provided by the Platform for Other Mission Processing.

### Other Mission Processing Tool Chain Description

This section documents how a Service is compiled for the Other Mission
Processing target implementation.

### OMS Attributes for Other Mission Processing

This section describes the OMS elements resident on the Other Mission
Processing solution.

### Service Deployment

This section documents how Services are deployed and managed within the
Other Mission Processing.

Time and Position Information
=============================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section describes the time and position information provided by the
OMS Platform.

Time Reference and Time Synchronization
---------------------------------------

This section identifies the time reference and its sources and documents
its precision and accuracy as well as the method of distributing a time
reference for synchronization.

Table 6.1-1 Time Synchronization Protocols, identifies all the time
reference methods provided by the Platform and implemented per OMS
Standard, OMSC-STD-001, “Time Reference.”

<span id="_Toc219294668" class="anchor"></span>Table 6.1-1 Time
Synchronization Protocols

<table>
<thead>
<tr class="header">
<th>Time Synchronization Protocol</th>
<th>Provided (Y/N)?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IEEE 1588-2008 PTP</td>
<td></td>
</tr>
<tr class="even">
<td>IEEE 588-2019 PTP</td>
<td></td>
</tr>
<tr class="odd">
<td>RFC 1119 NTP</td>
<td></td>
</tr>
</tbody>
</table>

When high fidelity time synchronization is required, all time reference
methods implemented per OMS Standard, OMSC-STD-001, “Time Reference,”
should be documented in Table 6.1-2 High Fidelity Time Reference and
Time Synchronization Mechanisms.

<span id="_Toc219294669" class="anchor"></span>Table 6.1-2 High Fidelity
Time Reference and Time Synchronization Mechanisms

<table>
<thead>
<tr class="header">
<th>Time Synchronization Mechanisms</th>
<th>Provided (Y/N)?</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IRIG B</td>
<td></td>
</tr>
<tr class="even">
<td>1 PPS</td>
<td></td>
</tr>
<tr class="odd">
<td>PTTI</td>
<td></td>
</tr>
</tbody>
</table>

When 1 PPS time synchronization mechanism is provided, the
**SystemTimeAtReference** message is required. In this case, the
Platform directly provides the **SystemTimeAtReference** message, and
the respective fields and characters should be in identified in Table
6.1-3, **SystemTimeAtReference** Inputs and Outputs.

<span id="_Toc219294670" class="anchor"></span>Table 6.1-3
SystemTimeAtReference Inputs and Outputs

<table>
<thead>
<tr class="header">
<th>MP</th>
<th>IO</th>
<th>DE</th>
<th>Data Exchange Name</th>
<th>Data Exchange Information (e.g., Topic Name for Messages or Protocol for Data Transfers)</th>
<th>LoM</th>
<th>P</th>
<th>Nominal Response Time or Nominal Periodic Rate</th>
<th>Max Response Time or Max Periodic Rate</th>
<th>Appendix C Mapping</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D</td>
<td>O</td>
<td>M</td>
<td>SystemTimeAtReference</td>
<td></td>
<td>M</td>
<td>P</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>Column Headings &amp; Cell Abbreviations:</p>
<ul>
<li><p>MP=Message Primitive: S=Status-1; C/CS=Command-2; AR/ARS=ActionRequest-2; DR/DRS=DataRequest-2; D=Data-1; DRec=DataRecord-1</p></li>
<li><p>I/O=Input/Output: I=Input; O=Output</p></li>
<li><p>DE=Data Exchange: M=OMS Message; DT=Data Transfer; SS=Special Signal; SE=Security Exchange</p></li>
<li><p>LoM=Level of Mandate: M=Mandatory; O=Optional</p></li>
<li><p>P=Periodicity: A=Asynchronous; OD=On Demand; P=Periodic</p></li>
</ul></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Position Information
--------------------

This section documents the accuracy and precision of the position
information.

### Position Information Indirectly Provided for the Platform

When a Subsystem, Service, or Isolator is indirectly providing the
position information to the Platform, the source of the
**PositionReport** and/or **PositionReportDetailed** should be
identified in Table 6.2-1 Source Providing Position Information.

<span id="_Toc219294671" class="anchor"></span>Table 6.2-1 Source
Providing Position Information

<table>
<thead>
<tr class="header">
<th>Position Information Provided</th>
<th>Subsystem, Service, or Isolator Name</th>
<th>Service Contract</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>PositionReport</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>PositionReportDetailed</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Position Information Directly Provided by Platform

When the Platform is directly providing the position information via the
**PositionReport** and/or **PositionReportDetailed** messages, the
respective fields and characters should be identified in Table 6.2-2,
Position Information Processing Inputs and Outputs.

<span id="_Toc219294672" class="anchor"></span>Table 6.2-2 Position
Information Processing Inputs and Outputs

<table>
<thead>
<tr class="header">
<th>MP</th>
<th>IO</th>
<th>DE</th>
<th>Data Exchange Name</th>
<th>Data Exchange Information (e.g., Topic Name for Messages or Protocol for Data Transfers)</th>
<th>LoM</th>
<th>P</th>
<th>Nominal Response Time or Nominal Periodic Rate</th>
<th>Max Response Time or Max Periodic Rate</th>
<th>Appendix C Mapping</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>D</td>
<td>O</td>
<td>M</td>
<td>PositionReport</td>
<td></td>
<td>M</td>
<td>P</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>D</td>
<td>O</td>
<td>M</td>
<td>PositionReportDetailed</td>
<td></td>
<td>M</td>
<td>P</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Column Headings &amp; Cell Abbreviations:</p>
<ul>
<li><p>MP=Message Primitive: S=Status-1; C/CS=Command-2; AR/ARS=ActionRequest-2; DR/DRS=DataRequest-2; D=Data-1; DRec=DataRecord-1</p></li>
<li><p>I/O=Input/Output: I=Input; O=Output</p></li>
<li><p>DE=Data Exchange: M=OMS Message; DT=Data Transfer; SS=Special Signal; SE=Security Exchange</p></li>
<li><p>LoM=Level of Mandate: M=Mandatory; O=Optional</p></li>
<li><p>P=Periodicity: A=Asynchronous; OD=On Demand; P=Periodic</p></li>
</ul></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Critical Abstraction Layer (CAL) Implementation
===============================================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

This section documents all of the CAL implementations.

CAL Available Implementations
-----------------------------

This section documents the method developers link CAL libraries into
applications.

Table 7.1-1, CAL Versions Available, identifies the operating system,
programming language, CAL Schema Compiler Version number, CAL
Implementation Version number, and target runtime location.

<span id="_Toc219294673" class="anchor"></span>Table 7.1-1 CAL Versions
Available

<table>
<thead>
<tr class="header">
<th>CAL Identifier</th>
<th>Operating System</th>
<th>Programming Language</th>
<th>OMS Specification Version</th>
<th>CAL Implementation Version</th>
<th>OMS Message Set</th>
<th>OCE/Non-OCE/Subsystem/Isolator/Platform</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Table 7.1-2, CAL Interaction Limitations, documents any restrictions
that the CALs may encounter while interacting with one another.

<span id="_Toc219294674" class="anchor"></span>Table 7.1-2 CAL
Interaction Limitations

<table>
<thead>
<tr class="header">
<th><p>CAL</p>
<p>Publisher</p>
<p>CAL</p>
<p>Subscriber</p></th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

None indicates the CAL pair interact without limitations.

Limited<sup>1</sup> indicates the CAL pair do not interact.

CAL Required Libraries / Licenses
---------------------------------

This section documents the required libraries and licenses required to
run the CAL implementations as shown in Table 7.2-1, CAL Licenses &
Libraries.

<span id="_Toc219294675" class="anchor"></span>Table 7.2-1 CAL Licenses
& Libraries

<table>
<thead>
<tr class="header">
<th>CAL Identifier(s)</th>
<th>Supported Operational Attribute Configuration</th>
<th>Purpose</th>
<th>Provider</th>
<th>Product</th>
<th>Version</th>
<th>License Type</th>
<th>Library Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

CAL Implementation Processing Architecture
------------------------------------------

This section documents the operating systems, wire protocols,
transports, middleware packages, and message security implementations
provided by this implementation of the Platform.

### Language-Specific CAL

This section documents configuration, externalizer implementation and
operational attributes for all Language-Specific CALs identified in
Table 7.1-1, CAL Versions Available.

#### \[CAL Identifier\]

The following sub-sections document the CAL configuration, externalizer
implementation(s) and operational attributes for the \[CAL Identifier\].

##### \[CAL Identifier\] CAL Configuration

This section documents specific details required for Language-Specific
CAL configuration.

##### \[CAL Identifier\] CAL Externalizer Implementation

This section documents specific details required for Externalizer
implementation, if an Externalizer is provided as shown in Table 7.3-1,
CAL Externalizer Implementation.

<span id="_Toc219294676" class="anchor"></span>Table 7.3-1 CAL
Externalizer Version Information

<table>
<thead>
<tr class="header">
<th>CAL Externalizer Name</th>
<th>CAL Identifier</th>
<th>Encoding</th>
<th>Schema Version</th>
<th>CAL API (OMS Version)</th>
<th>Vendor</th>
<th>Externalizer Version</th>
<th>Reference Documentation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

##### \[CAL Identifier\] CAL Operational Attributes

This section documents the operational attributes of each supported CAL.
These attributes are captured in a Supported Operational Attribute
Configuration (SOAC) table. Since a CAL can support different
configurations of operational attributes, the Platform should specify
the supported values of these operational attributes in one or more
tables, as needed. The first configuration is shown in Table 7.3-2,
SOAC-1.

<span id="_Toc219294677" class="anchor"></span>Table 7.3-2 SOAC-1

<table>
<thead>
<tr class="header">
<th>SOAC-1</th>
<th></th>
<th></th>
<th></th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Operational Attribute</td>
<td>Value</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>CAL READER</td>
<td>DEFAULT</td>
<td>MIN</td>
<td>MAX</td>
<td>Notes</td>
</tr>
<tr class="odd">
<td>Queue Length</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Filter Time</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Expiration Time</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Overflow Action</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Reliability</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>CAL WRITER</td>
<td>DEFAULT</td>
<td>MIN</td>
<td>MAX</td>
<td>Notes</td>
</tr>
<tr class="odd">
<td>Queue Length</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Overflow Action</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Reliability</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Language Agnostic CAL

This section documents access and configuration information for all
Language-Agnostic CALs identified in Table 7.1-1, CAL Versions
Available.

#### \[CAL Identifier\]

The following sub-sections document the Language-Agnostic CAL access and
configuration information for the \[CAL Identifier\].

<span id="_Toc219294678" class="anchor"></span>Table 7.3-3
Language-Agnostic CAL Access Information

<table>
<thead>
<tr class="header">
<th>CAL Identifier</th>
<th>Endpoint URI</th>
<th>Protocol</th>
<th>Sub-protocol Versions</th>
<th>Message Formats</th>
<th>Schema</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

##### \[CAL Identifier\] Language-Agnostic CAL Configuration

This section documents specific details required for CAL configuration.

Virtualization Environments
===========================

This section identifies and describes any virtual environments on the
Platform and their capabilities to be extended and/or reconfigured.

Virtualization Environment - &lt;&lt;Name&gt;&gt;
-------------------------------------------------

This section documents a virtualization environment within the OMS
Platform.

### Processor Virtualization

This section identifies if the virtualization approach is hardware
assisted or if a full virtualization approach is used. This section also
identifies the processor architectures that can be virtualized.

### Memory Virtualization

This section identifies the memory virtualization approach and
capabilities. This includes processor RAM, local file storage, and
network file storage.

### Network Virtualization

This section identifies the virtual network capabilities provided by the
virtual environment.

### Virtualization Environment Deployment

This section describes how the virtualized environment is deployed on
the Platform.

### Service Deployment

This section describes how a Service is deployed and managed in the
virtual environment, including any requirements placed on a Service to
run in the environment and for using a CAL or Data Transfers.

### Time

This section documents how time synchronization is supported by the
virtual environment.

### Virtualization Environment Configuration

This section documents the virtualized environment configuration
details.

Configuration Data
==================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

This section identifies all of the configuration data for the OMS
Platform as shown in Table 9.0-1, Configuration Data.

<span id="_Toc219294679" class="anchor"></span>Table 9.0-1 Configuration
Data

<table>
<thead>
<tr class="header">
<th>Configuration Data Identifier</th>
<th>File Pathname</th>
<th>File Format</th>
<th>Method or Tool for Modification</th>
<th>Other Details and Cross References</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Special Signals
===============

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section identifies how any special signals are provided or
provisioned for by the Platform as defined in the OMS Standard,
OMSC-STD-001, “Special Signals.”

Provided Special Signals
------------------------

This section lists the special signals that are provided by the OMS
Platform as identified in "Special Signals" of the OMS Standard,
OMSC-STD-001 as shown in Table 10.1-1, Provided Special Signals.

<span id="_Toc219294680" class="anchor"></span>Table 10.1-1 Provided
Special Signals

<table>
<thead>
<tr class="header">
<th>Signal Identification</th>
<th>Hardware Implementation Details</th>
<th>Software Interfaces</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Provisioned Special Signals
---------------------------

This section lists the special signals that are provisioned by the OMS
Platform as identified in "Special Signals" of the OMS Standard,
OMSC-STD-001 as shown in Table 10.2-1, Provisioned Special Signals.

<span id="_Toc219294681" class="anchor"></span>Table 10.2-1 Provisioned
Special Signals

<table>
<thead>
<tr class="header">
<th>Signal Identification</th>
<th>Signal Provisioning Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

Cybersecurity Posture
=====================

This section identifies the cybersecurity posture of the Platform.

Cyber Survivability Attributes (CSAs)
-------------------------------------

This section identifies the CSAs applicable to the Platform.

### Prevent CSAs

This section identifies and documents the System Survivability Key
Performance Parameter (KPP) Prevent CSAs implementation for the
Platform. Table 11.1-1 identifies the System Survivability KPP Prevent
CSAs applicable to the Platform.

<span id="_Toc219294682" class="anchor"></span>Table 11.1-1 Applicable
System Survivability KPP Prevent CSAs

<table>
<thead>
<tr class="header">
<th>CSA-01</th>
<th>CSA-02</th>
<th>CSA-03</th>
<th>CSA-04</th>
<th>CSA-05</th>
<th>CSA-06</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Mitigate CSAs

This section identifies and documents the System Survivability KPP
Mitigate CSAs implementation for the Platform. Table 11.1-2 identifies
the System Survivability KPP Mitigate CSAs applicable to the Platform.

<span id="_Toc219294683" class="anchor"></span>Table 11.1-2 Applicable
System Survivability KPP Mitigate CSAs

<table>
<thead>
<tr class="header">
<th>CSA-07</th>
<th>CSA-08</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Recover CSA

This section identifies and documents the System Survivability KPP
Recover CSA implementation for the Platform.

### Adapt CSA

This section identifies and documents the System Survivability KPP Adapt
CSA implementation for the Platform.

Security Addendum
=================

Proprietary Notice: The Security Addendum reference in this section is a
non-proprietary document. The Security Addendum may contain references
to external documents that may be proprietary.

This section identifies the Security Addendum document(s).

Appendix A Acronyms And Abbreviations
=====================================

This section lists the abbreviations and acronyms used in this document
not a copy of the OMS lexicon as shown in Table A.0-1, List of Acronyms
and Abbreviation Definitions

<span id="_Toc219294684" class="anchor"></span>Table A.0-1 List of
Acronym and Abbreviation Definitions

<table>
<thead>
<tr class="header">
<th>Acronym/Abbreviation</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ASB</td>
<td>Abstract Service Bus</td>
</tr>
<tr class="even">
<td>CAL</td>
<td>Critical Abstraction Layer</td>
</tr>
<tr class="odd">
<td>CSA</td>
<td>Cyber Survivability Attribute</td>
</tr>
<tr class="even">
<td>CSRC</td>
<td>Cyber Survivability Risk Category</td>
</tr>
<tr class="odd">
<td>ICD</td>
<td>Interface Control Document</td>
</tr>
<tr class="even">
<td>KPP</td>
<td>Key Performance Parameter</td>
</tr>
<tr class="odd">
<td>OACWG</td>
<td>Open Architecture Collaborative Working Group</td>
</tr>
<tr class="even">
<td>OAM</td>
<td>Open Architecture Management</td>
</tr>
<tr class="odd">
<td>OCE</td>
<td>Open Computing Environment</td>
</tr>
<tr class="even">
<td>OMS</td>
<td>Open Mission Systems</td>
</tr>
<tr class="odd">
<td>SOAC</td>
<td>Supported Operational Attribute Configuration</td>
</tr>
<tr class="even">
<td>UCI</td>
<td>Universal C2 Interface</td>
</tr>
</tbody>
</table>

This page is intentionally left blank.

Appendix B Glossary
===================

This section lists the terms used in this document as shown in Table
B.0-1, List of Term Definitions

<span id="_Toc219294685" class="anchor"></span>Table B.0-1 List of Term
Definitions

<table>
<thead>
<tr class="header">
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

This page is intentionally left blank

Appendix C Message Details
==========================

This appendix consists of one or more spreadsheet workbooks with a
separate tab for each **SystemTimeAtReference, PositionReport,** and/or
**PositionReportDetailed** message use based on each function’s input
and output messages.
