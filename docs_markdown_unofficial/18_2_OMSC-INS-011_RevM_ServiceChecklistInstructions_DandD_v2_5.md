Open Mission Systems (OMS)

Definition And Documentation (D&D)

OMS Service Checklist Instructions

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary open architecture for
integrating subsystems and services into mission packages.

The Service Checklist is an Excel workbook used to assist the Service
provider in creating the compliance documentation for an OMS Service.
The Checklist uses the Service Contract for the Service.

This OMS Service Checklist supports the compliance process per the OMS
Standard Version 2.5, OMSC-STD-001, Revision M, dated 22 January 2026.

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

[1 Service Checklist 1](#service-checklist)

[1.1 Usage Notes 1](#usage-notes)

[1.2 Contents 1](#contents)

[1.2.1 “WARNING NOTE” Tab 1](#warning-note-tab)

[1.2.2 “Cover” Tab 1](#cover-tab)

[1.2.3 “Abstract” Tab 1](#abstract-tab)

[1.2.4 “Rev” Tab 1](#rev-tab)

[1.2.5 “Tier Compliance” Tab 2](#tier-compliance-tab)

[1.2.6 “Service RQMT Checklist” Tab 2](#service-rqmt-checklist-tab)

[1.2.7 “Service Contract” Tab 2](#service-contract-tab)

[1.2.8 “OMS Msgs” Tab 3](#oms-msgs-tab)

[1.2.9 “Non-OMS Msgs” Tab 6](#non-oms-msgs-tab)

[1.2.10 “OMS Data Transfer” Tab 7](#oms-data-transfer-tab)

[1.2.11 “Non-OMS Data Transfer” Tab 8](#non-oms-data-transfer-tab)

[1.2.12 “OMS Special Signals” Tab 9](#oms-special-signals-tab)

[1.2.13 “Non-OMS Special Signals” Tab 9](#non-oms-special-signals-tab)

[1.2.13.1 Section A. Non-OMS Special Signals Allowed in the OMS Standard
10](#section-a.-non-oms-special-signals-allowed-in-the-oms-standard)

[1.2.13.2 Section B. Non-OMS Special Signals Superseded by OMS Messages
10](#section-b.-non-oms-special-signals-superseded-by-oms-messages)

[1.2.13.3 Section C. Other Non-OMS Special Signals
10](#section-c.-other-non-oms-special-signals)

[1.2.14 “Data Transfer Tables” and “Special Signals Tables” Tabs
11](#data-transfer-tables-and-special-signals-tables-tabs)

[2 References 12](#references)

This page is intentionally left blank.

List of Figures

[Figure 1.2-1 Mapping of Categories of OMS & Non-OMS Messages to
Checklist Tabs 4](#_Toc219357994)

This page is intentionally left blank.

List of Tables

[Table 2.0-1 OMS D&D Documents 12](#_Toc219357995)

This page is intentionally left blank.

Service Checklist
=================

Usage Notes
-----------

The OMS Service Checklist is an Excel workbook with the filename
18\_1\_OMSC-CHK-005\_RevM\_ServiceChecklist\_DandD\_v2\_5.xlsx.

The Checklist is used by the Service provider to generate the required
compliance documentation for an OMS Service. The Checklist uses the
Service Contract, which may include separate documents referenced in the
Security Addendum. Before attempting to fill out the checklist, the
Service compliance assessor should have access to the referenced Service
Contract for the Service.

In the Checklist, all green text must be replaced with the specific
information for the Service being documented and the workbook should be
saved using an appropriate filename.

User input is required on the ‘Green’ tabs called Cover, Abstract and
Rev, which all have green text that must be removed and replaced with
the information for the Service.

User input is required on the ‘Blue’ tabs highlighted by the blue shaded
cells, which are user editable. Some green text provided as examples in
these blue tabs should be left alone as they do not interfere with tier
compliance calculations.

Once all the data has been populated in the green and blue tabs, the
‘Orange’ tab called Tier Compliance will reflect the calculated tier
compliance.

Contents
--------

The OMS Service Checklist (workbook) includes the following tabs:

### “WARNING NOTE” Tab

This tab contains a warning notice and other notes for the user. There
are no user entries required on this tab.

### “Cover” Tab

This tab contains the template for the cover page of the completed
Service Checklist.

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
locked and contain formulas that cross-reference the Service RQMT
Checklist and perform an automated calculation of the Tier Compliance.
There are no user entries required on this tab.

### “Service RQMT Checklist” Tab

This tab lists each Requirement (RQMT) allocated to an OMS Service in
the OMS Standard, OMSC-STD-001. The tab includes columns listing the
subordinate requirements (if applicable), the Verification Requirements
(VRs) and Acceptance Criteria (ACs) for each RQMT along with the Tier at
which each VR is allocated. The tab includes formulas which determine if
the RQMT has been met based on the user input for each AC. The user
inputs for this tab are shaded (columns P & Q); the user selects True,
False or N/A (Not Applicable) for each AC. An indication of N/A requires
the user to input the rationale.

There are certain constructs in the ACs that follow an if-then pattern,
ending with “this VR is satisfied”. For these ACs, if the condition
stated is satisfied, mark the “AC Met?” column value as “TRUE” and mark
remaining ACs for that VR as “N/A”. If the condition is not satisfied,
mark the “AC Met?” column as “N/A,” and evaluate each subsequent AC for
the VR to determine and mark the appropriate response (“TRUE”, “FALSE”,
or “N/A”).

### “Service Contract” Tab

This tab is comprised of the outline for a Service Contract per the
Service Contract Template, OMSC-TMP-003. Each item of the template is
listed and the “Compliance” column indicates if the item is Required or
Optional. The user inputs for this tab are shaded (columns C & D); the
user selects True, False or N/A (Not Applicable) for each template item;
indicating that the template item is included in the Service Contract
for the OMS Service being documented. An indication of TRUE requires
that the heading and content is correct. An indication of N/A requires
the user to input the rationale. The template heading is required in
order to maintain the format and numbering of the template and the
content of the section may indicate that the section is reserved or not
applicable.

If a section, table caption, or figure caption is the following in the
Service Contract:

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

-   Deleted from or does not exist in the Service Contract:

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

To assess Section 3.4, Specific Functions, and its subsections in the
Service Contract, it is recommended to evaluate that section against the
following items in the Service Contract tab:

-   Section 3.4.x \[FunctionName\]

-   Section 3.4.x.1 \[FunctionName\] Description

-   Section 3.4.x.2 \[FunctionName\] Preconditions

-   Section 3.4.x.3 \[FunctionName\] Reporting Interval

-   Section 3.4.x.4 \[FunctionName\] Inputs and Outputs

-   Table 3.4-x \[FunctionName\] Inputs and Outputs

-   Section 3.4.x.5 \[FunctionName\] Workflow and Orchestration

-   Section 3.4.x.6 \[FunctionName\] Post Conditions

-   Section 3.4.x.7 \[FunctionName\] Error Handling.

If there are multiple specific functions, repeat the evaluation for each
specific function against the items listed above. For each item in this
section, compliance is met only if all of the corresponding specific
function items in the Service Contract satisfies compliance. If one item
in any specific function section fails to meet compliance, that item
will be assessed as FALSE.

### “OMS Msgs” Tab

In order to achieve some minimum interoperability between Subsystems and
Services of a particular tier, a Minimum Message Set (MMS) for the tiers
has been identified. Programs may have requirements to modify messages
in an MMS; therefore, modifications or extensions are permitted, but may
impact OMS compliance at an intended tier level. At Tier 3, all OMS
Messages used in an OMS Message Set must have been approved by the Open
Architecture Collaborative Working Group (OACWG) as defined in the OACWG
Governance Plan (i.e., they are Approved OMS Messages).

An Approved OMS Message is an unchanged message from the referenced UCI
Schema. An Approved OMS Message can also be a new message or
modification of an existing message that has been approved at the formal
OACWG change process. An Unapproved OMS Message is a new or changed
message from the referenced UCI Schema that has not been approved at the
formal OACWG change process. Figure 1.2-1, Mapping of Categories of OMS
& Non-OMS Messages to Checklist Tabs, provides an illustration showing
all OMS Messages goes through a CAL and how to determine if an OMS
Message is approved or unapproved. All Approved and Unapproved OMS
Messages should be documented in the “OMS Msgs” tab as illustrated in
the figure. Non-OMS Messages are documented in the “Non-OMS Msgs” tab,
which is discussed in the next section.

<img src="media/image2.png" style="width:6.5in;height:2.76944in" alt="Diagram AI-generated content may be incorrect." />

<span id="_Toc219357994" class="anchor"></span>Figure 1.2-1 Mapping of
Categories of OMS & Non-OMS Messages to Checklist Tabs

Special instructions for adding new OMS Messages to the “OMS Msgs” tab
(skip if not applicable to your Service):

-   Inserting new rows into the “OMS Msgs” tab at the bottom of the list
    of initially provided OMS Messages for the indicated UCI Schema
    version (see cell A4) is allowed. Follow these instructions
    carefully to ensure a new row and its cells are inserted properly
    for correct compliance assessment calculations:

<!-- -->

-   To insert rows at the end of the table, this sheet must be unlocked
    using the password “oms”. Once the sheet is unprotected, use CAUTION
    to avoid modifying/deleting equations:

<!-- -->

-   Select the entire last row just (&lt;AdditionalMessage&gt;) in the
    table by selecting the row number at the far left; then right click
    and select Insert. Repeat using right click and select Insert or use
    F4 (shortcut to perform the last action) to insert as many rows as
    needed

-   Select the entire &lt;AdditionalMessage&gt;) row at the bottom of
    the table (by clicking the number at the left) and copy (CTRL C).

-   Paste the copied row into the blank row(s) that was recently added;
    again by selecting the entire row and pasting (CTRL V); repeat as
    required.

-   Replace &lt;AdditionalMessage&gt; in column A with the name of the
    new OMS Message.

<!-- -->

-   Once completed, it is recommended to lock the sheet with the same
    “oms” password to avoid modifying/deleting equations.

IMPORTANT: The user completes the tab cell entries as follows for each
OMS Message documented in the Service Contract. NOTE: Any empty blue
shaded cells may affect compliance assessment calculations. For each
message:

-   In column F, “Used”, use pull-down list to indicate if the message
    is used:

<!-- -->

-   Select “Yes” if the message is used

-   Select “YES WITH MODIFICATION” if the message is used but being
    modified or the message name was being modified. The modification
    should be documented in the Service Contract

-   Select “No” if the message is applicable, but is NOT used.

-   Select “N/A” if the message is not applicable:

<!-- -->

-   Note: For each message marked “N/A” in column F, the user must enter
    the rationale in column G “Rationale for N/A”; otherwise, compliance
    assessment may be affected

<!-- -->

-   In column G, “Rationale for N/A,” enter rationale for why the
    message was marked as “N/A” in Column F. Rationale can be “Not
    applicable capability” or “Not supported.” If N/A was entered in
    column F, rationale must be provided or compliance assessment will
    be affected

-   In column P, “Service Contract Section,” enter the section number
    (multiple sections can be listed) of the Service Contract where the
    message is documented, e.g., SC §3.3.1.2

-   In columns Q and R, use pull-down list to indicate whether the
    message is an Input, or an Output, or both, by placing an “X” in the
    appropriate column(s)

-   In column S, enter the location (multiple locations can be listed)
    of the functional test results (typically a document number)
    indicating that the message has been tested and has successfully
    passed through a CAL between the Service and a test harness.

-   In column U, enter the OACWG-approved OMS Change Request Identifier
    (e.g., OAM-XXXX) for this new or modified message to indicate an
    Approved OMS Message that has passed OACWG

-   In column V, enter any additional notes pertaining to the message as
    needed.

EXAMPLES: A Service provider can either initiate a message modification
or may be requested to support a message modified by another
Architecture Element provider. A modification or extension that extends
messages in either of the MMSs may temporarily cause an Architecture
Element using these messages not be OMS compliant at the intended Tier
for the specific OMS release version until the change is approved by the
OACWG. Note that asserting or proving compliance will change as a
program evolves from a proposal/acquisition phase (e.g., initial
compliance assessments) to a program after final testing (e.g., final
compliance assessments).

Here are examples of how modifying MMS messages may affect tier
compliance of an Architecture Element:

-   Tier 1 Example: A Service modifies the **ServiceStatus** Tier 1 MMS
    message

Modification to an OMS Tier 1 MMS or a Tier 1 Required Subsystem Message
Set makes the Service not compliant at OMS Tier 1 until the modification
is approved by the OACWG

-   Tier 2 Example: A Service modifies the **MissionPlan** Tier 2 MMS
    message

Modification to an OMS Tier 2 MMS makes the Service not compliant at OMS
Tier 2 until the modification is approved by the OACWG. If all other
Tier 1 compliance requirements are met, Tier 1 compliance could be
achieved

-   Tier 3 Example: A Service modifies the **WeatherObservation**
    message

Modification to any OMS message not in any Tier 1 or Tier 2 Minimum
Message Set makes the Service not compliant at OMS Tier 3 until the
modification is approved by the OACWG. If all other Tier 2 compliance
requirements are met, Tier 2 compliance could be achieved.

### “Non-OMS Msgs” Tab

Non-OMS Messages are messages that are passed without the use of a CAL,
as shown in the bottom right-hand side of Figure 1.2-1, Mapping of
Categories of OMS & Non-OMS Messages to Checklist Tabs, shown in Section
1.2.8 “OMS Msgs” Tab. Non-OMS Messages are not compliant at any tier.

For this tab, the user completes the shaded columns for any Non-OMS
Messages used by the Service. If no Non-OMS Messages are used by the
Service then all the shaded fields should be left at their default
value; and the message compliance will be shown as TRUE. If a Non-OMS
Message is entered, then a rationale for using the Non-OMS Message must
be entered. If a Non-OMS Message is used, then the Service is not OMS
compliant at any tier. Consider using a Data Transfer until the Non-OMS
Message can be added to a future baseline UCI Schema using an UCI Change
Request, so it will go through a CAL.

### “OMS Data Transfer” Tab

OMS Data Transfer is a Data Transfer which is one of the four top-level
information exchange types described by OMS. OMS Data Transfer deals
with file and product exchanges that are restricted to the defined data
types and their allowed data formats, transfer protocols/APIs, and
sharing patterns described by the OMS Standard. An OMS Data Transfer
must adhere to the following restrictions: 1) does not overlap with OMS
Messages, 2) does not overlap with any other OMS Data Exchanges, and 3)
does not transfer external standards second hand.

A row of the table in this tab is completed for each OMS Data Transfer
documented in the Service Contract.

For this tab, the user completes a row for each OMS Data Transfer used
by the Service by filling in each shaded cell. Shaded cells left blank
may affect compliance assessment. Guidance for filling out the shaded
cells by column follows:

-   Column A: Enter the name of the OMS Data Transfer

-   Columns B-G: Note that the selected entries in these cells across
    each row must match allowed values per the “Data Transfer Formats,
    APIs, and Protocols” and “OMS URI Formats” tables in the OMS
    Standard

<!-- -->

-   Column B: Select the Data Type from the pull-down list that matches
    the allowed options in the first column of the “Data Transfer
    Formats, APIs, and Protocols” table in the OMS Standard

<!-- -->

-   If the Data Type does not exist in the Column B pull-down list, then
    this is a Non-OMS Data Transfer; use the \[\[Non-OMS Data
    Transfer\]\] tab instead to provide the Non-OMS Data Transfer
    detailed information

<!-- -->

-   Columns C-F: Select the remaining data from the pull-down lists that
    correspond to the selected Data Type in Column B for the OMS Data
    Transfer

<!-- -->

-   If any of the pull-down lists do not contain the desired values,
    then this is a Non-OMS Data Transfer; use the \[\[Non-OMS Data
    Transfer\]\] tab instead to provide the Non-OMS Data Transfer
    detailed information

-   Columns C-E: Select data in only one column, set the others to “Does
    Not Use” from the pull-down list

<!-- -->

-   Column G: Select the UFI format from the pull-down list that matches
    the allowed options in the “OMS URI Formats” table in the OMS
    Standard

<!-- -->

-   If the pull-down lists do not contain the desired value, then this
    is a Non-OMS Data Transfer; use the \[\[Non-OMS Data Transfer\]\]
    instead tab to provide the Non-OMS Data Transfer detailed
    information

<!-- -->

-   Columns H-J: Use pull-down list to the three answer restriction
    questions as TRUE or FALSE. The default value is set to TRUE.
    Selecting a FALSE value will result in OMS non-compliance at any
    tier

-   Columns K-M: These columns show individual compliance assessed per
    Data Transfer row and tier using auto-calculations (based on
    selections in Columns B-J), which are summarized at the top of the
    tab for each tier, and then these tier summaries are used to assess
    overall OMS Tier compliance

<!-- -->

-   If a TRUE does not appear in any of Columns K-M, then this is a
    Non-OMS Data Transfer; use the \[\[Non-OMS Data Transfer\]\] tab
    instead to provide the Non-OMS Data Transfer detailed information.

Do not enter any Non-OMS Data Transfers on this tab. Instead, enter
Non-OMS Data Transfer details in the \[\[Non-OMS Data Transfer\]\] tab.

### “Non-OMS Data Transfer” Tab

Non-OMS Data Transfer deals with file and product exchanges that fall
outside the Data Transfer defined data types and their allowed data
formats, transfer protocols/APIs, and sharing patterns described by the
OMS Standard. Non-OMS Data Transfers are typically restricted to OMS
compliance Tier 1. However, when an OACWG-approved Change Request is
identified, then the Non-OMS Data Transfer will be assessed at the
maximum allowed Tier specified by the OACWG.

A row of the table in this tab is completed for each Non-OMS Data
Transfer documented in the Service Contract.

For this tab, the user completes a row for each Non-OMS Data Transfer
used by the Service by filling in each shaded cell. Shaded cells left
blank may affect compliance assessment. Guidance for filling out the
shaded cells by column follows:

-   Column A: Enter the name of the Non-OMS Data Transfer

-   Columns B-F: These five columns in this tab match the columns of the
    “Non-OMS Data Transfers” table in the OMS Standard, which are
    similar to the “Data Transfer Formats, APIs, and Protocols” table in
    the OMS Standard

<!-- -->

-   Column B: 1) Select the Data Type from the pull-down list that
    matches the allowed options in the first column of the “Data
    Transfer Formats, APIs, and Protocols” table in the OMS Standard
    or 2) select “Other (See Description)” choice from the pull-down
    list for a new data type

-   Column C-F: 1) Select the remaining data from the pull-down lists
    that correspond to the selected Data Type in Column B for the OMS
    Data Transfer from the pull-down list that matches the allowed
    options in the first column of the “Data Transfer Formats, APIs, and
    Protocols” table in the OMS Standard, or 2) select “Other (See
    Description)” choice from the pull-down list for a new data
    corresponding to the new data type

-   Columns C-E: Select data in only one column, set the others to “Does
    Not Use” from the pull-down list

<!-- -->

-   Column G: 1) Select the UFI format from the pull-down list that
    matches the allowed options in the “OMS URI Formats” table in the
    OMS Standard, or 2) select “Other (See Description)” choice from the
    pull-down list for a new URI format

-   Columns H: Enter description of this Non-OMS Data Transfer

-   Column I: Enter rationale for using this Non-OMS Data Transfer

-   Column J: Enter an OMS Change Request Identifier (e.g., OAM-XXXX)
    for the Change Request that passed OACWG (required at Tier 3). If an
    OMS Change Request Identifier does not exist, in progress, or has
    not passed OACWG, Enter “N/A” (restricted to Tier 1)

-   Column K: Select the max tier allowed per OACWG-approved Change
    Request for this Non-OMS Data Transfer. If an OMS Change Request
    does not exist, in progress, or has not passed OACWG, select “N/A”
    (restricted to Tier 1)

-   Columns L-N: These columns show individual compliance assessed per
    Data Transfer row and tier using auto-calculations (based on
    selections in Columns B-K), which are summarized at the top of the
    tab for each tier, and then these tier summaries are used to assess
    overall OMS Tier compliance.

Do not enter any OMS Data Transfers on this tab. Instead, enter OMS Data
Transfer details in the \[\[OMS Data Transfer\]\] tab.

### “OMS Special Signals” Tab

For this tab, the user completes the shaded columns for each OMS Special
Signal used by the Service. The tables in this tab are drawn from the
tables of the same name in the OMS Standard. The user simply completes a
row for each OMS Special Signal used by the service by selecting the
appropriate Special Signal from the drop down list in the appropriate
table.

If a non-OMS special signal is entered, then the details must be entered
in the “Non-OMS Special Signals” tab.

### “Non-OMS Special Signals” Tab

The \[\[Non-OMS Special Signals\]\] tab has three sections.

The top section (Section A), when completed by the user, identifies the
non-OMS special signals listed in the “Non-OMS Special Signals Allowed
in the OMS Standard” table. However, the use of these signals are
allowed but OMS compliance will be restricted to a maximum of Tier 2.

The middle section (Section B), when completed by the user, identifies
the other non-OMS special signals listed in the “Special Signals
Superseded by OMS Messages” table in the Standard However, the use of
these signals is allowed, but OMS compliance will be restricted to a
maximum of Tier 2.

The bottom section (Section C), when completed by the user, identifies
any other non-OMS special signals used by the Service that are not
included in Section A or B. If a non-OMS special signal is used, fill in
the blue cells. Note that compliance assessment will be restricted until
an OACWG-approved Change Request identifier is provided.

#### Section A. Non-OMS Special Signals Allowed in the OMS Standard

If the Service Contract documents that the Service uses a non-OMS
special signal that is listed in the “Non-OMS Special Signals Allowed in
the OMS Standard” table, the user will identify that special signal in
Section A (top section) of the \[\[Non-OMS Special Signals\]\] tab by
entering the following information:

-   From the pull-down list, select the name of the special signal in
    column A “Non-OMS Special Signal Allowed in the OMS Standard”

-   Once a column A selection is made, a result in column B “Tier 3
    Non-OMS Special Signals Compliant” will show FALSE.

#### Section B. Non-OMS Special Signals Superseded by OMS Messages 

If the Service Contract documents that the Service uses other non-OMS
special signals that are not listed in the “Non-OMS Special Signals
Superseded by OMS Messages” table, the user will identify those non-OMS
special signals in Section B (middle section) of the \[\[Non-OMS Special
Signals\]\] tab. The user documents each non-OMS special signal in
Section B by entering the following information:

-   Select the non-OMS special signal from the pull-down list in column
    A “Non-OMS Special Signal Superseded by OMS Message”

-   Enter the name of the non-OMS special signal in column B “Name of
    Non-OMS Special Signal”

-   Document the rationale for using the non-OMS special signal in
    column C “Rationale”

-   Once a column A selection is made, a result in column D “Tier 3
    Non-OMS Special Signals Compliant” will show FALSE.

#### Section C. Other Non-OMS Special Signals

If the Service Contract documents that the Service uses other non-OMS
special signals that are not listed in the “Non-OMS Special Signals
Superseded by OMS Messages” table, the user will identify those special
signals in Section C (bottom section) of the \[\[Non-OMS Special
Signals\]\] tab. The user documents each non-OMS special signal in
Section C by entering the following information:

-   Enter the name of the non-OMS special signal in column A “Other
    Non-OMS Special Signal”

-   Document the rationale for using the non-OMS special signal in
    column B “Rationale”

-   Enter the name of the OACWG-approved Change Request identifier that
    proposes the addition of the non-OMS special signal to the OMS
    Standard in column C “OACWG-approved Change Request Identifier”

-   Once a column A selection is made, a result in column D “Tier 3
    Non-OMS Special Signals Compliant” will initially show FALSE until
    columns B and C are also completed.

### “Data Transfer Tables” and “Special Signals Tables” Tabs

These tabs contain the information from the Data Transfer Tables and
Special Signals tables in the OMS Standard; these tables feed the
logical tests in the “OMS Data Transfer” and “OMS Special Signals” tabs.
There are no user entries required on these tabs.

References
==========

The documents listed in Table 2.0-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219357995" class="anchor"></span>Table 2.0-1 OMS D&D
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
<td>OMSC-INS-011</td>
<td>OMS Service Checklist Instructions</td>
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
<td>OMSC-TMP-003</td>
<td>Service Contract Template</td>
<td>M</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>
