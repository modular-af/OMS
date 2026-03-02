Open Mission Systems (OMS)

Definition And Documentation (D&D)

Subsystem Description Document (SDD) Template Instructions

<img src="media/image1.jpeg" style="width:2.775in;height:1.73333in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

This Subsystem Description Document (SDD) Template Instructions
describes how the SDD Template is filled out. The General Template
Instructions provides a description of how this Template Instructions
document is used in filling out the corresponding associated SDD
Template.

This Subsystem Description Document (SDD) Template Instructions is
aligned with the Subsystem Description Document (SDD) Template,
OMSC-TMP-002, Revision M, dated 22 January 2026.

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
<td>M</td>
<td>22 January 2026</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

This page is intentionally left blank.

Table of Contents

[1 Overview 4](#overview)

[1.1 References 6](#references)

[1.2 OMS Subsystem Compliance Pattern
6](#oms-subsystem-compliance-pattern)

[2 Service Contract 9](#service-contract)

[3 Subsystem Specification Identification and Reference
10](#subsystem-specification-identification-and-reference)

[4 Licenses 11](#licenses)

[5 Subsystem Libraries Not Defined In The Service Contract
12](#subsystem-libraries-not-defined-in-the-service-contract)

[6 Subsystem Time Synchronization 13](#subsystem-time-synchronization)

[7 Service and Subsystem Startup 14](#service-and-subsystem-startup)

[8 Subsystem External Interfaces 15](#subsystem-external-interfaces)

[8.1 Open Ports and Protocols 18](#open-ports-and-protocols)

[9 Subsystem Data Transfer 20](#subsystem-data-transfer)

[9.1 Data Storage 20](#data-storage)

[9.1.1 Data Storage Access Controls 21](#data-storage-access-controls)

[9.1.2 Data Storage Confidentiality Mechanisms
22](#data-storage-confidentiality-mechanisms)

[9.1.3 Data Storage Integrity Mechanisms
23](#data-storage-integrity-mechanisms)

[9.2 Data Transfer Confidentiality Mechanisms for Data Storage
23](#data-transfer-confidentiality-mechanisms-for-data-storage)

[9.3 Data Transfer Integrity Mechanisms for Data Storage
24](#data-transfer-integrity-mechanisms-for-data-storage)

[9.4 Data Transfer Configuration for Data Storage
25](#data-transfer-configuration-for-data-storage)

[10 Subsystem Internal Interfaces 26](#subsystem-internal-interfaces)

[11 Open Computing Environment (OCE)
27](#open-computing-environment-oce)

[11.1 OCE Processor Types, Operating Systems, and Configuration
27](#oce-processor-types-operating-systems-and-configuration)

[11.2 General Environment 27](#general-environment)

[11.2.1 Build Environment and Tool Chain
27](#build-environment-and-tool-chain)

[11.2.2 Isolation Layer 27](#isolation-layer)

[11.2.3 Time 27](#time)

[11.3 Java Environment 27](#java-environment)

[11.3.1 Build Environment and Tool Chain
28](#build-environment-and-tool-chain-1)

[11.3.2 Java Data Transfer 28](#java-data-transfer)

[11.3.3 Time 28](#time-1)

[11.4 Virtualization Environment 28](#virtualization-environment)

[11.4.1 Hypervisor 28](#hypervisor)

[11.4.1.1 Processor 28](#processor)

[11.4.1.2 Memory Virtualization 28](#memory-virtualization)

[11.4.1.3 Network Virtualization 29](#network-virtualization)

[11.4.2 Time 29](#time-2)

[11.5 Service Deployment 29](#service-deployment)

[12 Test Procedures & Data 30](#test-procedures-data)

[13 Cybersecurity Posture 31](#cybersecurity-posture)

[13.1 Cyber Survivability Attributes (CSAs)
31](#cyber-survivability-attributes-csas)

[13.1.1 Prevent CSAs 31](#prevent-csas)

[13.1.2 Mitigate CSAs 32](#mitigate-csas)

[13.1.3 Recover CSA 32](#recover-csa)

[13.1.4 Adapt CSA 33](#adapt-csa)

[14 Security Addendum 34](#security-addendum)

[A Appendix A Acronyms and Abbreviations
35](#appendix-a-acronyms-and-abbreviations)

[B Appendix B Glossary 36](#appendix-b-glossary)

List of Figures

[Figure 1.0-1 SDD Document Tree 5](#_Toc219295202)

[Figure 1.2-1 Standalone Subsystem 7](#_Toc256000047)

[Figure 1.2-2 Platform-Hosted OMS Adaptation 8](#_Toc256000048)

[Figure 8.0-1 Plug Connection Diagram 15](#_Toc256000049)

[Figure 8.0-2 OMS Data Exchanges with a Platform-Hosted OMS Adapter
17](#_Toc256000050)

This page is intentionally left blank.

List of Tables

[Table 0.0-1 OMS D&D Documents 2](#_Toc219295207)

[Feedback Form Table 3](#_Toc219295208)

[Table 1.1-1 Reference Documents 6](#_Toc219295209)

[Table 2.0-1 Service Contract 9](#_Toc219295210)

[Table 3.0-1 Subsystem Specifications 10](#_Toc219295211)

[Table 4.0-1 Subsystem Licenses 11](#_Toc219295212)

[Table 5.0-1 Additional Subsystem Libraries 12](#_Toc219295213)

[Table 6.0-1 Time Sync 13](#_Toc219295214)

[Table 8.1-1 OMS Subsystem Open Ports and Protocols 18](#_Toc219295215)

[Table 8.1-2 OMS Subsystem Product/Data and Data Transfer Servers
19](#_Toc219295216)

[Table 9.1-1 Subsystem Data Storage Details 21](#_Toc219295217)

[Table 9.1-2 Data Storage Access Control Mechanisms 22](#_Toc219295218)

[Table 9.1-3 Data Storage Confidentiality 23](#_Toc219295219)

[Table 9.1-4 Data Storage Integrity 23](#_Toc219295220)

[Table 9.2-1 Data Transfer Confidentiality Mechanisms
24](#_Toc219295221)

[Table 9.3-1 Data Transfer Integrity Mechanisms 24](#_Toc219295222)

[Table 9.4-1 Subsystem Data Transfer Configuration 25](#_Toc219295223)

[Table 10.0-1 Subsystem Internal ICDs 26](#_Toc219295224)

[Table 13.1-1 Applicable System Survivability KPP Prevent CSAs
31](#_Toc219295225)

[Table 13.1-2 Applicable System Survivability KPP Mitigate CSAs
32](#_Toc219295226)

[Table A.0-1 List of Acronyms and Abbreviation Definitions
35](#_Toc219295227)

[Table B.0-1 List of Term Definitions 36](#_Toc219295228)

This page is intentionally left blank.

General Template Instructions

This document, Subsystem Description Document (SDD) Template
Instructions, OMSC-INS-002, provides information on how to fill in
required information in the SDD Template, OMSC-TMP-002. The outline of
the SDD Template Instructions is one-to-one aligned with each section in
the SDD Template. The green text in each section of this SDD Template
Instructions document should be used as guidance to fill out the
corresponding section in the SDD Template. Green text in the SDD
Template is considered guidance only and should be removed to reflect
your Subsystem. NOTE: The first page of the SDD Template document is for
Open Mission Systems (OMS) purposes only and should be removed prior to
the release of the completed Template.

A Subsystem provider should save the SDD Template using an appropriate
unique filename. The Subsystem provider should add an appropriate
document number, revision history and document date for configuration
management of program specific information. The distribution statement
should be filled out based on the program specific restrictions, and at
a minimum should be Distribution Statement A. If the contents of the
document require a higher restriction, the appropriate distribution
statement should be updated as needed. Green text in the SDD Template
represents guidance for the creation of the SDD. Green text should not
remain in the completed SDD and should be replaced on the Cover page, in
the Abstract, in the Revision Record and all applicable sections defined
in the SDD Template.

This document contains only non-proprietary information. Referenced
documents may contain proprietary information except in sections noted
otherwise. Proprietary information included in referenced documents
should include data transfer mechanisms and data structures, but should
not include proprietary data content. Classification of the SDD should
be based on the contents of the document.

Modify the sections in the template using the following guidelines:

1.  **Existing black text is required and should not be deleted.**

2.  **If a section is not applicable**, keep that section heading and
    add “Not Applicable” with a rationale for why that section is not
    applicable on a new line. For figures and tables below the not
    applicable section, replace figures with “Figure not applicable” and
    enter “N/A” in the first empty cell for tables.

The rationale behind not deleting table captions, figure captions, or
sections is to preserve section references and table/figure identifiers
to maintain traceability within the document and between documents. For
example, the Security Control Traceability Matrix (SCTM) traces a
security control to a specific document template, section and/or table
identifier.

1.  **Maintain existing table column headers.**

Tables can be further modified (e.g., adding additional columns when
applicable) but the original structure of existing tables should be
preserved.

1.  **Delete all green guidance text in the section, including green
    text added in table rows provided for exemplar purposes only.**

2.  **If additional tables or figure are added,** the table/figure
    caption must follow the third level numbering system. Existing,
    default captions already in the template are numbered against
    headings at level 2 (e.g., Under Section 1, the first table in the
    section is numbered Table 1.0-1. Under Section 2.4.1, the second
    table in the section is numbered Table 2.4-2). Newly added
    tables/figures should be numbered against headings at level 3 (e.g.,
    Under Section 1, the first newly added table in the section is
    numbered Table 1.0.0-1. Under Section 2.4.1, the second newly added
    table in the section is numbered 2.4.1-2). This results in
    preserving the numbering of the original tables.

Ensure correct table and figure caption styles are applied so they
appear in the List of Tables and List of Figures. Use the “TableCaption”
Style for table captions and “FigureCaption” Style for figure captions.

All documents referenced within the Subsystem Description Document must
include a document reference number with release dates and be included
in the compliance package deliverable.

The documents listed in Table 0.0-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219295207" class="anchor"></span>Table 0.0-1 OMS D&D
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
<td>OMSC-STD-001</td>
<td>OMS Standard Version 2.5</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-STD-002</td>
<td>Abbreviations and Glossary</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>

OMS Documentation Feedback Form

This form gives customers using the OMS documentation (Mission Package
Worksheet, Mission Package Description Document, Platform Description
Document, Subsystem Description Document and Service Contract) a venue
to submit feedback to the OACWG. Comments should identify errors in the
documentation or highlight areas of confusion.

<span id="_Toc219295208" class="anchor"></span>Feedback Form Table

<table>
<tbody>
<tr class="odd">
<td>Name of Commenter</td>
<td>Contact Information (Email/Phone)</td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td>Applicable File Name</td>
<td>Section, Figure, Table</td>
</tr>
<tr class="odd">
<td></td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Comment Details (i.e., Description of Issue and Proposed Updates (if applicable))</td>
<td></td>
</tr>
<tr class="even">
<td></td>
<td></td>
</tr>
</tbody>
</table>

Completed feedback forms may be submitted in one of two ways:

-   Upload the completed form to the Submit Requests folder on Pydio
    here: <span
    class="underline">https://pydio.dle.afrl.af.mil/ws-ase-group-1/OMS\_UCI/%2001\_Submitting%20a%20Change%20Request/Submit%20Requests</span>

-   Submit the completed form to the User Support Group at <span
    class="underline">oam-cwg-usersupport@rlist.app.ray.com</span>

Overview
========

This section includes a summary of key capabilities and functions of the
Subsystem.

It should state if the Subsystem is a standalone Subsystem or if it uses
a Platform-hosted Adapter.

Figure 1.0-1, SDD Document Tree, illustrates the document tree showing
references associated to this Subsystem.

The Open Mission Systems (OMS) Subsystem Description Document (SDD) is
the top-level document in the set of documents which specifies the key
aspects, interfaces and capabilities \[this should include all the
capabilities of the Subsystem\] of an OMS Subsystem.

This section may include a document tree that allows a Customer a quick
reference for the documents that are referenced in this document. An
example is shown in Figure 1.0-1, SDD Document Tree. An SDD is required
of all OMS Subsystems to be compliant and is the primary source of
documentation describing an OMS Subsystem. The SDD objectively describes
the “as built” configuration and capabilities of an OMS Subsystem, but
will evolve during the life-cycle of an OMS Subsystem’s development.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE. INCLUDE AN APPROPRIATE
FIGURE IF APPLICABLE. IF NOT APPLICABLE, REPLACE THE FIGURE WITH “FIGURE
NOT APPLICABLE” &gt;&gt;

<img src="media/image2.png" style="width:6.5in;height:6.48333in" />

<span id="_Toc219295202" class="anchor"></span>Figure 1.0-1 SDD Document
Tree

This document contains only non-proprietary information. Referenced
documents may contain proprietary information except in sections noted
otherwise. Proprietary information included in referenced documents
should include data transfer mechanisms and data structures, but should
not include proprietary data content. Classification of the SDD should
be based on the contents of the document.

References
----------

Table 1.1-1, Reference Documents, lists all the referenced documents
that are required to support the integration of this Subsystem.

This section should include the current OMS Standard for basis of
compliance, internal and external ICDs, and other important documents or
standards. Table 1.1-1, Reference Documents, lists all the required
reference documents. This section should also provide overview
description for each program/Subsystem specific document referenced in
this section.

<span id="_Toc219295209" class="anchor"></span>Table 1.1-1 Reference
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
<tr class="even">
<td>OMSC-TMP-003</td>
<td>Service Contract Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>Add rows as required.</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

OMS Subsystem Compliance Pattern
--------------------------------

This section identifies the compliance pattern for this Subsystem.

An OMS Subsystem, and its accompanying SDD, is unique to a Subsystem’s
implementation for a specific OMS Platform or other OMS implementation.
A key purpose of the SDD is to describe a Subsystem to the host Platform
integrator or Platform provider. The SDD provides the information
necessary to enable the Platform provider to incorporate the Subsystem
into the larger architecture and design of the Platform, and to enable
the Platform integrator to integrate the Subsystem into the Platform.
The SDD references the Subsystem’s Service Contract that defines and
describes the information required to support OMS Data Exchanges. A
Subsystem's Service Contract will contain a complete description of its
OMS-facing interface.

The OMS SDD references additional documents (Subsystem Spec, etc.) and,
with the inclusion of those references, provides the overarching
description of a Subsystem. The SDD identifies the OMS compliance
pattern of the Subsystem. There are two potential OMS compliance
patterns depicted in the following figures:

1.  Figure 1.2-1, Standalone OMS Subsystem, depicts where Subsystem
    implementation is OMS-compliant without requiring adaptation

2.  Figure 1.2-2, Platform-Hosted OMS Adaptation, depicts where a
    Platform-hosted Adapter provides OMS compliance.

The compliance pattern chosen for a particular Subsystem has no effect
on the Subsystem’s OMS compliance tier determination. Note that if a
legacy non-OMS subsystem is adapted to OMS compliance within the
boundary of the Subsystem, a Platform does not see that adaptation and
the Subsystem is considered a standalone Subsystem as depicted below.

This section should contain a block diagram similar to one of two
figures depicted below. The block diagram should be at a high level, and
does not need to go to a detailed ICD level as will be requested further
in the document. At a minimum, the block diagram should call out the
Subsystem, the Platform, related Services, and the connection(s) between
them. If you are including a block diagram, please introduce the figure
with a sentence.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE AND CAPTION. INCLUDE AN
APPROPRIATE FIGURE AND CAPTION FOR YOUR SYSTEM &gt;&gt;

<img src="media/image3.png" style="width:4.99167in;height:4.24167in" />

<span id="_Toc256000047" class="anchor"></span>Figure 1.2-1 Standalone
Subsystem

<img src="media/image4.png" style="width:6.5in;height:3.59167in" />

<span id="_Toc256000048" class="anchor"></span>Figure 1.2-2
Platform-Hosted OMS Adaptation

The issue of adaptation inherently defines two potential elements of a
Subsystem using an Adapter: the “non-OMS subsystem” which provides the
mission functions and/or Capabilities and consists of the OMS Subsystem
minus adaptation, and a subsystem’s OMS Adapter. The “non-OMS subsystem”
and the OMS Adapter may be separately acquired. The SDD describes the
non-OMS subsystem acquisition approaches, and describes any agreement(s)
between parties involved in the development of OMS Adapter(s). The SDD
describes the interfaces and key external physical characteristics of a
non-OMS subsystem that must be known to enable the various parties to
successfully design and integrate the overall Subsystem into the
Platform. In addition, the SDD specifies where the CAL Implementation
resides when the Subsystem is using a Platform-hosted Adapter. In this
case, the Subsystem might identify the location of the CAL
Implementation as the OCE or Other Mission Processing.

The SDD provides the information required to enable the Subsystem to be
exchanged with a similar Subsystem, as well as supplying information
that enables the Subsystem to be reused on another Platform. If the
non-OMS subsystem is adapted with a Platform-hosted Adapter the SDD
identifies and describes all interfaces that use Platform resources.

Service Contract
================

Table 2.0-1, Service Contract, identifies and refers to the Service
Contract for the Subsystem.

The Service Contract includes traditional IRS/IDD (Interface Requirement
Specification/Interface Design Document) information. The Service
Contract must be non-proprietary, but may include proprietary annexes or
references as noted in its template. See the Service Contract Template,
OMSC-TMP-003, for a description of the OMS Service Contract. Please add
a sentence to summarize your Service Contract and an additional sentence
to introduce the table below. You may delete rows as required, but this
document must be submitted with the referenced Service Contract and if
desired, a separate Service Contract Appendix C spreadsheet. Do not
include Service Contracts for Services hosted by this Subsystem: These
Service Contracts will be listed in MPDD “Mission Package Worksheet”
section, “Units of Replaceability Within the Mission Package Worksheet”
table.

The columns in Table 2.0-1, Service Contract, should contain the
following information:

-   Title – Name of the Service Contract Document

-   Reference – Unique identifier for the document’s configuration
    control

-   Date / Revision – Date and Revision of the Service Contract.

<span id="_Toc219295210" class="anchor"></span>Table 2.0-1 Service
Contract

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
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Subsystem Specification Identification and Reference
====================================================

Table 3.0-1, Subsystem Specifications, references the associated
Subsystem requirements specifications.

If none is available, then mark this section as “Not Applicable” with a
rationale and the first empty cell of the table with “N/A”.

This section should list applicable Subsystem specifications that
introduce, describe, and/or list any requirements documents that may be
applicable for the integration of the Subsystem. This includes top-level
Subsystem specifications, as well as internal interfaces that need to be
exposed to an integrator, such as interfaces to an OMS Platform-hosted
Adapter.

This section should also be used to identify unique tools and support
software that will be needed to install, integrate, and/or run the
Subsystem.

The columns in Table 3.0-1, Subsystem Specifications, should contain the
following information:

-   Title – Name of the document

-   Reference – Unique identifier for the document’s configuration
    control

-   Date / Revision – Date and release version for the document.

<span id="_Toc219295211" class="anchor"></span>Table 3.0-1 Subsystem
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
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Licenses
========

Table 4.0-1, Subsystem Licenses, documents the licenses required by the
Subsystem to integrate with the Platform.

This section only addresses licenses used by the Subsystem that are not
defined in the Service Contracts referenced in Table 2.0-1, Service
Contract, such as licenses to support Data Storage, an OCE, or Security
Information Exchanges not defined in a Service Contract. The intent of
this disclosure is to identify licenses that a Platform integrator would
be required to acquire in order to integrate the Subsystem. If this
section is not applicable, mark as “Not Applicable” with a rationale and
the first empty cell of the table with “N/A”.

The columns in Table 4.0-1, Subsystem Licenses, should contain the
following information:

-   License Description – Name and Description of the required License

-   Provider/Product/Version – Provide the source and version of the
    required License

-   Type – Please indicate if this is a runtime or non-runtime License

-   Purpose – Please indicate what the general purpose of the License is
    used for.

<span id="_Toc219295212" class="anchor"></span>Table 4.0-1 Subsystem
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
<td>DDS License</td>
<td>Super Software</td>
<td>DDS</td>
<td>1.2</td>
<td>Runtime</td>
<td>CAL Transport</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

Table 5.0-1, Additional Subsystem Libraries, documents libraries used by
the Subsystem that are not defined in the Service Contracts.

To preserve document formatting, if this section is not applicable, mark
as “Not Applicable” with a rationale and the first empty cell of the
table with “N/A”.

<span id="_Toc219295213" class="anchor"></span>Table 5.0-1 Additional
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
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Subsystem Time Synchronization
==============================

This section should include Special Signal references to any OMS
Standard time reference signals used that are specified in OMSC-STD-001,
OMS Standard, Time Reference Signals section. Table 6.0-1, Time Sync,
identifies and describes the method(s) used for time synchronization.

Include optional high fidelity time synchronization. Please list the
type of time synchronization your Subsystem requires, also note if it is
high or low speed (1 Hz is considered low speed). To preserve document
formatting, if this section is not applicable, mark as “Not Applicable”
with a rationale and the first empty cell of the table with “N/A”.

The columns in Table 6.0-1, Time Sync, should contain the following
information:

-   Method – Method of required time synchronization

-   Description – Please describe the method and the rate that is
    required.

<span id="_Toc219295214" class="anchor"></span>Table 6.0-1 Time Sync

<table>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>

Service and Subsystem Startup
=============================

This section documents the location, identity, and means for modifying
any configuration data required for OMS startup for a Service or
Subsystem.

(Note: This is not meant to include internal Subsystem configuration
data.) Please describe and list out any special startup instructions in
this section. Note that this section may include a sentence that simply
states “Apply power to startup this Subsystem.”

Subsystem External Interfaces
=============================

This section identifies and describes the Subsystem interfaces between
the Subsystem and the Platform ASB.

This figure is an example. Replace this figure with figures that
represent the Subsystem.

This section should include a description of the software and physical
interfaces of the Subsystem. This section should include Special Signal
references to any OMS Standard discrete and voltage reference signals
used that are specified in OMSC-STD-001, OMS Standard, Special Signals
section. This section should also include any Subsystem usage of non-OMS
special signals.

This section should include diagrams for any plugs or connections
between the Subsystem and Platform. The Figure 8.0-1, Plug Connection
Diagram, below depicts an example of a plug connection diagram that
could be included in this section, as needed.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE AND CAPTION. INCLUDE AN
APPROPRIATE FIGURE AND CAPTION IF APPLICABLE &gt;&gt;

<img src="media/image5.png" style="width:3.875in;height:3.49247in" />

<span id="_Toc256000049" class="anchor"></span>Figure 8.0-1 Plug
Connection Diagram

External interface descriptions should include physical connection
descriptions (cables, connectors, pin-out information) and interface
transport information for each of the interfaces. In the case of a
Platform-hosted Adapter, the external interfaces of a Subsystem occur
within the Platform’s mission processing environment, so descriptions of
physical interfaces are not required for messaging, Data Transfers and
Security Information Exchanges.

This section should include a description of all protocols used by the
Subsystem to transfer data to and from a file system, as well as
transfer data directly from one Service/Subsystem to another. This list
should be inclusive and any port not listed here is assumed to be
disabled. Please provide a block diagram like the one shown in Figure
8.0-2, OMS Data Exchanges with a Platform-hosted OMS Adapter, to
describe the data transfer interfaces that the Subsystem supports. At a
minimum it should include the data storage types, transfer protocols,
and any routing or gateways that are applicable. Please introduce this
figure with a sentence if the figure is included in this section.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE AND CAPTION. INCLUDE AN
APPROPRIATE FIGURE AND CAPTION IF APPLICABLE &gt;&gt;

<img src="media/image6.png" style="width:5.33704in;height:8.1875in" />

<span id="_Toc256000050" class="anchor"></span>Figure 8.0-2 OMS Data
Exchanges with a Platform-Hosted OMS Adapter

Open Ports and Protocols
------------------------

All listening ports, specific to the Subsystem, that are open
(accessible to the ASB) are listed in Table 8.1-1, OMS Subsystem Open
Ports and Protocols. Ports and protocols of Services and Isolators are
documented in their respective Service Contracts, not in this table. Any
ports not listed are assumed closed.

The columns in Table 8.1-1, OMS Subsystem Open Ports and Protocols,
should contain the following information on open ports and protocols on
the Subsystem:

-   Port – The network port number and the TCP or UDP protocol being
    used

-   Protocol – The protocol being used on the open port

-   Process/Service – identify the process (e.g., on Linux, the netstat
    command will provide OS process names) or Service (e.g., on Linux,
    the nmap command will provide OS Service names) that has the port
    open

-   Purpose – The purpose of the open port

-   Restriction Mechanism – Identify the method(s) that are implemented
    or expected to constrain or restrict access to the listed port,
    protocol, and process. This should include identification of
    expected hardware, software, and algorithms associated with the
    mechanism. If no mechanisms are implemented or expected, input
    “None” in the cell.

<span id="_Toc219295215" class="anchor"></span>Table 8.1-1 OMS Subsystem
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
<td>1025/TCP</td>
<td>NFSv3</td>
<td>nfsd</td>
<td>NFS Server</td>
<td>iptables firewall</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

It is not used to identify products produced by Services running within
the Subsystem; those products are documented within the applicable
Service Contracts.

-   Product/Data – The product or data item being sent or received from
    the server

-   Format – The format of the product or data. Include reference to
    documents containing formatting details

-   Send/Receive – Send = upload, write or Receive = download, read

-   Data Transfer Server – The URI (or address) of the Data Transfer
    Server that data is being sent to or received from

<span id="_Toc219295216" class="anchor"></span>Table 8.1-2 OMS Subsystem
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
<td>Configuration File</td>
<td>ASCII File</td>
<td>Receive</td>
<td>nfs://10.2.1.12/cfg/</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Subsystem Data Transfer
=======================

Data Storage
------------

This section identifies the Subsystem data storage capability as shown
in Table 9.1-1, Subsystem Data Storage Details.

The columns in Table 9.1-1, Subsystem Data Storage Details, should
contain the following information:

-   Data Store Address – The data store address of the TFTP/FTP/NFS/HTTP
    server which is addressable via a URI. If the address is
    configurable, it should be noted here and reference the document
    that provides guidance on changing its configuration

-   Data Store Label – The identifier for the data that is stored or
    retrieved. The Data Store Label must be a unique reference across
    this document’s table with the purpose to specify a range of
    cybersecurity attributes associated with the referenced data store

-   Shared Directories – The shared directories that are accessible via
    the data transfer protocols. Specifically if there are unique
    folders for OFPs, Configuration Files or Data Products, then each
    should be identified

-   Storage Capacity – The storage capacity allocated for the directory.
    Note: a separate row should be used for each directory if there are
    storage capacity limits per folder

-   Non-Volatile Storage (Yes/No) – If the storage stores data in
    volatile storage which is no longer accessible after a power-cycle,
    then input “No” otherwise input “Yes”

-   Protection In Place (No/C/I/CI):

<!-- -->

-   No – if neither confidentiality nor integrity mechanisms are in
    place

-   C – Confidentiality mechanisms, such as encryption, are in place. If
    there is a confidentiality mechanism in place, the additional
    details must be listed in Table 9.1-3, Data Storage Confidentiality

-   I – Integrity mechanisms, such as digital signature, are in place.
    If there is an integrity mechanism in place, the additional details
    must be listed in Table 9.1-4, Data Storage Integrity

-   CI – Confidentiality and Integrity mechanisms are in place. If there
    are confidentiality and integrity mechanisms in place, the
    additional details must be listed in Table 9.1-3, Data Storage
    Confidentiality and Table 9.1-4, Data Storage Integrity

<!-- -->

-   Data Transfer Protocols(s) – The supported protocols for accessing
    the data storage from either a Service or Subsystem. Refer to OMS
    Standard, OMSC-STD-001, “Data Transfer Formats, APIs, and
    Protocols,” and “Data Transfer Protocols and APIs” for the list of
    protocols that are allowed for Data Transfer.

<span id="_Toc219295217" class="anchor"></span>Table 9.1-1 Subsystem
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
<td>192.168.0.5</td>
<td>Subsystem FTP Server</td>
<td>/OFP/[Service name]/</td>
<td>1 TB</td>
<td>Yes</td>
<td>No</td>
<td>FTP</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

The table entries should specify the methods for identification,
authentication, access restrictions and audit logging. The following
table provides a template for file based data transfer protocol details.

The columns in Table 9.1-2, Data Storage Access Control Mechanisms,
should contain the following information. A separate section within the
table should be used for each Data Transfer protocol listed in Table
9.1-1, Subsystem Data Storage Details.

-   Mechanism – This column lists the Access Control mechanisms.

<!-- -->

-   Identification – The mechanism used to identify users (e.g., Unique
    usernames and client IP addresses are used to uniquely identify ftp
    users)

-   Authentication – The mechanism used to authenticate users and
    permitted to use the resource (e.g., All remote ftp users are
    authenticated via unique username and password combinations)

-   Access Control – The mechanisms put in place to restrict users,
    associated access and resources (e.g., The FTP Server Access Control
    consists of the restricting users (ftpusers), restricting commands
    (ftpaccess) and allowing only identified hosts being able to access
    the server (ftphosts). Uploads are restricted by users or groups
    into identified folders and file downloads of specific files are
    prevented (ftpaccess). Accounts are restricted to FTP access only by
    limiting shell access (/bin/false))

-   Audit Logging – The mechanism used to perform logging of data
    transfer resource access (e.g., All commands issued by FTP users are
    logged as specified in the configuration (ftpaccess))

<!-- -->

-   Implementation Summary – the Implementation Summary column should
    contain a brief Summary of how the Mechanism is implemented

<span id="_Toc219295218" class="anchor"></span>Table 9.1-2 Data Storage
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
<td>FTP Server</td>
<td></td>
</tr>
<tr class="even">
<td>Identification</td>
<td>Unique usernames and client IP addresses are used to uniquely identify FTP users.</td>
</tr>
<tr class="odd">
<td>Authentication</td>
<td>All remote FTP users are authenticated via unique username and password combinations</td>
</tr>
<tr class="even">
<td>Access Control</td>
<td>Folders and files have permissions based on client group and host, following FTP authentication.</td>
</tr>
<tr class="odd">
<td>Audit Logging</td>
<td>All commands issued by FTP users are logged as specified in the configuration (ftpaccess).</td>
</tr>
<tr class="even">
<td>NFS Server</td>
<td></td>
</tr>
<tr class="odd">
<td>Identification</td>
<td>Unique usernames and client IP addresses are used to uniquely identify NFS users.</td>
</tr>
<tr class="even">
<td>Authentication</td>
<td>All remote NFS users are authenticated via unique username and password combinations</td>
</tr>
<tr class="odd">
<td>Access Control</td>
<td>The NFS Server Access Control consists of the restricting users (root_squash), restricting shared directories (/etc/exports) and allowing only identified hosts being able to access the server (/etc/hosts.allow).</td>
</tr>
<tr class="even">
<td>Audit Logging</td>
<td>All commands issued by NFS users are logged as specified in the configuration (/etc/nfs/nfslog.conf).</td>
</tr>
</tbody>
</table>

### Data Storage Confidentiality Mechanisms

This section identifies the specific confidentiality mechanisms (e.g.,
host-based firewall) and use of encryption within the Data Storage as
shown in Table 9.1-3, Data Storage Confidentiality.

The columns in Table 9.1-3, Data Storage Confidentiality, should contain
the following information:

-   Data Store Address – The data store address of the TFTP/FTP/NFS/HTTP
    server which is addressable via a URI. If the address is
    configurable, it should be noted here and reference the document
    that provides guidance on changing its configuration

-   Data Store Label – The identifier for the data that is stored or
    retrieved. The Data Store Label must be a unique reference across
    this document’s tables with the purpose to specify a range of
    cybersecurity attributes associated with the referenced data store

-   Protected Data – The information items to which the confidentiality
    mechanism is applied

-   Confidentiality Mechanism – Identify the method(s) used by the
    Subsystem to provide confidentiality. This should include
    identification of applicable hardware, software, and algorithm
    associated with the implemented mechanism

-   Implementation Details – Details on how the confidentiality
    mechanism is implemented and/or include a reference to other
    documents and any additional information for clarification.

<span id="_Toc219295219" class="anchor"></span>Table 9.1-3 Data Storage
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
<td>192.168.0.5</td>
<td>FTP Data Store</td>
<td>Applications and Payload Products</td>
<td>AES256 GCM Mode</td>
<td>See DataStore-Encryption.docx for further details</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

The columns in Table 9.1-4, Data Storage Integrity, should contain the
following information:

-   Data Store Address – The data store address of the TFTP/FTP/NFS/HTTP
    server which is addressable via a URI. If the address is
    configurable, it should be noted here and reference the document
    that provides guidance on changing its configuration

-   Data Store Label – The identifier for the data that is stored or
    retrieved. The Data Store Label must be a unique reference across
    this document’s tables with the purpose to specify a range of
    cybersecurity attributes associated with the referenced data store

-   Protected Data – The information items to which the integrity
    mechanism is applied

-   Integrity Mechanism – Identify the method(s) used by the Subsystem
    to provide integrity. This should include identification of
    applicable hardware, software, and algorithm associated with the
    implemented mechanism

-   Implementation Details – Details on how the integrity mechanism is
    implemented and/or include a reference to other documents and any
    additional information for clarification.

<span id="_Toc219295220" class="anchor"></span>Table 9.1-4 Data Storage
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
<td>192.168.0.5</td>
<td>FTP Data Store</td>
<td>Applications &amp; Payload Products</td>
<td>SHA-256</td>
<td>Hash values calculated and provided in ProductMetadata</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

The columns in Table 9.2-1, Data Transfer Confidentiality Mechanisms,
should contain the following information:

-   Protected Data – The information items to which the confidentiality
    mechanism is applied

-   Confidentiality Mechanism – Identify the method(s) used by the
    Subsystem to provide confidentiality. This should include
    identification of applicable hardware, software, and algorithm
    associated with the implemented mechanism. For Secure Data transfers
    utilizing a VPN solution (e.g., IPsec, SSL) provide the
    implementation software name (e.g., strongSwan), type of VPN, and a
    pointer to the configuration file

-   Implementation Details – Details on how the confidentiality
    mechanism is implemented and/or include a reference to other
    documents and any additional information for clarification.

<span id="_Toc219295221" class="anchor"></span>Table 9.2-1 Data Transfer
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
<td>Config File</td>
<td>AES256 CBC Mode</td>
<td>Decrypted using AES-256 algorithm upon receipt</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

The columns in Table 9.3-1, Data Transfer Integrity Mechanisms, should
contain the following information:

-   Protected Data – The information items to which the integrity
    mechanism is applied

-   Integrity Mechanism – Identify the method used by the Subsystem to
    provide integrity. This should include identification of applicable
    hardware, software, and algorithm associated with the implemented
    mechanism

-   Implementation Details – Details on how the integrity mechanism is
    implemented and/or include a reference to other documents and any
    additional information for clarification.

<span id="_Toc219295222" class="anchor"></span>Table 9.3-1 Data Transfer
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
<td>Mission Data File</td>
<td>Hash/Digital Signature</td>
<td>Mission Data File is digitally signed</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

Example Data Transfer methods are: IPv4 and/or IPv6, NFS - version x,
UDP transport, no client authentication, etc.

The columns in Table 9.4-1, Subsystem Data Transfer Configuration,
should contain the following information:

-   Data Transfer Server – A resolvable location or URI for each server
    on the Subsystem. Refer to OMS Standard, OMSC-STD-001, “OMS URI
    Formats,” for the content and format of URIs that may be used for
    the allowed protocols

-   Data Transfer Protocol – This column should be one of the supported
    Data Transfer Protocols. Every supported protocol should be
    documented in its own row

-   Version – This column should identify the specific version of the
    Data Transfer Protocol. Use SCAP nomenclature if available and
    appropriate. For example FTP-0.10.-11.1

-   Configuration Details – This column should identify any specific
    configuration details for a given Data Transfer Protocol. For
    example, specific protocol versions, unsupported commands,
    configured ports, share limitations, should be indicated.

<span id="_Toc219295223" class="anchor"></span>Table 9.4-1 Subsystem
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
<td><a href=""><strong>Error! Hyperlink reference not valid.</strong></a></td>
<td>FTP</td>
<td>FTP-0.10.-11.1</td>
<td>passive ftp only (ports: 50000-50009)</td>
</tr>
<tr class="even">
<td>NFS://&lt;something&gt;</td>
<td>NFS</td>
<td>nfs-utils – 1.2.3</td>
<td>NFSv3, Portmapper (port:111), read only export (/ofp/), read/write export (/data/), secure-ports (1-1024) from NFS clients</td>
</tr>
<tr class="odd">
<td>RTP://&lt;something&gt;</td>
<td>RTP</td>
<td>FFmpeg 3.1.2</td>
<td>IPV4 UDP, H.264 format, 10-60fps, 1080p</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Subsystem Internal Interfaces
=============================

Table 10.0-1, Subsystem Internal ICDs, describes the non-OMS subsystem
internal interfaces that are exposed when the Subsystem is installed in
the Mission Package.

This section is applicable for Platform-hosted applications, or other
applications where Subsystem internal interfaces are exposed when
installed into the Mission Package, which may consume Platform resources
such as Ethernet bandwidth or which will need to be identified for use
in troubleshooting or investigating alternative
configurations/installations at a later time. Otherwise this section
should be marked as “Not Applicable”.

In the case where an Adapter is present, the description of the
interfaces between the non-OMS subsystem and the Adapter should be
included in this section, including a reference to the non-OMS subsystem
software ICD. In all cases, interfaces between physically separate
components of a Subsystem should be included in this section. Please use
this section to summarize in paragraph form the non-OMS subsystem
interfaces to the Adapter. This section should also include the
description of Subsystem internal interfaces a Platform-hosted Adapter
uses to create each of the four OMS Data Exchange types (OMS Messaging,
Data Transfer, Special Signals, and Security Information Exchanges).

This section can provide a reference to the Subsystem hardware ICD where
all physical data and signal interfaces (including cables, connectors
and pin-out information) between a non-OMS subsystem and Platform-hosted
Adapter, and/or between physically separate components of a Subsystem,
are identified and described. List these references in Table 10.0-1,
Subsystem Internal ICDs.

To preserve document formatting, if this section is not applicable, mark
as “Not Applicable” with a rationale and the first empty cell of the
table with “N/A”.

Table 10.0-1, Subsystem Internal ICDs, should contain the following
information:

-   Title – Name of the document

-   Reference – Unique identifier for the document’s configuration
    control

-   Date/Revision – Date and release version for the document.

<span id="_Toc219295224" class="anchor"></span>Table 10.0-1 Subsystem
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
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Open Computing Environment (OCE)
================================

This section documents the Subsystem’s OCE OMS mission processing
architecture and describes specific tool chains for building in the OCE
environment.

If an OCE is not provided, then document this section and its
subsections as “Not Applicable” with a rationale.

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

This identifies supported compilers and specific compiler options that
are required to build a Service in the OCE provided by this Subsystem.

This section documents the specific binary format for any OCE provided
binaries. This will include the format of the CAL libraries that will
run in the OCE.

This section documents how a Service is compiled for an OCE target
implementation. This section gives explicit instructions for building
for a particular OCE target.

### Isolation Layer

This section documents the implemented Façade interfaces for this OCE
provided by this Subsystem as defined in the OMS OS Façade
Specification.

This section documents how the Façade implementation supports the Data
Transfer methods, if specific client versions of software are used for
Data Transfer on the OCE, these should be called out as well.

### Time

This section documents how time synchronization is supported by the OCE.

This section should include how time is provided to applications and the
method for setting the system clock.

Java Environment
----------------

This section documents the specific Java environment provided by the
Java-based OCE.

If a Java-based OCE is not provided per system policy, then this section
will be identified as “Not allowed per system policy.”

### Build Environment and Tool Chain

This section documents the specific build environment for a Java-based
OCE.

This section should identify any Java tool chains required for building
a Java Service for running in the Java-based OCE.

This section documents how a Service is compiled for an OCE target
implementation. This section gives explicit instructions for building
for a particular OCE target.

### Java Data Transfer

This section documents the C/C++ libraries (if any) that are provided as
part of the Java-based OCE and that the Java environment is reliant upon
in order to perform data transfer operations.

Via its JNI interface, the Java environment will use the support
provided by these libraries to transfer data to and from applications
running in the Java environment. If the Java environment is reliant upon
specific versions of these libraries, then those versions should be
documented as well.

### Time

This section documents how time synchronization is supported by the
Java-based OCE.

This section should include how time is provided to applications and the
method for setting the system clock.

Virtualization Environment
--------------------------

This section identifies if there is a Virtual Machine (VM)-based
processing architecture on the Subsystem.

If there is no Virtual Environment on the OMS Subsystem then document
this section and its subsections as “Not Applicable” with a rationale.
This section describes the virtual environment that will host a virtual
appliance that supports a Façade-based OCE, a Java-based OCE, or both.

### Hypervisor

This section documents the specific hypervisor provided by the
virtualization-based OCE, which includes the following:

#### Processor

This section identifies if the virtualization approach is hardware
assisted or if a full virtualization approach is used.

#### Memory Virtualization

This section identifies the memory virtualization approach.

This section should contain a description of the memory virtualization
approach.

#### Network Virtualization

This section identifies the virtual network for each deployed virtual
appliance.

This section should contain a description of the virtual network for
each deployed virtual appliance.

### Time

This section documents how time synchronization is supported by the VM
OCE.

This section should include how time is provided to applications and the
method for setting the system clock.

Service Deployment
------------------

This section documents how Services are deployed and managed within the
OCE.

This includes any provisions for VMs/Appliances, Containerization, etc.
This should identify requirements placed on a Service to run in the
environment and for using a CAL or Data Transfer. This section should
also document any management functionality of Service packaging.

Test Procedures & Data
======================

This section identifies relevant available test procedures that were
used to integrate, verify and/or assess OMS compliance of the Subsystem.

If no test procedures are referenced, mark this section as not
applicable. This section can be completed in paragraph form or with a
table. If you use a table, please introduce the table with a sentence.
If you make this section not applicable, please state so in a sentence.
If possible, please provide a summary of the testing that is described
in the test procedures, for example, what is lab testing, flight
testing, simulated, live, comprehensive, stressing, etc.

Cybersecurity Posture
=====================

This section identifies the cybersecurity posture of the Subsystem.

Describe the Cybersecurity posture of the Subsystem. The Cybersecurity
Posture Section should describe the Cybersecurity posture implementation
of the Subsystem. The addendum may include classified implementation
details with reference to Interface Control Documents (ICDs). The
Cybersecurity posture as characterized by the Cyber Survivability Risk
Category (CSRC) identifies the level of rigor needed to describe the OMS
Cybersecurity features that fall under the applicable Cyber
Survivability Attributes (CSAs).

The Cybersecurity posture descriptions are in summary format with a
pointer to an external unclassified, non-proprietary document or
detailed in the follow section including diagrams to relay the
implementation.

Cyber Survivability Attributes (CSAs)
-------------------------------------

This section identifies the CSAs applicable to the Subsystem.

### Prevent CSAs

This section identifies and documents the System Survivability Key
Performance Parameter (KPP) Prevent CSAs implementation for the
Subsystem. Table 13.1-1 identifies the System Survivability KPP Prevent
CSAs applicable to the Subsystem.

In the table below, indicate the CSAs applicable to the Subsystem by
adding an “x”. If the CSAs are not applicable or not addressed, denote
this section with “N/A” and leave Table 13.1-1 empty.

<span id="_Toc219295225" class="anchor"></span>Table 13.1-1 Applicable
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

For applicable CSAs, provide a brief, high-level description (1-2
sentences) of how each Cyber Survivability Attribute (CSA) identified in
Table 13.1-1 is explicitly addressed by the OMS Subsystem. The
description should be unclassified and non-proprietary, and capture the
cybersecurity posture. The cybersecurity posture should be commensurate
with the expected CSRC.

-   CSA-01: Control Access

-   CSA-02: Reduce System’s Cyber Detectability

-   CSA-03: Secure Transmissions and Communication

-   CSA-04: Protect System’s Information from Exploitation

-   CSA-05: Partition and Ensure Critical Functions at Mission
    Completion Performance Levels

-   CSA-06: Minimize and Harden Attack Surfaces

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable SDD section(s). See the Cybersecurity
Guide for more information.

### Mitigate CSAs

This section identifies and documents the System Survivability KPP
Mitigate CSAs implementation for the Subsystem. Table 13.1-2 identifies
the System Survivability KPP Mitigate CSAs applicable to the Subsystem.

In the table below, indicate the CSAs applicable to the Subsystem by
adding an “x”. If the CSAs are not applicable or not addressed, denote
this section with “N/A” and leave Table 13.1-2 empty.

<span id="_Toc219295226" class="anchor"></span>Table 13.1-2 Applicable
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

For the applicable CSAs, provide a brief, high-level description (1-2
sentences) of how each Cyber Survivability Attribute (CSA) is explicitly
addressed by the Subsystem. The description should be unclassified and
non-proprietary, and capture the cybersecurity posture. The
cybersecurity posture should be commensurate with the expected CSRC.

-   CSA-07 Baseline and Monitor Systems and Detect Anomalies

-   CSA-08 Manage System Performance and Enable Cyberspace

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable SDD section(s). See the Cybersecurity
Guide for more information.

### Recover CSA

This section identifies and documents the System Survivability KPP
Recover CSA implementation for the Subsystem.

Provide a brief, high-level description (1-2 sentences) of how the
CSA-09 Recover System Capabilities is explicitly addressed by the
Subsystem. The description should be unclassified and non-proprietary,
and capture the cybersecurity posture. The cybersecurity posture should
be commensurate with the expected CSRC.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable SDD section(s). See the Cybersecurity
Guide for more information.

If the CSA is not applicable or not addressed, denote this with “N/A”.

### Adapt CSA

This section identifies and documents the System Survivability KPP Adapt
CSA implementation for the Subsystem.

Provide a brief, high-level description (1-2 sentences) of how the
CSA-10 Actively Manage System’s Configuration to Achieve and Maintain an
Operationally-Relevant Cyber Risk Posture is explicitly addressed by the
Subsystem. The description should be unclassified and non-proprietary,
and capture the cybersecurity posture. The cybersecurity posture should
be commensurate with the expected CSRC.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable SDD section(s). See the Cybersecurity
Guide for more information.

If the CSA is not applicable or not addressed, denote this with “N/A”.

Security Addendum
=================

This section identifies the Security Addendum document(s).

The Security Addendum is expected to be external to the SDD and can be
composed of one or more separate documents that:

-   Might already be existing/planned program documents that could be
    referenced to supply OMS-related information,

-   Might have to be published at different security levels, and

-   Could be developed/published at different points in the program
    lifecycle.

The name of the document(s) must be unclassified and non-proprietary.
Referenced documents may be both classified and proprietary. The
Security Addendum should describe the Security Information Exchanges
implemented by the Subsystem and provides additional, classified and/or
proprietary details relating to the security of the Subsystem. The
addendum may include classified implementation details with reference to
Interface Control Documents (ICDs).

Appendix A Acronyms and Abbreviations
=====================================

This section lists the abbreviations and acronyms used in this document
not a copy of the OMS lexicon as shown in Table A.0-1, List of Acronyms
and Abbreviation Definitions.

In addition, acronyms should be spelled out at first use in the body of
the document.

<span id="_Toc219295227" class="anchor"></span>Table A.0-1 List of
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
<td>UCI</td>
<td>Universal C2 Interface</td>
</tr>
<tr class="even">
<td>UML</td>
<td>Unified Modeling Language</td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>

Appendix B Glossary
===================

This section lists the terms used in this document as shown in Table
B.0-1, List of Term Definitions.

Note: the list of terms used should not be a copy of the OMS lexicon.

<span id="_Toc219295228" class="anchor"></span>Table B.0-1 List of Term
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
<td>Abstract Service Bus</td>
<td>The Abstract Service Bus (ASB) is an intermediary that allows mission Service functions to be widely available to other mission services, Subsystems, and resources. The ASB implements the CAL, Data Transfer interfaces, Special Signal interfaces, and Security Exchange interfaces. The ASB also defines the physical interfaces.</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>
