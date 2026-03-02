Open Mission Systems (OMS)

Definition And Documentation (D&D)

Version Description Document (VDD)

VERSION 002.5

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary open architecture for
integrating subsystems and services into mission packages.

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

[1 Scope 1](#scope)

[1.1 Program Overview 1](#program-overview)

[1.2 Documentation Overview 1](#documentation-overview)

[2 Component Documents 2](#component-documents)

[3 Changes for the Definition and Documentation (D&D)
4](#changes-for-the-definition-and-documentation-dd)

[3.1 OAM Requests Applied to Version 2.4
4](#oam-requests-applied-to-version-2.4)

[3.2 Changes from D&D Version 2.4 to Version 2.5 4](#_Toc219289744)

[3.2.1 Changes to the OMS Standard, OMSC-STD-001
4](#changes-to-the-oms-standard-omsc-std-001)

[3.2.2 Changes to the Abbreviations and Glossary, OMSC-STD-002
4](#changes-to-the-abbreviations-and-glossary-omsc-std-002)

[3.2.3 Changes to the CAL Specification, OMSC-SPC-001
5](#changes-to-the-cal-specification-omsc-spc-001)

[3.2.4 Changes to the Java CAL I/F Generation Specification,
OMSC-SPC-007
5](#changes-to-the-java-cal-if-generation-specification-omsc-spc-007)

[3.2.5 Changes to the C++ CAL I/F Generation Specification, OMSC-SPC-008
5](#changes-to-the-c-cal-if-generation-specification-omsc-spc-008)

[3.2.6 Changes to the OS Façade API Specification, OMSC-SPC-005
5](#changes-to-the-os-façade-api-specification-omsc-spc-005)

[3.2.7 Changes to the Cybersecurity Guide, OMSC-GDE-003
6](#changes-to-the-cybersecurity-guide-omsc-gde-003)

[3.2.8 Changes to the Mission Package Worksheet Template, OMSC-TMP-006
6](#changes-to-the-mission-package-worksheet-template-omsc-tmp-006)

[3.2.9 Changes to the Mission Package Worksheet Instructions,
OMSC-INS-013
6](#changes-to-the-mission-package-worksheet-instructions-omsc-ins-013)

[3.2.10 Changes to the Mission Package Description Document Template,
OMSC-TMP-007
6](#changes-to-the-mission-package-description-document-template-omsc-tmp-007)

[3.2.11 Changes to the Mission Package Description Document
Instructions, OMSC-INS-007
7](#changes-to-the-mission-package-description-document-instructions-omsc-ins-007)

[3.2.12 Changes to the Platform Description Document Template,
OMSC-TMP-001
7](#changes-to-the-platform-description-document-template-omsc-tmp-001)

[3.2.13 Changes to the Platform Description Document Instructions,
OMSC-INS-001
7](#changes-to-the-platform-description-document-instructions-omsc-ins-001)

[3.2.14 Changes to the Subsystem Description Document Template,
OMSC-TMP-002
7](#changes-to-the-subsystem-description-document-template-omsc-tmp-002)

[3.2.15 Changes to the Subsystem Description Document Instructions,
OMSC-INS-002
8](#changes-to-the-subsystem-description-document-instructions-omsc-ins-002)

[3.2.16 Changes to the Service Contract Template, OMSC-TMP-003
8](#changes-to-the-service-contract-template-omsc-tmp-003)

[3.2.17 Changes to the Service Contract Instructions, OMSC-INS-003
8](#changes-to-the-service-contract-instructions-omsc-ins-003)

[3.2.18 Changes to the OMS Mission Package Checklist Instructions,
OMSC-INS-008
8](#changes-to-the-oms-mission-package-checklist-instructions-omsc-ins-008)

[3.2.19 Changes to the OMS Platform Checklist Instructions, OMSC-INS-009
9](#changes-to-the-oms-platform-checklist-instructions-omsc-ins-009)

[3.2.20 Changes to the OMS Subsystem Checklist Instructions,
OMSC-INS-010
9](#changes-to-the-oms-subsystem-checklist-instructions-omsc-ins-010)

[3.2.21 Changes to the OMS Service Checklist Instructions, OMSC-INS-011
9](#changes-to-the-oms-service-checklist-instructions-omsc-ins-011)

[3.2.22 Changes to the OMS Isolator Checklist Instructions, OMSC-INS-012
9](#changes-to-the-oms-isolator-checklist-instructions-omsc-ins-012)

[3.2.23 Language-Agnostic CAL Specification, OMSC-SPC-013
10](#language-agnostic-cal-specification-omsc-spc-013)

This page is intentionally left blank.

List of Tables

[Table 2.1-1 Component Documents of the OMS D&D Set Version 2.5
2](#_Toc219289768)

[Table 3.1-1 OAM Requests Applied to Version 2.4 4](#_Toc219289769)

[Table 3.2-1 OMS Standard Changes (D&D v2.4 to v2.5) 4](#_Toc219289770)

[Table 3.2-2 Abbreviations and Glossary Changes (D&D v2.4 to v2.5)
4](#_Toc219289771)

[Table 3.2-3 CAL Specification Changes (D&D v2.4 to v2.5)
5](#_Toc219289772)

[Table 3.2-4 Java CAL I/F Generation Specification Changes (D&D v2.4 to
v2.5) 5](#_Toc219289773)

[Table 3.2-5 C++ CAL I/F Generation Specification Changes (D&D v2.4 to
v2.5) 5](#_Toc219289774)

[Table 3.2-6 OS Façade API Specification Changes (D&D v2.4 to v2.5)
5](#_Toc219289775)

[Table 3.2-7 Cybersecurity Guide Changes (D&D v2.4 to v2.5)
6](#_Toc219289776)

[Table 3.2-8 MPW Template Changes (D&D v2.4 to v2.5) 6](#_Toc219289777)

[Table 3.2-9 MPW Instructions Changes (D&D v2.4 to v2.5)
6](#_Toc219289778)

[Table 3.2-10 MPDD Template Changes (D&D v2.4 to v2.5)
6](#_Toc219289779)

[Table 3.2-11 MPDD Instructions Changes (D&D v2.4 to v2.5)
7](#_Toc219289780)

[Table 3.2-12 PDD Template Changes (D&D v2.4 to v2.5) 7](#_Toc219289781)

[Table 3.2-13 PDD Instructions Changes (D&D v2.4 to v2.5)
7](#_Toc219289782)

[Table 3.2-14 SDD Template Changes (D&D v2.4 to v2.5) 7](#_Toc219289783)

[Table 3.2-15 SDD Instructions Changes (D&D v2.4 to v2.5)
8](#_Toc219289784)

[Table 3.2-16 Service Contract Template Changes (D&D v2.4 to v2.5)
8](#_Toc219289785)

[Table 3.2-17 Service Contract Instructions Changes (D&D v2.4 to v2.5)
8](#_Toc219289786)

[Table 3.2-18 OMS Mission Package Checklist Instructions Changes (D&D
v2.4 to v2.5) 8](#_Toc219289787)

[Table 3.2-19 OMS Platform Checklist Instructions Changes (D&D v2.4 to
v2.5) 9](#_Toc219289788)

[Table 3.2-20 OMS Subsystem Checklist Instructions Changes (D&D v2.4 to
v2.5) 9](#_Toc219289789)

[Table 3.2-21 OMS Service Checklist Instructions Changes (D&D v2.4 to
v2.5) 9](#_Toc219289790)

[Table 3.2-22 OMS Isolator Checklist Instructions Changes (D&D v2.4 to
v2.5) 9](#_Toc219289791)

[Table 3.2-23 OMS Language-Agnostic CAL Specification (D&D 2.4 to v2.5)
10](#_Toc219289792)

This page is intentionally left blank.

Scope
=====

This Version Description Document (VDD) identifies all documents that
are delivered as part of the Open Mission Systems (OMS) Definition &
Documentation (D&D) set.

Program Overview
----------------

Open Mission Systems (OMS) is an industry-led initiative to develop and
demonstrate a consensus-driven, non-proprietary, open architecture for
integrating subsystems and services into platforms. The business cases
driving this effort are the need to reduce acquisition and life-cycle
costs as well as the need to reduce the risks associated with
development, sustainment, technology refresh, and capability upgrades of
mission system architectures on weapon systems. The OMS industry
participants have developed and are maturing a mission systems
architecture defined by key system interfaces between OMS Subsystems
(i.e., payloads and sensors) and Services connected through an Abstract
Service Bus (ASB). These consensus-defined interfaces use open and
standardized interface definitions, but decouple the technical
implementations from the interfaces to enable future technology upgrades
and provide flexibility that allows Platform, Subsystem and Service
providers to offer innovative and competitive solutions to future
problems.

Documentation Overview
----------------------

This OMS D&D includes the OMS Standard and supporting documents, and
references key externally published OMS documents which define
requirements, provide architecture definition and guidance, and specify
compliance assessment approaches that enable an OMS adopting program to
include OMS in their acquisition specifications.

Component Documents
===================

Table 2.1-1 lists all documents that are delivered as components of the
Open Mission Systems (OMS) Definition and Documentation (D&D) set.

<span id="_Toc219289768" class="anchor"></span>Table 2.1-1 Component
Documents of the OMS D&D Set Version 2.5

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
<tr class="even">
<td>OMSC-TMP-001</td>
<td>Platform Description Document (PDD) Template</td>
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
<td>OMSC-TMP-006</td>
<td>Mission Package Worksheet (MPW) Template</td>
<td>H</td>
<td>22 January 2026</td>
</tr>
<tr class="even">
<td>OMSC-TMP-007</td>
<td>Mission Package Description Document (MPDD) Template</td>
<td>I</td>
<td>22 January 2026</td>
</tr>
<tr class="odd">
<td>OMSC-VDD-001</td>
<td>Version Description Document (VDD)</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>

Changes for the Definition and Documentation (D&D)
==================================================

OAM Requests Applied to Version 2.4
-----------------------------------

Table 3.1-1 lists the OAM Requests Applied to Version 2.4 of the D&D,
which once incorporated, became part of the Version 2.5 release.

<span id="_Toc219289769" class="anchor"></span>Table 3.1-1 OAM Requests
Applied to Version 2.4

<table>
<thead>
<tr class="header">
<th>OAM Request Identifier</th>
<th>Title</th>
<th>Date</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
<td></td>
</tr>
</tbody>
</table>

Changes from D&D Version 2.4 to Version 2.5
-------------------------------------------

The tables in this section provide a summary of the OAM Requests applied
to each document in the D&D set.

### Changes to the OMS Standard, OMSC-STD-001

Table 3.2-1, OMS Standard Changes (D&D v2.4 to v2.5), provides a summary
of the changes to the OMS Standard, OMSC-STD-001, from D&D Version 2.4
(document revision L) to D&D Version 2.5 (document revision M).

<span id="_Toc219289770" class="anchor"></span>Table 3.2-1 OMS Standard
Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Abbreviations and Glossary, OMSC-STD-002

Table 3.2-2, Abbreviations and Glossary Changes (D&D v2.4 to v2.5),
provides a summary of the changes to the Abbreviations and Glossary,
OMSC-STD-002, from D&D Version 2.4 (document revision L) to D&D Version
2.5 (document revision M).

<span id="_Toc219289771" class="anchor"></span>Table 3.2-2 Abbreviations
and Glossary Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the CAL Specification, OMSC-SPC-001

Table 3.2-3, CAL Specification Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Critical Abstraction Layer (CAL)
Specification, OMSC-SPC-001, from D&D Version 2.4 (document revision K)
to D&D Version 2.5 (document revision L).

<span id="_Toc219289772" class="anchor"></span>Table 3.2-3 CAL
Specification Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Java CAL I/F Generation Specification, OMSC-SPC-007

Table 3.2-4, Java CAL I/F Generation Specification Changes (D&D v2.4 to
v2.5), provides a summary of the changes to the Java Critical
Abstraction Layer (CAL) Interface Generation Specification,
OMSC-SPC-007, from D&D Version 2.4 (document revision J) to D&D Version
2.5 (document revision K).

<span id="_Toc219289773" class="anchor"></span>Table 3.2-4 Java CAL I/F
Generation Specification Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the C++ CAL I/F Generation Specification, OMSC-SPC-008

Table 3.2-5, C++ CAL I/F Generation Specification Changes (D&D v2.4 to
v2.5), provides a summary of the changes to the C++ Critical Abstraction
Layer (CAL) Interface Generation Specification, OMSC-SPC-008, from D&D
Version 2.4 (document revision J) to D&D Version 2.5 (document revision
K).

<span id="_Toc219289774" class="anchor"></span>Table 3.2-5 C++ CAL I/F
Generation Specification Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the OS Façade API Specification, OMSC-SPC-005

Table 3.2-6, OS Façade API Specification Changes (D&D v2.4 to v2.5),
provides a summary of the changes to the Operating System (OS) Façade
Application Programming Interface (API) Specification, OMSC-SPC-005,
from D&D Version 2.4 (document revision I) to D&D Version 2.5 (document
revision J).

<span id="_Toc219289775" class="anchor"></span>Table 3.2-6 OS Façade API
Specification Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Cybersecurity Guide, OMSC-GDE-003

Table 3.2-7, Cybersecurity Guide Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Cybersecurity Guide, OMSC-GDE-003, from
D&D Version 2.4 (document revision C) to D&D Version 2.5 (document
revision D).

<span id="_Toc219289776" class="anchor"></span>Table 3.2-7 Cybersecurity
Guide Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Mission Package Worksheet Template, OMSC-TMP-006

Table 3.2-8, MPW Template Changes (D&D v2.4 to v2.5), provides a summary
of the changes to the Mission Package Worksheet (MPW) Template,
OMSC-TMP-006, from D&D Version 2.4 (document revision G) to D&D Version
2.5 (document revision H).

<span id="_Toc219289777" class="anchor"></span>Table 3.2-8 MPW Template
Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Mission Package Worksheet Instructions, OMSC-INS-013

Table 3.2-9, MPW Instructions Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Mission Package Worksheet (MPW)
Instructions, OMSC-INS-013, from D&D Version 2.4 (document revision G)
to D&D Version 2.5 (document revision H).

<span id="_Toc219289778" class="anchor"></span>Table 3.2-9 MPW
Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Mission Package Description Document Template, OMSC-TMP-007

Table 3.2-10, MPDD Template Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Mission Package Description Document
(MPDD) Template, OMSC-TMP-007, from D&D Version 2.4 (document revision
H) to D&D Version 2.5 (document revision I).

<span id="_Toc219289779" class="anchor"></span>Table 3.2-10 MPDD
Template Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Mission Package Description Document Instructions, OMSC-INS-007

Table 3.2-11, MPDD Instructions Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Mission Package Description Document
(MPDD) Instructions, OMSC-INS-007, from D&D Version 2.4 (document
revision H) to D&D Version 2.5 (document revision I).

<span id="_Toc219289780" class="anchor"></span>Table 3.2-11 MPDD
Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Platform Description Document Template, OMSC-TMP-001

Table 3.2-12, PDD Template Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Platform Description Document (PDD)
Template, OMSC-TMP-001, from D&D Version 2.4 (document revision L) to
D&D Version 2.5 (document revision M).

<span id="_Toc219289781" class="anchor"></span>Table 3.2-12 PDD Template
Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Platform Description Document Instructions, OMSC-INS-001

Table 3.2-13, PDD Instructions Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Platform Description Document (PDD)
Instructions, OMSC-INS-001, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289782" class="anchor"></span>Table 3.2-13 PDD
Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Subsystem Description Document Template, OMSC-TMP-002

Table 3.2-14, SDD Template Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Subsystem Description Document (SDD)
Template, OMSC-TMP-002, from D&D Version 2.4 (document revision L) to
D&D Version 2.5 (document revision M).

<span id="_Toc219289783" class="anchor"></span>Table 3.2-14 SDD Template
Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Subsystem Description Document Instructions, OMSC-INS-002

Table 3.2-15, SDD Instructions Changes (D&D v2.4 to v2.5), provides a
summary of the changes to the Subsystem Description Document (SDD)
Instructions, OMSC-INS-002, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289784" class="anchor"></span>Table 3.2-15 SDD
Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Service Contract Template, OMSC-TMP-003

Table 3.2-16, Service Contract Template Changes (D&D v2.4 to v2.5),
provides a summary of the changes to the Service Contract Template,
OMSC-TMP-003, from D&D Version 2.4 (document revision L) to D&D Version
2.5 (document revision M).

<span id="_Toc219289785" class="anchor"></span>Table 3.2-16 Service
Contract Template Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the Service Contract Instructions, OMSC-INS-003

Table 3.2-17, Service Contract Instructions Changes (D&D v2.4 to v2.5),
provides a summary of the changes to the Service Contract Template
Instructions, OMSC-INS-003, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289786" class="anchor"></span>Table 3.2-17 Service
Contract Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the OMS Mission Package Checklist Instructions, OMSC-INS-008

Table 3.2-18, OMS Mission Package Checklist Instructions Changes (D&D
v2.4 to v2.5), provides a summary of the changes to the OMS Mission
Package Checklist Instructions, OMSC-INS-008, from D&D Version 2.4
(document revision L) to D&D Version 2.5 (document revision M).

<span id="_Toc219289787" class="anchor"></span>Table 3.2-18 OMS Mission
Package Checklist Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the OMS Platform Checklist Instructions, OMSC-INS-009

Table 3.2-19, OMS Platform Checklist Instructions Changes (D&D v2.4 to
v2.5), provides a summary of the changes to the OMS Platform Checklist
Instructions, OMSC-INS-009, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289788" class="anchor"></span>Table 3.2-19 OMS Platform
Checklist Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the OMS Subsystem Checklist Instructions, OMSC-INS-010

Table 3.2-20, OMS Subsystem Checklist Instructions Changes (D&D v2.4 to
v2.5), provides a summary of the changes to the OMS Subsystem Checklist
Instructions, OMSC-INS-010, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289789" class="anchor"></span>Table 3.2-20 OMS
Subsystem Checklist Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the OMS Service Checklist Instructions, OMSC-INS-011

Table 3.2-21, OMS Service Checklist Instructions Changes (D&D v2.4 to
v2.5), provides a summary of the changes to the OMS Service Checklist
Instructions, OMSC-INS-011, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289790" class="anchor"></span>Table 3.2-21 OMS Service
Checklist Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Changes to the OMS Isolator Checklist Instructions, OMSC-INS-012

Table 3.2-22, OMS Isolator Checklist Instructions Changes (D&D v2.4 to
v2.5), provides a summary of the changes to the OMS Isolator Checklist
Instructions, OMSC-INS-012, from D&D Version 2.4 (document revision L)
to D&D Version 2.5 (document revision M).

<span id="_Toc219289791" class="anchor"></span>Table 3.2-22 OMS Isolator
Checklist Instructions Changes (D&D v2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

### Language-Agnostic CAL Specification, OMSC-SPC-013

Table 3.2-23, Language-Agnostic CAL Specification (D&D v2.4 to v2.5),
provides a summary of the changes to the OMS Language-Agnostic CAL
Specification, OMSC-SPC-013, from D&D Version 2.4 (document revision A)
to D&D Version 2.5 (document revision B).

<span id="_Toc219289792" class="anchor"></span>Table 3.2-23 OMS
Language-Agnostic CAL Specification (D&D 2.4 to v2.5)

<table>
<thead>
<tr class="header">
<th>OAM Request(s) Applied</th>
<th>Summary of Changes</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>N/A</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>
