Open Mission Systems (OMS)

Definition And Documentation (D&D)

C++ Critical Abstraction Layer (CAL) Interface Generation Specification

<img src="images/06_OMSC-SPC-008_RevK_CxxCALSpec_DandD_v2_5.docx/media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary, open architecture
standard for integrating subsystems and services into mission packages.

This is the top-level OMS Schema to C++ translation specification for
the OMS Standard.

C++ CAL Implementation requirements will adhere to the general CAL
requirements listed in the CAL specification unless otherwise stated.
Items listed here will either refine or clarify requirements as they
apply to the C++ CAL Implementation. This specification was originally
developed to be conformant with the C++98 Standard (ISO/IEC 14882:1998)
and has been modified to allow for the flexibility needed to be
compatible with newer versions of C++, up to and including C++17
(ISO/IEC 14882:2017).

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
<td>K</td>
<td>22 January 2026</td>
<td>Initial public release</td>
</tr>
</tbody>
</table>

This page is intentionally left blank.

Table of Contents

[1 Introduction 1](#introduction)

[1.1 Interface Specification Goals 1](#interface-specification-goals)

[1.2 References 3](#references)

[1.2.1 OMS D&D Documents 3](#oms-dd-documents)

[1.2.2 Other Documents 3](#other-documents)

[2 The XML Schema 4](#the-xml-schema)

[2.1 Schema Components 4](#schema-components)

[2.2 Namespaces 4](#namespaces)

[2.3 Prefixes 5](#prefixes)

[2.4 Primitive Data Types 5](#primitive-data-types)

[2.5 Names 7](#names)

[2.6 XSD References 8](#xsd-references)

[2.7 XSD Data Types 8](#xsd-data-types)

[2.8 The Schema Declaration 9](#the-schema-declaration)

[2.9 The Schema Components 10](#the-schema-components)

[2.9.1 Schema Component 10](#schema-component)

[2.9.1.1 Global Simple Types 10](#global-simple-types)

[2.9.1.2 Global Complex Types 11](#global-complex-types)

[2.9.1.3 Global Elements 11](#global-elements)

[2.9.2 Components 11](#components)

[2.9.2.1 Simple Restriction Component 11](#simple-restriction-component)

[2.9.2.2 Local Simple Type Component 12](#local-simple-type-component)

[2.9.2.3 Simple Content Component 12](#simple-content-component)

[2.9.2.4 Complex Content Component 12](#complex-content-component)

[2.9.3 Data Type Declarations 12](#data-type-declarations)

[2.9.3.1 Choice 12](#choice)

[2.9.3.2 Sequence 12](#sequence)

[2.9.4 Content Restriction and Extension Components
13](#content-restriction-and-extension-components)

[2.9.4.1 Simple Content Restriction Component
13](#simple-content-restriction-component)

[2.9.4.2 Simple Content Extension Component
13](#simple-content-extension-component)

[2.9.4.3 Complex Content Restriction Component
13](#complex-content-restriction-component)

[2.9.4.4 Complex Content Extension Component
14](#complex-content-extension-component)

[2.9.5 Local Element 14](#local-element)

[2.9.6 Local Complex Type Component 14](#local-complex-type-component)

[2.10 Variants 14](#variants)

[2.10.1 Singular Schema Components 14](#singular-schema-components)

[2.10.2 Collection Schema Components 15](#collection-schema-components)

[2.10.3 Optional Schema Components 15](#optional-schema-components)

[3 The C++ OMS Schema Compiler Conceptual Architecture
16](#the-c-oms-schema-compiler-conceptual-architecture)

[4 Namespaces 18](#namespaces-1)

[5 Names and Qualified Names 20](#names-and-qualified-names)

[6 Directory Structure 23](#directory-structure)

[6.1 Subdirectories 23](#subdirectories)

[6.1.1 type 23](#type)

[6.2 UCI Include Directory 23](#uci-include-directory)

[7 Accessor Construction and Destruction
24](#accessor-construction-and-destruction)

[8 Documentation and Annotations 25](#documentation-and-annotations)

[9 The Primitive and Basic Data Types
26](#the-primitive-and-basic-data-types)

[9.1 The Primitive Types 26](#the-primitive-types)

[9.1.1 The Simple Primitive Data Types
26](#the-simple-primitive-data-types)

[9.1.2 The String Primitive Data Types
28](#the-string-primitive-data-types)

[9.1.3 The Numeric String Primitive Data Types
28](#the-numeric-string-primitive-data-types)

[9.1.4 The Binary Primitive Data Types
28](#the-binary-primitive-data-types)

[9.1.5 The List Primitive Data Types 29](#the-list-primitive-data-types)

[9.2 The UCIException Class 29](#the-uciexception-class)

[9.2.1 UCIException Class Methods and Operators
30](#uciexception-class-methods-and-operators)

[9.2.1.1 Constructor(const std::string& reason)
30](#constructorconst-stdstring-reason)

[9.2.1.2 Constructor(const char\*) 31](#constructorconst-char)

[9.2.1.3 Constructor(const std::ostringstream&)
32](#constructorconst-stdostringstream)

[9.2.1.4 Method: getErrorCode 33](#method-geterrorcode)

[9.2.1.5 Macro: throwUciException 33](#macro-throwuciexception)

[9.3 The Accessor Type Constants 34](#the-accessor-type-constants)

[9.4 The Accessor Class 36](#the-accessor-class)

[9.4.1 The Accessor AccessorType 36](#the-accessor-accessortype)

[9.4.2 The Accessor Class 37](#the-accessor-class-1)

[9.4.2.1 The Accessor Class Methods and Operators
37](#the-accessor-class-methods-and-operators)

[9.4.2.1.1 Destructor: ~Accessor 37](#destructor-accessor)

[9.4.2.1.2 Method: getAccessorType 38](#method-getaccessortype)

[9.4.2.1.3 Method: reset 39](#method-reset)

[9.4.2.1.4 Default Constructor: 40](#default-constructor)

[9.4.2.1.5 Default Copy Constructor: 41](#default-copy-constructor)

[9.4.2.1.6 Operator: operator= 42](#operator-operator)

[9.5 The StringAccessor Class 42](#the-stringaccessor-class)

[9.5.1 The StringAccessor Class Methods and Operators
43](#the-stringaccessor-class-methods-and-operators)

[9.5.1.1 Destructor: ~StringAccessor 43](#destructor-stringaccessor)

[9.5.1.2 Method: str 43](#method-str)

[9.5.1.3 Method: c\_str 44](#method-c_str)

[9.5.1.4 Method: setStringValue 45](#method-setstringvalue)

[9.5.1.4.1 Overload for String 45](#overload-for-string)

[9.5.1.4.2 Overload for C-String 46](#overload-for-c-string)

[9.5.1.5 Operator: operator= 47](#operator-operator-1)

[9.5.1.5.1 Overload for StringAccessor 47](#overload-for-stringaccessor)

[9.5.1.5.2 Overload for String 48](#overload-for-string-1)

[9.5.1.5.3 Overload for C-String 49](#overload-for-c-string-1)

[9.5.1.6 Operator: operator &lt;qualifiedCxxPrimitiveName&gt;
49](#operator-operator-qualifiedcxxprimitivename)

[9.5.1.7 Default Constructor: 50](#default-constructor-1)

[9.5.1.8 Default Copy Constructor: 51](#default-copy-constructor-1)

[9.6 The SimpleList Template 52](#the-simplelist-template)

[9.6.1 SimpleList Template Typedefs 52](#simplelist-template-typedefs)

[9.6.2 SimpleList Template Constants 53](#simplelist-template-constants)

[9.6.3 The SimpleList Class Methods and Operators
53](#the-simplelist-class-methods-and-operators)

[9.6.3.1 Destructor: ~SimpleList 53](#destructor-simplelist)

[9.6.3.2 Method: size 54](#method-size)

[9.6.3.3 Method: max\_size 55](#method-max_size)

[9.6.3.4 Method: min\_size 56](#method-min_size)

[9.6.3.5 Method: resize 57](#method-resize)

[9.6.3.6 Method: capacity 58](#method-capacity)

[9.6.3.7 Method: empty 59](#method-empty)

[9.6.3.8 Method: reserve 60](#method-reserve)

[9.6.3.9 Method: pop\_back 61](#method-pop_back)

[9.6.3.10 Method: clear 62](#method-clear)

[9.6.3.11 Method: getMaximumLength 63](#method-getmaximumlength)

[9.6.3.12 Method: getMinimumLength 64](#method-getminimumlength)

[9.6.3.13 Method: getLength 65](#method-getlength)

[9.6.3.14 Operator: operator\[\] 66](#operator-operator-2)

[9.6.3.14.1 Non-Const Variant 66](#non-const-variant)

[9.6.3.14.2 Const Variant 67](#const-variant)

[9.6.3.15 Method: at(size\_type index) 68](#method-atsize_type-index)

[9.6.3.16 Method: at(size\_type index) const
69](#method-atsize_type-index-const)

[9.6.3.17 Method: push\_back 70](#method-push_back)

[9.6.3.18 Default Constructor: 71](#default-constructor-2)

[9.6.3.19 Default Copy Constructor: 71](#default-copy-constructor-2)

[9.6.3.20 Operator: operator= 72](#operator-operator-3)

[9.7 The BoundedList Template 72](#the-boundedlist-template)

[9.7.1 The BoundedList Typedefs 73](#the-boundedlist-typedefs)

[9.7.2 The BoundedList Template Constants
74](#the-boundedlist-template-constants)

[9.7.3 The BoundedList Template Methods and Operators
74](#the-boundedlist-template-methods-and-operators)

[9.7.3.1 Destructor: ~BoundedList 74](#destructor-boundedlist)

[9.7.3.2 Method: size 75](#method-size-1)

[9.7.3.3 Method: max\_size 76](#method-max_size-1)

[9.7.3.4 Method: min\_size 77](#method-min_size-1)

[9.7.3.5 Method: resize 77](#method-resize-1)

[9.7.3.6 Method: capacity 79](#method-capacity-1)

[9.7.3.7 Method: empty 80](#method-empty-1)

[9.7.3.8 Method: reserve 81](#method-reserve-1)

[9.7.3.9 Method: pop\_back 82](#method-pop_back-1)

[9.7.3.10 Method: clear 83](#method-clear-1)

[9.7.3.11 Method: getMaximumOccurs 84](#method-getmaximumoccurs)

[9.7.3.12 Method: getMinimumOccurs 85](#method-getminimumoccurs)

[9.7.3.13 Operator: operator\[\] 86](#operator-operator-4)

[9.7.3.13.1 Non-Const Variant 86](#non-const-variant-1)

[9.7.3.13.2 Const Variant 87](#const-variant-1)

[9.7.3.14 Method: at 88](#method-at)

[9.7.3.14.1 Non-Const Variant 88](#non-const-variant-2)

[9.7.3.14.2 Const Variant 89](#const-variant-2)

[9.7.3.15 Method: push\_back 90](#method-push_back-1)

[9.7.3.15.1 Overload for Const Reference
90](#overload-for-const-reference)

[9.7.3.15.2 Template Overload for Value
91](#template-overload-for-value)

[9.7.3.15.3 Template Overload for Const Reference
93](#template-overload-for-const-reference)

[9.7.3.16 Default Constructor: 93](#default-constructor-3)

[9.7.3.17 Default Copy Constructor: 94](#default-copy-constructor-3)

[9.7.3.18 Operator: operator= 95](#operator-operator-5)

[9.8 The Universally Unique Identification (UUID) Class
95](#the-universally-unique-identification-uuid-class)

[9.8.1 The UUID Class 96](#the-uuid-class)

[9.8.1.1 The UUID Class Data Types 97](#the-uuid-class-data-types)

[9.8.1.2 The UUID Class Methods and Operators
99](#the-uuid-class-methods-and-operators)

[9.8.1.2.1 Method: fromString 99](#method-fromstring)

[9.8.1.2.2 Method: fromOctets 100](#method-fromoctets)

[9.8.1.2.3 Method: generateUUID 101](#method-generateuuid)

[9.8.1.2.4 Method: getNamespaceUUID 101](#method-getnamespaceuuid)

[9.8.1.2.5 Method: createVersion3UUID 102](#method-createversion3uuid)

[9.8.1.2.6 Method: getOctets 103](#method-getoctets)

[9.8.1.2.7 Method: getValueUUID 104](#method-getvalueuuid)

[9.8.1.2.8 Method: toString 104](#method-tostring)

[9.8.1.2.9 Method: getVariant 104](#method-getvariant)

[9.8.1.2.10 Method: getVersion 105](#method-getversion)

[9.8.1.2.11 Method: getClockSequence 106](#method-getclocksequence)

[9.8.1.2.12 Method: getTimestamp 107](#method-gettimestamp)

[9.8.1.2.13 Method: getNodeAddress 107](#method-getnodeaddress)

[9.8.1.2.14 Operator: operator== 108](#operator-operator-6)

[9.8.1.2.15 Operator: operator!= 108](#operator-operator-7)

[9.8.1.2.16 Operator: operator&lt; 109](#operator-operator-8)

[9.8.1.2.17 Operator: operator&lt;= 110](#operator-operator-9)

[9.8.1.2.18 Operator: operator&gt; 111](#operator-operator-10)

[9.8.1.2.19 Operator: operator&gt;= 112](#operator-operator-11)

[9.8.1.2.20 Method: isNil 113](#method-isnil)

[9.8.1.2.21 Method: isValid 113](#method-isvalid)

[9.8.1.2.22 Method: toString 114](#method-tostring-1)

[9.8.1.2.23 Constructor 115](#constructor)

[9.8.1.2.24 Default Copy Constructor 117](#default-copy-constructor-4)

[9.8.1.2.25 Operator: operator= 117](#operator-operator-12)

[9.8.1.2.26 Hash Template Specialization
118](#hash-template-specialization)

[9.9 The AbstractServiceBusConnection Class
118](#the-abstractservicebusconnection-class)

[9.9.1 The AbstractServiceBusConnection Class Data Types
118](#the-abstractservicebusconnection-class-data-types)

[9.9.2 The AbstractServiceBusConnection Class Methods and Operators
119](#the-abstractservicebusconnection-class-methods-and-operators)

[9.9.2.1 Destructor: ~AbstractServiceBusConnection
119](#destructor-abstractservicebusconnection)

[9.9.2.2 Method: shutdown 120](#method-shutdown)

[9.9.2.3 Method: getMySystemLabel 120](#method-getmysystemlabel)

[9.9.2.4 Method: getMySystemUUID 121](#method-getmysystemuuid)

[9.9.2.5 Method: getMyServiceUUID 121](#method-getmyserviceuuid)

[9.9.2.6 Method: getMySubsystemUUID 122](#method-getmysubsystemuuid)

[9.9.2.7 Method: getMyComponentUUID 123](#method-getmycomponentuuid)

[9.9.2.8 Method: getMyCapabilityUUID 124](#method-getmycapabilityuuid)

[9.9.2.9 Reserved 124](#reserved)

[9.9.2.10 Method: getOmsSchemaVersion 124](#method-getomsschemaversion)

[9.9.2.11 Method: getOmsSchemaCompilerVersion
125](#method-getomsschemacompilerversion)

[9.9.2.12 Method: getOMSApiVersion 125](#method-getomsapiversion)

[9.9.2.13 Method: getAbstractServiceBusConnectionVersion
126](#method-getabstractservicebusconnectionversion)

[9.9.2.14 Default Constructor: 127](#default-constructor-4)

[9.9.2.15 Default Copy Constructor: 128](#default-copy-constructor-5)

[9.9.2.16 Operator: operator= 129](#operator-operator-13)

[9.9.2.17 Function: uci\_getAbstractServiceBusConnection
130](#function-uci_getabstractservicebusconnection)

[9.9.2.18 Method: getStatus 131](#method-getstatus)

[9.9.2.19 Method: addStatusListener 132](#method-addstatuslistener)

[9.9.2.20 Method: removeStatusListener
133](#method-removestatuslistener)

[9.10 The Listener Class 133](#the-listener-class)

[9.10.1 The Listener Class Methods and Operators
134](#the-listener-class-methods-and-operators)

[9.10.1.1 Destructor: ~Listener 134](#destructor-listener)

[9.10.1.2 Default Constructor: 134](#default-constructor-5)

[9.10.1.3 Default Copy Constructor: 135](#default-copy-constructor-6)

[9.10.1.4 Operator: operator= 135](#operator-operator-14)

[9.11 The Reader Class 136](#the-reader-class)

[9.11.1 The Reader Class Methods and Operators
136](#the-reader-class-methods-and-operators)

[9.11.1.1 Destructor: ~Reader 136](#destructor-reader)

[9.11.1.2 Default Constructor: 137](#default-constructor-6)

[9.11.1.3 Default Copy Constructor: 137](#default-copy-constructor-7)

[9.11.1.4 Operator: operator= 138](#operator-operator-15)

[9.12 The Writer Class 138](#the-writer-class)

[9.12.1 The Writer Class Methods and Operators
139](#the-writer-class-methods-and-operators)

[9.12.1.1 Destructor: ~Writer 139](#destructor-writer)

[9.12.1.2 Default Constructor: 139](#default-constructor-7)

[9.12.1.3 Default Copy Constructor: 140](#default-copy-constructor-8)

[9.12.1.4 Operator: operator= 140](#operator-operator-16)

[9.13 The AbstractServiceBusConnectionStatusListener Class
141](#the-abstractservicebusconnectionstatuslistener-class)

[9.13.1 The AbstractServiceBusConnectionStatusListener Class Methods and
Operators
141](#the-abstractservicebusconnectionstatuslistener-class-methods-and-operators)

[9.13.1.1 Destructor: ~AbstractServiceBusConnectionStatusListener
141](#destructor-abstractservicebusconnectionstatuslistener)

[9.13.1.2 Method: statusChanged 142](#method-statuschanged)

[9.14 The Externalizer Class 142](#the-externalizer-class)

[9.14.1 The Externalizer Class Methods and Operators
143](#the-externalizer-class-methods-and-operators)

[9.14.1.1 Destructor: ~Externalizer 143](#destructor-externalizer)

[9.14.1.2 Method: read 144](#method-read)

[9.14.1.2.1 Overload for Input Stream 144](#overload-for-input-stream)

[9.14.1.2.2 Overload for String 145](#overload-for-string-2)

[9.14.1.2.3 Overload for vector 145](#overload-for-vector)

[9.14.1.3 Method: write 146](#method-write)

[9.14.1.3.1 Overload for Output Stream 146](#overload-for-output-stream)

[9.14.1.3.2 Overload for String 147](#overload-for-string-3)

[9.14.1.3.3 Overload for Vector 148](#overload-for-vector-1)

[9.14.1.4 Method: messageReadOnly 149](#method-messagereadonly)

[9.14.1.5 Method: messageWriteOnly 149](#method-messagewriteonly)

[9.14.1.6 Method: supportsObjectRead 150](#method-supportsobjectread)

[9.14.1.7 Method: supportsObjectWrite 150](#method-supportsobjectwrite)

[9.14.1.8 Method: getCalApiVersion 151](#method-getcalapiversion)

[9.14.1.9 Method: getEncoding 151](#method-getencoding)

[9.14.1.10 Method: getSchemaVersion 152](#method-getschemaversion)

[9.14.1.11 Method: getVendorVersion 152](#method-getvendorversion)

[9.14.1.12 Method: getVendor 153](#method-getvendor)

[9.14.1.13 Default Constructor: 153](#default-constructor-8)

[9.14.1.14 Default Copy Constructor: 154](#default-copy-constructor-9)

[9.14.1.15 Operator: operator= 155](#operator-operator-17)

[9.15 The ExternalizerLoader Class 155](#the-externalizerloader-class)

[9.15.1 The ExternalizerLoader Class Methods and Operators
156](#the-externalizerloader-class-methods-and-operators)

[9.15.1.1 Destructor: ~ExternalizerLoader
156](#destructor-externalizerloader)

[9.15.1.2 Method: getExternalizer 157](#method-getexternalizer)

[9.15.1.3 Method: destroyExternalizer 158](#method-destroyexternalizer)

[9.15.1.4 Default Constructor: 158](#default-constructor-9)

[9.15.1.5 Default Copy Constructor: 159](#default-copy-constructor-10)

[9.15.1.6 Operator: operator= 160](#operator-operator-18)

[9.15.1.7 Function: uci\_getExternalizerLoader
161](#function-uci_getexternalizerloader)

[9.15.1.8 Function: uci\_destroyExternalizerLoader
161](#function-uci_destroyexternalizerloader)

[10 Accessors 162](#accessors)

[10.1 Generating C++ Data Type and Enumeration Item Names
162](#generating-c-data-type-and-enumeration-item-names)

[10.2 Class Declarations 163](#class-declarations)

[10.2.1 Accessor Instance Definitions
164](#accessor-instance-definitions)

[10.2.1.1 Destructor: ~&lt;cxxTypeName&gt; 165](#destructor-cxxtypename)

[10.2.1.2 Default Constructor: &lt;cxxTypeName&gt;
166](#default-constructor-cxxtypename)

[10.2.1.3 Default Copy Constructor: &lt;cxxTypeName&gt;
167](#default-copy-constructor-cxxtypename)

[10.2.2 Accessor Instance Member Functions
168](#accessor-instance-member-functions)

[10.2.2.1 Member Function: copy 168](#member-function-copy)

[10.2.2.2 Operator: operator= 169](#operator-operator-19)

[10.2.3 The Element Access Member Functions
169](#the-element-access-member-functions)

[10.2.3.1 Member Function: get&lt;cxxElementName&gt;
170](#member-function-getcxxelementname)

[10.2.3.2 Const Member Function: get&lt;cxxElementName&gt;
171](#const-member-function-getcxxelementname)

[10.2.3.3 Member Function: set&lt;cxxElementName&gt;
172](#member-function-setcxxelementname)

[10.2.3.4 Simple Primitive Const Member Function:
get&lt;cxxElementName&gt;
173](#simple-primitive-const-member-function-getcxxelementname)

[10.2.3.5 Simple Primitive Member Function: set&lt;cxxElementName&gt;
174](#simple-primitive-member-function-setcxxelementname)

[10.2.3.6 String Primitive Member Function: set&lt;cxxElementName&gt;
175](#string-primitive-member-function-setcxxelementname)

[10.2.3.6.1 Overload for String 175](#overload-for-string-4)

[10.2.3.6.2 Overload for C-String 176](#overload-for-c-string-3)

[10.2.3.7 Enumeration Member Function: set&lt;cxxElementName&gt;
177](#enumeration-member-function-setcxxelementname)

[10.2.3.8 Non-Simple Primitive Member Function:
get&lt;cxxElementName&gt;
178](#non-simple-primitive-member-function-getcxxelementname)

[10.2.3.9 Non-Simple Primitive Const Member Function:
get&lt;cxxElementName&gt;
179](#non-simple-primitive-const-member-function-getcxxelementname)

[10.2.3.10 Non-Simple Primitive Member Function:
set&lt;cxxElementName&gt;
180](#non-simple-primitive-member-function-setcxxelementname)

[10.2.3.11 Bounded List Member Function: get&lt;cxxElementName&gt;
180](#bounded-list-member-function-getcxxelementname)

[10.2.3.11.1 Const Variant 180](#const-variant-3)

[10.2.3.11.2 Non-Const Variant 181](#non-const-variant-3)

[10.2.3.12 Bounded List Member Function: set&lt;cxxElementName&gt;
182](#bounded-list-member-function-setcxxelementname)

[10.2.3.13 Member Function: has&lt;cxxElementName&gt;
183](#member-function-hascxxelementname)

[10.2.3.14 Member Function: enable&lt;cxxElementName&gt;
184](#member-function-enablecxxelementname)

[10.2.3.15 SimpleList Member Function: enable&lt;cxxElementName&gt;
185](#simplelist-member-function-enablecxxelementname)

[10.2.3.16 Member Function: clear&lt;cxxElementName&gt;
186](#member-function-clearcxxelementname)

[10.2.3.17 Member Function: getUCITypeVersion
187](#member-function-getucitypeversion)

[10.2.3.18 Method: create 188](#method-create)

[10.2.3.18.1 Overload for Default Initialized
188](#overload-for-default-initialized)

[10.2.3.18.2 Overload for Copying 189](#overload-for-copying)

[10.2.3.19 Method: destroy 190](#method-destroy)

[10.3 Global Element Accessors 190](#global-element-accessors)

[10.3.1 Global Element Accessor Header Files
190](#global-element-accessor-header-files)

[10.3.2 Realizing Global Element Accessor Instances
191](#realizing-global-element-accessor-instances)

[10.3.3 Realizing the Factory Methods
191](#realizing-the-factory-methods)

[10.3.3.1 Method: createReader 191](#method-createreader)

[10.3.3.2 Method: destroyReader 192](#method-destroyreader)

[10.3.3.3 Method: createWriter 193](#method-createwriter)

[10.3.3.4 Method: destroyWriter 194](#method-destroywriter)

[10.3.4 Global Element Accessor Special C++ Classes
194](#global-element-accessor-special-c-classes)

[10.3.4.1 Realizing the Listener Class
195](#realizing-the-listener-class)

[10.3.4.1.1 Method: handleMessage 195](#method-handlemessage)

[10.3.4.2 Realizing the Reader Class 196](#realizing-the-reader-class)

[10.3.4.2.1 Destructor: ~Reader 196](#destructor-reader-1)

[10.3.4.2.2 Method: addListener 197](#method-addlistener)

[10.3.4.2.3 Method: removeListener 198](#method-removelistener)

[10.3.4.2.4 Method: read 198](#method-read-1)

[10.3.4.2.5 Method: readNoWait() 200](#method-readnowait)

[10.3.4.2.6 Method: close 201](#method-close)

[10.3.4.2.7 Default Constructor: Reader
202](#default-constructor-reader)

[10.3.4.2.8 Default Copy Constructor: Reader
202](#default-copy-constructor-reader)

[10.3.4.2.9 Operator: operator= 203](#operator-operator-20)

[10.3.4.3 Realizing the Writer Class 204](#realizing-the-writer-class)

[10.3.4.3.1 Destructor: ~Writer 204](#destructor-writer-1)

[10.3.4.3.2 Method: write 205](#method-write-1)

[10.3.4.3.3 Method: close 206](#method-close-1)

[10.3.4.3.4 Default Constructor: Writer
207](#default-constructor-writer)

[10.3.4.3.5 Default Copy Constructor: Writer
208](#default-copy-constructor-writer)

[10.3.4.3.6 Operator: operator= 209](#operator-operator-21)

[10.4 Accessor Specification 209](#accessor-specification)

[10.5 The Primitive Accessors 210](#the-primitive-accessors)

[10.5.1 The SimplePrimitive Accessors
210](#the-simpleprimitive-accessors)

[10.5.1.1 Realizing the SimplePrimitive Instance
210](#realizing-the-simpleprimitive-instance)

[10.5.1.1.1 The SimplePrimitive Accessor Type
210](#the-simpleprimitive-accessor-type)

[10.5.1.1.2 The SimplePrimitive Accessor Class
210](#the-simpleprimitive-accessor-class)

[10.6 The Simple Accessors 216](#the-simple-accessors)

[10.6.1 The SimpleRestriction Accessor
216](#the-simplerestriction-accessor)

[10.6.1.1 An Example 216](#an-example)

[10.6.1.2 Realizing the SimpleRestriction Instance
216](#realizing-the-simplerestriction-instance)

[10.6.2 The Universally Unique Identifier Accessor
217](#the-universally-unique-identifier-accessor)

[10.6.2.1 An Example 217](#an-example-1)

[10.6.2.2 Realizing the UUID Instance Access Methods
218](#realizing-the-uuid-instance-access-methods)

[10.6.2.2.1 Method: get&lt;cxxElementName&gt;
218](#method-getcxxelementname)

[10.6.2.2.2 Method: set&lt;cxxElementName&gt;
219](#method-setcxxelementname)

[10.6.3 The Enumeration Accessor 219](#the-enumeration-accessor)

[10.6.3.1 An Example 219](#an-example-2)

[10.6.3.2 Realizing the Enumeration Instance
222](#realizing-the-enumeration-instance)

[10.6.3.2.1 Operator: operator= 224](#operator-operator-23)

[10.6.3.2.2 Method: setValue 226](#method-setvalue)

[10.6.3.2.3 Method: getValue 227](#method-getvalue)

[10.6.3.2.4 Method: getNumberOfItems 228](#method-getnumberofitems)

[10.6.3.2.5 Method: isValid 229](#method-isvalid-1)

[10.6.3.2.6 Operator: operator==(const &lt;cxxTypeName&gt;&)
232](#operator-operatorconst-cxxtypename)

[10.6.3.2.7 Operator: operator!= (const &lt;cxxTypeName&gt;&)
233](#operator-operator-const-cxxtypename)

[10.6.3.2.8 Operator: operator&lt;(const &lt;cxxTypeName&gt;&)
234](#operator-operatorconst-cxxtypename-1)

[10.6.3.2.9 Operator: operator&lt;=(const &lt;cxxTypeName&gt;&)
235](#operator-operatorconst-cxxtypename-2)

[10.6.3.2.10 Operator: operator&gt;(const &lt;cxxTypeName&gt;&)
236](#operator-operatorconst-cxxtypename-3)

[10.6.3.2.11 Operator: operator&gt;=(const &lt;cxxTypeName&gt;&)
237](#operator-operatorconst-cxxtypename-4)

[10.6.3.2.12 Operator: operator==(EnumerationItem rhs)
238](#operator-operatorenumerationitem-rhs)

[10.6.3.2.13 Operator: operator==(EnumerationItem lhs, const
&lt;cxxTypeName&gt;&)
239](#operator-operatorenumerationitem-lhs-const-cxxtypename)

[10.6.3.2.14 Operator: operator!= (EnumerationItem rhs)
240](#operator-operator-enumerationitem-rhs)

[10.6.3.2.15 Operator: operator!= (EnumerationItem lhs, const
&lt;cxxTypeName&gt;&)
241](#operator-operator-enumerationitem-lhs-const-cxxtypename)

[10.6.3.2.16 Operator: operator&lt;(EnumerationItem rhs)
242](#operator-operatorenumerationitem-rhs-1)

[10.6.3.2.17 Operator: operator&lt;(EnumerationItem lhs, const
&lt;cxxTypeName&gt;&)
243](#operator-operatorenumerationitem-lhs-const-cxxtypename-1)

[10.6.3.2.18 Operator: operator&lt;=(EnumerationItem rhs)
244](#operator-operatorenumerationitem-rhs-2)

[10.6.3.2.19 Operator: operator&lt;=(EnumerationItem lhs, const
&lt;cxxTypeName&gt;&)
245](#operator-operatorenumerationitem-lhs-const-cxxtypename-2)

[10.6.3.2.20 Operator: operator&gt;(EnumerationItem rhs)
246](#operator-operatorenumerationitem-rhs-3)

[10.6.3.2.21 Operator: operator&gt;(EnumerationItem lhs, const
&lt;cxxTypeName&gt;&)
247](#operator-operatorenumerationitem-lhs-const-cxxtypename-3)

[10.6.3.2.22 Operator: operator&gt;=(EnumerationItem rhs)
248](#operator-operatorenumerationitem-rhs-4)

[10.6.3.2.23 Operator: operator&gt;=(EnumerationItem lhs, const
&lt;cxxTypeName&gt;&)
249](#operator-operatorenumerationitem-lhs-const-cxxtypename-4)

[10.6.3.2.24 Method: toName 250](#method-toname)

[10.6.3.2.25 Method: fromName 252](#method-fromname)

[10.6.3.2.26 Method: setValueFromName 253](#method-setvaluefromname)

[10.6.3.2.27 Global Operator: operator&lt;&lt;
254](#global-operator-operator)

[10.7 The Complex Accessors 254](#the-complex-accessors)

[10.7.1 The LocalElement Accessor 254](#the-localelement-accessor)

[10.7.1.1 An Example 254](#an-example-3)

[10.7.1.2 Realizing the LocalElement Instance
255](#realizing-the-localelement-instance)

[10.7.2 The Choice Accessor 256](#the-choice-accessor)

[10.7.2.1 An Example 256](#an-example-4)

[10.7.2.2 Realizing the Choice Instance
258](#realizing-the-choice-instance)

[10.7.2.2.1 Method: get&lt;cxxTypeName&gt;ChoiceOrdinal
259](#method-getcxxtypenamechoiceordinal)

[10.7.2.2.2 Method: is&lt;cxxElementName&gt; const
260](#method-iscxxelementname-const)

[10.7.2.2.3 Method: set&lt;cxxName&gt;ChoiceOrdinal
261](#method-setcxxnamechoiceordinal)

[10.7.2.2.4 Complex Type Method: choose&lt;cxxElementName&gt;
263](#complex-type-method-choosecxxelementname)

[10.7.2.2.5 SimpleList Method: choose&lt;cxxElementName&gt;
264](#simplelist-method-choosecxxelementname)

[10.7.2.2.6 Bounded List Method: choose&lt;cxxElementName&gt;
265](#bounded-list-method-choosecxxelementname)

[10.7.3 The GlobalElement Accessor 266](#the-globalelement-accessor)

[10.7.3.1 An Example 266](#an-example-5)

[10.7.3.2 Realizing the GlobalElement Instance
266](#realizing-the-globalelement-instance)

[11 C++ CAL CERT Verification 267](#c-cal-cert-verification)

[12 List of Symbols, Abbreviations, and Acronyms
268](#list-of-symbols-abbreviations-and-acronyms)

[13 Glossary 269](#glossary)

This page is intentionally left blank.

List of Tables

[Table 1.2-1 OMS D&D Documents 3](#_Toc219293146)

[Table 1.2-2 Other Documents 3](#_Toc219293147)

[Table 2.4-1 The XSD Primitive Data Types 5](#_Toc219293148)

[Table 4.0-1 The XSD Namespace to C++ Namespace Translation Table
18](#_Toc219293149)

[Table 9.1-1 The Simple Primitive Types 27](#_Toc219293150)

[Table 9.1-2 The String Primitive Types 28](#_Toc219293151)

[Table 9.1-3 The Binary Primitive Types 29](#_Toc219293152)

[Table 9.4-1 getAccessorType() Return Values 39](#_Toc219293153)

[Table 10.1-1 C++ Reserved Keywords 163](#_Toc219293154)

This page is intentionally left blank.

Introduction
============

Interface Specification Goals
-----------------------------

One of the primary goals of the Open Mission Systems (OMS) program was
to specify a standard set of messages that could be used for command and
control (C2). The messages would be used, for example, to command a
Service to perform some function.

A secondary goal was to be able to specify the content and format of the
data in these messages in a way that was independent of programming
languages, data transport technologies, and data transport protocols.
This goal provides an independence of the OMS Message Set from the
technologies that could be used to move these messages from sender to
receiver on a Platform. Such independence allows development of the OMS
Messages and the transfer technologies to proceed independently of each
other.

The decision was made to use the XML Schema Definition language to
specify the content and format of the OMS Messages. See <span
class="underline">http://www.w3.org/TR/xmlschema-1/</span> \[XML Schema
Part 1: Structures Second Edition\] and <span
class="underline">http://www.w3.org/TR/xmlschema-2/</span> \[XML Schema
Part 2: Datatypes Second Edition\] for details.

The XML Schema Definition language is based on a concept of a schema. In
general, the purpose of a schema is to define a class of XML documents.
The following is from the XSD specification:

The purpose of an XSD schema is to define and describe a class of XML
documents by using schema components to constrain and document the
meaning, usage and relationships of their constituent parts: datatypes,
elements and their content and attributes and their values.

OMS does not use an XSD schema to define a class of documents but rather
to declare a set of data types in a programming language agnostic
manner. In other words, OMS uses XML Schema Definition language as an
Interface Definition Language (IDL) from which programming language
specific data types can be generated. This is similar to the way the
Object Management Group’s (OMG) IDL is used by both Common Object
Request Broker Architecture (CORBA) and Data Distribution Service (DDS)
to declare the data types that specify the content and format of the
data that is passed from sender to receiver. For OMS, these data types
are used to specify the content and format of the OMS Messages that are
sent from sender to receiver, e.g., from Service to Service.

The XML Schema Definition language is a specialization of the Extensible
Markup Language (XML). As such, it follows the format specified by XML.
The specialization comes in the form of restricting valid elements to a
small set of elements and restricting the relationship of the elements
to each other. These valid elements are known in the XML Schema
Definition language as schema components. These schema components are
normally used to specify how a valid document can be constructed. For
OMS, these schema components are used to declare different types of data
types. This is very similar to how keywords such as struct and union are
used in C++ to declare different types of data types.

Just to note that in earlier versions of the specification, schema
components were referred to as elements, following the XML naming
convention. This document will use the term schema component when
referring to these specialized elements.

Given the selection of the XML Schema Description language as the
language to be used to specify the contents and format of the OMS
Messages, a schema, the OMS Schema Definition, was created that
describes the content and format of the OMS Messages. Once this schema
existed, a mechanism was required to produce program specific data types
that corresponded to the data types specified in the OMS Schema. That
mechanism originally called the C++ CAL-GT and now called the OMS Schema
C++ Compiler, was created with the intent of creating a set of C++ data
types that corresponded to the data types specified in the OMS Schema
Definition.

The OMS Schema C++ Compiler belongs to a family of technologies known as
schema compilers. A famous example of such a compiler is the JAXB
compiler that is targeted at the Java programming language.

During the development of the OMS Schema C++ Compiler, a decision was
made to have the compiler produce C++ code that was independent of the
transport technologies that would be used to transfer the messages. This
independence would allow application developers to develop code
independently of which transfer technology would be used. This
independence was deemed very important for it would permit developers to
develop applications that could run on a wide variety of Platforms, even
if all Platforms chose to use a different transfer technology.

A second decision was made to realize these C++ data types as an
Application Programming Interface (API) whose underlying data structures
and method definitions may vary by implementation. This decision would
allow the development of the transport support code to be as efficient
as possible since the developers would be free to architect the data
structures and code in which ever manner was best suited for the chosen
transport technology while still requiring user interactions to occur
through a standardized interface.

The realization of these goals was a set of Accessor classes that
specified a set of getter and setter methods. Each schema component
declared in the OMS Schema Definition is generally realized as a C++
Accessor class (there are a few exceptions). The methods of an Accessor
class provide access to the data that corresponds to the data type
declared by the schema component.

As the OMS C++ Schema Compiler matured, the need for a specification
specifying how the schema components were translated into C++ data types
became apparent. Thus, this specification, which specifies how each
schema component is translated into a C++ data type, was written.

Unlike the OMS C++ Schema Compiler that clearly defines how the various
data types are to be implemented; this specification attempts to be
implementation independent and only specifies the prototypes for the
various methods and function as well as specifying bounds for various
data types, e.g., the range of values a data type must be able to
represent. There are a few places where implementation details are
called out in this specification.

References
----------

### OMS D&D Documents

The documents listed in Table 1.2-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219293146" class="anchor"></span>Table 1.2-1 OMS D&D
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

### Other Documents

The documents listed in Table 1.2-2, Other Documents, are cited
throughout this document. For dated references, only the edition cited
applies. For undated references, the latest edition of the referenced
document (including any amendments or corrigenda) applies.

<span id="_Toc219293147" class="anchor"></span>Table 1.2-2 Other
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
<td>ISO/IEC 14882:1998</td>
<td>Programming Languages – C++</td>
<td></td>
<td>01 September 1998</td>
</tr>
<tr class="even">
<td>ISO/IEC 14882:2017</td>
<td>Programming Languages – C++</td>
<td></td>
<td>01 December 2017</td>
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
<tr class="even">
<td>IETF RFC 4122</td>
<td>A Universally Unique IDentifier (UUID) URN Namespace</td>
<td></td>
<td>July 2005</td>
</tr>
</tbody>
</table>

The XML Schema
==============

This section provides a brief introduction of the XML Schema Definition
Language. The intent is to provide a description of the various aspects
of the XML schema that are used by the OMS Schema in order to construct
a framework upon which the details of the OMS Schema C++ Mapping can be
discussed. For further information regarding the XML schema, refer to
the W3C XML Schema Definition Language (XSD) 1.0 (Part 1: Structures and
Part 2: Datatypes).

Schema Components
-----------------

The XML Schema Definition (XSD) specification specifies a set of
elements known as schema components. As per the specification, these
components are used to define the various components that make up a
document, their format and content. OMS uses these components
differently, to declare a set of data types that are referred to in this
document as XSD data types.

The different types of schema components, e.g., a sequence and a choice
component, are used to declare different types of XSD data types. The
schema components do this by specifying the contents of that XSD data
type and the format used to declare those contents. The name of the
schema component is used to identify which component is to be used when
declaring a XSD data type.

This use of schema components is very similar to how C++ uses different
types of constructs to declare data types. For example, C++ has a
structure and a union constructs name struct and union respectively.
These two constructs specify what contents the data type can be declared
to hold, a set of values or one value from a set of values, and the
format used to declare those contents.

Namespaces
----------

All named entities in an XML schema, including the schema components and
the data types that they are used to declare, have associated names
(simple strings) that reside within the same or different namespaces
(collection of names).

Some of these namespaces are globally known. For example, the XML Schema
Definition specification declares several globally known namespaces. One
of these namespaces is used to hold the names of all schema components
and primitive (built-in) data types. This namespace, which is known as
the XML Schema Definition namespace, is named <span
class="underline">http://www.w3.org/2001/XMLSchema</span>.

OMS also uses a primary namespace that is used to hold the names of all
data types that are declared to be used with OMS Messages. The
namespace, known as the UCI namespace (for historical reasons) is named
org::ucistandard.

Prefixes
--------

The use of these long namespace names without the use of a prefix (see
next paragraph for an example), to identify a namespace has two
fundamental problems. The first is that the use of certain characters
with the name of the namespace may not be valid XML syntax and thus
cannot be used to identify a namespace. The second problem is that such
long names can make that schema more difficult to read. To solve the
first problem and ease the second problem, the prefix construct was
added to the XML Schema Definition specification.

A prefix is a short name that is used to refer to a namespace. For
example, the name xs can be used to refer to the XML Schema Definition
namespace, i.e., <span
class="underline">http://www.w3.org/2001/XMLSchema</span>. These
prefixes can be, and by convention are, used wherever a name of a
namespace is required, generally prior to the name of a schema component
or a data type (which is why they are known as prefixes). As will be
pointed out in Section 2.5, Names, the mapping of prefix to namespace is
specified as part of the Schema Component’s attribute set.

In the discussions and examples used in this document, the alias xs will
be used to refer to the XML Schema Definition namespace and the alias
uci will be used to refer to the UCI namespace.

Primitive Data Types
--------------------

The XML Schema Definition specifies a set of primitive, built-in data
types. These primitive types fall into one of the following classes:

-   Atomic: Values of this type are treated as indivisible units.

-   String: Values of this type are treated as being composed of a
    sequence of characters.

-   Binary: Values of this type are treated as an array of octets of
    binary values.

-   List: Values of this type are treated as a list of values.

Table 2.4-1, The XSD Primitive Data Types, lists the XSD primitive types
along with their name, their type, and additional comments:

<span id="_Toc219293148" class="anchor"></span>Table 2.4-1 The XSD
Primitive Data Types

<table>
<thead>
<tr class="header">
<th>XSD Data Type</th>
<th>Class</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>anyURI</td>
<td>string</td>
<td>An Internationalized Resource Identifier</td>
</tr>
<tr class="even">
<td>base64Binary</td>
<td>binary</td>
<td>Base64 encoded binary data</td>
</tr>
<tr class="odd">
<td>boolean</td>
<td>atomic</td>
<td>A boolean, two-value logic</td>
</tr>
<tr class="even">
<td>date</td>
<td>atomic</td>
<td>A specific day</td>
</tr>
<tr class="odd">
<td>dateTime</td>
<td>atomic</td>
<td>A specific instance of time</td>
</tr>
<tr class="even">
<td>dateTimeStamp</td>
<td>atomic</td>
<td>A specific instance of time</td>
</tr>
<tr class="odd">
<td>decimal</td>
<td>atomic</td>
<td>A real number data type</td>
</tr>
<tr class="even">
<td>integer</td>
<td>atomic</td>
<td>A signed integer value</td>
</tr>
<tr class="odd">
<td>long</td>
<td>atomic</td>
<td>A signed 64-bit integer value</td>
</tr>
<tr class="even">
<td>int</td>
<td>atomic</td>
<td>A signed 32-bit integer value</td>
</tr>
<tr class="odd">
<td>short</td>
<td>atomic</td>
<td>A signed 16-bit integer value</td>
</tr>
<tr class="even">
<td>byte</td>
<td>atomic</td>
<td>A signed 8-bit integer value</td>
</tr>
<tr class="odd">
<td>nonNegativeInteger</td>
<td>atomic</td>
<td>A non-negative signed integer value</td>
</tr>
<tr class="even">
<td>positiveInteger</td>
<td>atomic</td>
<td>A positive signed integer value</td>
</tr>
<tr class="odd">
<td>unsignedLong</td>
<td>atomic</td>
<td>An unsigned 64-bit integer value</td>
</tr>
<tr class="even">
<td>unsignedInt</td>
<td>atomic</td>
<td>An unsigned 32-bit integer value</td>
</tr>
<tr class="odd">
<td>unsignedShort</td>
<td>atomic</td>
<td>An unsigned 16-bit integer value</td>
</tr>
<tr class="even">
<td>unsignedByte</td>
<td>atomic</td>
<td>An unsigned 8-bit integer value</td>
</tr>
<tr class="odd">
<td>nonPositiveInteger</td>
<td>atomic</td>
<td>A non-positive signed integer value</td>
</tr>
<tr class="even">
<td>negativeInteger</td>
<td>atomic</td>
<td>A negative signed integer value</td>
</tr>
<tr class="odd">
<td>double</td>
<td>atomic</td>
<td>An IEEE double precision 64-bit floating point data type</td>
</tr>
<tr class="even">
<td>duration</td>
<td>atomic</td>
<td>A duration of time</td>
</tr>
<tr class="odd">
<td>dayTimeDuration</td>
<td>atomic</td>
<td>A duration of time</td>
</tr>
<tr class="even">
<td>yearMonthDuration</td>
<td>atomic</td>
<td>A duration of time</td>
</tr>
<tr class="odd">
<td>float</td>
<td>atomic</td>
<td>An IEEE single precision 32-bit floating point data type</td>
</tr>
<tr class="even">
<td>gDay</td>
<td>string</td>
<td>A Gregorian day</td>
</tr>
<tr class="odd">
<td>gMonth</td>
<td>string</td>
<td>A Gregorian month</td>
</tr>
<tr class="even">
<td>gMonthDay</td>
<td>string</td>
<td>A Gregorian month and day</td>
</tr>
<tr class="odd">
<td>gYear</td>
<td>string</td>
<td>A Gregorian year</td>
</tr>
<tr class="even">
<td>gYearMonth</td>
<td>string</td>
<td>A Gregorian year and month</td>
</tr>
<tr class="odd">
<td>hexBinary</td>
<td>binary</td>
<td>Hex encoded binary data</td>
</tr>
<tr class="even">
<td>NOTATION</td>
<td>string</td>
<td>An XML notation attribute</td>
</tr>
<tr class="odd">
<td>QName</td>
<td>string</td>
<td>An XML qualified name</td>
</tr>
<tr class="even">
<td>string</td>
<td>string</td>
<td>A simple character string</td>
</tr>
<tr class="odd">
<td>normalizedString</td>
<td>string</td>
<td>An XML white spaced, normalized string</td>
</tr>
<tr class="even">
<td>token</td>
<td>string</td>
<td>A tokenized string</td>
</tr>
<tr class="odd">
<td>language</td>
<td>string</td>
<td>A formal natural language identifier</td>
</tr>
<tr class="even">
<td>Name</td>
<td>string</td>
<td>An XML name</td>
</tr>
<tr class="odd">
<td>NCName</td>
<td>string</td>
<td>An XML non-colonized name</td>
</tr>
<tr class="even">
<td>ENTITY</td>
<td>string</td>
<td>An XML Entity attribute type</td>
</tr>
<tr class="odd">
<td>ID</td>
<td>string</td>
<td>An XML ID attribute type</td>
</tr>
<tr class="even">
<td>IDREF</td>
<td>string</td>
<td>An XML IDREF attribute type</td>
</tr>
<tr class="odd">
<td>NMTOKEN</td>
<td>string</td>
<td>A NMTOKEN XML attribute type</td>
</tr>
<tr class="even">
<td>time</td>
<td>atomic</td>
<td>Recurring instances of time</td>
</tr>
<tr class="odd">
<td>ENTITIES</td>
<td>list</td>
<td>A list of XML Entity attribute types</td>
</tr>
<tr class="even">
<td>IDREFS</td>
<td>list</td>
<td>A list of XML IDREF attribute types</td>
</tr>
<tr class="odd">
<td>NMTOKENS</td>
<td>list</td>
<td>A list of NMTOKEN XML attribute types</td>
</tr>
</tbody>
</table>

Names
-----

A schema uses names, strings of characters, to identify schema
components, data types, etc. Names come in two versions, qualified and
unqualified. The difference between the two is whether the name contains
an identification of the namespace within which the name was declared.
If the name does contain such identification, then that name is said to
be qualified. If it does not, then that name is said to be unqualified.

Unqualified names still require some mechanism that can be used to
determine which namespace they were declared in. This is required in
order to prevent collision between names. The context in which the name
is declared is determined by the default namespace and target namespace
that are declared as part of the schema (see Section 2.8, The Schema
Declaration). XML Schema Definition specification details how this
namespace determination is used.

In many cases, unqualified names cannot be used since there is no
mechanism that can be used to determine which namespace that name was
declared in. In these cases, and in cases where one wishes to avoid any
ambiguity in determining which namespace the name was declared in, one
would use a qualified name.

Qualified names use the following syntax:

&lt;prefix&gt;:&lt;name&gt;

where:

&lt;prefix&gt; is the prefix that refers to the XML Schema Definition
namespace, i.e., <span
class="underline">http://www.w3.org/2001/XMLSchema</span>. Following
from the discussion in Section 2.1, Schema Components, this prefix is
the string xs.

&lt;name&gt; is the name of the component, data type, etc.

XSD References
--------------

References are used within an XSD data type to refer to another XSD data
type. These references are the names of the XSD data types being
referred to. When an unqualified name is used, the XSD data type being
referred to must reside in the default data type. When a qualified name
is used, its prefix identifies the namespace in which the name of the
XSD data type being referred to was declared in.

XSD Data Types
--------------

The XML Schema Definition language specifies a set of schema components,
which are specialized XML elements that can be used to declare a data
type. These components include element, sequence, choice, complexType,
and simpleType. The set of components that are supported by this
specification are listed in Section 2.8, The Schema Declaration, and
Section 2.9, The Schema Components.

These schema components are used to realize a set of data types which
are referred to in this document as XSD data types. This naming is used
to differentiate the specification of the data type within the schema
from the specification of the C++ data types.

The schema component is used to specify the contents of the XSD data
type and the format used to declare those contents. Different components
will support different contents and different formats. This is similar
to the relationship in C++ between the keywords struct and union and the
data types that are declared when using these keywords.

A XSD data type has three distinct parts. They are:

-   The Schema Component Name: This is the name of the schema component
    (not the name of the XSD data type that is being declared by the
    schema component) that is used to specify the contents of the XSD
    data and the format used when declaring those contents. This name is
    sometimes referred to as the component’s element name since the
    component is just a specialized XML element.

-   The Attribute Set: A set of attributes that apply to the XSD data
    type being declared. The entries in the attribute set are formatted
    as name/value pairs in which the name is the name of one of the data
    type’s attributes and the value is the value of the named attribute.

For example, the entry

name=“myName”

in the attribute set would be used to set the name attribute of the XSD
data type being declared to myName.

The XSD standard specifies which attributes are supported on a per
schema element basis. For example, the standard specifies that for an
xs:complexType element, the supported attributes include id, name,
mixed, abstract, block, final, and defaultAttributesApply.

This is noted here that as far as this specification is concerned,
attributes are used for two purposes. The first purpose is to identify
which Schema Accessor should be bound to a given data type declaration
encountered in the Schema document. The second purpose is to initialize
the attributes of the Schema Accessor that is being bound to the data
type declaration.

-   Embedded Data Types: A set of XSD data types that are embedded
    within the declared data type. These embedded data types can
    themselves contain embedded data types. There is no limit to how
    deep this embedding of XSD data types can go but for practical
    purposes, going too deep makes reading the data type declaration
    more difficult. Note: The usual name scoping rules found in C++
    apply to these embedded data types. The XSD data type’s named schema
    component will specify which data types can be embedded. As far as
    the bindings specified in this specification goes, not all data
    types that are specified in the XML Schema Definition specification
    as being valid embeddable data types are supported. Sections 2.8,
    The Schema Declaration, and 2.9, The Schema Components, specify
    which data types can be embedded in each XSD data type.

The Schema Declaration
----------------------

The schema declaration, which is declared using the xs:schema element,
is the schema declaration within which all other declarations are made.
It is this declaration that defines the format and contents of a schema
document. From the perspective of the OMS Schema Compiler, the schema
declaration is the container for all declarations contained within an
OMS Schema Definition.

The declarations that are direct descendants of the schema declaration
are known as global or top-level declarations. In this specification,
both terms will be used to refer to these declarations. These global
declarations are special in the sense that they declare data types that
are visible to other declarations (global visibility) and can be
referenced (identified) by other declarations. Declarations that are not
direct descendants of the schema declaration, i.e., those declarations
that are embedded within other declarations, are known as embedded or
local declarations and are not visible outside of the declaration in
which they are embedded. In this specification, both terms will be used
to identify this class of declarations. Due to this visibility
restriction, these declarations cannot be referenced (identified) by
other declarations.

The schema component supports a variety of attributes. Those attributes
supported by the binding specified in this document include:

-   version: Specifies the version of the schema. Only one version can
    be specified.

-   xmlns: Specifies a name of a namespace. Any number of namespaces can
    be specified.

-   xmlns:&lt;alias&gt;: Specifies a mapping of an alias to a name of a
    namespace. Any number of aliases can be specified and any number of
    aliases can refer to the same namespace.

-   targetNamespace: Specifies the namespace that declarations of data
    types using unqualified names will be added. Only one single
    targetNamespace can be specified.

-   elementFormDefault: Specifies the default form of the element
    specifications. This can either be specified as qualified or
    unqualified. Only one single elementFormDefault can be specified.

-   attributeFormDefault: Specifies the default form of the attribute
    specifications. This can either be specified as qualified or
    unqualified. Only one single attributeFormDefault can be specified.

The schema component presents a chicken-and-egg problem in that the
qualified name of the schema component contains an alias to the XML
Schema Description namespace but no alias has been specified at the
point the schema component is encountered in the document. This issue
will be revisited later in Section 5.0, Names and Qualified Names.

The Schema Components
---------------------

As stated above, the XML Schema Definition specification contains a
variety of schema components. These components are used to declare a
variety of different kinds of data types. There is a one-to-one
relationship between a component and the kind of XSD data type that is
declared when using that component. For example, Global Simple Type
components are used to declare Global Simple Type data types.

In the discussions that follow, a reference to a primitive data type or
a named XSD data type is simply the name of that data type (either a
qualified or unqualified name). For example, the element name xs:Integer
is used to reference the Integer data type that was declared in the XML
Schema Definition namespace while the element name uci:MyName is used to
reference the MyName data type that was declared in the UCI namespace.

Several of the schema components share the same element name. For
example, the Global and Local Simple Types components share the element
name xs:simpleType. The context in which the component is used will
clarify which component is being specified.

The following is the list of schema components that are covered by the
OMS Schema C++ Mapping specification. These are the only types of schema
components that can be included in an OMS schema. The inclusion of any
other type of schema component in an OMS schema invalidates that schema.

### Schema Component

The schema component, which is identified using the xs:schema element
name, is the outer most declaration that is used to specify all data
types. This component can contain any number of declarations of Global
Simple Type, Global Complex Type, and Global Element data types.

#### Global Simple Types

A Global Simple Type component, which is identified using the
xs:simpleType element name, is used to declare a data type that belongs
to the class of named data types known as the named simple data types.
Exactly which XSD data type is being declared depends on the declaration
contained in the Global Simple Type.

A Global Simple Type component can contain one and only one declaration
that must be either a declaration of a Simple Restriction, a List, or a
Union data type. This declaration determines the XSD data type that is
being declared.

#### Global Complex Types

A Global Complex Type component, which is identified using the
xs:complexType element name, is used to declare a data type that belongs
to the class of named data types known as the named complex data types.
Exactly which XSD data type is being declared depends on the declaration
contained in the Global Complex Type.

The Global Complex Type component can contain a declaration of a Simple
Content data type, a Complex Content data type, or one or more
declarations of Sequence and Choice data types.

#### Global Elements

A Global Element component, which is identified using the xs:element
element name, is used to declare a named data type. The name of the data
type is declared using the component’s name attribute. The component’s
type may be declared in one of two ways:

-   By referencing a primitive data type (see Section 9.1, The Primitive
    Types), a named Global Simple Type data type, or a named Global
    Complex Type data type via the component’s type attribute.

-   By including a declaration of a Local Simple Type or a Local Complex
    Type data type.

### Components

#### Simple Restriction Component

A Simple Restriction component, which is identified using the
xs:restriction keyword, is used to declare an anonymous Simple
Restriction XSD data type which is a member of the class of Simple Data
Types. This type of data type is declared by restricting of some other
simple data type.

The data type that the Simple Restrictions component restricts is known
as the component’s base data type. The XML Schema Definition
specification supports a variety of Facets that are used to restrict the
Simple Restriction component’s base data type. Facet declarations are
included in the simple restriction using the facet’s element name to
identify the Facet and specifying the facet’s value using the facet’s
value attributes.

The Simple Restriction’s base data type can be declared in one of two
ways:

-   By referencing a primitive data type (see Section 9.1, The Primitive
    Types) or a named Global Simple Type data type via the component’s
    base attribute.

-   By including a declaration of a Local Simple Type data type.

The set of Facets contains an enumeration Facet named xs:enumeration.
This Facet restricts the base type to not only a specific data type but
to a specific set of valid values. This Facet is handled differently
than all other facets.

#### Local Simple Type Component

A Local Simple Type component, which is identified using the
xs:simpleType element name, is used to declare an anonymous simple data
type. A Local Simple Type component can contain one and only one
declaration that must be either a declaration of a Simple Restriction, a
List, or a Union data type.

#### Simple Content Component

A Simple Content component, which is identified using the
xs:simpleContent element name, is used to create an anonymous complex
data type. A Simple Content component can contain one and only one
declaration that must be either a declaration of a Simple Content
Restriction or a Simple Content Extension data type.

#### Complex Content Component

A Complex Content component, which is identified using the
xs:complexContent element name, is used to create an anonymous complex
data type. A Complex Content component can contain one and only one
declaration that must be either a declaration of a Complex Content
Restriction or a Complex Content Extension data type.

### Data Type Declarations

#### Choice

A Choice, which is identified using the xs:choice element name, is used
to declare an anonymous complex data type that consists of a selection
of one component from a set of components. A Choice can contain any
number of the following:

-   The declaration of a Local Element data type.

-   The declaration of a Sequence data type.

-   The declaration of a Choice data type.

#### Sequence

A Sequence, which is identified using the xs:sequence element name, is
used to declare an anonymous complex data type that consists of an
ordered-specific, set of data types. A Sequence can contain any number
of the following:

-   The declaration of a Local Element data type.

-   The declaration of a Sequence data type.

-   The declaration of a Choice data type.

### Content Restriction and Extension Components

#### Simple Content Restriction Component

A Simple Content Restriction component, which is identified using the
xs:restriction element name, is used to declare an anonymous simple data
type that is a restriction of some other simple data type. The data type
that the Simple Content Restrictions component restricts is known as the
component’s base data type.

The Simple Content Restriction’s base data type can be declared by
referencing a primitive data type (see Section 9.1, The Primitive Types)
or a named Global Simple Type data type via the component’s base
attribute.

The XML Schema Definition specification supports a variety of Facets
that are used to restrict the Simple Content Restriction component’s
base data type. Facet declarations are included in the simple
restriction using the facet’s element name to identify the Facet and
specifying the facet’s value using the facet’s value attributes.

#### Simple Content Extension Component

A Simple Content Extension component, which is identified using the
xs:extension element name, is used to declare an anonymous simple data
type that is an extension of some other simple data type. The data type
that the Simple Content Extension component extends is known as the
component’s base data type.

The Simple Content Extension’s base data type can be declared by
referencing a primitive data type (see Section 9.1, The Primitive Types)
or a named Global Simple Type data type via the component’s base
attribute.

The base data type is extended by including any number of declarations
of Local Attribute data types.

#### Complex Content Restriction Component

A Complex Content Restriction component, which is identified using the
xs:restriction element name, is used to declare an anonymous complex
data type that is a restriction of some other complex data type. The
data type that the Complex Content Extension component extends is known
as the component’s base data type.

The Complex Content Restriction’s base data type can be declared by
referencing a named Global Complex Type data type via the component’s
base attribute.

The base data type is restricted by including a declaration of a Choice
or a Sequence data type. These declarations are used to remove parts of
the data type that match these restricted data types.

#### Complex Content Extension Component

A Complex Content Extension component, which is identified using the
xs:extension element name, is used to declare an anonymous complex data
type that is an extension of some other complex data type. The data type
that the Complex Content Extension component extends is known as the
component’s base data type.

The Complex Content Extension’s base data type can be declared by
referencing a primitive data type (see Section 9.1, The Primitive
Types), a named Global Complex Type data type via the component’s base
attribute.

The base data type is extended by including a declaration of a Choice or
a Sequence data type.

### Local Element

A Local Element, which is identified using the xs:element element name,
is used to declare the existence of a field in the OMS Message of a
specific type. That type may be declared using the Local Element’s type
attribute which names another component or the Local Element may contain
a Local Complex Type Component that is used to declare the Local
Element’s type.

### Local Complex Type Component

A Local Complex Type component, which is identified using the
xs:complexType element name, is used to declare an anonymous complex
data type.

The Local Complex Type component can contain a declaration of a Simple
Content data type, a Complex Content data type, or one or more
declarations of Sequence and Choice data types.

Variants
--------

Several of the schema components described in the previous subsection
support the ability to specify XSD data types that come in one of three
variants. The schema components that do support the declaration of these
variants do so by supporting the specification of minOccurs and
maxOccurs attributes in the XSD data type’s attributes set. Schema
components that do not provide this support can only be used to declare
non-variant XSD data.

By default, when not declared in the XSD’s attribute set, the value of
these two attributes is set to 1. Either one, or both attributes, can be
declared in the XSD data type’s attribute set to be any value (note that
minOccurs must always be declared to be less than or equal to maxOccurs
in order for the schema to be valid).

The three variants of the XSD data types are:

### Singular Schema Components

These are schema components that declare to be single value of a
specified type. For these components, the minOccurs and maxOccurs are
both declared to be 1.

### Collection Schema Components

These are components that are declared to be a collection of values of a
specified type. For these components, the maxOccurs is declared to be
value greater than 1 (minOccurs can be declared to be any value less
than maxOccurs).

### Optional Schema Components

These are components that are declared to be optional; they may or may
not be included in an OMS Message. For these components, the minOccurs
is declared to be 0 and maxOccurs is declared to be 1.

The C++ OMS Schema Compiler Conceptual Architecture
===================================================

From a conceptual perspective, the C++ OMS Schema Compiler has a fairly
simple architecture. It is composed of an XML Schema Definition (XSD)
parser and a set of Accessors. The parser is used to parse the OMS
Schema Definition written using the XSD language while the Accessors
embody the rules and operations that are required to produce the C++
software that is the realization of the OMS Schema Definition.

For each declaration contained in the OMS Schema Definition, both
top-level and Embedded Declarations, the parser will select the Accessor
that is able to process that declaration. The selection of which
Accessor to use to process the declaration is dictated by the Accessor’s
rule set. This rule set contains a set of rules that have to be
satisfied in order for that Accessor to be selected. If no such Accessor
exists, i.e., if no Accessor exists whose rule set can be completely
satisfied, the OMS Schema Definition is said to be invalid. The
mechanism used to handle invalid OMS Schema Definitions is an
implementation issue and not specified in this document.

If all rules in an Accessor’s rule set are satisfied, then that Accessor
is selected and an Accessor Instance is instantiated from the selected
Accessor. That Accessor Instance is then bound to the declaration being
parsed.

Accessor Instances that are bound to top-level declarations are known as
Top-Level Accessor Instances while those that are bound to Embedded
Declarations are known as Embedded Accessor Instances.

Due to the fact that a data type declaration in an XSD schema can
reference a declaration before that declaration has been parsed, i.e.,
it is a forward reference, it may not be possible to fully bind an
Accessor Instance to a declaration or it might not be possible to select
an Accessor from which the Accessor Instance is to be instantiated. Due
to this issue, the parser must either support a multi-pass operation or
some sort of back patching. The choice of which mechanism to use to deal
with this issue is an implementation decision that is not specified in
this document. The key point is that once the parser has completed
parsing the OMS Schema Definition, all data type declarations must have
one, and only one, Accessor Instance bound to them.

An OMS Schema Compiler must have a “list” of Top-Level Accessor
Instances known as the Compiler’s Top-Level Accessor Instances List.
These Accessor Instances can either be bound to top-level declarations
in the main OMS Schema Definition or from any “included” or “imported”
schema definition. This “list” will be used to find an Accessor Instance
that has been identified by some declaration contained in either the
main OMS Schema Definition or from any “included” or “imported” schema
definition.

Once the parser has completed parsing the OMS Schema Definition, the
generation of the C++ software occurs by realizing each Accessor
Instance. This realization process generates the necessary files and C++
software that is required to fully realize the data types that were
declared in the OMS Schema Definition.

For most Accessor Instances, the C++ software that is generated is a C++
class known as C++ Accessor class. These classes provide access to the
type of data that correspond to the data type declarations that were
specified in the OMS Schema Definition. This is way these classes are
known as Accessors. The actual mechanism employed by these classes to
provide this access is an implementation issue and not specified in this
document.

One of the main philosophies behind the requirements levied on the OMS
Schema Compiler is that the compiler should detect issues with the OMS
Schema Definition that would result in invalid C++ code being generated.
In other words, the OMS Schema Compiler should not just blindly generate
C++ but should check to validate that the generated code is valid. For
example, many XSD constructs allow one to refer to an XSD data type
simply by naming that type. The compiler could simply convert that name
to its C++ equivalent and then use that name in the generated code,
regardless of whether that name is actually a name of a C++ data type.
Instead of allowing this blind use of the name, the requirements levied
on the compiler require it to validate that the name is valid before it
can be used.

These validation requirements do increase the complexity of the
compiler. The tradeoff is that this additional complexity does help
guarantee that the resulting C++ code is valid (there can still be other
issues with a particular compiler). From a user’s perspective, this is a
valuable tradeoff.

In the discussions that follow, the following terms will be used:

-   Accessor: can be used in two different manners throughout this
    document and may require the reader to utilize context to determine
    which definition is appropriate.

-   refers to the conceptual construct that is part of the C++ OMS
    Schema Compiler’s conceptual architecture. The details regarding
    these Accessors, including their rules and operations, are specified
    in this document.

-   refers to the C++ object instantiated from an Accessor class.

-   Accessor Instance: refers to an instance of an Accessor which is
    itself a conceptual construct.

-   Accessor class: refers to the realization of an Accessor Instance as
    a C++ class.

In the sections that follow, the details regarding Accessors is
discussed. This discussion includes:

-   what happens when the Accessor Instance is realized, i.e., what
    software is generated, and

-   how the data is accessed, i.e., what methods are generated that
    provide access to the data.

Namespaces
==========

As described in Section 2.2, Namespaces, names are declared in some
namespace. Two examples given were the XML Schema Definition namespace,
i.e., <span class="underline">http://www.w3.org/2001/XMLSchema</span>,
and the UCI namespace, <span
class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>. Every
namespace that is declared in a schema must be mapped to valid C++
names. The names of these namespaces cannot be used directly for they
can contain characters that are invalid as far as names for C++
namespaces are concerned.

There exists a variety of different ways the names of the XML Schema
Definition namespaces can be mapped to C++. This specification uses a
simple table (see Table 4.0-1, The XSD Namespace to C++ Namespace
Translation Table) to specify the mapping of the names of the XML Schema
Definition namespaces to C++.

<span id="_Toc219293149" class="anchor"></span>Table 4.0-1 The XSD
Namespace to C++ Namespace Translation Table

<table>
<thead>
<tr class="header">
<th>Schema Namespace</th>
<th>C++ Namespace</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span class="underline">http://www.w3.org/2001/XMLSchema</span></td>
<td>xs</td>
</tr>
<tr class="even">
<td><span class="underline">https://www.vdl.afrl.af.mil/programs/oam</span></td>
<td>uci</td>
</tr>
</tbody>
</table>

In addition to supporting these translations, all schema compilers must
provide support for extending this mapping without modification of code
(e.g., CAL generation tool, schema complier code, or CAL implementation
code). For example, a mechanism by which a new name of a schema
namespace and its translation to a name of a C++ namespace can be added
to this table. The schema compiler must also guarantee that no mapping
specified in Table 4.0-1, The XSD Namespace to C++ Namespace Translation
Table, is overridden by any new entries to this table.

As stated in Section 2.2, Namespaces, the two well-known namespaces
include:

-   <span
    class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>:
    This namespace is known as the UCI namespace and includes the names
    of all UCI related data types. As stated in Table 4.0-1, The XSD
    Namespace to C++ Namespace Translation Table, this XSD namespace is
    mapped to the C++ namespace uci.

-   <span class="underline">http://www.w3.org/2001/XMLSchema</span>:
    This namespace is known as the XML Schema namespace and includes the
    names of all primitive types that are declared in XML Schema
    specification. As stated in Table 4.0-1, The XSD Namespace to C++
    Namespace Translation Table, this namespace is mapped to the C++
    namespace xs.

A qualified namespace is composed of the names of one or more namespaces
concatenated into one string. The names in the namespace are separated
by some separator. For XSD namespaces, this separator is a single colon,
i.e., “:”, whereas for C++ namespaces, this separator is a double colon,
i.e., “::”.

The first name in the namespace is known as the root namespace. For
example, the namespace “uci” is the root namespace of the C++ namespace
“uci::type”. All Accessor Instances have an associated root namespace
(Section 10.1, Generating C++ Data Type and Enumeration Item Names) that
is used to generate the namespaces in which declarations of classes and
data types that are generated as part of realizing that Accessor
Instance are declared in. More information regarding these classes can
be found in Section 10.3, Global Accessors.

Names and Qualified Names
=========================

In the discussions that follow in this and other sections, the terms
“name” and “qualified name” are heavily used. The term “name” is meant
to be a simple string that is used to identify some entity, e.g., an
Accessor Instance. However, since multiple entities can have the same
name, names cannot uniquely identify an entity.

In order to uniquely identify an entity, one needs to use a “qualified
name”. Qualified names are strings that combine the name of the entity
with the name of a namespace that contains that name. Within a given
namespace, all names must be unique. Namespaces provide a hierarchical
structure in that a namespace can contain not only names of entities but
also names of other namespaces. Regardless of whether a name refers to
an entity or a namespace, all names within a namespace must be unique.

Qualified names come in a variety of formats. The XSD specification uses
a format in which the names of the namespaces are separated by a single
colon whereas the C++ specification uses a format in which the names of
the namespaces are separated by a double colon. For example, the entity
“data” that is contained in the namespace “types” that is contained in
the namespace “uci” would be written in an XSD document as
“uci:type:data” whereas it would be written in a C++ document as
“uci::type::data”.

This specification assumes that all names that are parsed by the XSD
parser are converted into qualified names of the form
“&lt;namespace&gt;:&lt;name&gt;” regardless of whether that name as
declared in the OMS Schema Definition was qualified or not. For example,
a complexType declaration may declare its name as “UserDataType.” For
this example, the parser is expected to convert this to a qualified name
having the form “&lt;targetNamespace&gt;:UserDataType”, where
&lt;targetNamespace&gt; is the name of the target namespace as specified
by the top-level schema declaration. In the discussions that follow,
&lt;namespace&gt; is referred to as the “namespace component” of the
qualified name and &lt;name&gt; is referred to as the “name component”
of the qualified name.

Names can be formatted in several different ways. These include:

-   Upper Case: Names of this format have all characters in their upper
    case form, i.e., ‘A’, ‘B’, ‘C’, etc.

-   Lower Case: Names of this format have all characters in their lower
    case form, i.e., ‘a’, ‘b’, ‘c’, etc.

-   Capitalize: Names of this format have the first character of the
    name in its upper case form, i.e., ‘A’, ‘B’, ‘C’, etc. This format
    says nothing regarding the remaining characters in the name.

-   Uncapitalize: Names of this format have the first character of the
    name in its lower case form, i.e., ‘a’, ‘b’, ‘c’, etc. This format
    says nothing regarding the remaining characters in the name.

The terms presented below are used throughout the document as
placeholders for member functions, type definitions, etc.

-   cxxBaseTypeName: defined as an xs:extension's base attribute
    translated using the rules specified in Section 10.1, Generating C++
    Data Type and Enumeration Item Names. When evaluating a CERT,
    substitute "cxxBaseTypeName" for \`parent::xs:extension/@base\` and
    perform the aforementioned translation.

-   cxxElementName: defined as an xs:element's name attribute translated
    using the rules specified in Section 10.1, Generating C++ Data Type
    and Enumeration Item Names. When evaluating a CERT, substitute
    "cxxElementName" for \`self::xs:element/@name\` and perform the
    aforementioned translation.

-   cxxElementTypeName: defined as an xs:element's type attribute
    translated using the rules specified in Section 10.1, Generating C++
    Data Type and Enumeration Item Names. When evaluating a CERT,
    substitute "cxxElementTypeName" for \`self::xs:element/@type\` and
    performed the aforementioned translation.

cxxPrimitiveName: defined as the name of the C++ primitive data type
that the Accessor Instance pertains to. These primitive names are
outlined in the "C++ Data Type" columns of the "The Simple Primitive
Types", "The String Primitive Types", "The Numeric String Types", "The
Binary Primitive Types", and "The List Primitive Types" tables and must
follow the requirements set within Section 9.1 "The Primitive Types".

-   cxxRootNamespace: defined as the namespace URI for the prefix of an
    xs:element's type attribute or xs:extension's base attribute mapped
    to the "Schema Namespace" column of Table 4.0-1 "The XSD Namespace
    to C++ Namespace Translation Table". When evaluating a CERT,
    substitute "cxxRootNamespace" for
    \`(self::xs:element|parent::xs:element)/@type|parent::xs:extension/@base\`
    and perform the aforementioned mapping.

-   cxxTargetNamespace: defined as the namespace URI of the root
    xs:schema element's targetNamespace attribute mapped to the "Schema
    Namespace" column of Table 4.0-1 "The XSD Namespace to C++ Namespace
    Translation Table". When evaluating a CERT, substitute
    "cxxTargetNamespace" for \`ancestor::xs:schema/@targetNamespace\`
    and perform the aforementioned mapping.

-   cxxTypeName: defined as the local name of a XSD element translated
    using the rules specified in Section 10.1, Generating C++ Data Type
    and Enumeration Item Names.

In addition, these terms can be used as arguments to the following
functions:

-   firstLetterToLowerCase(): the first character of the term is set to
    lower case.

-   toUpperCase(): all characters of the term are set to upper case.

As an example for these terms and functions:

-   A CERT with the text
    "&lt;cxxRootNamespace&gt;::type::&lt;cxxTypeName&gt;" is meant to be
    replaced with "uci::type::UserDataType".

-   A CERT with the text
    "&lt;cxxRootNamespace&gt;::base::accessorType::&lt;firstLetterToLowerCase(cxxTypeName)&gt;"
    is meant to be replaced with
    "uci::base::accessorType::userDataType".

Directory Structure
===================

The files that are generated by an OMS schema compiler are to be placed
in a set of directories having specific names and have a specific
relationship to each other and a root directory denoted in this
specification as the rootDirectory. This specification only specifies
that this directory must exist, it does not specify the path to the
rootDirectory. As such, implementers are free to locate the
rootDirectory anywhere in a file system, e.g.,
“/usr/include/oms/include” and “/usr/src/oms”.

For each namespace declared in a schema, a subdirectory having the same
name as the namespace must be created in the rootDirectory. These
directories are known as the namespace specific root directories for
they contain the files generated from the XSD declarations that were
declared in the associated namespace. For example, the files that are
generated as a result of parsing XSD declarations declared in the “<span
class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>”
namespace, which is mapped to the C++ “uci” namespace, would be created
in the “&lt;rootDirectory&gt;/uci” directory.

Subdirectories
--------------

### type

This directory is used to hold the header files generated for each C++
data type. For each XSD data type declared in the schema, a
corresponding C++ data type will be generated. A header file is created
in the “&lt;rootDirectory&gt;/&lt;cxxNamespace&gt;/type” directory for
each C++ data type that is generated. The name of this header file is
the same name as the name of the XSD data type with the first letter of
the name capitalized and the string “.h” appended to the name. Including
this file will result in the declaration of the C++ data type. This is
not to say that the C++ data type is declared in this file but rather
that the act of including this file causes the C++ data type to be
declared. For example, this header file may include other header files,
in one of which is the declaration of the data type. These files and
their contents are described in more detail in Sections 9.5, The
StringAccessor Class.

UCI Include Directory
---------------------

The UCI include directory, i.e., the “&lt;rootDirectory&gt;/uci”
directory, contains one additional subdirectory that is not included in
any other namespace specific root directories. This directory, known as
the uciBase directory, contains files that include the declaration of
the various base classes that are required regardless of which OMS
Schema Definition compiled. The name of this directory is “base” and its
relative path is “&lt;rootDirectory&gt;/uci/base”. Section 7, Accessor
Construction and Destruction provides the details regarding what files
are contained in this directory and the contents of those files.

Accessor Construction and Destruction
=====================================

One of the main goals of this specification was to produce an API
specification that imposed a minimum restriction on the implementation
of the Schema compiler. One aspect of the specified API that can impose
a major restriction on implementation is the mechanism employed to
instantiate the various C++ Accessors.

The standard mechanism employed to instantiate an object is the use of
the new operator. Depending on how the Accessor classes are implemented
and on how the underlying transport is supported, the new operator may
not be applicable. Due to this issue, this specification has chosen to
use the Factory programming paradigm data type factory methods in
constructing the Accessor objects. The Factory paradigm allows the
implementation to choose the appropriate mechanism to use when
instantiating Accessor objects.

In order to enforce the use of the data type factory methods and
disallow the use of the new operator, an Accessor’s default constructor,
copy constructor, and assignment operator need to all be declared with
protected access. Declaring access to these constructors and operators
as protected forces the compiler to disallow the use of the new operator
with these Accessor classes. Thus, the only way for an application to
instantiate an Accessor Instance is to use the proper factory functions.

As far as the other methods declared in the Accessor class, the
mechanism employed to implement these classes is also an implementation
decision that is not covered by this specification. For example, the
implementation for these methods may be inlined, implemented as an
Accessor class method in a source file, or implemented as part of a
derived class.

Documentation and Annotations
=============================

From the perspective of this specification, any documentation that is
embedded within a declaration using the xs:annotation and
xs:documentation declarations are valid as far as this specification is
concerned but that documentation is ignored. In other words, an OMS
Schema Definition can embed documentation within the various
declarations but, as far as this specification is concerned, that
documentation will not be used in generating any C++ content.

The fact that this specification states that the documentation is
ignored does imply any constraints on what a particular OMS Schema
Compiler must do with regards to this documentation. An OMS Schema
Compiler is free to also ignore these declarations or use them to
generate documentation in conjunction with generating the C++
declarations, e.g., by embedding the documentation within the C++
declarations or by producing a stand-alone document.

The Primitive and Basic Data Types
==================================

The following are a set of classes, type definitions, and functions that
must be generated regardless of the OMS schema being compiled. Each
class, type definition, and function must be declared when including the
specified header file.

The Primitive Types
-------------------

The XML Schema Definition specification includes the specification of a
set of primitive (or built-in) types. These primitive data types are
declared in the XML Schema Definition namespace, i.e., “[<span
class="underline">http://www.w3.org/2001/XMLSchema</span>](http://www.w3.org/2001/XMLSchema)”.

These primitive types are separated into 4 categories: simple types,
string types, binary types, and list types. They are detailed in the
following subsections.

### The Simple Primitive Data Types

Table 9.1-1, The Simple Primitive Types, contains a listing of all
simple primitive data types allowed in the UCI schema. The table
specifies the name of the simple primitive types as specified in the XML
Schema Definition (XSD) specification, the name of the corresponding C++
data type, the definition of that C++ data type, and the type’s
classification. The C++ data types are specified in the POSIX
specification. The type’s classification can be a combination of:

-   atomic: classifies the data type as being indivisible, i.e., cannot
    be divided into simpler types.

-   numeric: classifies the data type as being a numerical value,
    including integer and real (floating point) values.

<span id="_Toc219293150" class="anchor"></span>Table 9.1-1 The Simple
Primitive Types

<table>
<thead>
<tr class="header">
<th>XSD Data Type</th>
<th>C++ Data Type</th>
<th>Type Definition</th>
<th>Classification</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>boolean</td>
<td>Boolean</td>
<td>bool</td>
<td>atomic</td>
</tr>
<tr class="even">
<td>long</td>
<td>Long</td>
<td>int64_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="odd">
<td>int</td>
<td>Int</td>
<td>int32_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="even">
<td>short</td>
<td>Short</td>
<td>int16_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="odd">
<td>byte</td>
<td>Byte</td>
<td>int8_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="even">
<td>unsignedInt</td>
<td>UnsignedInt</td>
<td>uint32_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="odd">
<td>unsignedShort</td>
<td>UnsignedShort</td>
<td>uint16_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="even">
<td>unsignedByte</td>
<td>UnsignedByte</td>
<td>uint8_t</td>
<td>atomic, numeric</td>
</tr>
<tr class="odd">
<td>double</td>
<td>Double</td>
<td>double</td>
<td>atomic, numeric</td>
</tr>
<tr class="even">
<td>float</td>
<td>Float</td>
<td>float</td>
<td>atomic, numeric</td>
</tr>
<tr class="odd">
<td>duration</td>
<td>Duration</td>
<td>int64_t</td>
<td>atomic</td>
</tr>
<tr class="even">
<td>time</td>
<td>Time</td>
<td>int64_t</td>
<td>atomic</td>
</tr>
<tr class="odd">
<td>dateTime</td>
<td>DateTime</td>
<td>int64_t</td>
<td>atomic</td>
</tr>
</tbody>
</table>

> CERT CXX-004937 \[An OMS C++ CAL API shall define the type
> "&lt;cxxPrimitiveName&gt;" in the "xs" namespace equivalent to the
> type "Type Definition" for each "C++ Data Type" of "The Simple
> Primitive Types" table when the file
> "xs/type/simpleXmlSchemaPrimitives.h" is included.\]

Please note that the XSD specification documents duration, time,
dateTime, and date as being strings specifying some time, date, or a
combination of both. The OMS program has chosen to realize these as
atomic values, i.e., a 64-bit integer value. The reason for this is that
it improves performance when the Services use these values as there will
be no need for converting strings to numerical values and back again.
Such conversions are required when work with times and dates that are
obtained by other means such as invoking an Operating System function
(see the various POSIX APIs).

The impact of this decision is that new restrictions have been placed on
how these three data types can be used in the OMS Schema Definition. For
example, Facets that can be used to restrict these types, such as the
pattern facet, are no longer applicable.

For the Simple Primitive Data Types, the reader and writer
construction/destruction methods are not realized.

### The String Primitive Data Types

Table 9.1-2, The String Primitive Types, contains a listing of all
string primitive data types allowed in the UCI schema. The table
specifies the name of the string primitive types as specified in the XML
Schema Definition (XSD) specification, the name of the corresponding C++
data type, and the name of the AccessorType that is associated with the
Accessor that will provide access to the string data type (Section 9.3,
The Accessor Type Constants).

<span id="_Toc219293151" class="anchor"></span>Table 9.1-2 The String
Primitive Types

<table>
<thead>
<tr class="header">
<th>XSD Data Type</th>
<th>C++ Data Type</th>
<th>Accessor Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>string</td>
<td>String</td>
<td>string</td>
</tr>
</tbody>
</table>

> CERT CXX-004940 \[An OMS C++ CAL API shall define the type
> "&lt;cxxPrimitiveName&gt;" in the "xs" namespace equivalent to the
> type "uci::base::StringAccessor" for each "C++ Data Type" of "The
> String Primitive Types" table when the file
> "xs/type/stringXmlSchemaPrimitives.h" is included.\]

For the String Primitive Data Types, the reader and writer
construction/destruction methods are not realized.

### The Numeric String Primitive Data Types

Numeric string primitive data types are not allowed in the UCI schema.

### The Binary Primitive Data Types

Table 9.1-3, The Binary Primitive Types, contains a listing of all
binary primitive data types allowed in the UCI schema. The table
specifies the name of the binary primitive types as specified in the XML
Schema Definition (XSD) specification, the name of the corresponding C++
data type, and the name of the AccessorType that is associated with the
Accessor that will provide access to the binary data type (Section 9.3,
The Accessor Type Constants).

<span id="_Toc219293152" class="anchor"></span>Table 9.1-3 The Binary
Primitive Types

<table>
<thead>
<tr class="header">
<th>XSD Data Type</th>
<th>C++ Data Type</th>
<th>Accessor Type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>hexBinary</td>
<td>HexBinary</td>
<td>hexBinary</td>
</tr>
</tbody>
</table>

> CERT CXX-004946 \[An OMS C++ CAL API shall define the type
> "&lt;cxxPrimitiveName&gt;" in the "xs" namespace equivalent to the
> type "uci::base::SimpleList&lt; uint8\_t, 0 &gt;" for each "C++ Data
> Type" of "The Binary Primitive Types" table when the file
> "xs/type/binaryXmlSchemaPrimitives.h" is included.\]

For the Binary Primitive Data Types, the reader and writer
construction/destruction methods are not realized.

### The List Primitive Data Types

List primitive data types are not allowed in the UCI schema.

The UCIException Class
----------------------

The UCIException class is the exception that can be thrown by the
implementation of the C++ methods described throughout this document.

> CERT CXX-004954 \[An OMS C++ CAL API shall define the "UCIException"
> class in the "uci::base" namespace that publicly and singly inherits
> from "std::runtime\_error" when the file "uci/base/UCIException.h" is
> included.\]

Programming note: The term "singly" implies the derived class inherits
from a base class through exactly one path allowing for an implicit
upcast and dynamic downcast. Dynamic downcast requires that the base
class have at least one virtual function or that the derived class
virtually inherits the base class.

For example, the following can be generated:

class UCIException : public std::runtime\_error

> GUID CXX-011257 \[An OMS C++ CAL API should indicate that a method
> should not throw an exception by using either throw() or noexcept as
> appropriate for the targeted C++ version.\]
>
> CERT CXX-004959 \[An OMS C++ CAL API shall define the public member
> type "ErrorCode" of the "uci::base::UCIException" class equivalent to
> the type "uint32\_t".\]

### UCIException Class Methods and Operators

#### Constructor(const std::string& reason)

-   Signature:

explicit

UCIException(const std::string& reason, ErrorCode errorCode = 0)

-   Return:

N/A

-   Parameters:

reason: a C++ standard library string that explains the reason the
exception was thrown.

errorCode: The associated error code. The default value for this
parameter is 0 (zero).

-   Exceptions:

std::runtime\_error: Exception thrown if the construction of the
exception fails.

-   Access:

Public.

> CERT CXX-004962 \[An OMS C++ CAL API shall declare the public explicit
> constructor UCIException(const std::string&, ErrorCode = 0) of the
> "uci::base::UCIException" class.\]

#### Constructor(const char\*)

-   Signature:

explicit

UCIException(const char\* reason, ErrorCode errorCode = 0)

-   Return:

N/A

-   Parameters:

reason: a C-string that explains the reason the exception was thrown.

errorCode: The associated error code. The default value for this
parameter is 0 (zero).

-   Exceptions:

std::runtime\_error: Exception thrown if the construction of the
exception fails.

-   Access:

Public.

> CERT CXX-004964 \[An OMS C++ CAL API shall declare the public explicit
> constructor UCIException(const char\*, ErrorCode = 0) of the
> "uci::base::UCIException" class.\]

#### Constructor(const std::ostringstream&)

-   Signature:

explicit

UCIException(const std::ostringstream& reason, ErrorCode errorCode = 0)

-   Return:

N/A

-   Parameters:

reason: a C++ standard library output string stream that explains the
reason the exception was thrown.

errorCode: The associated error code. The default value for this
parameter is 0 (zero).

-   Exceptions:

std::runtime\_error: Exception thrown if the construction of the
exception fails.

-   Access:

Public.

> CERT CXX-004966 \[An OMS C++ CAL API shall declare the public explicit
> constructor UCIException(const std::ostringstream&, ErrorCode = 0) of
> the "uci::base::UCIException" class.\]

#### Method: getErrorCode

Returns this UCIException’s error code.

-   Signature:

ErrorCode getErrorCode() const

throw()

-   Return:

This exception’s error code.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public.

> CERT CXX-004969 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UCIException::ErrorCode getErrorCode() of
> the "uci::base::UCIException" class as non-throwing.\]

#### Macro: throwUciException

> CERT CXX-004971 \[An OMS C++ CAL API shall define the
> throwUciException(message) macro equivalent to "\#define
> throwUciException(message) do { std::ostringstream oStream; oStream
> &lt;&lt; message; throw ::uci::base::UCIException(oStream); } while
> (false)" when the file "uci/base/UCIException.h" is included.\]

This macro is provided for ease-of-use. It provides support for throwing
an exception using a stream to construct the reason for why the
exception was thrown. For example, one could write the following:

throwUciException(“A reason: value =” &lt;&lt; value);

Note the line continuation symbols, i.e., the backslash, are only
required if the definition is split across lines in the header file in
which it is defined.

The Accessor Type Constants
---------------------------

Since there will be a need among applications to easily determine which
type of Accessor Instance the application is using, a simple mechanism
that allows an application to easily determine types has been added to
this specification that all schema compilers must support.

These additional declarations are associated with an Accessor Instance.
The generation of these additional AccessorType declarations is called
out in the appropriate sections of this document. When this
documentation specifies that a declaration of an AccessorType is to be
generated, that documentation will specify the qualifiedCxxName of the
AccessorType (see Section 4, Namespaces for a discussion of qualified
names and the namespace and name components that make up the qualified
name).

To accomplish this association, all C++ Accessor classes should declare
and implement a method whose signature is as follows:

a\. uci::base::accessorType::AccessorType getAccessorType() const

Section 9.4, The Accessor Class, provides the details regarding this
method.

The value that the getAccessorType() method returns should be a unique
value that is associated with its accessorType.

A schema compiler is free to choose any mechanism to associate an
AccessorType value with a specific Accessor Instance provided that every
Accessor Instance is assigned a unique value.

As the above method signature shows, the value’s type is declared to be
an AccessorType.

The definition of this AccessorType should be declared in the
“uci::base::accessorType” namespace.

This AccessorType should be declared when including the file
“uci/base/accessorType.h”.

> CERT CXX-004979 \[An OMS C++ CAL API shall define the type
> "AccessorType" in the "uci::base::accessorType" namespace equivalent
> to the type "uint32\_t" when the file "uci/base/accessorType.h" is
> included.\]
>
> CERT CXX-004985 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant "null" in the
> "uci::base::accessorType" namespace when the file
> "uci/base/accessorType.h" is included.\]
>
> CERT CXX-005760 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant
> "&lt;firstLetterToLowerCase(cxxPrimitiveName)&gt;Accessor" in the
> "uci::base::accessorType" namespace for each "C++ Data Type" of "The
> Simple Primitive Types" table when the file "uci/base/accessorType.h"
> is included.\]
>
> CERT CXX-005832 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant "Accessor Type" in the
> "xs::accessorType" namespace for each "Accessor Type" of "The String
> Primitive Types" table when the file "uci/base/accessorType.h" is
> included.\]
>
> CERT CXX-005924 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant "Accessor Type" in the
> "xs::accessorType" namespace for each "Accessor Type" of "The Numeric
> String Primitive Types" table when the file "uci/base/accessorType.h"
> is included.\]
>
> CERT CXX-005990 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant "Accessor Type" in the
> "xs::accessorType" namespace for each "Accessor Type" of "The Binary
> Primitive Types" table when the file "uci/base/accessorType.h" is
> included.\]
>
> CERT CXX-006065 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant "Accessor Type" in the
> "xs::accessorType" namespace for each "Accessor Type" of "The List
> Primitive Types" table when the file "uci/base/accessorType.h" is
> included.\]
>
> CERT CXX-006140 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant
> "&lt;firstLetterToLowerCase(cxxTypeName)&gt;" in the
> "&lt;cxxTargetNamespace&gt;::type::accessorType" namespace for each
> \`/xs:schema/xs:simpleType\[not(ancestor::xs:schema/@targetNamespace =
> '<span
> class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>' and
> @name = 'UniversallyUniqueIdentifierType')\]\` when the file
> "uci/base/accessorType.h" is included.\]
>
> CERT CXX-007112 \[An OMS C++ CAL API shall define the
> uci::base::accessorType::AccessorType constant
> "&lt;firstLetterToLowerCase(cxxTypeName)&gt;" in the
> "&lt;cxxTargetNamespace&gt;::type::accessorType" namespace for each
> \`/xs:schema/xs:complexType\` when the file "uci/base/accessorType.h"
> is included.\]

For example, the AccessorType can be declared:

typedef uint32\_t AccessorType;

In addition to declaring the AccessorType, the inclusion of the file
“uci/base/accessorType.h” should also include the declarations of
additional accessor types.

When generating the AccessorType declaration, the following applies:

-   The AccessorType declaration should be declared when the file
    “uci/base/accessorType.h” is included.

-   The AccessorType declaration should be declared within the namespace
    that is the namespace component of the qualifiedCxxName of the
    AccessorType.

-   The AccessorType declaration should be of the form:

-   static const uci::base::accessorType::AccessorType &lt;name&gt; =
    &lt;value&gt;;

-   where:

-   &lt;name&gt; is the name component of the qualifiedCxxName of the
    AccessorType.

-   &lt;value&gt; is the AccessorType’s value.

Note: As stated above, the schema compiler is free to choose any value
provided that the chosen value is unique among all accessor types.

For example, the following can be generated for an AccessorType whose
qualifiedCxxName is specified as the string
“uci::base::accessorType::example”:

namespace uci {

namespace base {

namespace accessorType {

static const uci::base::accessorType::AccessorType example = 123;

}

}

}

The Accessor Class
------------------

The Accessor class is the base class from which all Accessors classes
are derived. The actual accessor objects are instantiated from these
Accessor classes. These objects provide access to data contained in or
associated with an OMS Message.

Several basic Accessor classes/templates are generated by the schema
compiler regardless of which OMS Schema Definition is being compiled.
Details of these classes/templates can be found in the sections that
follow. In addition, schema specific Accessor classes are generated as
part of compiling an OMS Schema Definition. Details regarding these
Accessor classes can be found in Section 10, Accessors.

### The Accessor AccessorType

The OMS Schema Compiler should generate a declaration of an AccessorType
(“The Accessor Type Constants” section) that is to be associated with
the Accessor class.

### The Accessor Class

> CERT CXX-004987 \[An OMS C++ CAL API shall define the "Accessor" class
> in the "uci::base" namespace when the file "uci/base/Accessor.h" is
> included.\]

#### The Accessor Class Methods and Operators

##### Destructor: ~Accessor

Destroys the Accessor when the Accessor goes out of scope or is deleted.

-   Signature:

~Accessor()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-011090 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::Accessor" class.\]

##### Method: getAccessorType

Returns the accessor type for this Accessor. See Section 9.3, The
Accessor Type Constants, for an explanation regarding accessor types.

-   Signature:

uci::base::accessorType::AccessorType getAccessorType() const

throw()

-   Return:

The accessor type constant (see Section 9.3, The Accessor Type
Constants).

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public.

> CERT CXX-004993 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::accessorType::AccessorType
> getAccessorType() of the "uci::base::Accessor" class as
> non-throwing.\]
>
> GUID CXX-011197 \[An OMS C++ CAL API should declare the public const
> member function uci::base::accessorType::AccessorType
> getAccessorType() of the "uci::base::Accessor" class that returns the
> values specified in the "getAccessorType() Return Values" table.\]

<span id="_Toc219293153" class="anchor"></span>Table 9.4-1
getAccessorType() Return Values

<table>
<thead>
<tr class="header">
<th>C++ Accessor</th>
<th>AccessorType Value</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>uci::base::Accessor</td>
<td>uci::base::accessorType::null</td>
</tr>
<tr class="even">
<td>uci::base::StringAccessor</td>
<td>::xs::accessorType::string</td>
</tr>
<tr class="odd">
<td>uci::base::SimpleList</td>
<td>uci::base::accessorType::null</td>
</tr>
<tr class="even">
<td>uci::base::BoundedList</td>
<td>uci::base::accessorType::null</td>
</tr>
<tr class="odd">
<td>SimplePrimitive Accessors</td>
<td>uci::base::accessorType::&lt;firstLetterToLowerCase(cxxTypeName)&gt;</td>
</tr>
<tr class="even">
<td>Global Accessors</td>
<td>&lt;cxxRootNamespace&gt;::type::accessorType::&lt;firstLetterToLowerCase(cxxTypeName)&gt;</td>
</tr>
<tr class="odd">
<td>Local Enumeration</td>
<td>&lt;cxxTargetNamespace&gt;::type::accessorType::&lt;firstLetterToLowerCase(`/xs:schema/xs:*/@name`)&gt;::&lt;firstLetterToLowerCase(cxxElementName)&gt;</td>
</tr>
</tbody>
</table>

##### Method: reset

This method resets the contents of this Accessor to its initial state,
i.e., the state of the Accessor’s contents where in when the Accessor
was instantiated.

-   Signature:

void reset()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs resetting
the Accessor.

-   Access:

Public.

> GUID CXX-004996 \[At a minimum, this should perform the following
> operations:
>
> a\. erasing the contents of any string
>
> b\. erasing the contents of any SimpleList
>
> c\. erasing the contents of any BoundedList
>
> d\. resetting any Choice so that no field is enabled
>
> e\. Implementations are free to perform additional operations as part
> of resetting an accessor.\]
>
> CERT CXX-004997 \[An OMS C++ CAL API shall declare the public
> non-static member function void reset() of the "uci::base::Accessor"
> class.\]

##### Default Constructor:

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s access is protected in order to enforce the use of the
accessor static create methods when constructing an Accessor.

-   Signature:

Accessor()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Accessor fails.

-   Access:

Protected.

> CERT CXX-004998 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::Accessor" class.\]

##### Default Copy Constructor:

Since the Accessor class does not provide access to any data, there is
generally no need to copy any data other than the state of the specified
Accessor (rhs). However, implementations are free to perform whatever
data copying is required to initialize the newly constructed Accessor.
As stated in Section 7, this constructor’s access is protected in order
to enforce the use of the accessor static create methods when
constructing an Accessor.

-   Signature:

Accessor(const Accessor& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Accessor whose contents are used to initialize the contents of
the newly constructed Accessor.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Accessor fails.

-   Access:

Protected.

> CERT CXX-004999 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::Accessor" class.\]

##### Operator: operator=

Sets the contents of this Accessor to be the same as the contents of the
specified Accessor (rhs). Since the Accessor class does not provide
access to any data, this is generally a null operation, i.e., no copying
of data occurs. However, implementations are free to perform whatever
data copying is required to satisfy this operation. As stated in Section
7: Accessor Construction and Destruction, this operator’s access is
protected in order to enforce the use of the Accessor static create
methods when constructing an Accessor.

-   Signature:

Accessor& operator=(const Accessor& rhs)

-   Return:

A reference to this Accessor.

-   Parameters:

rhs: The Accessor on the right hand side (rhs) of the assignment
operator that is used to set the content of this Accessor. Generally,
this parameter is ignored.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected.

> CERT CXX-011148 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the "uci::base::Accessor" class.\]

The StringAccessor Class
------------------------

Support for the primitive string data types is provided via a String
Accessor class that provides access to string data types.

> CERT CXX-005002 \[An OMS C++ CAL API shall define the "StringAccessor"
> class in the "uci::base" namespace that publicly and singly inherits
> from "uci::base::Accessor" when the file "uci/base/StringAccessor.h"
> is included.\]

For example, the following can be generated:

class StringAccessor : public uci::base::Accessor

### The StringAccessor Class Methods and Operators

#### Destructor: ~StringAccessor

Destroys the StringAccessor when the StringAccessor goes out of scope or
is deleted.

-   Signature:

~StringAccessor()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-012700 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::StringAccessor" class.\]

#### Method: str

Returns the string accessed by this StringAccessor as a C++ standard
library string.

-   Signature:

std::string str() const

-   Return:

The string accessed by this StringAccessor returned as a C++ standard
library string.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the string accessed by this StringAccessor.

-   Access:

Public

> CERT CXX-005008 \[An OMS C++ CAL API shall declare the public const
> member function std::string str() of the "uci::base::StringAccessor"
> class.\]

#### Method: c\_str

Returns the string accessed by this StringAccessor as a C-string (i.e.,
const char \*). The string that is returned is owned by this
StringAccessor. Thus the returned pointer should never be deleted. Doing
so will produce undefined results.

-   Signature:

const char\* c\_str() const

-   Return:

The string accessed by this StringAccessor returned as a C-string (i.e.,
const char \*). This point should never be deleted.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the string accessed by this StringAccessor.

-   Access:

Public

> CERT CXX-005009 \[An OMS C++ CAL API shall declare the public const
> member function const char\* c\_str() of the
> "uci::base::StringAccessor" class.\]

#### Method: setStringValue

##### Overload for String

Sets the string accessed by this StringAccessor to the contents of the
specified value which is a C++ standard library string.

-   Signature:

uci::base::StringAccessor& setStringValue(const std::string& value)

-   Return:

A reference to this StringAccessor.

-   Parameters:

value: The C++ standard library string whose contents are to be used to
set the string accessed by this StringAccessor.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs upon
setting the string accessed by this StringAccessor.

-   Access:

Public

> CERT CXX-011141 \[An OMS C++ CAL API shall declare the public
> non-static member function uci::base::StringAccessor&
> setStringValue(const std::string&) of the "uci::base::StringAccessor"
> class.\]

##### Overload for C-String

Sets the string accessed by this StringAccessor to the contents of the
specified value which is a C-string (i.e., const char \*).

-   Signature:

uci::base::StringAccessor& setStringValue(const char\* value)

-   Return:

A reference to this StringAccessor.

-   Parameters:

value: The C-string (i.e., const char \*) whose contents are to be used
to set the string accessed by this StringAccessor.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs upon
setting the string accessed by this StringAccessor.

-   Access:

Public

> CERT CXX-011142 \[An OMS C++ CAL API shall declare the public
> non-static member function uci::base::StringAccessor&
> setStringValue(const char\*) of the "uci::base::StringAccessor"
> class.\]

#### Operator: operator=

##### Overload for StringAccessor

Sets the value of the string accessed by this StringAccessor to the
value of the string accessed by the StringAccessor on the right hand
side (rhs) of the assignment operator.

-   Signature:

StringAccessor& operator=(const StringAccessor& rhs)

-   Return:

A reference to this StringAccessor.

-   Parameters:

rhs: The StringAccessor on the right hand side (rhs) of the assignment
operator which provides access to the string whose contents are to be
assigned to the string that is accessed by this StringAccessor.

-   Exceptions:

Exceptions may be thrown.

-   Access:

Public

##### Overload for String

Sets the value of the string that is accessed by this StringAccessor to
the value of the C++ standard library string on the right hand side
(rhs) of the assignment operator.

-   Signature:

StringAccessor& operator=(const std::string& rhs)

-   Return:

A reference to this StringAccessor.

-   Parameters:

rhs: The C++ standard library string on the right hand side (rhs) of the
assignment operator whose contents are to be copied to the string
accessed by this StringAccessor.

-   Exceptions:

Exceptions may be thrown.

-   Access:

Public

> CERT CXX-011144 \[An OMS C++ CAL API shall declare the public
> non-static member function uci::base::StringAccessor& operator=(const
> std::string&) of the "uci::base::StringAccessor" class.\]

##### Overload for C-String

Sets the value of the string that is accessed by this StringAccessor to
the value of the C-string (i.e., const char\*) on the right hand side
(rhs) of the assignment operator.

-   Signature:

StringAccessor& operator=(const char\* rhs)

-   Return:

A reference to this StringAccessor.

-   Parameters:

rhs: The C-string on the right hand side (rhs) of the assignment
operator whose contents are to be copied to the string accessed by this
StringAccessor.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-011145 \[An OMS C++ CAL API shall declare the public
> non-static member function uci::base::StringAccessor& operator=(const
> char\*) of the "uci::base::StringAccessor" class.\]
>
> CERT CXX-011143 \[An OMS C++ CAL API shall declare the public
> non-static member function uci::base::StringAccessor& operator=(const
> uci::base::StringAccessor&) of the "uci::base::StringAccessor"
> class.\]

#### Operator: operator &lt;qualifiedCxxPrimitiveName&gt;

Returns the value accessed by this Accessor.

-   Signature:

operator std::string() const

-   Return:

The value accessed by this Accessor.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value accessed by this Accessor.

-   Access:

Public.

> CERT CXX-011146 \[An OMS C++ CAL API shall declare the public const
> member function operator std::string() of the
> "uci::base::StringAccessor" class.\]

#### Default Constructor:

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s visibility is protected in order to enforce the use of the
accessor static create methods when constructing StringAccessors.

-   Signature:

StringAccessor()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
StringAccessor fails.

-   Access:

Protected.

> CERT CXX-005040 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::StringAccessor" class.\]

#### Default Copy Constructor:

This constructor will perform a deep copy of the string accessed by the
specified StringAccessor (rhs). As is discussed in Section 7, Accessor
Construction and Destruction, this constructor’s access is protected in
order to enforce the use of the StringAccessor static create methods
when constructing StringAccessor.

-   Signature:

StringAccessor(const StringAccessor& rhs)

-   Return:

N/A

-   Parameters:

rhs: The StringAccessor whose contents are used to initialize the
contents of the newly constructed StringAccessor.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
StringAccessor fails.

-   Access:

Protected.

> CERT CXX-005047 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::StringAccessor" class.\]

The SimpleList Template
-----------------------

A SimpleList is a container of accessors whose size (number of elements)
may be limited. Such limitation can be specified in the XSD
specification that declares a list with minLength, maxLength, and/or
length facets.

The SimpleList is realized by the C++ SimpleList template that is
modeled on the vector template from the C++ standard library.

> CERT CXX-005049 \[An OMS C++ CAL API shall define the "SimpleList"
> class taking the template parameters &lt;class T,
> uci::base::accessorType::AccessorType V&gt; in the "uci::base"
> namespace that publicly and singly inherits from "uci::base::Accessor"
> when the file "uci/base/SimpleList.h" is included.\]

For example, the following can be generated for the SimpleList template:

template&lt;class T, uci::base::accessorType::AccessorType V&gt;

class SimpleList : public uci::base::Accessor

### SimpleList Template Typedefs

-   size\_type: an unsigned integer type that can represent any
    non-negative “size” values that are associated with the SimpleList,
    e.g., the number of elements in the SimpleList.

> CERT CXX-005054 \[An OMS C++ CAL API shall define the public member
> type "size\_type" of the "uci::base::SimpleList" class equivalent to
> the type "size\_t".\]

For example,

typedef std::size\_t size\_type;

-   reference: a reference to a variable of the type of the elements
    stored in the SimpleList.

> CERT CXX-011156 \[An OMS C++ CAL API shall define the public member
> type "reference" of the "uci::base::SimpleList" class equivalent to
> the type "T&".\]

Since the template specifies this type in the template declaration,
i.e., T in the above declaration, this type can be declared to be a
reference to T, i.e.,

typedef T& reference;

-   const\_reference: a constant reference to a variable of the type of
    the elements stored in the SimpleList.

> CERT CXX-011157 \[An OMS C++ CAL API shall define the public member
> type "const\_reference" of the "uci::base::SimpleList" class
> equivalent to the type "const T&".\]

Since the template specifies this type in the template declaration,
i.e., T in the above declaration, the reference type can be declared to
be a constant reference to T, i.e., typedef const T& const\_reference;

### SimpleList Template Constants

-   Constant: MAXIMUM\_LENGTH

> CERT CXX-005056 \[An OMS C++ CAL API shall define the public static
> size\_type const member variable "MAXIMUM\_LENGTH" of the
> "uci::base::SimpleList" class.\]

The maximum length of a SimpleList. If the value returned by the
getMaximumLength() method equals this value, then neither the maxLength
or length Facets were specified in the XSD specification. Such lists are
simply limited by natural constraints.

-   Signature:

static const size\_type MAXIMUM\_LENGTH

Type: size\_type

-   Access:

Public.

Value: CAL specific

Implementation Note:

Since the C++ standard library includes the declaration of a constant
who value is the maximum value of std::size\_t, i.e., SIZE\_MAX, this
constant can be used as the value of MAXIMUM\_LENGTH, i.e.,

static const size\_type MAXIMUM\_LENGTH = SIZE\_MAX;

### The SimpleList Class Methods and Operators

#### Destructor: ~SimpleList

Destroys the SimpleList when the SimpleList goes out of scope or is
deleted.

-   Signature:

~SimpleList()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-012701 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::SimpleList" class.\]

#### Method: size

Returns the number of elements in the SimpleList that is accessed by
this SimpleList. This number is the number of actual objects held in the
SimpleList which is not necessarily equal to its storage capacity.

-   Signature:

size\_type size() const

throw()

-   Return:

Returns the number of elements in the SimpleList this SimpleList
provides access to

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005061 \[An OMS C++ CAL API shall declare the public const
> member function size\_type size() of the "uci::base::SimpleList" class
> as non-throwing.\]

#### Method: max\_size

Returns the maximum number of elements that the SimpleList can hold. The
value returned is the same that is returned by the getMaximumLength()
method. If not specified in the XSD, then this is the maximum size the
container can reach due to known system or library implementation
limitations, i.e., MAXIMUM\_LENGTH, but the container is by no means
guaranteed to be able to reach that size: it can still fail to allocate
storage at any point before that size is reached.

-   Signature:

size\_type max\_size() const

-   Return:

Returns the maximum number of elements that can be contained in the
SimpleList that is accessed by this SimpleList.

-   Parameters:

None.

-   Exceptions:

No exceptions may be thrown.

-   Access:

Public

> CERT CXX-005063 \[An OMS C++ CAL API shall declare the public const
> member function size\_type max\_size() of the "uci::base::SimpleList"
> class as non-throwing.\]

#### Method: min\_size

Returns the minimum number of elements that the SimpleList can hold. The
value returned is the same that is returned by the getMinimumLength()
method.

-   Signature:

size\_type min\_size() const

throw()

-   Return:

Returns the minimum number of elements that the SimpleList that is
accessed by this SimpleList can hold in order to be considered valid.
This method should return 0 (zero) if the minimum length Facet was not
specified in the XSD.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> GUID CXX-005065 \[This method should return 0 (zero) if the minimum
> length Facet was not specified in the XSD.\]
>
> CERT CXX-005066 \[An OMS C++ CAL API shall declare the public const
> member function size\_type min\_size() of the "uci::base::SimpleList"
> class as non-throwing.\]

#### Method: resize

Resizes the SimpleList that this accessed by the SimpleList such that
the SimpleList contains the specified number of elements. The parameter
newSize is the size of the SimpleList after it has been resized. If
newSize is smaller than the current container size, the SimpleList is
reduced to its first newSize elements, removing those beyond. Whether
those elements are destroyed or not is implementation dependent.

If newSize is greater than the current size of the SimpleList, then the
number of elements in the SimpleList is increased by inserting as many
elements at the end of the SimpleList as are needed in order to reach a
size of newSize. The newly added elements are value initialized
(initialized according to their type).

The type of element to insert is specified by the type argument (see
Section 9.3, The Accessor Type Constants). The use of this parameter
provides support for inheritable types. This type defaults to V which is
the template’s second template argument. If specified, this argument
must either be the accessor type associated with the Accessor specified
as the template’s first template argument, i.e., T, or must be an
accessor type associated with an Accessor that is derived from this
accessor, i.e., an accessor that is derived from T.

If newSize is greater than the current capacity of the SimpleList, an
automatic reallocation of the allocated storage space takes place (the
actual mechanism employed to perform this reallocation is implementation
dependent). Notice that this method changes the actual content of the
SimpleList by inserting or erasing elements from it.

-   Signature:

void resize(size\_type newSize,

uci::base::accessorType::AccessorType type = V)

-   Return:

None.

-   Parameters:

newSize: The size of the SimpleList after it has been resized.

type: The accessor type of the accessors that are to be inserted at the
end of the SimpleList if required to increase the size of the
SimpleList. This value defaults to V which is the template’s second
argument.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs resizing
the SimpleList.

-   Access:

Public

> CERT CXX-011200 \[An OMS C++ CAL API shall declare the public
> non-static member function void resize(size\_type,
> uci::base::accessorType::AccessorType = V) of the
> "uci::base::SimpleList" class.\]

#### Method: capacity

Returns the size of the allocated storage capacity of the SimpleList
accessed by this SimpleList. The capacity is expressed in terms of
elements. This capacity is not necessarily equal to the size of the
SimpleList. It can be equal to or greater than this size with the extra
space allowing it to accommodate future growth without the need to
reallocate on each insertion. Notice that this capacity does not suppose
a limit on the size of the SimpleList. When this capacity is exhausted
and more is needed, the capacity is automatically expanded by the
container (reallocating it storage space). The theoretical limit on the
size of a SimpleList is given by the method max\_size(). The capacity of
a SimpleList can be explicitly altered by calling the method reserve().

-   Signature:

size\_type capacity() const

throw()

-   Return:

The capacity of the SimpleList that is accessed by this SimpleList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005068 \[An OMS C++ CAL API shall declare the public const
> member function size\_type capacity() of the "uci::base::SimpleList"
> class as non-throwing.\]

#### Method: empty

Tests whether the SimpleList that is accessed by this SimpleList is
empty, returning true if the SimpleList is empty (size == 0) or false
otherwise. This method does not modify the container in any way. To
clear the contents of a SimpleList, see the method clear(). Note that
this method is equivalent to “size() == 0” but may offer better
performance due to implementation constraints.

-   Signature:

bool empty() const

throw()

-   Return:

A boolean indicating whether the SimpleList accessed by this SimpleList
is empty (true) or not (false).

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005070 \[An OMS C++ CAL API shall declare the public const
> member function bool empty() of the "uci::base::SimpleList" class as
> non-throwing.\]

#### Method: reserve

Request a change in the capacity of the SimpleList that is accessed by
this SimpleList such that the capacity is at least large enough to
contain newCapacity elements. The parameter newCapacity specifies the
new capacity of the SimpleList. If newCapacity is greater than the
SimpleList’s current capacity, then the SimpleList’s capacity will be
increased to the new capacity. This action may result in a reallocation
of the SimpleList’s storage using new storage whose capacity is equal to
or greater than newCapacity. The mechanism used to perform this
reallocation is implementation dependent. In all other cases, the method
does not cause a reallocation and the SimpleList’s capacity is not
affected. Note that this method has no effect on the size of the
SimpleList and cannot alter its elements.

-   Signature:

void reserve(size\_type newCapacity)

-   Return:

None.

-   Parameters:

newCapacity: The new capacity of the SimpleList accessed by this
SimpleList.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs modifying
the capacity of the SimpleList accessed by this SimpleList.

-   Access:

Public

> CERT CXX-011159 \[An OMS C++ CAL API shall declare the public
> non-static member function void reserve(size\_type) of the
> "uci::base::SimpleList" class.\]

#### Method: pop\_back

Removes the last element of the SimpleList accessed by this SimpleList,
effectively reducing the size of the SimpleList by one. This method
effectively destroys the removed element.

-   Signature:

void pop\_back()

throw()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

See GUID CXX-005077 following.

-   Access:

Public

> CERT CXX-011160 \[An OMS C++ CAL API shall declare the public
> non-static member function void pop\_back() of the
> "uci::base::SimpleList" class as non-throwing.\]
>
> GUID CXX-005077 \[This method should not throw an exception if the
> SimpleList accessed by this SimpleList is not empty, otherwise the
> method is a no-op.\]

#### Method: clear

Removes all elements from the SimpleList accessed by this SimpleList
leaving the SimpleList with a size of 0 (zero). A reallocation is not
guaranteed to happen, and the SimpleList’s capacity is not guaranteed to
change due to calling this method. All existing references to the
elements in the SimpleList are invalidated.

-   Signature:

void clear()

throw()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005084 \[An OMS C++ CAL API shall declare the public
> non-static member function void clear() of the "uci::base::SimpleList"
> class as non-throwing.\]

#### Method: getMaximumLength

Returns the “maximum length” of the SimpleList accessed by this
SimpleList. A SimpleList’s “maximum length” is the value of the list’s
“maxLength” Facet as specified in the OMS Schema Definition. Note that
the value returned is the same as that returned by max\_size().

-   Signature:

size\_type getMaximumLength() const

throw()

-   Return:

The maximum length that was specified for the SimpleList accessed by
this SimpleList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005091 \[An OMS C++ CAL API shall declare the public const
> member function size\_type getMaximumLength() of the
> "uci::base::SimpleList" class as non-throwing.\]
>
> GUID CXX-005093 \[If the SimpleList’s declaration did not contain a
> “maxLength” Facet declaration, then this method should return
> MAXIMUM\_LENGTH.\]

#### Method: getMinimumLength

Returns the “minimum length” of the SimpleList accessed by this
SimpleList. A SimpleList’s “minimum length” is the value of the
SimpleList’s “minLength” Facet as specified in the OMS Schema
Definition. Note that the value returned is the same as that returned by
min\_size().

-   Signature:

size\_type getMinimumLength() const

throw()

-   Return:

The minimum length that was specified for the SimpleList accessed by
this SimpleList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005100 \[An OMS C++ CAL API shall declare the public const
> member function size\_type getMinimumLength() of the
> "uci::base::SimpleList" class as non-throwing.\]
>
> GUID CXX-005102 \[If the SimpleList’s declaration did not contain a
> “minLength” Facet declaration, then this method should return 0
> (zero).\]

#### Method: getLength

Returns the “length” of the SimpleList accessed by this SimpleList. A
SimpleList’s “length” is the value of the SimpleList’s “length” Facet as
specified in the OMS Schema Definition.

-   Signature:

size\_type getLength() const

throw()

-   Return:

The length that was specified for the SimpleList accessed by this
SimpleList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005109 \[An OMS C++ CAL API shall declare the public const
> member function size\_type getLength() of the "uci::base::SimpleList"
> class as non-throwing.\]
>
> GUID CXX-005111 \[If the SimpleList’s declaration did not contain a
> “length” Facet declaration, then this method should return
> MAXIMUM\_LENGTH.\]

#### Operator: operator\[\]

##### Non-Const Variant

Returns a reference to the accessor found at position index in the
SimpleList accessed by this SimpleList. This operator does not perform
any bounds checking. The results of specifying an index that exceeds the
bounds of the SimpleList are undefined. See the member method at() for a
version of this operator that does perform bounds checking.

-   Signature:

reference operator\[\](size\_type index)

-   Return:

A reference to the accessor found at position index in the SimpleList
accessed by this SimpleList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

See GUID CXX-005118 following.

-   Access:

Public

> CERT CXX-011163 \[An OMS C++ CAL API shall declare the public
> non-static member function reference operator\[\](size\_type) of the
> "uci::base::SimpleList" class.\]
>
> GUID CXX-005118 \[This method should not throw an exception if the
> size of the SimpleList accessed by this SimpleList is greater than the
> specified index, otherwise the results of this method are undefined.\]

##### Const Variant

Returns a constant reference to the accessor found at position index in
the SimpleList accessed by this SimpleList. This operator does not
perform any bounds checking. The results of specifying an index that
exceeds the bounds of the SimpleList are undefined. See the member
method at() for a version of this operator that does perform bounds
checking.

-   Signature:

const\_reference operator\[\](size\_type index) const

-   Return:

A reference to the accessor found at position index in the SimpleList
accessed by this SimpleList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

See GUID CXX-005126 following.

-   Access:

Public

> CERT CXX-005125 \[An OMS C++ CAL API shall declare the public const
> member function const\_reference operator\[\](size\_type) of the
> "uci::base::SimpleList" class.\]
>
> GUID CXX-005126 \[This method should not throw an exception if the
> size of the SimpleList accessed by this SimpleList is greater than the
> specified index, otherwise the results of this method are undefined.\]

#### Method: at(size\_type index)

Returns a reference to the accessor found at position index in the
SimpleList accessed by this SimpleList. This method automatically checks
whether index is within the bounds of valid elements in the SimpleList,
throwing an exception if it is not (i.e., if index is greater than or
equal to the SimpleList’s size). This is in contrast with member
operator\[\], that does not perform any bounds checking.

-   Signature:

reference at(size\_type index)

-   Return:

A reference to the accessor found at position index in the SimpleList
accessed by this SimpleList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

uci::base::UCIException: Exception thrown if an out of bounds index is
specified.

-   Access:

Public

> CERT CXX-011178 \[An OMS C++ CAL API shall declare the public
> non-static member function reference at(size\_type) of the
> "uci::base::SimpleList" class.\]

#### Method: at(size\_type index) const

Returns a constant reference to the accessor found at position index in
the SimpleList accessed by this SimpleList. This method automatically
checks whether index is within the bounds of valid elements in the
SimpleList, throwing an exception if it is not (i.e., if index is
greater than or equal to the SimpleList’s size). This is in contrast
with member operator\[\], that does not perform any bounds checking.

-   Signature:

const\_reference at(size\_type index) const

-   Return:

A constant reference to the accessor found at position index in the
SimpleList accessed by this SimpleList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

uci::base::UCIException: Exception thrown if an out of bounds index is
specified.

-   Access:

Public

> CERT CXX-005139 \[An OMS C++ CAL API shall declare the public const
> member function const\_reference at(size\_type) of the
> "uci::base::SimpleList" class.\]

#### Method: push\_back

Adds a new element, value, to the end of the SimpleList accessed by this
SimpleList after its current last element. The content of value is
copied to the new element. This effectively increases the size of the
SimpleList by one, which causes an automatic reallocation of the
allocated storage space if, and only if, the new size of the SimpleList
surpasses the current capacity of the SimpleList.

-   Signature:

void push\_back(const\_reference value) const

-   Return:

None.

-   Parameters:

value: The value to be push on the end of the SimpleList accessed by
this SimpleList.

-   Exceptions:

uci::base::UCIException: Exception thrown if the push fails.

-   Access:

Public

> CERT CXX-011179 \[An OMS C++ CAL API shall declare the public
> non-static member function void push\_back(const\_reference) of the
> "uci::base::SimpleList" class.\]

#### Default Constructor:

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s access is protected in order to enforce the use of the
SimpleList accessor when constructing SimpleLists.

-   Signature:

SimpleList()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
SimpleList fails.

-   Access:

Protected

> CERT CXX-005152 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::SimpleList" class.\]

#### Default Copy Constructor:

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s access is protected in order to enforce the use of the
SimpleList when constructing SimpleLists.

-   Signature:

SimpleList(const SimpleList&lt;T,V&gt;& rhs)

-   Return:

N/A

-   Parameters:

rhs: The SimpleList whose contents are used to initialize the contents
of the newly constructed SimpleList.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
SimpleList fails.

-   Access:

Protected

> CERT CXX-005159 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::SimpleList" class.\]

#### Operator: operator=

Performs a deep copy of the contents of the SimpleList that is accessed
by the specified SimpleList (rhs) and sets the contents of the
SimpleList that is accessed by this SimpleList to the resulting copy. As
stated in Section 7, Accessor Construction and Destruction, this
operator’s access is protected in order to enforce the use of the
SimpleList factories when constructing SimpleLists.

-   Signature:

SimpleList&lt;T,V&gt;& operator=(const SimpleList&lt;T,V&gt;& rhs)

-   Return:

A reference to this SimpleList.

-   Parameters:

rhs: The SimpleList on the right hand side (rhs) of the assignment
operator which provides access to the SimpleList whose contents are to
be assigned to the SimpleList that is accessed by this SimpleList.

-   Exceptions:

None

-   Access:

Protected

> CERT CXX-011180 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the "uci::base::SimpleList" class.\]

The BoundedList Template
------------------------

A BoundedList is a container of accessors whose size (number of
elements) may be bounded. Such bounding will be specified in the XSD
specification using the minOccurs and maxOccurs declarations.

The BoundedList is realized by the C++ BoundedList template that is
modeled on the vector template from the C++ standard library.

> CERT CXX-005168 \[An OMS C++ CAL API shall define the "BoundedList"
> class taking the template parameters &lt;class T,
> uci::base::accessorType::AccessorType V&gt; in the "uci::base"
> namespace that publicly and singly inherits from "uci::base::Accessor"
> when the file "uci/base/BoundedList.h" is included.\]

The class T template parameter should be the name of an accessor class,
i.e., some class that is derived from the Accessor class (see “The
Accessor Class” section).

The uci::base::accessorType::AccessorType V template parameter should be
the accessor type (see “The Accessor Type Constants” section) that is
associated with the Accessor class specified for the class T template
argument.

For example, the following can be generated for the BoundedList
template:

template&lt;class T, uci::base::accessorType::AccessorType V&gt;

class BoundedList : public uci::base::Accessor

### The BoundedList Typedefs

size\_type: an unsigned integer type that can represent any non-negative
“size” value that is associated with the BoundedList, e.g., the number
of elements in the BoundedList.

> CERT CXX-005172 \[An OMS C++ CAL API shall define the public member
> type "size\_type" of the "uci::base::BoundedList" class equivalent to
> the type "size\_t".\]

For example, this type can be declared to be std::size\_t, i.e.,

typedef std::size\_t size\_type;

reference: a reference to a variable of the type of the elements stored
in the BoundedList.

> CERT CXX-011183 \[An OMS C++ CAL API shall define the public member
> type "reference" of the "uci::base::BoundedList" class equivalent to
> the type "T&".\]

Since the template specifies this type in the template declaration,
i.e., T in the above declaration, this type can be declared to be a
reference to T, i.e.,

typedef T& reference;

const\_reference: a constant reference to a variable of the type of the
elements stored in the BoundedList.

> CERT CXX-011184 \[An OMS C++ CAL API shall define the public member
> type "const\_reference" of the "uci::base::BoundedList" class
> equivalent to the type "const T&".\]

Since the template specifies this type in the template declaration,
i.e., T in the above declaration, the reference type can be declared to
be a constant reference to T, i.e.,

typedef const T& const\_reference;

### The BoundedList Template Constants

Constant: UNBOUNDED\_BOUND

The maximum size of a BoundedList. If the value returned by the
getMaximumOccurs() method equals this value, then no bounds were
specified in the XSD specification and this list is bounded simply by
natural constraints.

-   Signature:

static const size\_type UNBOUNDED\_BOUND

Type:

size\_type

-   Access:

Public.

Value: CAL specific

Implementation Note:

Since the C++ standard library includes the declaration of a constant
who value is the maximum value of std::size\_t, i.e., SIZE\_MAX, this
constant can be used as the value of UNBOUNDED\_BOUND, i.e.,

static const unsigned long UNBOUNDED\_BOUND = SIZE\_MAX

> CERT CXX-005174 \[An OMS C++ CAL API shall define the public static
> size\_type const member variable "UNBOUNDED\_BOUND" of the
> "uci::base::BoundedList" class.\]

### The BoundedList Template Methods and Operators

#### Destructor: ~BoundedList

Destroys the BoundedList when the BoundedList goes out of scope or is
deleted

-   Signature:

~BoundedList()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-012702 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::BoundedList" class.\]

#### Method: size

Returns the number of elements in the BoundedList that is accessed by
this BoundedList. This number is the number of actual objects held in
the BoundedList which is not necessarily equal to its storage capacity.

-   Signature:

size\_type size() const

throw()

-   Return:

Returns the number of elements in the BoundedList this BoundedList
provides access to.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005179 \[An OMS C++ CAL API shall declare the public const
> member function size\_type size() of the "uci::base::BoundedList"
> class as non-throwing.\]

#### Method: max\_size

Returns the maximum number of elements that the BoundedList that can
hold. The value returned is the same that is returned by the
getMaximumOccurs() method. If not specified in the schema, then this is
the maximum size the container can reach due to known system or library
implementation limitations, i.e., UNBOUNDED\_BOUND, but the container is
by no means guaranteed to be able to reach that size: it can still fail
to allocate storage at any point before that size is reached.

-   Signature:

size\_type max\_size() const

-   Return:

Returns the maximum number of elements that can be contained in the
BoundedList that is accessed this BoundedList.

-   Parameters:

None.

-   Exceptions:

No exceptions may be thrown.

-   Access:

Public

> CERT CXX-005181 \[An OMS C++ CAL API shall declare the public const
> member function size\_type max\_size() of the "uci::base::BoundedList"
> class as non-throwing.\]

#### Method: min\_size

Returns the minimum number of elements that the BoundedList can hold.
The value returned is the same that is returned by the
getMinimumOccurs() method.

-   Signature:

size\_type min\_size() const

-   Return:

Returns the minimum number of elements that the BoundedList that is
accessed this BoundedList can hold in order to be considered valid.

-   Parameters:

None.

-   Exceptions:

Exceptions may be thrown.

-   Access:

Public

> GUID CXX-005183 \[This method should return 0 (zero) if the specified
> “minimum occurs” attribute was not specified in the XSD.\]
>
> CERT CXX-005184 \[An OMS C++ CAL API shall declare the public const
> member function size\_type min\_size() of the "uci::base::BoundedList"
> class as non-throwing.\]

#### Method: resize

Resizes the BoundedList that this accessed by the BoundedList such that
the BoundedList contains the specified number of elements. The parameter
newSize is the size of the BoundedList after it has been resized. If
newSize is smaller than the current container size, the BoundedList is
reduced to its first newSize elements, removing those beyond. Whether
those elements are destroyed or not is implementation dependent.

If newSize is greater than the current size of the BoundedList, then the
number of elements in the BoundedList is increased by inserting as many
elements at the end of the BoundedList as are needed in order to reach a
size of newSize. The newly added elements are value initialized
(initialized according to their type).

The type of element to insert is specified by the type argument (see
Section 9.3, The Accessor Type Constants). The use of this parameter
provides support for inheritable types. This type defaults to V which is
the template’s second template argument. If specified, this argument
must either be the accessor type associated with the Accessor specified
as the template’s first template argument, i.e., T, or must be an
accessor type associated with an Accessor that is derived from this
accessor, i.e., an accessor that is derived from T.

If newSize is greater than the current capacity of the BoundedList, an
automatic reallocation of the allocated storage space takes place (the
actual mechanism employed to perform this reallocation is implementation
dependent). Notice that this method changes the actual content of the
BoundedList by inserting or erasing elements from it.

-   Signature:

void resize(size\_type newSize,

uci::base::accessorType::AccessorType type = V)

-   Return:

None.

-   Parameters:

newSize: The size of the BoundedList after it has been resized.

type: The accessor type of the accessors that are to be inserted at the
end of the BoundedList if required to increase the size of the
BoundedList. This value defaults to V which is the template’s second
argument.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs resizing
the BoundedList.

-   Access:

Public

> CERT CXX-011201 \[An OMS C++ CAL API shall declare the public
> non-static member function void resize(size\_type,
> uci::base::accessorType::AccessorType = V) of the
> "uci::base::BoundedList" class.\]

#### Method: capacity

Returns the size of allocated storage capacity of the BoundedList
accessed by this BoundedList. The capacity is expressed in terms of
elements. This capacity is not necessarily equal to the size of the
BoundedList. It can be equal to or greater than this size with the extra
space allowing it to accommodate future growth without the need to
reallocate on each insertion. Notice that this capacity does not suppose
a limit on the size of the BoundedList. When this capacity is exhausted
and more is needed, the capacity is automatically expanded by the
container (reallocating it storage space). The theoretical limit on the
size of a BoundedList is given by the method max\_size(). The capacity
of a BoundedList can be explicitly altered by calling the method
reserve().

-   Signature:

size\_type capacity() const

throw()

-   Return:

The capacity of the BoundedList that is accessed by this BoundedList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005187 \[An OMS C++ CAL API shall declare the public const
> member function size\_type capacity() of the "uci::base::BoundedList"
> class as non-throwing.\]

#### Method: empty

Tests whether the BoundedList that is accessed by this BoundedList is
empty, returning true if the BoundedList is empty (size == 0) or false
otherwise. This method does not modify the container in any way. To
clear the contents of a BoundedList, see the method clear(). Note that
this method is equivalent to “size() == 0” but may offer better
performance due to implementation constraints.

-   Signature:

bool empty() const

throw()

-   Return:

A boolean indicating whether the BoundedList accessed by this
BoundedList is empty (true) or not (false).

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005195 \[An OMS C++ CAL API shall declare the public const
> member function bool empty() of the "uci::base::BoundedList" class as
> non-throwing.\]

#### Method: reserve

Request a change in the capacity of the BoundedList that is accessed by
this BoundedList such that the capacity is at least large enough to
contain newCapacity elements. The parameter newCapacity specifies the
new capacity of the BoundedList. If newCapacity is greater than the
BoundedList’s current capacity, then the BoundedList’s capacity will be
increased to the new capacity. This action may result in a reallocation
of the BoundedList’s storage using new storage whose capacity is equal
to or greater than newCapacity. The mechanism used to perform this
reallocation is implementation dependent. In all other cases, the method
does not cause a reallocation and the BoundedList’s capacity is not
affected. Note that this method has no effect on the size of the
BoundedList and cannot alter its elements.

-   Signature:

void reserve(size\_type newCapacity)

-   Return:

None.

-   Parameters:

newCapacity: The new capacity of the BoundedList accessed by this
BoundedList.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs modifying
the capacity of the BoundedList accessed by this BoundedList.

-   Access:

Public

> CERT CXX-011186 \[An OMS C++ CAL API shall declare the public
> non-static member function void reserve(size\_type) of the
> "uci::base::BoundedList" class.\]

#### Method: pop\_back

Removes the last element of the BoundedList accessed by this BoundedList
effectively reducing the size of the BoundedList by one. This method
effectively destroys the removed element.

-   Signature:

void pop\_back()

throw()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

See GUID CXX-005209 following.

-   Access:

Public

> CERT CXX-011187 \[An OMS C++ CAL API shall declare the public
> non-static member function void pop\_back() of the
> "uci::base::BoundedList" class.\]
>
> GUID CXX-005209 \[This method should not throw an exception if the
> BoundedList accessed by this BoundedList is not empty, otherwise the
> method is a no-op.\]

#### Method: clear

Removes all elements from the BoundedList accessed by this BoundedList
leaving the BoundedList with a size of 0 (zero). A reallocation is not
guaranteed to happen, and the BoundedList’s capacity is not guaranteed
to change due to calling this method. All existing references to the
elements in the BoundedList are invalidated.

-   Signature:

void clear()

throw()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005216 \[An OMS C++ CAL API shall declare the public
> non-static member function void clear() of the
> "uci::base::BoundedList" class as non-throwing.\]

#### Method: getMaximumOccurs

Returns the “maximum occurs” attribute of the BoundedList accessed by
this BoundedList. A BoundedList’s “maximum occurs” is the BoundedList’s
“maxOccurs” attribute as specified in the OMS Schema Definition. Note
that the value returned is the same as that returned by max\_size().

-   Signature:

size\_type getMaximumOccurs() const

throw()

-   Return:

The maximum occurs that was specified for the BoundedList accessed by
this BoundedList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> GUID CXX-005223 \[If the BoundedList’s declaration did not contain a
> “maxOccurs” attribute declaration, then this method should return
> UNBOUNDED\_BOUND.\]
>
> CERT CXX-005224 \[An OMS C++ CAL API shall declare the public const
> member function size\_type getMaximumOccurs() of the
> "uci::base::BoundedList" class as non-throwing.\]

#### Method: getMinimumOccurs

Returns the “minimum occurs” of the BoundedList accessed by this
BoundedList. A BoundedList’s “minimum occurs” is the BoundedList’s
“minOccurs” attribute as specified in the OMS Schema Definition.

-   Signature:

size\_type getMinimumOccurs() const

throw()

-   Return:

The minimum occurs for the BoundedList accessed by this BoundedList.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> GUID CXX-005232 \[If the BoundedList’s declaration did not contain a
> “minOccurs” declaration, then this method should return 0 (zero).\]
>
> CERT CXX-005233 \[An OMS C++ CAL API shall declare the public const
> member function size\_type getMinimumOccurs() of the
> "uci::base::BoundedList" class as non-throwing.\]

#### Operator: operator\[\]

##### Non-Const Variant

Returns a reference to the accessor found at position index in the
BoundedList accessed by this BoundedList. This operator does not perform
any bounds checking. The results of specifying an index that exceeds the
bounds of the BoundedList are undefined. See the member method at() for
a version of this operator that does perform bounds checking.

-   Signature:

reference operator\[\](size\_type index)

-   Return:

A reference to the accessor found at position index in the BoundedList
accessed by this BoundedList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

See GUID CXX-005241 following.

-   Access:

Public

> GUID CXX-005241 \[This method should not throw an exception if the
> size of the BoundedList accessed by this BoundedList is greater than
> the specified index; otherwise the results of this method are
> undefined.\]
>
> CERT CXX-011189 \[An OMS C++ CAL API shall declare the public
> non-static member function reference operator\[\](size\_type) of the
> "uci::base::BoundedList" class.\]

##### Const Variant

Returns a constant reference to the accessor found at position index in
the BoundedList accessed by this BoundedList. This operator does not
perform any bounds checking. The results of specifying an index that
exceeds the bounds of the BoundedList are undefined. See the member
method at() for a version of this operator that does perform bounds
checking.

-   Signature:

const\_reference operator\[\](size\_type index) const

-   Return:

A reference to the accessor found at position index in the BoundedList
accessed by this BoundedList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

See GUID CXX-005248 following.

-   Access:

Public

> GUID CXX-005248 \[This method should not throw an exception if the
> size of the BoundedList accessed by this BoundedList is greater than
> the specified index; otherwise the results of this method are
> undefined.\]
>
> CERT CXX-005249 \[An OMS C++ CAL API shall declare the public const
> member function const\_reference operator\[\](size\_type) of the
> "uci::base::BoundedList" class.\]

#### Method: at

##### Non-Const Variant

Returns a reference to the accessor found at position index in the
BoundedList accessed by this BoundedList. This method automatically
checks whether index is within the bounds of valid elements in the
BoundedList, throwing an exception if it is not (i.e., if index is
greater than or equal to the BoundedList’s size). This is in contrast
with member operator\[\], that does not perform any bounds checking.

-   Signature:

reference at(size\_type index)

-   Return:

A reference to the accessor found at position index in the BoundedList
accessed by this BoundedList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

uci::base::UCIException: Exception thrown if an out of bounds index is
specified.

-   Access:

Public

> CERT CXX-011190 \[An OMS C++ CAL API shall declare the public
> non-static member function reference at(size\_type) of the
> "uci::base::BoundedList" class.\]

##### Const Variant

Returns a constant reference to the accessor found at position index in
the BoundedList accessed by this BoundedList. This method automatically
checks whether index is within the bounds of valid elements in the
BoundedList, throwing an exception if it is not (i.e., if index is
greater than or equal to the BoundedList’s size). This is in contrast
with member operator\[\], that does not perform any bounds checking.

-   Signature:

const\_reference at(size\_type index) const

-   Return:

A constant reference to the accessor found at position index in the
BoundedList accessed by this BoundedList.

-   Parameters:

index: The index of the element whose reference is to be returned.
Indexing starts at 0 (zero).

-   Exceptions:

uci::base::UCIException: Exception thrown if an out of bounds index is
specified.

-   Access:

Public

> CERT CXX-005262 \[An OMS C++ CAL API shall declare the public const
> member function const\_reference at(size\_type) of the
> "uci::base::BoundedList" class.\]

#### Method: push\_back

##### Overload for Const Reference

Adds a new element, value, to the end of the BoundedList accessed by
this BoundedList after its current last element. The content of value is
copied to the new element. This effectively increases the size of the
BoundedList by one, which causes an automatic reallocation of the
allocated storage space if, and only if, the new size of the BoundedList
surpasses the current capacity of the BoundedList.

-   Signature:

void push\_back(const\_reference value)

-   Return:

None.

-   Parameters:

value: The value to be push on the end of the BoundedList accessed by
this BoundedList.

-   Exceptions:

uci::base::UCIException: Exception thrown if the push fails.

-   Access:

Public

> CERT CXX-011191 \[An OMS C++ CAL API shall declare the public
> non-static member function void push\_back(const\_reference) of the
> "uci::base::BoundedList" class.\]

##### Template Overload for Value

Adds a new element, value, to the end of the BoundedList accessed by
this BoundedList after its current last element. The content of value is
copied to the new element. This effectively increases the size of the
BoundedList by one, which causes an automatic reallocation of the
allocated storage space if, and only if, the new size of the BoundedList
surpasses the current capacity of the BoundedList.

This function participates in overload resolution only when pushing back
primitive values, enum values, and const char\* values to lists that
support them.

-   Signature:

template &lt;typename U&gt; void push\_back(U value)

-   Return:

None.

-   Parameters:

value: The value to be push on the end of the BoundedList accessed by
this BoundedList.

-   Exceptions:

uci::base::UCIException: Exception thrown if the push fails.

-   Access:

Public

> CERT CXX-012971 \[An OMS C++ CAL API shall declare the public
> non-static member function template &lt;typename U&gt; void
> push\_back(U) of the "uci::base::BoundedList" class that does not
> participate in overload resolution unless U is assignable to reference
> and U is not a reference type.\]

Programming note: This overload and the next overload only participate
in overload resolution if the value parameter is assignable to the
reference type. (See the typedefs section for more details on the
reference type.) This is done using SFINAE (substitution failure is not
an error) techniques. For example, the following code can be used to
disable the function if the value parameter is not assignable to the
reference type:

private:

template &lt;typename U, U&gt; struct CheckType;

template &lt;typename U, typename W&gt; class IsAssignable

{

template &lt;typename To, typename From&gt; static int
Check(CheckType&lt;To &(To::\*)(From), &To::operator= &gt;\*);

template &lt;typename, typename&gt; static char Check(...);

public:

static const bool VALUE = sizeof(Check&lt;U, W&gt;(0)) == sizeof(int);

};

template &lt;typename U&gt; struct IsReference { static const bool VALUE
= false; };

template &lt;typename U&gt; struct IsReference&lt;U&&gt; { static const
bool VALUE = true; };

template &lt;bool B, typename = void&gt; struct EnableIf { };

template &lt;typename U&gt; struct EnableIf&lt;true, U&gt; { typedef U
Type; };

public:

template &lt;typename U&gt; typename EnableIf&lt;IsAssignable&lt;T,
U&gt;::VALUE && !IsReference&lt;U&gt;::VALUE&gt;::Type push\_back(U
value)

{

const size\_type index = size();

resize(index + 1);

operator\[\](index) = value;

}

template &lt;typename U&gt; typename EnableIf&lt;IsAssignable&lt;T,
const U&&gt;::VALUE&gt;::Type push\_back(const U &value)

{

const size\_type index = size();

resize(index + 1);

operator\[\](index) = value;

}

##### Template Overload for Const Reference

Adds a new element, value, to the end of the BoundedList accessed by
this BoundedList after its current last element. The content of value is
copied to the new element. This effectively increases the size of the
BoundedList by one, which causes an automatic reallocation of the
allocated storage space if, and only if, the new size of the BoundedList
surpasses the current capacity of the BoundedList.

This function participates in overload resolution only when pushing back
std:strings or const references to lists that support them.

-   Signature:

template &lt;typename U&gt; void push\_back(const U &value)

-   Return:

None.

-   Parameters:

value: The value to be push on the end of the BoundedList accessed by
this BoundedList.

-   Exceptions:

uci::base::UCIException: Exception thrown if the push fails.

-   Access:

Public

> CERT CXX-013010 \[An OMS C++ CAL API shall declare the public
> non-static member function template &lt;typename U&gt; void
> push\_back(const U&) of the "uci::base::BoundedList" class that does
> not participate in overload resolution unless const U& is assignable
> to reference.\]

#### Default Constructor:

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s access is protected in order to enforce the use of the
BoundedList accessor factory when constructing BoundedLists.

-   Signature:

BoundedList()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
BoundedList fails.

-   Access:

Protected

> CERT CXX-005275 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::BoundedList" class.\]

#### Default Copy Constructor:

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s access is protected in order to enforce the use of the
BoundedList when constructing BoundedLists.

-   Signature:

BoundedList(const BoundedList&lt;T,V&gt;& rhs)

-   Return:

N/A

-   Parameters:

rhs: The BoundedList whose contents are used to initialize the contents
of the newly constructed BoundedList.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
BoundedList fails.

-   Access:

Protected

> CERT CXX-005282 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::BoundedList" class.\]

#### Operator: operator=

Performs a deep copy of the contents of the BoundedList that is accessed
by the specified BoundedList (rhs) and sets the contents of the
BoundedList that is accessed by this BoundedList to the resulting copy.
As stated in Section 7, Accessor Construction and Destruction, this
operator’s access is protected in order to enforce the use of the
BoundedList factories when constructing BoundedLists.

-   Signature:

BoundedList&lt;T,V&gt;& operator=(const BoundedList&lt;T,V&gt;& rhs)

-   Return:

A reference to this BoundedList.

-   Parameters:

rhs: The BoundedList on the right hand side (rhs) of the assignment
operator which provides access to the BoundedList whose contents are to
be assigned to the BoundedList that is accessed by this BoundedList.

-   Exceptions:

None.

-   Access:

Protected

> CERT CXX-011192 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the "uci::base::BoundedList" class.\]

The Universally Unique Identification (UUID) Class
--------------------------------------------------

All elements on an OMS-compliant Platform are identified using
universally unique identifiers, including Services and Subsystems. The
UUID class provides access to the universally unique identifiers that
may be contained within an OMS Message or that may be returned by some
method invocation. The C++ UUID class is specified in this section.

This document uses the terms “UUID” when referring to a universally
unique identifier, “UUID class” when referring to the C++ realization of
the UUID C++ class, and “UUID” when referring to an instance of the UUID
class.

The types of universally unique identifier (UUID) that are used by OMS
is specified by the Internet Engineering Task Force (IETF) Request for
Comments (RFC) 4122. The RFC 4122 specification specifies a UUID as
being composed of 32 hexadecimal digits (0-9A-Fa-f).

The RFC 4122 specification provides for several different variants of a
UUID.

> GUID CXX-005289 \[All UUIDs used in OMS compliant systems should be
> the current variant.\]

In addition, the RFC 4122 specification provides for several different
versions of a UUID.

> GUID CXX-005290 \[All UUIDs used in OMS compliant systems should be
> time-based UUIDs (also known as version 1 UUIDs), MD5 hash UUIDs (also
> known as version 3), and/or pseudorandom UUIDs (also known as version
> 4).\]
>
> GUID CXX-005291 \[The format of a string that specifies a time-based
> UUID should be as follows:
>
> uuid:
> &lt;timeLow&gt;-&lt;timeMid&gt;-&lt;timeHigh&Version&gt;-&lt;clockSeq&Reserved&gt;-
>
> &lt;clockSeqLow&gt;-&lt;node&gt;
>
> timeLow:
> &lt;hexOctet&gt;&lt;hexOctet&gt;&lt;hexOctet&gt;&lt;hexOctet&gt;
>
> timeMid: &lt;hexOctet&gt;&lt;hexOctet&gt;
>
> timeHigh&Version: &lt;hexOctet&gt;&lt;hexOctet&gt;
>
> clockSeq&Reserved: &lt;hexOctet&gt;
>
> clockSeqLow: &lt;hexOctet&gt;
>
> node:
> &lt;hexOctet&gt;&lt;hexOctet&gt;&lt;hexOctet&gt;&lt;hexOctet&gt;&lt;hexOctet&gt;&lt;hexOctet&gt;
>
> hexOctet: &lt;hexDigit&gt;&lt;hexDigit&gt;
>
> hexDigit: 0 / 1 / 2 / 3 / 4 / 5 / 6 / 7 / 8 / 9/
>
> a / b / c / d / e / f
>
> A / B / C / D / E / F\]

The following is an example of a current, time-based UUID string.

550E8400-E29B-10D4-7716-446655440000

From the perspective of the UUID class, a UUID is an ordered container
of octets, each octet being an 8-bit unsigned integer. The hexadecimal
digits of a UUID are stored in these octets pairwise, two digits per
octet, with the most significant hexadecimal digit being stored in the
most significant 4 bits of the octet and the least significant
hexadecimal digit being stored in the least significant 4 bits of the
octet. The hexadecimal digits are ordered in the container in network
ordering, i.e., big endian ordering, with the first two most significant
hexadecimal digits of the UUID stored in the container’s first octet,
the next two most significant hexadecimal digits of the UUID stored in
the container’s second octet, and so on until 32 hexadecimal digits are
stored in the container’s 16 octets. The methods of the UUID class are
based on this perspective.

The UUID class provides access to these UUIDs.

### The UUID Class

> CERT CXX-005296 \[An OMS C++ CAL API shall define the "UUID" class in
> the "uci::base" namespace when the file "uci/base/UUID.h" is
> included.\]

For example, the following can be generated:

class UUID

m\_numberOfOctets: The number of octets used to specify a UUID. This
constant also specifies the size of the Octets vector (see Section
9.8.1.1, The UUID Class Data Types).

> CERT CXX-005300 \[An OMS C++ CAL API shall define the public static
> const size\_t member variable "m\_numberOfOctets" of the
> "uci::base::UUID" class with the value 16.\]

m\_sizeOfNodeAddress: The number of bytes used to specify a node
address.

> CERT CXX-012548 \[An OMS C++ CAL API shall define the public static
> const size\_t member variable "m\_sizeOfNodeAddress" of the
> "uci::base::UUID" class with the value 6.\]

#### The UUID Class Data Types

Octet: The Octet is the data type used to hold two hexadecimal digits,
each represented using 4 bits.

> CERT CXX-005307 \[An OMS C++ CAL API shall define the public member
> type "Octet" of the "uci::base::UUID" class equivalent to the type
> "uint8\_t".\]

The Octet is declared to be of a single atomic type as opposed to a
container of types (array, vector, etc.) so that its usage better aligns
with the UUID specification. The most significant hexadecimal digit (4
bits) is stored in the most significant 4 bits of the Octet while the
least significant hexadecimal digit (4 bits) is stored in the least
significant 4 bits of the Octet.

Octets: Octets is a vector containing a set of octet values. This vector
can be used to set and get the value of a UUID.

The octets are ordered in the vector in network ordering, i.e., big
endian ordering, such that the most significant octet is found in the
first element of the vector, i.e., octets\[0\], and the least
significant octet is found in the last element of the vector, i.e.,
octets\[m\_numberOfOctets – 1\].

> CERT CXX-005310 \[An OMS C++ CAL API shall define the public member
> type "Octets" of the "uci::base::UUID" class equivalent to the type
> "std::vector&lt;Octet&gt;".\]

For example, the following can be generated:

typedef std::vector&lt;Octet&gt; Octets

NodeAddress: The node address is used to uniquely identify the
processing node on a network of processing nodes that created the UUID.
In many cases, this is the MAC address of the device used by the
processor that created this UUID. The NodeAddress is realized as a
vector of 8-bit unsigned integer values. The data is ordered in the
vector in network ordering, i.e., big endian ordering, such that the
most significant unsigned 8-bit integer of the node address is found in
the first element of the vector, i.e., nodeAddress\[0\], and the least
significant unsigned 8-bit integer of the node address is found in the
last element of the vector, i.e., nodeAddress\[m\_sizeOfNodeAddress –
1\].

> CERT CXX-005311 \[An OMS C++ CAL API shall define the public member
> type "NodeAddress" of the "uci::base::UUID" class equivalent to the
> type "std::vector&lt;uint8\_t&gt;".\]

For example, the following can be generated:

typedef std::vector&lt;uint8\_t&gt; NodeAddress

Timestamp: The timestamp is used to record the current time.

> CERT CXX-005312 \[An OMS C++ CAL API shall define the public member
> type "Timestamp" of the "uci::base::UUID" class equivalent to the type
> "uint64\_t".\]
>
> GUID CXX-005313 \[The bytes should be ordered within the timestamp in
> network ordering, i.e., big endian ordering.\]

ClockSequence: The clock sequence is the additional sequence that is
combined with the current timestamp in order to produce a unique time.

> CERT CXX-005314 \[An OMS C++ CAL API shall define the public member
> type "ClockSequence" of the "uci::base::UUID" class equivalent to the
> type "uint16\_t".\]
>
> GUID CXX-005315 \[The bytes should be ordered within the clock
> sequence in network ordering, i.e., big endian ordering.\]

Variant: The Variant is an enumeration of the UUID variants as specified
in RFC 4122. A UUID variant specifies the layout of the octets contained
in the UUID.

> CERT CXX-005316 \[An OMS C++ CAL API shall define the public member
> enum "Variant" of the "uci::base::UUID" class with the enumerators
> "variantNCS", "variantMicrosoft", "variantCurrent", "variantFuture",
> and "variantUnknown" in accordance with RFC 4122.\]

Version: The Version is an enumeration of the UUID versions as specified
in RFC 4122. The version specifies how the data contained within the
UUID is generated and interpreted.

> CERT CXX-005317 \[An OMS C++ CAL API shall define the public member
> enum "Version" of the "uci::base::UUID" class with the enumerators
> “versionNil”, "versionTimeBased", "versionDceSecurity",
> "versionNameBasedMD5", "versionRandomNumber", "versionNameBasedSHA1",
> and "versionUnknown" in accordance with RFC 4122.\]

ValueUUID: The ValueUUID is a 128-bit data type that contains the value
of the UUID expressed as two 64-bit values.

> CERT CXX-005318 \[An OMS C++ CAL API shall define the public member
> struct "ValueUUID" of the "uci::base::UUID" class.\]

mostSignificantBits: The most significant 64 bits, i.e., the most
significant 16 hexadecimal digits, of the UUID. The hexadecimal digits
are stored in network ordering, i.e., big endian ordering.

> CERT CXX-005319 \[An OMS C++ CAL API shall define the public uint64\_t
> member variable "mostSignificantBits" of the
> "uci::base::UUID::ValueUUID" class.\]

leastSignificantBits: The least significant 64 bits, i.e., the least
significant 16 hexadecimal digits, of the UUID. The hexadecimal digits
are stored in network ordering, i.e., big endian ordering.

> CERT CXX-005320 \[An OMS C++ CAL API shall define the public uint64\_t
> member variable "leastSignificantBits" of the
> "uci::base::UUID::ValueUUID" class.\]

#### The UUID Class Methods and Operators

##### Method: fromString

Creates a UUID from a stringified UUID formatted as specified in RFC
4122.

-   Signature:

static uci::base::UUID fromString(const std::string& stringifiedUUID)

-   Return:

A UUID with the value represented by the stringified UUID.

-   Parameters:

stringifiedUUID: A UUID expressed as a string as specified in RFC 4122.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs parsing
the stringified UUID or if the provided stringifiedUUID results in a
UUID that does not conform to RFC 4122.

-   Access:

Public

> CERT CXX-011150 \[An OMS C++ CAL API shall declare the public static
> member function uci::base::UUID fromString(const std::string&) of the
> "uci::base::UUID" class.\]

##### Method: fromOctets

Creates a UUID from a vector of octets.

-   Signature:

static uci::base::UUID fromOctets (const Octets& octets)

-   Return:

A UUID with the value represented by the octets.

-   Parameters:

octets: A UUID expressed as a vector of octets that is used to create
the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs or if the
provided octets results in a UUID that does not conform to RFC 4122.

-   Access:

Public

> CERT CXX-011152 \[An OMS C++ CAL API shall declare the public static
> member function uci::base::UUID fromOctets(const Octets&) of the
> "uci::base::UUID" class.\]

##### Method: generateUUID

Generates a UUID that conforms to RFC 4122 version 1 or version 4.

-   Signature:

static uci::base::UUID generateUUID()

-   Return:

The generated RFC 4122 version 1 or version 4 UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
generating the UUID.

-   Access:

Public

> CERT CXX-011165 \[An OMS C++ CAL API shall declare the public static
> member function uci::base::UUID generateUUID() of the
> "uci::base::UUID" class.\]

##### Method: getNamespaceUUID

Returns the UUID that is used in creating a Version 3 UUID for the
method that does not provide the namespace parameter (see Section
9.8.1.2.6)

-   Signature:

uci::base::UUID getNamespaceUUID()

-   Return:

The UUID that can be used as the namespace for the
createVersion3UUID(const UUID &ns, const std::string& name) method to
create OMS Platform-specific, consistent UUIDs.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the namespace UUID.

-   Access:

Public

> CERT CXX-012574 \[An OMS C++ CAL API shall declare the public static
> member function uci::base::UUID getNamespaceUUID() of the
> "uci::base::UUID" class.\]

##### Method: createVersion3UUID

###### Overload for Namespace and Name

Creates a UUID that conforms to RFC 4122 version 3 from the namespace
UUID and string name.

-   Signature:

static uci::base::UUID createVersion3UUID(const uci::base::UUID &ns,
const std::string& name) const

-   Return:

The created RFC 4122 version 3 UUID.

-   Parameters:

ns: The namespace UUID used to create the version 3 UUID.

name: The string name encoded in UTF-8 used to create the version 3
UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs creating
the UUID.

-   Access:

Public

> CERT CXX-012587 \[An OMS C++ CAL API shall declare the public static
> member function uci::base::UUID createVersion3UUID(const
> uci::base::UUID&, const std::string&) of the "uci::base::UUID"
> class.\]

###### Overload for Name

Creates a UUID that conforms to RFC 4122 version 3 from a string name.
The getNamespaceUUID() member function will return the namespace UUID
used to create the RFC 4122 Version 3 UUID

-   Signature:

static uci::base::UUID createVersion3UUID(const std::string& name) const

-   Return:

The created RFC 4122 version 3 UUID.

-   Parameters:

name: The string name encoded in UTF-8 used to create the version 3
UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs creating
the UUID.

-   Access:

Public

> CERT CXX-012600 \[An OMS C++ CAL API shall declare the public static
> member function uci::base::UUID createVersion3UUID(const std::string&)
> of the "uci::base::UUID" class.\]

##### Method: getOctets

Returns the value of the UUID expressed as a vector of octets.

-   Signature:

Octets getOctets() const

-   Return:

The value of the UUID expressed as a vector of octets.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs.

-   Access:

Public

> CERT CXX-005328 \[An OMS C++ CAL API shall declare the public const
> member function Octets getOctets() of the "uci::base::UUID" class.\]

##### Method: getValueUUID

Returns the value of the UUID expressed as a ValueUUID.

-   Signature:

ValueUUID getValueUUID() const

-   Return:

The value of the UUID expressed as a ValueUUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs.

-   Access:

Public

> CERT CXX-005329 \[An OMS C++ CAL API shall declare the public const
> member function ValueUUID getValueUUID() of the "uci::base::UUID"
> class.\]

##### Method: toString

Returns the value of the UUID expressed as a string formatted according
to the RFC 4122 specification.

-   Signature:

std::string toString() const

-   Return:

The value of the UUID expressed as a string.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs.

-   Access:

Public

> CERT CXX-005331 \[An OMS C++ CAL API shall declare the public const
> member function std::string toString() of the "uci::base::UUID"
> class.\]

##### Method: getVariant

Returns the variant of the UUID.

-   Signature:

Variant getVariant() const

-   Return:

The variant of the UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to return the variant of the UUID.

-   Access:

Public

> CERT CXX-005332 \[An OMS C++ CAL API shall declare the public const
> member function Variant getVariant() of the "uci::base::UUID" class.\]
>
> GUID CXX-005333 \[This method should return variantUnknown if the
> UUID’s variant field does not identify a valid variant.\]

Such a situation usually results from a corrupted UUID.

##### Method: getVersion

Returns the version of the UUID.

-   Signature:

Version getVersion() const

-   Return:

The version of the UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to return the version of the UUID.

-   Access:

Public

> CERT CXX-005334 \[An OMS C++ CAL API shall declare the public const
> member function Version getVersion() of the "uci::base::UUID" class.\]
>
> GUID CXX-005335 \[This method should return versionUnknown if the
> UUID’s version field does not identify a valid version.\]

Such a situation usually results from a corrupted UUID.

##### Method: getClockSequence

Returns the clock sequence of the UUID.

-   Signature:

ClockSequence getClockSequence() const

-   Return:

The clock sequence contained in the UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to return the clock sequence of the UUID.

-   Access:

Public

> CERT CXX-005336 \[An OMS C++ CAL API shall declare the public const
> member function ClockSequence getClockSequence() of the
> "uci::base::UUID" class.\]

##### Method: getTimestamp

Returns the time stamp of the UUID.

-   Signature:

Timestamp getTimestamp() const

-   Return:

The time stamp contained in the UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to return the time stamp of the UUID.

-   Access:

Public

> CERT CXX-005337 \[An OMS C++ CAL API shall declare the public const
> member function Timestamp getTimestamp() of the "uci::base::UUID"
> class.\]

##### Method: getNodeAddress

Returns the node address of the UUID.

-   Signature:

NodeAddress getNodeAddress() const

-   Return:

The node address contained in the UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to return the node address of the UUID.

-   Access:

Public

> CERT CXX-005338 \[An OMS C++ CAL API shall declare the public const
> member function NodeAddress getNodeAddress() of the "uci::base::UUID"
> class.\]

##### Operator: operator==

Tests whether the UUID is equal to the specified UUID (rhs) returning
true if they are equal, false otherwise.

-   Signature:

bool operator==(const UUID& rhs) const

-   Return:

A boolean indicating whether the UUID is equal to the UUID rhs (true) or
not (false).

-   Parameters:

rhs: A constant reference to a UUID that provides access to the UUID
that is to be compared to the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to compare the two UUIDs.

-   Access:

Public

> CERT CXX-005339 \[An OMS C++ CAL API shall declare the public const
> member function bool operator==(const UUID&) of the "uci::base::UUID"
> class.\]

##### Operator: operator!=

Tests whether the UUID is not equal to the specified UUID (rhs)
returning true if they are not equal, false otherwise.

-   Signature:

bool operator!=(const UUID& rhs) const

-   Return:

A boolean indicating whether the UUID is not equal to the UUID rhs
(true) or not (false).

-   Parameters:

rhs: A constant reference to a UUID that provides access to the UUID
that is to be compared to the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to compare the two UUIDs.

-   Access:

Public

> CERT CXX-005340 \[An OMS C++ CAL API shall declare the public const
> member function bool operator!=(const UUID&) of the "uci::base::UUID"
> class.\]

##### Operator: operator&lt;

Tests whether the UUID is less than the specified UUID (rhs) returning
true if the UUID is less than the specified UUID (rhs), false otherwise.
The comparison is performed on a hexadecimal digit by hexadecimal digit
basis starting with the most significant hexadecimal digit.

-   Signature:

bool operator&lt;(const UUID& rhs) const

-   Return:

A boolean indicating whether the UUID is less than to the UUID rhs
(true) or not (false).

-   Parameters:

rhs: A constant reference to a UUID that provides access to the UUID
that is to be compared to the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to compare the two UUIDs.

-   Access:

Public

> CERT CXX-005351 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&lt;(const UUID&) of the
> "uci::base::UUID" class.\]

##### Operator: operator&lt;=

Tests whether the UUID is less than or equal to the specified UUID (rhs)
returning true if the UUID is less than or equal to the specified UUID
(rhs), false otherwise. The comparison is performed on a hexadecimal
digit by hexadecimal digit basis starting with the most significant
hexadecimal digit.

-   Signature:

bool operator&lt;=(const UUID& rhs) const

-   Return:

A boolean indicating whether the UUID is less than or equal to the UUID
rhs (true) or not (false).

-   Parameters:

rhs: A constant reference to a UUID that is to be compared to the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to compare the two UUIDs.

-   Access:

Public

> CERT CXX-005358 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&lt;=(const UUID&) of the
> "uci::base::UUID" class.\]

##### Operator: operator&gt;

Tests whether the UUID is greater than the specified UUID (rhs)
returning true if the UUID is greater than the specified UUID (rhs),
false otherwise. The comparison is performed on a hexadecimal digit by
hexadecimal digit basis starting with the most significant hexadecimal
digit.

-   Signature:

bool operator&gt;(const UUID& rhs) const

-   Return:

A boolean indicating whether the UUID is greater than the UUID rhs
(true) or not (false).

-   Parameters:

rhs: A constant reference to a UUID that is to be compared to the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to compare the two UUIDs.

-   Access:

Public

> CERT CXX-005365 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&gt;(const UUID&) of the
> "uci::base::UUID" class.\]

##### Operator: operator&gt;=

Tests whether the UUID is greater than or equal to the specified UUID
(rhs) returning true if the UUID is greater than or equal to the
specified UUID (rhs), false otherwise. The comparison is performed on a
hexadecimal digit by hexadecimal digit basis starting with the most
significant hexadecimal digit.

-   Signature:

bool operator&gt;=(const UUID& rhs) const

-   Return:

A boolean indicating whether the UUID is greater than or equal to the
UUID rhs (true) or not (false).

-   Parameters:

rhs: A constant reference to a UUID that is to be compared to the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to compare the two UUIDs.

-   Access:

Public

> CERT CXX-005372 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&gt;=(const UUID&) of the
> "uci::base::UUID" class.\]

##### Method: isNil

Returns whether the UUID is a nil UUID. A nil UUID is one in which all
hexadecimal digits are 0 (zero).

-   Signature:

bool isNil() const

-   Return:

A boolean indicating whether the UUID is a nil UUID (true) or not
(false).

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to test the UUID.

-   Access:

Public

> CERT CXX-005379 \[An OMS C++ CAL API shall declare the public const
> member function bool isNil() of the "uci::base::UUID" class.\]

##### Method: isValid

Returns whether the UUID is valid (true) or not (false). A UUID is valid
if the UUID is a nil UUID or if both the version and variant of the UUID
conform to RFC 4122. Any UUID created using generateUUID() or
createVersion3UUID() is guaranteed to be valid.

-   Signature:

bool isValid() const

-   Return:

A boolean indicating whether the UUID is valid (true) or not (false).

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to test the UUID.

-   Access:

Public

> CERT CXX-012615 \[An OMS C++ CAL API shall declare the public const
> member function bool isValid() of the "uci::base::UUID" class.\]

##### Method: toString

###### Overload for Variant

Returns the specified variant as a string.

-   Signature:

static const char\* toString(Variant variant)

throw()

-   Return:

A stringified version of the specified variant.

-   Parameters:

variant: The variant to be converted to a string.

-   Exceptions:

None.

-   Access:

Public

> GUID CXX-005386 \[For each variant, a unique string that identifies
> the variant should be returned.\]
>
> CERT CXX-005387 \[An OMS C++ CAL API shall declare the public static
> member function const char\* toString(Variant) of the
> "uci::base::UUID" class as non-throwing.\]

###### Overload for Version

Returns the specified version as a string.

-   Signature:

static const char\* toString(Version version)

throw()

-   Return:

A stringified version of the specified version.

-   Parameters:

version: The version to be converted to a string.

-   Exceptions:

None.

-   Access:

Public

> GUID CXX-005395 \[For each version, a unique string that identifies
> the version should be returned.\]
>
> CERT CXX-005396 \[An OMS C++ CAL API shall declare the public static
> member function const char\* toString(Version) of the
> "uci::base::UUID" class as non-throwing.\]

##### Constructor

###### Overload for ValueUUID

This constructor initializes the UUID using a value UUID that defaults
to the nil UUID.

-   Signature:

explicit UUID(const ValueUUID& value = ValueUUID())

-   Return:

N/A

-   Parameters:

value: the ValueUUID used to initialize the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
UUID fails.

-   Access:

Public

> CERT CXX-012628 \[An OMS C++ CAL API shall declare the public explicit
> constructor UUID(const uci::base::UUID::ValueUUID& = ValueUUID()) of
> the "uci::base::UUID" class.\]

###### Overload for C-String

This constructor initializes the UUID using a stringified UUID formatted
as specified in RFC 4122.

-   Signature:

UUID(const char\* stringifiedUUID)

-   Return:

N/A

-   Parameters:

stringifiedUUID: A UUID expressed as a string as specified in RFC 4122.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
UUID fails.

-   Access:

Public

> CERT CXX-012641 \[An OMS C++ CAL API shall declare the public
> constructor UUID(const char\*) of the "uci::base::UUID" class.\]

###### Overload for Bits

This constructor initializes the UUID using two 64-bit integers
representing the most significant bits and the least significant bits of
the UUID in big-endian byte order.

-   Signature:

UUID(uint64\_t mostSignificantBits, uint64\_t leastSignificantBits)

-   Return:

N/A

-   Parameters:

mostSignificantBits: the most significant bits of the UUID as a
big-endian, 64-bit integer.

leastSignificantBits: the least significant bits of the UUID as a
big-endian, 64-bit integer.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
UUID fails.

-   Access:

Public

> CERT CXX-012654 \[An OMS C++ CAL API shall declare the public
> constructor UUID(uint64\_t, uint64\_t) of the "uci::base::UUID"
> class.\]

##### Default Copy Constructor

This constructor initializes the UUID to the value of the UUID
parameter.

-   Signature:

UUID(const UUID& rhs)

-   Return:

N/A

-   Parameters:

rhs: The UUID whose contents are used to initialize the contents of the
newly constructed UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
UUID fails.

-   Access:

Public

> CERT CXX-005411 \[An OMS C++ CAL API shall declare the public copy
> constructor of the "uci::base::UUID" class.\]

##### Operator: operator=

Sets the value of the UUID to the value of the specified UUID (rhs).

-   Signature:

UUID& operator=(const UUID& rhs)

-   Return:

A reference to this UUID.

-   Parameters:

rhs: The UUID on the right hand side (rhs) of the assignment operator
that is used to set the value of this UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Public

> CERT CXX-011154 \[An OMS C++ CAL API shall declare the public copy
> assignment operator of the "uci::base::UUID" class.\]

##### Hash Template Specialization

The UUID header file also provides specialization of the std::hash
template on C++11 and newer versions. This allows uci::base::UUID to be
used as a key for the std::unordered\_\* collection types.

> CERT CXX-012657 \[An OMS C++ CAL API shall define the enabled template
> specialization std::hash&lt;uci::base::UUID&gt; when the value of the
> "\_\_cplusplus" preprocessor symbol is greater than or equal to 201103
> when the file "uci/base/UUID.h" is included.\]

The AbstractServiceBusConnection Class
--------------------------------------

The AbstractServiceBusConnection class provides the necessary
functionality that allows an application to connect to the “Abstract
Service Bus” and use that bus to create, send, and receive messages.

> CERT CXX-005419 \[An OMS C++ CAL API shall define the
> "AbstractServiceBusConnection" class in the "uci::base" namespace when
> the file "uci/base/AbstractServiceBusConnection.h" is included.\]

### The AbstractServiceBusConnection Class Data Types

AbstractServiceBusConnectionStateEnum: The
AbstractServiceBusConnectionStateEnum is an enumeration of the states of
the AbstractServiceBusConnection.

> CERT CXX-011275 \[An OMS C++ CAL API shall define the public member
> enum "AbstractServiceBusConnectionStateEnum" of the
> "uci::base::AbstractServiceBusConnection" class with the enumerators
> "INITIALIZING", "NORMAL", "DEGRADED", "INOPERABLE", "FAILED".\]

AbstractServiceBusConnectionStatusData: The
AbstractServiceBusConnectionStatusData is a data type that contains
information about the current state of the AbstractServiceBusConnection.

> CERT CXX-011277 \[An OMS C++ CAL API shall define the public member
> struct "AbstractServiceBusConnectionStatusData" of the
> "uci::base::AbstractServiceBusConnection" class.\]

state: The current AbstractServiceBusConnection state.

> CERT CXX-011279 \[An OMS C++ CAL API shall define the public
> uci::base::AbstractServiceBusConnection::AbstractServiceBusConnectionStateEnum
> member variable "state" of the
> "uci::base::AbstractServiceBusConnection::AbstractServiceBusConnectionStatusData"
> class.\]

stateDetail: Information concerning current AbstractServiceBusConnection
state.

> CERT CXX-011281 \[An OMS C++ CAL API shall define the public
> std::string member variable "stateDetail" of the
> "uci::base::AbstractServiceBusConnection::AbstractServiceBusConnectionStatusData"
> class.\]

### The AbstractServiceBusConnection Class Methods and Operators

#### Destructor: ~AbstractServiceBusConnection

Destroys the AbstractServiceBusConnection when the
AbstractServiceBusConnection goes out of scope or is deleted.

-   Signature:

~AbstractServiceBusConnection()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-011091 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::AbstractServiceBusConnection" class.\]

#### Method: shutdown

Shuts down this AbstractServiceBusConnection. Once shutdown, this
AbstractServiceBusConnection can no longer be used. In addition, any
object associated with this AbstractServiceBusConnection will no longer
be usable.

-   Signature:

void shutdown()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs shutting
down this AbstractServiceBusConnection.

-   Access:

Public

> CERT CXX-011164 \[An OMS C++ CAL API shall declare the public
> non-static member function void shutdown() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getMySystemLabel

Returns the system label of the system this AbstractServiceBusConnection
is executing on.

-   Signature:

std::string getMySystemLabel() const

-   Return:

The system label.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-005424 \[An OMS C++ CAL API shall declare the public const
> member function std::string getMySystemLabel() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getMySystemUUID

Returns the UUID of the system that this AbstractServiceBusConnection is
executing on (see Section 9.9, The AbstractServiceBusConnection Class).

-   Signature:

uci::base::UUID getMySystemUUID() const

-   Return:

The system UUID.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the system UUID.

-   Access:

Public

> CERT CXX-011168 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UUID getMySystemUUID() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getMyServiceUUID

Returns the UUID of the Service associated with the
AbstractServiceBusConnection (see Section 9.9, The
AbstractServiceBusConnection Class).

-   Signature:

uci::base::UUID getMyServiceUUID() const

-   Return:

The UUID of the Service associated with the
AbstractServiceBusConnection.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the Service UUID.

-   Access:

Public

> CERT CXX-011169 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UUID getMyServiceUUID() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getMySubsystemUUID

Returns the UUID of the Subsystem associated with the
AbstractServiceBusConnection (see Section 9.9, The
AbstractServiceBusConnection Class).

-   Signature:

uci::base::UUID getMySubsystemUUID() const

-   Return:

The UUID of the Subsystem associated with the
AbstractServiceBusConnection.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the Subsystem UUID.

-   Access:

Public

> CERT CXX-011170 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UUID getMySubsystemUUID() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getMyComponentUUID

Returns the UUID of the component having the specified name.

-   Signature:

uci::base::UUID

getMyComponentUUID(const std::string& name) const

-   Return:

The UUID of the component associated with the specified name.

-   Parameters:

name: The name of the component whose UUID is to be returned. The name
must uniquely identify the component to avoid collision with other
components and to retrieve the appropriate UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the component UUID.

-   Access:

Public

> CERT CXX-011171 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UUID getMyComponentUUID(const std::string&)
> of the "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getMyCapabilityUUID

Returns the UUID of the capability having the specified name.

-   Signature:

uci::base::UUID

getMyCapabilityUUID(const std::string& name) const

-   Return:

The UUID of the capability associated with the specified name.

-   Parameters:

name: The name of the capability whose UUID is to be returned. The name
must uniquely identify the capability to avoid collision with other
capabilities and to retrieve the appropriate UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the capability UUID.

-   Access:

Public

> CERT CXX-011172 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UUID getMyCapabilityUUID(const
> std::string&) of the "uci::base::AbstractServiceBusConnection"
> class.\]

#### Reserved

#### Method: getOmsSchemaVersion

Returns the version of the OMS Schema Definition from which this
AbstractServiceBusConnection class was generated.

-   Signature:

std::string getOmsSchemaVersion() const

-   Return:

The OMS Schema version.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-011174 \[An OMS C++ CAL API shall declare the public const
> member function std::string getOmsSchemaVersion() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getOmsSchemaCompilerVersion

Returns the version of this vendor’s OMS Schema compiler.

-   Signature:

std::string getOmsSchemaCompilerVersion() const

-   Return:

The version of the specification of this vendor’s OMS Schema compiler.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-011175 \[An OMS C++ CAL API shall declare the public const
> member function std::string getOmsSchemaCompilerVersion() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getOMSApiVersion

Returns the version of the OMS API from which this
AbstractServiceBusConnection class was generated.

-   Signature:

std::string getOMSApiVersion() const

-   Return:

The OMS API version.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the OMS API version.

-   Access:

Public

> CERT CXX-012694 \[An OMS C++ CAL API shall declare the public const
> member function std::string getOMSApiVersion() of the
> "uci::base::AbstractServiceBusConnection" class.\]

#### Method: getAbstractServiceBusConnectionVersion

Returns the implementation specific identifier for the version of the
Abstract Service Bus that is realized by this
AbstractServiceBusConnection class.

-   Signature:

std::string getAbstractServiceBusConnectionVersion() const

-   Return:

The implementation specific identifier for the version of the Abstract
Service Bus that is realized by this AbstractServiceBusConnection class.

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-011176 \[An OMS C++ CAL API shall declare the public const
> member function std::string getAbstractServiceBusConnectionVersion()
> of the "uci::base::AbstractServiceBusConnection" class.\]

#### Default Constructor:

This constructor’s access is protected in order to enforce the use of
the uci\_getAbstractServiceBusConnection function (see Section 9.9.2.17,
Function: uci\_getAbstractServiceBusConnection).

-   Signature:

AbstractServiceBusConnection()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
AbstractServiceBusConnection fails.

-   Access:

Protected

> CERT CXX-005431 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::AbstractServiceBusConnection"
> class.\]

#### Default Copy Constructor:

This constructor’s access is protected in order to enforce the use of
the uci\_getAbstractServiceBusConnection function (see Section 9.9.2.17,
Function: uci\_getAbstractServiceBusConnection).

-   Signature:

AbstractServiceBusConnection(const AbstractServiceBusConnection& rhs)

-   Return:

N/A

-   Parameters:

rhs: The AbstractServiceBusConnection whose contents are used to
initialize the contents of the newly constructed
AbstractServiceBusConnection.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
AbstractServiceBusConnection fails.

-   Access:

Protected

> CERT CXX-005432 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::AbstractServiceBusConnection" class.\]

#### Operator: operator=

Sets the contents of this AbstractServiceBusConnection to contents of
the specified AbstractServiceBusConnection (rhs). This operator’s access
is protected in order to enforce the use of the
uci\_getAbstractServiceBusConnection function (see Section 9.9.2.17,
Function: uci\_getAbstractServiceBusConnection).

-   Signature:

AbstractServiceBusConnection&

operator=(const AbstractServiceBusConnection& rhs)

-   Return:

A reference to this AbstractServiceBusConnection.

-   Parameters:

rhs: The AbstractServiceBusConnection on the right hand side (rhs) of
the assignment operator which is used to initialize this
AbstractServiceBusConnection.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected

> CERT CXX-011177 \[An OMS C++ CAL API shall disable access to the
> assignment operator of the "uci::base::AbstractServiceBusConnection"
> class.\]

#### Function: uci\_getAbstractServiceBusConnection

-   Signature:

uci::base::AbstractServiceBusConnection\*

uci\_getAbstractServiceBusConnection(

const std::string& serviceIdentifier,

const std::string& typeOfAbstractServiceBusConnection)

-   Return:

A pointer to the AbstractServiceBusConnection that provides access to
AbstractServiceBusConnection of the specified type and that supports the
specified service.

-   Parameters:

serviceIdentifier: The identifier of the service that is requesting
access to the Abstract Service Bus that has been configured to support
the requesting service.

typeOfAbstractServiceBusConnection: The type of Abstract Service Bus
that the invoker is requesting access to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the Abstract Service Bus.

-   Access:

Public

> CERT CXX-005433 \[An OMS C++ CAL API shall declare the free function
> uci::base::AbstractServiceBusConnection\*
> uci\_getAbstractServiceBusConnection(const std::string&, const
> std::string&) in the global namespace when the file
> "uci/base/AbstractServiceBusConnection.h" is included.\]
>
> GUID CXX-005436 \[This uci\_getAbstractServiceBusConnection function
> should be declared to have C, not C++, linkage (generally accomplished
> using the “extern C” declaration).\]

#### Method: getStatus

Returns the current status of this AbstractServiceBusConnection.

-   Signature:

AbstractServiceBusConnectionStatusData getStatus() const

-   Return:

The status of the abstract AbstractServiceBusConnection.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when this
method attempts to return the current status of this
AbstractServiceBusConnection.

-   Access:

Public

> CERT CXX-011295 \[An OMS C++ CAL API shall declare the public const
> member function
> uci::base::AbstractServiceBusConnection::AbstractServiceBusConnectionStatusData
> getStatus() of the "uci::base::AbstractServiceBusConnection" class.\]

#### Method: addStatusListener

Adds an AbstractServiceBusConnectionStatusListener to this
AbstractServiceBusConnection to process changes in the operational
status.

-   Signature:

void addStatusListener(AbstractServiceBusConnectionStatusListener&
listener)

-   Return:

None.

-   Parameters:

listener: The listener that will process changes to the operational
status.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the addition of the AbstractServiceBusConnectionStatusListener to this
AbstractServiceBusConnection.

-   Access:

Public

> CERT CXX-011082 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> addStatusListener(uci::base::AbstractServiceBusConnectionStatusListener&)
> of the "uci::base::AbstractServiceBusConnection" class.\]

#### Method: removeStatusListener

Removes the specified listener from this AbstractServiceBusConnection.

-   Signature:

void removeStatusListener(AbstractServiceBusConnectionStatusListener&
listener)

-   Return:

None.

-   Parameters:

listener: The listener that is to be removed from this
AbstractServiceBusConnection.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the removal of the AbstractServiceBusConnectionStatusListener from this
AbstractServiceBusConnection.

-   Access:

Public

> CERT CXX-011083 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> removeStatusListener(uci::base::AbstractServiceBusConnectionStatusListener&)
> of the "uci::base::AbstractServiceBusConnection" class.\]

The Listener Class
------------------

The Listener class is the base class from which all Listener classes are
derived. The Listener class is responsible for providing support needed
to listen for incoming OMS Messages.

> CERT CXX-010675 \[An OMS C++ CAL API shall define the "Listener" class
> in the "uci::base" namespace when the file "uci/base/Listener.h" is
> included.\]

### The Listener Class Methods and Operators

#### Destructor: ~Listener

Destroys the Listener when the Listener goes out of scope or is deleted.

-   Signature:

virtual ~Listener()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-010691 \[An OMS C++ CAL API shall specify the destructor of
> the "uci::base::Listener" class as virtual.\]

#### Default Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Listener()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Listener fails.

-   Access:

Protected

> CERT CXX-010704 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::Listener" class.\]

#### Default Copy Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Listener(const Listener& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Listener whose contents are used to initialize the contents of
the newly constructed Listener.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Listener fails.

-   Access:

Protected

> CERT CXX-010717 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::Listener" class.\]

#### Operator: operator=

Sets the contents of this Listener to contents of the specified Listener
(rhs). This operator’s access is protected in order to enforce the use
of child classes.

-   Signature:

Listener&

operator=(const Listener& rhs)

-   Return:

A reference to this Listener.

-   Parameters:

rhs: The Listener on the right hand side (rhs) of the assignment
operator which is used to initialize this Listener.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected

> CERT CXX-011182 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the "uci::base::Listener" class.\]

The Reader Class
----------------

The Reader class is the base class from which all Reader classes are
derived. These objects are responsible for providing support needed to
read an OMS Message from the Abstract Service Bus.

> CERT CXX-010733 \[An OMS C++ CAL API shall define the "Reader" class
> in the "uci::base" namespace when the file "uci/base/Reader.h" is
> included.\]

### The Reader Class Methods and Operators

#### Destructor: ~Reader

Destroys the Reader when the Reader goes out of scope or is deleted.

-   Signature:

~Reader()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-011094 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::Reader" class.\]

#### Default Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Reader()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Reader fails.

-   Access:

Protected

> CERT CXX-010763 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::Reader" class.\]

#### Default Copy Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Reader(const Reader& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Reader whose contents are used to initialize the contents of
the newly constructed Reader.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Reader fails.

-   Access:

Protected

> CERT CXX-010776 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::Reader" class.\]

#### Operator: operator=

Sets the contents of this Reader to contents of the specified Reader
(rhs). This operator’s access is protected in order to enforce the use
of child classes.

-   Signature:

Reader&

operator=(const Reader& rhs)

-   Return:

A reference to this Reader.

-   Parameters:

rhs: The Reader on the right hand side (rhs) of the assignment operator
which is used to initialize this Reader.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected

> CERT CXX-011204 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the "uci::base::Reader" class.\]

The Writer Class
----------------

The Writer class is the base class from which all Writer classes are
derived. These objects are responsible for providing support needed to
write an OMS Message to the Abstract Service Bus.

> CERT CXX-010792 \[An OMS C++ CAL API shall define the "Writer" class
> in the "uci::base" namespace when the file "uci/base/Writer.h" is
> included.\]

### The Writer Class Methods and Operators

#### Destructor: ~Writer

Destroys the Writer when the Writer goes out of scope or is deleted.

-   Signature:

~Writer()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-011095 \[An OMS C++ CAL API shall disable access to the
> destructor of the "uci::base::Writer" class.\]

#### Default Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Writer()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Writer fails.

-   Access:

Protected

> CERT CXX-010822 \[An OMS C++ CAL API shall disable access to the
> default constructor of the "uci::base::Writer" class.\]

#### Default Copy Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Writer(const Writer& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Writer whose contents are used to initialize the contents of
the newly constructed Writer.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Writer fails.

-   Access:

Protected

> CERT CXX-010835 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the "uci::base::Writer" class.\]

#### Operator: operator=

Sets the contents of this Writer to contents of the specified Writer
(rhs). This operator’s access is protected in order to enforce the use
of child classes.

-   Signature:

Writer&

operator=(const Writer& rhs)

-   Return:

A reference to this Writer.

-   Parameters:

rhs: The Writer on the right hand side (rhs) of the assignment operator
which is used to initialize this Writer.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected.

> CERT CXX-011205 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the "uci::base::Writer" class.\]

The AbstractServiceBusConnectionStatusListener Class
----------------------------------------------------

The AbstractServiceBusConnectionStatusListener class is responsible for
providing support needed to listen for changes in the operation status
of the Abstract Service Bus.

> CERT CXX-011324 \[An OMS C++ CAL API shall define the
> "AbstractServiceBusConnectionStatusListener" class in the "uci::base"
> namespace when the file
> "uci/base/AbstractServiceBusConnectionStatusListener.h" is included.\]

### The AbstractServiceBusConnectionStatusListener Class Methods and Operators

#### Destructor: ~AbstractServiceBusConnectionStatusListener

Destroys the AbstractServiceBusConnectionStatusListener when the
AbstractServiceBusConnectionStatusListener goes out of scope or is
deleted.

-   Signature:

virtual ~AbstractServiceBusConnectionStatusListener()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-011341 \[An OMS C++ CAL API shall specify the destructor of
> the "uci::base::AbstractServiceBusConnectionStatusListener" class as
> virtual.\]

#### Method: statusChanged

This method handles changes in the state of the
AbstractServiceBusConnection.

-   Signature:

virtual void statusChanged (AbstractServiceBusConnectionStatusData
newStatus) = 0

-   Return:

None.

-   Parameters:

newStatus: The AbstractServiceBusConnectionStatusData that contains data
that describes the current state of the AbstractServiceBusConnection.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the handling of the change of the state of the
AbstractServiceBusConnection.

-   Access:

Public

> CERT CXX-011355 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> statusChanged(uci::base::AbstractServiceBusConnection::AbstractServiceBusConnectionStatusData)
> of the "uci::base::AbstractServiceBusConnectionStatusListener" class
> as pure virtual.\]

The Externalizer Class
----------------------

The Externalizer class provides support to export and import messages to
and from an external format. The external format can be independent of
any internal CAL serialization and transport implementations. The
methods used by the externalizer to read and write data are
implementation dependent.

> CERT CXX-012071 \[An OMS C++ CAL API shall define the “Externalizer”
> class in the “uci::base” namespace when the file
> “uci/base/Externalizer.h” is included.\]

### The Externalizer Class Methods and Operators

#### Destructor: ~Externalizer

Destroys the Externalizer when the Externalizer goes out of scope or is
deleted.

-   Signature:

~Externalizer()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected

CERT CXX-012703 \[An OMS C++ CAL API shall disable access to the
destructor of the "uci::base::Externalizer" class.\]

#### Method: read

##### Overload for Input Stream

This method reads the contents of the C++ standard library istream into
the object. Due to the limits of the C++ stream library, all streams
opened by the user of the Externalizer shall be opened in binary mode.
The reason for this is that C++ binary streams can properly handle text
as well as binary data. But the reverse is not true. As a result, use of
binary streams assures users that stream data can be properly handled
without requiring explicit knowledge of stream mode to be communicated
at the time of connection. This is stated as guidance rather than a
requirement enforced by CERT.

-   Signature:

virtual void read(std::istream& istream, uci::base::Accessor& type)

-   Return:

None.

-   Parameters:

istream: The C++ standard library istream whose content will be used to
import into the object.

type: The object to be written to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
processing of the object.

-   Access:

Public

> CERT CXX-012099 \[An OMS C++ CAL API shall declare the public
> non-static member function void read(std::istream&,
> uci::base::Accessor&) of the “uci::base::Externalizer” class as
> virtual.\]

##### Overload for String

This method reads the contents of the C++ standard library string into
the object.

-   Signature:

virtual void read(const std::string& string, uci::base::Accessor& type)

-   Return:

None.

-   Parameters:

string: The C++ standard library string whose content will to be used to
import into the object.

type: The object to be written to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
processing of the object.

-   Access:

Public

> CERT CXX-012115 \[An OMS C++ CAL API shall declare the public
> non-static member function void read(const std::string&,
> uci::base::Accessor&) of the “uci::base::Externalizer” class as
> virtual.\]

##### Overload for vector

This method reads the contents of the C++ standard library vector into
the object.

-   Signature:

virtual void read(const std::vector&lt;uint8\_t&gt;& vec,
uci::base::Accessor& type)

-   Return:

None.

-   Parameters:

vec: The C++ standard library vector of uint8\_t values whose content
will to be used to import into the object.

type: The object to be written to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
processing of the object.

-   Access:

Public

> CERT CXX-012131 \[An OMS C++ CAL API shall declare the public
> non-static member function void read(const
> std::vector&lt;uint8\_t&gt;&, uci::base::Accessor&) of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: write

##### Overload for Output Stream

This method writes the contents of the object into the C++ standard
library ostream. Due to the limits of the C++ stream library, all
streams opened by the user of the Externalizer shall be opened in binary
mode. The reason for this is that C++ binary streams can properly handle
text as well as binary data. But the reverse is not true. As a result,
use of binary streams assures users that stream data can be properly
handled without requiring explicit knowledge of stream mode to be
communicated at the time of connection. This is stated as guidance
rather than a requirement enforced by CERT.

-   Signature:

virtual void write(const uci::base::Accessor& type, std::ostream&
ostream)

-   Return:

None.

-   Parameters:

type: The object whose content will be used to export into the ostream.

ostream: The C++ standard library ostream to be written to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
processing of the object.

-   Access:

Public

> CERT CXX-012146 \[An OMS C++ CAL API shall declare the public
> non-static member function void write(const uci::base::Accessor&,
> std::ostream&) of the “uci::base::Externalizer” class as virtual.\]

##### Overload for String

This method writes the contents of the object into the C++ standard
library string.

-   Signature:

virtual void write(const uci::base::Accessor& type, std::string& string)

-   Return:

None.

-   Parameters:

type: The object whose content will be used to export into the ostream.

string: The C++ standard library string to be written to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
processing of the object.

-   Access:

Public

> CERT CXX-012161 \[An OMS C++ CAL API shall declare the public
> non-static member function void write(const uci::base::Accessor&,
> std::string&) of the “uci::base::Externalizer” class as virtual.\]

##### Overload for Vector

This method writes the contents of the object into the C++ standard
library vector.

-   Signature:

virtual void write(const uci::base::Accessor& message,
std::vector&lt;uint8\_t&gt;& vec)

-   Return:

None.

-   Parameters:

type: The object whose content will be used to export into the ostream.

vec: The C++ standard library vector of uint8\_t to be written to.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
processing of the object.

-   Access:

Public

> CERT CXX-012176 \[An OMS C++ CAL API shall declare the public
> non-static member function void write(const uci::base::Accessor&,
> std::vector&lt;uint8\_t&gt;& vec) of the “uci::base::Externalizer”
> class as virtual.\]

#### Method: messageReadOnly

Returns whether this Externalizer only supports the read functions with
OMS Messages.

-   Signature:

virtual bool messageReadOnly() const

-   Return:

A boolean indicating the Externalizer is only capable of processing OMS
Messages.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the messageReadOnly status.

-   Access:

Public

> CERT CXX-012688 \[An OMS C++ CAL API shall declare the public const
> member function bool messageReadOnly() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: messageWriteOnly

Returns whether this Externalizer only supports the write functions with
OMS Messages.

-   Signature:

virtual bool messageWriteOnly() const

-   Return:

A boolean indicating the Externalizer is only capable of processing OMS
Messages.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the messageWriteOnly status.

-   Access:

Public

> CERT CXX-012689 \[An OMS C++ CAL API shall declare the public const
> member function bool messageWriteOnly() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: supportsObjectRead

Returns whether this Externalizer supports the read functions with
objects.

-   Signature:

virtual bool supportsObjectRead() const

-   Return:

A boolean indicating the Externalizer is capable of processing objects.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the supportsObjectRead status.

-   Access:

Public

> CERT CXX-012690 \[An OMS C++ CAL API shall declare the public const
> member function bool supportsObjectRead() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: supportsObjectWrite

Returns whether this Externalizer supports the write functions with
objects.

-   Signature:

virtual bool supportsObjectWrite() const

-   Return:

A boolean indicating the Externalizer is capable of processing objects.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the supportsObjectWrite status.

-   Access:

Public

> CERT CXX-012691 \[An OMS C++ CAL API shall declare the public const
> member function bool supportsObjectWrite() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: getCalApiVersion

Returns the version of the OMS CAL API associated with this
Externalizer.

-   Signature:

virtual std::string getCalApiVersion() const

-   Return:

The OMS CAL API version.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the OMS API version.

-   Access:

Public

> CERT CXX-012238 \[An OMS C++ CAL API shall declare the public const
> member function std::string getCalApiVersion() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: getEncoding

Returns the Externalizer encoding associated with this Externalizer.

-   Signature:

virtual std::string getEncoding() const

-   Return:

The Externalizer encoding.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the Externalizer encoding.

-   Access:

Public

> CERT CXX-012252 \[An OMS C++ CAL API shall declare the public const
> member function std::string getEncoding() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: getSchemaVersion

Returns the version of the Schema Definition associated with this
Externalizer.

-   Signature:

virtual std::string getSchemaVersion() const

-   Return:

The OMS Schema Definition version.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the OMS Schema Definition version.

-   Access:

Public

> CERT CXX-012266 \[An OMS C++ CAL API shall declare the public const
> member function std::string getSchemaVersion() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: getVendorVersion

Returns the Vendor’s version associated with this Externalizer.

-   Signature:

virtual std::string getVendorVersion() const

-   Return:

The Vendor’s version of this Externalizer.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the vendor version.

-   Access:

Public

> CERT CXX-012280 \[An OMS C++ CAL API shall declare the public const
> member function std::string getVendorVersion() of the
> “uci::base::Externalizer” class as virtual.\]

#### Method: getVendor

Returns the Vendor associated with this Externalizer.

-   Signature:

virtual std::string getVendor() const

-   Return:

The externalizer vendor.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the externalizer vendor.

-   Access:

Public

> CERT CXX-012294 \[An OMS C++ CAL API shall declare the public const
> member function std::string getVendor() of the
> “uci::base::Externalizer” class as virtual.\]

#### Default Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Externalizer()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Externalizer fails.

-   Access:

Protected

> CERT CXX-012308 \[An OMS C++ CAL API shall disable access to the
> default constructor of the “uci::base::Externalizer” class.\]

#### Default Copy Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

Externalizer(const Externalizer& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Externalizer whose contents are used to initialize the contents
of the newly constructed Externalizer.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Externalizer fails.

-   Access:

Protected

> CERT CXX-012321 \[An OMS C++ CAL API shall disable access to the
> default copy constructor of the “uci::base::Externalizer” class.\]

#### Operator: operator=

Sets the contents of this Externalizer to contents of the specified
Externalizer (rhs). This operator’s access is protected in order to
enforce the use of child classes.

-   Signature:

Externalizer&

operator=(const Externalizer& rhs)

-   Return:

A constant reference to this Externalizer.

-   Parameters:

rhs: The Externalizer on the right hand side (rhs) of the assignment
operator which is used to initialize this Externalizer.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected

> CERT CXX-012335 \[An OMS C++ CAL API shall disable access to the
> assignment operator of the “uci::base::Externalizer” class.\]

The ExternalizerLoader Class
----------------------------

The ExternalizerLoader class is responsible for obtaining and removing
access to implementations of the Externalizer class.

> CERT CXX-012338 \[An OMS C++ CAL API shall define the
> “ExternalizerLoader” class in the “uci::base” namespace when the file
> “uci/base/ExternalizerLoader.h” is included.\]

### The ExternalizerLoader Class Methods and Operators

#### Destructor: ~ExternalizerLoader

Destroys the ExternalizerLoader when the ExternalizerLoader goes out of
scope or is deleted.

-   Signature:

~ExternalizerLoader()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected

CERT CXX-012704 \[An OMS C++ CAL API shall disable access to the
destructor of the "uci::base::ExternalizerLoader" class.\]

#### Method: getExternalizer

This method provides access to an Externalizer of the specified type.

-   Signature:

uci::base::Externalizer\* getExternalizer(const std::string& encoding,
const std::string& schemaVersion, const std::string& calApiVersion)

-   Return:

A pointer to an Externalizer that provides access to an Externalizer of
the specified type.

-   Parameters:

encoding: The type encoding format of the Externalizer.

schemaVersion: The OMS Schema Definition version of the Externalizer.

calApiVersion: The OMS CAL API version of the Externalizer.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs when
obtaining access to an Externalizer.

-   Access:

Public

> CERT CXX-012367 \[An OMS C++ CAL API shall declare the public
> non-static member function uci::base::Externalizer\*
> getExternalizer(const std::string&, const std::string&, const
> std::string&) of the “uci::base::ExternalizerLoader” class.\]

#### Method: destroyExternalizer

This method destroys the specified Externalizer instance.

-   Signature:

void destroyExternalizer(uci::base::Externalizer\* externalizer)

-   Return:

None.

-   Parameters:

externalizer: The Externalizer to be destroyed.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the destruction of the Externalizer.

-   Access:

Public

> CERT CXX-012381 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> destroyExternalizer(uci::base::Externalizer\*) of the
> “uci::base::ExternalizerLoader” class.\]

#### Default Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

ExternalizerLoader()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
ExternalizerLoader fails.

-   Access:

Protected

> CERT CXX-012395 \[An OMS C++ CAL API shall disable access to the
> default constructor of the “uci::base::ExternalizerLoader” class.\]

#### Default Copy Constructor:

This constructor’s access is protected in order to enforce the use of
child classes for construction.

-   Signature:

ExternalizerLoader(const ExternalizerLoader& rhs)

-   Return:

N/A

-   Parameters:

rhs: The ExternalizerLoader whose contents are used to initialize the
contents of the newly constructed ExternalizerLoader.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
ExternalizerLoader fails.

-   Access:

Protected

> CERT CXX-012408 \[An OMS C++ CAL API shall disable access to the
> default copy constructor of the “uci::base::ExternalizerLoader”
> class.\]

#### Operator: operator=

Sets the contents of this ExternalizerLoader to contents of the
specified ExternalizerLoader (rhs). This operator’s access is protected
in order to enforce the use of child classes.

-   Signature:

ExternalizerLoader&

operator=(const ExternalizerLoader& rhs)

-   Return:

A constant reference to this ExternalizerLoader.

-   Parameters:

rhs: The ExternalizerLoader on the right hand side (rhs) of the
assignment operator which is used to initialize this ExternalizerLoader.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Protected

> CERT CXX-012422 \[An OMS C++ CAL API shall disable access to the
> assignment operator of the “uci::base::ExternalizerLoader” class.\]

#### Function: uci\_getExternalizerLoader

-   Signature:

uci::base::ExternalizerLoader\* uci\_getExternalizerLoader()

-   Return:

A pointer to the ExternalizerLoader that provides access to
Externalizers. When access to the ExternalizerLoader is no longer
needed, the ExternalizerLoader should be destroyed by invoking the
destroy ExternalizerLoader function, i.e.,
uci\_destroyExternalizerLoader.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
retrieving the ExternalizerLoader.

-   Access:

Public

> CERT CXX-012434 \[An OMS C++ CAL API shall declare the free function
> uci::base::ExternalizerLoader\* uci\_getExternalizerLoader() in the
> global namespace when the file “uci/base/ExternalizerLoader.h” is
> included.\]

#### Function: uci\_destroyExternalizerLoader

-   Signature:

void uci\_destroyExternalizerLoader(uci::base::ExternalizerLoader\*
externalizerLoader)

-   Return:

None.

-   Parameters:

externalizerLoader: The pointer to the ExternalizerLoader that is to be
destroyed.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs
destroying the ExternalizerLoader.

-   Access:

Public

> CERT CXX-012446 \[An OMS C++ CAL API shall declare the free function
> void uci\_destroyExternalizerLoader(uci::base::ExternalizerLoader\*)
> in the global namespace when the file “uci/base/ExternalizerLoader.h”
> is included.\]

Accessors
=========

Section 3, The C++ Schema Compiler Conceptual Architecture, provides the
details regarding the C++ OMS Schema Compiler’s conceptual architecture.
As stated in that section, the XSD parser will generate a set of
Accessor instances in response to the declarations that are contained in
the OMS Schema Definition. In this section, the details regarding these
Accessors will be provided.

Section 5, Names and Qualified Names, provides details regarding terms
and functions used throughout the document.

Generating C++ Data Type and Enumeration Item Names
---------------------------------------------------

The XSD specification allows names of declarations to use formats that
are not valid C++ names. Given this, the name of the C++ data types
cannot directly use the name of the declaration. Thus the name of the
declaration, known as an XSD name, must be translated to a valid C++
name.

The following rules, known as the Data Type Name Translation Rules, are
to be applied when translating a name of an XSD declaration to the name
of a C++ data type:

-   Prepend ‘D\_’ to any name that starts with a digit.

-   Capitalize the first letter of the name of the XSD name.

-   Replace any “ ”, i.e., space, in the XSD name with underscores,
    i.e., “\_”.

-   Replace any “-”, i.e., hyphen, in the XSD name with underscores,
    i.e., “\_”.

-   Replace any “.”, i.e., period, in the XSD name with underscores,
    i.e., “\_”.

-   Append ‘\_r’ to any name that is a reserved C++ reserved name; for
    the full list of reserved keywords see Table 10.1-1. This
    translation is case sensitive. For example, whereas “class” would be
    translated, “Class” would not.

<span id="_Toc219293154" class="anchor"></span>Table 10.1-1 C++ Reserved
Keywords

<table>
<thead>
<tr class="header">
<th>and</th>
<th>and_eq</th>
<th>asm</th>
<th>bitand</th>
<th>bitor</th>
<th>bool</th>
<th>break</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>case</td>
<td>catch</td>
<td>char</td>
<td>class</td>
<td>compl</td>
<td>const</td>
<td>const_cast</td>
</tr>
<tr class="even">
<td>continue</td>
<td>default</td>
<td>delete</td>
<td>do</td>
<td>double</td>
<td>dynamic_cast</td>
<td>else</td>
</tr>
<tr class="odd">
<td>enum</td>
<td>explicit</td>
<td>export</td>
<td>extern</td>
<td>false</td>
<td>float</td>
<td>for</td>
</tr>
<tr class="even">
<td>friend</td>
<td>goto</td>
<td>if</td>
<td>inline</td>
<td>int</td>
<td>long</td>
<td>mutable</td>
</tr>
<tr class="odd">
<td>namespace</td>
<td>new</td>
<td>not</td>
<td>not_eq</td>
<td>operator</td>
<td>or</td>
<td>or_eq</td>
</tr>
<tr class="even">
<td>private</td>
<td>protected</td>
<td>public</td>
<td>register</td>
<td>reinterpret_cast</td>
<td>return</td>
<td>short</td>
</tr>
<tr class="odd">
<td>signed</td>
<td>sizeof</td>
<td>static</td>
<td>static_cast</td>
<td>struct</td>
<td>switch</td>
<td>template</td>
</tr>
<tr class="even">
<td>this</td>
<td>throw</td>
<td>true</td>
<td>try</td>
<td>typedef</td>
<td>typeid</td>
<td>typename</td>
</tr>
<tr class="odd">
<td>union</td>
<td>unsigned</td>
<td>using</td>
<td>virtual</td>
<td>void</td>
<td>volatile</td>
<td>wchar_t</td>
</tr>
<tr class="even">
<td>while</td>
<td>xor</td>
<td>xor_eq</td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

The following rules, known as the Enumerated Item Name Translation
Rules, are to be applied when translating a name of an enumeration XSD
declaration to the name of a C++ enumerated item:

-   Capitalize every letter of the xs:enumeration value.

-   Replace any “ ”, i.e., space, in the XSD name with underscores,
    i.e., “\_”.

-   Replace any “-”, i.e., hyphen, in the XSD name with underscores,
    i.e., “\_”.

-   Replace any “.”, i.e., period, in the XSD name with underscores,
    i.e., “\_”.

Class Declarations
------------------

In the declaration of an Accessor, a set of similar member functions are
generated for each instantiation of a class. This includes associated
reader, writer, and listener classes. Deviation from the rules set by
this section are expressed further within the document for the accessor
type the exception is attributed to.

### Accessor Instance Definitions

> CERT CXX-005456 \[An OMS C++ CAL API shall define the
> "&lt;cxxTypeName&gt;" class in the "&lt;cxxTargetNamespace&gt;::type"
> namespace that publicly and singly inherits from
> "&lt;cxxRootNamespace&gt;::type::&lt;cxxBaseTypeName&gt;" where
> &lt;cxxBaseTypeName&gt; is the
> \`xs:complexContent/xs:extension/@base\` translated using the
> “Generating C++ Data Type and Enumeration Item Names” section "Data
> Type Name Translation Rules" when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each
> \`/xs:schema/xs:complexType\[xs:complexContent/xs:extension/@base\]\`.\]
>
> CERT CXX-011135 \[An OMS C++ CAL API shall define the
> "&lt;cxxTypeName&gt;" class in the "&lt;cxxTargetNamespace&gt;::type"
> namespace that publicly and singly inherits from "uci::base::Accessor"
> when the file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h"
> is included for each
> \`/xs:schema/xs:complexType\[not(xs:complexContent/xs:extension/@base)\]\`.\]

For example, if the cxxTypeName is specified as “UserData” and the
baseAccessor is specified as default, then following can be generated:

class UserData : public uci::base::Accessor

#### Destructor: ~&lt;cxxTypeName&gt;

Destroys the &lt;cxxTypeName&gt; when the &lt;cxxTypeName&gt; goes out
of scope or is deleted.

-   Signature:

~&lt;cxxTypeName&gt;()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-012705 \[An OMS C++ CAL API shall disable access to the
> destructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/(xs:simpleType\[not(ancestor::xs:schema/@targetNamespace
> = '<span
> class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>' and
> @name =
> 'UniversallyUniqueIdentifierType')\]|xs:complexType|xs:element)\`.\]

#### Default Constructor: &lt;cxxTypeName&gt;

As stated in Section 7, Accessor Construction and Destruction, this
constructor’s visibility is protected in order to enforce the use of the
Accessor static create methods when constructing these Accessors.

-   Signature:

&lt;cxxTypeName&gt;()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Accessor fails.

-   Access:

Protected

> CERT CXX-005464 \[An OMS C++ CAL API shall disable access to the
> default constructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/(xs:simpleType\[not(ancestor::xs:schema/@targetNamespace
> = '<span
> class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>' and
> @name =
> 'UniversallyUniqueIdentifierType')\]|xs:complexType|xs:element)\`.\]

#### Default Copy Constructor: &lt;cxxTypeName&gt;

The default copy constructor is not used since the copy construction has
to be protected and only visible to derived classes. As stated in
Section 7, Accessor Construction and Destruction, this is required in
order to enforce the use of the Accessor static create methods when
constructing these Accessors.

-   Signature:

&lt;cxxTypeName&gt;(const &lt;cxxTypeName&gt;& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Accessor that is used to initialize the contents of the newly
constructed Accessor.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Accessor fails.

-   Access:

Protected

> CERT CXX-005465 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/(xs:simpleType\[not(ancestor::xs:schema/@targetNamespace
> = '<span
> class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>' and
> @name =
> 'UniversallyUniqueIdentifierType')\]|xs:complexType|xs:element)\`.\]

### Accessor Instance Member Functions

#### Member Function: copy

Performs a deep copy of the data accessed by the specified Accessor to
the data accessed by this Accessor.

-   Signature:

void copy(const &lt;cxxTypeName&gt;& accessor)

-   Return:

None.

-   Parameters:

accessor: The Accessor that provides access to the data whose contents
are to be copied to the data accessed by this Accessor.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the copy.

-   Access:

Public

> CERT CXX-011063 \[An OMS C++ CAL API shall declare the public
> non-static member function void copy(const &lt;cxxTypeName&gt;&) of
> the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for
> each \`/xs:schema/xs:complexType\`.\]

The data accessed by this Accessor prior to the invocation of the copy
method should be freed prior to the execution of the method.

#### Operator: operator=

Performs a deep copy of the contents of the data that is accessed by the
specified Accessor (rhs) and sets the contents of the data that is
accessed by this Accessor to the resulting copy. As stated in Section 7,
Accessor Construction and Destruction, this operator’s access is
protected in order to enforce the use of the Accessor static create
methods when constructing Accessors.

-   Signature:

&lt;cxxTypeName&gt;& operator=(const &lt;cxxTypeName&gt;& rhs)

-   Return:

A reference to this Accessor.

-   Parameters:

rhs: The Accessor on the right hand side (rhs) of the assignment
operator which provides access to the data that is to be copied to the
data that is accessed by this Accessor.

-   Exceptions:

None

-   Access:

Protected

> CERT CXX-011064 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType\`.\]

### The Element Access Member Functions

The following are required to be specified when an instance of the
accessor class member functions are to be realized.

#### Member Function: get&lt;cxxElementName&gt;

Returns the value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Signature:

&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
get&lt;cxxElementName&gt;()

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011213 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@type="uci:UniversallyUniqueIdentifierType")
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1) and
> not(starts-with(@type, 'xs:'))\]\` where \`@type\` does not derive
> from an "XSD Data Type" of "The Simple Primitive Types" table.\]

Programming note: The phrase “derives from” is referring to the XSD
simpleType {base type definition} of the type definition as defined by
XML Schema Part 1: Structures

#### Const Member Function: get&lt;cxxElementName&gt;

Returns the value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Signature:

const &lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
get&lt;cxxElementName&gt;() const

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011214 \[An OMS C++ CAL API shall declare the public const
> member function const
> &lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@type="uci:UniversallyUniqueIdentifierType")
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1) and
> not(starts-with(@type, 'xs:'))\]\` where \`@type\` does not derive
> from an "XSD Data Type" of "The Simple Primitive Types" table.\]

#### Member Function: set&lt;cxxElementName&gt;

Sets the value of the accessor data type that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(const
&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;& value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value to be used to set the accessor's data type that is
identified by the &lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs setting
the value of the accessor's data type.

-   Access:

Public

> CERT CXX-011215 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(const
> &lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@type="uci:UniversallyUniqueIdentifierType")
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1) and
> not(starts-with(@type, 'xs:'))\]\` where \`@type\` does not derive
> from an "XSD Data Type" of "The Simple Primitive Types" table .\]

The following variations are seen when declaring instance access methods
for elements of certain accessor types.

#### Simple Primitive Const Member Function: get&lt;cxxElementName&gt;

Returns the Simple Primitive value of the element that is identified by
&lt;cxxElementName&gt;.

-   Signature:

xs::&lt;cxxPrimitiveName&gt; get&lt;cxxElementName&gt;() const

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011216 \[An OMS C++ CAL API shall declare the public const
> member function xs::&lt;cxxPrimitiveName&gt;
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@maxOccurs='unbounded'
> or @maxOccurs&gt;1)\]\` where \`@type\` is or derives from an "XSD
> Data Type" of "The Simple Primitive Types" table.\]

#### Simple Primitive Member Function: set&lt;cxxElementName&gt;

Sets the Simple Primitive value of the element that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(xs::&lt;cxxPrimitiveName&gt; value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011217 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(xs::&lt;cxxPrimitiveName&gt;) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@maxOccurs='unbounded'
> or @maxOccurs&gt;1)\]\` where \`@type\` is or derives from an "XSD
> Data Type" of "The Simple Primitive Types" table.\]

#### String Primitive Member Function: set&lt;cxxElementName&gt;

##### Overload for String

Sets the String Primitive value of the element that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(const std::string& value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011219 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(const std::string&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(ends-with(@type,'Enum'))
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1)\]\` where \`@type\`
> is or derives from an "XSD Data Type" of "The String Primitive Types"
> table.\]

##### Overload for C-String

Sets the String Primitive value of the element that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(const char\* value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011220 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(const char\*) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(ends-with(@type,'Enum'))
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1)\]\` where \`@type\`
> is or derives from an "XSD Data Type" of "The String Primitive Types"
> table.\]

#### Enumeration Member Function: set&lt;cxxElementName&gt;

Sets the value of the enumeration that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;::EnumerationItem
value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value to be used to set the accessor's data type that is
identified by the &lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs setting
the value of the accessor's data type.

-   Access:

Public

> CERT CXX-011223 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;::EnumerationItem)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[ends-with(@type,'Enum')
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1)\]\`.\]

#### Non-Simple Primitive Member Function: get&lt;cxxElementName&gt;

Returns the value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Signature:

xs::&lt;cxxPrimitiveName&gt;& get&lt;cxxElementName&gt;()

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-012706 \[An OMS C++ CAL API shall declare the public
> non-static member function xs::&lt;cxxPrimitiveName&gt;&
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@type="uci:UniversallyUniqueIdentifierType")
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1) and
> not(ends-with(@type, 'Enum'))\]\` where \`@type\` is or derives from
> an "XSD Data Type" of "The String Primitive Types", "The Numeric
> String Primitive Types", "The Binary Primitive Types", or "The List
> Primitive Types" tables.\]

#### Non-Simple Primitive Const Member Function: get&lt;cxxElementName&gt;

Returns the value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Signature:

const xs::&lt;cxxPrimitiveName&gt;& get&lt;cxxElementName&gt;() const

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-012707 \[An OMS C++ CAL API shall declare the public const
> member function const xs::&lt;cxxPrimitiveName&gt;&
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@type="uci:UniversallyUniqueIdentifierType")
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1) and
> not(ends-with(@type, 'Enum'))\]\` where \`@type\` is or derives from
> an "XSD Data Type" of "The String Primitive Types", "The Numeric
> String Primitive Types", "The Binary Primitive Types", or "The List
> Primitive Types" tables.\]

#### Non-Simple Primitive Member Function: set&lt;cxxElementName&gt;

Sets the value of the accessor data type that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(const xs::&lt;cxxPrimitiveName&gt;& value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value to be used to set the accessor's data type that is
identified by the &lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs setting
the value of the accessor's data type.

-   Access:

Public

> CERT CXX-012708 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(const xs::&lt;cxxPrimitiveName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[not(@type="uci:UniversallyUniqueIdentifierType")
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1) and
> not(ends-with(@type, 'Enum'))\]\` where \`@type\` is or derives from
> an "XSD Data Type" of "The String Primitive Types", "The Numeric
> String Primitive Types", "The Binary Primitive Types", or "The List
> Primitive Types" tables.\]

The following variations are seen when declaring instance access methods
for elements with attributes meeting specific conditions.

Elements with a \`@maxOccurs\` attribute set the string "unbounded" or
an integer greater than 1 prompts the declaration of a BoundedList whose
contents is the accessorType of the element. This also declares a get
and set method subject to the items within that BoundedList.

#### Bounded List Member Function: get&lt;cxxElementName&gt;

##### Const Variant

Returns the value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Signature:

const
&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
get&lt;cxxElementName&gt;() const

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011226 \[An OMS C++ CAL API shall declare the public const
> member function const
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[@maxOccurs='unbounded'
> or @maxOccurs&gt;1\]\`.\]

##### Non-Const Variant

Returns the value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
get&lt;cxxElementName&gt;()

-   Return:

The value of the accessor that is identified by the
&lt;cxxElementName&gt;.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value of the accessor.

-   Access:

Public

> CERT CXX-011227 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
> get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[@maxOccurs='unbounded'
> or @maxOccurs&gt;1\]\`.\]

#### Bounded List Member Function: set&lt;cxxElementName&gt;

Sets the value of the accessor data type that is identified by the
&lt;cxxElementName&gt; and returns a reference to the parent object.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(const
&lt;cxxRootNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
value)

-   Return:

A reference to the object on which this method was called

-   Parameters:

value: The value to be used to set the accessor's data type that is
identified by the &lt;cxxElementName&gt;.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs setting
the value of the accessor's data type.

-   Access:

Public

> CERT CXX-011228 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(const
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:choice|xs:sequence)/xs:element\[@maxOccurs='unbounded'
> or @maxOccurs&gt;1\]\`.\]

Elements having the \`@minOccurs\` attribute set to 0 or the
\`xsd:attribute/@use\` attribute set to "optional" are considered
optional elements and attributes. The declaration of an optional element
will result in member functions that add further context to the
accessor.

#### Member Function: has&lt;cxxElementName&gt;

This method returns whether the element that is identified by
&lt;cxxElementName&gt; exists (is enabled) or not.

-   Signature:

bool has&lt;cxxElementName&gt;() const

-   Return:

A Boolean that indicates whether this element that is identified by
&lt;cxxElementName&gt; exists (true) or not (false).

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown if a failure occurs
ascertaining whether the element exists.

-   Access:

Public

> CERT CXX-011229 \[An OMS C++ CAL API shall declare the public const
> function bool has&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/xs:sequence/xs:element\[@minOccurs='0'
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1)\]\`.\]

#### Member Function: enable&lt;cxxElementName&gt;

This method enables the element that is identified by the
&lt;cxxElementName&gt; making it available to be accessed and returns a
reference to the object being enabled. After invoking this method, the
has&lt;cxxElementName&gt;() method will return true and the
get&lt;cxxElementName&gt;() and set&lt;cxxElementName&gt;() methods will
be able to access the element.

Note: the enable function only includes complexTypes, Binary Primitives,
and List Primitives.

-   Signature:

&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
enable&lt;cxxElementName&gt;(uci::base::accessorType::AccessorType type
= uci::base::accessorType::null)

-   Return:

A reference to the object being enabled.

-   Parameters:

type: The accessor type (see Section 9.3, The Accessor Type Constants)
that is associated with the Accessor class that should be instantiated
when this element is enabled. The use of this parameter provides the
support for inheritance. Passing in the "null" accessor type constant is
the same as passing in the accessor type constant for the type of the
element.

-   Exceptions:

uci::base::UCIException: Exception thrown if a failure occurs enabling
the element.

-   Access:

Public

> CERT CXX-011230 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
> enable&lt;cxxElementName&gt;(uci::base::accessorType::AccessorType =
> uci::base::accessorType::null) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/xs:sequence/xs:element\[not(@maxOccurs='unbounded'
> or @maxOccurs&gt;1)\]\` where \`@type\` is an xs:complexType and
> \`@minOccurs='0'\` or \`@type\` is an xs:complexType with
> derivations.\]

#### SimpleList Member Function: enable&lt;cxxElementName&gt;

This method enables the element that is identified by the
&lt;cxxElementName&gt; making it available to be accessed and returns a
reference to the object being enabled. After invoking this method, the
has&lt;cxxElementName&gt;() method will return true and the
get&lt;cxxElementName&gt;() and set&lt;cxxElementName&gt;() methods will
be able to access the element.

-   Signature:

xs::&lt;cxxPrimitiveName&gt;& enable&lt;cxxElementName&gt;()

-   Return:

A reference to the object being enabled.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown if a failure occurs enabling
the element.

-   Access:

Public

> CERT CXX-012709 \[An OMS C++ CAL API shall declare the public
> non-static member function xs::&lt;cxxPrimitiveName&gt;&
> enable&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/xs:sequence/xs:element\[@minOccurs='0'
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1 or
> @type='uci:UniversallyUniqueIdentifierType')\]\` where \`@type\` is or
> derives from an "XSD Data Type" of "The Binary Primitive Types" or
> "The List Primitive Types" tables.\]

#### Member Function: clear&lt;cxxElementName&gt;

This method clears the element that is identified by the
&lt;cxxElementName&gt; making it unavailable to be accessed and returns
a reference to the parent object. After invoking this method, the
has&lt;cxxElementName&gt;() method will return false and the
get&lt;cxxElementName&gt;() and set&lt;cxxElementName&gt;() methods will
not be able to access the element.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
clear&lt;cxxElementName&gt;()

-   Return:

A reference to the object on which this method was called.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown if a failure occurs clearing
the element.

-   Access:

Public

> CERT CXX-011231 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> clear&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/xs:sequence/xs:element\[@minOccurs='0'
> and not(@maxOccurs='unbounded' or @maxOccurs&gt;1)\]\`.\]

#### Member Function: getUCITypeVersion

-   Signature:

static UCI\_EXPORT std::string getUCITypeVersion()

-   Return:

A constant reference to the Accessor’s version attribute that was
initialized from \`xs:complexType/@uci:version\`.

-   Parameters:

None

-   Exceptions:

None

-   Access:

Public

> CERT CXX-011410 \[An OMS C++ CAL API shall declare the public static
> member function std::string getUCITypeVersion() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType\`.\]

#### Method: create

##### Overload for Default Initialized

Creates an OMS cxxTypeName and returns an Accessor that provides access
to that newly created cxxTypeName.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
create(uci::base::AbstractServiceBusConnection\*
abstractServiceBusConnection = null)

-   Return:

A reference to the Accessor that provides access to the newly
constructed cxxTypeName.

-   Parameters:

abstractServiceBusConnection: The AbstractServiceBusConnection used to
establish the communications link for the \[writer/reader\] and apply
the appropriate QoS settings, topic mappings, or other properties.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the construction of the OMS cxxTypeName or the Accessor that provides
access to that cxxTypeName.

-   Access:

Public

> CERT CXX-011066 \[An OMS C++ CAL API shall declare the public static
> member function &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> create(uci::base::AbstractServiceBusConnection\* = NULL) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType\[not(@abstract='true')\]\`.\]

##### Overload for Copying

Creates an OMS cxxTypeName and returns an Accessor that provides access
to that newly created cxxTypeName. The contents of the newly created
message are initialized to the contents of the OMS cxxTypeName that the
specified Accessor (accessor) provides access to.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;& create(const
&lt;cxxRootNamespace&gt;::type::&lt;cxxTypeName&gt; & accessor,
uci::base::AbstractServiceBusConnection\* abstractServiceBusConnection =
null)

-   Return:

A reference to the Accessor that provides access to the newly
constructed cxxTypeName.

-   Parameters:

accessor: The Accessor that provides access to the OMS cxxTypeName that
is used to initialize the newly created OMS cxxTypeName.

abstractServiceBusConnection: The AbstractServiceBusConnection used to
establish the communications link for the \[writer/reader\] and apply
the appropriate QoS settings, topic mappings, or other properties.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the construction of the OMS cxxTypeName or the Accessor that provides
access to that cxxTypeName.

-   Access:

Public

> CERT CXX-011067 \[An OMS C++ CAL API shall declare the public static
> member function &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> create(const &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&,
> uci::base::AbstractServiceBusConnection\* = NULL) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType\[not(@abstract='true')\]\`.\]

#### Method: destroy

Destroys the specified Accessor and the OMS cxxTypeName that is accessed
by that accessor. Any use of the specified Accessor following the
invocation of this method will result in undefined behavior.

-   Signature:

void destroy(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
accessor)

-   Return:

None.

-   Parameters:

accessor: The Accessor that is to be destroyed.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the destruction of the Accessor.

-   Access:

Public

> CERT CXX-011068 \[An OMS C++ CAL API shall declare the public static
> member function void
> destroy(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType\[not(@abstract='true')\]\`.\]

Global Element Accessors
------------------------

Accessors whose rule set is satisfied by a global declaration (Section
2.8, The Schema Declaration) are known as global Accessors. Similarly,
Accessor Instances instantiated from these global Accessors are known as
global Accessor Instances.

### Global Element Accessor Header Files

When global Accessor Instances are realized, a C++ header file, known as
the Accessor header file, is created.

A simple way of meeting this requirement is to write the declarations
directly to this file. An alternative is to generate a set of C++ header
files and then include these header files in the Accessor header file.
The choice of which mechanism to use is not specified as part of this
document.

Once the global Accessor Instance has been realized, the header file is
closed along with any opened namespace to implement the Accessor.

Not specified in this document is the generation of any include
statements or other compiler directives that are required in order for
the header files to be compiled. The generation of these statements is a
general requirement on the OMS Schema Compiler.

### Realizing Global Element Accessor Instances

When realizing a global Accessor, a set of actions are commonly taken.
These steps can include opening the header(s) discussed in the section
Global Accessor Header Files and including all necessary file(s).

### Realizing the Factory Methods

The Accessor classes provide static factory methods which are
responsible for constructing and destroying connections to the Accessor
data type. If the Accessor is a Global Element then the corresponding
factory methods for construction and destruction of the Accessor class’s
nested Reader and Writer classes are also provided.

#### Method: createReader

Creates a Reader that can read an OMS Message.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader&
createReader(const std::string& topic,
uci::base::AbstractServiceBusConnection \*abstractServiceBusConnection)

-   Return:

A reference to the newly constructed Reader.

-   Parameters:

topic: The name of the topic that the reader is to subscribe to such
that it can read messages published to that topic.

abstractServiceBusConnection: The AbstractServiceBusConnection used to
establish the communications link for the \[writer/reader\] and apply
the appropriate QoS settings, topic mappings, or other properties.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the construction of the Reader.

-   Access:

Public

> CERT CXX-005494 \[An OMS C++ CAL API shall declare the public static
> member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader&
> createReader(const std::string&,
> uci::base::AbstractServiceBusConnection\*) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:element\`.\]

#### Method: destroyReader

Destroys the specified Reader (reader). Once destroyed, any future use
of references to the Reader will result in undefined behavior.

-   Signature:

void
destroyReader(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader&
reader)

-   Return:

None.

-   Parameters:

reader: The Reader to be destroyed.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the destruction of the Reader.

-   Access:

Public

> CERT CXX-005495 \[An OMS C++ CAL API shall declare the public static
> member function void
> destroyReader(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader&)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> for each \`/xs:schema/xs:element\`.\]

#### Method: createWriter

Creates a Writer that can write an OMS Message.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer&
createWriter(const std::string& topic,
uci::base::AbstractServiceBusConnection \*abstractServiceBusConnection)

-   Return:

A reference to the newly constructed Writer.

-   Parameters:

topic: The name of the topic that messages written using this writer are
to be published to.

abstractServiceBusConnection: The AbstractServiceBusConnection used to
establish the communications link for the \[writer/reader\] and apply
the appropriate QoS settings, topic mappings, or other properties.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the construction of the Writer.

-   Access:

Public

> CERT CXX-005499 \[An OMS C++ CAL API shall declare the public static
> member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer&
> createWriter(const std::string&,
> uci::base::AbstractServiceBusConnection\*) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:element\`.\]

#### Method: destroyWriter

Destroys the specified Writer (writer). Once destroyed, any future use
of references to the Writer will result in undefined behavior.

-   Signature:

void
destroyWriter(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer&
writer)

-   Return:

None.

-   Parameters:

writer: The Writer to be destroyed.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the destruction of the Writer.

-   Access:

Public

> CERT CXX-005506 \[An OMS C++ CAL API shall declare the public static
> member function void
> destroyWriter(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer&)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> for each \`/xs:schema/xs:element\`.\]

### Global Element Accessor Special C++ Classes

When global Accessor Instances are realized, one or more common classes
are to be generated. These classes include:

-   The Accessor Instance’s Listener class.

-   The Accessor Instance’s Reader class.

-   The Accessor Instance’s Writer class.

The sections that follow detail how these classes are generated.

#### Realizing the Listener Class

The Listener class is responsible for providing support needed to listen
for an incoming OMS Messages.

> CERT CXX-005546 \[An OMS C++ CAL API shall define the public member
> class "Listener" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class that
> publicly and singly inherits from "uci::base::Listener" when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each \`/xs:schema/xs:element\`.\]

For example, if Listener is declared in the &lt;cxxTypeName&gt;
namespace, then the following declaration can be generated:

class Listener : public uci::base::Listener

##### Method: handleMessage

This method handles received OMS Messages.

-   Signature:

virtual void handleMessage(const
&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;& message) = 0;

-   Return:

None.

-   Parameters:

message: The OMS Message that is to be handled by this method.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the handling of the message.

-   Access:

Public

> CERT CXX-005564 \[An OMS C++ CAL API shall declare the public
> non-static member function void handleMessage(const
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener"
> class as pure virtual for each \`/xs:schema/xs:element\`.\]

#### Realizing the Reader Class

The Reader class is responsible for providing support needed to read an
OMS Message.

> CERT CXX-005567 \[An OMS C++ CAL API shall define the public member
> class "Reader" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class that
> publicly and singly inherits from "uci::base::Reader" when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each \`/xs:schema/xs:element\`.\]

For example, if Reader is declared in the &lt;cxxTypeName&gt; namespace,
then the following declaration can be generated:

class Reader : public uci::base::Reader

##### Destructor: ~Reader

This destructor’s visibility is protected in order to enforce the use of
the &lt;cxxTypeName&gt; destroyReader() method.

-   Signature:

~Reader()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-012710 \[An OMS C++ CAL API shall disable access to the
> destructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader" class
> for each \`/xs:schema/xs:element\`.\]

##### Method: addListener

Adds a Listener to this Reader that will handle incoming OMS Messages.

-   Signature:

void
addListener(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener
& listener)

-   Return:

None.

-   Parameters:

listener: A reference to the Listener to add to this Reader.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the addition of the Listener to this Reader.

-   Access:

Public

> CERT CXX-011072 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> addListener(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener&)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader"
> class for each \`/xs:schema/xs:element\`.\]

##### Method: removeListener

Removes the specified Listener from this Reader.

-   Signature:

void
removeListener(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener&
listener)

-   Return:

None.

-   Parameters:

listener: A reference to the Listener that is to be removed from this
Reader.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the removal of the Listener from this Reader.

-   Access:

Public

> CERT CXX-011073 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> removeListener(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener&)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader"
> class for each \`/xs:schema/xs:element\`.\]

##### Method: read

Reads one or more OMS Messages that are received by this Reader. An
exception is thrown if this Reader already has a Listener that has been
previously added that is listening for OMS Messages. This method allows
for the specification of a timeout value and a maximum number of
messages to process. If no timeout is desired, it is recommended that
the readNoWait method be used instead.

-   Signature:

unsigned long read(unsigned long timeout,

unsigned long numberOfMessages,

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener &
listener)

-   Return:

The number of messages handled.

-   Parameters:

timeout: Maximum time in microseconds to wait for new messages to
arrive. The timeout is ignored if one or more messages are already
queued. After the first invocation of the listener’s handleMessage(),
this timeout is ignored. A zero indicates that the read should wait
forever.

numberOfMessages: The maximum number of messages that will be handled by
the read operation

listener: A reference to the Listener that will handle the messages read
during this invocation.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the reading of the OMS Messages.

-   Access:

Public

> CERT CXX-011074 \[An OMS C++ CAL API shall declare the public
> non-static member function unsigned long read(unsigned long, unsigned
> long,
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener&) of
> the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader"
> class for each \`/xs:schema/xs:element\`.\]

##### Method: readNoWait()

Reads one or more OMS Messages that are received by this Reader. An
exception is thrown if this Reader already has a Listener that has been
previously added that is listening for OMS Messages. The behavior of
this method is similar to that of the read method, except no timeout
value is applied. If no messages are queued and ready to be processed
when this method is invoked, the method will return immediately.

-   Signature:

unsigned long readNoWait(unsigned long numberOfMessages,

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener&
listener)

-   Return:

The number of messages handled.

-   Parameters:

numberOfMessages: The maximum number of messages that will be handled by
the readNoWait operation

listener: A reference to the Listener that will handle the invocation.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs during
the reading of the OMS Messages.

-   Access:

Public

> CERT CXX-011075 \[An OMS C++ CAL API shall declare the public
> non-static member function unsigned long readNoWait(unsigned long,
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Listener&) of
> the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader"
> class for each \`/xs:schema/xs:element\`.\]

##### Method: close

Closes this Reader. Once closed, any further attempts to use this Reader
to read messages, either by adding new Listeners or by invoking the
read() or readNoWait() methods, will result in an undefined behavior.

-   Signature:

void close()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs closing
this Reader.

-   Access:

Public

> CERT CXX-011076 \[An OMS C++ CAL API shall declare the public
> non-static member function void close() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader" class
> for each \`/xs:schema/xs:element\`.\]

##### Default Constructor: Reader

This constructor’s visibility is protected in order to enforce the use
of the &lt;cxxTypeName&gt; createReader() method.

-   Signature:

Reader()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Reader fails.

-   Access:

Protected

> CERT CXX-005608 \[An OMS C++ CAL API shall disable access to the
> default constructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader" class
> for each \`/xs:schema/xs:element\`.\]

##### Default Copy Constructor: Reader

The compiler’s default copy constructor is not used since the copy
construction has to be protected and only visible to derived classes.
This is required in order to enforce the use of the &lt;cxxTypeName&gt;
createReader() method.

-   Signature:

Reader(const &lt;cxxTypeName&gt;::Reader& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Reader that is used to initialize the contents of the newly
constructed Reader.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Reader fails.

-   Access:

Protected

> CERT CXX-005615 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader" class
> for each \`/xs:schema/xs:element\`.\]

##### Operator: operator=

Sets the contents of this Reader to the contents of the specified Reader
on the right hand side (rhs) of the assignment operator. This operator’s
access is protected in order to enforce the use of the
&lt;cxxTypeName&gt; createReader() method.

-   Signature:

Reader& operator=(const &lt;cxxTypeName&gt;Reader& rhs)

-   Return:

A reference to this Reader.

-   Parameters:

rhs: The Reader on the right hand side (rhs) of the assignment operator
which is to be used to initialize this Reader.

-   Exceptions:

None.

-   Access:

Protected

> CERT CXX-011077 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Reader" class
> for each \`/xs:schema/xs:element\`.\]

#### Realizing the Writer Class

A Writer class is responsible for providing support needed to write an
OMS Message.

> CERT CXX-005624 \[An OMS C++ CAL API shall define the public member
> class "Writer" class of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class that
> publicly and singly inherits from "uci::base::Writer" when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each \`/xs:schema/xs:element\`.\]

For example, if Writer is declared in the &lt;cxxTypeName&gt; namespace,
then the following declaration can be generated:

class Writer : public uci::base::Writer

##### Destructor: ~Writer

This destructor’s visibility is protected in order to enforce the use of
the &lt;cxxTypeName&gt; destroyWriter() method.

-   Signature:

~Writer()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

None.

-   Access:

Protected.

> CERT CXX-012711 \[An OMS C++ CAL API shall disable access to the
> destructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer" class
> for each \`/xs:schema/xs:element\`.\]

##### Method: write

Writes the OMS Message to the topic specified when this Writer was
created.

-   Signature:

void write(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
accessor)

-   Return:

None.

-   Parameters:

accessor: The Accessor that provides access to the message that is to be
written.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error writing the
message.

-   Access:

Public

> CERT CXX-011078 \[An OMS C++ CAL API shall declare the public
> non-static member function void
> write(&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer" class
> for each \`/xs:schema/xs:element\`.\]

##### Method: close

Closes this Writer. Once closed, any further attempts to use this Writer
to write messages will result in an undefined behavior.

-   Signature:

void close()

-   Return:

None.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs closing
this Writer.

-   Access:

Public

> CERT CXX-011079 \[An OMS C++ CAL API shall declare the public
> non-static member function void close() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer" class
> for each \`/xs:schema/xs:element\`.\]

##### Default Constructor: Writer

This constructor’s visibility is protected in order to enforce the use
of the &lt;cxxTypeName&gt; createWriter() method.

-   Signature:

Writer()

-   Return:

N/A

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Writer fails.

-   Access:

Protected

> CERT CXX-005653 \[An OMS C++ CAL API shall disable access to the
> default constructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer" class
> for each \`/xs:schema/xs:element\`.\]

##### Default Copy Constructor: Writer

The compiler’s default copy constructor is not used since the copy
construction has to be protected and only visible to derived classes.
This is required in order to enforce the use of the &lt;cxxTypeName&gt;
createWriter() method.

-   Signature:

Writer(const &lt;cxxTypeName&gt;Writer& rhs)

-   Return:

N/A

-   Parameters:

rhs: The Writer that is used to initialize the contents of the newly
constructed Writer.

-   Exceptions:

uci::base::UCIException: Exception thrown if the construction of the
Writer fails.

-   Access:

Protected

> CERT CXX-005660 \[An OMS C++ CAL API shall disable access to the copy
> constructor of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer" class
> for each \`/xs:schema/xs:element\`.\]

##### Operator: operator=

Sets the contents of this Writer to the contents of the specified Writer
on the right hand side (rhs) of the assignment operator. This operator’s
access is protected in order to enforce the use of the
&lt;cxxTypeName&gt; createWriter() method.

-   Signature:

Writer& operator=(const &lt;cxxTypeName&gt;Writer& rhs)

-   Return:

A reference to this Writer.

-   Parameters:

rhs: The Writer on the right hand side (rhs) of the assignment operator
which is to be used to initialize this Writer.

-   Exceptions:

None.

-   Access:

Protected

> CERT CXX-011080 \[An OMS C++ CAL API shall disable access to the copy
> assignment operator of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::Writer" class
> for each \`/xs:schema/xs:element\`.\]

Accessor Specification
----------------------

The sections that follow provide the details for each type of Accessor.
Each subsection that describes an Accessor contains one or more of the
following subsections:

-   Validation Rules: These rules are used to validate that the Accessor
    Instance instantiated from the selected Accessor will be a valid
    Accessor Instance. These rules specify what the Instance’s
    attributes have to be in order for that Instance to be considered
    valid.

-   Realizing the Accessor Instance: discusses the actions taken in
    order to realize the Accessor Instance, i.e., what C++ software
    needs to be generated. For most data types, this involves the
    declaration of a C++ Accessor class that is responsible for
    providing access to the data.

-   Realizing the Accessor Instance Access Methods: discusses how to
    generate the C++ methods that provide the mechanism to access the
    data that the Accessor Instance is to provide access to. For simple
    primitive data types, these methods provide direct access to the
    data. For all other types, these methods provide access to the
    Accessors that provide access to the data.

The Primitive Accessors
-----------------------

The Primitive Accessors are a class of Accessors that provide access to
the XSD Primitive data types that are described in Section 9.1, The
Primitive Types. These Accessors are different from all other types of
accessors in that instances instantiated from these Accessors are never
bound to a declaration of a data type in an OMS Schema Definition. The
reason this binding never occurs is that these declarations are never
included in an XSD Definition as they are “built-in” data types.
Instead, the following three requirements apply:

### The SimplePrimitive Accessors

The SimplePrimitive Accessors are responsible for providing access to
the Simple Primitive data types that are listed in Table 9.1-1, The
Simple Primitive Types.

#### Realizing the SimplePrimitive Instance

Support for all simple primitive data types is provided via an
AccessorType constant (Section 9.3, The Accessor Type Constants) and one
C++ class, an accessor class that provides access to the simple
primitive data type. Realizing a SimplePrimitive Instance will result in
the generation of the AccessorType constant and a SimplePrimitive
Accessor class.

##### The SimplePrimitive Accessor Type

##### The SimplePrimitive Accessor Class

This class will provide access to a SimplePrimitive data type as
specified for the Instance being realized in Table 9.1-1, The Simple
Primitive Types.

> CERT CXX-005765 \[An OMS C++ CAL API shall define the
> "&lt;cxxPrimitiveName&gt;Accessor" class in the "uci::base" namespace
> that publicly and singly inherits from "uci::base::Accessor" for each
> "C++ Data Type" of "The Simple Primitive Types" table when the file
> "uci/base/&lt;cxxPrimitiveName&gt;Accessor.h" is included.\]

###### Method: get&lt;cxxPrimitiveName&gt;Value

Returns the value accessed by this Accessor.

-   Signature:

xs::&lt;cxxPrimitiveName&gt; get&lt;cxxPrimitiveName&gt;Value() const

-   Return:

The value accessed by this Accessor.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value accessed by this Accessor.

-   Access:

Public

> CERT CXX-005775 \[An OMS C++ CAL API shall declare the public const
> member function xs::&lt;cxxPrimitiveName&gt;
> get&lt;cxxPrimitiveName&gt;Value() of the
> "uci::base::&lt;cxxPrimitiveName&gt;Accessor" class for each "C++ Data
> Type" of "The Simple Primitive Types" table.\]

###### Method: set&lt;cxxPrimitiveName&gt;Value

Sets the value accessed by this Accessor to the specified value and
returns a reference to the parent object.

-   Signature:

&lt;parentQualifiedCxxName&gt;&
set&lt;cxxName&gt;Value(&lt;qualifiedCxxPrimitiveName&gt; value)

-   Return:

A reference to the object on which this method was called.

-   Parameters:

value: The value used to set the value that is accessed by this
Accessor.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs upon
setting the value accessed by this Accessor.

-   Access:

Public

> CERT CXX-011087 \[An OMS C++ CAL API shall declare the public
> non-static member function
> uci::base::&lt;cxxPrimitiveName&gt;Accessor&
> set&lt;cxxPrimitiveName&gt;Value(xs::&lt;cxxPrimitiveName&gt;) of the
> "uci::base::&lt;cxxPrimitiveName&gt;Accessor" class for each "C++ Data
> Type" of "The Simple Primitive Types" table.\]

###### Operator: operator=

####### Overload for SimplePrimitive Accessor

Sets the value accessed by this Accessor to the value that is accessed
by the Accessor on the right hand side (rhs) of the assignment operator.

-   Signature:

uci::base::&lt;cxxPrimitiveName&gt;Accessor& operator=(const
&lt;cxxPrimitiveName&gt;Accessor& rhs)

-   Return:

A reference to the object on which this method was called.

-   Parameters:

rhs: The Accessor on the right hand side (rhs) of the assignment
operator which provides access to the value that is to be used to set
the value that is accessed by this Accessor.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs upon
setting the value accessed by this &lt;cxxPrimitiveName&gt;Accessor.

-   Access:

Public

> CERT CXX-011088 \[An OMS C++ CAL API shall declare the public
> non-static member function
> uci::base::&lt;cxxPrimitiveName&gt;Accessor& operator=(const
> uci::base::&lt;cxxPrimitiveName&gt;Accessor&) of the
> "uci::base::&lt;cxxPrimitiveName&gt;Accessor" class for each "C++ Data
> Type" of "The Simple Primitive Types" table.\]

####### Overload for Primitive Value

Sets the value accessed by this Accessor to the specified value and
returns a reference to the parent object.

-   Signature:

uci::base::&lt;cxxPrimitiveName&gt;Accessor&
operator=(&lt;qualifiedCxxPrimitiveName&gt; value)

-   Return:

A reference to the object on which this method was called.

-   Parameters:

value: The value used to set the value that is accessed by this
Accessor. Exceptions: uci::base::UCIException: Exception thrown when an
error occurs upon setting the value accessed by this
&lt;cxxPrimitiveName&gt;Accessor.

-   Access:

Public

> CERT CXX-013023 \[An OMS C++ CAL API shall declare the public
> non-static member function
> uci::base::&lt;cxxPrimitiveName&gt;Accessor& operator=(
> xs::&lt;cxxPrimitiveName&gt;) of the
> "uci::base::&lt;cxxPrimitiveName&gt;Accessor" class for each "C++ Data
> Type" of "The Simple Primitive Types" table.\]

###### Operator: operator xs::&lt;cxxPrimitiveAccessor&gt;

Returns the value accessed by this Accessor.

-   Signature:

operator xs::&lt;cxxPrimitiveAccessor&gt;() const

-   Return:

The value accessed by this Accessor.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the value accessed by this Accessor.

-   Access:

Public.

> CERT CXX-011089 \[An OMS C++ CAL API shall declare the conversion
> operator xs::&lt;cxxPrimitiveName&gt;() of the
> "uci::base::&lt;cxxPrimitiveName&gt;Accessor" class for each "C++ Data
> Type" of "The Simple Primitive Types" table.\]

The Simple Accessors
--------------------

### The SimpleRestriction Accessor

The SimpleRestriction Accessor is responsible for handling declarations
of simple, atomic restrictions.

#### An Example

The following is an example of a simple restriction declaration.

For this example, assume that the qualifiedCxxName was specified as
“uci::type::UserDataType”.

&lt;xs:simpleType name="UserDataType"&gt;

&lt;xs:restriction base=“xs:int”&gt;

&lt;/xs:restriction&gt;

&lt;/xs:simpleType&gt;

Given this example, the following declaration would be generated:

namespace uci {

namespace type {

typedef uci::base::IntAccessor UserDataType;

typedef xs::int UserDataTypeValue;

}

}

#### Realizing the SimpleRestriction Instance

> CERT CXX-006143 \[An OMS C++ CAL API shall define the public member
> type "&lt;cxxTypeName&gt;" in the "&lt;cxxTargetNamespace&gt;::type"
> namespace equivalent to the type
> "uci::base::&lt;cxxPrimitiveName&gt;Accessor" when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each
> \`/xs:schema/xs:simpleType\[xs:restriction\[not(xs:enumeration)\]\]\`
> where \`xs:restriction/@base\` is or derives from an "XSD Data Type"
> of "The Simple Primitive Types" table.\]

Using the example declaration declared above, the following declaration
can be generated:

typedef uci::base::IntAccessor UserDataType;

> CERT CXX-006144 \[An OMS C++ CAL API shall define the public member
> type "&lt;cxxTypeName&gt;Value" in the
> "&lt;cxxTargetNamespace&gt;::type" namespace equivalent to the type
> "xs::&lt;cxxPrimitiveName&gt;" when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each
> \`/xs:schema/xs:simpleType\[xs:restriction\[not(xs:enumeration)\]\]\`
> where \`xs:restriction/@base\` is or derives from an "XSD Data Type"
> of "The Simple Primitive Types" table.\]

Using the example declaration declared above, the following declaration
can be generated:

typedef uci::xs::Int UserDataTypeValue

> CERT CXX-006553 \[An OMS C++ CAL API shall define the public member
> type "&lt;cxxTypeName&gt;" in the "&lt;cxxTargetNamespace&gt;::type"
> namespace equivalent to the type "xs::&lt;cxxPrimitiveName&gt;" when
> the file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[not(ancestor::xs:schema/@targetNamespace =
> '<span
> class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>' and
> @name = 'UniversallyUniqueIdentifierType') and
> xs:restriction\[not(xs:enumeration)\]\]\` whose
> \`xs:restriction/@base\` is or derives from an "XSD Data Type" of "The
> String Primitive Types", "The Numeric String Primitive Types", "The
> Binary Primitive Types", or "The List Primitive Types" tables.\]

Using the example declaration declared above, the following declaration
can be generated:

typedef xs::String UserDataType;

### The Universally Unique Identifier Accessor

The Universally Unique Identifier (UUID) Accessor is responsible for
handling declarations of Universally Unique Identifiers.

#### An Example

The following is an example of a simple restriction declaration.

For this example, assume that the qualifiedCxxName as specified as
“uci::type::UserDataType”.

&lt;xs:complexType name="UserDataType"&gt;

&lt;xs:sequence&gt;

&lt;xs:element name="UUID"
type="uci:UniversallyUniqueIdentifierType"/&gt;

&lt;/xs:sequence&gt;

&lt;/xs:complexType&gt;

Given this example, the following declaration would be generated:

namespace uci {

namespace type {

class UserDataType : public virtual uci::base::Accessor {

public:

virtual uci::base::UUID getUUID() const {...}

virtual void setUUID(const uci::base::UUID& value) {...}

...

};

}

}

#### Realizing the UUID Instance Access Methods

##### Method: get&lt;cxxElementName&gt;

Returns the UUID.

-   Signature:

uci::base::UUID get&lt;cxxElementName&gt;() const

-   Return:

The UUID.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown if a failure occurs returning
the UUID.

-   Access:

Public

> CERT CXX-006154 \[An OMS C++ CAL API shall declare the public const
> member function uci::base::UUID get&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:sequence|xs:choice)/xs:element\[@type="uci:UniversallyUniqueIdentifierType"\]\`.\]

##### Method: set&lt;cxxElementName&gt;

Performs a deep copy of the specified UUID (uuid) and sets the UUID to
the resultant copy.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
set&lt;cxxElementName&gt;(const uci::base::UUID& uuid)

-   Return:

A reference to the object on which this method was called

Parameters:

uuid: The UUID that is used to set the UUID.

-   Exceptions:

uci::base::UCIException: Exception thrown if a failure occurs setting
this UUID.

-   Access:

Public

> CERT CXX-011054 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxElementName&gt;(const uci::base::UUID&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(xs:complexContent/xs:extension|.)/(xs:sequence|xs:choice)/xs:element\[@type="uci:UniversallyUniqueIdentifierType"\]\`.\]

### The Enumeration Accessor

The Enumeration Accessor is responsible for handling declarations of
enumerations.

#### An Example

The following is an example of an enumeration declaration.

For this example, assume that the qualifiedCxxName was specified as
“uci::type::UserDataType”.

&lt;xs:simpleType name="UserDataType"&gt;

&lt;xs:restriction base="xs:string"&gt;

&lt;xs:enumeration value=“item1” /&gt;

&lt;xs:enumeration value=“item2” /&gt;

&lt;xs:enumeration value=“item3” /&gt;

&lt;/xs:restriction&gt;

&lt;/xs:simpleType&gt;

Given this example, the following declaration would be generated:

namespace uci {

namespace type {

class UserDataType : public virtual uci::base::Accessor {

public:

enum EnumerationItem {

enumNotSet,

UCI\_ITEM1,

UCI\_ITEM2,

UCI\_ITEM3,

enumMaxExclusive

};

const UserDataType& operator=(const UserDataType& rhs) {...}

const UserDataType& operator=(EnumerationItem rhs) {...}

void setValue(EnumerationItem item) {...}

EnumerationItem getValue(bool testForValidity=true) const {...}

int getNumberOfItems() const noexcept {...}

bool isValid() const noexcept {...}

static bool isValid(EnumerationItem item) noexcept {...}

static bool isValid(const std::string& name) {...}

bool operator==(const UserDataType& rhs) const {...}

bool operator!=(const UserDataType& rhs) const {...}

bool operator&lt;(const UserDataType& rhs) const {...}

bool operator&lt;=(const UserDataType& rhs) const {...}

bool operator&gt;(const UserDataType& rhs) const {...}

bool operator&gt;=(const UserDataType& rhs) const {...}

bool operator==(EnumerationItem rhs) const {...}

friend bool operator==(EnumerationItem lhs, const UserDataType& rhs)
{...}

bool operator!=(EnumerationItem rhs) const {...}

friend bool operator!=(EnumerationItem lhs, const UserDataType& rhs)
{...}

bool operator&lt;(EnumerationItem rhs) const {...}

friend bool operator&lt;(EnumerationItem lhs, const UserDataType& rhs)
{...}

bool operator&lt;=(EnumerationItem rhs) const {...}

friend bool operator&lt;=(EnumerationItem lhs, const UserDataType& rhs)
{...}

bool operator&gt;(EnumerationItem rhs) const {...}

friend bool operator&gt;(EnumerationItem lhs, const UserDataType& rhs)
{...}

bool operator&gt;=(EnumerationItem rhs) const {...}

friend bool operator&gt;=(EnumerationItem lhs, const UserDataType& rhs)
{...}

static std::string toName(EnumerationItem item) {...}

static EnumerationItem fromName(const std::string& itemName) {...}

virtual std::string toName() const {...}

virtual void setValueFromName(const std::string& itemName) {...}

...

};

}

}

template&lt;typename charT, typename traits&gt;

std::basic\_ostream&lt;charT, traits&gt;&

operator&lt;&lt;(std::basic\_ostream&lt;charT, traits&gt;& oStream,
const uci::type::UserDataType& enumeration)

#### Realizing the Enumeration Instance

> CERT CXX-006166 \[An OMS C++ CAL API shall define the
> "&lt;cxxTypeName&gt;" class in the "&lt;cxxTargetNamespace&gt;::type"
> namespace that publicly and singly inherits from "uci::base::Accessor"
> when the file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h"
> is included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

For example, if cxxName is specified as UserEnumeration, then the
following declaration can be generated:

class UserEnumeration : public uci::base::Accessor

> CERT CXX-006172 \[An OMS C++ CAL API shall define the public member
> enum "EnumerationItem" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class with the
> enumerators "enumNotSet" defined as 0 and "enumMaxExclusive" defined
> as \`count(xs:restriction/xs:enumeration) + 1\` for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]
>
> CERT CXX-006173 \[An OMS C++ CAL API shall define an enumerator
> "&lt;toUpperCase(cxxTargetNamespace)&gt;\_&lt;enumItem&gt;" in the
> enum member type "EnumerationItem" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class with a
> value greater than "enumNotSet" and less than "enumMaxExclusive" where
> &lt;enumItem&gt; is the \`xs:restriction/xs:enumeration/@value\`
> translated using the “Generating C++ Data Type and Enumeration Item
> Names” section "Enumerated Item Name Translation Rules" for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

For example, if the name of the enumerated item in the enumerationItems
list is “item1” and the namespace was “uci”, then the generated name
that would be used in the C++ enumeration would be “UCI\_ITEM1”.

From the above example, the following declaration can be generated:

enum EnumerationItem {

enumNotSet,

UCI\_ITEM1,

UCI\_ITEM2,

UCI\_ITEM3,

enumMaxExclusive

};

Note that Enumerations can exist in either a valid or an invalid state.
An Enumeration is said to be valid if the enumerated item that is
accessed by the Enumeration is greater than enumNotSet and is less than
enumMaxExclusive as specified in that Enumeration’s EnumerationItem
enumeration.

##### Operator: operator=

###### Overload for Enumeration

Sets the EnumerationItem that is accessed by this Enumeration to the
EnumerationItem that is accessed by the Enumeration on the right hand
side (rhs) of the assignment operator.

-   Signature:

&lt;cxxTypeName&gt;& operator=(const &lt;cxxTypeName&gt;& rhs)

-   Return:

A reference to this Enumeration.

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the assignment
operator that accesses the EnumerationItem that is to be used to set the
EnumerationItem that is accessed by this Enumeration.

-   Exceptions:

uci::base::UCIException: Exception thrown if the assignment fails.

-   Access:

Public

> CERT CXX-006211 \[An OMS C++ CAL API shall declare the public
> non-static member function &lt;cxxTypeName&gt;& operator=(const
> &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]
>
> GUID CXX-006212 \[An exception should be thrown if rhs is not valid.\]

###### Overload for EnumerationItem

Sets the EnumerationItem that is accessed by this Enumeration to the
EnumerationItem on the right hand side (rhs) of the assignment operator.

-   Signature:

&lt;cxxTypeName&gt;& operator=(EnumerationItem rhs)

-   Return:

A reference to this Enumeration.

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the assignment
operator that is used to set the EnumerationItem that is accessed by
this Enumeration.

-   Exceptions:

None

-   Access:

Public

> CERT CXX-011062 \[An OMS C++ CAL API shall declare the public
> non-static member function &lt;cxxTypeName&gt;&
> operator=(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Method: setValue

Sets the EnumerationItem that is accessed by this Enumeration to the
specified item.

-   Signature:

void setValue(EnumerationItem item)

-   Return:

None

-   Parameters:

item: The value that is used to set the EnumerationItem that is accessed
by this Enumeration.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs setting
the EnumerationItem accessed by this Enumeration.

-   Access:

Public

> CERT CXX-011055 \[An OMS C++ CAL API shall declare the public
> non-static member function void setValue(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Method: getValue

Returns the EnumerationItem that is accessed by this Enumeration.

-   Signature:

EnumerationItem getValue(bool testForValidity=true) const

-   Return:

The EnumerationItem that is accessed by this Enumeration.

-   Parameters:

testForValidity: Specifies whether this Enumeration should be tested for
validity before accessing its EnumerationItem.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
the EnumerationItem that is accessed by this Enumeration.

-   Access:

Public

> CERT CXX-011149 \[An OMS C++ CAL API shall declare the public const
> member function EnumerationItem getValue(bool = true) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]
>
> GUID CXX-006229 \[True indicates that the validity check should be
> performed.\]
>
> GUID CXX-006230 \[False indicates that the validity check should not
> be performed.\]
>
> GUID CXX-006231 \[This parameter should be set to true by default.\]

##### Method: getNumberOfItems

Returns the number of enumerated items in this Enumeration excluding the
two special items, enumNotSet and enumMaxExclusive. Given the example
(Section 10.6.3.1, An Example), this method would return 3.

-   Signature:

int getNumberOfItems() const

throw()

-   Return:

The number of items in this Enumeration.

-   Parameters:

None

-   Exceptions:

None

-   Access:

Public

> CERT CXX-006240 \[An OMS C++ CAL API shall declare the public const
> member function int getNumberOfItems() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class as
> non-throwing for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Method: isValid

###### Non-Static Variant

Returns whether this Enumeration is valid (true) or not (false). This
Enumeration is valid if the EnumerationItem that is accessed by this
Enumeration is greater than this Enumeration’s enumNotSet and less than
this Enumeration’s enumMaxExclusive.

-   Signature:

bool isValid() const

throw()

-   Return:

A boolean indicating whether this Enumeration is valid (true) or not
(false).

-   Parameters:

None

-   Exceptions:

None

-   Access:

Public

> CERT CXX-011057 \[An OMS C++ CAL API shall declare the public const
> member function bool isValid() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class as
> non-throwing for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

###### Static Variant for EnumerationItem

Returns whether the value of specified EnumerationItem is valid (true)
or not (false). The EnumerationItem is valid if it is greater than this
Enumeration’s enumNotSet and less than this Enumeration’s
enumMaxExclusive.

-   Signature:

static bool isValid(EnumerationItem item)

throw()

-   Return:

A boolean indicating whether the item is valid (true) or not (false).

-   Parameters:

item: The EnumerationItem to test for validity.

-   Exceptions:

None

-   Access:

Public

> CERT CXX-006253 \[An OMS C++ CAL API shall declare the public static
> member function bool isValid(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class as
> non-throwing for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

###### Overload for String

Returns whether the specified name is a name of one of this
Enumeration’s EnumerationItems. The specified name must exactly match
one of the names in enumerateionItems list. If an EnumerationItem having
the specified name is found, it is considered valid if it is greater
than enumNotSet and less than enumMaxExclusive.

-   Signature:

static bool isValid(const std::string& name)

-   Return:

A boolean indicating whether the name is a name of a valid
EnumerationItem (true) or not (false).

-   Parameters:

name: The name of the EnumerationItem to be tested for validity.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006260 \[An OMS C++ CAL API shall declare the public static
> member function bool isValid(const std::string&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class as
> non-throwing for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator==(const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem accessed by this Enumeration is equal
to the EnumerationItem accessed by the Enumeration on the right hand
side (rhs) of the comparison operator, returning true if they are equal,
false otherwise.

-   Signature:

bool operator==(const &lt;cxxTypeName&gt;& rhs) const

-   Return:

A Boolean indicating whether the two Enumerations are equal (true) or
not (false).

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the assignment
operator that is to be compared to this Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006267 \[An OMS C++ CAL API shall declare the public const
> member function bool operator==(const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator!= (const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem accessed by this Enumeration is not
equal to the EnumerationItem accessed by the Enumeration on the right
hand side (rhs) of the comparison operator, returning true if they are
not equal, false otherwise.

-   Signature:

bool operator!=(const &lt;cxxTypeName&gt;& rhs) const

-   Return:

A Boolean indicating whether the two Enumerations are not equal (true)
or not (false).

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the assignment
operator that is to be compared to this Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006275 \[An OMS C++ CAL API shall declare the public const
> member function operator!=(const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&lt;(const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem accessed by this Enumeration is less
than the EnumerationItem accessed by the Enumeration on the right hand
side (rhs) of the comparison operator, returning true if this
Enumeration is less than rhs, false otherwise.

-   Signature:

bool operator&lt;(const &lt;cxxTypeName&gt;& rhs) const

-   Return:

A Boolean indicating whether this Enumeration is less than the
Enumeration on the right hand side (rhs) of the comparison operator.

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the comparison
operator that is to be compared to this Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006283 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&lt;(const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&lt;=(const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem accessed by this Enumeration is less
than or equal to the EnumerationItem accessed by the Enumeration on the
right hand side (rhs) of the comparison operator, returning true if this
Enumeration is less than or equal to rhs, false otherwise.

-   Signature:

bool operator&lt;=(const &lt;cxxTypeName&gt;& rhs) const

-   Return:

A Boolean indicating whether this Enumeration is less than or equal to
the Enumeration on the right hand side (rhs) of the comparison operator.

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the comparison
operator that is to be compared to this Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006291 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&lt;=(const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&gt;(const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem accessed by this Enumeration is
greater the EnumerationItem accessed by the Enumeration on the right
hand side (rhs) of the comparison operator, returning true if this
Enumeration is greater than rhs, false otherwise.

-   Signature:

bool operator&gt;(const &lt;cxxTypeName&gt;& rhs) const

-   Return:

A Boolean indicating whether this Enumeration is greater than the
Enumeration on the right hand side (rhs) of the comparison operator.

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the comparison
operator that is to be compared to this Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006299 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&gt;(const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&gt;=(const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem accessed by this Enumeration is
greater than or equal to the EnumerationItem accessed by the Enumeration
on the right hand side (rhs) of the comparison operator, returning true
if this Enumeration is greater than or equal to rhs, false otherwise.

-   Signature:

bool operator&gt;=(const &lt;cxxTypeName&gt;& rhs) const

-   Return:

A Boolean indicating whether this Enumeration is greater than or equal
to the Enumeration on the right hand side (rhs) of the comparison
operator.

-   Parameters:

rhs: The Enumeration on the right hand side (rhs) of the comparison
operator that is to be compared to this Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006307 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&gt;=(const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator==(EnumerationItem rhs)

Tests whether the EnumerationItem accessed by this Enumeration is equal
to the EnumerationItem on the right hand side (rhs) of the comparison
operator, returning true if they are equal, false otherwise.

-   Signature:

bool operator==(EnumerationItem rhs) const

-   Return:

A Boolean indicating whether the EnumerationItem that is accessed by
this Enumeration is equal to the specified EnumerationItem (rhs) (true)
or not (false).

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the comparison
operator that is to be compared to the EnumerationItem accessed by this
Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006315 \[An OMS C++ CAL API shall declare the public const
> member function bool operator==(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator==(EnumerationItem lhs, const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem on the left hand side (lhs) of the
comparison operator is equal to the EnumerationItem that is accessed by
the Enumeration on the right hand side (rhs) of the comparison operator,
returning true if they are equal, false otherwise.

-   Signature:

friend bool operator==(EnumerationItem lhs, const &lt;cxxTypeName&gt;&
rhs)

-   Return:

A Boolean indicating whether the EnumerationItem (lhs) is equal to the
EnumerationItem that is accessed by this Enumeration (rhs) (true) or not
(false).

-   Parameters:

lhs: The EnumerationItem on the left hand side of the comparison
operator that is to be tested.

rhs: The Enumeration on the right hand side of the comparison operator
that provides access to the EnumerationItem that is to be tested.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006323 \[An OMS C++ CAL API shall declare the friend function
> bool operator==(EnumerationItem, const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class when the
> file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator!= (EnumerationItem rhs)

Tests whether the EnumerationItem accessed by this Enumeration is not
equal to the EnumerationItem on the right hand side (rhs) of the
comparison operator, returning true if they are not equal, false
otherwise.

-   Signature:

bool operator!=(EnumerationItem rhs) const

-   Return:

A Boolean indicating whether the EnumerationItem that is accessed by
this Enumeration is not equal to the specified EnumerationItem (rhs)
(true) or not (false).

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the comparison
operator that is to be compared to the EnumerationItem accessed by this
Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006332 \[An OMS C++ CAL API shall declare the public const
> member function bool operator!=(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator!= (EnumerationItem lhs, const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem on the left hand side (lhs) of the
comparison operator is equal to the EnumerationItem that is accessed by
the Enumeration on the right hand side (rhs) of the comparison operator,
returning true if they are not equal, false otherwise.

-   Signature:

friend bool operator!=(EnumerationItem lhs, const &lt;cxxTypeName&gt;&
rhs)

-   Return:

A Boolean indicating whether the EnumerationItem (lhs) is not equal to
the EnumerationItem that is accessed by this Enumeration (rhs) (true) or
they are equal (false).

-   Parameters:

lhs: The EnumerationItem on the left hand side of the comparison
operator that is to be tested.

rhs: The Enumeration on the right hand side of the comparison operator
that provides access to the EnumerationItem that is to be tested.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006340 \[An OMS C++ CAL API shall declare the friend function
> bool operator!=(EnumerationItem, const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class when the
> file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&lt;(EnumerationItem rhs)

Tests whether the EnumerationItem accessed by this Enumeration is less
than the EnumerationItem on the right hand side (rhs) of the comparison
operator, returning true if this Enumeration is less than rhs, false
otherwise.

-   Signature:

bool operator&lt;(EnumerationItem rhs) const

-   Return:

A Boolean indicating whether the EnumerationItem accessed by this
Enumeration is less than the EnumerationItem on the right hand side
(rhs) of the comparison operator (true) or not (false).

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the comparison
operator that is to be compared to the EnumerationItem accessed by this
Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006349 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&lt;(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&lt;(EnumerationItem lhs, const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem on the left hand side (lhs) of the
comparison operator is less than the EnumerationItem that is accessed by
the Enumeration on the right hand side (rhs) of the comparison operator,
returning true if the EnumerationItem is less than rhs, false otherwise.

-   Signature:

friend bool operator&lt;(EnumerationItem lhs, const &lt;cxxTypeName&gt;&
rhs)

-   Return:

A Boolean indicating whether the EnumerationItem (lhs) is less than the
EnumerationItem that is accessed by the Enumeration on the right hand
side of the comparison operator (rhs) (true) or not (false).

-   Parameters:

lhs: The EnumerationItem on the left hand side of the comparison
operator that is to be tested.

rhs: The Enumeration on the right hand side of the comparison operator
that provides access to the EnumerationItem that is to be tested.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006357 \[An OMS C++ CAL API shall declare the friend function
> bool operator&lt;(EnumerationItem, const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class when the
> file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&lt;=(EnumerationItem rhs)

Tests whether the EnumerationItem accessed by this Enumeration is less
than or equal to the EnumerationItem on the right hand side (rhs) of the
comparison operator, returning true if this Enumeration is less than or
equal to rhs, false otherwise.

-   Signature:

bool operator&lt;=(EnumerationItem rhs) const

-   Return:

A Boolean indicating whether the EnumerationItem accessed by this
Enumeration is less than or equal to the EnumerationItem on the right
hand side (rhs) of the comparison operator (true) or not (false).

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the comparison
operator that is to be compared to the EnumerationItem accessed by this
Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006366 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&lt;=(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&lt;=(EnumerationItem lhs, const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem on the left hand side (lhs) of the
comparison operator is less than or equal to the EnumerationItem that is
accessed by the Enumeration on the right hand side (rhs) of the
comparison operator, returning true if the EnumerationItem is less than
or equal to rhs, false otherwise.

-   Signature:

friend bool operator&lt;=(EnumerationItem lhs, const
&lt;cxxTypeName&gt;& rhs)

-   Return:

A Boolean indicating whether the EnumerationItem (lhs) is less than or
equal to the EnumerationItem that is accessed by the Enumeration on the
right hand side of the comparison operator (rhs) (true) or not (false).

-   Parameters:

lhs: The EnumerationItem on the left hand side of the comparison
operator that is to be tested.

rhs: The Enumeration on the right hand side of the comparison operator
that provides access to the EnumerationItem that is to be tested.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006374 \[An OMS C++ CAL API shall declare the friend function
> bool operator&lt;=(EnumerationItem, const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class when the
> file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&gt;(EnumerationItem rhs)

Tests whether the EnumerationItem accessed by this Enumeration is
greater than the EnumerationItem on the right hand side (rhs) of the
comparison operator, returning true if this Enumeration is greater than
rhs, false otherwise. Both this Enumeration and the specified
EnumerationItem (rhs) should be validated as part of this testing and an
exception should be thrown if either is not valid.

-   Signature:

bool operator&gt;(EnumerationItem rhs) const

-   Return:

A Boolean indicating whether the EnumerationItem accessed by this
Enumeration is greater the EnumerationItem on the right hand side (rhs)
of the comparison operator (true) or not (false).

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the comparison
operator that is to be compared to the EnumerationItem accessed by this
Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006383 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&gt;(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&gt;(EnumerationItem lhs, const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem on the left hand side (lhs) of the
comparison operator is greater than the EnumerationItem that is accessed
by the Enumeration on the right hand side (rhs) of the comparison
operator, returning true if the EnumerationItem is greater than rhs,
false otherwise.

-   Signature:

friend bool operator&gt;(EnumerationItem lhs, const &lt;cxxTypeName&gt;&
rhs)

-   Return:

A Boolean indicating whether the EnumerationItem (lhs) is greater than
the EnumerationItem that is accessed by the Enumeration on the right
hand side of the comparison operator (rhs) (true) or not (false).

-   Parameters:

lhs: The EnumerationItem on the left hand side of the comparison
operator that is to be tested.

rhs: The Enumeration on the right hand side of the comparison operator
that provides access to the EnumerationItem that is to be tested.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006391 \[An OMS C++ CAL API shall declare the friend function
> bool operator&gt;(EnumerationItem, const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class when the
> file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&gt;=(EnumerationItem rhs)

Tests whether the EnumerationItem accessed by this Enumeration is
greater than or equal to the EnumerationItem on the right hand side
(rhs) of the comparison operator, returning true if this Enumeration is
greater than or equal to rhs, false otherwise.

-   Signature:

bool operator&gt;=(EnumerationItem rhs) const

-   Return:

A Boolean indicating whether the EnumerationItem accessed by this
Enumeration is greater than or equal to the EnumerationItem on the right
hand side (rhs) of the comparison operator (true) or not (false).

-   Parameters:

rhs: The EnumerationItem on the right hand side (rhs) of the comparison
operator that is to be compared to the EnumerationItem accessed by this
Enumeration.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006400 \[An OMS C++ CAL API shall declare the public const
> member function bool operator&gt;=(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Operator: operator&gt;=(EnumerationItem lhs, const &lt;cxxTypeName&gt;&)

Tests whether the EnumerationItem on the left hand side (lhs) of the
comparison operator is greater than or equal to the EnumerationItem that
is accessed by the Enumeration on the right hand side (rhs) of the
comparison operator, returning true if the EnumerationItem is greater
than or equal to rhs, false otherwise.

-   Signature:

friend bool operator&gt;=(EnumerationItem lhs, const
&lt;cxxTypeName&gt;& rhs)

-   Return:

A Boolean indicating whether the EnumerationItem (lhs) is greater than
or equal to the EnumerationItem that is accessed by the Enumeration on
the right hand side of the comparison operator (rhs) (true) or not
(false).

-   Parameters:

lhs: The EnumerationItem on the left hand side of the comparison
operator that is to be tested.

rhs: The Enumeration on the right hand side of the comparison operator
that provides access to the EnumerationItem that is to be tested.

-   Exceptions:

None.

-   Access:

Public

> CERT CXX-006408 \[An OMS C++ CAL API shall declare the friend function
> bool operator&gt;=(EnumerationItem, const &lt;cxxTypeName&gt;&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class when the
> file "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is
> included for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Method: toName

###### Static Variant for EnumerationItem

Returns the name of the specified EnumerationItem item.

-   Signature:

static std::string toName(EnumerationItem item)

-   Return:

The name of the EnumerationItem item.

-   Parameters:

item: The EnumerationItem whose name is to be returned.

-   Exceptions:

uci::base::UCIException: Exception thrown if an invalid EnumerationItem
or one of the two special EnumerationItems, enumNotSet and
enumMaxExclusive, is not specified.

-   Access:

Public

> CERT CXX-006417 \[An OMS C++ CAL API shall declare the public static
> member function std::string toName(EnumerationItem) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

###### Static Variant for EnumerationItem

Returns the name of the EnumerationItem accessed by this Enumeration.

-   Signature:

std::string toName() const

-   Return:

The name of the EnumerationItem accessed by this Enumeration.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown if this Enumeration is
invalid.

-   Access:

Public

> CERT CXX-011059 \[An OMS C++ CAL API shall declare the public const
> member function std::string toName() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Method: fromName

Returns the EnumerationItem whose name exactly matches the specified
name.

-   Signature:

static EnumerationItem fromName(const std::string& itemName)

-   Return:

The EnumerationItem item whose name exactly matches the specified name.

-   Parameters:

name: The name of the EnumerationItem that is to be returned.

-   Exceptions:

uci::base::UCIException: Exception thrown if the specified name does not
exactly match the name of any EnumerationItem including the two special
EnumerationItems, enumNotSet and enumMaxExclusive.

-   Access:

Public

> CERT CXX-006424 \[An OMS C++ CAL API shall declare the public static
> member function EnumerationItem fromName(const std::string&) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Method: setValueFromName

Sets the EnumerationItem accessed by this Enumeration to the
EnumerationItem whose name exactly matches the specified name.

-   Signature:

void setValueFromName(const std::string& itemName)

-   Return:

None

-   Parameters:

name: The name of the EnumerationItem that is to be used to set the
EnumerationItem accessed by this Enumeration.

-   Exceptions:

uci::base::UCIException: Exception thrown if a valid EnumerationItem
having the specified name does not exist.

-   Access:

Public

> CERT CXX-011060 \[An OMS C++ CAL API shall declare the public
> non-static member function void setValueFromName(const std::string&)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]

##### Global Operator: operator&lt;&lt;

-   Signature:

template&lt;typename charT, typename traits&gt;

std::basic\_ostream&lt;charT, traits&gt;&

operator&lt;&lt;(std::basic\_ostream&lt;charT, traits&gt;& oStream,

const &lt;cxxTypeName&gt;& enumeration)

-   Return:

The output stream the Enumeration was streamed to.

-   Parameters:

oStream: The output stream the Enumeration is to be streamed to.

enumeration: The Enumeration to be streamed.

-   Exceptions:

uci::base::UCIException: Exception thrown if the Enumeration cannot be
streamed.

-   Access:

Global

> CERT CXX-006457 \[An OMS C++ CAL API shall declare the free function
> template&lt;typename charT, typename traits&gt;
> std::basic\_ostream&lt;charT, traits&gt;&
> operator&lt;&lt;(std::basic\_ostream&lt;charT, traits&gt;&, const
> &lt;cxxTypeName&gt;&) in the global namespace when the file
> "&lt;cxxTargetNamespace&gt;/type/&lt;cxxTypeName&gt;.h" is included
> for each
> \`/xs:schema/xs:simpleType\[xs:restriction/xs:enumeration\]\`.\]
>
> GUID CXX-006458 \[When streaming, the name of the EnumerationItem
> accessed by this Enumeration should be streamed.\]

The Complex Accessors
---------------------

### The LocalElement Accessor

The LocalElement Accessor is responsible for handling declarations of
local elements.

#### An Example

The following is an example of a local element declaration.

For this example, assume that the cxxNamespace was specified as
“uci::type”.

&lt;xs:complexType name="UserDataType"&gt;

&lt;xs:sequence&gt;

&lt;xs:element name=“elementName” type=“uci:ElementType”/&gt;

&lt;xs:element maxOccurs="unbounded" name="dataTypeName"
type="uci:DataType1"/&gt;

&lt;/xs:sequence&gt;

&lt;/xs:complexType&gt;

Given this example, the following declaration would be generated:

namespace uci {

namespace type {

class ElementType;

class UserDataType : public virtual uci::base::Accessor {

typedef uci::base::BoundedList&lt;uci::type::DataType1,
uci::type::accessorType::dataType1&gt; dataTypeName;

...

};

}

}

#### Realizing the LocalElement Instance

The LocalElement Instance is to be realized as follows.

> CERT CXX-007053 \[An OMS C++ CAL API shall define the public member
> type "&lt;cxxElementName&gt;" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> equivalent to the type
> "uci::base::BoundedList&lt;&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;,
> &lt;cxxRootNamespace&gt;::type::accessorType::&lt;firstLetterToLowercase(cxxElementTypeName)&gt;&gt;"
> for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/(xs:choice|xs:sequence)/xs:element\[(@maxOccurs="unbounded"
> or @maxOccurs&gt;1) and not(starts-with(@type, 'xs:') or
> @type='uci:UniversallyUniqueIdentifierType')\]\`.\]
>
> CERT CXX-012712 \[An OMS C++ CAL API shall define the public member
> type "&lt;cxxElementName&gt;" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> equivalent to the type
> "uci::base::BoundedList&lt;xs::&lt;cxxPrimitiveName&gt;,
> xs::accessorType::'Accessor Type'&gt;" for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/(xs:choice|xs:sequence)/xs:element\[@maxOccurs="unbounded"
> or @maxOccurs&gt;1\]\` where \`@type\` is an "XSD Data Type" of "The
> String Primitive Types", "The Numeric String Primitive Types", "The
> Binary Primitive Types", and "The List Primitive Types" tables.\]
>
> CERT CXX-012713 \[An OMS C++ CAL API shall define the public member
> type "&lt;cxxElementName&gt;" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> equivalent to the type
> "uci::base::BoundedList&lt;uci::base::&lt;cxxPrimitiveName&gt;Accessor,
> uci::base::accessorType::&lt;firstLetterToLowercase(cxxPrimitiveName)&gt;Accessor&gt;"
> for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/(xs:choice|xs:sequence)/xs:element\[@maxOccurs="unbounded"
> or @maxOccurs&gt;1\]\` where \`@type\` is an "XSD Data Type" of "The
> Simple Primitives" table.\]

### The Choice Accessor

This section is responsible for handling declarations of xs:elements
within a xs:choice.

#### An Example

The following is an example of a choice declaration.

For this example, assume that the qualifiedCxxName as specified as
“uci::type::UserDataType” and the baseType was specified as null.

&lt;xs:complexType name="UserDataType"&gt;

&lt;xs:choice&gt;

&lt;xs:element name=“element1” type=“uci:DataType1”/&gt;

&lt;xs:element name=“element2” type=“uci:DataType2”/&gt;

&lt;/xs:choice&gt;

&lt;/xs:complexType&gt;

Given this example, the following declaration would be generated:

namespace uci {

namespace type {

class Element1;

class Element2;

class UserDataType : public virtual uci::base::Accessor {

Public:

enum UserDataTypeChoice {

USERDATATYPE\_CHOICE\_NONE,

USERDATATYPE\_CHOICE\_ELEMENT1,

USERDATATYPE\_CHOICE\_ELEMENT2

};

virtual UserDataTypeChoice getUserDataTypeChoiceOrdinal() const {...}

virtual void setUserDataTypeChoiceOrdinal(UserDataTypeChoice
chosenElementOrdinal, uci::base::accessorType::AccessorType type =
uci::base::accessorType::null) {...}

...

...

};

}

}

#### Realizing the Choice Instance

> CERT CXX-007137 \[An OMS C++ CAL API shall define an enumerator
> "&lt;toUpperCase(cxxTypeName)&gt;\_CHOICE\_NONE" in the enum member
> type "&lt;cxxTypeName&gt;Choice" of the
> "&lt;cxxRootNamespace&gt;::type::&lt;cxxTypeName&gt;" class with a
> value of 0 for each
> \`/xs:schema/xs:complexType\[(.|xs:complexContent/xs:extension)/xs:choice/xs:element\]\`.\]
>
> CERT CXX-007138 \[An OMS C++ CAL API shall define an enumerator
> "&lt;toUpperCase(cxxTypeName)&gt;\_CHOICE\_&lt;enumItem&gt;" in the
> enum member type "&lt;cxxTypeName&gt;Choice" of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class with a
> value greater than "&lt;toUpperCase(cxxTypeName)&gt;\_CHOICE\_NONE"
> where &lt;enumItem&gt; is the \`self::xs:element/@name\` translated
> using the “Generating C++ Data Type and Enumeration Item Names”
> section "Enumerated Item Name Translation Rules" for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/xs:choice/xs:element\`.\]

For example, if the cxxName attribute is specified as “UserDataType” and
the data type is declared as above, then the following C++ enumeration
can be generated:

enum UserDataTypeChoice {

USERDATATYPE\_CHOICE\_NONE,

USERDATATYPE\_CHOICE\_ELEMENT1,

USERDATATYPE\_CHOICE\_ELEMENT2

};

##### Method: get&lt;cxxTypeName&gt;ChoiceOrdinal

Returns this choice’s “selection ordinal.” A choice’s “selection
ordinal” is used to specify which item in the choice is selected to be
active.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;Choice
get&lt;cxxTypeName&gt;ChoiceOrdinal() const

-   Return:

The value of this Choice’s selection ordinal.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
this Choice’s selection ordinal.

-   Access:

Public

> CERT CXX-011109 \[An OMS C++ CAL API shall declare the public const
> member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxTypeName&gt;Choice
> get&lt;cxxTypeName&gt;ChoiceOrdinal() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType\[(.|xs:complexContent/xs:extension)/xs:choice/xs:element\]\`.\]

##### Method: is&lt;cxxElementName&gt; const

Returns whether this choice's "selection ordinal" is set to the choice
in the method name.

-   Signature:

bool is&lt;cxxElementName&gt;() const

-   Return:

True, if this Choice's selection ordinal is set to "cxxElementName",
false otherwise.

-   Parameters:

None

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs returning
this Choice's selection ordinal

-   Access:

Public

For example, if the data type is declared as above, then the following
C++ accessors can be generated:

bool isElement1() const;

bool isElement2() const;

> CERT CXX-012695 \[An OMS C++ CAL API shall declare the public const
> member function bool is&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/xs:choice/xs:element\`.\]

##### Method: set&lt;cxxName&gt;ChoiceOrdinal

Sets this choice’s “selection ordinal.” A choice’s “selection ordinal”
is used to specify which element in the choice is selected to be active.
There are two mechanisms that can be used to set a choice’s “selection
ordinal.” The first mechanism is by invoking this method. The second
mechanism is by invoking one of the set methods associated with one of
the elements contained in this choice. Once this method is invoked, the
value returned by get&lt;cxxTypeName&gt;ChoiceOrdinal() will be the
ordinal specified when this method was invoked. In addition, the access
methods associated with the selected element will be enabled and will
provide access to the chosen element. This method returns a reference to
this ChoiceType.

If the select element has never been selected, the underlying
implementation will create an element of the proper type. The type of
element to be created is specified by this method’s second argument,
i.e., the type argument. By default (when no argument is specified), the
underlying implementation will create an element that corresponds to the
type declared for that element in the OMS Schema Definition. This is
known as the base type. This default operation can be overridden by
specifying a type argument that is a data type that is derived from the
base type. This capability provides the mechanism required to support
inheritance. The second argument is ignored if the element is a simple
primitive data type (Section 9.1.1, The Simple Primitive Data Types).

-   Signature:

&lt;qualifiedCxxName&gt;& set&lt;cxxTypeName&gt;ChoiceOrdinal(

&lt;cxxTypeName&gt;Choice ordinal,

uci::base::accessorType::AccessorType type =

uci::base::accessorType::null)

-   Return:

A reference to this ChoiceType

-   Parameters:

ordinal: The ordinal to set this Accessor’s selection ordinal to.

type: The data type to create if selected element has never been
selected before.

-   Exceptions:

uci::base::UCIException: Exception thrown when an error occurs setting
this Choice’s selection ordinal.

-   Access:

Public

> CERT CXX-011110 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;&
> set&lt;cxxTypeName&gt;ChoiceOrdinal(&lt;cxxTypeName&gt;Choice,
> uci::base::accessorType::AccessorType = uci::base::accessorType::null)
> of the "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class
> for each
> \`/xs:schema/xs:complexType\[(.|xs:complexContent/xs:extension)/xs:choice/xs:element\]\`.\]

##### Complex Type Method: choose&lt;cxxElementName&gt;

Sets this choice's "selection ordinal" to the choice in the method name,
and returns a reference to the (possibly new) underlying element.

Do not generate this method for simple primitive types as described in
table 9.1-1.

-   Signature:

&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
choose&lt;cxxElementName&gt;(uci::base::accessorType::AccessorType type
= uci::base::accessorType::null)

-   Return:

A reference to the Choice that provides access to the Choice that is
named by elementName.

-   Parameters:

type: The accessor type (see Section 10.3, The Accessor Type Constants)
that is associated with the Accessor class that should be instantiated
when this Sequence is enabled. The use of this parameter provides the
support for inheritance.

-   Exceptions:

uci::base::UCIException thrown if a failure occurs setting the Choice's
selection ordinal or returning the Choice

For example, if the data type is declared as above, then the following
C++ methods can be generated:

Element1 & chooseElement1();

Element2 & chooseElement2();

> CERT CXX-012696 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;&
> choose&lt;cxxElementName&gt;(uci::base::accessorType::AccessorType =
> uci::base::accessorType::null) of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/xs:choice/xs:element\[not(@maxOccurs='unbounded'
> or @maxOccurs&gt;1)\]\` where \`@type\` is an xs:complexType.\]

##### SimpleList Method: choose&lt;cxxElementName&gt;

Sets this choice's "selection ordinal" to the choice in the method name,
and returns a reference to the (possibly new) underlying element.

Do not generate this method for simple primitive types as described in
table 9.1-1.

-   Signature:

xs::&lt;cxxPrimitiveName&gt;& choose&lt;cxxElementName&gt;()

-   Return:

A reference to the Choice that provides access to the Choice that is
named by elementName.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException thrown if a failure occurs setting the Choice's
selection ordinal or returning the Choice

> CERT CXX-012714 \[An OMS C++ CAL API shall declare the public
> non-static member function xs::&lt;cxxPrimitiveName&gt;&
> choose&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/xs:choice/xs:element\[not(@maxOccurs='unbounded'
> or @maxOccurs&gt;1 or @type='uci:UniversallyUniqueIdentifierType')\]\`
> where \`@type\` is or derives from an "XSD Data Type" of "The Binary
> Primitive Types" or "The List Primitive Types" tables.\]

##### Bounded List Method: choose&lt;cxxElementName&gt;

Sets this choice's "selection ordinal" to the choice in the method name,
and returns a reference to the (possibly new) underlying element.

Do not generate this method for simple primitive types as described in
table 9.1-1.

-   Signature:

&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
choose&lt;cxxElementName&gt;()

-   Return:

A reference to the Choice that provides access to the Choice that is
named by elementName.

-   Parameters:

None.

-   Exceptions:

uci::base::UCIException thrown if a failure occurs setting the Choice's
selection ordinal or returning the Choice

> CERT CXX-012715 \[An OMS C++ CAL API shall declare the public
> non-static member function
> &lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;::&lt;cxxElementName&gt;&
> choose&lt;cxxElementName&gt;() of the
> "&lt;cxxTargetNamespace&gt;::type::&lt;cxxTypeName&gt;" class for each
> \`/xs:schema/xs:complexType/(.|xs:complexContent/xs:extension)/xs:choice/xs:element\[@maxOccurs='unbounded'
> or @maxOccurs&gt;1\]\`.\]

### The GlobalElement Accessor

The Global Element Accessors are used to process global element
declarations. In an OMS Schema Definition, a global element declaration
is used to declare an OMS Message.

#### An Example

The following is an example of a GlobalElement declaration.

For this example, assume that the declaration was declared in the “<span
class="underline">https://www.vdl.afrl.af.mil/programs/oam</span>”
namespace, i.e., the UCI namespace.

&lt;xs:element name=“UserData” type=“UserDataType”/&gt;

Given this example, the following declaration would be generated:

namespace uci {

namespace type {

typedef uci::type::UserDataType UserData;

}

}

#### Realizing the GlobalElement Instance

> CERT CXX-007316 \[An OMS C++ CAL API shall define the type
> "&lt;cxxTypeName&gt;" in the "&lt;cxxTargetNamespace&gt;::type"
> namespace equivalent to the type
> "&lt;cxxRootNamespace&gt;::type::&lt;cxxElementTypeName&gt;" for each
> \`/xs:schema/xs:element\`.\]

C++ CAL CERT Verification
=========================

Verification is normally performed by inspection, analysis,
demonstration and/or test. These CERTs are typically verified either by
inspection of specific documents, analysis of test results, or
demonstration of specific OMS Services or programs that prove that
something has been implemented properly.

One of the goals of proving OMS compliance is to leverage existing test
plan artifacts and not to generate duplicate testing.

List of Symbols, Abbreviations, and Acronyms
============================================

For the list of acronyms, refer to the document OMSC-STD-002:
Abbreviations and Glossary.

Glossary
========

For the glossary of terms, refer to the document OMSC-STD-002:
Abbreviations and Glossary.
