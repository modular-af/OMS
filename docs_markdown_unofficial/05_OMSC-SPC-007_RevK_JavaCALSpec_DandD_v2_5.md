Open Mission Systems (OMS)

Definition And Documentation (D&D)

Java Critical Abstraction Layer (CAL) Interface Generation Specification

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary, open architecture
standard for integrating subsystems and services into mission packages.

This is the top-level OMS Schema to Java interface specification.

Java CAL Implementation requirements will adhere to the general CAL
requirements listed in the CAL specification unless otherwise stated.
Items listed here will either refine or clarify requirements as they
apply to the Java CAL Implementation.

A Java CAL is provided as part of the Open Computing Environment (OCE).
The OCE will be capable of running a Long Term Support version of Java,
currently recommended as Java Standard Edition 11; therefore, Java CALs
should consider an implementation that is capable of running on a Java
11 Java Virtual Machine.

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

[2 Scope 2](#scope)

[3 References 3](#references)

[3.1 OMS D&D Documents 3](#oms-dd-documents)

[3.2 Other Documents 3](#other-documents)

[4 Schema to Java Compiler 4](#schema-to-java-compiler)

[4.1 XML Schema to Java CAL API Binding
4](#xml-schema-to-java-cal-api-binding)

[5 Common Behaviors of the Generated Java CAL API Bindings
10](#common-behaviors-of-the-generated-java-cal-api-bindings)

[5.1 Setting & Getting Message Field Values
10](#setting-getting-message-field-values)

[5.2 Required Fields 10](#required-fields)

[5.3 Optional Fields 11](#optional-fields)

[5.4 List Fields 11](#list-fields)

[5.5 Choices 11](#choices)

[5.6 Constructors 11](#constructors)

[5.7 Customization 11](#customization)

[6 Common Classes and Interfaces 12](#common-classes-and-interfaces)

[6.1 Abstract Service Bus 15](#abstract-service-bus)

[6.2 Abstract Service Bus Factory 17](#abstract-service-bus-factory)

[6.3 Abstract Service Bus Factory Loader
18](#abstract-service-bus-factory-loader)

[6.4 UCIType Interface 19](#ucitype-interface)

[6.5 Bounded List 19](#bounded-list)

[6.6 Message Listener 20](#message-listener)

[6.7 Message Reader 21](#message-reader)

[6.8 Message Writer 23](#message-writer)

[6.9 UCI Exception 24](#uci-exception)

[6.10 UUID Factory 25](#uuid-factory)

[6.11 UUID Factory Loader 27](#uuid-factory-loader)

[6.12 Version Info 28](#version-info)

[6.13 Externalizer 29](#externalizer)

[6.14 Externalizer Loader 30](#externalizer-loader)

[6.15 AbstractServiceBusConnection Status
32](#abstractservicebusconnection-status)

[6.15.1 AbstractServiceBusConnectionStatusListener class
32](#abstractservicebusconnectionstatuslistener-class)

[6.15.2 AbstractServiceBusConnectionStateEnum enumeration
32](#abstractservicebusconnectionstateenum-enumeration)

[6.15.3 AbstractServiceBusConnectionStatusData class
33](#abstractservicebusconnectionstatusdata-class)

[7 Java CAL CERT Verification 34](#java-cal-cert-verification)

[8 Acronyms and Symbols 35](#acronyms-and-symbols)

[9 Glossary 36](#glossary)

This page is intentionally left blank.

List of Figures

[Figure 6.0-1 UML Overview of Common CAL Classes and Interfaces (part 1)
13](#_Toc219292530)

[Figure 6.0-2 UML Overview of Common CAL Classes and Interfaces (part 2)
14](#_Toc219292531)

[Figure 6.1-1 UML for AbstractServiceBusConnection Interface
15](#_Toc219292532)

[Figure 6.2-1 UML for AbstractServiceBusConnectionFactory Interface
17](#_Toc219292533)

[Figure 6.3-1 UML for AbstractServiceBusConnectionFactoryLoader Class
18](#_Toc219292534)

[Figure 6.5-1 UML for BoundedList Interface 19](#_Toc219292535)

[Figure 6.6-1 UML for Message Listener Interface 20](#_Toc219292536)

[Figure 6.7-1 UML for Message Reader Interface 21](#_Toc219292537)

[Figure 6.8-1 UML for Message Writer Interface 23](#_Toc219292538)

[Figure 6.9-1 UML for UCIException Class 24](#_Toc219292539)

[Figure 6.10-1 UML for UUIDFactory Interface 25](#_Toc219292540)

[Figure 6.11-1 UML for UUIDFactoryLoader Class 27](#_Toc219292541)

[Figure 6.12-1 UML for Version Info Class 28](#_Toc219292542)

[Figure 6.13-1 UML for Externalizer Interface 29](#_Toc219292543)

[Figure 6.14-1 UML for ExternalizerLoader Class 30](#_Toc219292544)

This page is intentionally left blank.

List of Tables

[Table 3.1-1 OMS D&D Documents 3](#_Toc219292545)

[Table 3.2-1 Other Documents 3](#_Toc219292546)

[Table 4.1-1 Supplementary Method Definitions 5](#_Toc219292547)

[Table 4.1-2 Datatype Mappings 6](#_Toc219292548)

[Table 4.1-3 Namespace to Package Mappings 6](#_Toc219292549)

[Table 4.1-4 ChoiceType Class Definition 8](#_Toc219292550)

[Table 6.1-1 AbstractServiceBusConnection Interface Definition
15](#_Toc219292551)

[Table 6.2-1 AbstractServiceBusConnectionFactory Interface Definition
17](#_Toc219292552)

[Table 6.3-1 AbstractServiceBusConnectionFactoryLoader Final Class
Definition 18](#_Toc219292553)

[Table 6.5-1 BoundedList Interface Definition 20](#_Toc219292554)

[Table 6.5-2 BoundedList Fields 20](#_Toc219292555)

[Table 6.6-1 Message Listener Interface Definition 20](#_Toc219292556)

[Table 6.7-1 Message Reader Interface Definition 22](#_Toc219292557)

[Table 6.8-1 MessageWriter Interface Definition 23](#_Toc219292558)

[Table 6.9-1 UCIException Class Definition 25](#_Toc219292559)

[Table 6.10-1 UUIDFactory Interface Definition 26](#_Toc219292560)

[Table 6.11-1 UUIDFactoryLoader Final Class Definition
27](#_Toc219292561)

[Table 6.12-1 Version Info Class Definition 28](#_Toc219292562)

[Table 6.13-1 Externalizer Interface Definition 30](#_Toc219292563)

[Table 6.14-1 ExternalizerLoader Final Class Definition
31](#_Toc219292564)

[Table 6.15-1 AbstractServiceBusConnectionStatusListener Interface
Definition 32](#_Toc219292565)

[Table 6.15-2 AbstractServiceBusConnectionStateEnum Enum Definition
32](#_Toc219292566)

[Table 6.15-3 AbstractServiceBusConnectionStatusData Class Definition
33](#_Toc219292567)

This page is intentionally left blank.

Introduction
============

This is the top-level OMS Schema to Java interface specification. The
Java CAL provides an interface between the Abstract Service Bus and OMS
Services, Subsystems, and Isolators. These interfaces use open and
standardized non-proprietary interface definitions, but decouple the
technical implementations from the interfaces. This OMS Standard enables
future technology upgrades; providing flexibility that allows Platform,
Subsystem and Service providers to offer innovative and competitive
solutions to future problems.

This specification prefixes all schema types defined in the <span
class="underline">http://www.w3.org/2001/XMLSchema</span> namespace with
“xs:”.

Scope
=====

In the following sections, the XML Schema Definition (XSD) to Java
interface requirements (CERTs) necessary for OMS compliance are
described and enumerated.

References
==========

OMS D&D Documents 
-----------------

Table 3.1-1, OMS D&D Documents, lists the documents that assist in the
understanding and implementation of OMS.

<span id="_Toc219292545" class="anchor"></span>Table 3.1-1 OMS D&D
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
<tr class="odd">
<td>OMSC-SPC-001</td>
<td>Critical Abstraction Layer (CAL) Specification</td>
<td>L</td>
<td>22 January 2026</td>
</tr>
</tbody>
</table>

Other Documents
---------------

The documents listed in Table 3.2-1, Other Documents, are cited
throughout this document. For dated references, only the edition cited
applies. For undated references, the latest edition of the referenced
document (including any amendments or corrigenda) applies.

<span id="_Toc219292546" class="anchor"></span>Table 3.2-1 Other
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
<td>JSR-000222</td>
<td>Java® Architecture for XML Binding (JAXB) 2.3 (Maintenance Release 3)</td>
<td>2.3</td>
<td>19 September 2017</td>
</tr>
<tr class="even">
<td>JSR-337</td>
<td>The Java® Language Specification</td>
<td>8</td>
<td>15 February 2015</td>
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

Schema to Java Compiler
=======================

A Schema to Java Compiler (SJC) translates a Universal Command and
Control (C2) Interface (UCI) XSD to the Java code that makes up the Java
CAL Interface. The necessary publish and subscribe interfaces for
sending and receiving the OMS Messages using Java are described. These
interfaces are implemented by compliant Java CAL Implementations.

XML Schema to Java CAL API Binding
----------------------------------

With the exception of schema choices and some added rules below, the XML
Schema is converted to the Java CAL API following the rules set forth in
the JSR-000222 Java Architecture for XML Binding (JAXB) specification.
SJCs are not required to implement all of the JSR-000222 specification.
SJCs are only required to implement the portions called out in this
specification using the customizations and addendums given in this
specification. There are no requirements to support JAXB annotations or
any customizations except those called out in this specification.
Additional methods and/or fields may be added to non-interface classes.
Interface classes may not contain additional methods or fields other
than as is prescribed in this document.

When interpreting the tables in this document, “Modifier and Type” only
restricts the access modifier, whether it is static or non-static, and
the abstractness or finality of the class, method, or field. The “Method
and Description” column of a method contains a description of the method
name, parameter types, and exceptions thrown. Checked exceptions other
than what are prescribed may not be thrown from these methods. Remarks
provided describe the intended implementation behavior of the method.

> CERT JAVA-000128 \[A Java CAL API shall provide Java classes, enum
> constants, and methods, as specified in the “Binding XML Schema to
> Java Representation” section of the JAXB specification, as though only
> the default customizations are defined with the below addendums.\]
>
> CERT JAVA-001460 \[A Java CAL API shall provide Java constructs as
> though the JAXB underscoreBinding global binding parameter is defined
> as asCharInWord.\]
>
> CERT JAVA-001461 \[A Java CAL API shall provide enum constants
> prepended with an underscore when the first character of the
> xs:enumeration facet value supplied to
> “java.lang.Character.isJavaIdentifierStart” is false.\]
>
> CERT JAVA-001462 \[A Java CAL API shall provide the
> &lt;javaClassName&gt;
> set&lt;property&gt;(&lt;javaElementClassName&gt;) method for each
> Optional or Required field.\]
>
> CERT JAVA-001463 \[A Java CAL API shall provide the methods in the
> “Supplementary Method Definitions” table for each normal class
> declaration generated from the schema.\]

<span id="_Toc219292547" class="anchor"></span>Table 4.1-1 Supplementary
Method Definitions

<table>
<thead>
<tr class="header">
<th>Applicability</th>
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>The field is Optional</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>if&lt;property&gt;Present(java.util.function.Consumer&lt;? super &lt;javaElementClassName&gt;&gt;)</p>
<p>The if&lt;property&gt;Present method calls the supplied Consumer given the has&lt;property&gt; method returns true. No exceptions should be raised when calling this method given the has&lt;property&gt; method returns false.</p></td>
</tr>
<tr class="even">
<td>The field is Required</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>with&lt;property&gt;(java.util.function.Consumer&lt;? super &lt;javaElementClassName&gt;&gt;)</p>
<p>The with&lt;property&gt; method calls the supplied Consumer with the underlying value.</p></td>
</tr>
<tr class="odd">
<td>The field is a List</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>forEach&lt;property&gt;( java.util.function.Consumer&lt;? super &lt;javaElementClassName&gt;&gt;)</p>
<p>The forEach&lt;property&gt; method calls the supplied Consumer with each underlying value.</p></td>
</tr>
<tr class="even">
<td>The field is a List</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>add&lt;property&gt;(&lt;javaElementClassName&gt;…)</p>
<p>The add&lt;property&gt; method appends each &lt;javaElementClassName&gt; instance to the backing BoundedList. The parameter type of this method is unboxed when &lt;javaElementClassName&gt; is primitive.</p></td>
</tr>
<tr class="odd">
<td>The field is a List</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>add&lt;property&gt;(java.lang.Iterable&lt;? extends &lt;javaElementClassName&gt;&gt;)</p>
<p>The add&lt;property&gt; method appends each &lt;javaElementClassName&gt; instance to the backing BoundedList.</p></td>
</tr>
</tbody>
</table>

<span id="_Toc219292548" class="anchor"></span>Table 4.1-2 Datatype
Mappings

<table>
<thead>
<tr class="header">
<th>XML Schema Datatype</th>
<th>Java Datatype</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>xs:time</td>
<td>java.time.LocalTime</td>
</tr>
<tr class="even">
<td>xs:dateTime</td>
<td>java.time.Instant</td>
</tr>
<tr class="odd">
<td>xs:duration</td>
<td>java.time.Duration</td>
</tr>
<tr class="even">
<td>uci:UniversallyUniqueIdentifierType</td>
<td>java.util.UUID</td>
</tr>
<tr class="odd">
<td>xs:string</td>
<td>java.lang.String</td>
</tr>
<tr class="even">
<td>xs:integer</td>
<td>java.math.BigInteger</td>
</tr>
<tr class="odd">
<td>xs:int</td>
<td>int</td>
</tr>
<tr class="even">
<td>xs:long</td>
<td>long</td>
</tr>
<tr class="odd">
<td>xs:short</td>
<td>short</td>
</tr>
<tr class="even">
<td>xs:decimal</td>
<td>java.math.BigDecimal</td>
</tr>
<tr class="odd">
<td>xs:float</td>
<td>float</td>
</tr>
<tr class="even">
<td>xs:double</td>
<td>double</td>
</tr>
<tr class="odd">
<td>xs:boolean</td>
<td>boolean</td>
</tr>
<tr class="even">
<td>xs:byte</td>
<td>byte</td>
</tr>
<tr class="odd">
<td>xs:base64Binary</td>
<td>byte[]</td>
</tr>
<tr class="even">
<td>xs:hexBinary</td>
<td>byte[]</td>
</tr>
<tr class="odd">
<td>xs:unsignedInt</td>
<td>long</td>
</tr>
<tr class="even">
<td>xs:unsignedShort</td>
<td>int</td>
</tr>
<tr class="odd">
<td>xs:unsignedByte</td>
<td>short</td>
</tr>
</tbody>
</table>

> CERT JAVA-000151 \[A Java CAL API shall provide Java types using the
> datatype mappings specified in the “Datatype Mappings” table.\]

<span id="_Toc219292549" class="anchor"></span>Table 4.1-3 Namespace to
Package Mappings

<table>
<thead>
<tr class="header">
<th>XML Namespace</th>
<th>Java Package</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><span class="underline">https://www.vdl.afrl.af.mil/programs/oam</span></td>
<td>uci.types</td>
</tr>
</tbody>
</table>

> CERT JAVA-000206 \[A Java CAL API shall provide Java constructs using
> the package mappings specified in the “Namespace to Package Mappings”
> table.\]

Appendix D.5 of the JAXB specification is to be replaced with the XML
Namespace to Java Package mappings specified in the “Namespace to
Package Mappings” Table 4.1-3. Extension schemas must have any new XML
Namespaces mapped to a Java package. If the extensions are approved by
the OMS board, extension mappings for the new XML Namespace will become
part of the OMS standard.

> CERT JAVA-000208 \[A Java CAL shall provide a 1-to-1 mapping mechanism
> for XML Namespaces that are not already mapped in the XML Namespace to
> Java Package mapping table for Java packages during the schema to Java
> translation.\]

The following additions are to be applied to the Java CAL API
generation. A normal class declaration is defined in Section 8.1 of the
Java Language Specification.

> CERT JAVA-000212 \[A Java CAL API shall provide a public boolean
> has&lt;property&gt;() method for each Optional Field where
> &lt;property&gt; is derived according to appendix D.2 of the JAXB
> specification.\]
>
> CERT JAVA-000213 \[A Java CAL API shall provide an overridden public
> &lt;javaClassName&gt; clone() method for each normal class declaration
> generated from the schema to perform a deep copy of the object.\]
>
> CERT JAVA-000214 \[A Java CAL API shall implement the
> java.lang.Cloneable interface for each normal class declaration
> generated from the schema.\]
>
> CERT JAVA-000216 \[A Java CAL API shall provide ChoiceType classes
> that define the methods in the “ChoiceType Class Definition” table.\]

<span id="_Toc219292550" class="anchor"></span>Table 4.1-4 ChoiceType
Class Definition

<table>
<thead>
<tr class="header">
<th>Applicability</th>
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>All choice elements</td>
<td>public final &lt;javaElementClassName&gt;</td>
<td><p>as&lt;property&gt; ()</p>
<p>The as&lt;property&gt; method returns the choice value set with choose&lt;property&gt;. The return type of this method is unboxed when &lt;javaElementClassName&gt; is primitive. It is a semantic error to invoke this method when is&lt;property&gt; returns false, so a runtime exception is thrown.</p></td>
</tr>
<tr class="even">
<td>All choice elements</td>
<td>public final boolean</td>
<td><p>is&lt;property&gt;()</p>
<p>The is&lt;property&gt; method returns true when choiceType() equals ChoiceTypeEnum.&lt;property&gt;.</p></td>
</tr>
<tr class="odd">
<td>All choice elements</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>if&lt; property&gt;(java.util.function.Consumer&lt;? super &lt;javaElementClassName&gt;&gt;)</p>
<p>The if&lt;property&gt; method evaluates a consumer with the choice value when is&lt;property&gt; returns true.</p>
<p>Returns this choice type instance.</p></td>
</tr>
<tr class="even">
<td>Non-List choice elements</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>choose&lt;property&gt;(&lt;javaElementClassName&gt;)</p>
<p>The choose&lt;property&gt; method sets the choice value of this instance. The parameter type of this method is boxed when &lt;javaElementClassName&gt; is primitive. Invoking this method with a value of null clears the instance to its uninitialized state.</p>
<p>Returns this choice type.</p></td>
</tr>
<tr class="odd">
<td>List choice elements</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>choose&lt;property&gt;(&lt;javaElementClassName&gt;…)</p>
<p>The choose&lt;property&gt; method sets the choice values of this instance. The parameter type of this method is unboxed when &lt;javaElementClassName&gt; is primitive. Invoking this method with a value of null clears the instance to its uninitialized state.</p>
<p>Returns this choice type.</p></td>
</tr>
<tr class="even">
<td>List choice elements</td>
<td>public final &lt;javaClassName&gt;</td>
<td><p>choose&lt;property&gt;(java.lang.Iterable&lt;? extends &lt;javaElementClassName&gt;&gt;)</p>
<p>The choose&lt;property&gt; method sets the choice values of this instance. Invoking this method with a value of null clears the instance to its uninitialized state.</p>
<p>Returns this choice type.</p></td>
</tr>
<tr class="odd">
<td>All choice elements</td>
<td>public final &lt;javaClassName&gt;.ChoiceTypeEnum</td>
<td><p>choiceType()</p>
<p>The choiceType method returns the enumeration value corresponding to the current choice value of this instance set with choose&lt;property&gt;. When this instance contains no choice value this method returns null.</p>
<p>Returns the current choice type enumeration value.</p></td>
</tr>
</tbody>
</table>

> CERT JAVA-000221 \[A Java CAL API shall generate the public inner enum
> “ChoiceTypeEnum” for each ChoiceType with the Constant Names derived
> according to appendix D.2 of the JAXB specification.\]
>
> CERT JAVA-000240 \[A Java CAL API shall use the uci.BoundedList type
> in place of the java.util.List used by JAXB.\]
>
> CERT JAVA-001370 \[A Java CAL API shall generate a public static final
> String UCI\_TYPE\_VERSION field for each normal class declaration
> generated from the schema to identify the version of the UCI type used
> to generate the class.\]

Common Behaviors of the Generated Java CAL API Bindings
=======================================================

The generated Java CAL API bindings must adhere to the common behaviors
described in this section.

Setting & Getting Message Field Values
--------------------------------------

The Java CAL Implementation relies on references and does not perform
deep copies when setting message values.

In Java CAL Implementations, class implementations are used to represent
all XSD complex types defined in the schema. XSD simple types are
created via the appropriate Java language mechanism.

In Java CAL Implementations, objects are used to represent all types,
both primitive and complex. OMS Message Objects are created on the heap.
Sub-message objects are not initially constructed. Java CAL Clients will
use the “new” operator or an implicit “new” operation (e.g., Integer
myInt = 1;) to create sub-message objects before setting them within the
larger message object.

To avoid requiring services to catch exceptions while creating OMS
Message objects, OMS Message objects and sub-objects should avoid
throwing checked exceptions in constructors and member accessor methods.

All method definitions in Table 4.1-1, Supplementary Method Definitions,
and Table 4.1-4, ChoiceType Class Definition, on concrete OMS Message
Objects need to be marked as final. Since each class that extends
another OMS Message Object overrides the setter to return the correct
type, setters should only be marked as final on classes with no OMS
Message Object extensions.

Required Fields
---------------

A Required field is any xs:element whose minOccurs and maxOccurs
attributes are equivalent to 1.

When setting a required field, Java Clients provide an object
representing the value to be used to set the field. The Java CAL
Implementation will use a reference to the provided object until the OMS
Message has been sent.

Optional Fields
---------------

An Optional field is any xs:element whose minOccurs attribute is 0 and
maxOccurs attribute is equivalent to 1.

If the value for an optional field is null, the field is considered to
be disabled. If the value is non-null, the field is considered to be
enabled. The Java CAL interface will return null to Java Clients
attempting to access disabled optional fields.

When setting an optional field, Java Clients provide an object
representing the value to be used to set the field. The Java CAL
Implementation will use a reference to the provided object until the OMS
Message has been sent.

Java CAL Clients may clear an optional field by setting the value to
null. Setting the optional field to null will transition the field to a
disabled state.

List Fields
-----------

A List field is any xs:element whose maxOccurs attribute is greater than
1.

Choices
-------

A choice is a data construct that may have any of several data
representations. In the OMS Message Schema, choices are defined using
the “xs:choice” tag. A choice field is considered to be uninitialized
when no type has been selected for the current data representation.

Java CAL Clients determine the choice value represented by a ChoiceType
either the choiceType() method or the applicable is&lt;property&gt;()
method. If choiceType() returns null then the ChoiceType contains no
value. The as&lt;property&gt;() method may throw a runtime exception if
invoked when either is&lt;property&gt; returns false or choiceType()
does not equal the corresponding ChoiceTypeEnum.&lt;property&gt;.

Constructors
------------

A public, default, no-argument constructor needs to be provided on each
OMS Message Object.

Customization
-------------

Provided that all behaviors in this section are preserved, CAL
implementations are allowed to do the following:

-   Add public, private, protected, and package protected methods,
    fields and classes to any OMS Message Object

-   Add implementation required imports to OMS Message Object

-   Overload or override API prescribed non-static methods

Common Classes and Interfaces
=============================

In addition to the classes generated from the schema, the Java CAL
provides a common set of classes and interfaces, shown in Figure 6.0-1,
Unified Modeling Language (UML) Overview of Common CAL Classes and
Interfaces used to construct the CAL and to read and write data to the
Abstract Service Bus (ASB).

<img src="media/image2.png" style="width:9in;height:5.28125in" />

<span id="_Toc219292530" class="anchor"></span>Figure 6.0-1 UML Overview
of Common CAL Classes and Interfaces (part 1)

<img src="media/image3.png" style="width:9in;height:3.47917in" />

<span id="_Toc219292531" class="anchor"></span>Figure 6.0-2 UML Overview
of Common CAL Classes and Interfaces (part 2)

Abstract Service Bus
--------------------

An instance of the AbstractServiceBusConnection is a CAL instance. It
provides the fundamental support for sending and receiving messages.

<img src="media/image4.png" style="width:6.5in;height:2.82292in" />

<span id="_Toc219292532" class="anchor"></span>Figure 6.1-1 UML for
AbstractServiceBusConnection Interface

> CERT JAVA-000267 \[The Java CAL shall provide the public
> uci.AbstractServiceBusConnection interface that extends
> uci.UUIDFactory with methods defined in the
> “AbstractServiceBusConnection Interface Definition” table.\]

<span id="_Toc219292551" class="anchor"></span>Table 6.1-1
AbstractServiceBusConnection Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>public</p>
<p>&lt;T extends MessageType&gt;</p>
<p>MessageReader&lt;T&gt;</p></td>
<td><p>createReader(java.lang.String target, java.lang.Class&lt;T&gt; type) throws UCIException</p>
<p>Constructs a new MessageReader that can be used to read messages of type T.</p></td>
</tr>
<tr class="even">
<td><p>public</p>
<p>&lt;T extends MessageType&gt;</p>
<p>MessageWriter&lt;T&gt;</p></td>
<td><p>createWriter(java.lang.String target, java.lang.Class&lt;T&gt; type) throws UCIException</p>
<p>Constructs a new MessageWriter that can be used to write messages of type T.</p></td>
</tr>
<tr class="odd">
<td>public java.util.UUID</td>
<td><p>getMyCapabilityUUID(java.lang.String name) throws UCIException</p>
<p>Returns the UUID of the given capability name.</p></td>
</tr>
<tr class="even">
<td>public java.util.UUID</td>
<td><p>getMyComponentUUID(java.lang.String name)</p>
<p>throws UCIException</p>
<p>Returns the UUID of the given component name.</p></td>
</tr>
<tr class="odd">
<td>public java.util.UUID</td>
<td><p>getMyServiceUUID()</p>
<p>Returns the UUID of the service that created the AbstractServiceBusConnection instance.</p></td>
</tr>
<tr class="even">
<td>public java.util.UUID</td>
<td><p>getMySubSystemUUID()</p>
<p>Returns the UUID of the subsystem that create the AbstractServiceBusConnection instance.</p></td>
</tr>
<tr class="odd">
<td>public java.lang.String</td>
<td><p>getMySystemLabel()</p>
<p>Returns the system label.</p></td>
</tr>
<tr class="even">
<td>public java.util.UUID</td>
<td><p>getMySystemUUID()</p>
<p>Returns this system’s UUID.</p></td>
</tr>
<tr class="odd">
<td>public java.lang.String</td>
<td><p>getName()</p>
<p>Returns the name of this AbstractServiceBusConnection instance.</p></td>
</tr>
<tr class="even">
<td>public VersionInfo</td>
<td><p>getVersion()</p>
<p>Returns the version info related to this CAL/ASB implementation</p></td>
</tr>
<tr class="odd">
<td>public void</td>
<td><p>shutdown() throws UCIException</p>
<p>The shutdown method is used to shutdown this ASB. Once shutdown, this ASB can no longer be used. In addition, any factory associated with this ASB will no longer be usable.</p></td>
</tr>
<tr class="even">
<td>public void</td>
<td><p>addStatusListener(AbstractServiceBusConnectionStatusListener listener) throws UCIException</p>
<p>Add listener for ASB service state changes</p></td>
</tr>
<tr class="odd">
<td>public void</td>
<td><p>removeStatusListener(AbstractServiceBusConnectionStatusListener listener) throws UCIException</p>
<p>Remove listener for ASB service status changes</p></td>
</tr>
<tr class="even">
<td>public AbstractServiceBusConnectionStatusData</td>
<td><p>getStatus() throws UCIException</p>
<p>Get current ASB status</p></td>
</tr>
<tr class="odd">
<td>public Externalizer</td>
<td><p>getExternalizer(String externalizerType) throws UCIException</p>
<p>Helper function that calls getExternalizer with ASB’s Schema version and CAL API version</p></td>
</tr>
</tbody>
</table>

Abstract Service Bus Factory
----------------------------

The AbstractServiceBusConnectionFactory in Figure 6.2-1, UML for
AbstractServiceBusConnectionFactory Interface, provides the ability to
create AbstractServiceBusConnection instances for the CAL Implementation
to which the factory belongs. It is used to obtain an Abstract Service
Bus connection. Using the same serviceInitId will always return the same
CAL instance.

<img src="media/image5.png" style="width:6.5in;height:1.33333in" />

<span id="_Toc219292533" class="anchor"></span>Figure 6.2-1 UML for
AbstractServiceBusConnectionFactory Interface

> CERT JAVA-000316 \[The Java CAL shall provide the public
> uci.AbstractServiceBusConnectionFactory interface with methods defined
> in the “AbstractServiceBusConnectionFactory Interface Definition”
> table.\]

<span id="_Toc219292552" class="anchor"></span>Table 6.2-1
AbstractServiceBusConnectionFactory Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public AbstractServiceBusConnection</td>
<td><p>createAbstractServiceBusConnection(java.lang.String serviceInitId) throws UCIException</p>
<p>This method is used to create a new ASB instance for use by the service having the specified init id. An exception is thrown if the service is not allowed to use this ASB or if one of the required initialization activities fail.</p></td>
</tr>
<tr class="even">
<td>public java.lang.String</td>
<td><p>getName() throws UCIException</p>
<p>Returns the name of this AbstractServiceBusConnectionFactory instance.</p></td>
</tr>
</tbody>
</table>

Abstract Service Bus Factory Loader
-----------------------------------

The ASB factory loader shown in Figure 6.3-1, UML for
AbstractServiceBusConnectionFactoryLoader Class, uses the Java’s service
loader to load the AbstractServiceBusConnectionFactory implementation.

<img src="media/image6.png" style="width:6.5in;height:1.21875in" />

<span id="_Toc219292534" class="anchor"></span>Figure 6.3-1 UML for
AbstractServiceBusConnectionFactoryLoader Class

> CERT JAVA-000332 \[The Java CAL shall provide the public
> uci.service.AbstractServiceBusConnectionFactoryLoader final class with
> methods defined in the “AbstractServiceBusConnectionFactoryLoader
> Final Class Definition” table.\]

<span id="_Toc219292553" class="anchor"></span>Table 6.3-1
AbstractServiceBusConnectionFactoryLoader Final Class Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>private Constructor</td>
<td>AbstractServiceBusConnectionFactoryLoader()</td>
</tr>
<tr class="even">
<td>public static java.util.List &lt;AbstractServiceBusConnectionFactory&gt;</td>
<td><p>getAbstractServiceBusConnectionFactories() throws UCIException</p>
<p>Return a list of all AbstractServiceBusConnectionFactory instances found on the classpath.</p></td>
</tr>
<tr class="odd">
<td>public static AbstractServiceBusConnectionFactory</td>
<td><p>getAbstractServiceBusConnectionFactory() throws UCIException</p>
<p>Return the AbstractServiceBusConnectionFactory found on the classpath.</p></td>
</tr>
<tr class="even">
<td>public static AbstractServiceBusConnectionFactory</td>
<td><p>getAbstractServiceBusConnectionFactory( java.lang.String name) throws UCIException</p>
<p>Return the</p>
<p>AbstractServiceBusConnectionFactory of the specified name.</p></td>
</tr>
</tbody>
</table>

UCIType Interface
-----------------

The UCIType Interface is a marker interface for types generated by a
Java CAL SJC from the UCI XSD.

> CERT JAVA-001471 \[A Java CAL API shall provide the interface
> uci.UCIType.\]
>
> CERT JAVA-001715 \[A Java CAL API shall implement the uci.UCIType
> interface for each normal class declaration generated from the
> schema.\]

Bounded List
------------

Java CAL Implementations provide bounded list objects that implement the
java.util.List interface, shown in Figure 6.5-1, UML for BoundedList
Interface. In addition to the methods defined by java.util.List, the
Java CAL Implementation provides the ability to obtain the “minOccurs”
and “maxOccurs” values associated with the bounded list. In the context
of CERT JAVA-000356, the deep copy includes performing an element by
element deep copy of all elements contained in the list.

Java Clients are not able to set bounded list data members based on
existing bounded list objects. Clients may obtain and modify bounded
lists from OMS Message Objects.

The BoundedList is not thread-safe.

<img src="media/image7.png" style="width:6.5in;height:2.38542in" />

<span id="_Toc219292535" class="anchor"></span>Figure 6.5-1 UML for
BoundedList Interface

> CERT JAVA-000356 \[The Java CAL shall provide the public
> uci.BoundedList interface, which extends java.util.List, with methods
> defined in the “BoundedList Interface Definition” table and static
> field defined in the “BoundedList Fields” table.\]

<span id="_Toc219292554" class="anchor"></span>Table 6.5-1 BoundedList
Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public int</td>
<td><p>getMaxOccurs()</p>
<p>Returns this BoundedList’s maxOccurs as specified in the XML Schema specification.</p></td>
</tr>
<tr class="even">
<td>public int</td>
<td><p>getMinOccurs()</p>
<p>Returns this BoundedList’s minOccurs as specified in the XML Schema specification.</p></td>
</tr>
</tbody>
</table>

<span id="_Toc219292555" class="anchor"></span>Table 6.5-2 BoundedList
Fields

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Field and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public static final int</td>
<td><p>UNBOUNDED</p>
<p>The maximum size of a bounded list.</p></td>
</tr>
</tbody>
</table>

Message Listener
----------------

The MessageListener shown in Figure 6.6-1, UML for Message Listener
Interface, is the interface specification of a class of objects that
listen for arriving T messages.

<img src="media/image8.png" style="width:6.5in;height:1.4375in" />

<span id="_Toc219292536" class="anchor"></span>Figure 6.6-1 UML for
Message Listener Interface

> CERT JAVA-000395 \[The Java CAL shall provide the public
> uci.MessageListener&lt;T extends MessageType&gt; interface with
> methods defined in the “Message Listener Interface Definition”
> table.\]

<span id="_Toc219292556" class="anchor"></span>Table 6.6-1 Message
Listener Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public void</td>
<td><p>handleMessage(T message) throws UCIException</p>
<p>The handleMessage method is used to handle incoming messages.</p></td>
</tr>
</tbody>
</table>

Message Reader
--------------

The Java CAL interface for polling shown in Figure 6.7-1, UML for
Message Reader Interface, is designed to handle a single OMS Message
Object per invocation. The read operation accepts a single argument
specifying the timeout value. A timeout value of zero never expires, and
the call blocks indefinitely. If successful, the read operation returns
a reference to the OMS Message Object being read. If the operation times
out, null is returned. If no timeout is desired, use the readNoWait
method, which has the same behavior as the read method but returns
immediately.

Java CAL Instances and Clients rely on the Java VM heap to manage the
memory life cycle of OMS Message Objects. Once provided to the CAL
Client, OMS Message Objects will not be modified by the Java CAL. The
provided OMS Message Object references may be freely retained by the CAL
Client. Since the provided OMS object reference is shared by all
listeners, CAL clients should not modify the provided referenced object.

<img src="media/image9.png" style="width:6.5in;height:1.45833in" />

<span id="_Toc219292537" class="anchor"></span>Figure 6.7-1 UML for
Message Reader Interface

> CERT JAVA-000409 \[The Java CAL shall provide the public
> uci.MessageReader&lt;T extends MessageType&gt; interface that extends
> java.lang.AutoCloseable with the methods defined in the “Message
> Reader Interface Definition” table.\]

<span id="_Toc219292557" class="anchor"></span>Table 6.7-1 Message
Reader Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public MessageListener&lt;T&gt;</td>
<td><p>addListener(MessageListener&lt;T&gt; listener) throws UCIException</p>
<p>Registers a listener that will listen for new messages as they arrive.</p></td>
</tr>
<tr class="even">
<td>public void</td>
<td><p>close() throws UCIException</p>
<p>Closes this reader.</p></td>
</tr>
<tr class="odd">
<td>public T</td>
<td><p>read(long timeoutSeconds) throws UCIException</p>
<p>Reads arriving messages. If no messages have arrived previous to the invocation of this method, then this method will block waiting for messages to arrive or until the timeout expires in which case this method will immediately return null. Once messages are available for processing, the messages will be returned in FIFO order. The timeoutSeconds argument indicates a maximum time in seconds to wait for new messages to arrive. A timeoutSeconds value of zero never expires, and the call blocks indefinitely. If no timeout is desired, use the readNoWait method.</p></td>
</tr>
<tr class="even">
<td>public T</td>
<td><p>readNoWait() throws UCIException</p>
<p>Reads arriving messages. If no messages have arrived previous to the invocation of this method, then this method will immediately return null. If messages are available for processing, the messages will be returned in FIFO order.</p></td>
</tr>
<tr class="odd">
<td>public void</td>
<td><p>removeListener(MessageListener&lt;T&gt; listener) throws UCIException</p>
<p>Removes the specified listener that was previously added to listen to the arrival of new messages.</p></td>
</tr>
</tbody>
</table>

Message Writer
--------------

The MessageWriter shown in Figure 6.8-1, UML for Message Writer
Interface, writes messages to specified topics. The write operation
accepts a single OMS Message Object that is not modified by the Java
CAL. The OMS Message Object may be freely reused by a CAL Client when
the write operation returns.

<img src="media/image10.png" style="width:6.5in;height:1.39583in" />

<span id="_Toc219292538" class="anchor"></span>Figure 6.8-1 UML for
Message Writer Interface

> CERT JAVA-000431 \[The Java CAL shall provide the public
> uci.MessageWriter&lt;T extends MessageType&gt; interface that extends
> java.lang.AutoCloseable with methods defined in the “MessageWriter
> Interface Definition” table.\]

<span id="_Toc219292558" class="anchor"></span>Table 6.8-1 MessageWriter
Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public void</td>
<td><p>close() throws UCIException</p>
<p>Closes this writer.</p></td>
</tr>
<tr class="even">
<td>public void</td>
<td><p>write(T message) throws UCIException</p>
<p>Writes the message to the target specified when this Writer was constructed.</p></td>
</tr>
</tbody>
</table>

UCI Exception
-------------

The base class of exceptions that are thrown by UCI methods are depicted
in Figure 6.9-1, UML for UCIException Class.

<img src="media/image11.png" style="width:6.5in;height:3.70833in" />

<span id="_Toc219292539" class="anchor"></span>Figure 6.9-1 UML for
UCIException Class

> CERT JAVA-000447 \[The Java CAL shall provide the public
> uci.UCIException class, which extends java.lang.Exception, with the
> methods defined in the “UCIException Class Definition” table.\]

<span id="_Toc219292559" class="anchor"></span>Table 6.9-1 UCIException
Class Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public Constructor</td>
<td>UCIException()</td>
</tr>
<tr class="even">
<td>public Constructor</td>
<td>UCIException(long errorCode)</td>
</tr>
<tr class="odd">
<td>public Constructor</td>
<td>UCIException(java.lang.String reason)</td>
</tr>
<tr class="even">
<td>public Constructor</td>
<td>UCIException(java.lang.String reason, long errorCode)</td>
</tr>
<tr class="odd">
<td>public Constructor</td>
<td>UCIException(java.lang.String reason, java.lang.Throwable cause)</td>
</tr>
<tr class="even">
<td>public Constructor</td>
<td>UCIException(java.lang.String reason, java.lang.Throwable cause, long errorCode)</td>
</tr>
<tr class="odd">
<td>public Constructor</td>
<td>UCIException(java.lang.Throwable cause)</td>
</tr>
<tr class="even">
<td>public Constructor</td>
<td>UCIException(java.lang.Throwable cause, long errorCode)</td>
</tr>
<tr class="odd">
<td>public long</td>
<td><p>getErrorCode()</p>
<p>Returns this exception’s error code which was specified when the exception was created.</p></td>
</tr>
</tbody>
</table>

UUID Factory
------------

The UUIDFactory in Figure 6.10-1, UML for UUIDFactory Interface,
provides the ability to create UUIDs for creating and modifying OMS
Messages.

<img src="media/image12.png" style="width:6.5in;height:1.77083in" />

<span id="_Toc219292540" class="anchor"></span>Figure 6.10-1 UML for
UUIDFactory Interface

> CERT JAVA-001572 \[The Java CAL shall provide the public
> uci.UUIDFactory interface with methods defined in the “UUIDFactory
> Interface Definition” table.\]

<span id="_Toc219292560" class="anchor"></span>Table 6.10-1 UUIDFactory
Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public java.lang.String</td>
<td><p>getName()</p>
<p>Returns the name of this UUIDFactory instance.</p></td>
</tr>
<tr class="even">
<td>public java.util.UUID</td>
<td><p>getNilUUID()</p>
<p>This method will return an RFC 4122 nil UUID. The returned value may be a consistent instance or a different instance for each call</p></td>
</tr>
<tr class="odd">
<td>public java.util.UUID</td>
<td><p>generateUUID()</p>
<p>This method will generate a new RFC 4122 Version 1 or 4 UUID</p></td>
</tr>
<tr class="even">
<td>public java.util.UUID</td>
<td><p>getNamespaceUUID()</p>
<p>This method returns the UUID that can be used as the namespace for the createVersion3UUID(java.util.UUID namespace, java.lang.String name) method to create OMS Platform-specific, consistent UUIDs.</p></td>
</tr>
<tr class="odd">
<td>public java.util.UUID</td>
<td><p>createVersion3UUID(java.util.UUID namespace, java.lang.String name)</p>
<p>This method will create a new deterministic time-invariant RFC 4122 Version 3 UUID based on the provided namespace and name. The name is converted to UTF-8 for hashing and should be meaningful and unique. The namespace is itself a UUID and not a string representation of a UUID and is RFC 4122 conformant.</p></td>
</tr>
<tr class="even">
<td>public java.util.UUID</td>
<td><p>createVersion3UUID(java.lang.String name)</p>
<p>This method will create a new deterministic time-invariant RFC 4122 Version 3 UUID based on the provided name using an internal namespace that is unique to each Platform. The name is converted to UTF-8 for hashing and should be meaningful and unique. The getNamespaceUUID() method will return the namespace UUID used to create the RFC 4122 Version 3 UUID.</p></td>
</tr>
</tbody>
</table>

UUID Factory Loader
-------------------

The UUID factory loader shown in Figure 6.11-1, UML for
UUIDFactoryLoader Class, uses the Java’s service loader to load a
UUIDFactory implementation.

<img src="media/image13.png" style="width:6.5in;height:1.67708in" />

<span id="_Toc219292541" class="anchor"></span>Figure 6.11-1 UML for
UUIDFactoryLoader Class

> CERT JAVA-001578 \[The Java CAL shall provide the public
> uci.service.UUIDFactoryLoader final class with methods defined in the
> “UUIDFactoryLoader Final Class Definition” table.\]

<span id="_Toc219292561" class="anchor"></span>Table 6.11-1
UUIDFactoryLoader Final Class Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>private Constructor</td>
<td>UUIDFactoryLoader()</td>
</tr>
<tr class="even">
<td>public static java.util.List&lt;uci.UUIDFactory&gt;</td>
<td><p>getUUIDFactories() throws uci.UCIException</p>
<p>Return a list of all UUIDFactory instances found on the classpath.</p></td>
</tr>
<tr class="odd">
<td>public static uci.UUIDFactory</td>
<td><p>getUUIDFactory() throws uci.UCIException</p>
<p>Return any UUIDFactory found on the classpath</p></td>
</tr>
<tr class="even">
<td>public static uci.UUIDFactory</td>
<td><p>getUUIDFactory(java.lang.String name) throws uci.UCIException</p>
<p>Return the UUIDFactory of the Abstract Service Bus connection factory with the specified name.</p></td>
</tr>
</tbody>
</table>

Version Info
------------

The class encapsulating the version information for the instance of the
Java CAL Implementation is depicted in Figure 6.12-1, UML for Version
Info Class.

<img src="media/image14.png" style="width:6.5in;height:2.09375in" />

<span id="_Toc219292542" class="anchor"></span>Figure 6.12-1 UML for
Version Info Class

> CERT JAVA-000483 \[The Java CAL shall provide the public
> uci.VersionInfo class with the methods defined in the “Version Info
> Class Definition” table.\]

<span id="_Toc219292562" class="anchor"></span>Table 6.12-1 Version Info
Class Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public Constructor</td>
<td>VersionInfo(java.lang.String calVersion)</td>
</tr>
<tr class="even">
<td>public java.lang.String</td>
<td><p>getAPIGeneratorVersion()</p>
<p>Returns the version of the tool used to generate this CAL API</p></td>
</tr>
<tr class="odd">
<td>public java.lang.String</td>
<td><p>getAPIVersion()</p>
<p>Returns the version of this generated CAL API</p></td>
</tr>
<tr class="even">
<td>public java.lang.String</td>
<td><p>getCALVersion()</p>
<p>Returns the version of the CAL Implementation</p></td>
</tr>
<tr class="odd">
<td>public java.lang.String</td>
<td><p>getSchemaVersion()</p>
<p>Returns the schema version as defined at the top of the schema used to generate this CAL API</p></td>
</tr>
<tr class="even">
<td>public java.lang.String</td>
<td><p>getOMSApiVersion()</p>
<p>Returns the OMS API version</p></td>
</tr>
<tr class="odd">
<td>public java.lang.String</td>
<td>toString()</td>
</tr>
</tbody>
</table>

Externalizer
------------

The Externalizer API allows an externally generated tool, built to the
API, to export/import to an external format. The Externalizer API allows
for the replacement of the to/from XML functionality, but also allows a
method to export/import to an external format regardless of underlying
CAL serialization and/or transport.

<img src="media/image15.png" style="width:6.5in;height:2.30208in" />

<span id="_Toc219292543" class="anchor"></span>Figure 6.13-1 UML for
Externalizer Interface

> CERT JAVA-001380 \[The Java CAL shall provide the public
> uci.Externalizer interface, with methods defined in the “Externalizer
> Interface Definition” table.\]

<span id="_Toc219292563" class="anchor"></span>Table 6.13-1 Externalizer
Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier, Type and Method Generic Parameter</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public &lt;T extends UCIType&gt; T</td>
<td><p>read(java.io.Reader, java.lang.Class&lt;T&gt;) throws UCIException</p>
<p>reads in model object with a Reader object</p></td>
</tr>
<tr class="even">
<td>public &lt;T extends UCIType&gt; T</td>
<td><p>read(java.io.File, java.lang.Class&lt;T&gt;) throws UCIException</p>
<p>reads in model object with a File object</p></td>
</tr>
<tr class="odd">
<td>public &lt;T extends UCIType&gt; T</td>
<td><p>read(java.io.InputStream, java.lang.Class&lt;T&gt;) throws UCIException</p>
<p>reads in model object with a InputStream object</p></td>
</tr>
<tr class="even">
<td>public &lt;T extends UCIType&gt; void</td>
<td><p>write(java.io.Writer, T) throws UCIException</p>
<p>writes out model object with Writer object</p></td>
</tr>
<tr class="odd">
<td>public &lt;T extends UCIType&gt; void</td>
<td><p>write(java.io.File, T) throws UCIException</p>
<p>writes out model object with File object</p></td>
</tr>
<tr class="even">
<td>public &lt;T extends UCIType&gt; void</td>
<td><p>write(java.io.OutputStream, T) throws UCIException</p>
<p>writes out model object with OutputStream object</p></td>
</tr>
<tr class="odd">
<td>public String</td>
<td><p>getSchemaVersion()throws UCIException</p>
<p>gets schema version associated with this Externalizer</p></td>
</tr>
<tr class="even">
<td>public String</td>
<td><p>getEncoding() throws UCIException</p>
<p>gets the Externalizer encoding type for this Externalizer</p></td>
</tr>
<tr class="odd">
<td>public String</td>
<td><p>getCalApiVersion() throws UCIException</p>
<p>gets the CAL API version for this Externalizer</p></td>
</tr>
<tr class="even">
<td>public String</td>
<td><p>getVendor() throws UCIException</p>
<p>gets the vendor of this Externalizer</p></td>
</tr>
<tr class="odd">
<td>public String</td>
<td><p>getVendorVersion() throws UCIException</p>
<p>gets the vendor version of this Externalizer</p></td>
</tr>
</tbody>
</table>

Externalizer Loader
-------------------

The Externalizer Loader API allows an externally generated tool to be
loaded by the CAL.

<img src="media/image16.png" style="width:6.5in;height:1.5in" />

<span id="_Toc219292544" class="anchor"></span>Figure 6.14-1 UML for
ExternalizerLoader Class

> CERT JAVA-001385 \[The Java CAL shall provide the public
> uci.service.ExternalizerLoader final class, with methods defined in
> the “ExternalizerLoader Final Class Definition” table.\]

<span id="_Toc219292564" class="anchor"></span>Table 6.14-1
ExternalizerLoader Final Class Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>private Constructor</td>
<td>ExternalizerLoader()</td>
</tr>
<tr class="even">
<td>public static Externalizer</td>
<td><p>getExternalizer(String schemaVersion, String calApiVersion, String encoding) throws UCIException</p>
<p>get an Externalizer for a given schema version, API version, and externalizer type</p></td>
</tr>
<tr class="odd">
<td>public static Externalizer</td>
<td><p>getExternalizer() throws UCIException</p>
<p>get the only Externalizer available, throws error if 0 or &gt;1 on the classpath</p></td>
</tr>
<tr class="even">
<td>public static java.util.List&lt;Externalizer&gt;</td>
<td><p>getExternalizers() throws UCIException</p>
<p>get all service loaded externalizers</p></td>
</tr>
</tbody>
</table>

AbstractServiceBusConnection Status
-----------------------------------

The AbstractServiceBusConnection Status classes provide the Java API
requirements for the AbstractServiceBusConnection status.

### AbstractServiceBusConnectionStatusListener class

The AbstractServiceBusConnectionStatusListener class is responsible for
providing support needed to listen for changes in the operation status
of the ASB.

> CERT JAVA-001307 \[The Java CAL shall provide the public
> uci.AbstractServiceBusConnectionStatusListener interface with the
> methods defined in the “AbstractServiceBusConnectionStatusListener
> Interface Definition” table.\]

<span id="_Toc219292565" class="anchor"></span>Table 6.15-1
AbstractServiceBusConnectionStatusListener Interface Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public void</td>
<td>statusChanged(uci.AbstractServiceBusConnectionStatusData status)</td>
</tr>
</tbody>
</table>

### AbstractServiceBusConnectionStateEnum enumeration

The AbstractServiceBusConnectionStateEnum provides all possible states
of the ASB.

> CERT JAVA-001310 \[The Java CAL shall provide the public
> uci.AbstractServiceBusConnectionStateEnum enum with the enumeration
> constants defined in the “AbstractServiceBusConnectionStateEnum Enum
> Definition” table.\]

<span id="_Toc219292566" class="anchor"></span>Table 6.15-2
AbstractServiceBusConnectionStateEnum Enum Definition

<table>
<thead>
<tr class="header">
<th>Enum Constant Name</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>INITIALIZING</td>
<td>CAL is starting up, where initialization has begun but is not complete. Read and write methods will return an error. Blocking reads will behave as normal</td>
</tr>
<tr class="even">
<td>NORMAL</td>
<td>CAL is functioning normally, All QoS settings, as applicable, are being met. Read and write methods will behave as normal. Blocking reads will behave as normal</td>
</tr>
<tr class="odd">
<td>DEGRADED</td>
<td>Not all QoS settings are being satisfied. The CAL can send and receive but QoS settings are not being satisfied. Read and write methods will behave as normal. Blocking reads will behave as normal</td>
</tr>
<tr class="even">
<td>INOPERABLE</td>
<td>CAL is unable to send or receive messages and is attempting to recover. Read and write methods will return an error. Blocking reads will behave as normal</td>
</tr>
<tr class="odd">
<td>FAILED</td>
<td>Identical to Inoperable state but recovery is not possible. Read and write methods will return an error. Blocking reads will release thread, returning a UCI exception</td>
</tr>
</tbody>
</table>

### AbstractServiceBusConnectionStatusData class

The AbstractServiceBusConnectionStatusData class provides the status
payload provided by the statusChanged method of the
AbstractServiceBusConnectionStatusListener or returned by the getStatus
method of the AbstractServiceBusConnection.

> CERT JAVA-001313 \[The Java CAL shall provide the public
> uci.AbstractServiceBusConnectionStatusData class with the methods
> defined in the “AbstractServiceBusConnectionStatusData Class
> Definition” table.\]

<span id="_Toc219292567" class="anchor"></span>Table 6.15-3
AbstractServiceBusConnectionStatusData Class Definition

<table>
<thead>
<tr class="header">
<th>Modifier and Type</th>
<th>Method and Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>public (Constructor)</td>
<td>AbstractServiceBusConnectionStatusData(uci.AbstractServiceBusConnectionStateEnum state, java.lang.String stateDetail)</td>
</tr>
<tr class="even">
<td>public AbstractServiceBusConnectionStateEnum</td>
<td>getState() returns connection state enumeration</td>
</tr>
<tr class="odd">
<td>public java.lang.String</td>
<td>getStateDetail() return details string defined by CAL Implementation</td>
</tr>
</tbody>
</table>

Java CAL CERT Verification
==========================

Verification is normally performed by inspection, analysis,
demonstration and/or test. These CERTS are typically verified either by
inspection of specific documents, analysis of test results, or
demonstration of specific OMS Services or programs that prove that
something has been implemented properly.

One of the goals of proving OMS compliance is to leverage existing test
plan artifacts and not to generate duplicate testing.

Acronyms and Symbols
====================

For the OMS list of acronyms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.

Glossary
========

For the glossary of terms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.
