Open Mission Systems (OMS)

Definition And Documentation (D&D)

Subsystem Description Document (SDD) Template

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

&lt;REQUIRED: Subsystem Description Document Title&gt;

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

This Subsystem Description Document (SDD) complies with the Subsystem
Description Document (SDD) Template, OMSC-TMP-002, Revision M, dated 22
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

[1.2 OMS Subsystem Compliance Pattern
1](#oms-subsystem-compliance-pattern)

[2 Service Contract 2](#service-contract)

[3 Subsystem Specification Identification and Reference
3](#subsystem-specification-identification-and-reference)

[4 Licenses 4](#licenses)

[5 Subsystem Libraries Not Defined In The Service Contract
5](#subsystem-libraries-not-defined-in-the-service-contract)

[6 Subsystem Time Synchronization 6](#subsystem-time-synchronization)

[7 Service and Subsystem Startup 7](#service-and-subsystem-startup)

[8 Subsystem External Interfaces 8](#subsystem-external-interfaces)

[8.1 Open Ports and Protocols 8](#open-ports-and-protocols)

[9 Subsystem Data Transfer 9](#subsystem-data-transfer)

[9.1 Data Storage 9](#data-storage)

[9.1.1 Data Storage Access Controls 9](#data-storage-access-controls)

[9.1.2 Data Storage Confidentiality Mechanisms
10](#data-storage-confidentiality-mechanisms)

[9.1.3 Data Storage Integrity Mechanisms
10](#data-storage-integrity-mechanisms)

[9.2 Data Transfer Confidentiality Mechanisms for Data Storage
10](#data-transfer-confidentiality-mechanisms-for-data-storage)

[9.3 Data Transfer Integrity Mechanisms for Data Storage
10](#data-transfer-integrity-mechanisms-for-data-storage)

[9.4 Data Transfer Configuration for Data Storage
11](#data-transfer-configuration-for-data-storage)

[10 Subsystem Internal Interfaces 12](#subsystem-internal-interfaces)

[11 Open Computing Environment (OCE)
13](#open-computing-environment-oce)

[11.1 OCE Processor Types, Operating Systems, and Configuration
13](#oce-processor-types-operating-systems-and-configuration)

[11.2 General Environment 13](#general-environment)

[11.2.1 Build Environment and Tool Chain
13](#build-environment-and-tool-chain)

[11.2.2 Isolation Layer 13](#isolation-layer)

[11.2.3 Time 13](#time)

[11.3 Java Environment 13](#java-environment)

[11.3.1 Build Environment and Tool Chain
13](#build-environment-and-tool-chain-1)

[11.3.2 Java Data Transfer 13](#java-data-transfer)

[11.3.3 Time 13](#time-1)

[11.4 Virtualization Environment 14](#virtualization-environment)

[11.4.1 Hypervisor 14](#hypervisor)

[11.4.1.1 Processor 14](#processor)

[11.4.1.2 Memory Virtualization 14](#memory-virtualization)

[11.4.1.3 Network Virtualization 14](#network-virtualization)

[11.4.2 Time 14](#time-2)

[11.5 Service Deployment 14](#service-deployment)

[12 Test Procedures & Data 15](#test-procedures-data)

[13 Cybersecurity Posture 16](#cybersecurity-posture)

[13.1 Cyber Survivability Attributes (CSAs)
16](#cyber-survivability-attributes-csas)

[13.1.1 Prevent CSAs 16](#prevent-csas)

[13.1.2 Mitigate CSAs 16](#mitigate-csas)

[13.1.3 Recover CSA 16](#recover-csa)

[13.1.4 Adapt CSA 16](#adapt-csa)

[14 Security Addendum 17](#security-addendum)

[A Appendix A Acronyms and Abbreviations
18](#appendix-a-acronyms-and-abbreviations)

[B Appendix B Glossary 20](#appendix-b-glossary)

List of Figures

[Figure 1.0-1 SDD Document Tree 1](#_Toc219295059)

This page is intentionally left blank.

List of Tables

[Table 1.1-1 Reference Documents 1](#_Toc219295060)

[Table 2.0-1 Service Contracts 2](#_Toc219295061)

[Table 3.0-1 Subsystem Specifications 3](#_Toc219295062)

[Table 4.0-1 Subsystem Licenses 4](#_Toc219295063)

[Table 5.0-1 Additional Subsystem Libraries 5](#_Toc219295064)

[Table 6.0-1 Time Sync 6](#_Toc219295065)

[Table 8.1-1 OMS Subsystem Open Ports and Protocols 8](#_Toc219295066)

[Table 8.1-2 OMS Subsystem Product/Data and Data Transfer Servers
8](#_Toc219295067)

[Table 9.1-1 Subsystem Data Storage Details 9](#_Toc219295068)

[Table 9.1-2 Data Storage Access Control Mechanisms 9](#_Toc219295069)

[Table 9.1-3 Data Storage Confidentiality 10](#_Toc219295070)

[Table 9.1-4 Data Storage Integrity 10](#_Toc219295071)

[Table 9.2-1 Data Transfer Confidentiality Mechanisms
10](#_Toc219295072)

[Table 9.3-1 Data Transfer Integrity Mechanisms 10](#_Toc219295073)

[Table 9.4-1 Subsystem Data Transfer Configuration 11](#_Toc219295074)

[Table 10.0-1 Subsystem Internal ICDs 12](#_Toc219295075)

[Table 13.1-1 Applicable System Survivability KPP Prevent CSAs
16](#_Toc219295076)

[Table 13.1-2 Applicable System Survivability KPP Mitigate CSAs
16](#_Toc219295077)

[Table A.0-1 List of Acronyms and Abbreviation Definitions
18](#_Toc219295078)

[Table B.0-1 List of Term Definitions 20](#_Toc219295079)

This page is intentionally left blank.

Overview
========

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section includes a summary of key capabilities and functions of the
Subsystem.

Figure 1.0-1, SDD Document Tree, illustrates the document tree showing
references associated to this Subsystem.

&lt;&lt;INSERT FIGURE HERE. SEE ACCOMPANYING INSTRUCTIONS FOR AN
EXAMPLE&gt;&gt;

<span id="_Toc219295059" class="anchor"></span>Figure 1.0-1 SDD Document
Tree

References
----------

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

Table 1.1-1, Reference Documents, lists all the referenced documents
that are required to support the integration of this Subsystem.

<span id="_Toc219295060" class="anchor"></span>Table 1.1-1 Reference
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
<td>OMSC-TMP-002</td>
<td>Subsystem Description Document (SDD) Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>

OMS Subsystem Compliance Pattern
--------------------------------

This section identifies the compliance pattern for this Subsystem.

Service Contract
================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

Table 2.0-1, Service Contracts, identifies and refers to the Service
Contract for the Subsystem.

<span id="_Toc219295061" class="anchor"></span>Table 2.0-1 Service
Contracts

<table>
<thead>
<tr class="header">
<th>Title</th>
<th>Reference</th>
<th>Date</th>
<th>Revision</th>
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

Subsystem Specification Identification and Reference
====================================================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

Table 3.0-1, Subsystem Specifications, references the associated
Subsystem requirements specifications.

<span id="_Toc219295062" class="anchor"></span>Table 3.0-1 Subsystem
Specifications

<table>
<thead>
<tr class="header">
<th>Title</th>
<th>Reference</th>
<th>Date</th>
<th>Revision</th>
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

Licenses
========

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

Table 4.0-1, Subsystem Licenses, documents the licenses required by the
Subsystem to integrate with the Platform.

<span id="_Toc219295063" class="anchor"></span>Table 4.0-1 Subsystem
Licenses

<table>
<thead>
<tr class="header">
<th>License Description</th>
<th>Provider</th>
<th>Product</th>
<th>Version</th>
<th>Type</th>
<th>Purpose</th>
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

Subsystem Libraries Not Defined In The Service Contract
=======================================================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

Table 5.0-1, Additional Subsystem Libraries, documents libraries used by
the Subsystem that are not defined in the Service Contracts.

<span id="_Toc219295064" class="anchor"></span>Table 5.0-1 Additional
Subsystem Libraries

<table>
<thead>
<tr class="header">
<th>Library Name</th>
<th>Provider</th>
<th>Version</th>
<th>Purpose</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Subsystem Time Synchronization
==============================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section should include Special Signal references to any OMS
Standard time reference signals used that are specified in OMSC-STD-001,
OMS Standard, Time Reference Signals section. Table 6.0-1, Time Sync,
identifies and describes the method(s) used for time synchronization.

<span id="_Toc219295065" class="anchor"></span>Table 6.0-1 Time Sync

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

Service and Subsystem Startup
=============================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section documents the location, identity, and means for modifying
any configuration data required for OMS startup for a Service or
Subsystem.

Subsystem External Interfaces
=============================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

This section identifies and describes the Subsystem interfaces between
the Subsystem and the Platform ASB.

Open Ports and Protocols
------------------------

All listening ports, specific to the Subsystem, that are open
(accessible to the ASB) are listed in Table 8.1-1, OMS Subsystem Open
Ports and Protocols. Ports and protocols of Services and Isolators are
documented in their respective Service Contracts, not in this table. Any
ports not listed are assumed closed.

<span id="_Toc219295066" class="anchor"></span>Table 8.1-1 OMS Subsystem
Open Ports and Protocols

<table>
<thead>
<tr class="header">
<th><p>Port</p>
<p>(TCP/UDP)</p></th>
<th>Protocol</th>
<th>Process/Service</th>
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
</tr>
</tbody>
</table>

Table 8.1-2, OMS Subsystem Product/Data and Data Transfer Servers,
contains information on the products/data being sent or received by the
Data Transfer server.

<span id="_Toc219295067" class="anchor"></span>Table 8.1-2 OMS Subsystem
Product/Data and Data Transfer Servers

<table>
<thead>
<tr class="header">
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
</tr>
</tbody>
</table>

Subsystem Data Transfer
=======================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

Data Storage
------------

This section identifies the Subsystem data storage capability as shown
in Table 9.1-1, Subsystem Data Storage Details.

<span id="_Toc219295068" class="anchor"></span>Table 9.1-1 Subsystem
Data Storage Details

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

### Data Storage Access Controls

Table 9.1-2, Data Storage Access Control Mechanisms, details the data
storage access controls.

<span id="_Toc219295069" class="anchor"></span>Table 9.1-2 Data Storage
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

This section identifies the specific confidentiality mechanisms (e.g.,
host-based firewall) and use of encryption within the Data Storage as
shown in Table 9.1-3, Data Storage Confidentiality.

<span id="_Toc219295070" class="anchor"></span>Table 9.1-3 Data Storage
Confidentiality

<table>
<thead>
<tr class="header">
<th>Data Store Address</th>
<th>Data Store Label</th>
<th>Protected Data</th>
<th><p>Confidentiality</p>
<p>Mechanism</p></th>
<th>Implementation Details</th>
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

### Data Storage Integrity Mechanisms

This section identifies the specific integrity mechanisms within the
Data Storage as shown in Table 9.1-4, Data Storage Integrity.

<span id="_Toc219295071" class="anchor"></span>Table 9.1-4 Data Storage
Integrity

<table>
<thead>
<tr class="header">
<th><p>Data Store</p>
<p>Address</p></th>
<th>Data Store Label</th>
<th>Protected Data</th>
<th><p>Integrity</p>
<p>Mechanism</p></th>
<th>Implementation Details</th>
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

Data Transfer Confidentiality Mechanisms for Data Storage
---------------------------------------------------------

This section identifies the confidentiality mechanisms the Subsystem
supports for data transfers to the Subsystem data storage as shown in
Table 9.2-1, Data Transfer Confidentiality Mechanisms.

<span id="_Toc219295072" class="anchor"></span>Table 9.2-1 Data Transfer
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

Data Transfer Integrity Mechanisms for Data Storage
---------------------------------------------------

This section identifies the integrity mechanisms the Subsystem supports
for data transfers to the Subsystem data storage as shown in Table
9.3-1, Data Transfer Integrity Mechanisms.

<span id="_Toc219295073" class="anchor"></span>Table 9.3-1 Data Transfer
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

Data Transfer Configuration for Data Storage
--------------------------------------------

This section identifies the Data Transfer methods provided by the
Subsystem and the configuration details associated with the Data
Transfer methods to the Subsystem data storage as shown in Table 9.4-1,
Subsystem Data Transfer Configuration.

<span id="_Toc219295074" class="anchor"></span>Table 9.4-1 Subsystem
Data Transfer Configuration

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

Subsystem Internal Interfaces
=============================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

Table 10.0-1, Subsystem Internal ICDs, describes the non-OMS subsystem
internal interfaces that are exposed when the Subsystem is installed in
the Mission Package.

<span id="_Toc219295075" class="anchor"></span>Table 10.0-1 Subsystem
Internal ICDs

<table>
<thead>
<tr class="header">
<th>Title</th>
<th>Reference</th>
<th>Date</th>
<th>Revision</th>
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

Open Computing Environment (OCE)
================================

Proprietary Notice: References to external documents that provide for
the data in this section refer only to non-proprietary documents.

This section documents the Subsystem’s OCE OMS mission processing
architecture and describes specific tool chains for building in the OCE
environment.

OCE Processor Types, Operating Systems, and Configuration
---------------------------------------------------------

This section documents the processor architecture/type, processor
memory, processor quantity, and operating systems (type and 32 or 64
bit) for each processor in the OCE.

General Environment
-------------------

This section documents the general environment provided by the OCE.

### Build Environment and Tool Chain

This section documents the specific build environment for an OCE.

### Isolation Layer

This section documents the implemented Façade interfaces for this OCE
provided by this Subsystem as defined in the OMS OS Façade
Specification.

### Time

This section documents how time synchronization is supported by the OCE.

Java Environment
----------------

This section documents the specific Java environment provided by the
Java-based OCE.

### Build Environment and Tool Chain

This section documents the specific build environment for a Java-based
OCE.

### Java Data Transfer

This section documents the C/C++ libraries (if any) that are provided as
part of the Java-based OCE and that the Java environment is reliant upon
in order to perform data transfer operations.

### Time

This section documents how time synchronization is supported by the
Java-based OCE.

Virtualization Environment
--------------------------

This section identifies if there is a Virtual Machine (VM)-based
processing architecture on the Subsystem.

### Hypervisor

This section documents the specific hypervisor provided by the
virtualization-based OCE which includes the following:

#### Processor

This section identifies if the virtualization approach is hardware
assisted or if a full virtualization approach is used.

#### Memory Virtualization

This section identifies the memory virtualization approach.

#### Network Virtualization

This section identifies the virtual network for each deployed virtual
appliance.

### Time

This section documents how time synchronization is supported by the VM
OCE.

Service Deployment
------------------

This section documents how Services are deployed and managed within the
OCE.

Test Procedures & Data
======================

Proprietary Notice: References to external documents that provide for
the data in this section may refer to proprietary documents.

This section identifies relevant available test procedures that were
used to integrate, verify and/or assess OMS compliance of the Subsystem.

Cybersecurity Posture
=====================

This section identifies the cybersecurity posture of the Subsystem.

Cyber Survivability Attributes (CSAs) 
-------------------------------------

This section identifies the CSAs applicable to the Subsystem.

### Prevent CSAs

This section identifies and documents the System Survivability Key
Performance Parameter (KPP) Prevent CSAs implementation for the
Subsystem. Table 13.1-1 identifies the System Survivability KPP Prevent
CSAs applicable to the Subsystem.

<span id="_Toc219295076" class="anchor"></span>Table 13.1-1 Applicable
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
Mitigate CSAs implementation for the Subsystem. Table 13.1-2 identifies
the System Survivability KPP Mitigate CSAs applicable to the Subsystem.

<span id="_Toc219295077" class="anchor"></span>Table 13.1-2 Applicable
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
Recover CSA implementation for the Subsystem.

### Adapt CSA

This section identifies and documents the System Survivability KPP Adapt
CSA implementation for the Subsystem.

Security Addendum
=================

Proprietary Notice: The Security Addendum reference in this section is a
non-proprietary document. The Security Addendum may contain references
to external documents that may be proprietary.

This section identifies the Security Addendum document(s).

Appendix A Acronyms and Abbreviations
=====================================

This section lists the abbreviations and acronyms used in this document
not a copy of the OMS lexicon as shown in Table A.0-1, List of Acronyms
and Abbreviation Definitions.

<span id="_Toc219295078" class="anchor"></span>Table A.0-1 List of
Acronyms and Abbreviation Definitions

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
<td>CSA</td>
<td>Cyber Survivability Attribute</td>
</tr>
<tr class="odd">
<td>KPP</td>
<td>Key Performance Parameter</td>
</tr>
<tr class="even">
<td>OACWG</td>
<td>Open Architecture Collaborative Working Group</td>
</tr>
<tr class="odd">
<td>OCE</td>
<td>Open Computing Environment</td>
</tr>
<tr class="even">
<td>OMS</td>
<td>Open Mission Systems</td>
</tr>
</tbody>
</table>

This page is intentionally left blank

Appendix B Glossary
===================

This section lists the terms used in this document as shown in Table
B.0-1, List of Term Definitions.

<span id="_Toc219295079" class="anchor"></span>Table B.0-1 List of Term
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
