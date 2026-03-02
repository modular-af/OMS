Open Mission Systems (OMS)

Definition And Documentation (D&D)

Platform Description Document (PDD) Template Instructions

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

This Platform Description Document (PDD) Template Instructions describes
how the PDD Template is filled out. The General Template Instructions
provides a description of how this Template Instructions document is
used in filling out the corresponding associated PDD Template.

This Platform Description Document (PDD) Template Instructions is
aligned with the Platform Description Document (PDD) Template,
OMSC-TMP-001, Revision M, dated 22 January 2026.

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

[1.1 References 4](#references)

[2 Platform 5](#platform)

[2.1 Platform Licenses 5](#platform-licenses)

[2.2 Platform Software Dependencies 5](#platform-software-dependencies)

[3 Abstract Service Bus (ASB) 7](#abstract-service-bus-asb)

[3.1 OMS Message Set 7](#oms-message-set)

[3.2 Network 7](#network)

[3.2.1 Network Interconnect Diagram 7](#network-interconnect-diagram)

[3.2.2 Ports & Protocols 9](#ports-protocols)

[3.2.3 Network Address Information 11](#network-address-information)

[4 Data Transfer 12](#data-transfer)

[4.1 Data Storage 12](#data-storage)

[4.1.1 Data Storage Access Controls 13](#data-storage-access-controls)

[4.1.2 Data Storage Confidentiality Mechanisms
14](#data-storage-confidentiality-mechanisms)

[4.1.3 Data Storage Integrity Mechanisms
15](#data-storage-integrity-mechanisms)

[4.2 Data Transfer Confidentiality Mechanisms
16](#data-transfer-confidentiality-mechanisms)

[4.3 Data Transfer Integrity Mechanisms
16](#data-transfer-integrity-mechanisms)

[4.4 Data Transfer Configuration 17](#data-transfer-configuration)

[4.4.1 Data Transfer Protocol Details
17](#data-transfer-protocol-details)

[5 Mission Processing 19](#mission-processing)

[5.1 Open Computing Environment (OCE)
19](#open-computing-environment-oce)

[5.1.1 OCE Processor Types, Operating Systems, and Configuration
19](#oce-processor-types-operating-systems-and-configuration)

[5.1.2 General Environment 19](#general-environment)

[5.1.2.1 Build Environment and Tool Chain
19](#build-environment-and-tool-chain)

[5.1.2.2 Isolation Layer 19](#isolation-layer)

[5.1.2.3 Time 20](#time)

[5.1.3 Java Environment 20](#java-environment)

[5.1.3.1 Build Environment and Tool Chain
20](#build-environment-and-tool-chain-1)

[5.1.3.2 Java Data Transfer 20](#java-data-transfer)

[5.1.3.3 Time 20](#time-1)

[5.1.4 Service Deployment 20](#service-deployment)

[5.2 Other Mission Processing 21](#other-mission-processing)

[5.2.1 Other Mission Processor Types, Configuration and Interfaces
21](#other-mission-processor-types-configuration-and-interfaces)

[5.2.2 Other Mission Processing Tool Chain Description
21](#other-mission-processing-tool-chain-description)

[5.2.3 OMS Attributes for Other Mission Processing
21](#oms-attributes-for-other-mission-processing)

[5.2.4 Service Deployment 21](#service-deployment-1)

[6 Time and Position Information 22](#time-and-position-information)

[6.1 Time Reference and Time Synchronization
22](#time-reference-and-time-synchronization)

[6.2 Position Information 26](#position-information)

[6.2.1 Position Information Indirectly Provided for the Platform
26](#position-information-indirectly-provided-for-the-platform)

[6.2.2 Position Information Directly Provided by Platform
27](#position-information-directly-provided-by-platform)

[7 Critical Abstraction Layer (CAL) Implementation
29](#critical-abstraction-layer-cal-implementation)

[7.1 CAL Available Implementations 29](#cal-available-implementations)

[7.2 CAL Required Libraries / Licenses
32](#cal-required-libraries-licenses)

[7.3 CAL Implementation Processing Architecture
34](#cal-implementation-processing-architecture)

[7.3.1 Language-Specific CAL 34](#language-specific-cal)

[7.3.1.1 \[CAL Identifier\] 34](#cal-identifier)

[7.3.1.1.1 \[CAL Identifier\] CAL Configuration
34](#cal-identifier-cal-configuration)

[7.3.1.1.2 \[CAL Identifier\] CAL Externalizer Implementation
35](#cal-identifier-cal-externalizer-implementation)

[7.3.1.1.3 \[CAL Identifier\] CAL Operational Attributes
36](#cal-identifier-cal-operational-attributes)

[7.3.2 Language-Agnostic CAL 39](#language-agnostic-cal)

[7.3.2.1 \[CAL Identifier\] 40](#cal-identifier-1)

[7.3.2.1.1 \[CAL Identifier\] Language-Agnostic CAL Configuration
41](#cal-identifier-language-agnostic-cal-configuration)

[8 Virtualization Environments 42](#virtualization-environments)

[8.1 Virtualization Environment - &lt;&lt;Name&gt;&gt;
42](#virtualization-environment---name)

[8.1.1 Processor Virtualization 42](#processor-virtualization)

[8.1.2 Memory Virtualization 42](#memory-virtualization)

[8.1.3 Network Virtualization 42](#network-virtualization)

[8.1.4 Virtualization Environment Deployment
43](#virtualization-environment-deployment)

[8.1.5 Service Deployment 43](#service-deployment-2)

[8.1.6 Time 43](#time-2)

[8.1.7 Virtualization Environment Configuration
43](#virtualization-environment-configuration)

[9 Configuration Data 44](#configuration-data)

[10 Special Signals 45](#special-signals)

[10.1 Provided Special Signals 45](#provided-special-signals)

[10.2 Provisioned Special Signals 46](#provisioned-special-signals)

[11 Cybersecurity Posture 47](#cybersecurity-posture)

[11.1 Cyber Survivability Attributes (CSAs)
47](#cyber-survivability-attributes-csas)

[11.1.1 Prevent CSAs 48](#prevent-csas)

[11.1.2 Mitigate CSAs 49](#mitigate-csas)

[11.1.3 Recover CSA 49](#recover-csa)

[11.1.4 Adapt CSA 50](#adapt-csa)

[12 Security Addendum 51](#security-addendum)

[A Appendix A Acronyms and Abbreviations
52](#appendix-a-acronyms-and-abbreviations)

[B Appendix B Glossary 53](#appendix-b-glossary)

[C Appendix C Message Details 54](#appendix-c-message-details)

List of Figures

[Figure 3.2-1 Network Interconnect Diagram 8](#_Toc219294954)

This page is intentionally left blank.

List of Tables

[Table 0.0-1 OMS D&D Documents 2](#_Toc219294955)

[Feedback Form Table 3](#_Toc219294956)

[Table 1.1-1 Reference Documents 4](#_Toc219294957)

[Table 2.1-1 Platform Licenses 5](#_Toc219294958)

[Table 2.2-1 Platform Software Dependencies 6](#_Toc219294959)

[Table 3.1-1 OMS Message Set 7](#_Toc219294960)

[Table 3.2-1 Network Segmentation 9](#_Toc219294961)

[Table 3.2-2 Open Ports and Protocols 10](#_Toc219294962)

[Table 3.2-3 Product/Data and Data Transfer Servers 10](#_Toc219294963)

[Table 3.2-4 Networking Information 11](#_Toc219294964)

[Table 4.1-1 Platform Data Storage Details 13](#_Toc219294965)

[Table 4.1-2 Data Storage Access Control Mechanisms 14](#_Toc219294966)

[Table 4.1-3 Data Storage Confidentiality 15](#_Toc219294967)

[Table 4.1-4 Data Storage Integrity 15](#_Toc219294968)

[Table 4.2-1 Data Transfer Confidentiality Mechanisms
16](#_Toc219294969)

[Table 4.3-1 Data Transfer Integrity Mechanisms 17](#_Toc219294970)

[Table 4.4-1 Platform Data Transfer Configuration 17](#_Toc219294971)

[Table 6.1-1 Time Synchronization Protocols 22](#_Toc219294972)

[Table 6.1-2 High Fidelity Time Reference and Time Synchronization
Mechanisms 23](#_Toc219294973)

[Table 6.1-3 SystemTimeAtReference Inputs and Outputs
25](#_Toc219294974)

[Table 6.2-1 Source Providing Position Information 26](#_Toc219294975)

[Table 6.2-2 Position Information Processing Inputs and Outputs
28](#_Toc219294976)

[Table 7.1-1 CAL Versions Available 30](#_Toc219294977)

[Table 7.1-2 CAL Interaction Limitations 31](#_Toc219294978)

[Table 7.2-1 CAL Licenses & Libraries 33](#_Toc219294979)

[Table 7.3-1 CAL Externalizer Version Information 35](#_Toc219294980)

[Table 7.3-2 SOAC-1 &lt;SOAC name&gt; 39](#_Toc219294981)

[Table 7.3-3 Language-Agnostic CAL Access Information
40](#_Toc219294982)

[Table 9.0-1 Configuration Data 44](#_Toc219294983)

[Table 10.1-1 Provided Special Signals 45](#_Toc219294984)

[Table 10.2-1 Provisioned Special Signals 46](#_Toc219294985)

[Table 11.1-1 Applicable System Survivability KPP Prevent CSAs
48](#_Toc219294986)

[Table 11.1-2 Applicable System Survivability KPP Mitigate CSAs
49](#_Toc219294987)

[Table A.0-1 List of Acronyms and Abbreviation Definitions
52](#_Toc219294988)

[Table B.0-1 List of Term Definitions 53](#_Toc219294989)

This page is intentionally left blank.

General Template Instructions

This document, Platform Description Document (PDD) Template
Instructions, OMSC-INS-001, provides information on how to fill in
required information in the PDD Template, OMSC-TMP-001. The outline of
the PDD Template Instructions is one-to-one aligned with each section in
the PDD Template. The green text in each section of this PDD Template
Instructions document should be used as guidance to fill out the
corresponding section in the PDD Template. Green text in the PDD
Template is considered guidance only and should be removed to reflect
your Platform. NOTE: The first page of the PDD Template document is for
Open Mission Systems (OMS) purposes only and should be removed prior to
the release of the completed Template.

A Platform provider should save the PDD Template using an appropriate
unique filename. The Platform provider should add an appropriate
document number, revision history and document date for configuration
management of program specific information. The distribution statement
should be filled out based on the program specific restrictions, and at
a minimum should be Distribution Statement A. If the contents of the
document require a higher restriction, the appropriate distribution
statement should be updated as needed. Green text in the PDD Template
represents guidance for the creation of the PDD. Green text should not
remain in the completed PDD and should be replaced in the Cover page,
Abstract, Revision Record, and all applicable sections defined in the
PDD Template.

This document contains only non-proprietary information. Referenced
documents may contain proprietary information except in sections noted
otherwise. Proprietary information included in referenced documents
should include data transfer mechanisms and data structures, but should
not include proprietary data content. Classification of the PDD should
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

2.  **If additional tables or figures are added,** the table/figure
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

All documents referenced within this PDD must include a document
reference number with release dates and be included in the compliance
package deliverable.

The documents listed in Table 0.0-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219294955" class="anchor"></span>Table 0.0-1 OMS D&D
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

<span id="_Toc219294956" class="anchor"></span>Feedback Form Table

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

This section identifies the OMS Platform that is incorporated into a
Weapon System or Test Configuration which is in a software
integration/test facility.

This section should document key aspects and capabilities of the subject
OMS Platform, including details on the Abstract Service Bus (ASB), Open
Computing Environment (OCE), Time Reference and Time Synchronization,
Position Information, Data Transfer, and other included components of
the OMS Platform.

Block diagrams or figures can be included as appropriate to give the
reader a high level understanding of the OMS Platform described in this
PDD.

References
----------

This section lists all the referenced documents that are required to
support the integration of this Platform as shown in Table 1.1-1,
Reference Documents.

This section should include the current OMS Standard for basis of
compliance, internal and external ICDs, and other important documents or
standards. Table 1.1-1, Reference Documents, lists all the required
reference documents.

<span id="_Toc219294957" class="anchor"></span>Table 1.1-1 Reference
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
<tr class="even">
<td>NIST SP 800-145</td>
<td>The NIST Definition of Cloud Computing</td>
<td>-</td>
<td>September 2011</td>
</tr>
<tr class="odd">
<td>Add rows as required.</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Platform
========

Platform Licenses
-----------------

This section identifies the licenses required in order to operate the
Platform, including the OCE, Other Mission Processing hardware,
software, or infrastructure as shown in Table 2.1-1, Platform Licenses.

Examples include Operating Systems, Servers, and Executables. Critical
Abstraction Layer (CAL) licenses are listed in Table 7.1-1, CAL Versions
Available.

The columns in Table 2.1-1, Platform Licenses, should contain the
following information:

-   License Name/Provider/Version – These columns should identify the
    product by license name, provider, and the version of the license

-   Purpose – This column should identify the overall purpose of the
    licensed software

-   License Type – This column should identify the type of license; Type
    is Commercial or Specific Open Source (e.g., Freeware, GNU, Apache)

-   License URI – This column should provide enough information that the
    reader could go get the license if needed (e.g., a link to the
    website or a data source for obtaining more information on the
    license).

<span id="_Toc219294958" class="anchor"></span>Table 2.1-1 Platform
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
<td>RedHat Enterprise Linux</td>
<td>RedHat</td>
<td>6.1</td>
<td>Operating System</td>
<td><p>Commercial</p>
<p>Run-time</p></td>
<td><a href="http://redhat.com"><span class="underline">http://redhat.com</span></a></td>
</tr>
<tr class="even">
<td>ASB</td>
<td>XYZ Corp</td>
<td>8.7</td>
<td>Infrastructure</td>
<td><p>Commercial</p>
<p>Run-time</p></td>
<td><a href="http://xyzcorp.com"><span class="underline">http://xyzcorp.com</span></a></td>
</tr>
<tr class="odd">
<td>ESXi</td>
<td>VMWare</td>
<td>5.5</td>
<td>Virtualization</td>
<td><p>Commercial</p>
<p>Run-time</p></td>
<td><a href="http://esxi.com"><span class="underline">http://esxi.com</span></a></td>
</tr>
<tr class="even">
<td>HTTPD</td>
<td>Apache</td>
<td>2.4.9</td>
<td>Data Transfer</td>
<td>Apache 2.0</td>
<td><a href="http://apache.org"><span class="underline">http://apache.org</span></a></td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
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

This section identifies all software (first, second, and third party)
that are required to run the Platform even if a license is not required
as shown in Table 2.2-1, Platform Software Dependencies.

This table may include CAL dependencies required for other elements of
the ASB (e.g., OCE, Subsystem), but specific software required to build
and run the CAL are listed in the CAL Libraries listing in Table 9.2-1,
CAL Licenses and Libraries. For a Platform containing at least one
virtualized environment, this table would include the software being
used to implement the virtualized environment(s). Duplication between
the two tables is permissible.

The columns in Table 2.2-1, Platform Software Dependencies, should
contain the following information:

-   Name/Provider/Version – These columns should identify the software
    by name, provider, and the version

-   Purpose – This column should identify the overall purpose of the
    software

-   OS – This column should identify the operating system and version
    number, if applicable, that the software is built for

-   OCE/Non-OCE/Subsystem/Platform – This column should identify where
    the software will be used. It can be one or more either OCE,
    Non-OCE, Subsystem, and/or Platform.

<span id="_Toc219294959" class="anchor"></span>Table 2.2-1 Platform
Software Dependencies

<table>
<thead>
<tr class="header">
<th>Name</th>
<th>Provider</th>
<th>Version</th>
<th>Purpose</th>
<th>OS</th>
<th>OCE / Non-OCE / Subsystem / Platform</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ActiveMQ</td>
<td>Apache</td>
<td>5</td>
<td>Message Broker for CAL implementation</td>
<td>Windows 7 Professional / RedHat6.2</td>
<td>OCE/ Non-OCE / Subsystem</td>
</tr>
<tr class="even">
<td>Java environment</td>
<td>Oracle</td>
<td>1.8.0</td>
<td>Running Java applications on mission processing</td>
<td>Windows 7 Professional/ Red Hat 6.2</td>
<td>Non-OCE</td>
</tr>
<tr class="odd">
<td>Elastic Container Service (ECS)</td>
<td>Amazon Web Services (AWS)</td>
<td>N/A</td>
<td>Container Orchestration</td>
<td>Amazon Linux 2</td>
<td>Platform</td>
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

Abstract Service Bus (ASB)
==========================

This section documents the Platform’s network infrastructure and data
exchanges.

This section may include any architecture description and details of the
network.

OMS Message Set
---------------

This section identifies the ASB Identifier, Baseline OMS Message Schema,
and the Extension Schema as shown in Table 3.1-1, OMS Message Set.

The columns in Table 3.1-1, OMS Message Set, should contain the
following information:

-   ASB Identifier – This column should identify the identifier for each
    version of the ASB that is supported on this OMS Platform

-   Baseline OMS Message Schema – This column should identify the
    baseline OMS Message Schema that is used on the ASB identified in
    this row, which should be an official UCI Schema release

-   Extension Schema(s) – This column should identify all of the
    extension schemas that are used on the ASBs identified in this row.

<span id="_Toc219294960" class="anchor"></span>Table 3.1-1 OMS Message
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
<td>ActiveMQ_ASB</td>
<td>UCI 2.2</td>
<td>Ghost Detector Extension Schema v1.8</td>
</tr>
<tr class="even">
<td>DDS_ASB</td>
<td>UCI 2.2</td>
<td><p>OACWG package APx3</p>
<p>(provide .xsd reference)</p></td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Network
-------

This section identifies details of the network(s) such as the bandwidth
and network routing/switching.

This should include identification of IPv4 or IPv6 support and identify
which protocols (UDP, TCP, etc.) are supported on the ASB. It should
describe the network architecture including endpoint connections.

In the case of a Platform utilizing virtualized environment(s), this
section should contain the details of the implemented architecture that
is being instantiated in the virtualized environment(s). Include only
utilized capabilities of the virtualization environment(s).

### Network Interconnect Diagram

This section describes the endpoint connections, interface speeds, and
any limitations of the Platform network architecture.

Diagram should include network architecture including endpoint
connections, interface speeds (e.g., 10/100, GigE, 10GigE, etc.), any
limitations (e.g., QoS, Bandwidth Limits) and a legend. This diagram
should only contain details specific to the Platform and not contain any
details regarding Subsystems, Services or Isolators.

Figure 3.2-1, Network Interconnect Diagram, is a representation of the
Platform’s network.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE. INCLUDE AN APPROPRIATE
FIGURE FOR YOUR SYSTEM &gt;&gt;

<img src="media/image2.png" style="width:6.5in;height:5.875in" />

<span id="_Toc219294954" class="anchor"></span>Figure 3.2-1 Network
Interconnect Diagram

A description of Figure 3.2-1 will be placed here.

Table 3.2-1, Network Segmentation, lists the network segments, the
method used for segmentation and a description.

The hardware is described in &lt;hardwareReferenceDocument&gt; and the
&lt;configurationGuideBook&gt; document provides guidance on changing
its configuration.

-   Network Segment – Identify the network segment or IP address ranges

-   Segmentation Method – The method used to create the segmentation

-   Description – A description of the network segment

<span id="_Toc219294961" class="anchor"></span>Table 3.2-1 Network
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
<td>10.1.1.0/24</td>
<td>Private VLAN</td>
<td>Mission Processing</td>
</tr>
<tr class="even">
<td>10.1.3.0/24</td>
<td>VLAN</td>
<td>Mission Processing</td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Ports & Protocols

This section identifies the ports and protocols that are in use and
accessible on the ASB network or bus.

Using the Table 3.2-2, Open Ports and Protocols, and Table 3.2-3,
Product/Data and Data Transfer Servers, identify the ports and protocols
that are in use and accessible on the ASB network or bus. Local loopback
connections, serial connections or any other non-accessible connectivity
(e.g., Ethernet cross-over cable) is not required to be documented.

These tables are inclusive and any port not listed here is assumed to be
disabled.

The following table summarizes the open ports and protocols on the
Mission Package.

-   Port – identify the network ingress port number and the TCP or UDP
    protocol being used

-   Protocol – identify the protocol being used on the open port

-   Process/Service – identify the process (e.g., on Linux, the netstat
    command will provide OS process names) or Service (e.g., on Linux,
    the nmap command will provide OS Service names) that has the port
    open

-   Address – the IP address of the system whose port is open if known,
    otherwise the URI used to access the product/data and Data Transfer
    servers

-   Purpose – identify the purpose of the open port

-   Restriction Mechanism – identify the method(s) that are implemented
    or expected to constrain or restrict access to the listed port,
    protocol, and process. This should include identification of
    expected hardware, software, and algorithms associated with the
    mechanism. If no mechanisms implemented or expected, input “None” in
    the cell

Table 3.2-2, Open Ports and Protocols, identifies the ports and
protocols on the Mission Package.

<span id="_Toc219294962" class="anchor"></span>Table 3.2-2 Open Ports
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
<td>21</td>
<td>TCP</td>
<td>FTP</td>
<td>vsftpd</td>
<td>10.1.1.11</td>
<td>FTP Server</td>
<td>iptables firewall</td>
</tr>
<tr class="even">
<td>111</td>
<td>TCP</td>
<td>RPC Portmapper</td>
<td>Portmapper</td>
<td>10.1.1.11</td>
<td>NFS Server</td>
<td>iptables firewall</td>
</tr>
<tr class="odd">
<td>2049</td>
<td>TCP</td>
<td>NFSv3</td>
<td>nfsd</td>
<td>10.1.1.11</td>
<td>NFS Server</td>
<td>iptables firewall</td>
</tr>
<tr class="even">
<td>3260</td>
<td>TCP</td>
<td>iSCSI</td>
<td>iscsid</td>
<td>10.1.1.100</td>
<td>iSCSI</td>
<td>iptables firewall</td>
</tr>
<tr class="odd">
<td>61616</td>
<td>TCP</td>
<td>OpenWire</td>
<td>activemq</td>
<td><a href="https://activemq.platform:61616"><span class="underline">https://activemq.platform:61616</span></a></td>
<td>CAL Message Broker</td>
<td>iptables firewall</td>
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

Table 3.2-3, Product/Data and Data Transfer Servers, identifies the
products being sent or received by Data Transfer server.

The following table identifies the products being sent or received by
the Data Transfer server.

-   Client Address – the IP address of the client if known, otherwise
    the client’s Fully Qualified Domain Name

-   Product/Data – the product or data item being sent or received from
    a server

-   Format – The format of the product (identify OMS approved data
    format) or data type (ASCII file, xml, binary, etc.)

-   Send/Receive – Send = upload, write or Receive = download, read

-   Data Transfer Server – the IP address of the Data Transfer Server if
    known, otherwise the Data Transfer Server’s URI

<span id="_Toc219294963" class="anchor"></span>Table 3.2-3 Product/Data
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
<td>10.1.1.12</td>
<td>Sensor Product Files</td>
<td>NITF</td>
<td>Receive</td>
<td><a href="ftp://ftpserver.local/products/"><span class="underline">ftp://ftpserver.local/products/</span></a></td>
</tr>
<tr class="even">
<td>producer1.platform</td>
<td>Sensor Product Files</td>
<td>JPEG 2000</td>
<td>Send</td>
<td><a href="ftp://producer1.platform/products/"><span class="underline">ftp://producer1.platform/products/</span></a></td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Identify the mechanism for enabling the ports and protocols for data
transfers. If there is no mechanism for enabling or disabling ports and
protocols then this should be stated here. (Ex. iptables)

### Network Address Information

This section identifies the network segment, IP Address Space (& network
mask), IP Gateways and method for assigning IP addresses as shown in
Table 3.2-4, Networking Information.

Using Table 3.2-4, Networking Information, identify the network segment,
IP Address Space (& network mask), IP Gateways and method for assigning
IP addresses. Use of DNS services (or DDNS) to locate Services should be
described and a reference to the implementation documentation should be
included.

-   Network Segment – The IP address space(& network mask)

-   Gateway – The IP Gateway address

-   DNS Server – One or more IP addresses of DNS Servers used to resolve
    hostnames. “DHCP configured” is used to denote automatic
    configuration with DHCP. N/A is used to denote the segment uses only
    static addressing with no DNS hostname resolution.

-   IP Address Assignment – The method used to assign IP addresses
    (e.g., static or DHCP)

<span id="_Toc219294964" class="anchor"></span>Table 3.2-4 Networking
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
<td>10.1.1.0/24</td>
<td>10.1.1.1</td>
<td>DHCP configured</td>
<td>DHCP (10.1.1.2)</td>
</tr>
<tr class="even">
<td>10.1.3.0/24</td>
<td>10.1.3.1</td>
<td><p>10.1.3.2</p>
<p>10.1.3.3</p></td>
<td>Static</td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

Data Transfer
=============

This section details the Platform’s data storage; data transfer
integrity and confidentiality as well as the data transfer
configuration.

Data Storage
------------

This section identifies the Platform’s data storage capability that can
be utilized by properly authenticated OMS Services and Subsystems as
shown in Table 4.1-1, Platform Data Storage Details.

In the case of a Platform utilizing virtualized environment(s), this
section should contain the details of the implemented architecture that
is being instantiated in the virtualized environment(s). Include only
utilized capabilities of the virtualization environment(s).

One or more tables, structured like Table 4.1-1, Platform Data Storage
Details, may be used to document the Platform’s Data Transfer Protocols.
Each table should contain the following information:

-   Data Store Address – This column identifies the data store address
    of the TFTP/FTP/NFS/HTTP server which is addressable via a URI

-   Data Store Label – The identifier for the data that is stored or
    retrieved. The Data Store Label should be a unique reference within
    this table with the purpose to specify a range of cybersecurity
    attributes associated with the referenced data store

-   Shared Directories – This column identifies the shared directories
    that are accessible via the data transfer protocols. Specifically,
    if there are unique folders for software applications (e.g., OFPs),
    Configuration Files or Data Products then each should be identified

-   Storage Capacity – This column identifies storage capacity allocated
    for the directory. Note: a separate row should be used for each
    directory if there are storage capacity limits per folder

-   Non-Volatile Storage (Yes/No) – If the storage stores data in
    volatile storage which is no longer accessible after a power-cycle
    then input “No” otherwise input “Yes”

-   Protection In Place (No/C/I/CI):

<!-- -->

-   No – if neither confidentiality nor integrity mechanisms are in
    place

-   C – Confidentiality mechanisms, such as encryption, are in place. If
    there is a confidentiality mechanism in place, the additional
    details should be listed in Table 4.1-3, Data Storage
    Confidentiality

-   I – Integrity mechanisms, such as digital signature, are in place.
    If there is an integrity mechanism in place, the additional details
    should be listed in Table 4.1-4, Data Storage Integrity

-   CI – Confidentiality and Integrity mechanisms are in place. If there
    are confidentiality and integrity mechanisms in place, the
    additional details should be listed in Table 4.1-3, Data Storage
    Confidentiality, and Table 4.1-4, Data Storage Integrity.

<!-- -->

-   Data Transfer Protocol(s) – This column identifies the supported
    protocols and methods for accessing the data storage from either a
    Service or Subsystem. Refer to the “Data Transfer Protocols and
    APIs” Table in the OMS Standard, OMSC-STD-001, for allowed protocols

<span id="_Toc219294965" class="anchor"></span>Table 4.1-1 Platform Data
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
<td>10.1.1.100</td>
<td>TFTP Data Store</td>
<td>/SW_APP/[Service name]/</td>
<td>1 TB</td>
<td>Yes</td>
<td>C</td>
<td>TFTP</td>
</tr>
<tr class="even">
<td>10.1.1.100</td>
<td>FTP Data Store</td>
<td>/subsystems/[Subsystem name]/</td>
<td>2 TB</td>
<td>Yes</td>
<td>I</td>
<td>FTP</td>
</tr>
<tr class="odd">
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

No – Neither confidentiality nor integrity mechanisms are in place

C – Confidentiality mechanisms are in place

I – Integrity mechanisms are in place

CI – Confidentiality and Integrity mechanisms are in place

### Data Storage Access Controls

This section identifies the methods for identification authentication,
access restrictions, and audit logging as shown in Table 4.1-2, Data
Storage Access Control Mechanisms.

Data Storage Access Control is documented in Table 4.1-2, Data Storage
Control Mechanisms. The table entries should specify the methods for
identification, authentication, access restrictions and audit logging.
The following table provides a template for file based data transfer
protocol details. If this section is not applicable, mark as “Not
Applicable” with a rationale and the first empty cell of the table with
“N/A”.

The columns in Table 4.1-2, Data Storage Access Control Mechanisms,
should contain the following information. A separate section within the
table should be used for each Data Transfer protocol listed in Table
4.1-1, Platform Data Storage Details.

-   Mechanism – This column lists the Access Control mechanisms

<!-- -->

-   Identification – mechanism used to identify users

-   Authentication – mechanism used to authenticate users and permitted
    to use the resource

-   Access Control – mechanisms put in place to restrict users,
    associated access and resources

-   Audit Logging – mechanism used to perform logging of data transfer
    resource access

<!-- -->

-   Implementation Summary – The implementation summary column should
    contain a brief summary of how the mechanism is implemented

<span id="_Toc219294966" class="anchor"></span>Table 4.1-2 Data Storage
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
<td>The FTP Server Access Control consists of restricting users (ftpusers), restricting commands (ftpaccess) and allowing only identified hosts being able to access the server (ftphosts). Uploads are restricted by users or groups into identified folders and file downloads of specific files are prevented (ftpaccess). Accounts are restricted to FTP access only by limiting shell access (/bin/false)</td>
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
<td>The NFS Server Access Control consists of restricting users (root_squash), restricting shared directories (/etc/exports) and allowing only identified hosts being able to access the server (/etc/hosts.allow).</td>
</tr>
<tr class="even">
<td>Audit Logging</td>
<td>All commands issued by NFS users are logged as specified in the configuration (/etc/nfs/nfslog.conf).</td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>

### Data Storage Confidentiality Mechanisms

This section identifies the specific mechanisms provided for Data
storage as shown in Table 4.1-3, Data Storage Confidentiality.

Data Storage Confidentiality Mechanisms should be documented in Table
4.1-3, Data Storage Confidentiality.

Table 4.1-3, Data Storage Confidentiality, should detail the specific
confidentiality mechanisms provided for Data Storage.

-   Data Store Label – The identifier for the protected data that is
    stored or retrieved. The Data Store Label should be a unique
    reference within this table with the purpose to specify a range of
    cybersecurity attributes associated with the referenced data store

-   Protected Data – The information items to which the confidentiality
    mechanism is applied

-   Confidentiality Mechanism – Identify the method to provide
    confidentiality. This should include identification of applicable
    hardware, software, and algorithm associated with the implemented
    mechanism

-   Implementation Details – Details on how the confidentiality
    mechanism is implemented and/or include a reference to other
    documents and any additional information for clarification

<span id="_Toc219294967" class="anchor"></span>Table 4.1-3 Data Storage
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
<td>FTP Data Store</td>
<td>Applications &amp; Payload Products</td>
<td>NSA Type-1</td>
<td>See DataStore-Encryption.docx for further details</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Data Storage Integrity Mechanisms

This section identifies the specific integrity mechanisms provided for
Data Storage as shown in Table 4.1-4, Data Storage Integrity.

Table 4.1-4, Data Storage Integrity, should detail the specific
integrity mechanisms provided for Data Storage.

-   Data Store Label – The identifier for the protected data that is
    stored or retrieved. The Data Store Label should be a unique
    reference within this table with the purpose to specify a range of
    cybersecurity attributes associated with the referenced data store

-   Protected Data – The information items to which the integrity
    mechanism is applied

-   Integrity Mechanism – The mechanism used to guarantee integrity

-   Implementation Details – Details on how the integrity mechanism is
    implemented and/or include a reference to other documents and any
    additional information for clarification

<span id="_Toc219294968" class="anchor"></span>Table 4.1-4 Data Storage
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
<td>FTP Data Store</td>
<td>Applications &amp; Payload Products</td>
<td>SHA-256</td>
<td>Hash values calculated and provided in <strong>ProductMetadata</strong></td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

This section identifies the confidentiality mechanisms the Platform
supports for data transfers, as shown in Table 4.2-1, Data Transfer
Confidentiality Mechanisms. If this section is not applicable, mark as
“Not Applicable” with a rationale and the first empty cell of the table
with “N/A”.

The columns in Table 4.2-1, Data Transfer Confidentiality Mechanisms,
should contain the following information:

-   Protected Data – The information items to which the confidentiality
    mechanism is applied

-   Confidentiality Mechanism – Identify the method(s) used by the
    Platform to provide confidentiality. This should include
    identification of applicable hardware, software, and algorithm
    associated with the implemented mechanism. For Secure Data transfers
    utilizing a VPN solution (e.g., IPsec, SSL) provide the
    implementation software name (e.g., strongSwan), type of VPN, and a
    pointer to the configuration file

-   Implementation Details – Details on how the confidentiality
    mechanism is implemented with appropriate references to other
    documents and additional information for clarification.

<span id="_Toc219294969" class="anchor"></span>Table 4.2-1 Data Transfer
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
<td>Sensor Product Files</td>
<td>Suite B algorithm</td>
<td>Decrypted using AES-256 algorithm upon receipt</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

If this section is not applicable, mark as “Not Applicable” and the
first empty cell of the table with “N/A”.

The columns in Table 4.3-1, Data Transfer Integrity Mechanisms, should
contain the following information:

-   Protected Data – The information items to which the integrity
    mechanism is applied

-   Integrity Mechanism – Identify the method(s) used by the Platform to
    provide integrity. This should include identification of applicable
    hardware, software, and algorithm associated with the implemented
    mechanism

-   Implementation Details – Details on how the integrity mechanism is
    implemented and/or include a reference to other documents and any
    additional information for clarification.

<span id="_Toc219294970" class="anchor"></span>Table 4.3-1 Data Transfer
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
<td>Sensor Product Files</td>
<td>Hash/Digital Signature</td>
<td>Sensor Product Files are digitally signed</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

For example: IPv4 and/or IPv6, NFS - version x, UDP transport, no client
authentication, etc.

### Data Transfer Protocol Details

This section identifies the Data Transfer methods provided by this
Platform and the configuration details associated with the Data Transfer
methods as shown in Table 4.4-1, Platform Data Transfer Configuration.

The columns in Table 4.4-1, Platform Data Transfer Configuration, should
contain the following information:

-   Data Transfer Server – A resolvable location or URI for each server
    on the Platform

-   Data Transfer Protocol – This column should be one of the supported
    Data Transfer Protocols. Each row of the table will cover a single
    method. Every supported protocol should be documented in its own row

-   Version – This column identifies the specific version of the Data
    Transfer Protocol. Use SCAP nomenclature if available and
    appropriate, for example FTP-0.10.-11.1

-   Configuration Details – This column identifies any specific
    configuration details for a given Data Transfer Protocol. For
    example, specific protocol versions, unsupported commands,
    configured ports, share limitations, should be indicated.

<span id="_Toc219294971" class="anchor"></span>Table 4.4-1 Platform Data
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
<td><span class="underline">FTP://&lt;something&gt;</span></td>
<td>FTP</td>
<td>FTP-0.10.-11.1</td>
<td>passive ftp only (ports: 50000-50009)</td>
</tr>
<tr class="even">
<td><span class="underline">NFS://&lt;something&gt;</span></td>
<td>NFS</td>
<td>nfs-utils – 1.2.3</td>
<td>NFSv3, Portmapper (port:111), read only export (/sw_app/), read/write export (/data/), secure-ports (1-1024) from NFS clients</td>
</tr>
<tr class="odd">
<td><span class="underline">RTP://&lt;something&gt;</span></td>
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

Mission Processing
==================

This section documents the Platform’s mission processing architecture
including both the required Open Computing Environment (OCE) and Other
Mission Processing.

Open Computing Environment (OCE)
--------------------------------

This section documents the Platform’s OCE OMS mission processing
architecture and describes specific tool chains for building in the
various OCE environments.

An OMS Platform is responsible for providing OCE implementations for its
Mission Package. A Platform must provide at least one OCE
implementation. Define the OCE implementation(s) in the sub-sections
below.

In the case of a Platform utilizing virtualized environment(s), this
section should contain the details of the implemented architecture that
is being instantiated in the virtualized environment(s). Include only
utilized capabilities of the virtualization environment(s).

### OCE Processor Types, Operating Systems, and Configuration

This section documents the processor architecture/type, processor
memory, processor quantity, and operating systems (type and 32 or 64
bit) for each processor in the OCE.

### General Environment

This section documents the general environment provided by the OCE.

#### Build Environment and Tool Chain

This section documents the specific build environment for an OCE.

This identifies supported compilers and specific compiler options that
are required to build a Service in the OCE provided by this Platform.

This section documents the specific binary format for any OCE provided
binaries. This will include the format of the CAL libraries that will
run in the OCE.

This section documents how a Service is compiled for an OCE target
implementation. This section gives explicit instructions for building
for a particular OCE target.

#### Isolation Layer

This section documents the implemented Façade interfaces for this
Platform as defined in the OMS OS Façade Specification.

This section documents how the Façade implementation supports the Data
Transfer methods, if specific client versions of software are used for
Data Transfer on the OCE, these should be called out as well.

#### Time

This section documents how time synchronization is supported by the OCE.

This section should include how time is provided to applications and the
method for setting the system clock.

### Java Environment

This section documents the specific Java environment provided by the
Java-based OCE.

If a Java-based OCE is not provided per system policy, then this section
will be identified as “Not allowed per system policy.”

#### Build Environment and Tool Chain

This section documents the specific build environment for a Java-based
OCE and how a Service is compiled for an OCE target implementation.

This section should identify any Java tool chains required for building
a Java Service for running in the Java-based OCE.

This section documents how a Service is compiled for an OCE target
implementation. This section gives explicit instructions for building
for a particular OCE target.

#### Java Data Transfer

This section documents the C/C++ libraries (if any) that are provided as
part of the Java-based OCE and that the Java environment is reliant upon
in order to perform data transfer operations.

Via its JNI interface, the Java environment will use the support
provided by these libraries to transfer data to and from applications
running in the Java environment. If the Java environment is reliant upon
specific versions of these libraries, then those versions should be
documented as well.

#### Time 

This section documents how time synchronization is supported by the
Java-based OCE.

This section should include how time is provided to applications and the
method for setting the system clock.

### Service Deployment

This section documents how Services are deployed and managed within the
OCE.

This includes any provisions for VMs/Appliances, Containerization, etc.
This should identify requirements placed on a Service to run in the
environment and for using a CAL or Data Transfers. This section should
also document any management functionality of Service packaging.

Other Mission Processing
------------------------

This section documents any Platform non-OCE Other Mission Processing
architecture and describes specific tool chains for building in the
Other Mission Processing environments.

In the case of a Platform utilizing virtualized environment(s), this
section should contain the details of the implemented architecture that
is being instantiated in the virtualized environment(s). Include only
utilized capabilities of the virtualization environment(s).

If all mission processing is OCE-based, then document this section and
its subsections as “Not Applicable” with a rationale.

### Other Mission Processor Types, Configuration and Interfaces

This section documents the architecture, type, memory, and quantity of
processors provided by the Platform for Other Mission Processing.

This may also include secure processors for OMS processing. This section
also documents any other interfaces that may be available on the
Platform, such as a 1553 bus.

### Other Mission Processing Tool Chain Description

This section documents how a Service is compiled for the Other Mission
Processing target implementation.

### OMS Attributes for Other Mission Processing

This section describes the OMS elements resident on the Other Mission
Processing solution.

Other Mission Processing may also host OMS software Services, functions,
and Adapters. Describe the OMS elements resident on the Other Mission
Processing solution. This may include the CAL, connections to the ASB,
provisions to share time reference/time synchronization, position
information processing, Data Transfer design, Special Signals
implemented, and Security Information Exchanges.

### Service Deployment

This section documents how Services are deployed and managed within the
Other Mission Processing.

This includes any provisions for VMs/Appliances, Containerization, etc.
This should identify requirements placed on a Service to run in the
environment and for using a CAL or Data Transfers. This section should
also document any management functionality of Service packaging.

Time and Position Information
=============================

This section may not be tailored expect where indicated.

This section describes the time and position information provided by the
OMS Platform.

If any functionality in this section is not provided by the OMS
Platform, then that section can be marked as “Not Applicable” with a
rationale, but must contain a reference to the OMS Service Contract that
describes how the OMS Mission Package will receive that capability
(e.g., using an Isolator).

Time Reference and Time Synchronization
---------------------------------------

Platform provider must complete Table 6.1-1.

This section identifies the time reference and its sources and documents
its precision and accuracy as well as the method of distributing a time
reference for synchronization.

A Platform utilizes one or more time sources which may be internal or
external to the Mission Package to provide a time reference.

All time reference methods implemented per OMS Standard, OMSC-STD-001,
“Time Reference,” should be documented in this section. Examples of a
time reference are a GPS-disciplined oscillator, an Atomic clock, or an
NTP server synchronized to an external time server.

In the case of virtualized environments, this section can reference the
corresponding Section 8.1.6, Time, for further implementation details.

Table 6.1-1 Time Synchronization Protocols, identifies all the time
reference methods provided by the Platform and implemented per OMS
Standard, OMSC-STD-001, “Time Reference.”

The cells in this table specifies the time reference methods according
to the following column definitions:

-   Time Synchronization Protocol: this column lists all the approved
    Time Synchronization Protocol a Platform can provide as identified
    in the OMS Standard, OMSC-STD-001.

-   Provided (Y/N)?: this column identifies which approved Time
    Synchronization Protocol the Platform provides. At least one Time
    Synchronization Protocol should be provided.

<span id="_Toc219294972" class="anchor"></span>Table 6.1-1 Time
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
<td>N</td>
</tr>
<tr class="even">
<td>IEEE 1588-2019 PTP</td>
<td>Y</td>
</tr>
<tr class="odd">
<td>RFC 1119 NTP</td>
<td>N</td>
</tr>
</tbody>
</table>

When high fidelity time synchronization is required, all time reference
methods implemented per OMS Standard, OMSC-STD-001, “Time Reference,”
should be documented in Table 6.1-2 High Fidelity Time Reference and
Time Synchronization Mechanisms.

The cells in this table specifies the time reference methods according
to the following column definitions:

-   Time Synchronization Mechanisms: this column indicates Approved Time
    Synchronization Mechanism provided by the Platform as identified in
    the OMS Standard, OMSC-STD-001.

-   Provided (Y/N)?: this column identifies which approved Time
    Synchronization Protocol the Platform provides.

<span id="_Toc219294973" class="anchor"></span>Table 6.1-2 High Fidelity
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
<td>N</td>
</tr>
<tr class="even">
<td>1 PPS</td>
<td>Y</td>
</tr>
<tr class="odd">
<td>PTTI</td>
<td>N</td>
</tr>
</tbody>
</table>

When 1 PPS time synchronization mechanism is provided, the
**SystemTimeAtReference** message is required. In this case, the
Platform directly provides the **SystemTimeAtReference** message, and
the respective fields and characters should be identified in Table
6.1-3, **SystemTimeAtReference** Inputs and Outputs.

The **SystemTimeAtReference** message is only applicable when providing
a 1 PPS time synchronization mechanism. If the Platform does not provide
**SystemTimeAtReference** message enter “N/A” in first blank cell. The
cells in this table specify the **SystemTimeAtReference** according to
the following column definitions:

-   Message Primitive (MP) – this column indicates the Message
    Primitive, defined in the OAC-SPC-001 UCI Schema Style and Design
    Specification and corresponds to the PRIMITIVE\_TYPE tag annotation
    for the message in the UCI schema message definitions file

-   Input/Output (I/O) – this column indicates the data exchange is an
    output (O)

-   Data Exchange (DE) – this column indicates the Data Exchange is an
    OMS Message (M)

-   Data Exchange Name – this column indicates the message name of the
    Data Exchange. The only allowed message is
    **SystemTimeAtReference**. The rows should indicate all the
    combinations of this message, topic names, and corresponding rates
    being provided by the Platform

-   Data Exchange Information (e.g., Topic Name for Messages or Protocol
    for Data Transfers) – this column indicates the specific topic name
    of which the message is published

-   Level of Mandate (LoM) – this column states this message is
    mandatory (M)

-   Periodicity (P) – This column details indicate this message is
    periodic (P)

-   Nominal Response Time or Nominal Periodic Rate – This column details
    the informative (not normative) nominal response time (in seconds)
    or a periodic rate (in Hertz)

-   Max Response Time or Max Periodic Rate – This column details the
    informative (not normative) maximum response time (in seconds) or a
    maximum periodic rate (in Hertz)

-   Appendix C Mapping – this column provides the cross reference to the
    workbook/tab name for the message details contained in Appendix C.

<span id="_Toc219294974" class="anchor"></span>Table 6.1-3
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
<td>1PPS_SystemTime</td>
<td>M</td>
<td>P</td>
<td>1 Hz</td>
<td>1 Hz</td>
<td>1PPS_SystemTime</td>
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

This section may not be tailored except where indicated. The source of
the **PositionReport** and/or **PositionReportDetailed** should be
identified in this section.

If position information is not required, mark this section and its
subsections as “Not Applicable” with a rationale and the first empty
cell of each table with “N/A”. When position information is required,
Section 6.2.1, Section 6.2.2, or both must be filled out as applicable.

This section documents the accuracy and precision of the position
information.

### Position Information Indirectly Provided for the Platform

When a Subsystem, Service, or Isolator is indirectly providing the
position information to the Platform, the source of the
**PositionReport** and/or **PositionReportDetailed** should be
identified in Table 6.2-1 Source Providing Position Information.

If the Platform directly provides the **PositionReport** and/or
**PositionReportDetailed** messages, mark the first empty cell of each
applicable row in Table 6.2-1, Source Providing Position Information,
with “N/A”.

When applicable, additional rows can be added as shown in Table 6.2-1,
Source Providing Position Information, to support multiple sources
providing **PositionReport** and/or **PositionReportDetailed**. The
cells in this table specifies the Service Contract associated with the
Subsystem, Service, or Isolator indirectly providing the position
information for the Platform according to the following column
definitions:

-   Position Information Provided: this column identifies the position
    information provided by the identified Subsystem, Service, or
    Isolator (**PositionReport** and/or **PositionReportDetailed**
    messages only)

-   Subsystem/Service/Isolator: this column indicates the Subsystem,
    Service, or Isolator providing the position information on behalf of
    the Platform

-   Service Contract: this column indicates the name of the Service
    Contract of the Subsystem, Service, or Isolator providing the
    position on behalf of the Platform. The necessary input/output of
    the position information should be captured in the identified
    Service Contract.

<span id="_Toc219294975" class="anchor"></span>Table 6.2-1 Source
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
<td>ServiceA</td>
<td>ServiceA_ServiceContract</td>
</tr>
<tr class="even">
<td>PositionReportDetailed</td>
<td>SubsystemA</td>
<td>SubsystemA_ServiceContract</td>
</tr>
<tr class="odd">
<td>PositionReport</td>
<td>SubsystemB</td>
<td>SubsystemB_ServiceContract</td>
</tr>
<tr class="even">
<td>PositionReportDetailed</td>
<td>SubsystemB</td>
<td>SubsystemB_ServiceContract</td>
</tr>
</tbody>
</table>

### Position Information Directly Provided by Platform

When the Platform is directly providing the position information via the
**PositionReport** and/or **PositionReportDetailed** messages, the
respective fields and characters should be identified in Table 6.2-2,
Position Information Processing Inputs and Outputs.

If a Subsystem, Service, or Isolator indirectly provides the
**PositionReport** and/or **PositionReportDetailed** messages, mark the
first empty cell of each applicable row Table 6.2-2, Position
Information Processing Inputs and Outputs, with “N/A”.

When applicable, additional rows can be added as shown in Table 6.2-2,
Position Information Processing Inputs and Outputs to support multiple
publication characteristics of the **PositionReport** and/or
**PositionReportDetailed** messages. The cells in this table specifies
the position information according to the following column definitions:

-   Message Primitive (MP) – this column indicates the Message
    Primitive, defined in the OAC-SPC-001 UCI Schema Style and Design
    Specification and corresponds to the PRIMITIVE\_TYPE tag annotation
    for the message in the UCI schema message definitions file

-   Input/Output (I/O) – this column indicates the data exchange is an
    output (O)

-   Data Exchange (DE) – this column indicates the Data Exchange is an
    OMS Message (M)

-   Data Exchange Name – this column indicates the message name of the
    Data Exchange. The only allowed messages are **PositionReport** or
    **PositionReportDetailed**. The rows should indicate all the
    combinations of these messages, topic names, and corresponding rates
    being provided by the Platform

-   Data Exchange Information (e.g., Topic Name for Messages or Protocol
    for Data Transfers) – this column indicates the specific topic name
    of which the message is published

-   Level of Mandate (LoM) – this column states this message is
    mandatory (M)

-   Periodicity (P) – This column details indicate this message is
    periodic (P)

-   Nominal Response Time or Nominal Periodic Rate – This column details
    the informative (not normative) nominal response time (in seconds)
    or a periodic rate (in Hertz). Refer to the OMS Standard,
    OMSC-STD-001, for approved **PositionReport** nominal rates and
    **PositionReportDetailed** approved nominal publish rates

-   Max Response Time or Max Periodic Rate – This column details the
    informative (not normative) maximum response time (in seconds) or a
    maximum periodic rate (in Hertz)

-   Appendix C Mapping - this column provides the cross reference to the
    workbook/tab name for the message details contained in Appendix C.
    When multiple **PositionReport** and/or **PositionReportDetailed**
    Data Exchanges exist, the Appendix C Mapping can be the same
    Appendix C or specific Appendix C.

<span id="_Toc219294976" class="anchor"></span>Table 6.2-2 Position
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
<td>PositionReportNetwork1</td>
<td>M</td>
<td>P</td>
<td>1 Hz</td>
<td>1 Hz</td>
<td>PositionReportNetwork1</td>
</tr>
<tr class="even">
<td>D</td>
<td>O</td>
<td>M</td>
<td>PositionReport</td>
<td>PositionReportNetwork2</td>
<td>M</td>
<td>P</td>
<td>1 Hz</td>
<td>1 Hz</td>
<td>PositionReportNetwork2</td>
</tr>
<tr class="odd">
<td>D</td>
<td>O</td>
<td>M</td>
<td>PositionReportDetailed</td>
<td>PositionReportDetailedRate1</td>
<td>M</td>
<td>P</td>
<td>50 Hz</td>
<td>50 Hz</td>
<td>PositionReportDetailedRate1</td>
</tr>
<tr class="even">
<td>D</td>
<td>O</td>
<td>M</td>
<td>PositionReportDetailed</td>
<td>PositionReportDetailedRate2</td>
<td>M</td>
<td>P</td>
<td>100 Hz</td>
<td>100 Hz</td>
<td>PositionReportDetailedRate2</td>
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

This section documents all of the CAL implementations.

Every CAL implementation should be documented and identified in the
subsections below.

CAL Available Implementations
-----------------------------

This section documents the method developers link CAL libraries into
applications.

For specific implementations, this section documents how developers can
link CAL libraries into applications.

Table 7.1-1, CAL Versions Available, identifies the operating system,
programming language, CAL Schema Compiler Version number, CAL
Implementation Version number, and target runtime location.

Additionally, each CAL listed should identify the operating system,
programming language, CAL Schema Compiler Version number, CAL
Implementation Version number, and target runtime location, or
Subsystems in general, and should be provided in Table 7.1-1, CAL
Versions Available.

The columns in Table 7.1-1, CAL Versions Available, should contain the
following information:

-   CAL Identifier – Provide an identifier for each CAL to uniquely
    identify it from other CALs on the same OMS Platform

-   Operating System – Provide the operating system the CAL
    Implementation is run on

-   Programming Language – Provide the applicable programming language
    for each CAL. Language-specific CALs should choose C++ or Java (and
    specify version). Language-agnostic CALs should list supported
    protocols and message formats (e.g. WebSocket/OMS JSON)

-   OMS Specification Version – Provide the specification version that
    defines the API the CAL implements

-   CAL Implementation Version – Provide the version of the CAL
    Implementation

-   OMS Message Set – The schema the CAL implementation supports

-   OCE / Non-OCE / Subsystem / Isolator / Platform – Provide the target
    runtime location of the CAL.

<span id="_Toc219294977" class="anchor"></span>Table 7.1-1 CAL Versions
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
<td>OCE C++ CAL</td>
<td>RedHat Enterprise Linux 6.1</td>
<td>C++</td>
<td>2.0</td>
<td>1.2.2</td>
<td>OACWG package APx3</td>
<td>OCE</td>
</tr>
<tr class="even">
<td>OCE Java CAL</td>
<td>RedHat Enterprise Linux 6.1</td>
<td>Java 11</td>
<td>2.0</td>
<td>1.2.5</td>
<td>OACWG package APx3</td>
<td>OCE</td>
</tr>
<tr class="odd">
<td>VxWorks CAL</td>
<td>VxWorks 6.5</td>
<td>C++</td>
<td>2.0</td>
<td>1.19</td>
<td>OACWG package APx3</td>
<td>Non-OCE</td>
</tr>
<tr class="even">
<td>Subsystem CAL</td>
<td>RedHat Enterprise Linux 6.3</td>
<td>C++</td>
<td>2.0</td>
<td>1.2.2</td>
<td>Ghost Detector Extension Schema v1.8</td>
<td>Subsystem</td>
</tr>
<tr class="odd">
<td>Language Agnostic CAL</td>
<td>RedHat Enterprise Linux 6.1</td>
<td>WebSocket/JSON</td>
<td>2.3</td>
<td>1.0.0</td>
<td>2.3</td>
<td>Platform</td>
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

Table 7.1-2, CAL Interaction Limitations, documents any restrictions
that the CALs may encounter while interacting with one another.

For specific implementations, this section documents how developers can
link CAL libraries into applications. The intention is that Services
built with various language bindings (e.g., C++, Java) and for different
operating environments (e.g., Windows, Linux) on the same OMS Platform
will be able to interact. If there are restrictions of any kind that
would preclude any of these CALs being able to interact with another, it
should be documented here so users of the CALs understand these
limitations. Restrictions can be in many forms. For example, certain CAL
implementations may be designed to work at a specific security level and
would not interact with CALs that operate at a different level. Another
example is a CAL that is built to support only a subset of the OMS
Messages to meet some performance, sizing, or security concern. If there
are any restrictions, from a Platform perspective, they should be
identified in Table 7.1-2. In some instances, a CAL may limit the
messages to which it may subscribe or publish. In this case, the cell
should denote “Limited” and be superscripted with a note that will
identify where that limitation is documented.

<span id="_Toc219294978" class="anchor"></span>Table 7.1-2 CAL
Interaction Limitations

<table>
<thead>
<tr class="header">
<th><p>CAL</p>
<p>Publisher</p>
<p>CAL</p>
<p>Subscriber</p></th>
<th><p>OCE Java</p>
<p>CAL</p></th>
<th><p>OCE C++</p>
<p>CAL</p></th>
<th><p>VxWorks C++</p>
<p>CAL</p></th>
<th><p>MLS Secret C++</p>
<p>CAL</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>OCE Java</p>
<p>CAL</p></td>
<td>None</td>
<td>None</td>
<td>Limited<sup>2</sup></td>
<td>Limited<sup>1</sup></td>
</tr>
<tr class="even">
<td><p>OCE C++</p>
<p>CAL</p></td>
<td>None</td>
<td>None</td>
<td>Limited<sup>3</sup></td>
<td>Limited<sup>1</sup></td>
</tr>
<tr class="odd">
<td><p>VxWorks C++</p>
<p>CAL</p></td>
<td>Limited<sup>2</sup></td>
<td>Limited<sup>3</sup></td>
<td>None</td>
<td>Limited<sup>1</sup></td>
</tr>
<tr class="even">
<td><p>MLS Secret C++</p>
<p>CAL</p></td>
<td>None</td>
<td>None</td>
<td>Limited<sup>1</sup></td>
<td>None</td>
</tr>
</tbody>
</table>

The type of restriction is denoted as a superscript. “None” or “Limited”
is used to determine the result of the restriction.

None indicates the CAL pair interact without limitations.

Limited<sup>1</sup> indicates the CAL pair do not interact.

If required, add legends to describe any additional type of
restrictions. For example:

Limited<sup>2</sup> The VxWorks C++ CAL will interact with the OCE Java
CAL as identified in Appendix 1 of this document.

Limited<sup>3</sup> The VxWorks C++ CAL will interact with the OCE C++
CAL as identified in Appendix 2 of this document.

CAL Required Libraries / Licenses
---------------------------------

This section documents the required libraries and licenses required to
run the CAL implementations as shown in Table 7.2-1, CAL Licenses &
Libraries.

This section should document the required libraries and licenses
required to run the CAL implementations for each location that a CAL is
deployed in the OMS Platform (e.g., OCE, Non-OCE processors, Subsystem).
The CAL identifiers used in Table 7.1-1, CAL Versions Available, and
Table 7.2-1, CAL Licenses and Libraries, are used to link the entries in
each of the tables together. If a license and its associated library in
Table 7.2-1, CAL Licenses and Libraries, are common to all of the CALs
listed in Table 7.1-1, CAL Versions Available, then the identifier “ALL
CALs” or the enumeration of all of the CAL identifiers in the first
column is permissible.

-   CAL Identifier(s) – Provide an identifier for each CAL to uniquely
    identify it from other CALs on the same OMS Platform

-   Supported Operational Attribute Configuration (SOAC) – Identify
    supported configuration table(s) from the “CAL Operational
    Attributes” section that contain the operational attribute
    configuration (e.g., SOAC-1 &lt;SOAC name&gt;, SOAC-2 &lt;SOAC
    name&gt;)

-   Purpose – Identify overall purpose of the library

-   Provider – Identify the license provider

-   Product – Identify the license product

-   Version – Identify the license version

-   License Type – Identify the license type

-   Library Type – Identify the library type

<span id="_Toc219294979" class="anchor"></span>Table 7.2-1 CAL Licenses
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
<td><p>OCE C++ CAL</p>
<p>Subsystem CAL</p></td>
<td>SOAC-1 &lt;SOAC name&gt;</td>
<td>CAL Middleware</td>
<td>VendorX</td>
<td>SuperTransport</td>
<td>4.3</td>
<td>Open Source</td>
<td>Runtime .so</td>
</tr>
<tr class="even">
<td>OCE Java CAL</td>
<td></td>
<td>CAL Middleware</td>
<td>VendorX</td>
<td>SuperTransport</td>
<td>4.4</td>
<td>Open Source</td>
<td>Runtime JAR</td>
</tr>
<tr class="odd">
<td>VxWorks CAL</td>
<td></td>
<td>CAL Middleware</td>
<td>VendorX</td>
<td>SuperTransport</td>
<td>3.9</td>
<td>Open Source</td>
<td>Compile time .lib</td>
</tr>
<tr class="even">
<td>ALL CALs</td>
<td></td>
<td>CAL Cyber security</td>
<td>VendorY</td>
<td>EncryptorY</td>
<td>3.2.1</td>
<td>Commercial runtime seat license</td>
<td>Compile time .lib</td>
</tr>
<tr class="odd">
<td>OCE Java CAL</td>
<td></td>
<td>Java Middleware</td>
<td>VendorZ</td>
<td>Java JDK Core Lib</td>
<td>1.0</td>
<td>Commercial runtime seat license</td>
<td>Runtime JAR</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

Every CAL implementation should be documented. If some CAL
implementations implement different protocols, transport, middleware
packages, or message security implementations (e.g., confidentiality,
integrity, non-repudiation, etc.), then those differences should be
clearly identified.

### Language-Specific CAL

This section documents configuration, externalizer implementation and
operational attributes for all Language-Specific CALs identified in
Table 7.1-1, CAL Versions Available.

#### \[CAL Identifier\]

The following sub-sections document the CAL configuration, externalizer
implementation(s) and operational attributes for the \[CAL Identifier\].

IMPORTANT: Section 7.3.1.1, \[CAL Identifier\], and each of its
sub-paragraphs below should be repeated for each relevant CAL, and
numbered as 7.3.1.1 (7.3.1.1.1, 7.3.1.1.2, etc.), 7.3.1.2, and so on. In
each sub-paragraph, CAL Identifiers should match the CAL Identifiers in
Table 7.1-1 CAL Versions Available. Note that the square brackets around
\[CAL Identifier\] throughout are just field delimiters indicating where
your CAL Identifier should replace it. The final document should have no
square brackets around the CAL Identifier.

##### \[CAL Identifier\] CAL Configuration

This section documents specific details required for Language-Specific
CAL configuration.

This section may include specifics on CAL configuration for each target
environment (OCE, Non-OCE, Subsystem) and for each CAL implementation.
Include specifics on config file format, network setup and other system
variables important to making all OMS Services and Subsystems
communicate. This may include settable configuration parameters for the
CAL, such as QoS and other system functions. This includes the location,
content, format, and means for modifying any OMS Platform QoS files that
provide for any of these identified OMS defined QoS settings.

##### \[CAL Identifier\] CAL Externalizer Implementation

This section documents specific details required for Externalizer
implementation, if an Externalizer is provided as shown in Table 7.3-1,
CAL Externalizer Implementation.

This section may include specifics on the optional Externalizer
implementation for each target language (Java or C++).

The Externalizer is a software interface that converts CAL messages into
another format. It enables the services to take the messages from the
CAL and externalize them to whatever format the service wants. It is
referenced in the Java and C++ CAL Specifications. The Externalizer
cannot be used for OMS Data Transfers. It is situated between the
Service and the CAL API. The Externalizer API allows an externally
generated tool, built to the API, to export/import to an external
format. The Externalizer API allows a method to export/import to an
external format independent of any underlying/internal CAL serialization
and/or transport implementations. Multiple Externalizers are allowed.
These may include Externalizers provided by the CAL or by a Service
Provider. If this section is not applicable, mark as “Not Applicable”
with a rationale and the first empty cell of the table with “N/A”. For
each Externalizer implemented, Table 7.3-1 identifies the information
that needs to be provided.

-   CAL Externalizer Name– Provide the CAL Externalizer name identifier

-   CAL Identifier – The name of the CAL in which the Externalizer will
    be used as referenced in Table 7.1-1 CAL Versions Available

-   Encoding – Provide the encoding the Externalizer performs (i.e.,
    JSON, XML, custom, etc.)

-   Schema Version – Provide the UCI Message Schema version the
    Externalizer was built against with any related Extensions, if
    applicable

-   CAL API (OMS Version) – Provide the CAL API (OMS Version) as
    specified by the vendor associated with each Externalizer as
    applicable

-   Vendor – Provide the name of the Externalizer vendor

-   Externalizer Version – Provide the version of the Externalizer

-   Reference Documentation – A reference that provides details,
    description, and/or implementation of the encoding as referenced in
    Table 1.1-1, Reference Documents

<span id="_Toc219294980" class="anchor"></span>Table 7.3-1 CAL
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
<td>Company A Externalizer</td>
<td>OCE Java CAL</td>
<td>XML</td>
<td>v2.2.0</td>
<td>v2.2.0</td>
<td>A</td>
<td>1.0.0</td>
<td>A-EXT-001</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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
Configuration (SOAC) Table. Since a CAL can support different
configurations of operational attributes, the Platform should specify
the supported values of these operational attributes in one or more
tables, as needed. The first configuration is shown in Table 7.3-2,
SOAC-1 &lt;SOAC name&gt;.

The operational attributes of a CAL are those attributes that control
how the CAL operates when exchanging messages. These attributes are
primarily used to configure the CAL’s Readers and Writers when they are
instantiated. The attributes listed in this section are the minimal set
of attributes that all CALs must support (the relevant CERTs are listed
below).

CAL Readers have the following input queue attributes that are
configured when the CAL Reader is instantiated:

-   **Queue Length**: The length of the CAL Reader’s input queue (see
    CERT CAL-015746, defined in the “Message Buffer” Section of the
    Critical Abstraction Layer (CAL) Specification)

-   **Filter Time**: The time interval that is used with time-based
    filtering (see CERT CAL-005431, defined in the “Time Based Filter”
    Section of the Critical Abstraction Layer (CAL) Specification)

-   **Expiration Time**: The expiration time for messages held by the
    CAL Reader (see CERT CAL-005437, defined in the “Expiration” Section
    of the Critical Abstraction Layer (CAL) Specification)

-   **Overflow Action**: The action that is to be taken should the CAL
    Reader’s input queue overflow (see CERT CAL-016079, defined in the
    “Message Buffer” Section of the Critical Abstraction Layer (CAL)
    Specification)

-   **Reliability**: The reliability requested indicates one of two
    levels: Best Effort and Reliable see (see CERT CAL-005434, defined
    in the “Reliability” Section of the Critical Abstraction Layer (CAL)
    Specification).

CAL Writers have the following output queue attributes that are
configured when the CAL Writer is instantiated:

-   **Queue Length**: The length of the CAL Writer’s output queue (see
    CERT CAL-005444, defined in the “Message Buffer” Section of the
    Critical Abstraction Layer (CAL) Specification)

-   **Overflow Action**: The action that is to be taken should the CAL
    Writer’s output queue overflow (see CERT CAL-005445, defined in the
    “Message Buffer” Section of the Critical Abstraction Layer (CAL)
    Specification)

-   **Reliability**: The reliability requested indicates one of two
    levels: Best Effort and Reliable see (see CERT CAL-005434, defined
    in the “Reliability” Section of the Critical Abstraction Layer (CAL)
    Specification).

The operational attributes as specified in this table include the CAL
Reader’s input queue. If an operational attribute is “Not Applicable,”
then mark it as “N/A”. The notes entry should document any benefits or
adverse effects from the indicated values.

-   **Queue Length: **Specifies in number of messages, the **nominal
    (default)**, **minimum** and **maximum** length of the input queue.
    The minimum queue length is at least one, per the CAL specification,
    unless set to a different value greater than one. The nominal value
    is used unless the CAL has been specifically configured to use a
    different value between the minimum and maximum. The minimum and
    maximum values represent the input queue length that is supported.

-   **Filter Time:** Specifies in microseconds, the **nominal
    (default),** **minimum** and **maximum** filter time. The nominal
    value is used unless the CAL has been specifically configured to use
    a different value between the minimum and maximum. The minimum and
    maximum values represent filter time that is supported.

-   **Expiration Time:** Specifies in microseconds, the **nominal
    (default)**, **minimum** and **maximum** expiration time. The
    nominal value is used unless the CAL has been specifically
    configured to use a different value between the minimum and maximum.
    The minimum and maximum values represent the expiration time that is
    supported.

-   **Overflow Action:** Specifies the default action taken by CAL
    Readers if their input queue should overflow. Actions include:

<!-- -->

-   **Drop Oldest**: Specifies that the CAL Reader should drop the
    oldest message in the input queue when the input queue overflows

-   **Drop Newest**: Specifies that the CAL Reader should drop the
    newest message in the input queue when the input queue overflows.

<!-- -->

-   **Reliability:** Specifies the reliability setting requested of CAL
    Readers by the CAL Client to indicate one of two levels of
    reliability: Best Effort and Reliable. Settings include:

<!-- -->

-   **Best Effort:** The CAL does not guarantee message delivery and
    will not retransmit missing or dropped data

-   **Reliable:** The CAL will try to deliver the message after failure,
    giving best effort. This means the reliable delivery may be built
    upon best effort and could introduce latency and throughput
    complications.

The operational attributes as specified in this table also include the
CAL Writer’s output queue. If an operational attribute is “Not
Applicable,” mark it as “N/A”. The **notes** entry should document any
benefits or adverse effects from the indicated values.

-   **Queue Length:** Specifies in number of messages, the **nominal
    (default),** **minimum** and **maximum** length of the output queue.
    The nominal value is used unless the CAL has been specifically
    configured to use a different value between the minimum and maximum.
    The minimum and maximum values represent the output queue length
    that is supported.

-   **Overflow Action:** Specifies the default action taken by CAL
    Writers if their output queue should overflow. Actions include:

<!-- -->

-   **Drop Oldest**: Specifies that the CAL Writer should drop the
    oldest message in the output queue when the output queue overflows

-   **Drop Newest**: Specifies that the CAL Writer should drop the
    newest message in the output queue when the output queue overflows

-   **Block**: Specifies that the CAL Writer’s write operation should
    block until room becomes available in that CAL Writer’s output queue

-   **Throw Exception**: Specifies that the CAL Writer’s write operation
    should throw an exception indicating that the CAL Writer’s output
    queue is full.

<!-- -->

-   **Reliability:** Specifies the reliability setting requested of CAL
    Writers by the CAL Client to indicate one of two levels of
    reliability: Best Effort and Reliable. Settings include:

<!-- -->

-   **Best Effort:** The CAL does not guarantee message delivery and
    will not retransmit missing or dropped data

-   **Reliable:** The CAL will try to deliver the message after failure,
    giving best effort. This means the reliable delivery may be built
    upon best effort and could introduce latency and throughput
    complications.

The following table is filled with example data.

<span id="_Toc219294981" class="anchor"></span>Table 7.3-2 SOAC-1
&lt;SOAC name&gt;

<table>
<thead>
<tr class="header">
<th>SOAC-1 &lt;SOAC name&gt;</th>
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
<td>5</td>
<td>1</td>
<td>N/A</td>
<td></td>
</tr>
<tr class="even">
<td>Filter Time</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td></td>
</tr>
<tr class="odd">
<td>Expiration Time</td>
<td>N/A</td>
<td>N/A</td>
<td>N/A</td>
<td></td>
</tr>
<tr class="even">
<td>Overflow Action</td>
<td>Drop Oldest</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Reliability</td>
<td>Reliable</td>
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
<td>N/A</td>
<td>20</td>
<td>N/A</td>
<td>The output queue length must be able to support messages in a burst mode</td>
</tr>
<tr class="even">
<td>Overflow Action</td>
<td>Drop Oldest</td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>Reliability</td>
<td>Reliable</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

When more than one SOAC needs to be specified, copy the Table 7.3-2
table caption and Table 7.3-2 table here. Include a sentence before the
new table caption that introduces the new table, such as “Another
configuration is shown in Table 7.3.3-1, SOAC-2.” (see General Template
Instruction above for table numbering). Note that the table caption in
the introductory sentence and the actual table caption both need to be
consistent; remember to increment the numbers by one every time a new
configuration is documented.

### Language-Agnostic CAL

This section documents access and configuration information for all
Language-Agnostic CALs identified in Table 7.1-1, CAL Versions
Available.

#### \[CAL Identifier\]

The following sub-sections document the Language-Agnostic CAL access and
configuration information for the \[CAL Identifier\].

IMPORTANT: Section 7.3.2.1, \[CAL Identifier\], and each of its
sub-paragraphs below should be repeated for each relevant CAL, and
numbered as 7.3.2.1 (7.3.2.1.1); and so on. In each sub-paragraph, CAL
Identifiers should match the Language-Agnostic CAL Identifiers in Table
7.1-1 CAL Versions Available. Note that the square brackets around \[CAL
Identifier\] throughout are just field delimiters indicating where your
CAL Identifier should replace it. The final document should have no
square brackets around the CAL Identifier.

This section is used to document any information needed to utilize a
Language-Agnostic CAL. Table 7.3-3 Language-Agnostic CAL Access
Information provides information Subsystems, Services, and/or Isolators
need to connect and utilize a language-agnostic CAL.

-   CAL Identifier(s) – Provide an identifier for each CAL to uniquely
    identify it from other CALs on the same OMS Platform

-   Endpoint URI – The URI location(s) where a language-agnostic CAL can
    be accessed

-   Protocol – Approved protocol a language-agnostic CAL supports

-   Sub-protocol Versions – Supported sub-protocol version(s) a
    language-agnostic CAL supports

-   Message Formats – Approved message format(s) a language-agnostic CAL
    supports

-   Schema – Supported schema versions a language-agnostic CAL supports
    and validates messages against.

<span id="_Toc219294982" class="anchor"></span>Table 7.3-3
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
<td>Language Agnostic CAL</td>
<td>ws://cal.platform.gov</td>
<td>WebSocket</td>
<td>OWP 1.0</td>
<td>OMS JSON</td>
<td>2.3</td>
</tr>
<tr class="even">
<td>Language Agnostic CAL</td>
<td>wss://cal.platform.gov</td>
<td>WebSocket</td>
<td>OWP 1.0</td>
<td>OMS JSON</td>
<td>Ghost Detector Extension Schema v1.8</td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
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

This section may include specifics on Language-Agnostic CAL
configuration for each target environment (OCE, Non-OCE, Subsystem) and
for each CAL implementation. Include specifics on config file format,
network setup and other system variables important to making all OMS
Services and Subsystems communicate. This may include settable
configuration parameters for the CAL, such as QoS and other system
functions. This includes the location, content, format, and means for
modifying any OMS Platform QoS files that provide for any of these
identified OMS defined QoS settings.

Virtualization Environments
===========================

This section identifies and describes any virtual environments on the
Platform and their capabilities to be extended and/or reconfigured.

If there are no virtualized environments on the OMS Platform then
document this section and its subsection as “Not Applicable” with a
rationale.

If there is more than one virtualized environments, replicate the
subsections below for each environment.

The following subsections should document the capabilities of the
virtualization environment(s) that are being used to implement portions
of the OMS Platform, not the architecture that is being implemented in
the virtual environment. Those details belong in other sections within
this document.

Virtualization Environment - &lt;&lt;Name&gt;&gt;
-------------------------------------------------

This section documents a virtualization environment within the OMS
Platform.

Examples of virtualization environments are a specific hypervisor,
virtual machine, or cloud computing environment. Insert a unique name
for the virtualization environment into the section header.

In the case of a cloud computing environment, identify if it is a
Private Cloud, Community Cloud, Public Cloud, or Hybrid Cloud, per the
definitions in NIST SP 800-145. Also identify the owner of the cloud
computing environment.

### Processor Virtualization

This section identifies if the virtualization approach is hardware
assisted or if a full virtualization approach is used. This section also
identifies the processor architectures that can be virtualized.

### Memory Virtualization

This section identifies the memory virtualization approach and
capabilities. This includes processor RAM, local file storage, and
network file storage.

This section should contain a description of the memory virtualization
approach.

### Network Virtualization

This section identifies the virtual network capabilities provided by the
virtual environment.

This section should contain a description of the virtual network
capabilities provided by the virtual environment.

### Virtualization Environment Deployment

This section describes how the virtualized environment is deployed on
the Platform.

This section should identify and specific steps or requirements needed
to deploy the virtualized environment on the Platform.

### Service Deployment

This section describes how a Service is deployed and managed in the
virtual environment, including any requirements placed on a Service to
run in the environment and for using a CAL or Data Transfers.

This section should identify specific additional requirements for using
a CAL or Data Transfers. This section should also document any
management functionality of Service packaging.

### Time

This section documents how time synchronization is supported by the
virtual environment.

This includes how time is provided to both the virtualized environment
and to applications running on the virtualized environment. A
virtualized environment should sync its internal time to an external
time source provided by the Platform at the boundary of the virtualized
environment. Accuracy and precision of time provided by virtualized
environment to Services should be documented.

### Virtualization Environment Configuration

This section documents the virtualized environment configuration
details.

In the case of a virtualized environment, this section should also
contain details on the configuration of the virtualization environment.
This might include a reference to an external document that contains the
details.

Configuration Data
==================

This section identifies all of the configuration data for the OMS
Platform as shown in Table 9.0-1, Configuration Data.

This may include the following items if they are applicable to a given
OMS Platform:

-   Platform configuration data files

-   Platform boot or startup configuration files.

-   Configuration files required for Service/Subsystem startup. This
    should include the location, identity, and means for modifying any
    OMS Platform configuration files required for OMS startup for a
    Service or Subsystem. (Note: This is not meant to include internal
    Subsystem configuration data.)

-   This section may include cross references for Configuration Guides
    and/or VDD’s as applicable. CAL configuration data should reside in
    the CAL Section.

The columns in Table 9.0-1, Configuration Data, should contain the
following information:

-   Configuration Data Identifier – This column should identify the type
    or name of the configuration data

-   File Pathname – This column should identify the full path including
    file name and extension

-   File Format – This column should identify the format of the file.
    This could include binary, text, XML, CSV, etc.

-   Method or Tool for Modification – This column should identify the
    program or tool for modifying the configuration file

-   Other Details and Cross References – This column may include any
    additional details or cross references that help define the purpose
    and usage of the configuration data item.

<span id="_Toc219294983" class="anchor"></span>Table 9.0-1 Configuration
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
<td>Platform Config</td>
<td>/config_data/platform/platform.config</td>
<td>text</td>
<td>notepad.exe or any text editor</td>
<td>Standard text file</td>
</tr>
<tr class="even">
<td>Cyber Config</td>
<td>/config_data/platform/</td>
<td>XML</td>
<td>Any XML editing tool</td>
<td></td>
</tr>
<tr class="odd">
<td>Software boot files</td>
<td>/root/</td>
<td>binary</td>
<td>Config tool</td>
<td>See Software Installation Document</td>
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

Special Signals
===============

This section identifies how any special signals are provided or
provisioned for by the Platform as defined in the OMS Standard,
OMSC-STD-001, “Special Signals.”

If no special signals are provided or provisioned for, then this section
and its subsections should be marked “Not Applicable” with a rationale
and the first empty cell of the table with “N/A”.

Provided Special Signals
------------------------

This section lists the special signals that are provided by the OMS
Platform as identified in "Special Signals" of the OMS Standard,
OMSC-STD-001 as shown in Table 10.1-1, Provided Special Signals.

Each provided signal should include the details on how these special
signals are implemented by the Platform.

The columns in Table 10.1-1, Provided Special Signals, should contain
the following information:

-   Signal Identification – This column should identify the name of the
    special signal

-   Hardware Implementation Details – This column should identify how
    the special signal was implemented from a hardware perspective. For
    example this could be one of the implementation methods identified
    in the OMS Standard for this special signal or a description of how
    the signal should be interpreted or defined from a hardware
    perspective

-   Software Interface – This column should identify any Software
    interfaces that a Service or Subsystem could use to access or read
    the special signal. This could refer to an external document.

<span id="_Toc219294984" class="anchor"></span>Table 10.1-1 Provided
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
<td>Weight on wheels</td>
<td>+28V per MIL-STD-704</td>
<td>See Air Vehicle ICD</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
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

Each provisioned special signal should include the details on how these
signals are provisioned for on the Platform.

The columns in Table 10.2-1, Provisioned Special Signals should contain
the following information:

-   Signal Identification – This column should identify the name of the
    special signal

-   Signal Provisioning Details – This column should identify how the
    special signal was provisioned on the OMS Platform.

<span id="_Toc219294985" class="anchor"></span>Table 10.2-1 Provisioned
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
<td>Weight on wheels</td>
<td>Existing wiring could carry discretes</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>

Cybersecurity Posture
=====================

This section identifies the cybersecurity posture of the Platform.

Describe the Cybersecurity posture of the Platform. The Cybersecurity
Posture Section should describe the Cybersecurity posture implementation
of the Platform. The addendum may include classified implementation
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

This section identifies the CSAs applicable to the Platform.

Provide descriptions of the cybersecurity features used as evidence to
meet the program-assigned System Survivability Key Performance
Parameters (KPPs). These descriptions are in summary format with an
external reference, pointer to an OMS PDD Section, or detailed including
diagrams to relay to the reader how the feature is employed within the
Platform. If a CSA is not applicable or not addressed, denote this with
“N/A”. See the Cybersecurity Guide for more information.

Within the Cyber Survivability Endorsement framework, cybersecurity
implementation information is captured or referenced in ten CSAs. They
articulate measurable and testable cybersecurity implementation and are
supported by NIST cybersecurity technical controls.

An example mapping from the CSAs to NIST 800-53 controls for programs
operating within a Risk Management Framework (RMF) could be shown as
follows. Note that the selected CSA and Controls are for example only
and do not reflect actual program implementation.

<table>
<thead>
<tr class="header">
<th><span class="underline">Feature</span></th>
<th><span class="underline">CSA</span></th>
<th><span class="underline">Controls (NIST 800-53)</span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Confidentiality</td>
<td>CSA-03: Secure Transmission &amp; Communications</td>
<td>SC-7 SC-8, AC-4, AC-7</td>
</tr>
<tr class="even">
<td>Authentication</td>
<td>CSA-01: Control Access</td>
<td>AC-1, AC-2, IA-2, AC-8, AC-11</td>
</tr>
<tr class="odd">
<td>Integrity</td>
<td>CSA-04: Protect System’s Information from Exploitation</td>
<td>SI-7, SI-10</td>
</tr>
<tr class="even">
<td>Non-Repudiation</td>
<td>CSA-10: Manage System’s Configuration Achieve and Maintain an Operationally-Relevant Cyber Risk Posture</td>
<td>AU-10(all), AU-11</td>
</tr>
</tbody>
</table>

### Prevent CSAs

This section identifies and documents the System Survivability Key
Performance Parameter (KPP) Prevent CSAs implementation for the
Platform. Table 11.1-1 identifies the System Survivability KPP Prevent
CSAs applicable to the Platform.

In the table below, indicate the CSAs applicable to the Platform by
adding an “x”.

<span id="_Toc219294986" class="anchor"></span>Table 11.1-1 Applicable
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

Provide a brief, high-level description (1-2 sentences) of how each
Cyber Survivability Attribute (CSA) identified in Table 11.1-1 is
explicitly addressed by the OMS Platform. The description should be
unclassified and non-proprietary, and capture the cybersecurity posture.
The cybersecurity posture should be commensurate with the expected CSRC
of the Mission Package in which the Platform is integrated.

-   CSA-01: Control Access

-   CSA-02: Reduce System’s Cyber Detectability

-   CSA-03: Secure Transmissions and Communication

-   CSA-04: Protect System’s Information from Exploitation

-   CSA-05: Partition and Ensure Critical Functions at Mission
    Completion Performance Level

-   CSA-06: Minimize and Harden Attack Surfaces

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable PDD Section(s). See the Cybersecurity
Guide for more information.

### Mitigate CSAs

This section identifies and documents the System Survivability KPP
Mitigate CSAs implementation for the Platform. Table 11.1-2 identifies
the System Survivability KPP Mitigate CSAs applicable to the Platform.

In the table below, indicate the CSAs applicable to the Platform by
adding an “x”. If the CSAs are not applicable or not addressed, denote
this section with “N/A” and leave Table 11.1-2 empty.

<span id="_Toc219294987" class="anchor"></span>Table 11.1-2 Applicable
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

Provide a brief, high-level description (1-2 sentences) of how each
Cyber Survivability Attribute (CSA) identified in Table 11.1-2 is
explicitly addressed by the OMS Platform. The description should be
unclassified and non-proprietary, and capture the cybersecurity posture.
The cybersecurity posture should be commensurate with the expected CSRC
of the Mission Package in which the Platform is integrated.

-   CSA-07 Baseline and Monitor Systems and Detect Anomalies

-   CSA-08 Manage System Performance and Enable Cyberspace Defense

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable PDD Section(s). See the Cybersecurity
Guide for more information.

### Recover CSA

This section identifies and documents the System Survivability KPP
Recover CSA implementation for the Platform.

Provide a brief, high-level description (1-2 sentences) of how the
CSA-09 Recover System Capabilities is explicitly addressed by the OMS
Platform. The description should be unclassified and non-proprietary,
and capture the cybersecurity posture. The cybersecurity posture should
be commensurate with the expected CSRC of the Mission Package in which
the Platform is integrated.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable PDD Section(s). See the Cybersecurity
Guide for more information.

If the CSA is not applicable or not addressed, denote this with “N/A”.

### Adapt CSA

This section identifies and documents the System Survivability KPP Adapt
CSA implementation for the Platform.

Provide a brief, high-level description (1-2 sentences) of how the
CSA-10 Actively Manage System’s Configuration to Achieve and Maintain an
Operationally-Relevant Cyber Risk Posture is explicitly addressed by the
OMS Platform. The description should be unclassified and
non-proprietary, and capture the cybersecurity posture. The
cybersecurity posture should be commensurate with the expected CSRC of
the Mission Package in which the Platform is integrated.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable PDD Section(s). See the Cybersecurity
for more information.

If the CSA is not applicable or not addressed, denote this with “N/A”.

Security Addendum
=================

This section identifies the Security Addendum document(s).

The Security Addendum is expected to be external to the PDD and can be
composed of one or more separate documents that:

-   Might already be existing/planned program documents that could be
    referenced to supply OMS-related information,

-   Might have to be published at different security levels, and

-   Could be developed/published at different points in the program
    lifecycle.

The name of the document(s) must be unclassified and non-proprietary.
Referenced documents may be both classified and proprietary. The
Security Addendum should describe the Security Information Exchanges of
the Platform and provides additional, classified, and/or proprietary
details relating to the security of the Platform. The addendum may
include classified implementation details with reference to Interface
Control Documents (ICDs).

In the case of a virtualized environment, this section should include
any security features being leveraged from the virtualization
environment(s).

Appendix A Acronyms and Abbreviations
=====================================

This section lists the abbreviations and acronyms used in this document
not a copy of the OMS lexicon as shown in Table A.0-1, List of Acronyms
and Abbreviation Definitions.

In addition, acronyms should be spelled out at first use in the body of
the document.

<span id="_Toc219294988" class="anchor"></span>Table A.0-1 List of
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
<td>SOAC</td>
<td>Supported Operational Attribute Configuration</td>
</tr>
<tr class="even">
<td>UCI</td>
<td>Universal C2 Interface</td>
</tr>
<tr class="odd">
<td>UML</td>
<td>Unified Modeling Language</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>

Appendix B Glossary
===================

This section lists the terms used in this document as shown in Table
B.0-1, List of Term Definition.

Note: the list of terms used should not be a copy of the OMS lexicon.

<span id="_Toc219294989" class="anchor"></span>Table B.0-1 List of Term
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

Appendix C Message Details
==========================

This appendix consists of one of more spreadsheet workbooks with a
separate tab for each **SystemTimeAtReference*,* PositionReport,**
and/or **PositionReportDetailed** message use based on each function’s
input and output messages.

This section is only applicable for Platforms directly providing the
**SystemTimeAtReference*,* PositionReport,** and/or
**PositionReportDetailed** messages. No additional messages can be
directly provided by the Platform nor recorded in this section.

Please note that the Adopting Program may choose to create a document
table within this section of the document if appropriate for a simple
PDD. An example Excel Workbook is provided as guidance.

See file Example\_PDD\_AppC\_OMS-FIG-0228C.xlsx

Adopting Programs should update the attached
Example\_PDD\_AppC\_OMS-FIG-0228C.xlsx for Platforms directly providing
the **SystemTimeAtReference*,* PositionReport,** and/or
**PositionReportDetailed** messages. As part of the Starter Kit, the
SchemaToXLS tool is provided to assist Adopting Programs in generating
this Appendix C Table from the available UCI Schema as an output Excel
Workbook containing individual tabs for the **SystemTimeAtReference*,*
PositionReport,** and/or **PositionReportDetailed** messages. See OAM
Starter Kit for details. The example
Example\_PDD\_AppC\_OMS-FIG-0228C.xlsx was generated by the SchemaToXLS
tool for the following messages: **SystemTimeAtReference*,*
PositionReport,** and **PositionReportDetailed**. Delete any messages as
applicable, additional messages cannot be added. If different fields of
the same message are used in different functions, there must be a
different message workbook/tab for each function that uses different
fields of the same message. If the same message fields are used in
multiple functions, the same message workbook/tab can be used, but it
must reference the functions that apply to it.

A Table of Contents tab should be created to summarize messages as
identified by the individual message tabs to related functions performed
by the Platform. The format of this Table of Contents will consist of
the following columns, as a minimum, in the order shown. The SchemaToXLS
tool will produce an initial Table of Contents for the user.

-   Appendix C Mapping – one entry per message tab; this name could be
    abbreviated for shorter tab names; recommend hyperlink to jump to
    tab within the spreadsheet

-   Full Message Name – indicate full message name

-   Message Direction (Input/Output) – indicate message as “Input” or
    “Output”. Platforms directly providing the
    **SystemTimeAtReference*,* PositionReport,** and/or
    **PositionReportDetailed** should indicate these messages are an
    “Output”.

The format for these tables will consist of the following columns as a
minimum, in the order shown.

-   Element – one entry per element in the message

<!-- -->

-   Any item with multiplicity should indicate the number of minimum
    occurrences (minOccurs) and maximum occurrences (maxOccurs). The
    SchemaToXLS tool automatically populates the occurrences in the
    format \[minOccurs:maxOccurs\]. Unb indicates unbounded. Use the
    Notes column to indicate which will be used by the Service.

<!-- -->

-   Schema Use:

<!-- -->

-   Required – indicates the element is a required element per the
    schema (must be populated if its parent element is populated)

-   Optional – indicates the element is an Optional element per the
    schema (only needs to be filled out if applicable)

<!-- -->

-   Choice – indicates the element is part of a Choice per the schema

<!-- -->

-   Service Use:

<!-- -->

-   For Input Messages:

<!-- -->

-   This data is not applicable for Platforms directly providing
    **SystemTimeAtReference*,* PositionReport,** and/or
    **PositionReportDetailed** messages

<!-- -->

-   For Output Messages:

<!-- -->

-   Mandatory – indicates the element will be populated

-   If a range is included in the Schema Use column, include in the
    Service Use column, and adjust the range if needed to indicate
    further limitation of the range

-   Supported – indicates the element will be populated if the
    appropriate conditions were met

-   If a range is included in the Schema Use column, include in the
    Service Use column, and adjust the range if needed to indicate
    further limitation of the range

-   Unused – indicates the element will never be populated

<!-- -->

-   Notes:

<!-- -->

-   This field is a free-form field to be used to provide additional
    information not included in the Description column. For example:

<!-- -->

-   Clarify element usage (e.g., speed is in nm/s, latitude is expected
    in radians)

-   Indicate behavior if range limitations are exceeded (e.g., message
    will be rejected if range limitation is exceeded, or message will be
    accepted up to the number of items in the allowed range)

<!-- -->

-   Description (from schema):

<!-- -->

-   Indicate the Element description. This field is auto populated by
    the SchemaToXLS tool

<!-- -->

-   Extension Type:

<!-- -->

-   If Abstract Types (e.g., Polymorphic Extension Type or Capability
    Base Type) are used, indicate the name of the extension types. This
    field is auto populated by the SchemaToXLS tool

<!-- -->

-   Type:

<!-- -->

-   Indicates the Type Name. This field is auto populated by the
    SchemaToXLS tool.
