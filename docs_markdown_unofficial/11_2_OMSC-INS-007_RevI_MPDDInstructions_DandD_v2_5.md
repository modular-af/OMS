Open Mission Systems (OMS)

Definition And Documentation (D&D)

Mission Package Description Document (MPDD) Template Instructions

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

This Mission Package Description Document (MPDD) Template Instructions
describes how the MPDD Template is filled out. The General Template
Instructions provides a description of how this Template Instructions
document is used in filling out the corresponding associated MPDD
Template.

This Mission Package Description Document (MPDD) Template Instructions
is aligned with the Mission Package Description Document (MPDD)
Template, OMSC-TMP-007, Revision I, dated 22 January 2026.

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
<td>I</td>
<td>22 January 2026</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

This page is intentionally left blank.

Table of Contents

[1 Overview 5](#overview)

[1.1 References 5](#references)

[1.2 Mission Package Worksheet 5](#mission-package-worksheet)

[1.3 Mission Package Data Storage 6](#mission-package-data-storage)

[1.4 Mission Package Open Computing Environment (OCE)
7](#mission-package-open-computing-environment-oce)

[1.5 Mission Package External Interface
8](#mission-package-external-interface)

[2 Cybersecurity Posture 9](#cybersecurity-posture)

[2.1 Policy Overview 9](#policy-overview)

[2.2 CSRC 10](#csrc)

[2.3 Cyber Survivability Attributes (CSAs)
11](#cyber-survivability-attributes-csas)

[2.3.1 Prevent CSAs 11](#prevent-csas)

[2.3.1.1 Security Domain Definition 12](#security-domain-definition)

[2.3.1.2 Cybersecurity Flow Description
14](#cybersecurity-flow-description)

[2.3.1.3 Cybersecurity Confidentiality Implementation(s)
17](#cybersecurity-confidentiality-implementations)

[2.3.1.4 Cybersecurity Flow, Ports, and Protocols Restriction Policy
18](#cybersecurity-flow-ports-and-protocols-restriction-policy)

[2.3.1.5 Cybersecurity Identification & Authentication Implementation(s)
21](#cybersecurity-identification-authentication-implementations)

[2.3.1.6 Cybersecurity Access Controls
22](#cybersecurity-access-controls)

[2.3.1.6.1 Non-Streaming Data Transfer Access Controls
22](#non-streaming-data-transfer-access-controls)

[2.3.1.6.2 Streaming Data Transfer Access Controls
23](#streaming-data-transfer-access-controls)

[2.3.1.7 Cybersecurity Integrity Implementation(s)
26](#cybersecurity-integrity-implementations)

[2.3.2 Mitigate CSAs 27](#mitigate-csas)

[2.3.3 Recover CSA 27](#recover-csa)

[2.3.4 Adapt CSA 27](#adapt-csa)

[2.4 Cyber Survivability Rationale 28](#cyber-survivability-rationale)

[3 Security Addendum 29](#security-addendum)

[A Appendix A Acronyms and Abbreviations
30](#appendix-a-acronyms-and-abbreviations)

[B Appendix B Glossary 31](#appendix-b-glossary)

This page is intentionally left blank.

List of Figures

[Figure 2.1-1 OMS Cybersecurity Guidance in Acquisition
10](#_Toc219294463)

[Figure 2.3-1 Security Domain Boundaries 13](#_Toc219294464)

[Figure 2.3-2 Non-Streaming Data Transfer Information Flow Diagram
15](#_Toc219294465)

[Figure 2.3-3 Streaming Data Transfer Information Flow Diagram
16](#_Toc219294466)

This page is intentionally left blank.

List of Tables

[Table 0.0-1 OMS D&D Documents 3](#_Toc219294467)

[Feedback Form Table 4](#_Toc219294468)

[Table 1.1-1 Reference Documents 5](#_Toc219294469)

[Table 1.2-1 Mission Package Worksheet 6](#_Toc219294470)

[Table 1.2-2 Units of Replaceability Within the Mission Package
Worksheet 6](#_Toc219294471)

[Table 1.3-1 Data Storage Allocation 7](#_Toc219294472)

[Table 1.4-1 Open Computing Environment 8](#_Toc219294473)

[Table 1.5-1 External Interface 8](#_Toc219294474)

[Table 2.2-1 Mission Package CSRC 10](#_Toc219294475)

[Table 2.3-1 Applicable System Survivability KPP Prevent CSAs
11](#_Toc219294476)

[Table 2.3-2 Non-Streaming Data Transfer Information Flow
15](#_Toc219294477)

[Table 2.3-3 Streaming Data Transfer Information Flow
16](#_Toc219294478)

[Table 2.3-4 Confidentiality Implementation 17](#_Toc219294479)

[Table 2.3-5 Ports and Protocol Enforcement Policy 19](#_Toc219294480)

[Table 2.3-6 Open Ports and Protocols 20](#_Toc219294481)

[Table 2.3-7 Product/Data and Data Transfer Servers 21](#_Toc219294482)

[Table 2.3-8 Data Transfer Protocol Identification & Authentication
22](#_Toc219294483)

[Table 2.3-9 Non-Streaming Data Transfer Access Control Policy
23](#_Toc219294484)

[Table 2.3-10 Streaming Data Transfer Access Control Policy
25](#_Toc219294485)

[Table 2.3-11 Integrity Implementation 26](#_Toc219294486)

[Table 2.3-12 Applicable System Survivability KPP Mitigate CSAs
27](#_Toc219294487)

[Table A.0-1 List of Acronyms and Abbreviation Definitions
30](#_Toc219294488)

[Table B.0-1 List of Term Definitions 31](#_Toc219294489)

This page is intentionally left blank.

General Template Instructions

This document, Mission Package Description Document (MPDD) Template
(TMP) Instructions, OMSC-INS-007, provides information on how to fill in
required information in the MPDD Template, OMSC-TMP-007. The outline of
the MPDD Template Instructions is one-to-one aligned with each section
in the MPDD Template. The green text in each section of this MPDD
Template Instructions document should be used as guidance to fill out
the corresponding section in the MPDD Template. Green text in the MPDD
Template is considered guidance only and should be removed to reflect
your Mission Package. NOTE: The first page of the MPDD Template document
is for Open Mission Systems (OMS) purposes only and should be removed
prior to the release of the completed Template.

The MPDD Instructions also identifies version and revision history for
the template itself, versus that of an MPDD derived from the template.
When creating an MPDD, the last sentence in its Abstract/Summary,
identifying the revision and date of the MPDD Template to which the MPDD
conforms, should match the version information found herein for this
matching MPDD Template Instructions. The abstract is a brief summary of
the document that follows and is used to help the reader quickly
ascertain document’s purpose and overall content.

A Mission Package provider should save the MPDD Template using an
appropriate unique filename. The Mission Package provider should add an
appropriate document number, revision history and document date for
configuration management of program specific information. The
distribution statement should be filled out based on the program
specific restrictions, and at a minimum should be Distribution Statement
A. If the contents of the document require a higher restriction, the
appropriate distribution statement should be updated as needed. Green
text in the MPDD Template represents guidance for the creation of the
MPDD. Green text should not remain in the completed MPDD and should be
replaced in the cover page, Abstract, Revision Record, and all
applicable sections defined in the MPDD Template.

Each OMS Mission Package requires an associated MPDD to be compliant.
The OMS MPDD documents key implementation details of an OMS Mission
Package. When an Adopting Program (AP) decides to incorporate a
compliant OMS Mission Package into a weapon system, the Mission Package
Worksheet (MPW) is used to identify and provide key top-level
information on the composition of the Mission Package; viz., the OMS
Platform, Services, Subsystems, and Isolators of the Mission Package, as
applicable, and the compliance tier for each of these components. The
MPDD complements the MPW, by objectively describing the “as built”
security policies and data configuration of an OMS Mission Package.
These will evolve during the life-cycle of an OMS Mission Package’s
development.

The MPDD describes the implementation of the OMS Mission Package,
especially regarding the following areas:

-   Data storage allocation, including addresses, and data transfer
    protocols

-   Open Computing Environment (OCE)

-   Cybersecurity posture

-   The MPDD Security Addendum.

This document contains only non-proprietary information. Referenced
documents may contain proprietary information except in sections noted
otherwise. Proprietary information included in referenced documents
should include data transfer mechanisms and data structures, but should
not include proprietary data content. Classification of the MPDD should
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
    headings at level 2 (e.g., under Section 1, the first table in the
    section is numbered Table 1.0-1. Under Section 2.4.1, the second
    table in the section is numbered Table 2.4-2). Newly added
    tables/figures should be numbered against headings at level 3 (e.g.,
    under Section 1, the first newly added table in the section is
    numbered Table 1.0.0-1. Under Section 2.4.1, the second newly added
    table in the section is numbered 2.4.1-2). This results in
    preserving the numbering of the original tables.

Ensure correct table and figure caption styles are applied so they
appear in the List of Tables and List of Figures. Use the “TableCaption”
Style for table captions and “FigureCaption” Style for figure captions.

All documents referenced within the MPDD must include a document
reference number with release dates and be included in the compliance
package deliverable.

The documents listed in Table 0.0-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219294467" class="anchor"></span>Table 0.0-1 OMS D&D
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
<td>OMSC-GDE-003</td>
<td>Cybersecurity Guide</td>
<td>D</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-STD-001</td>
<td>OMS Standard Version 2.5</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
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

<span id="_Toc219294468" class="anchor"></span>Feedback Form Table

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

This section identifies the Units of Replaceability (UoRs), data
storage, and Open Computing Environment (OCE) of the Mission Package.

This section should describe the “as built” implementation of the
Mission Package.

References
----------

This section lists all the referenced documents that are required to
support the integration of this Mission Package as shown in Table 1.1-1,
Reference Documents.

This section should include the current OMS Standard for basis of
compliance, internal and external ICDs, and other important documents or
standards. Table 1.1-1, Reference Documents, lists all the required
reference documents.

<span id="_Toc219294469" class="anchor"></span>Table 1.1-1 Reference
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
<td>OMSC-GDE-003</td>
<td>Cybersecurity Guide</td>
<td>D</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-STD-001</td>
<td>OMS Standard Version 2.5</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-TMP-007</td>
<td>Mission Package Description Document (MPDD) Template</td>
<td>I</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>Cyber Survivability Endorsement Implementation Guide (CSEIG)</td>
<td>Version 3</td>
<td>July 2022</td>
</tr>
<tr class="odd">
<td>OAC-TMP-001</td>
<td>Mission Package Interface Module (MPIM) Description Document (MPIMDD) Template</td>
<td>B</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OAC-INS-001</td>
<td>Mission Package Interface Module (MPIM) Description Document (MPIMDD) Template Instructions</td>
<td>B</td>
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

Mission Package Worksheet
-------------------------

This section identifies the UoRs of the Mission Package by referencing
the version of the Mission Package Worksheet (MPW) identified in Table
1.2-1, Mission Package Worksheet, and UoRs identified in Table 1.2-2,
Units of Replaceability Within the Mission Package Worksheet.

The MPW:

-   Identifies the Mission Package Units of Replaceability (UoRs), i.e.,
    the Mission Package itself and its Platform, Services, Subsystems,
    and Isolators

-   Documents the compliance tiers for the Mission Package and its
    Platform, Services, and Subsystems

-   Documents CSRCs for the Mission Package

A Mission Package Worksheet (MPW) is used by the program to identify the
OMS UoRs that comprise the OMS Mission Package. It is recommended that
the "latest" MPW be referenced in this section. Historical versions or
descriptions of changes to the MPW through the history of creation may
also be provided to give context to the reader as to the evolution of
the Mission Package from initial concept to the current point in the
Mission Package lifecycle. Provide a brief description of the elements
that are in the MPW. A discussion of compliance is recommended. This
discussion can describe changes from the original MPW and the reasons
for change.

The columns in Table 1.2-1, Mission Package Worksheet, should contain
the following information:

-   Document Title – Name of the Mission Package Worksheet document

-   Document Number – Unique identifier for the document’s configuration
    control

<span id="_Toc219294470" class="anchor"></span>Table 1.2-1 Mission
Package Worksheet

<table>
<thead>
<tr class="header">
<th>Document Title</th>
<th>Document Number</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td></td>
<td></td>
</tr>
</tbody>
</table>

The columns in Table 1.2-2, Units of Replaceability Within the Mission
Package Worksheet, should contain the following information:

-   Name of UoR – Name of the UoR that appears in the Mission Package
    Worksheet document

-   Document Title – Name of the Mission Package Description Document
    (MPDD), Platform Description Document (PDD), Subsystem Description
    Document (SDD), and/or Service Contract for each UoR in the MPW
    (i.e., Mission Package, Platform, Service, Subsystem, and Isolator)

-   Document Number – Unique identifier for the document’s configuration
    control

<span id="_Toc219294471" class="anchor"></span>Table 1.2-2 Units of
Replaceability Within the Mission Package Worksheet

<table>
<thead>
<tr class="header">
<th>Name of UoR</th>
<th>Document Title</th>
<th>Document Number</th>
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

Mission Package Data Storage
----------------------------

This section identifies where Subsystems, Services, and Isolators store
files and subdirectories on a Platform or Subsystem and the capacities
available to each Subsystem, Service, and Isolators as shown in Table
1.3-1, Data Storage Allocation.

The columns should contain the following information:

-   Subsystem/Service/Isolator – one of the Subsystem, Service, or
    Isolator names listed in the MPW. Each Subsystem, Service, and
    Isolator that utilizes more than one storage location should be
    listed on a separate row

-   Data Store Label – identify the data store (FTP/NFS Server) that
    data is retrieved from or stored to

-   Data Store Address – identify via a valid URI, where on a mass
    storage device a Subsystem, Service, or Isolator can read/write
    files. If each Subsystem, Service, or Isolator will have its own
    unique directory then try to identify that. For example: <span
    class="underline">ftp://10.1.2.22/mass\_storage/services/\[Service\_Name\]/</span>

-   Storage Allocation – identify storage capacity for each Subsystem,
    Service, or Isolator listed in the first column. For shared storage
    capacity, an estimate is sufficient. If the storage capacity for
    Services and Subsystems is shared, then indicate that with a note
    after the table

-   Data Transfer Protocol(s) – identify the protocol the Subsystem,
    Service, or Isolator will utilize to access the data transfer
    server.

Note: The contents of this table are for estimation purposes only.

<span id="_Toc219294472" class="anchor"></span>Table 1.3-1 Data Storage
Allocation

<table>
<thead>
<tr class="header">
<th>Subsystem/Service/Isolator</th>
<th>Data Store Label</th>
<th>Data Store Address</th>
<th>Storage Allocation</th>
<th>Data Transfer Protocol(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Service A</td>
<td>FTP Data Store</td>
<td><span class="underline">ftp://ftpserver.local/products/[Service_name]/</span></td>
<td>1 TB</td>
<td>FTP</td>
</tr>
<tr class="even">
<td>Subsystem B</td>
<td>NFS Data Store</td>
<td>nfs://10.1.1.11/products/[Subsystem_name]/</td>
<td>2 TB</td>
<td>NFS</td>
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

Mission Package Open Computing Environment (OCE)
------------------------------------------------

This section identifies where Open Computing Environments exist within
the Mission Package as shown in Table 1.4-1, Open Computing Environment.

The Platform is responsible for providing at least one OCE
implementation as shown in the first row.

The columns should contain the following information:

-   Platform/Subsystem – one of the Platform or Subsystem names listed
    in the MPW

-   H/W – processing hardware architecture (X86-64, X86-32, PPC, ARM,
    etc.)

-   Linux – version of the Linux kernel

-   Java – version of the Java environment, if applicable

-   Virtualization – type of virtualization (e.g., Native Hypervisor,
    Hosted Hypervisor, Cloud), if applicable.

<span id="_Toc219294473" class="anchor"></span>Table 1.4-1 Open
Computing Environment

<table>
<thead>
<tr class="header">
<th>Platform/Subsystem</th>
<th>H/W</th>
<th>Linux</th>
<th>Java</th>
<th>Virtualization</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Platform</td>
<td>X86-64</td>
<td>2.6</td>
<td>SE Development Kit 11.0.6</td>
<td>Hosted Hypervisor</td>
</tr>
<tr class="even">
<td>Subsystem B</td>
<td>PPC</td>
<td>3.0.</td>
<td>N/A</td>
<td>N/A</td>
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

Mission Package External Interface
----------------------------------

This section identifies the documentation for the external interface of
the Mission Package as shown in Table 1.5-1, External Interface.

The columns should contain the following information:

-   Document Number – the number associated with the document

-   Document Title – the title of the document

Revision and date information should be entered along with number and
title in Table 1.2-1.

The external interfaces for a Mission Package are typically complex
interactions and documented at the program level. This section captures
the documents that describe the external interfaces.

For Mission Packages that have an external interface that supports
UCI-based messaging, use table 1.5-1 to identify the document number and
title for where that interface is documented.

There is no OMS standard for how such an interface is documented.
However, two documents are provided that can be useful as guidance on
what content ought to be included in interface documentation.

OAC-TMP-001 Mission Package Interface Module (MPIM) Description Document
(MPIMDD) Template

OAC-INS-001 MPIMDD Template Instructions

<span id="_Toc219294474" class="anchor"></span>Table 1.5-1 External
Interface

<table>
<thead>
<tr class="header">
<th>Document Number</th>
<th>Document Title</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>A-OMS-023</td>
<td>Program Alpha MPIM</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
</tr>
</tbody>
</table>

Cybersecurity Posture
=====================

This section identifies the cybersecurity posture of the Mission
Package.

The cybersecurity table formats specified by this template are required.
If tools are used to generate table content, the output must be
formatted to match the tabular format specified by the template. Do not
reformat the tables to utilize outputs from tools. The metadata in the
tables is the minimum information to be documented. Additional tables
and/or sections can be added to fully capture the cybersecurity posture
of the Mission Package.

Describe the cybersecurity posture of the Mission Package. The
Cybersecurity Posture section should describe the cybersecurity posture
implementation of the Mission Package. The addendum may include
classified implementation details with reference to Interface Control
Documents (ICDs). The cybersecurity posture as characterized by the
Cyber Survivability Risk Category (CSRC) identifies the level of rigor
needed to describe the cybersecurity features of the Mission Package
that fall under the applicable Cyber Survivability Attributes (CSAs).

The cybersecurity posture descriptions are in summary format with a
pointer to an external unclassified, non-proprietary document or
detailed in the follow section including diagrams to relay the
implementation.

Policy Overview
---------------

The OMS Cybersecurity Guide, OMSC-GDE-003, provides concepts and
guidance to complete OMS compliance documentation. These documents can
be used as part of a Program Protection and Systems Security Engineering
(SSE) process and incorporate concepts provided by the Joint Chiefs of
Staff (JCS) Cyber Survivability Endorsements Implementation Guide
(CSEIG). OMS documentation helps fill the gap when no external
cybersecurity requirements are present, and provides flexibility to
reference external documents when a system-level cybersecurity process
with requirements is in place. The role of OMS Cybersecurity in the SSE
process is therefore to reference or provide relevant information to
support the Adopting Program and system designers in addressing
cybersecurity requirements as shown in Figure 2.1-1. The OMS
Cybersecurity is a component of the overall cybersecurity accreditation
of the weapon system.

<img src="media/image2.png" style="width:6.5in;height:4.125in" />

<span id="_Toc219294463" class="anchor"></span>Figure 2.1-1 OMS
Cybersecurity Guidance in Acquisition

CSRC
----

This identifies the CSRC for the Mission Package as shown in Table 2.2-1
Mission Package CSRC.

The expected CSRC of the weapon system should be documented here, as
provided as part of the weapon system cybersecurity requirements.

In the table below, indicate the CSRC applicable to the Mission Package
by adding an “x”. If a CSRC is not applicable or not addressed, denote
this section with “Not Applicable” and leave Table 2.2-1 empty. See the
Cybersecurity Guide, OMSC-GDE-003, for more information.

<span id="_Toc219294475" class="anchor"></span>Table 2.2-1 Mission
Package CSRC

<table>
<thead>
<tr class="header">
<th>CSRC 1</th>
<th>CSRC 2</th>
<th>CSRC 3</th>
<th>CSRC 4</th>
<th>CSRC 5</th>
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

Cyber Survivability Attributes (CSAs)
-------------------------------------

This section identifies the CSAs applicable to the Mission Package.

Provide descriptions of the cybersecurity features used as evidence to
meet the program-assigned System Survivability Key Performance
Parameters (KPPs). These descriptions are in summary format with a
pointer to an external reference, pointer to an OMS MPDD section, or
detailed description including diagrams to relay to the reader how the
feature is employed within the Mission Package. If a CSA is not
applicable or not addressed, denote this with “Not Applicable”. See the
Cybersecurity Guide, OMSC-GDE-003, for more information.

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
<td>CSA-10: Manage System’s Configuration to Achieve and Maintain an Operationally-Relevant Cyber Risk Posture</td>
<td>AU-10(all), AU-11</td>
</tr>
</tbody>
</table>

### Prevent CSAs

This section identifies and documents the System Survivability Key
Performance Parameter (KPP) Prevent CSAs implementation for the Mission
Package. Table 2.3-1 identifies the System Survivability KPP Prevent
CSAs applicable to the Mission Package.

In the table below, indicate the CSAs applicable to the Mission Package
by adding an “x”. If the Prevent CSAs are not applicable or not
addressed, denote this section with “Not Applicable” and leave Table
2.3-1 empty.

<span id="_Toc219294476" class="anchor"></span>Table 2.3-1 Applicable
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

For the applicable CSAs, provide a brief, high-level description (1-2
sentences) of how each Cyber Survivability Attribute (CSA) identified in
Table 2.3-1 is explicitly addressed by the Mission Package. The
description should be unclassified and non-proprietary, and capture the
cybersecurity posture. The cybersecurity posture should be commensurate
with the expected CSRC.

-   CSA-01: Control Access

-   CSA-02: Reduce System’s Cyber Detectability

-   CSA-03: Secure Transmissions and Communication

-   CSA-04: Protect System Information from Exploitation

-   CSA-05: Partition and Ensure Critical Functions at Mission
    Completion Performance Levels

-   CSA-06: Minimize and Harden Attack Surfaces.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. See the Cybersecurity Guide, OMSC-GDE-003, for
more information. If referencing a previous section, denote this with a
reference to the applicable MPDD section(s). See the Cybersecurity
Guide, OMSC-GDE-003, for more information.

The following sections provide the minimum information for documenting
Prevent CSAs. Additional sections can be added as needed to fully
document the Mission Package cybersecurity.

#### Security Domain Definition

This section describes the cybersecurity policies and configurations
implemented in the Mission Package.

The MPDD may contain increasing levels of detail across its lifecycle
and may include information such as data storage, IP addresses,
processor values, wiring types, transport protocols, ports, etc.

Figure 2.3-1, Security Domain Boundaries, is a representation of the
security domains for a platform. It provides a reference for how the
network described in the PDD is connected to Subsystems which may have
single or multiple security domains.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE. REPLACE THE FOLLOWING
FIGURE WITH AN APPROPRIATE FIGURE FOR YOUR SYSTEM &gt;&gt;

<img src="media/image3.png" style="width:6.5in;height:5.21875in" />

<span id="_Toc219294464" class="anchor"></span>Figure 2.3-1 Security
Domain Boundaries

Each security domain identified in the figure should be described in
this section with the classification of the information within the
domain, specific data stores which house the data, and the use of any
isolator or controlled interface between security domains. This section
should describe the overall policy of the Mission Package and any
transfers of data across the domain. The following provides an example
summary.

Security Domain A contains &lt;insert classification&gt; data that is
considered “system high” on the platform. All system high data is stored
on the FTP Server (10.1.1.25) which is keyed via a USB thumb drive by
maintenance personnel during system startup (see PDD description of data
store encryption mechanism). As access is restricted, any access to this
data on the FTP server by users and systems must be audited and
restricted to only those individuals with proper access. Network
security measures and appropriate identification and authentication
controls are used to ensure platform maintenance personnel do not have
direct access to the system. The integrity of the software applications
used on the system are checked at startup and each time an MDF is
updated its integrity must match the **FileMetadata** information (see
Section 2.3.1.7, Cybersecurity Integrity Implementation(s)).

Security Domain B contains &lt;insert classification&gt; and is used for
sending remote users video from the platform sensor. There is no data
storage in Security Domain B. Access is restricted to the streaming data
through the use of an encrypted tunnel across the communications link.
For improved clarity of the video stream additional encoding is
utilized.

The sections that follow provide details on the flow of information
(what) and then what confidentiality and integrity is applied.
Confidentiality mechanisms applied to the data flows are broken out
further into the following: restrictions on the flow of data can go
(where), the identification and authentication of the user (who), and
what access controls there are on the data resources.

#### Cybersecurity Flow Description

This section describes the cybersecurity policies for flow control as
implemented in this Mission Package.

The information flows for OMS Data Transfers should be documented with
information flow diagram(s) and a corresponding information flow table
that identifies the actors and the information being sent in the flow
described (these items should align with the items identified in the
Service Contract or in the SDD). A separate diagram and matrix may be
used per data transfer method (e.g., FTP/NFS/HTTP/TFTP) which will have
a unique identifier for each data flow.

The following are exemplar flows that should be updated to meet the
implemented Mission Package.

Figure 2.3-2, Non-Streaming Data Transfer Information Flow Diagram,
identifies the server and clients.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE. REPLACE THE FOLLOWING
FIGURE WITH AN APPROPRIATE FIGURE FOR YOUR SYSTEM &gt;&gt;

<img src="media/image4.png" style="width:5.57292in;height:3.82292in" />

<span id="_Toc219294465" class="anchor"></span>Figure 2.3-2
Non-Streaming Data Transfer Information Flow Diagram

Table 2.3-2, Non-Streaming Data Transfer Information Flow, identifies
the actors and the information being sent in the flow described.

<span id="_Toc219294477" class="anchor"></span>Table 2.3-2 Non-Streaming
Data Transfer Information Flow

<table>
<thead>
<tr class="header">
<th>Ref #</th>
<th>Actor A (Server)</th>
<th>Actor B (Client)</th>
<th>Information Item</th>
<th>Security Domain(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Flow-001</td>
<td>FTP Server -ftpserver.local (10.1.1.11)</td>
<td>Sensor1 10.1.1.130 (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Sensor Application, Sensor Product Files</td>
<td>Domain A</td>
</tr>
<tr class="even">
<td>Flow-002</td>
<td>FTP Server (10.1.1.11)</td>
<td>Comm Gateway Isolator 10.1.1.12 (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Sensor Product Files</td>
<td>Domain A</td>
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

Figure 2.3-3, Streaming Data Transfer Information Flow Diagram,
identifies the producer and consumers.

&lt;&lt; THE FOLLOWING IS AN EXAMPLE FIGURE. REPLACE THE FOLLOWING
FIGURE WITH AN APPROPRIATE FIGURE FOR YOUR SYSTEM &gt;&gt;

<img src="media/image5.png" style="width:6.5in;height:4.01042in" />

<span id="_Toc219294466" class="anchor"></span>Figure 2.3-3 Streaming
Data Transfer Information Flow Diagram

Table 2.3-3, Streaming Data Transfer Information Flow, identifies the
actors and the information being sent in the flow described.

<span id="_Toc219294478" class="anchor"></span>Table 2.3-3 Streaming
Data Transfer Information Flow

<table>
<thead>
<tr class="header">
<th>Ref #</th>
<th>Actor A (Producer)</th>
<th>Actor B (Consumer)</th>
<th>Information Item</th>
<th>Security Domain(s)</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Flow-003</td>
<td>Sensor2 10.1.1.140 (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Local Display (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Video Stream (MPEG)</td>
<td>Domain A</td>
</tr>
<tr class="even">
<td>Flow-004</td>
<td>Sensor2 10.1.1.140 (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Remote User (Coalition)</td>
<td>Video Stream (MPEG)</td>
<td><p>Domain A</p>
<p>Domain B</p></td>
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

#### Cybersecurity Confidentiality Implementation(s)

This section describes the implemented mechanism(s) used to ensure
confidentiality of information in the Mission Packages as shown in Table
2.3-4, Confidentiality Implementation.

All confidentiality implementation for information flows of data
transfers should be described in this section. The following table with
columns:

-   Information Flow – the information flow identified in above tables
    (use same reference \#)

-   Outside of Mission Package (Yes/No) – any flow that crosses outside
    of the Mission Package

-   Ports and Protocol Restriction (Yes/No) – if any restriction of
    ports and protocol is in place that restricts that data flow
    (describe further in Section 2.3.1.4, Cybersecurity Flow, Ports, and
    Protocols Restriction Policy, the devices which perform the
    restrictions)

-   Restriction Mechanism – identify the method(s) that are implemented
    to constrain or restrict access to the information flow. This should
    include identification of expected hardware, software, and
    algorithms associated with the mechanism. If no mechanisms
    implemented or expected, input “None” in the cell

-   Implementation Summary – describe how the confidentiality mechanism
    is implemented and/or references to other documents (e.g., The ASB
    VLAN segmentation as documented in the &lt;platformName&gt; PDD)
    along with any additional information for clarification. For Secure
    Data transfers utilizing a VPN solution (e.g., IPsec, SSL) provide
    the implementation software name (e.g., strongSwan), type of VPN,
    and a pointer to the configuration file.

<span id="_Toc219294479" class="anchor"></span>Table 2.3-4
Confidentiality Implementation

<table>
<thead>
<tr class="header">
<th>Information Flow</th>
<th>Outside of Mission Package</th>
<th>Ports and Protocols Restriction</th>
<th><p>Restriction</p>
<p>Mechanism</p></th>
<th>Implementation Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Flow-001, Flow-002, Flow-003</td>
<td>N</td>
<td>Y</td>
<td>Disable Port at Network Switch, Network Switch, Host Firewall</td>
<td>Network switch disables unused ports (port down), segments network traffic and performs IP restrictions. Host firewall (iptables) on Platform Mission Processors configured to limit network traffic on specified ports.</td>
</tr>
<tr class="even">
<td>Flow-004</td>
<td>Y</td>
<td>N</td>
<td>Comm. Cross Domain Solution</td>
<td>Communications Gateway Isolator Service implements a Cross Domain Solution streaming data between security domains (see MPDD_SecurityAddendum documentation for further details)</td>
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

#### Cybersecurity Flow, Ports, and Protocols Restriction Policy

This section documents the cybersecurity policies for restricting
information flows, ports, and protocols as implemented in this Mission
Package.

Open ports accessible on the ASB network via a local connection or
across other devices expose a potential attack vector. In this section
there should be an identification of all the devices which limit flows
of those that are identified above. Data flows identified in the
previous section that are outside of the controlled boundary (Mission
Package) are flows that have the potential to expose the Mission Package
to unauthorized information flows out of control of the Mission Package.
At a minimum, the OMS Isolator and/or other boundary protection
component that restricts access based on specific IPs, range of IPs
and/or port restrictions should be described in this section.

The following table should summarize the information flow policy and
restriction of ports and protocols. This should include the
identification of the component that enforces any flow, ports and
protocols restrictions.

-   Enforcement Component – identify all the relevant components whether
    hardware, such as a network switch, software, such as a host
    firewall, or an OMS element, such as an Isolator or the ASB, which
    implement IP and/or Port restrictions

-   Controlled Flows – identify one or more of the OMS Data Transfer
    flows identified above

-   Port or Protocol Restrictions (Yes/No) – identify if the restriction
    mechanism applies to a specific TCP/UDP Port or protocol (e.g.,
    ICMP). Consider the following situations: If a network device
    restricts traffic only to IP addresses then there are no port
    restrictions (i.e., enter “N”). If a data stores host firewall
    performs only port restrictions then there are port restrictions
    (i.e., enter “Y”). The network firewall does not block ports, but
    limits the ICMP messages based on the type field, this is a protocol
    restriction (i.e., enter “Y”)

-   Restriction Method – identify if a host firewall, network access
    control list or other boundary protection mechanism is put in place
    to restrict the flow of information (e.g., host firewall IP:port
    restrictions via iptables, network ACL)

-   Implementation Summary – a summary description of the type of policy
    enforcement in use (e.g., stateful packet firewall) and
    identification of documentation that can provide specific
    implementation configuration details (e.g., network ACL output).

Table 2.3-5, Ports and Protocol Enforcement Policy, summarizes the
information flow policy and restriction of ports and protocols.

This should include the identification of the component that enforces
any flow, ports and protocols restrictions.

<span id="_Toc219294480" class="anchor"></span>Table 2.3-5 Ports and
Protocol Enforcement Policy

<table>
<thead>
<tr class="header">
<th>Enforcement Component</th>
<th>Controlled Flows</th>
<th>Port and Protocol Restrictions</th>
<th>Restriction Method</th>
<th>Implementation Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Network Switch</td>
<td>Flow-001, Flow-002, Flow-003, Flow-004</td>
<td>N</td>
<td>Access Control List – IP Address restriction</td>
<td>ACL restricts only IP address (see MissionPackage_NetworkSwitch_Config documentation for further details)</td>
</tr>
<tr class="even">
<td>Host Firewall</td>
<td>Flow-001, Flow-002, Flow-003, Flow-004</td>
<td>Y</td>
<td>iptables port restrictions on mission processors</td>
<td>Iptables limits ports to only those documented in Table 15 (see MissionPackage_HostFirewall_Config documentation for further details)</td>
</tr>
<tr class="odd">
<td>Isolator Service</td>
<td>Flow-004</td>
<td>Y</td>
<td>Cross-Domain Solution</td>
<td>Communications Gateway Isolator Service implements a Cross Domain Solution streaming data between security domains (see MPDD_SecurityAddendum documentation for further details)</td>
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

Table 2.3-6, Open Ports and Protocols, summarizes the open ports and
protocols on the Mission Package.

-   Port – identify the network port number and the transport (OSI
    Layer 4) protocol (TCP or UDP) being used

-   Protocol – identify the application (OSI Layer 7) protocol (e.g.,
    FTP, HTTP, NFS) being used on the open port

-   Process/Service – identify the process (e.g., on Linux, the netstat
    command will provide OS process names) or Service (e.g., on Linux,
    the nmap command will provide OS service names) that has the port
    open

-   Address – the IP address of the system which port is referred to in
    the port

-   Purpose – identify the purpose of the open port

-   Restriction Mechanism – identify any mechanism on the host (e.g.,
    iptables) or network (e.g., network ACL) to constrain or prevent
    data transmission if no mechanisms are used, input “None” in the
    cell.

<span id="_Toc219294481" class="anchor"></span>Table 2.3-6 Open Ports
and Protocols

<table>
<thead>
<tr class="header">
<th>Port (TCP/UDP)</th>
<th>Protocol</th>
<th>Process/Service</th>
<th>Address</th>
<th>Purpose</th>
<th>Restriction Mechanism</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>21/TCP</td>
<td>FTP</td>
<td>vsftpd</td>
<td>10.1.1.11</td>
<td>FTP Server</td>
<td>iptables firewall</td>
</tr>
<tr class="even">
<td>111/TCP</td>
<td>RPCPortmapper</td>
<td>Portmapper</td>
<td>10.1.1.11</td>
<td>NFS Server</td>
<td>iptables firewall</td>
</tr>
<tr class="odd">
<td>2049/TCP</td>
<td>NFSv3</td>
<td>nfsd</td>
<td>10.1.1.11</td>
<td>NFS Server</td>
<td>iptables firewall</td>
</tr>
<tr class="even">
<td>3260/TCP</td>
<td>iSCSI</td>
<td>iscsid</td>
<td>10.1.1.100</td>
<td>iSCSI</td>
<td>Iptables firewall</td>
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

> Table 2.3-7, Product/Data and Data Transfer Servers, identifies the
> products being sent or received by the Data Transfer server.

-   Client Address – the resolvable address or IP address of the client

-   Product/Data – the product or data item being sent or received from
    a server

-   Format – The format of the product (identify OMS approved data
    format) or data type (ASCII file, xml, binary, etc.)

-   Send/Receive – Send = upload, write or Receive = download, read

-   Data Transfer Server – identify via the URI (or address) the Data
    Transfer server that data is being sent or received.

<span id="_Toc219294482" class="anchor"></span>Table 2.3-7 Product/Data
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
<td><span class="underline">ftp://ftpserver.local/products/</span></td>
</tr>
<tr class="even">
<td>10.1.1.130</td>
<td>Sensor Application</td>
<td>Binary File</td>
<td>Receive</td>
<td><span class="underline">ftp://ftpserver.local/SW_APP/</span></td>
</tr>
<tr class="odd">
<td>10.1.1.130</td>
<td>Sensor Product Files</td>
<td>NITF</td>
<td>Send</td>
<td><span class="underline">ftp://ftpserver.local/products/</span></td>
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

#### Cybersecurity Identification & Authentication Implementation(s)

This section documents the mechanism(s) used to identify Platform,
Subsystems, Services, and Isolators as implemented as shown in Table
2.3-8, Data Transfer Protocol Identification & Authentication.

The Mission Package identification and authentication implementations
for Data Transfer protocols should be described in this section. The
matrix below should describe if anonymous logins are allowed, what is
the unique identifier used for logins (if any) and what mechanism is
used for authentication. For authentication mechanisms identified a
description of how passwords, tokens, etc. are distributed.

The following table provides insight into how Identification and
Authentication is handled by a non-streaming (file-based) data transfer.

-   Data Transfer Server – a resolvable location or URI for each server
    on the Mission Package

-   Anonymous Login (Yes/No) – identify if the server allows anonymous
    logins

-   Client Identification – for the data transfer server what specific
    identifier is used to identify a remote user (e.g., UUID of Services
    are the login username)

-   Authentication Mechanism – this should identify the mechanism used
    for authentication and if credentials (passwords) are used how they
    are distributed. (e.g., TFTP Server: IP firewall to only those
    systems requiring access w/ time limited availability. FTP Server:
    Username/Password – Username provided in OMS configuration file,
    password sent via MDF configuration file).

<span id="_Toc219294483" class="anchor"></span>Table 2.3-8 Data Transfer
Protocol Identification & Authentication

<table>
<thead>
<tr class="header">
<th>Data Transfer Server</th>
<th>Anonymous Login (Yes/No)</th>
<th>Client Identification</th>
<th>Authentication Mechanism</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>ftpserver.local (FTP)</td>
<td>No</td>
<td>Username is UUID of Service</td>
<td>Username and password combinations are used for FTP authentication. Authentication configuration is detailed in MissionPackage_FTPServer_Config documentation.</td>
</tr>
<tr class="even">
<td>10.1.1.11 (NFS)</td>
<td>No</td>
<td>Username is UUID of Service</td>
<td>Username and password combinations are used for NFS authentication. Authentication configuration for NFS is detailed in MissionPackage_NFSServer_Config documentation.</td>
</tr>
<tr class="odd">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

#### Cybersecurity Access Controls

This section describes the cybersecurity policies for access control as
implemented in this Mission Package.

##### Non-Streaming Data Transfer Access Controls

This section documents the access control policy in place for the data
transfer within the Mission Package as shown in Table 2.3-9,
Non-Streaming Data Transfer Access Control Policy.

The following table provides the following columns to be addressed on
every flow for non-streaming data transfers:

-   Data Flow – identify one or more of the OMS Data Transfer flows
    identified above

-   Server – This is the actor (FTP/NFS/TFTP/HTTP Server) that a client
    connects to and stores and retrieves files. Provides the resource
    identified in a URI

-   Client – this is the actor in the data flow which operates as an
    FTP/NFS client

-   Permissions – specify the permissions that the server system uses
    for controlling access to data (e.g., R-Read/W-Write/X-Execute;
    user, group, system IDs.). Additional sub-columns under permission
    can be added

-   Information Item (Product/Data) – The information item may combine
    one or more “product/data” items from SDD Table 9.1-2 which go to
    the same server into a single line item. The separate data items
    should be identified. The table entry should describe both the data
    product that is transferred and its associated access permissions.
    For example, based on the information within the data flow transfer,
    certain items may be read only and other items read/write. Such a
    distinction should be made (e.g., Software Application Load (Read),
    Product Data Storage (Write))

-   Implementation Summary – a summary description of the type of access
    control in use (e.g., RBAC) and identification of documentation that
    can provide specific implementation configuration details (e.g., PDD
    Access Control reference).

What follows is an example set of tables, diagrams and explanation text
to assist in documenting the policy of the Mission Package.

<span id="_Toc219294484" class="anchor"></span>Table 2.3-9 Non-Streaming
Data Transfer Access Control Policy

<table>
<thead>
<tr class="header">
<th>Data Flow</th>
<th>Server</th>
<th>Client</th>
<th>Permissions</th>
<th>Information Item (Product/Data)</th>
<th>Implementation Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Flow-001</td>
<td>10.1.1.11</td>
<td>10.1.1.130</td>
<td>Read/Write</td>
<td>Sensor Application, Sensor Product Files</td>
<td>The FTP Server implements RBAC with each Subsystem having read-only access to software applications and write access to the products folder.</td>
</tr>
<tr class="even">
<td>Flow-002</td>
<td>10.1.1.11</td>
<td>10.1.1.12</td>
<td>Read</td>
<td>Sensor Product Files</td>
<td>The FTP Server implements RBAC with each product processing Service having read-only access to the products folder. Details regarding the transfer for the Isolator are detailed in the MPDD_SecurityAddendum.</td>
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

##### Streaming Data Transfer Access Controls

This section describes the streaming data flows and the mechanism that
is used to initiate the start of the streaming data transfer as shown in
Table 2.3-10, Streaming Data Transfer Access Control Policy.

The following table provides the following columns to be addressed on
every flow for streaming data transfers:

-   Data Flow – identify one or more of the OMS Data Transfer flows
    identified above

-   Producer – This is the actor that produces the data stream. Provides
    the resource identified in a URI

-   Consumer – this is the actor in the data flow which receives the
    data stream

-   Permissions – specify the permissions that the producer uses for
    controlling access to the data stream. Additional sub-columns under
    permission can be added

-   Information Item – The information item may combine one or more
    “product/data” items from SDD Table 9.1-2 which go to the same
    server into a single line item. The separate data items should be
    identified. The table entry should describe both the data product
    that is transferred and its associated access permissions. If the
    consumer separates channels based on roles, this could be captured
    in this table entry point

-   Implementation Summary – A summary description of how access control
    is implemented (e.g., username/password) and/or references to other
    documents (e.g., &lt;server name&gt; access control is documented in
    the &lt;platformName&gt; PDD) along with any additional information
    for clarification.

<span id="_Toc219294485" class="anchor"></span>Table 2.3-10 Streaming
Data Transfer Access Control Policy

<table>
<thead>
<tr class="header">
<th>Data Flow</th>
<th>Producer</th>
<th>Consumer</th>
<th>Permissions</th>
<th>Information Item (Product/Data)</th>
<th>Implementation Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Flow-003</td>
<td>Sensor2 10.1.1.140 (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Local Display (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>None</td>
<td>Video Stream</td>
<td>No Access Control</td>
</tr>
<tr class="even">
<td>Flow-004</td>
<td>Sensor2 10.1.1.140 (Svc UUID: XXXX-XXX-XXX-XXXXXX)</td>
<td>Remote User (Coalition)</td>
<td>Username/ Password</td>
<td>Video Stream</td>
<td>The producer publishes the URI of the stream in the ProductLocation message. The Isolator Service acts as an RTSP server and the Remote User (Coalition) client issues an RTSP SETUP request using the URL to send the data to requested clients. Details regarding this are detailed in the MPDD SecurityAddendum</td>
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

#### Cybersecurity Integrity Implementation(s)

This section documents the implemented mechanism(s) used to ensure
integrity of data in the Mission Package as shown in Table 2.3-11,
Integrity Implementation.

Describe usage of Integrity Implementations in use that protect data
transfers. The following describes the definitions of each of the
columns:

-   Information Flow – the information flow identified in above tables
    (use same reference \#)

-   Outside of Mission Package (Yes/No) – any flow that crosses outside
    of the Mission Package

-   Integrity Mechanism – Identify the method(s) used in the Mission
    Package to provide integrity. This should include identification of
    applicable hardware, software, and algorithm associated with the
    implemented mechanism

-   Implementation Summary – How the integrity mechanism is implemented
    (e.g., IPsec w/ SHA-256 HMAC algorithm) and/or references to other
    documents (e.g., The ASB Ethernet integrity mechanism as documented
    in the &lt;platformName&gt; PDD) along with any additional
    information for clarification.

<span id="_Toc219294486" class="anchor"></span>Table 2.3-11 Integrity
Implementation

<table>
<thead>
<tr class="header">
<th>Information Flow</th>
<th>Outside of Mission Package</th>
<th>Integrity Mechanism</th>
<th>Implementation Summary</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Flow-001, Flow-002</td>
<td>N</td>
<td>Network Stack, Hash of File</td>
<td>Ethernet stack checksums and the <strong>ProductMetadata</strong> hash values produced by the Subsystem are used when reading and sending data products.</td>
</tr>
<tr class="even">
<td>Flow-003</td>
<td>N</td>
<td>Network Stack</td>
<td>Ethernet Stack checksums</td>
</tr>
<tr class="odd">
<td>Flow-004</td>
<td>Y</td>
<td>Reed-Solomon</td>
<td>Network stream has an application integrity layer that implements Reed-Solomon encoding to improve the integrity of the data stream (see MPDD_SecurityAddendum for further implementation details)</td>
</tr>
<tr class="even">
<td>Add rows as required</td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

### Mitigate CSAs

This section identifies and documents the System Survivability KPP
Mitigate CSAs implementation for the Mission Package. Table 2.3-12
identifies the System Survivability KPP Mitigate CSAs applicable to the
Mission Package.

In the table below, indicate the CSAs applicable to the Mission Package
by adding an “x”. If the Mitigate CSAs are not applicable or not
addressed, denote this section with “Not Applicable” and leave Table
2.3-12 empty.

<span id="_Toc219294487" class="anchor"></span>Table 2.3-12 Applicable
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

For the applicable CSAs, provide a brief high-level description (1-2
sentences) of how each Cyber Survivability Attribute (CSA) is explicitly
addressed by the Mission Package. The description should be unclassified
and non-proprietary, and capture the cybersecurity posture. The
cybersecurity posture should be commensurate with the expected CSRC.

-   CSA-07 Baseline and Monitor Systems and Detect Anomalies

-   CSA-08 Manage System Performance and Enable Cyberspace Defense

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable MPDD section(s). See the
Cybersecurity Guide, OMSC-GDE-003, for more information.

### Recover CSA

This section identifies and documents the System Survivability KPP
Recover CSA implementation for the Mission Package.

Provide a brief high-level description (1-2 sentences) of how the CSA-09
Recover System Capabilities is explicitly addressed by the Mission
Package. The description should be unclassified and non-proprietary, and
capture the cybersecurity posture. The cybersecurity posture should be
commensurate with the expected CSRC.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable MPDD section(s). See the
Cybersecurity Guide, OMSC-GDE-003, for more information.

If the Recover CSA is not applicable or not addressed, denote this with
“Not Applicable”.

### Adapt CSA

This section identifies and documents the System Survivability KPP Adapt
CSA implementation for the Mission Package.

Provide a brief high-level description (1-2 sentences) of how the CSA-10
Actively Manage System’s Configurations to Achieve and Maintain an
Operationally-Relevant Cyber Risk Posture is explicitly addressed by the
Mission Package. The description should be unclassified and
non-proprietary, and capture the cybersecurity posture. The
cybersecurity posture should be commensurate with the expected CSRC.

If an external source is referenced for additional information on the
CSA implementation, denote this with a reference to the unclassified,
non-proprietary document. If referencing a previous section, denote this
with a reference to the applicable MPDD section(s). See the
Cybersecurity Guide, OMSC-GDE-003, for more information.

If the Adapt CSA is not applicable or not addressed, denote this with
“Not Applicable”.

Cyber Survivability Rationale
-----------------------------

This subsection describes Cyber Survivability rationale.

Provide a brief high-level summary of the verification methods
(inspection, analysis, tests, etc.) and evidence used to assess the
cybersecurity implementation meets the expected CSRC. The description
should be unclassified and non-proprietary. See the Cybersecurity Guide,
OMSC-GDE-003, for more information.

Security Addendum
=================

This section identifies the Security Addendum document(s).

The Security Addendum is expected to be external to the MPDD and can be
composed of one or more separate documents that:

-   Might already be existing/planned program documents that could be
    referenced to supply OMS-related information,

-   Might have to be published at different security levels, and

-   Could be developed/published at different points in the program
    lifecycle.

The name of the document(s) must be unclassified and non-proprietary.
Referenced documents may be both classified and proprietary. The
Security Addendum should describe the Security Information Exchanges
implemented by the Platform, Subsystems, Services, and Isolators, and
provides additional, classified and/or proprietary details relating to
the security of the Mission Package. The addendum may include classified
implementation details with reference to Interface Control Documents
(ICDs).

Appendix A Acronyms and Abbreviations
=====================================

This section lists the abbreviations and acronyms used in this document
not a copy of the OMS lexicon as shown in Table A.0-1, List of Acronyms
and Abbreviation Definitions.

In addition, acronyms should be spelled out at first use in the body of
the document.

<span id="_Toc219294488" class="anchor"></span>Table A.0-1 List of
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

<span id="_Toc219294489" class="anchor"></span>Table B.0-1 List of Term
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
