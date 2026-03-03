Open Mission Systems (OMS)

Definition And Documentation (D&D)

OMS Mission Package Checklist Instructions

<img src="images/15_2_OMSC-INS-008_RevM_MissionPackageChecklistInstructions_DandD_v2_5.docx/media/image1.jpeg" style="width:2.77778in;height:1.73611in" />

22 january 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary open architecture for
integrating subsystems and services into mission packages.

The Mission Package Checklist is an Excel workbook used to assist the
Mission Package integrator to create the compliance documentation for an
OMS Mission Package. The Checklist uses the Mission Package Worksheet
(MPW) and Mission Package Description Document (MPDD) for the Mission
Package.

This OMS Mission Package Checklist supports the compliance process per
the OMS Standard Version 2.5, OMSC-STD-001, Revision M, dated 22 January
2026.

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

[1 Mission Package Checklist 1](#mission-package-checklist)

[1.1 Usage Notes 1](#usage-notes)

[1.2 Contents 1](#contents)

[1.2.1 “WARNING NOTE” Tab 1](#warning-note-tab)

[1.2.2 “Cover” Tab 1](#cover-tab)

[1.2.3 “Abstract” Tab 1](#abstract-tab)

[1.2.4 “Rev” Tab 1](#rev-tab)

[1.2.5 “Tier Compliance” Tab 2](#tier-compliance-tab)

[1.2.6 “Mission Package RQMT Checklist” Tab
2](#mission-package-rqmt-checklist-tab)

[1.2.7 “MPDD” Tab 3](#mpdd-tab)

[2 References 4](#references)

This page is intentionally left blank.

List of Tables

[Table 2.0-1 OMS D&D Documents 4](#_Toc219296848)

This page is intentionally left blank.

Mission Package Checklist
=========================

Usage Notes
-----------

The OMS Mission Package Checklist is an Excel workbook with a file name
of
15\_1\_OMSC-CHK-002\_RevM\_MissionPackageChecklist\_DandD\_v2\_5.xlsx.

The Checklist is used by the Mission Package integrator to generate the
required compliance documentation for an OMS Mission Package. The
Checklist uses the Mission Package Worksheet (MPW) and Mission Package
Description Document (MPDD), which may include separate documents
referenced in the Security Addendum. Before attempting to fill out the
checklist, the Mission Package compliance assessor should have access to
the referenced MPW and MPDD documents for the Mission Package, as well
as the individual checklists for its Platform, Subsystems, Services, and
Isolators in the Mission Package.

In the Checklist, all green text must be replaced with the specific
information for the Mission Package being documented and the workbook
should be saved using an appropriate filename.

User input is required on the ‘Green’ tabs called Cover, Abstract and
Rev, which all have green text that must be removed and replaced with
the information for the Mission Package.

User input is required on the ‘Blue’ tabs highlighted by the blue shaded
cells, which are user editable. Some green text provided as examples in
these blue tabs should be left alone as they do not interfere with tier
compliance calculations.

Once all the data has been populated in the green and blue tabs, the
‘Orange’ tab called Tier Compliance will reflect the calculated tier
compliance.

Contents
--------

The OMS Mission Package Checklist (workbook) includes the following
tabs:

### “WARNING NOTE” Tab

This tab contains a warning notice and other notes for the user. There
are no user entries required on this tab.

### “Cover” Tab

This tab contains the template for the cover page of the completed
Mission Package Checklist.

### “Abstract” Tab

This tab contains a template for the Abstract page. The abstract is
required and is a brief summary of the document that follows and is used
to help the reader quickly ascertain the document’s purpose and overall
content.

### “Rev” Tab

This tab contains the template for the Revision Record for the document
being generated.

### “Tier Compliance” Tab

This tab contains the Tier Compliance Summary. The cells of this tab are
locked and contain formulas that cross-reference the Mission Package
RQMT Checklist and perform an automated calculation of the Tier
Compliance. There are no user entries required on this tab.

### “Mission Package RQMT Checklist” Tab

This tab lists each Requirement (RQMT) allocated to an OMS Mission
Package in the OMS Standard, OMSC-STD-001. The tab includes columns
listing the subordinate requirements (if applicable), the Verification
Requirements (VRs) and Acceptance Criteria (ACs) for each RQMT along
with the Tier at which each VR is allocated. The tab includes formulas
which determine if the RQMT has been met based on the user input for
each AC. The user inputs for this tab are shaded (columns P & Q); the
user selects True, False or N/A (Not Applicable) for each AC. An
indication of N/A requires the user to input the rationale.

There are certain constructs in the ACs that follow an if-then pattern,
ending with “this VR is satisfied”. For these ACs, if the condition
stated is satisfied, mark the “AC Met?” column value as “TRUE” and mark
remaining ACs for that VR as “N/A”. If the condition is not satisfied,
mark the “AC Met?” column as “N/A,” and evaluate each subsequent AC for
the VR to determine and mark the appropriate response (“TRUE”, “FALSE”,
or “N/A”).

### “MPDD” Tab

This tab is comprised of the outline for a Mission Package Description
Document (MPDD) per the MPDD Template, OMSC-TMP-007. Each item of the
template is listed and the “Compliance” column indicates if the item is
Required or Optional. The user inputs for this tab are shaded (columns C
& D); the user selects True, False or N/A (Not Applicable) for each
template item indicating that the template item is included in the PDD
for the Platform being documented. An indication of TRUE requires that
the heading and content is correct. An indication of N/A requires the
user to input the rationale. The template heading is required in order
to maintain the format and numbering of the template and the content of
the section may indicate that the section is reserved or not applicable.

If a section, table caption, or figure caption is the following in the
MPDD:

-   Exist:

<!-- -->

-   Select “TRUE” in the “Per Template?” column (column C).

<!-- -->

-   Marked as “Not Applicable”, “N/A”, or “Figure is not applicable”:

<!-- -->

-   Select “N/A” in the “Per Template?” column (column C) and enter a
    rationale why the section, table caption, or figure/figure caption
    is not applicable in the “N/A Rationale” column (column D).

<!-- -->

-   Deleted from or does not exist in the MPDD:

<!-- -->

-   Select “FALSE” in the “Per Template?” column (column C).

If the distribution statement in the evaluating document is of the
following:

-   Distribution Statement A or more restrictive:

<!-- -->

-   In row 8 and 9, select “TRUE” in the “Per Template?” column (column
    C).

<!-- -->

-   Distribution Statement less restrictive than A:

<!-- -->

-   In row 8 and 9, select “FALSE” in the “Per Template?” column (Column
    C). The OMS D&D Documents are required to be at least Distribution
    Statement A; it is not allowed for the evaluating document
    distribution statement to be less restrictive than Distribution
    Statement A.

References
==========

The documents listed in Table 2.0-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219296848" class="anchor"></span>Table 2.0-1 OMS D&D
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
<td>OMSC-INS-008</td>
<td>OMS Mission Package Checklist Instructions</td>
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
<tr class="odd">
<td>OMSC-TMP-007</td>
<td>Mission Package Description Document (MPDD) Template</td>
<td>I</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>
