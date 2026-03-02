Open Mission Systems (OMS)

Definition And Documentation (D&D)

Critical Abstraction Layer (CAL) Specification

<img src="media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 January 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary, open architecture
standard for integrating subsystems and services into mission packages.

This document defines the required attributes and behaviors for
implementations of the Open Mission Systems (OMS) Critical Abstraction
Layer (CAL) Application Programming Interface (API). A provider of an
OMS Platform is responsible for delivering a CAL Implementation for each
programming language with a defined CAL API. The required attributes and
behaviors defined by this document provide commonality between disparate
CAL Implementations, regardless of the messaging technology stack
selected by the implementer. This document makes no restriction on the
tools, libraries, or products that may be used to meet the requirements
and fully implement the CAL API.

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
<td>L</td>
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

[3.1 Related Standards 3](#related-standards)

[3.2 OMS D&D Documents 3](#oms-dd-documents)

[4 CAL Terms and Definitions 4](#cal-terms-and-definitions)

[4.1 OMS Message 5](#oms-message)

[4.2 CAL Application Programming Interface (API)
5](#cal-application-programming-interface-api)

[4.3 CAL Messages 5](#cal-messages)

[4.4 CAL Client 6](#cal-client)

[4.5 CAL Implementation 6](#cal-implementation)

[4.6 CAL Instance 7](#cal-instance)

[4.7 Network Configuration 7](#network-configuration)

[4.8 Publish and Subscribe 7](#publish-and-subscribe)

[4.9 CAL Messages, Readers, Writers, and Factories
7](#cal-messages-readers-writers-and-factories)

[4.10 Service Identifier 8](#service-identifier)

[4.11 Topics and Connections 8](#topics-and-connections)

[4.12 Abstract Service Bus 9](#abstract-service-bus)

[5 CAL Requirements 10](#cal-requirements)

[5.1 General CAL Requirements 10](#general-cal-requirements)

[5.1.1 Execution Models 10](#execution-models)

[5.1.2 Error Handling 11](#error-handling)

[5.1.3 Schemas Compatibility 11](#schemas-compatibility)

[5.2 CAL Interface 12](#cal-interface)

[5.2.1 Integer Type 12](#integer-type)

[5.2.2 Time Types 13](#time-types)

[5.2.3 UUID Type 13](#uuid-type)

[5.3 CAL Initialization 14](#cal-initialization)

[5.4 Topics 15](#topics)

[5.5 CAL Messages 16](#cal-messages-1)

[5.5.1 CAL Message Contents 16](#cal-message-contents)

[5.5.1.1 Optional Fields 16](#optional-fields)

[5.5.1.2 Required Fields 16](#required-fields)

[5.5.1.3 Bounded Lists 17](#bounded-lists)

[5.5.1.4 Choices 17](#choices)

[5.5.1.5 Sequences 17](#sequences)

[5.5.1.6 Enumerations 17](#enumerations)

[5.5.1.7 Validation 17](#validation)

[5.5.2 CAL Message Construction 18](#cal-message-construction)

[5.5.2.1 Optional Fields 18](#optional-fields-1)

[5.5.2.2 Required Fields 18](#required-fields-1)

[5.5.2.3 Bounded Lists 19](#bounded-lists-1)

[5.5.2.4 Choices 19](#choices-1)

[5.5.2.5 Enumeration 19](#enumeration)

[5.5.3 Message Destruction 19](#message-destruction)

[5.5.4 Accessing Message Values 19](#accessing-message-values)

[5.5.4.1 Optional Fields 20](#optional-fields-2)

[5.5.4.2 Required Fields 20](#required-fields-2)

[5.5.4.3 Bounded Lists 21](#bounded-lists-2)

[5.5.4.4 Choices 21](#choices-2)

[5.5.4.5 Sequences 21](#sequences-1)

[5.6 Writers 22](#writers)

[5.7 Readers 23](#readers)

[5.7.1 Callback Interface 24](#callback-interface)

[5.7.2 Polling Interface 25](#polling-interface)

[5.8 CAL QoS Settings 25](#cal-qos-settings)

[5.8.1 Time Based Filter 26](#time-based-filter)

[5.8.2 Reliability 26](#reliability)

[5.8.3 Expiration 27](#expiration)

[5.8.4 Message Buffer 28](#message-buffer)

[5.9 Abstract Service Bus Connection Status
29](#abstract-service-bus-connection-status)

[6 CAL CERT Verification 34](#cal-cert-verification)

[7 Acronyms and Symbols 35](#acronyms-and-symbols)

[8 Glossary 36](#glossary)

List of Figures

[Figure 1.0-1 CAL API Message Generation Process 1](#_Toc219292478)

[Figure 4.0-1 CAL Client Stack 4](#_Toc219292479)

[Figure 4.11-1 CAL and Client Topics 8](#_Toc219292480)

[Figure 5.9-1 CAL Abstract Service Bus Connection Status State Diagram
31](#_Toc219292481)

[Figure 5.9-2 CAL Abstract Service Bus Connection Status State
Transitions 32](#_Toc219292482)

This page is intentionally left blank.

List of Tables

[Table 3.1-1 Reference Standards 3](#_Toc219292483)

[Table 3.2-1 OMS D&D Documents 3](#_Toc219292484)

[Table 5.8-1 CAL Reliability Definitions 26](#_Toc219292485)

[Table 5.9-1 CAL Abstract Service Bus Connection Status State Definition
30](#_Toc219292486)

[Table 5.9-2 CAL Abstract Service Bus Connection Status State Behaviors
33](#_Toc219292487)

This page is intentionally left blank.

Introduction
============

The CAL API is defined by the translation of the OMS Message Schema, an
XML Schema Definition (XSD) file, to software message types called CAL
Message containers or simply CAL Messages (see Figure 1.0-1, CAL API
Message Generation Process). The CAL API provides the means for the
creation of these CAL Messages as well as the setting and accessing of
their fields. The CAL API also defines the interface through which
applications send and receive CAL Messages. This interface decouples the
technical implementations from the interface to enable future technology
upgrades and provide flexibility that allows Platform, Subsystem, and
Service providers to offer innovative and competitive solutions to
future problems. This document defines the requirements that ensure the
disparate implementations, each developed to solve unique performance
requirements, all behave in a common manner. The over-arching goal is
that a software application developed and tested against a specific CAL
Implementation, can be compiled against any given CAL Implementation and
execute properly. The requirements levied in this document provide
common CAL behavior and Quality of Service (QoS) attributes available
for topics (see Section 4.11, Topics and Connections). Good systems
engineering will still be required to ensure that when a software
application moves between CAL Implementations the application still
meets its functional mission requirements.

<img src="media/image2.png" style="width:6.5in;height:3.41667in" />

<span id="_Toc219292478" class="anchor"></span>Figure 1.0-1 CAL API
Message Generation Process

Scope
=====

In the following sections, the CAL Specification requirements for a
compliant OMS CAL Implementation are described and enumerated as
certification requirements (CERTs). Guidance and descriptive text have
been added to assist the developer in achieving the goals of this
specification and to help verification engineers fully understand the
intention of the requirements and how they should be tested.

References 
==========

Related Standards
-----------------

The documents listed in Table 3.1-1, Reference Standards, are cited
throughout this document. For dated references, only the edition cited
applies. For undated references, the latest edition of the referenced
document (including any amendments or corrigenda) applies.

<span id="_Toc219292483" class="anchor"></span>Table 3.1-1 Reference
Standards

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
<td>IETF RFC 4122</td>
<td>A Universally Unique IDentifier (UUID) URN Namespace</td>
<td></td>
<td>July 2005</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>Extensible Markup Language (XML) 1.0 (Fifth Edition)</td>
<td>1.0</td>
<td>26 November 2008</td>
</tr>
<tr class="odd">
<td>N/A</td>
<td>XML Schema Part 1: Structures Second Edition</td>
<td>1.0</td>
<td>28 October 2004</td>
</tr>
<tr class="even">
<td>N/A</td>
<td>XML Schema Part 2: Datatypes Second Edition</td>
<td>1.0</td>
<td>28 October 2004</td>
</tr>
</tbody>
</table>

OMS D&D Documents
-----------------

The documents listed in Table 3.2-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219292484" class="anchor"></span>Table 3.2-1 OMS D&D
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

CAL Terms and Definitions
=========================

The Critical Abstraction Layer (CAL) is an OMS architecture concept and
approach supporting the standardized OMS Messaging between the OMS
Platform and the OMS Subsystems, Services, and Isolators that are part
of an OMS Mission Package. A CAL is realized by a CAL Implementation
that supports the CAL Application Programming Interface (API) through
which Subsystems, Services, and Isolators interact with the CAL
messaging library as shown in Figure 4.0-1, CAL Client Stack. The API
includes interfaces to CAL Messages as well as the methods for
publishing and receiving those messages. OMS Messaging interactions
between OMS participants must use the CAL-provided publish and subscribe
interface. CAL Messages provided by the messaging library may be used
within services for any purpose desired by the service implementers. CAL
APIs are designed to guarantee commonality of the CAL API across CALs
for the same OMS version for that language.

<img src="media/image3.png" style="width:6.5in;height:3.25in" />

<span id="_Toc219292479" class="anchor"></span>Figure 4.0-1 CAL Client
Stack

OMS Message
-----------

OMS Messages are primarily command-and-control-oriented exchanges used
inside of a Mission Package to coordinate key mission functionality,
technical capabilities, and operational behaviors of the interaction
between the Architecture Elements (Platforms, Subsystems, Services, and
Isolators).

An OMS Message is a unit of information exchanged sent or received using
an OMS CAL. The content and structure of OMS Messages are defined using
an eXtensible Markup Language (XML) Schema Definition (XSD)
specification that conforms to the UCI Schema Style and Design
Specification (OAC-SPC-001) message schema. The XSD is translated in
accordance with the OMSC-SPC-008, C++ CAL Interface Generation
Specification, or OMSC-SPC-007, Java CAL Interface Generation
Specification (see Table 3.2-1, OMS D&D Documents) to create the CAL
API.

CAL Application Programming Interface (API)
-------------------------------------------

The CAL API is the interface that Subsystems, Services, and Isolators
use to access the capabilities supported by a CAL (e.g., the exchanges
of OMS Messages). CAL APIs are designed to guarantee commonality of the
CAL API across CALs for the same OMS version for that language.

CAL Messages
------------

CAL Messages are representations of OMS Messages (see Section 4.1, OMS
Messages) as defined by the CAL API. The CAL and its API provide the
means to create, destroy, manipulate, send, and receive CAL Messages. A
CAL Implementation (see Section 4.5, CAL Implementation) converts back
and forth between OMS Messages and CAL Messages; a process sometimes
called de-serialization/serialization. When the message is being
manipulated by the CAL API or CAL Client it is an OMS Message. When the
message is in its serialized form it is a CAL Message.

CAL Client
----------

A CAL Client (see Figure 4.0-1, CAL Client Stack) exclusively uses the
CAL API to create access, set, publish, and receive CAL Messages. Each
CAL Client is uniquely identified by an argument passed to the CAL when
getting the handle to the CAL instance (see Section 4.6 CAL Instance).
Throughout this document the term “CAL Client” is used to indicate the
software that is using or invoking the CAL Implementation through the
CAL API. One type of CAL Client is an OMS Service; however, CALs may be
used by applications that are not fully compliant OMS Services.

CAL Clients are responsible for obtaining access to and initializing an
instance of a CAL Implementation (see Section 4.5, CAL Implementation).
Under special circumstances, a CAL Client may obtain access to and
initialize multiple instances of one or more CAL Implementations. CAL
Clients are only allowed to utilize a single instance of a CAL
Implementation for a given network configuration. In effect, this means
that when a CAL Client chooses to create multiple instances of a CAL
Implementation, the set of communication links created for each of those
instances will be unique as a whole. This will prevent the scenario of a
single CAL Client sending a single message multiple times over
essentially the same communications link. Special circumstances for
having multiple instances of one or more CAL Implementations might
include: a “bridging” application for translating OMS Messages between
two different CAL Implementations; or bridging two instances of the same
CAL Implementation configured for different networks.

CAL Implementation
------------------

A CAL Implementation is a manifestation and fulfillment of the CAL API
that adheres to the requirements defined in this CAL Specification. One
or more CAL Implementations serve as an integral component of an OMS
Platform Abstract Service Bus (ASB) (see Section 4.12, Abstract Service
Bus) and are provided by the OMS Platform. A Platform must make
available an appropriate CAL Implementation that satisfies the CAL API
in all languages with OMS Standard-defined XSD-to-API translations.
Currently, only the C++ (specified by OMSC-SPC-008, C++ CAL Interface
Generation Specification) and Java (specified by OMSC-SPC-007, Java CAL
Interface Generation Specification) languages are supported in OMS. CAL
Implementations do not have to be fully implemented in the same language
as the interface. For example, a C++ CAL Implementation may satisfy the
C++ CAL interface while being partially implemented in C or Java.
Developers of Encoders/Decoders in both C++ and Java must be sensitive
to the fact that there are unsigned data types in the schema and handle
appropriately.

CAL Instance
------------

CAL instance refers to the specific instantiation of a Platform’s CAL
Implementation used by a particular CAL Client. Each CAL instance will
maintain a unique set of resources related to its network configuration
(see Section 4.6, Network Configuration) and the memory management
provided to the CAL Client through CAL API factories (note that memory
management only applies to C++ CALs).

Network Configuration
---------------------

The CAL instance is configured at runtime to connect with underlying
middleware technologies, network resources, and transport layers. The
Network Configuration identifies valid CAL Topics, their associated
network connections, and how these network connections are actually
implemented across the available network resources. A CAL instance can
only have one network configuration, but CAL Clients may create multiple
CAL instances that each have distinct network configurations.

Publish and Subscribe
---------------------

The CAL Implementation presents a publish/subscribe architecture to the
CAL Client. A publish/subscribe architecture is a messaging pattern
consisting of message publishers and subscribers. A publisher is a
client that creates and sends messages. A subscriber is a client that
receives messages. A client may be both a publisher and a subscriber.
Publishers do not send messages directly to specific subscribers but
publish without knowledge of what, if any, subscribers may receive the
message. Similarly, subscribers express interest in one or more messages
without knowledge of what, if any, publishers may generate those
messages. The CAL Implementation may achieve this publish/subscribe
architecture through many different approaches, including direct
connections between message generators and receivers. The programming
model from the CAL Client’s perspective is always publish/subscribe.

CAL Messages, Readers, Writers, and Factories
---------------------------------------------

CAL Implementations consist of several components including CAL
Messages, Readers, Writers, and Factories. CAL Readers are entities used
by CAL Clients to receive incoming CAL Messages and CAL Writers are
entities used by CAL Clients to send CAL Messages. CAL Factories are
entities used by CAL Clients to create CAL Readers and CAL Writers. C++
CAL Clients also use Factories to create CAL Messages, while Java CAL
Clients use the “new” operator (or an implicit new operation) to create
CAL Messages. The behaviors of the CAL and each of these components are
defined in Section 5.0, CAL Requirements.

Service Identifier
------------------

A Service Identifier is a string name given to a Service that is used to
associate it with a globally unique identifier called a Universally
Unique Identifier (UUID) (Internet Engineering Task Force (IETF) Request
for Comments (RFC) 4122) specific to an instance of that Service on a
single specific system. By system, it is meant an element that could be
represented as: a vehicle; a node acting as a collection of vehicles; a
node on the ground control system; etc. The Service Identifier is a key
argument used to initialize a CAL instance by the CAL Client.

Topics and Connections
----------------------

A Connection is a communication link established between a CAL Reader
and a CAL Writer through the Abstract Service Bus (see Section 4.12,
Abstract Service Bus). A CAL Topic is a CAL Implementation’s internal
identifier for a communications link between CAL Readers and CAL
Writers. Multiple Connections may be associated with a single CAL Topic:
CAL Writers can have Connections to multiple CAL Readers over a given
CAL Topic; and CAL Readers can have Connections to multiple CAL Writers
over a given CAL Topic. A Client Topic is the logical topic name used by
a CAL Client to identify the communications between CAL Readers and CAL
Writers. A CAL Implementation maps internal CAL Topics to Client Topics.
Figure 4.11-1, CAL and Client Topics, depicts these interactions.

<img src="media/image4.png" style="width:6.5in;height:3.19792in" />

<span id="_Toc219292480" class="anchor"></span>Figure 4.11-1 CAL and
Client Topics

Abstract Service Bus
--------------------

The Abstract Service Bus (ASB) is the collection of resources that at a
minimum allow IP based network traffic, in the form of OMS Messages;
from one CAL instance to another given that they are of the same CAL
Implementation. An ASB may also contain other network traffic that a CAL
instance is not aware of. The network related resources of an ASB are
defined in part by the aggregation of network configurations (see
Section 4.7, Network Configuration) of all active CAL Clients. In
general, a CAL Client is completely unaware of how the ASB performs its
responsibilities and of the resources it uses.

CAL Requirements
================

General CAL Requirements
------------------------

These requirements apply to the CAL Implementation in general. CAL
Clients have a general expectation that CAL Implementations have
thread-safe readers, writers, and message factories. Those methods that
are required to be thread-safe are identified explicitly in the
OMSC-SPC-008, C++ CAL Interface Generation Specification, and
OMSC-SPC-007, Java CAL Interface Generation Specification. However,
thread-safety is not a required attribute across an entire CAL
Implementation.

> CERT CAL-005179 \[A C++ CAL Implementation shall implement the methods
> defined by the C++ CAL Interface Generation Specification (document
> OMSC-SPC-008).\]
>
> CERT CAL-005180 \[A Java CAL Implementation shall implement the
> methods defined by the Java CAL Interface Generation Specification
> (document OMSC-SPC-007).\]

### Execution Models

CAL Clients may operate within various execution models: there may be
multiple services within a single address space (e.g., one service per
thread/task); only one service in a single address space; or one service
distributed across multiple address spaces. CAL Implementations must
support the execution model of multiple services within a single address
space. The other execution models are considered to be subsets of this
model because once multiple services within a single address space are
handled; a single service in an address space is well handled. In the
case of one OMS Service distributed across multiple address spaces, it
is assumed that inter-process communication (IPC) to/from the single CAL
instance will be utilized to distribute CAL Messages throughout the
service. Any deviation from this assumption of IPC utilization must be
coordinated with the CAL provider and may not be fully supported. Note
that this implies CAL implementers may assume their CAL will execute
within a single address space.

Under certain circumstances, there may be multiple CAL instances within
a single address space. As previously discussed, each CAL instance
maintains a unique set of resources related to its network configuration
and memory management. Each instance of a CAL Client will have one and
only one instance of a given CAL Implementation for a network
configuration. A CAL Client may act as a “bridge” by translating OMS
Messages between two different CAL Implementations, or between two
instances of the same CAL Implementation configured for different
networks. This means that two instances of the same CAL Implementation
within a single service will not communicate with each other over their
shared ASB.

> CERT CAL-016015 \[A CAL Implementation shall provide multiple CAL
> Clients operating in a single address space with the same behavior as
> if each CAL Client were executing in separate address spaces.\]

Testing criteria for this requirement is to instantiate two services
(two CAL Clients) within a single address space and to show that (a)
each is provided its own Service UUID and (b) when one service publishes
a message and the other subscribes to that same topic, the CAL
appropriately provides the message to the receiving service.

### Error Handling

A CAL Implementation is responsible for detecting, handling, and
reporting error conditions within the CAL Implementation and dependent
software components. When an unrecoverable error condition is detected,
the CAL Implementation will respond by reporting the error to the CAL
Client. The method by which the error is reported is defined in
OMSC-SPC-008, C++ CAL Interface Generation Specification, for C++
implementations and OMSC-SPC-007, Java CAL Interface Generation
Specification for Java implementations (see Section 3, References, for
document details). Certain general error conditions are identified
within this CAL Specification and must be handled in accordance with the
aforementioned C++ and Java CAL Interface Generation Specifications. The
possible error conditions that may be detected and reported by a CAL
Implementation are not limited to those defined in this document.

### Schemas Compatibility

A CAL Implementation is created against a specific version of the OMS
Message Schema. Over time, the OMS Message Schema will be updated and
new versions will be released. There may also be cases where extensions
are made to the schema in order to support new capabilities or service
interactions before the schema modifications are officially adopted in
the standard. In both cases there is a change in the OMS Message Schema
and the compatibility of CAL Implementations built against different
schemas must be addressed.

In the case where changes to the schema are limited to the addition of
new OMS Messages and types, it *may* be possible to generate and build
an extended CAL Implementation that need only be used by services
requiring the new OMS Messages. OMS Services and OMS Subsystems that do
not use the schema additions can continue to use the baseline CAL
Implementation. However, there are commonly used middleware solutions
that do not support instances of CAL Implementations built against
different schemas. In order to not rule out a broad category of
middleware solutions, there is *no requirement* that a CAL
Implementation support interoperability between instances built against
different message schema versions.

CAL Implementations should gracefully ignore messages they cannot
de-serialize. In order to not burden CAL Clients with corrupted data,
errors are not generated when bad messages are received. A CAL
Implementation may log bad message events or report them as auditable
events. A requirement to perform with this specific behavior is not
practical because, depending on the technologies used, a CAL
Implementation may never see messages itself that it cannot de-serialize
in order to drop them or report errors to the CAL Client.

Note: Extending an existing message to include new fields or sub-message
types (see Section 5.5.1, CAL Message Contents) creates a unique message
type. CAL Implementations are based on the association of one message
type to one or many Client Topics (see additional discussion in Section
5.4, Topics). Client Topics may not be associated with more than one
message type. Each instance of a CAL Implementation enforces this
association for its CAL Clients. However, systems engineering or other
enforcement policies are needed to ensure every instance of a CAL
Implementation consistently associates the same message types to
connected Client Topics.

An OMS Message that was generated with a different schema version than
that expected by a CAL Implementation may be rejected. In cases where an
extension schema is used, the CAL Implementation may still be able to
handle the OMS Message. For instances of a CAL Implementation to be
completely compatible they will also be based on the same messaging
schema, including any applicable extensions.

A CAL Implementation may be built specifically for a Client, including
limiting the scope of the message model provided to the Client. The
message model supported by a particular CAL Implementation may be the
full schema or a subset of the schema, provided that interoperability
when exchanging the common elements of the subset-schemas is maintained.
When the CAL Implementation receives a message that falls outside its
restricted message model, the implementation will cleanly ignore that
message.

CAL Interface
-------------

The CAL API is defined by either OMSC-SPC-008, C++ CAL Interface
Generation Specification, or OMSC-SPC-007, Java CAL Interface Generation
Specification depending on whether the implementation language is C++ or
Java respectively. The translation between the OMS Message Schema and
the software APIs plus the required behaviors associated with each
method can be found in the CAL Interface Specifications. However, some
elements of the API are consistent across languages to ensure
interoperability between CALs written in different languages. Those
elements are documented in this section.

### Integer Type

The CAL presents the W3C XML Schema built-in integer datatype as a
64-bit integer in order to provide a performant representation for the
CAL Client.

> CERT CAL-016024 \[A CAL Implementation shall represent the xs:integer
> built-in datatype as a signed 64-bit integer.\]

### Time Types

Several W3C XML Schema built-in datatypes are used to represent time. In
order to allow for compatibility in resolution and a performant
representation for the CAL Client, the CAL API deviates from the W3C
definition in its representation of time datatypes. Because of this
decision, there are facets allowed by the XSD that are not accessible
through the CAL API. CAL Clients may not depend on manipulating those
facets for proper execution.

> CERT CAL-016027 \[A CAL Implementation shall represent the xs:duration
> built-in datatype as a signed 64-bit integer.\]
>
> CERT CAL-016028 \[A CAL Implementation shall represent the xs:dateTime
> built-in datatype as a signed 64-bit integer.\]
>
> CERT CAL-016029 \[A CAL Implementation shall represent the xs:time
> built-in datatype as a signed 64-bit integer.\]

OMS is choosing to interpret these time types as 64-bit integers to
avoid frequent inefficient translations between string and numerical
representations of time. In order to support CAL Clients moving between
various CAL Implementations, there is a need to have a common definition
and precision of the numeric time value represented by the 64-bit
integer. Fields of type xs:duration should be interpreted as a number of
nanoseconds. Fields of type xs:time should be interpreted as number of
nanoseconds since 00:00z of the current day. Fields of type xs:dateTime
should be interpreted as nanoseconds since 00:00z of 1/1/1970 (POSIX
Epoch). How CAL Clients interpret the time integers is not enforced by
the CAL. The CAL itself has no responsibility for enforcing that the CAL
Client interpret and set the time values in a consistent manner.

### UUID Type

UUIDs are a fundamental structure in OMS. UUIDs are used to identify
objects, link messages together, and allow for Service and Subsystem
tasking among other uses. Having well formed UUIDs is critical to the
success of a Mission Package. The following requirements (CERTs) are
levied on CALs to promote consistent behavior and good practices among
CAL users.

> CERT CAL-016477 \[A CAL Implementation shall enforce UUID conformance
> to RFC 4122.\]

CALs are responsible for promoting good UUID usages. CALs should at a
minimum check the version and variant bits of UUIDs provided through the
CAL API for conformance to RFC 4122. CALs should also make efforts in
their configuration mechanism to promote responsible UUID usage.

> CERT CAL-016479 \[A CAL Implementation shall generate variant 1
> (Leach–Salz) UUIDs in accordance with the RFC 4122.\]
>
> CERT CAL-005181 \[A CAL Implementation shall generate UUIDs in
> accordance with the RFC 4122, UUID version 1, 3, and 4.\]

The CAL will generate UUIDs using RFC 4122. CALs may choose to implement
version 1 and/or 4. Version 1 is based on the MAC address of the
associated network interface and the current time. If a MAC address is
not assigned to the associated network interface, MAC addresses will be
purchased to ensure collisions do not occur. Version 4 is based on using
a pseudorandom number generator that is well seeded and has negligible
chance of collision. A cryptographically secure pseudorandom number
generator that is properly implemented and seeded is suitable for
version 4 generation. Version 3 UUIDs are provided when deterministic
time invariant (a priori) UUIDs are needed. Version 3 UUIDs are created
by taking the 128 bit MD5 hash of the concatenation of the namespace and
name, then setting the version and variant bits by overwriting them. The
namespace used in creating a version 3 UUID is itself a UUID. The name
should be unique in order to reduce the probability of collisions.

CAL Initialization
------------------

A CAL Client will initialize each CAL instance using a Service
Identifier (see Section 4.9, Service Identifier) the first time they
access each CAL instance through the CAL API. Subsequent calls to
retrieve a specific CAL instance from the CAL API will use the same
Service Identifier used to access it the first time. The Service
Identifiers used to initialize a CAL Implementation will be coordinated
between the OMS Service provider and the CAL provider.

Each CAL instance will be successfully initialized prior to the CAL
Client invoking any CAL operations (e.g., creating CAL Messages, CAL
Readers, or CAL Writers). A given CAL instance is to be initialized by
the CAL Client that obtained access to that CAL instance. Each CAL
instance should be accessed by one and only one CAL Client.

> CERT CAL-005201 \[A CAL Implementation shall have a mechanism for the
> CAL Client to obtain a fully initialized instance of the CAL
> associated with a Service Identifier.\]

A fully initialized CAL instance is ready to provide CAL Messages, CAL
Readers, and CAL Writers to the CAL Client. The Service Identifier is a
string name that is interpreted within the context of an OMS Platform.
See Section 4.10, Service Identifier, for more information on the
Service Identifier.

> CERT CAL-005202 \[A CAL Implementation shall associate a single CAL
> instance with each unique combination of Service Identifier and ASB
> Identifier.\]

The definition of an instance of a CAL is clarified in Section 4.6, CAL
Instance.

Instances of different CAL Implementations will not return the same
reference given the same service identifier.

> CERT CAL-005203 \[A CAL Implementation shall have a mechanism for
> retrieving the UUIDs that identify the System, Service, Subsystem,
> Components, and Capabilities associated with the initializing
> Service.\]
>
> CERT CAL-005204 \[A CAL Implementation shall report an error to the
> CAL Client in the event the initialization of the CAL instance
> fails.\]

Topics
------

In a topic-based publish/subscribe system; messages are published to
“topics”. A topic is a distribution mechanism for publishing messages
that are to be delivered to one or more subscribers. A topic is
associated with one and only one message type. Publishers send instances
of a message on the topic and any subscribers on the topic receive those
message instances. Note that schema extensions to an existing message
type create a new unique message type. Exchanging extended messages over
a topic associated with the un-extended base message type results in
undefined behavior.

CAL Clients can name their topics as desired. A Client Topic, as
described in Section 4.11, Topics and Connections, is a logical
identifier for a connection between CAL Reader(s) and CAL Writer(s).
Each Client Topic name, message type, and topic specific required
Quality of Service (QoS) settings tuple is exposed in the CAL Clients’
Service Contracts. The CAL Implementation defines and names topics for
internal use. These internal CAL Topics will be mapped to the applicable
Client Topics. QoS Settings are applied to each topic. Only one group of
QoS settings can be applied to a topic within a single CAL Client. For
example, two readers of a given topic within a CAL Client will apply
compatible QoS settings for the topic.

> CERT CAL-005208 \[A CAL Implementation shall associate a topic with
> one and only one CAL Message type.\]
>
> CERT CAL-005209 \[A CAL Implementation shall map Client Topics to the
> applicable CAL Topics.\]
>
> CERT CAL-005210 \[A CAL Implementation shall support the configuration
> of independent Quality of Service settings for each Client Topic.\]

Note: In this case, Client Topic includes the Topic name plus its QoS
settings. If a single Client (which could be multiple services) needs
different QoS settings, then it will need to have multiple Client Topics
– one per set of QoS settings. QoS settings are defined in the CAL QoS
Settings section.

CAL Messages
------------

CAL Messages are in the CAL Implementation that satisfy the language
specific message API described in OMSC-SPC-008, C++ CAL Interface
Generation Specification, for C++ implementations and OMSC-SPC-007, Java
CAL Interface Generation Specification, for Java implementations. All
interactions between CAL Clients and OMS Messages take place via CAL
Message containers (also referred to simply as CAL Messages). OMS
specifies standard C++ and Java interfaces for CAL Messages in the
language-specific CAL Interface Generation Specifications. The CAL
interface to the CAL Message containers defines methods for getting and
setting message data member values.

Only CAL Message types may be associated with a topic and published by
the CAL Client. CAL Sub-message types cannot be sent or received outside
of the context of an encapsulating CAL Message.

### CAL Message Contents

CAL Messages contain one or more data members. Data members may be
categorized as either optional or required. A data member may be a
primitive or an encapsulated type. Primitive types are the most basic
data types available in a specific language and serve as the building
blocks for more complex encapsulated types.

Primitive types cannot be decomposed any further. In the context of OMS,
primitive types are defined in the W3C XML Schema 1.0 specification and
include built-in XML types like integers, doubles, Booleans, and
strings. See Section 5.2, CAL Interface**,** for OMS-specific
interpretations of the simple types. Encapsulated types are constructed
using primitive types and other encapsulated types. Encapsulated types
also include special data constructs like choices, lists, and
enumerations.

A data member of a CAL Message that is a complex type is known as a CAL
Sub-message type. Abstract CAL Message types may not be instantiated as
CAL Message types or CAL Sub-message types. An Abstract CAL Message type
is an OMS Message type defined in the OMS Message Schema with an
attribute named “abstract” set to a value of “true”. A non-abstract
extension of an abstract type may be instantiated and then represent a
parent abstract type.

#### Optional Fields

An optional field is a data member that is optionally populated.
Optional fields are considered to be disabled if the field has not been
populated. Optional fields are considered to be enabled when populated.

#### Required Fields

A required field is a data member that must be populated.

#### Bounded Lists

A bounded list is a data construct that is a list of elements whose size
can be set. The elements may be either primitive or encapsulated types.
All elements within the bounded list must be of the same base type,
including types derived from the base type. The reason being that many
languages could have difficulty maintaining a list with elements of
different fundamental size (e.g., a list containing 32-bit integers and
64-bit doubles) or might have difficulty fully copying the contents of
an element with different type specializations (a term known as object
slicing). A bounded list is considered to be empty when it contains no
elements.

#### Choices

A choice is a data construct that may have one of several data
representations. A choice field is considered to be uninitialized when
no type has been selected for the current data representation.

#### Sequences

A sequence is a data construct consisting of one or more primitive or
complex types. Each contained type may be categorized as either optional
or required. Sequences are also known as structures.

#### Enumerations

An Enumeration is a data construct consisting of a set of enumerated
items. Data members that are defined as enumerations have a value
corresponding to one of the enumerated values from the associated
enumeration definition.

#### Validation

CAL Implementations are not responsible for ensuring the validity of CAL
Messages either at object creation time or at publication time.

### CAL Message Construction

CAL Clients use the mechanisms defined by the CAL API for creating
instances of CAL Messages/Sub-messages and populating them. A CAL
Implementation is responsible for realizing those mechanism defined by
the CAL API. These mechanisms include: the selection between choices;
the population of list elements; and the population of data members. As
described previously, creation and destruction of CAL Messages and
Sub-messages is generally language specific. C++ uses CAL Factories,
while Java uses the “new” operation to create CAL Messages and CAL
Sub-messages. A CAL Sub-message is the lower level complexType and
simpleTypes that are defined and used to build up the definition of CAL
Messages. Most of the other constructs for populating a CAL
Message/Sub-message are fairly language agnostic. The CAL API defines
the mechanism for selecting/activating a specific data member from a
choice of data types and likewise there are means defined for enabling
and disabling optional data members.

> CERT CAL-016033 \[A CAL Implementation shall support the creation of
> non-abstract CAL Messages and Sub-messages.\]
>
> CERT CAL-016035 \[A CAL Implementation shall prevent the creation of
> abstract CAL Messages and Sub-messages.\]

#### Optional Fields

Optional fields are considered to be disabled if the field has not been
populated. Optional fields are considered to be enabled when populated.
When CAL Clients create a CAL Message or Sub-message, all contained
optional fields will be placed in a “disabled” state. No guarantee is
made of pre-allocation of memory or other resources for optional fields.
Developers should check the state of an optional field prior to use to
ensure that it is enabled.

> CERT CAL-005254 \[A CAL Implementation shall create optional fields in
> a disabled state.\]

#### Required Fields

When CAL Clients create a CAL Message or Sub-message, the memory
management approach required of the CAL Implementation is language
specific. Refer to OMSC-SPC-008, C++ CAL Interface Generation
Specification, for C++ implementations and OMSC-SPC-007, Java CAL
Interface Generation Specification, for Java implementations for
additional requirements and common behaviors in each language.

#### Bounded Lists

When CAL Clients create a CAL Message or Sub-message, all contained
lists are created in an empty state. No elements exist in the list. No
guarantee is made of pre-allocation of memory or other resources for
elements within a bounded list.

> CERT CAL-005264 \[CAL Implementation shall create bounded lists in an
> empty state.\]

#### Choices

When CAL Clients create a CAL Message or Sub-message, all choices
contained therein will be created in an uninitialized state. No
guarantee is made of pre-allocation of memory or other resources for
choice fields.

> CERT CAL-005267 \[A CAL Implementation shall create choice fields in
> an uninitialized state.\]

#### Enumeration

When CAL Clients create a CAL Message or Sub-message, all enumerations
contained therein will be created in an uninitialized state.

> CERT CAL-016038 \[A CAL Implementation shall create enumerations in an
> uninitialized state.\]

### Message Destruction

The memory management approach associated with the destruction of CAL
Messages and Sub-messages is language specific. Refer to OMSC-SPC-008,
C++ CAL Interface Generation Specification, for C++ implementations and
OMSC-SPC-007, Java CAL Interface Generation Specification, for Java
implementations for additional requirements and common behaviors in each
language.

> CERT CAL-005275 \[A CAL Implementation shall have a mechanism for
> destroying CAL Messages and Sub-messages.\]

### Accessing Message Values

CAL Messages provide a mechanism for accessing field values. The
specific mechanism varies between programming languages. Refer to
OMSC-SPC-008, C++ CAL Interface Generation Specification, for C++
implementations and OMSC-SPC-007, Java CAL Interface Generation
Specification, for Java implementations.

#### Optional Fields

During the creation of CAL Messages, optional fields are created in a
disabled state. No initial value for the field is set. Checking a CAL
Message for a disabled optional field’s state will return a value of
“false”. Optional fields are enabled once a CAL Client sets the optional
value. Disabling an optional field is a language-specific operation. See
the OMSC-SPC-008, C++ CAL Interface Generation Specification, for C++
implementations and OMSC-SPC-007, Java CAL Interface Generation
Specification, for Java implementations referred to in Section 3,
References, for details and requirements. Checking a CAL Message for an
enabled optional field’s state will return a value of “true”. The
standard CAL interface provides a means for Clients to retrieve and set
the values of optional fields.

> CERT CAL-005290 \[A CAL Implementation shall have a mechanism to
> enable or disable optional fields.\]
>
> CERT CAL-005293 \[A CAL Implementation shall have a mechanism to
> determine the enabled or disabled state of an optional field.\]
>
> CERT CAL-005294 \[A CAL Implementation shall indicate to the CAL
> Client that a field is disabled when a disabled optional field is
> accessed.\]
>
> CERT CAL-005296 \[A CAL Implementation shall provide the value of the
> field when the value of an enabled optional field is accessed.\]

#### Required Fields

The CAL Client actions on required fields are language specific. See the
OMSC-SPC-008, C++ CAL Interface Generation Specification, for C++
implementations and OMSC-SPC-007, Java CAL Interface Generation
Specification, for Java implementations referred to in Section 3,
References, for details and requirements.

#### Bounded Lists

CAL Clients can retrieve a reference to a bounded list attribute. The
language specific list interface must then be used to access individual
elements within the list. All CAL Implementations support a basic set of
operations for lists. This includes operations providing the following
capabilities:

-   Retrieve size or current number of elements in list.

-   Retrieve maximum bound of list as defined in OMS Message Schema.

-   Retrieve minimum bound of list as defined in OMS Message Schema.

-   Reserve resources for a specified number of elements, thus modifying
    current capacity of the list.

Check whether or not list is empty.

-   Add an element to end of the list.

-   Remove an element from end of list.

-   Clear or remove all elements from list.

-   Obtain reference to an element at a specified position within the
    list.

CAL Clients can use references to manipulate the value of the CAL
instance’s internal representation of the sub-message via the defined
CAL interface. There are language-specific additions to this list that
can be found in the OMSC-SPC-008, C++ CAL Interface Generation
Specification, for C++ implementations and OMSC-SPC-007, Java CAL
Interface Generation Specification, for Java implementations. Memory
management associated with the bounded list is also language-specific
and is not addressed at this level.

#### Choices

The CAL Client actions on choices are language-specific. See the
OMSC-SPC-008, C++ CAL Interface Generation Specification, for C++
implementations and OMSC-SPC-007, Java CAL Interface Generation
Specification, for Java implementations referred to in Section 3,
References, for details and requirements.

#### Sequences

The CAL Client actions on sequences are language specific. See
OMSC-SPC-008, C++ CAL Interface Generation Specification, for C++
implementations and OMSC-SPC-007, Java CAL Interface Generation
Specification, for Java implementations, for details and requirements.

Writers
-------

CAL Writers are entities used by CAL Clients to send CAL Messages. Each
writer instance is associated with one and only one CAL Client Topic.
CAL Writers will meet or exceed the quality of service settings
specified for the associated topic. CAL Writers can only be associated
with Client Topics. CAL Writers will only send CAL Messages.

The CAL Client may only obtain an instance of a CAL Writer from the CAL.
The CAL Client is responsible for closing the CAL Writer instance using
the standard CAL interface for the writer.

The CAL Implementation for a writer provides an operation for sending
CAL Messages. This write operation takes a reference to the CAL Message
to be sent. CAL Clients are free to reuse the referenced CAL Message
once the write operation returns.

Note that when using certain reliable QoS settings on a Client Topic,
the invocation of the write operation may return before all subscribers
on the network have received the message. If the History Depth QoS is
set relatively small, and additional write invocations take place,
messages may be dropped before they can be delivered to the network
layer without notification to the CAL Client.

> CERT CAL-005364 \[A CAL Implementation shall have a mechanism to
> create Writers associated with a Client Topic.\]
>
> CERT CAL-005368 \[A CAL Writer Instance shall be associated with one
> and only one Client Topic.\]
>
> CERT CAL-005369 \[A CAL Writer Instance shall report an error upon
> invocation of the write operation when the associated Client Topic is
> unavailable.\]

There are a number of reasons why a CAL Client Topic may not be
available. For instance: there may not be a legitimate mapping from
Client Topic to a CAL Implementation’s internal CAL Topic (see Section
4.11, Topics and Connections) or the Client Topic may not be traceable
to an entry in the CAL Implementation’s network configuration (see
Section 4.7, Network Configuration).

> CERT CAL-016043 \[A CAL Writer Instance shall report an error upon
> invocation of the write operation when the required resources to
> complete the operation are not available.\]

Readers
-------

CAL Readers are entities used by CAL Clients to receive incoming CAL
Messages. Each reader instance is associated with one and only one CAL
Client Topic. CAL Readers will meet or exceed the Quality of Service
(QoS) settings specified for the associated topic. CAL Readers can only
be associated with Client Topics. Note that multiple CAL Readers can be
created in association with a single Client Topic. Each CAL Reader will
provide unique CAL Message references to a CAL Client, even when the CAL
Readers are associated with the same Client Topic. Each CAL Reader will
enforce the same QoS settings associated with the Client Topic, but each
CAL Reader will perform their own enforcement of the QoS settings. CAL
Readers will only receive CAL Messages.

The CAL Client may only obtain an instance of a CAL Reader via the CAL.
The CAL Client is responsible for closing the CAL Reader instance using
the language-specific CAL interface for the reader.

The CAL Implementation for a reader provides two styles of interfaces
for receiving CAL Messages. The first style is a callback interface. CAL
Clients register a callback routine that is invoked upon receipt of an
instance of the specified CAL Message type. The second style is a
polling interface. CAL Clients poll or query the CAL instance for
received instances of the specified CAL Message type.

> CERT CAL-005374 \[A CAL Implementation shall have a mechanism to
> create Readers associated with a Client Topic.\]
>
> CERT CAL-005378 \[A CAL Reader Instance shall be associated with one
> and only one Client Topic.\]
>
> CERT CAL-005379 \[A CAL Reader Implementation shall provide a callback
> interface for receiving CAL Messages.\]
>
> CERT CAL-005380 \[A CAL Reader Implementation shall provide a polling
> interface for receiving CAL Messages.\]

### Callback Interface

The CAL Reader Implementation provides an operation for a CAL Client to
register instances of the listener. A CAL Client may register more than
one listener. Once registered, each listener’s message handler operation
will be invoked one time for each received instance of the associated
CAL Message type in accordance with the Quality of Service settings
associated with the topic. The invocation of the listener’s message
handler operation will be from a unit of execution (i.e.,
thread/process/task) controlled and owned by the CAL Implementation
Instance. CAL Clients will assume that the registered listeners could be
called either in sequence from a single reader thread or in parallel
from independent threads. This is important when determining the
throughput of the reader and race-conditions between registered
callbacks. The CAL Reader Implementation provides the same CAL Message
reference to each registered listener’s message handler operation. The
CAL Instance guarantees that the CAL Message reference is good for the
CAL Client to use for the duration of the message handler operation.

The CAL Reader Implementation provides an operation for a CAL Client to
unregister an instance of the listener class. Once unregistered, the
listener’s message handler operation will no longer be invoked for
incoming CAL Messages.

> CERT CAL-005391\[A CAL Reader Implementation shall allow a CAL Client
> to register zero or more listener instances for receiving incoming CAL
> Messages.\]
>
> CERT CAL-005392 \[A CAL Reader Implementation shall provide a CAL
> Client with a single, shared CAL Message reference by invoking the
> message handler operation of each registered listener instance one
> time for each received CAL Message instance.\]
>
> CERT CAL-005394 \[A CAL Reader Implementation shall establish the
> topic connection when the Reader is created.\]
>
> CERT CAL-016044 \[A CAL Reader Implementation shall begin buffering
> received CAL Messages based on the topic QoS Settings when the topic
> connection is established.\]
>
> CERT CAL-016045 \[A CAL Reader Implementation shall remove the CAL
> Message instance from the receive buffer once the message handler
> operation of each registered listener instance has been completed.\]
>
> CERT CAL-016046 \[A CAL Implementation shall make available without
> modification the CAL Message accessed by the registered listener for
> the duration of an invoked registered listeners’ message handler
> operation.\]
>
> CERT CAL-005396 \[A CAL Implementation shall provide the ability to
> unregister a listener instance.\]

### Polling Interface

The polling interface provides the ability for CAL Clients to retrieve
CAL Messages. The CAL Reader Implementation provides operations for a
CAL Client to read received CAL Messages. These operations execute
within the unit of execution used by the CAL Client to invoke the
operation.

The read operation accepts a timeout value. The timeout is the duration
that the read operation will block until a CAL Message is available. A
CAL Reader Implementation is expected to buffer received CAL Messages in
accordance with Quality of Service Settings associated with the topic.
As each CAL Message is processed, it will be removed from the buffer.

The readNoWait operation does not accept a timeout value. The readNoWait
operation will not block or wait until a CAL Message is available.

> CERT CAL-016049 \[A CAL Reader Instance shall block within the read
> operation until the specified timeout value has expired, a new CAL
> Message arrives, or the Reader Instance is closed.\]
>
> CERT CAL-016050 \[A CAL Reader Implementation shall report an error
> when the read operation is invoked on a Reader Instance with one or
> more registered listeners.\]

A CAL Client is not allowed to use <span class="underline">both</span>
the CAL Reader callback and polling mechanisms at the same time as this
can create undefined behavior.

> CERT CAL-016052 \[A CAL Reader Implementation shall remove the CAL
> Message instance from the receive buffer when the CAL Message is
> provided to the CAL Client.\]

A CAL Message will only be provided to a CAL Client through the
invocation of the CAL Reader’s read or readNoWait methods on the first
thread/task that arrives. If a second read invocation occurs before the
first has completed, the second read will not access the CAL Message
provided to the first CAL Client thread/task.

CAL QoS Settings
----------------

The CAL Implementation is required to provide a series of Quality of
Service settings. These settings are configurable but cannot be modified
by the CAL Client during execution. The CAL Implementer is responsible
for ensuring the QoS settings are available, and creating the mechanism
for configuration.

### Time Based Filter

Time Based Filtering can be used by the CAL Client reader instances to
indicate a desire to see a select set of values of each instance
published under the Client Topic based on a periodic rate. Specifically,
the reader can choose to see one change in a nominal minimum separation
period. It is reasonable to expect some variability (jitter) in the
actual separation period obtained during operation, so the period is
only approximate. This filter applies to each reader instance
separately. This provides for the case where data can be generated at a
much faster rate than the application using the reader would want to
accept updates. Additional guidance will be provided in this section in
a future release.

> CERT CAL-005431 \[A CAL Reader Instance shall provide Time Based
> Filter Quality of Service such that the CAL Reader drops CAL Messages
> received on a Client Topic within a specified time period since the
> last CAL Message was accepted on the Client Topic.\]

### Reliability

Reliability can be requested of CAL Readers and CAL Writers by the CAL
Client to indicate one of two levels of reliability: Best Effort and
Reliable. When a CAL Client chooses a Reliable setting, the writer
instance may block if there is a potential that data may be lost. When
the Best Effort setting is chosen, the writer instance will not
retransmit missing or dropped data. Additional guidance will be provided
in this section in a future release.

The definitions of reliability in Table 5.8-1, CAL Reliability
Definitions, are from the CAL perspective and captured here to clarify
the text that follows.

<span id="_Toc219292485" class="anchor"></span>Table 5.8-1 CAL
Reliability Definitions

<table>
<thead>
<tr class="header">
<th>Term</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Reliable</td>
<td>The CAL will try to deliver the message after failure, giving best effort. This means the reliable delivery may be built upon best effort and could introduce latency and throughput complications.</td>
</tr>
<tr class="even">
<td>Reliability</td>
<td>The CAL will make the effort to ensure that any message sent by the writer will be received by all the subscribers until the expiration time has expired.</td>
</tr>
<tr class="odd">
<td>Best Effort</td>
<td>The CAL does not guarantee message delivery and will not retransmit missing or dropped data.</td>
</tr>
<tr class="even">
<td>Ordering</td>
<td>The CAL will ensure delivery and ordering between each pair of CAL Readers and CAL Writers on a given Client Topic. When a CAL Reader does not receive a message, the CAL Writer of the message will resend the message and the CAL Reader will not delivery any newer messages to the CAL Client until the message is successfully received, or the expiration time has expired.</td>
</tr>
<tr class="odd">
<td>Connection</td>
<td>See Section 4.11, Topics and Connections.</td>
</tr>
</tbody>
</table>

> CERT CAL-005434 \[A CAL Implementation shall provide the Reliability
> Quality of Service such that the CAL Implementation resends CAL
> Messages on connections to CAL Readers that have not received the CAL
> Message while the CAL Message remains available for retransmit.\]

The availability of a message for retransmit is dictated by the
Expiration QoS setting as well as the History Depth QoS Setting in
combination with the rate at which the CAL Client invokes the write
operation. The responsibility for performing this requirement is
specified deliberately as the “CAL Implementation” but may be realized
by the CAL Writer or some other delegate.

> CERT CAL-016076 \[A CAL Implementation shall provide the Reliability
> Quality of Service such that the CAL Implementation preserves the
> order of CAL Messages on a connection.\]

The responsibility for performing this requirement is specified
deliberately as the “CAL Implementation” but may be realized by the CAL
Writer or some other delegate.

### Expiration

Expiration can be set on a Client Topic to avoid publishing or receiving
“expired” messages. The expiration time of the message is computed by
adding the “shelf life” identified in the setting for the Client Topic
to the timestamp when the message was placed in the Message Buffer.
Expired CAL Messages will be removed from the CAL Reader’s buffer.

> CERT CAL-005437 \[A CAL Implementation shall provide the Expiration
> Quality of Service such that the CAL Implementation removes expired
> CAL Messages from the CAL Reader’s buffer.\]

### Message Buffer

The Message Buffer setting on a Client Topic regulates the maximum
number of messages the CAL Implementation will maintain and deliver. The
minimum Message Buffer size is 1. A Message Buffer size of 1 indicates
that only the most recent message received is provided. A higher Message
Buffer level requires the CAL Implementation to store the specified
number of unread messages until they have been provided to the CAL
Client. A message is considered to be unread until the message handler
operations of all registered listeners have completed or the message
read operation has completed.

> CERT CAL-015746 \[A CAL Implementation shall provide the Message
> Buffer Quality of Service such that the CAL Implementation will buffer
> a configurable, maximum number of CAL Messages that the CAL
> Implementation has received but not yet delivered to the CAL Client.\]
>
> CERT CAL-005444 \[A CAL Implementation shall provide the Message
> Buffer Quality of Service such that the CAL Implementation will buffer
> a configurable, maximum number of CAL Messages that the CAL
> Implementation has received from the CAL Client but not yet delivered
> to the network connection.\]
>
> CERT CAL-005445 \[A CAL Implementation shall remove the oldest message
> in the CAL Writer’s buffer of CAL Messages when the number of CAL
> Messages exceeds the value configured by the Message Buffer Quality of
> Service.\]
>
> CERT CAL-016079 \[A CAL Implementation shall remove the oldest message
> in the CAL Reader’s buffer of CAL Messages when number of CAL Messages
> exceeds the value configured by the Message Buffer Quality of
> Service.\]

In the context of CERTs CAL-005445 and CAL-016079 the term “oldest” is
intended to be measured by the time that the message was placed in the
Message Buffer.

Abstract Service Bus Connection Status
--------------------------------------

Each CAL instance provides the ability to query the status of the
Abstract Service Bus (ASB) connection.

The CAL Connection Status Implementation for the connection status
provides two styles of interfaces for determining the status. The first
style is a callback interface. CAL Clients register a callback routine
that is invoked when the connection status changes. The second style is
a polling interface. CAL Clients poll or query the CAL Instance for the
current connection status.

The CAL Connection Status Implementation provides an operation for a CAL
Client to register instances of the listener. A CAL Client may register
more than one listener. Once registered, each listener’s status handler
operation will immediately be invoked with the current status and then
in the future each time the connection status changes. The invocation of
the listener’s status handler operation will be from a unit of execution
(i.e., thread/process/task) controlled and owned by the CAL
Implementation Instance. CAL Clients will assume that the registered
listeners could be called either in sequence from a single thread or in
parallel from independent threads.

The CAL Connection Status Implementation provides an operation for a CAL
Client to unregister an instance of the listener class. Once
unregistered, the listener’s status handler operation will no longer be
invoked for changes to the connection status.

The CAL Connection Status Implementation provides operations for a CAL
Client to query the current connection status. These operations execute
within the unit of execution used by the CAL Client to invoke the
operation.

The following applies to the Abstract Service Bus Connection Status:

-   The CAL status interface poll and callback will provide the
    enumeration of the current state and a CAL implementer-defined
    string

-   Upon registering as a state listener, the state change message will
    be called instantly with the current state

-   All other API calls should work as normal regardless of connection
    state

> CERT CAL-016366 \[Upon successful completion of a request to register
> as an Abstract Service Bus Connection Status listener, a CAL
> Implementation shall call the registered class’ API notification
> method with the current state of the ASB connection.\]

The definitions of the states are provided in Table 5.9-1, CAL Abstract
Service Bus Connection Status State Definition.

<span id="_Toc219292486" class="anchor"></span>Table 5.9-1 CAL Abstract
Service Bus Connection Status State Definition

<table>
<thead>
<tr class="header">
<th>State</th>
<th>Definition</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>INITIALIZING*</td>
<td>CAL is starting up, where initialization has begun but is not complete (e.g., still loading configuration files). Read and write methods will return an error. Blocking reads will behave as normal.</td>
</tr>
<tr class="even">
<td>NORMAL</td>
<td>CAL is functioning normally, where all functions can be used. All QoS settings, as applicable, are being met. Read and write methods will behave as normal. Blocking reads will behave as normal.</td>
</tr>
<tr class="odd">
<td>DEGRADED*</td>
<td>CAL is not functioning normally, where functions can be used but there may be limitations. Not all QoS settings are being satisfied. The CAL can send and receive but QoS settings are not being satisfied. Read and write methods will behave as normal. Blocking reads will behave as normal.</td>
</tr>
<tr class="even">
<td>INOPERABLE*</td>
<td>CAL is unusable but may return to an operational state in the future. CAL is unable to send or receive messages and is attempting to recover. Read and write methods will return an error. Blocking reads will behave as normal.</td>
</tr>
<tr class="odd">
<td>FAILED</td>
<td>CAL is unusable and return to an operational state is not possible. Identical to Inoperable state but recovery is not possible. Read and write methods will return an error. Blocking reads will release thread, returning a UCI exception.</td>
</tr>
</tbody>
</table>

where \* indicates an optional state

The allowed states and transitions for the Abstract Service Bus
Connection Status are illustrated in Figure 5.9-1, CAL Abstract Service
Bus Connection Status State Diagram.

<img src="media/image5.png" style="width:6.5in;height:4.70833in" />

<span id="_Toc219292481" class="anchor"></span>Figure 5.9-1 CAL Abstract
Service Bus Connection Status State Diagram

A summary of the state transitions that are allowed and not allowed for
the Abstract Service Bus Connection status is provided in Figure 5.9-2,
CAL Abstract Service Bus Connection Status State Transitions. Only
NORMAL and FAILED states are guaranteed to be provided by the Abstract
Service Bus Connection Status API.

<img src="media/image6.png" style="width:5.57292in;height:6.28125in" />

<span id="_Toc219292482" class="anchor"></span>Figure 5.9-2 CAL Abstract
Service Bus Connection Status State Transitions

A summary of the state definitions and behaviors of CAL Readers and
Writers identified in Table 5.9-1 are shown in Table 5.9-2, CAL Abstract
Service Bus Connection Status State Behaviors. The top rows indicate
what a new call would return in an existing state. The bottom rows
indicate what would happen to existing listeners and blocked reads of
CAL Readers when transitioning into a new state.

<span id="_Toc219292487" class="anchor"></span>Table 5.9-2 CAL Abstract
Service Bus Connection Status State Behaviors

<table>
<thead>
<tr class="header">
<th></th>
<th>Initializing</th>
<th>Normal</th>
<th>Degraded</th>
<th>Inoperable</th>
<th>Failed</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>New call in current state</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>addListener()</td>
<td>OK</td>
<td>OK</td>
<td>OK</td>
<td>OK</td>
<td>E</td>
</tr>
<tr class="odd">
<td>read() (blocking)</td>
<td>OK</td>
<td>OK</td>
<td>OK</td>
<td>OK</td>
<td>E</td>
</tr>
<tr class="even">
<td>readNoWait()</td>
<td>E</td>
<td>OK</td>
<td>OK</td>
<td>E</td>
<td>E</td>
</tr>
<tr class="odd">
<td>write()</td>
<td>E</td>
<td>OK</td>
<td>OK</td>
<td>E</td>
<td>E</td>
</tr>
<tr class="even">
<td>Transition into new state</td>
<td></td>
<td></td>
<td></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>existing listener</td>
<td>NC</td>
<td>NC</td>
<td>NC</td>
<td>NC</td>
<td>NO/OP</td>
</tr>
<tr class="even">
<td>existing blocking read</td>
<td>NC</td>
<td>NC</td>
<td>NC</td>
<td>NC</td>
<td>E</td>
</tr>
</tbody>
</table>

where

OK = Normal processing

E = Exception thrown

NC = No Change

NO/OP = Listener will never be called back

CAL CERT Verification
=====================

Verification is normally performed by inspection, analysis,
demonstration and/or test. These CERTs are typically verified either by
inspection of specific documents, analysis of test results, or
demonstration of specific OMS Services or programs that prove that
something has been implemented properly.

One of the goals of proving OMS compliance is to leverage existing test
plan artifacts and not to generate duplicate testing.

Acronyms and Symbols
====================

For the list of OMS acronyms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.

Glossary
========

For the glossary of terms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.
