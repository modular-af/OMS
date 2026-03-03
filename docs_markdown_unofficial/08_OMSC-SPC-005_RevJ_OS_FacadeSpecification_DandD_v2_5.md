Open Mission Systems (OMS)

Definition And Documentation (D&D)

Operating System Façade Specification

<img src="images/08_OMSC-SPC-005_RevJ_OS_FacadeSpecification_DandD_v2_5.docx/media/image1.jpeg" style="width:2.78125in;height:1.73958in" />

22 january 2026

Prepared By:

Open Architecture Collaborative Working Group (OACWG)

This page is intentionally left blank.

Abstract

Open Mission Systems (OMS) is a non-proprietary open architecture for
integrating subsystems and services into mission packages.

This Operating System (OS) Façade Specification lists the set of all
Portable Operating System Interface (POSIX) calls. It identifies those
calls which are allowed and those calls that are restricted with comment
to alternative options.

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
<td>J</td>
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

[4 OMS Operating System (OS) Façade 4](#oms-operating-system-os-façade)

[4.1 RESTRICTIONS 4](#restrictions)

[4.1.1 X/Open System Interface 4](#xopen-system-interface)

[4.1.2 Multi-Purpose-Realtime-System Profile (PSE54)
4](#multi-purpose-realtime-system-profile-pse54)

[5 Acronyms and Symbols 75](#acronyms-and-symbols)

[6 Glossary 76](#glossary)

This page is intentionally left blank.

List of Tables

[Table 3.1-1 Reference Standards 3](#_Toc219293180)

[Table 3.2-1 OMS D&D Documents 3](#_Toc219293181)

[Table 4.0-1 OS Façade Mapping to POSIX 5](#_Toc219293182)

This page is intentionally left blank.

Introduction
============

OMS Services are primarily implemented using Java or C++ as the
programming language. A C++ implementation results in a binary image
compatible with either the native machine hardware or the virtual
machine hardware the Service is hosted upon, depending on the
implementation. A Java implementation results in a pseudo-binary image
compatible with the standard Java Virtual Machine (JVM) which is an
intrinsic part of any Java run-time configuration. Java also provides
the Java Native Interface (JNI) services, which allow a Java application
to interface with the host operating system (OS) and/or shared (linked
at run-time, not at build-time) library functions hosted by the OS.

OMS Services may, if available, use a Language Agnostic (LA) Critical
Abstraction Layer (CAL). The LA CAL enables the use of other programming
languages and provides a non-proprietary interface for OMS Services to
communicate with the OMS Platform.

For a Service intended to be hosted by an OCE, additional constraints
are desirable to provide the desired portability. For C++, additional
standardization is recommended to ensure there are no incompatible
dependencies (e.g., a library call that only one version of operating
system supports).

A “façade” is the term used in computer science to indicate a software
architecture design pattern that presents a standard interface for an
underlying software resource, typically to mask or encapsulate a more
complex structure. A façade can simplify and/or restrict access to parts
of the underlying resource. A primary use of the façade pattern is to
provide a standard interface (aka “wrapper”) to one or more similar but
incompatible resources (e.g., OS services).

IEEE-1003, the Portable Operating System Interface (POSIX), was selected
as the basis for standardizing OMS C++ Service implementations. POSIX
provides a standard Application Programmer’s Interface (API) for any
underlying operating system which supports it (e.g., Unix, Linux,
Windows™, etc.).

POSIX is itself a type of façade. However, POSIX is based on library
calls originally provided in the Unix operating system, and some of the
available functions have issues that make their use problematic for
interoperability including the following:

-   Cybersecurity vulnerabilities (e.g., unbounded/unchecked buffer
    allocation)

-   Thread-safety (i.e., function was originally designed for
    single-threaded applications)

-   Historical implementations that cause incompatibilities

-   Deprecated functions

-   Library calls incompatible with the Future Airborne Capability
    Environment (FACE™) Technical Standard

-   Functions that provide services already supported by other parts of
    OMS (e.g., Data Transfer)

Scope
=====

The following sections define the OMS OS Façade.

References
==========

Related Standards
-----------------

The documents listed in Table 3.1-1, Reference Standards, are cited
throughout this document. For dated references, only the edition cited
applies. For undated references, the latest edition of the referenced
document (including any amendments or corrigenda) applies.

<span id="_Toc219293180" class="anchor"></span>Table 3.1-1 Reference
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
<td></td>
<td>Future Airborne Capability Environment (FACE™) Technical Standard</td>
<td>Version 1.0</td>
<td>26 January 2012</td>
</tr>
<tr class="even">
<td>IEEE Std 1003.1-2008</td>
<td>IEEE Standard for Information Technology – Portable Operating System Interface (POSIX)</td>
<td></td>
<td>01 December 2008</td>
</tr>
<tr class="odd">
<td>IEEE Std 1003.1-2013</td>
<td>IEEE Standard for Information Technology – Portable Operating System Interface (POSIX)</td>
<td></td>
<td>19 April 2013</td>
</tr>
<tr class="even">
<td>IEEE Std 1003.13TM-2003</td>
<td><p>IEEE Standard for Information Technology - Standardized Application Environment Profile (AEP) - POSIX Realtime and Embedded Application Support</p>
<p>PSE54 Multipurpose Realtime 1003.13TM-2003 System Product Standard</p></td>
<td></td>
<td>10 December 2003</td>
</tr>
</tbody>
</table>

OMS D&D Documents 
-----------------

The documents listed in Table 3.2-1, OMS D&D Documents, are the
documents that assist in the understanding and implementation of OMS.

<span id="_Toc219293181" class="anchor"></span>Table 3.2-1 OMS D&D
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

OMS Operating System (OS) Façade
================================

Table 4.0-1, OS Façade Mapping to POSIX, defines the subset of OS calls
to support Service portability across different Open Computing
Environment (OCE) OS and Hardware (HW) hardware implementations. It is
based on POSIX calls derived from IEEE Std. (POSIX) 1003.1-2008 and IEEE
Std. (POSIX) 1003.1-2013 with select calls restricted from use
consistent with the FACE™ OS segment general purpose profile.

RESTRICTIONS
------------

### X/Open System Interface

X/Open System Interface (XSI) option is the core application programming
interface for C and sh (command shell) programming for systems
conforming to the Single UNIX specification. This is a superset of the
mandatory requirements for conformance to POSIX.1-2008. The OMS Façade
is concerned with POSIX.1-2013 compliance as its base, thus a superset
of the POSIX standard would not be included.

### Multi-Purpose-Realtime-System Profile (PSE54)

PSE54 is defined by IEEE Std 1003.13-2003. Its interface is a subset of
the POSIX library functions. The included functions were chosen based on
their portability between compliant operating systems.

<span id="_Toc219293182" class="anchor"></span>Table 4.0-1 OS Façade
Mapping to POSIX

<table>
<thead>
<tr class="header">
<th>IEEE Std 1003.1 API (POSIX)</th>
<th>OS Façade Allowed</th>
<th>OS Façade Restricted</th>
<th>Comments</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>_exit()</td>
<td></td>
<td>X</td>
<td>The _exit() function does not call functions registered with atexit() nor any registered signal handlers; the side-effects of calling this function is implementation-defined. Simply change _exit() to exit().</td>
</tr>
<tr class="even">
<td>_Exit()</td>
<td></td>
<td>X</td>
<td>The _Exit() function does not call functions registered with atexit() nor any registered signal handlers; the side-effects of calling this function is implementation-defined. Developers should call exit() instead which does not suffer from these issues. Simply change _Exit() to exit().</td>
</tr>
<tr class="odd">
<td>_longjmp()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Developers should use longjmp() instead. Simply change _longjmp()to longjmp()</td>
</tr>
<tr class="even">
<td>_setjmp()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Developers should use setjmp() instead.</td>
</tr>
<tr class="odd">
<td>_tolower()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Developers should use the tolower() function instead.</td>
</tr>
<tr class="even">
<td>_toupper()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Developers should use the toupper() function instead.</td>
</tr>
<tr class="odd">
<td>a64l()</td>
<td></td>
<td>X</td>
<td>FACE forbids using a64l and l64a. Developers should use the strtoll()/strtoul() family of functions instead.</td>
</tr>
<tr class="even">
<td>abort()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>abs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>accept()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>access()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>acos()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>acosf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>acosh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>acoshf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>acoshl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>acosl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>aio_cancel()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>aio_error()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>aio_fsync()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>aio_read()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>aio_return()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>aio_suspend()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>aio_write()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>alarm()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>alphasort()</td>
<td></td>
<td>X</td>
<td>This function is restricted due to an assessment of the function being unsafe with possible impact to the heap and kernel file descriptors when called or cancelled asynchronously. The lower level opendir() and readdir() functions should be used directly rather than the higher level scandir() and alphasort() convenience functions.</td>
</tr>
<tr class="odd">
<td>asctime()</td>
<td></td>
<td>X</td>
<td>asctime() and asctime_r() are included in POSIX for compatibility with older implementations and do not support localized date and time formats. Developers should use strftime() instead.</td>
</tr>
<tr class="even">
<td>asctime_r()</td>
<td></td>
<td>X</td>
<td>asctime() and asctime_r() are included in POSIX for compatibility with older implementations and do not support localized date and time formats. Developers should use strftime() instead.</td>
</tr>
<tr class="odd">
<td>asin()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>asinf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>asinh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>asinhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>asinhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>asinl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>assert()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atan()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atan2()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atan2f()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atan2l()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atanh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atanhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atanhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atanl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atexit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atof()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atoi()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>atol()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>atoll()</td>
<td></td>
<td>X</td>
<td><p>The atoll() function does not perform error checking and has been subsumed in POSIX by the newer strtoll() function which does. The POSIX standards committee chose to retain the atoll() function as well because of its extensive use in existing code but developers should use the strtoll() function instead which performs error checking.</p>
<p>FIX: Change</p>
<p>atoll(str)</p>
<p>to</p>
<p>strtoll(str, (char**) NULL, 10)</p>
<p>which is functionally equivalent.</p></td>
</tr>
<tr class="even">
<td>basename()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>bcopy()</td>
<td></td>
<td>X</td>
<td><p>The bcopy() function has been removed from IEEE Std 1003.1-2013 after having previously been deprecated in the 2008 release of the standard. Although removed from the current version of the standard this function is included in the Façade API because it is still widely available on many implementations. Developers should use memmove() instead which is still supported and provides equivalent functionality.</p>
<p>FIX: Change</p>
<p>bcopy(s1,s2,n)</p>
<p>to</p>
<p>memmove(s2,s1,n)</p>
<p>Note that the number and type of arguments is the same; the order is simply different.</p></td>
</tr>
<tr class="even">
<td>bind()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>bsearch()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>btowc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>bzero()</td>
<td></td>
<td>X</td>
<td><p>The bzero() function has been removed from IEEE Std 1003.1-2013 after having previously been deprecated in the 2008 release of the standard. Although removed from the current version of the standard this function is included in the Façade API because it is still widely available on many implementations. Developers should use memset() instead which is still supported and provides equivalent functionality.</p>
<p>FIX: Change</p>
<p>bzero(b, len)</p>
<p>to</p>
<p>memset(b, ‘\0’, len)</p>
<p>which provides equivalent functionality.</p></td>
</tr>
<tr class="even">
<td>cabs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cabsf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cabsl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cacos()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cacosf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cacosh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cacoshf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cacoshl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cacosl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>calloc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>carg()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cargf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cargl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>casin()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>casinf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>casinh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>casinhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>casinhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>casinl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>catan()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>catanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>catanh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>catanhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>catanhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>catanl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>catclose()</td>
<td></td>
<td>X</td>
<td><p>Developers should use the Critical Abstraction Layer (CAL) and/or Data Transfer instead of message catalogs for storing and/or transferring messages.</p>
<p>The issue, in short, is that text read from message catalogs may not be trustworthy. In addition, the catopen() and catgets() functions are dependent upon the value of the NLSPATH environment variable. If an attacker is able to modify the environment, he or she can modify this variable to cause a program to load strings from arbitrary files; alternatively, an attacker can exploit NLSPATH to overwrite a message catalog and cause it to return arbitrarily long strings, which can subsequently be used to execute arbitrary code.</p></td>
</tr>
<tr class="even">
<td>catgets()</td>
<td></td>
<td>X</td>
<td><p>Developers should use the CAL and/or Data Transfer instead of message catalogs for storing and/or transferring messages.</p>
<p>The issue, in short, is that text read from message catalogs may not be trustworthy. In addition, the catopen() and catgets() functions are dependent upon the value of the NLSPATH environment variable. If an attacker is able to modify the environment, he or she can modify this variable to cause a program to load strings from arbitrary files; alternatively, an attacker can exploit NLSPATH to overwrite a message catalog and cause it to return arbitrarily long strings, which can subsequently be used to execute arbitrary code.</p></td>
</tr>
<tr class="odd">
<td>catopen()</td>
<td></td>
<td>X</td>
<td><p>Developers should use the CAL and/or Data Transfer instead of message catalogs for storing and/or transferring messages.</p>
<p>The issue, in short, is that text read from message catalogs may not be trustworthy. In addition, the catopen() and catgets() functions are dependent upon the value of the NLSPATH environment variable. If an attacker is able to modify the environment, he or she can modify this variable to cause a program to load strings from arbitrary files; alternatively, an attacker can exploit NLSPATH to overwrite a message catalog and cause it to return arbitrarily long strings, which can subsequently be used to execute arbitrary code.</p></td>
</tr>
<tr class="even">
<td>cbrt()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cbrtf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cbrtl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ccos()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ccosf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ccosh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ccoshf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ccoshl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ccosl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ceil()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ceilf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ceill()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cexp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cexpf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cexpl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cfgetispeed()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>cfgetospeed()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>cfsetispeed()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>cfsetospeed()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>chdir()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>chmod()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>chown()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cimag()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cimagf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cimagl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>clearerr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>clock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>clock_getcpuclockid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>clock_getres()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>clock_gettime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>clock_nanosleep()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>clock_settime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>clog()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>clogf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>clogl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>close()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>closedir()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>closelog()</td>
<td></td>
<td>X</td>
<td>The implementation of system logs is implementation defined. Developers should use OMS defined logging facilities instead.</td>
</tr>
<tr class="even">
<td>confstr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>conj()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>conjf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>conjl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>connect()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>copysign()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>copysignf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>copysignl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cos()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cosf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cosh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>coshf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>coshl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cosl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cpow()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cpowf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cpowl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cproj()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>cprojf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>cprojl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>creal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>crealf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>creall()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>creat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>crypt()</td>
<td></td>
<td>X</td>
<td>The implementation of the algorithm for this function is implementation defined and may not be suitable for usage in an OMS Service. The values returned from this function are additionally not guaranteed by the standard to be portable among conformant systems.</td>
</tr>
<tr class="odd">
<td>csin()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>csinf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>csinh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>csinhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>csinhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>csinl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>csqrt()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>csqrtf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>csqrtl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ctan()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ctanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ctanh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ctanhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ctanhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ctanl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ctermid()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>ctime()</td>
<td></td>
<td>X</td>
<td><p>The ctime() function is not thread-safe; developer should use the ctime_r() function instead, which is.</p>
<p>FIX: Change</p>
<p>ctime()</p>
<p>to</p>
<p>ctime_r()</p>
<p>which provides equivalent functionality.</p></td>
</tr>
<tr class="even">
<td>ctime_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>daylight</td>
<td></td>
<td>X</td>
<td>Developers should not manipulate the external variable daylight which is included in the time.h header directly. Developers should instead rely on standard functions such as tzset() to set this variable correctly.</td>
</tr>
<tr class="even">
<td>dbm_clearerr()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="odd">
<td>dbm_close()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="even">
<td>dbm_delete()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="odd">
<td>dbm_error()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="even">
<td>dbm_fetch()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="odd">
<td>dbm_firstkey()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="even">
<td>dbm_nextkey()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="odd">
<td>dbm_open()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="even">
<td>dbm_store()</td>
<td></td>
<td>X</td>
<td>The dbm_* family of database functions are restricted from use as the functionality provided has severe limitations (see IEEE Std 1003.1, 2013 Edition, Database Functions, Application Usage for additional details).</td>
</tr>
<tr class="odd">
<td>difftime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>dirfd()</td>
<td></td>
<td>X</td>
<td>This function is excluded due to a time of check to time of use (TOCTTOU) vulnerability where the relative path returned from dirfd() may not refer to the right location by the time it would be passed to the kernel.</td>
</tr>
<tr class="odd">
<td>dirname()</td>
<td></td>
<td>X</td>
<td><p>The dirname() function may return a pointer to internal storage which might be invalidated or the data it points to overwritten by a subsequent call.</p>
<p>FIX: Developers should use standard string functions or regular expressions instead of dirname().</p></td>
</tr>
<tr class="even">
<td>div()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>dlclose()</td>
<td></td>
<td>X</td>
<td><p>FACE does not permit libraries to be dynamically loaded at run-time.</p>
<p>FIX: Developers should use static linking instead.</p></td>
</tr>
<tr class="even">
<td>dlerror()</td>
<td></td>
<td>X</td>
<td><p>FACE does not permit libraries to be dynamically loaded at run-time.</p>
<p>FIX: Developers should use static linking instead.</p></td>
</tr>
<tr class="odd">
<td>dlopen()</td>
<td></td>
<td>X</td>
<td><p>FACE does not permit libraries to be dynamically loaded at run-time.</p>
<p>FIX: Developers should use static linking instead.</p></td>
</tr>
<tr class="even">
<td>dlsym()</td>
<td></td>
<td>X</td>
<td><p>FACE does not permit libraries to be dynamically loaded at run-time.</p>
<p>FIX: Developers should use static linking instead.</p></td>
</tr>
<tr class="odd">
<td>dprintf()</td>
<td></td>
<td>X</td>
<td><p>Developers should use fprintf() which writes output to a file stream rather than dprintf() which writes output to a lower level file descriptor.</p>
<p>FIX: Developers should use fprintf() rather than dprintf().</p></td>
</tr>
<tr class="even">
<td>drand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="odd">
<td>dup()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>dup2()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>duplocale()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>encrypt()</td>
<td></td>
<td>X</td>
<td>The implementation of the algorithm for this function is implementation defined and may not be suitable for usage in an OMS Service.</td>
</tr>
<tr class="odd">
<td>endgrent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>endhostent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>endnetent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>endprotoent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>endpwent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>endservent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>endutxent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>environ</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>erand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="even">
<td>erf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>erfc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>erfcf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>erfcl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>erff()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>erfl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>errno</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>execl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>execle()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>execlp()</td>
<td></td>
<td>X</td>
<td>Developers should not use execlp() or execve() to load another program as these functions specify only a program name and not a complete path which is considered dangerous as an attacker could modify the PATH environment variable to cause a different program to be launched. Developers should instead use one of the other functions in the exec family which do require that a full path be specified, which includes: execl(), execle(), execv(), or execve().</td>
</tr>
<tr class="even">
<td>execv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>execve()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>execvp()</td>
<td></td>
<td>X</td>
<td>Developers should not use execlp() or execve() to load another program as these functions specify only a program name and not a complete path which is considered dangerous as an attacker could modify the PATH environment variable to cause a different program to be launched. Developers should instead use one of the other functions in the exec family which do require that a full path be specified, which includes: execl(), execle(), execv(), or execve().</td>
</tr>
<tr class="odd">
<td>exit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>exp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>exp2()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>exp2f()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>exp2l()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>expf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>expl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>expm1()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>expm1f()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>expm1l()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fabs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fabsf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fabsl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>faccessat()</td>
<td></td>
<td>X</td>
<td>Using faccessat() to determine a user’s permissions relative to a file should be avoided as this function uses a relative path and is additionally subject to potential race conditions. For example, using faccessat() to check whether a user is authorized to open a particular file, before performing an open() on said file, creates a security hole as the user could exploit the short time interval between checking and opening the file to manipulate it. Developers should use the access() function instead which uses an absolute path. Note that the access() function, which FACE allows, also suffers from the same security holes as noted above however, but it does use a full, rather than a relative, path.</td>
</tr>
<tr class="odd">
<td>fattach()</td>
<td></td>
<td>X</td>
<td>The fattach() function should not be used as it is not widely available on Linux</td>
</tr>
<tr class="even">
<td>fchdir()</td>
<td></td>
<td>X</td>
<td>Developers should use chdir() instead of fchdir() to change the current working directory. The chdir() function is functionally similar to fchdir() except that it uses a fully qualified path, rather than a open file descriptor, to specify the new current working directory which is considered safer. fchdir() is typically forbidden for this reason. In addition, using fchdir() along with a file descriptor requires a developer to make use of lower level I/O calls (i.e., those that work directly with file descriptors rather than the higher level standard I/O calls), not all of which are allowed by this Standard.</td>
</tr>
<tr class="odd">
<td>fchmod()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fchmodat()</td>
<td></td>
<td>X</td>
<td>Developer should use fchmod() rather than fchmodat(). The fchmod() function uses a fully qualified path as input whereas the fchmodat() function specifies the path relative to an open file descriptor. Specifying full qualified rather than relative paths is generally considered safer and additionally facilitates path checking. The use of a relative path combined with a file descriptor is additionally susceptible to potential exploits. See notes on fchdir() in this Standard for additional information.</td>
</tr>
<tr class="odd">
<td>fchown()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fchownat()</td>
<td></td>
<td>X</td>
<td>Developers should use fchown() rather than fchownat(). See fattach() and fchdir() above.</td>
</tr>
<tr class="odd">
<td>fclose()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fcntl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>FD_CLR()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>FD_ISSET()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>FD_SET()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>FD_ZERO()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fdatasync()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fdetach()</td>
<td></td>
<td>X</td>
<td>Developers should avoid this call as it is not widely available on Linux.</td>
</tr>
<tr class="odd">
<td>fdim()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fdimf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fdiml()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fdopen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fdopendir()</td>
<td></td>
<td>X</td>
<td>Developers should use opendir() rather than fdopendir(). fdopendir() is functionally similar to opendir(). POSIX leaves it unspecified whether a successful call to fdopendir() will set the close-on-exec flag for the input file descriptor, fd.</td>
</tr>
<tr class="even">
<td>feclearexcept()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fegetenv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fegetexceptflag()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fegetround()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>feholdexcept()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>feof()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>feraiseexcept()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ferror()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fesetenv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fesetexceptflag()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fesetround()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fetestexcept()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>feupdateenv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fexecve()</td>
<td></td>
<td>X</td>
<td>Developers should use execve() instead of fexecve(). These functions perform the same task but fexecve() is not as widely available on Linux and additionally uses a file descriptor rather than an absolute path as input.</td>
</tr>
<tr class="even">
<td>fflush()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ffs()</td>
<td></td>
<td>X</td>
<td>Software running within the OS Façade should not be performing bit-twiddling operations and is part of XSI POSIX extension.</td>
</tr>
<tr class="even">
<td>fgetc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fgetpos()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fgets()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fgetwc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fgetws()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fileno()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>flockfile()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>floor()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>floorf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>floorl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fma()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fmaf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fmal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fmax()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fmaxf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fmaxl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fmemopen()</td>
<td></td>
<td>X</td>
<td>Restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>fmin()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fminf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fminl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fmod()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fmodf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fmodl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fmtmsg()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>fnmatch()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe; it accesses the locale and the environment without any guards to ensure safety in the presence of concurrent modification.</td>
</tr>
<tr class="odd">
<td>fopen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fork()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fpathconf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fpclassify()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fputc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fputs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fputwc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fputws()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fread()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>free()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>freeaddrinfo()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>freelocale()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>freopen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>frexp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>frexpf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>frexpl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fseek()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fseeko()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fsetpos()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fstat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fstatat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits; use stat() or lstat() instead.</td>
</tr>
<tr class="even">
<td>fstatvfs()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits; use statvfs() instead.</td>
</tr>
<tr class="odd">
<td>fsync()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ftell()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ftello()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ftok()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>ftruncate()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ftrylockfile()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ftw()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>funlockfile()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>futimens()</td>
<td></td>
<td>X</td>
<td>An OMS Service should not change the file access times.</td>
</tr>
<tr class="even">
<td>fwide()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fwprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>fwrite()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>fwscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>gai_strerror()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getaddrinfo()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getc_unlocked()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getchar()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getchar_unlocked()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getcwd()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getdate()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>getdate_err</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>getdelim()</td>
<td></td>
<td>X</td>
<td>Restricted by PSE54.</td>
</tr>
<tr class="even">
<td>getegid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getenv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>geteuid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getgid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getgrent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>getgrgid()</td>
<td></td>
<td>X</td>
<td>An OMS Service should not need access to the User Groups on the local host.</td>
</tr>
<tr class="even">
<td>getgrgid_r()</td>
<td></td>
<td>X</td>
<td>An OMS Service should not need access to the User Groups on the local host.</td>
</tr>
<tr class="odd">
<td>getgrnam()</td>
<td></td>
<td>X</td>
<td>An OMS Service should not need access to the User Groups on the local host.</td>
</tr>
<tr class="even">
<td>getgrnam_r()</td>
<td></td>
<td>X</td>
<td>An OMS Service should not need access to the User Groups on the local host.</td>
</tr>
<tr class="odd">
<td>getgroups()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>gethostbyname()</td>
<td></td>
<td>X</td>
<td>The gethostbyname() function is not thread-safe and has been removed from POSIX as of the 2008 release of the standard. It is included in the Façade API because it is still widely available on many implementations. Developers should use getnameinfo() instead.</td>
</tr>
<tr class="odd">
<td>gethostent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>gethostid()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>gethostname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getitimer()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>getline()</td>
<td></td>
<td>X</td>
<td>Restricted by PSE54.</td>
</tr>
<tr class="even">
<td>getlogin()</td>
<td>X</td>
<td></td>
<td>This function is not thread-safe. An OMS Service should not need access to the User credentials on the local host.</td>
</tr>
<tr class="odd">
<td>getlogin_r()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe. An OMS Service should not need access to the User credentials on the local host.</td>
</tr>
<tr class="even">
<td>getmsg()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Not implemented in certain versions of Linux.</td>
</tr>
<tr class="odd">
<td>getnameinfo()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getnetbyaddr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getnetbyname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getnetent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getopt()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe.</td>
</tr>
<tr class="even">
<td>getpeername()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getpgid()</td>
<td></td>
<td>X</td>
<td>OMS Services are not expected to need the group process id.</td>
</tr>
<tr class="even">
<td>getpgrp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getpid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getpmsg()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Not implemented in certain versions of Linux.</td>
</tr>
<tr class="odd">
<td>getppid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getpriority()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>getprotobyname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getprotobynumber()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getprotoent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getpwent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>getpwnam()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe. OMS Services are not expected to need user login information.</td>
</tr>
<tr class="even">
<td>getpwnam_r()</td>
<td></td>
<td>X</td>
<td>OMS Services are not expected to need user login information.</td>
</tr>
<tr class="odd">
<td>getpwuid()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe. OMS Services are not expected to need user login information.</td>
</tr>
<tr class="even">
<td>getpwuid_r()</td>
<td></td>
<td>X</td>
<td>OMS Services are not expected to need user login information.</td>
</tr>
<tr class="odd">
<td>getrlimit()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>getrusage()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>gets()</td>
<td></td>
<td>X</td>
<td>This function can cause buffer overflows; use fgets() instead.</td>
</tr>
<tr class="even">
<td>getservbyname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getservbyport()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getservent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getsid()</td>
<td></td>
<td>X</td>
<td>An OMS Service is not expected to need access to the session id.</td>
</tr>
<tr class="even">
<td>getsockname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getsockopt()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>getsubopt()</td>
<td></td>
<td>X</td>
<td>This function is restricted because it is used in conjunction with getopt() to retrieve command line options. getopt() is restricted.</td>
</tr>
<tr class="odd">
<td>gettimeofday()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>getuid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getutxent()</td>
<td></td>
<td>X</td>
<td>FACE does not permit usage of the user accounting database functions.</td>
</tr>
<tr class="even">
<td>getutxid()</td>
<td></td>
<td>X</td>
<td>FACE does not permit usage of the user accounting database functions.</td>
</tr>
<tr class="odd">
<td>getutxline()</td>
<td></td>
<td>X</td>
<td>FACE does not permit usage of the user accounting database functions.</td>
</tr>
<tr class="even">
<td>getwc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>getwchar()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>glob()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>globfree()</td>
<td></td>
<td>X</td>
<td>This function is restricted due to its association with the glob() function.</td>
</tr>
<tr class="even">
<td>gmtime()</td>
<td></td>
<td>X</td>
<td>gmtime() is not thread-safe. Should use the thread-safe function gmtime_r() instead.</td>
</tr>
<tr class="odd">
<td>gmtime_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>grantpt()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>gcvt()</td>
<td></td>
<td>X</td>
<td>The gcvt() function is deprecated and may be withdrawn from future versions of POSIX. Should use the snprintf() function instead.</td>
</tr>
<tr class="even">
<td>hcreate()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>hdestroy()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>hsearch()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>htonl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>htons()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>hypot()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>hypotf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>hypotl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iconv()</td>
<td></td>
<td>X</td>
<td>OMS Services are not expected to convert from one character set to another; function is also reliant on locale.</td>
</tr>
<tr class="odd">
<td>iconv_close()</td>
<td></td>
<td>X</td>
<td>OMS Services are not expected to convert from one character set to another; function is also reliant on locale</td>
</tr>
<tr class="even">
<td>iconv_open()</td>
<td></td>
<td>X</td>
<td>OMS Services are not expected to convert from one character set to another; function is also reliant on locale</td>
</tr>
<tr class="odd">
<td>if_freenameindex()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>if_indextoname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>if_nameindex()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>if_nametoindex()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ilogb()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ilogbf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ilogbl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>imaxabs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>imaxdiv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>index()</td>
<td></td>
<td>X</td>
<td>The index() functions has been removed from POSIX. Should use the strchr() function instead which is functionally equivalent and takes the same arguments. Simply change index(a, b) =&gt; strchr(a, b).</td>
</tr>
<tr class="odd">
<td>inet_addr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>inet_ntoa()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>inet_ntop()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>inet_pton()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>initstate()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>insque()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>ioctl()</td>
<td></td>
<td>X</td>
<td>This function does not fit into a uniform standard. OMS Services are not expected to use low level device control mechanisms.</td>
</tr>
<tr class="even">
<td>isalnum()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isalnum_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isalnum_l() can cause undefined behavior. Developers should use isalnum() instead.</td>
</tr>
<tr class="even">
<td>isalpha()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isalpha_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isalpha_l() can cause undefined behavior. Developers should use isalpha() instead.</td>
</tr>
<tr class="even">
<td>isascii()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>isastream()</td>
<td></td>
<td>X</td>
<td>This function is not implemented in Linux kernels.</td>
</tr>
<tr class="even">
<td>isatty()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>isblank()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isblank_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isblank_l() can cause undefined behavior. Developers should use isblank() instead.</td>
</tr>
<tr class="odd">
<td>iscntrl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iscntrl_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iscntrl_l() can cause undefined behavior. Developers should use iscntrl() instead.</td>
</tr>
<tr class="odd">
<td>isdigit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isdigit_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isdigit_l() can cause undefined behavior. Developers should use isdigit() instead.</td>
</tr>
<tr class="odd">
<td>isfinite()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isgraph()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isgraph_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isgraph_l() can cause undefined behavior. Developers should use isgraph() instead.</td>
</tr>
<tr class="even">
<td>isgreater()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isgreaterequal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isinf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isless()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>islessequal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>islessgreater()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>islower()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>islower_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of islower_l() can cause undefined behavior. Developers should use islower() instead.</td>
</tr>
<tr class="even">
<td>isnan()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isnormal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isprint()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isprint_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isprint_l() can cause undefined behavior. Developers should use isprint() instead.</td>
</tr>
<tr class="even">
<td>ispunct()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ispunct_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of ispunct_l() can cause undefined behavior. Developers should use ispunct() instead.</td>
</tr>
<tr class="even">
<td>isspace()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isspace_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isspace_l() can cause undefined behavior. Developers should use isspace() instead.</td>
</tr>
<tr class="even">
<td>isunordered()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>isupper()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isupper_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isupper_l() can cause undefined behavior. Developers should use isupper() instead.</td>
</tr>
<tr class="odd">
<td>iswalnum()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswalnum_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswalnum_l() can cause undefined behavior. Developers should use iswalnum() instead.</td>
</tr>
<tr class="odd">
<td>iswalpha()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswalpha_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswalpha_l() can cause undefined behavior. Developers should use iswalpha() instead.</td>
</tr>
<tr class="odd">
<td>iswblank()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswblank_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswblank_l() can cause undefined behavior. Developers should use iswblank() instead.</td>
</tr>
<tr class="odd">
<td>iswcntrl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswcntrl_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswcntrl_l() can cause undefined behavior. Developers should use iswcntrl() instead.</td>
</tr>
<tr class="odd">
<td>iswctype()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswctype_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswctype_l() can cause undefined behavior. Developers should use iswctype() instead.</td>
</tr>
<tr class="odd">
<td>iswdigit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswdigit_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswdigit_l() can cause undefined behavior. Developers should use iswdigit() instead.</td>
</tr>
<tr class="odd">
<td>iswgraph()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswgraph_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswgraph_l() can cause undefined behavior. Developers should use iswgraph() instead.</td>
</tr>
<tr class="odd">
<td>iswlower()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswlower_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswlower_l() can cause undefined behavior. Developers should use iswlower() instead.</td>
</tr>
<tr class="odd">
<td>iswprint()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswprint_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswprint_l() can cause undefined behavior. Developers should use iswprint() instead.</td>
</tr>
<tr class="odd">
<td>iswpunct()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswpunct_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswpunct_l() can cause undefined behavior. Developers should use iswpunct() instead.</td>
</tr>
<tr class="odd">
<td>iswspace()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswspace_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswspace_l() can cause undefined behavior. Developers should use iswspace() instead.</td>
</tr>
<tr class="odd">
<td>iswupper()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswupper_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswupper_l() can cause undefined behavior. Developers should use iswupper() instead.</td>
</tr>
<tr class="odd">
<td>iswxdigit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>iswxdigit_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of iswxdigit_l() can cause undefined behavior. Developers should use iswxdigit() instead.</td>
</tr>
<tr class="odd">
<td>isxdigit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>isxdigit_l()</td>
<td></td>
<td>X</td>
<td>Certain usages of isxdigit_l() can cause undefined behavior. Developers should use isxdigit() instead.</td>
</tr>
<tr class="odd">
<td>j0()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>j1()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>jn()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>jrand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="odd">
<td>kill()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>killpg()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>l64a()</td>
<td></td>
<td>X</td>
<td>FACE forbids using a64l and l64a. Developers should use the strtoll()/strtoul() family of functions instead.</td>
</tr>
<tr class="even">
<td>labs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lchown()</td>
<td></td>
<td>X</td>
<td></td>
</tr>
<tr class="even">
<td>lcong48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="odd">
<td>ldexp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ldexpf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ldexpl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ldiv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lfind()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>lgamma()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lgammaf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lgammal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>link()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>linkat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits; use link() instead.</td>
</tr>
<tr class="odd">
<td>lio_listio()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>listen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>llabs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lldiv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>llrint()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>llrintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>llrintl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>llround()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>llroundf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>llroundl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>localeconv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>localtime()</td>
<td></td>
<td>X</td>
<td>localtime() is not thread-safe. Should use the thread-safe function localtime_r() instead.</td>
</tr>
<tr class="odd">
<td>localtime_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lockf()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>log()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>log10()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>log10f()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>log10l()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>log1p()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>log1pf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>log1pl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>log2()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>log2f()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>log2l()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>logb()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>logbf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>logbl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>logf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>logl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>longjmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lrand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="even">
<td>lrint()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lrintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lrintl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lround()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lroundf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>lroundl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lsearch()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>lseek()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>lstat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>malloc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mblen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mbrlen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mbrtowc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mbsinit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mbsnrtowcs()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe.</td>
</tr>
<tr class="odd">
<td>mbsrtowcs()</td>
<td>X</td>
<td></td>
<td>This function is not thread-safe.</td>
</tr>
<tr class="even">
<td>mbstowcs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mbtowc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>memccpy()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>memchr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>memcmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>memcpy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>memmove()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>memset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mkdir()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mkdirat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="even">
<td>mkdtemp()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>mkfifo()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mkfifoat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="odd">
<td>mknod()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>mknodat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="odd">
<td>mkstemp()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>mktime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mlock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mlockall()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mmap()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>modf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>modff()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>modfl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mprotect()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mq_close()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mq_getattr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mq_notify()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mq_open()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mq_receive()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mq_send()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mq_setattr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mq_timedreceive()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mq_timedsend()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>mq_unlink()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>mrand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="odd">
<td>msgctl()</td>
<td></td>
<td>X</td>
<td>Developers should use the CAL rather than message queues for interprocess communications.</td>
</tr>
<tr class="even">
<td>msgget()</td>
<td></td>
<td>X</td>
<td>Developers should use the CAL rather than message queues for interprocess communications.</td>
</tr>
<tr class="odd">
<td>msgrcv()</td>
<td></td>
<td>X</td>
<td>Developers should use the CAL rather than message queues for interprocess communications.</td>
</tr>
<tr class="even">
<td>msgsnd()</td>
<td></td>
<td>X</td>
<td>Developers should use the CAL rather than message queues for interprocess communications.</td>
</tr>
<tr class="odd">
<td>msync()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>munlock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>munlockall()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>munmap()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nan()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>nanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nanl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>nanosleep()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nearbyint()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>nearbyintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nearbyintl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>newlocale()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>nextafter()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>nextafterf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nextafterl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>nexttoward()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nexttowardf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>nexttowardl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>nftw()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>nice()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>nl_langinfo()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>nl_langinfo_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>nrand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="even">
<td>ntohl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ntohs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>open()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>open_memstream()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>open_wmemstream()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>openat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="even">
<td>opendir()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>openlog()</td>
<td></td>
<td>X</td>
<td>The implementation of system logs is implementation defined. Developers should use OMS defined logging facilities instead.</td>
</tr>
<tr class="even">
<td>optopt</td>
<td></td>
<td>X</td>
<td>This variable is used in conjunction with getopt() which is restricted.</td>
</tr>
<tr class="odd">
<td>pathconf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pause()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pclose()</td>
<td></td>
<td>X</td>
<td>OMS Services should use the CAL for inter-process communication (IPC).</td>
</tr>
<tr class="even">
<td>perror()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pipe()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>poll()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>popen()</td>
<td></td>
<td>X</td>
<td>OMS Services should use the CAL for IPC.</td>
</tr>
<tr class="even">
<td>posix_devctl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_fadvise()</td>
<td></td>
<td>X</td>
<td>This function is not provided on all implementations.</td>
</tr>
<tr class="even">
<td>posix_fallocate()</td>
<td></td>
<td>X</td>
<td>This function is only thread-safe in certain conditions. It is also part of the Advisory Information option and isn’t guaranteed to be provided on all implementations.</td>
</tr>
<tr class="odd">
<td>posix_madvise()</td>
<td></td>
<td>X</td>
<td>This function is part of the Advisory Information option and is not provided on all implementations.</td>
</tr>
<tr class="even">
<td>posix_mem_offset()</td>
<td></td>
<td>X</td>
<td>This function is part of the advanced real time options group. OMS Services are not expected to have hard real time requirements.</td>
</tr>
<tr class="odd">
<td>posix_memalign()</td>
<td></td>
<td>X</td>
<td>This function is part of the advanced real time options group. OMS Services are not expected to have hard real time requirements.</td>
</tr>
<tr class="even">
<td>posix_openpt()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>posix_spawn()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawn_file_actions_ addclose()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawn_file_actions_ adddup2()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawn_file_actions_ addopen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawn_file_actions_ destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawn_file_actions_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_ getschedparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_ getschedpolicy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_ setschedparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_ setschedpolicy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_getflags()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_getpgroup()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_getsigdefault()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_getsigmask()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_setflags()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_setpgroup()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnattr_setsigdefault()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_spawnattr_setsigmask()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>posix_spawnp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>posix_trace_attr_ getcreatetime()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_ getgenversion()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_ getlogfullpolicy()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_ getmaxdatasize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_ getmaxsystemeventsize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_ getmaxusereventsize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_ getstreamfullpolicy()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_ getstreamsize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_ setlogfullpolicy()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_ setmaxdatasize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_ setstreamfullpolicy()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_destroy()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_getclockres()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_getinherited()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_getlogsize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_getname()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_init()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_setinherited()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_setlogsize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_attr_setname()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_attr_setstreamsize()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_clear()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_close()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_create()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_create_withlog()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_event()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_eventid_equal()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_eventid_get_ name()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_eventid_open()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_eventset_ ismember()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_eventset_add()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_eventset_del()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_eventset_empty()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_eventset_fill()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_eventtypelist_ getnext_id()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_eventtypelist_ rewind()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_flush()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_get_attr()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_get_filter()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_get_status()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_getnext_event()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_open()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_rewind()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_set_filter()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_shutdown()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_start()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_stop()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_timedgetnext_ event()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_trace_trid_eventid_ open()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="odd">
<td>posix_trace_trygetnext_event()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete by IEEE Std 1003.1 and may be removed in a future release of the standard. Strictly confirming POSIX applications are not allowed to use obsolescent features. Thus developers should not use or rely upon this functionality being available.</td>
</tr>
<tr class="even">
<td>posix_typed_mem_get_info()</td>
<td></td>
<td>X</td>
<td>This function is part of the advanced real time options group. OMS Services are not expected to have hard real time requirements.</td>
</tr>
<tr class="odd">
<td>posix_typed_mem_open()</td>
<td></td>
<td>X</td>
<td>This function is part of the advanced real time options group. OMS Services are not expected to have hard real time requirements.</td>
</tr>
<tr class="even">
<td>pow()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>powf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>powl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pread()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>printf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pselect()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>psiginfo()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>psignal()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_atfork()</td>
<td></td>
<td>X</td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_getdetachstate()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_getguardsize()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_getinheritsched()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_getschedparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_getschedpolicy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_getscope()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_getstack()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_getstackaddr()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Use pthread_attr_getstack() instead.</td>
</tr>
<tr class="even">
<td>pthread_attr_getstacksize()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_setdetachstate()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_setguardsize()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_setinheritsched()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_setschedparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_setschedpolicy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_setscope()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_attr_setstack()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_attr_setstackaddr()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Use pthread_attr_setstack() instead.</td>
</tr>
<tr class="even">
<td>pthread_attr_setstacksize()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_barrier_destroy()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_barrier_init()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_barrier_wait()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_barrierattr_ getpshared()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_barrierattr_destroy()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_barrierattr_init()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_barrierattr_setpshared()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_cancel()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_cleanup_pop()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_cleanup_push()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_cond_broadcast()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_cond_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_cond_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_cond_signal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_cond_timedwait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_cond_wait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_condattr_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_condattr_getclock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_condattr_getpshared()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_condattr_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_condattr_setclock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_condattr_setpshared()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_create()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_detach()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_equal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_exit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_getconcurrency()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_getcpuclockid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_getschedparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_getspecific()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_join()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_key_create()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_key_delete()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_kill()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutex_consistent()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_mutex_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutex_getprioceiling()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutex_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutex_lock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutex_setprioceiling()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutex_timedlock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutex_trylock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutex_unlock()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutexattr_ getprioceiling()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutexattr_ getprotocol()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutexattr_ setprioceiling()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutexattr_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutexattr_getpshared()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutexattr_getrobust()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_mutexattr_gettype()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutexattr_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutexattr_setprotocol()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_mutexattr_setpshared()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_mutexattr_setrobust()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_mutexattr_settype()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_once()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_rwlock_destroy()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_rwlock_init()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="odd">
<td>pthread_rwlock_rdlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_rwlock_timedrdlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="odd">
<td>pthread_rwlock_timedwrlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_rwlock_tryrdlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="odd">
<td>pthread_rwlock_trywrlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_rwlock_unlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="odd">
<td>pthread_rwlock_wrlock()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_rwlockattr_ getpshared()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="odd">
<td>pthread_rwlockattr_ setpshared()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_rwlockattr_destroy()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="odd">
<td>pthread_rwlockattr_init()</td>
<td></td>
<td>X</td>
<td>Developers should not use read-write locks as they are susceptible to priority inversion which can lead to unpredictable behavior and unbounded latency.</td>
</tr>
<tr class="even">
<td>pthread_self()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_setcancelstate()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_setcanceltype()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_setconcurrency()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_setschedparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_setschedprio()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_setspecific()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pthread_sigmask()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pthread_spin_destroy()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_spin_init()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_spin_lock()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_spin_trylock()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>pthread_spin_unlock()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>pthread_testcancel()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ptsname()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>putc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>putc_unlocked()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>putchar()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>putchar_unlocked()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>putenv()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>putmsg()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX.</td>
</tr>
<tr class="odd">
<td>putpmsg()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX.</td>
</tr>
<tr class="even">
<td>puts()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>pututxline()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result. Also, FACE does not permit usage of the user accounting database functions.</td>
</tr>
<tr class="even">
<td>putwc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>putwchar()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>pwrite()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>qsort()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>raise()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>rand()</td>
<td></td>
<td>X</td>
<td>The rand() function is not thread-safe. Developers should use the thread-safe function rand_r() instead.</td>
</tr>
<tr class="even">
<td>rand_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>random()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>read()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>readdir()</td>
<td></td>
<td>X</td>
<td>The readdir() function is not thread-safe. Developers should use readdir_r() instead.</td>
</tr>
<tr class="even">
<td>readdir_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>readlink()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="even">
<td>readlinkat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="odd">
<td>readv()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>realloc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>realpath()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>recv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>recvfrom()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>recvmsg()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>regcomp()</td>
<td></td>
<td>X</td>
<td>This function takes a character array with no size argument. This pattern is a known security issue due to buffer overflows.</td>
</tr>
<tr class="even">
<td>regerror()</td>
<td></td>
<td>X</td>
<td>This function is part of the regular expressions option which has been restricted due to buffer overflow concerns.</td>
</tr>
<tr class="odd">
<td>regexec()</td>
<td></td>
<td>X</td>
<td>This function is part of the regular expressions option which has been restricted due to buffer overflow concerns.</td>
</tr>
<tr class="even">
<td>regfree()</td>
<td></td>
<td>X</td>
<td>This function is part of the regular expressions option which has been restricted due to buffer overflow concerns.</td>
</tr>
<tr class="odd">
<td>remainder()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>remainderf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>remainderl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>remove()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>remque()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>remquo()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>remquof()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>remquol()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>rename()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>renameat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="odd">
<td>rewind()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>rewinddir()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>rint()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>rintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>rintl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>rmdir()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>round()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>roundf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>roundl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>scalbln()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>scalblnf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>scalblnl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>scalbn()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>scalbnf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>scalbnl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>scandir()</td>
<td></td>
<td>X</td>
<td>This function is restricted due to an assessment of the function being unsafe with possible impact to the heap and kernel file descriptors when called or cancelled asynchronously. The lower level opendir() and readdir() functions should be used directly rather than the higher level scandir() and alphasort() convenience functions.</td>
</tr>
<tr class="odd">
<td>scanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sched_get_priority_max()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sched_get_priority_min()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sched_getparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sched_getscheduler()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sched_rr_get_interval()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sched_setparam()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sched_setscheduler()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sched_yield()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>seed48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="odd">
<td>seekdir()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>select()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sem_close()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sem_destroy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sem_getvalue()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sem_init()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sem_open()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sem_post()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sem_timedwait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sem_trywait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sem_unlink()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sem_wait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>semctl()</td>
<td></td>
<td>X</td>
<td>System V semaphores contain a well-known race condition due to the fact that creating and initializing a Semaphore is not atomic. See Unix Network Programming by W. Richard Steven for a more detailed explanation. Developers should use POSIX semaphores instead.</td>
</tr>
<tr class="even">
<td>semget()</td>
<td></td>
<td>X</td>
<td>System V semaphores contain a well-known race condition due to the fact that creating and initializing a Semaphore is not atomic. See Unix Network Programming by W. Richard Steven for a more detailed explanation. Developers should use POSIX semaphores instead.</td>
</tr>
<tr class="odd">
<td>semop()</td>
<td></td>
<td>X</td>
<td>System V semaphores contain a well-known race condition due to the fact that creating and initializing a Semaphore is not atomic. See Unix Network Programming by W. Richard Steven for a more detailed explanation. Developers should use POSIX semaphores instead.</td>
</tr>
<tr class="even">
<td>send()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sendmsg()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sendto()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>setbuf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setegid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>setenv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>seteuid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>setgid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setgrent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sethostent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setitimer()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>setjmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setkey()</td>
<td></td>
<td>X</td>
<td>The setkey() function provides access to an implementation defined encoding algorithm which may not be suitable for use in an OMS Service.</td>
</tr>
<tr class="odd">
<td>setlocale()</td>
<td>X</td>
<td></td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>setlogmask()</td>
<td></td>
<td>X</td>
<td>The implementation of system logs is implementation defined. Developers should use OMS defined logging facilities instead.</td>
</tr>
<tr class="odd">
<td>setnetent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setpgid()</td>
<td></td>
<td>X</td>
<td>This function is used for shell job control and is associated with terminal functions. Terminal functions are restricted.</td>
</tr>
<tr class="odd">
<td>setpgrp()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>setpriority()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>setprotoent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setpwent()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result. Also, FACE does not permit usage of the user database functions in POSIX.</td>
</tr>
<tr class="odd">
<td>setregid()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>setreuid()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>setrlimit()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>setservent()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>setsid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>setsockopt()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>setstate()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>setuid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>setutxent()</td>
<td></td>
<td>X</td>
<td>FACE does not permit usage of the user accounting database functions.</td>
</tr>
<tr class="even">
<td>setvbuf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>shm_open()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>shm_unlink()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>shmat()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>shmctl()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>shmdt()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>shmget()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>shutdown()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigaction()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sigaddset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigaltstack()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sigdelset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigemptyset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sigfillset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sighold()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sigignore()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>siginterrupt()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sigismember()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>siglongjmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>signal()</td>
<td></td>
<td>X</td>
<td>Developers should use sigaction() instead as signal() is deprecated, doesn’t always work correctly in multi-threaded environments, and is known to be less reliable.</td>
</tr>
<tr class="even">
<td>signbit()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>signgam</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>sigpause()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sigpending()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigprocmask()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sigqueue()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigrelse()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sigset()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>sigsetjmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sigsuspend()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigtimedwait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sigwait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sigwaitinfo()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sin()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sinf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sinh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sinhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sinhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sinl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sleep()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>snprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sockatmark()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>socket()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>socketpair()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sprintf()</td>
<td></td>
<td>X</td>
<td>sprintf() is susceptible to buffer overflows. Should use snprintf() instead.</td>
</tr>
<tr class="odd">
<td>sqrt()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>sqrtf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>sqrtl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>srand()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>srand48()</td>
<td></td>
<td>X</td>
<td>This function uses a linear congruential algorithm for randomness which does not provide a large enough range of numbers to be considered useful in support of encryption computations. An additional reason to not allow the use of this set of functions is that the use of 48-bit arithmetic does not guarantee the use of the remaining bits.</td>
</tr>
<tr class="even">
<td>srandom()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>sscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>stat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>statvfs()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>stpcpy()</td>
<td></td>
<td>X</td>
<td>This function is susceptible to buffer overflows. Use strncpy() instead.</td>
</tr>
<tr class="odd">
<td>stpncpy()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>strcasecmp()</td>
<td></td>
<td>X</td>
<td>This function is susceptible to buffer overflows.</td>
</tr>
<tr class="odd">
<td>strcasecmp_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>strcat()</td>
<td></td>
<td>X</td>
<td>strcat() is susceptible to buffer overflows. Should use strncat() instead</td>
</tr>
<tr class="odd">
<td>strchr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strcmp()</td>
<td></td>
<td>X</td>
<td>strcmp() is susceptible to buffer overflows. Should use strncmp instead. Change strcmp(str1, str2) =&gt; strncmp(str1, str2, n).</td>
</tr>
<tr class="odd">
<td>strcoll()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strcoll_l()</td>
<td></td>
<td>X</td>
<td></td>
</tr>
<tr class="odd">
<td>strcpy()</td>
<td></td>
<td>X</td>
<td>strcpy() is susceptible to buffer overflows. Should use strncpy() instead. Change strcpy(dest, src) to strncpy(dest, src, size-of-dest - 1)</td>
</tr>
<tr class="even">
<td>strcspn()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strdup()</td>
<td></td>
<td>X</td>
<td></td>
</tr>
<tr class="even">
<td>strerror()</td>
<td></td>
<td>X</td>
<td>strerror() is not thread-safe. Should use strerror_r() instead.</td>
</tr>
<tr class="odd">
<td>strerror_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>strerror_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strfmon()</td>
<td></td>
<td>X</td>
<td>This function converts monetary value to a string. It is not expected for an OMS service to process monetary values.</td>
</tr>
<tr class="even">
<td>strfmon_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>strftime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strftime_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>strlen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strncasecmp()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>strncasecmp_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>strncat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strncmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strncpy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strndup()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>strnlen()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>strpbrk()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strptime()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>strrchr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strsignal()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe. Usage can cause race conditions.</td>
</tr>
<tr class="odd">
<td>strspn()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strstr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strtod()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strtof()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strtoimax()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strtok()</td>
<td></td>
<td>X</td>
<td>strtok() is not thread-safe. Should use strtok_r() instead which stores its state in a user-supplied buffer instead of using a static data area that may be overwritten by an unrelated call from another thread.</td>
</tr>
<tr class="odd">
<td>strtok_r()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strtol()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strtold()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strtoll()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strtoul()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strtoull()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strtoumax()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>strxfrm()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>strxfrm_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>swab()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>swprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>swscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>symlink()</td>
<td></td>
<td>X</td>
<td>This function is a security concern. A symbolic link references a fully qualified path through an alias. The path that the alias refers can be manipulated outside the service allowing for exploits.</td>
</tr>
<tr class="even">
<td>symlinkat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="odd">
<td>sync()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>sysconf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>syslog()</td>
<td></td>
<td>X</td>
<td>The implementation of system logs is implementation defined. Developers should use OMS defined logging facilities instead.</td>
</tr>
<tr class="even">
<td>system()</td>
<td></td>
<td>X</td>
<td>This function is a security concern. Also, there are certain conditions where the call is not thread-safe.</td>
</tr>
<tr class="odd">
<td>tan()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>tanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>tanh()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>tanhf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>tanhl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>tanl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>tcdrain()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>tcflow()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>tcflush()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>tcgetattr()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>tcgetpgrp()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>tcgetsid()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>tcsendbreak()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>tcsetattr()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>tcsetpgrp()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>tdelete()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>telldir()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>tempnam()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>tfind()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>tgamma()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>tgammaf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>tgammal()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>time()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>timer_create()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>timer_delete()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>timer_getoverrun()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>timer_gettime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>timer_settime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>times()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>timezone</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>tmpfile()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>tmpnam()</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX. Applications should use tmpfile instead.</td>
</tr>
<tr class="odd">
<td>toascii()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>tolower()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>tolower_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>toupper()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>toupper_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>towctrans()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>towctrans_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>towlower()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>towlower_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>towupper()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>towupper_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>trunc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>truncate()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>truncf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>truncl()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>tsearch()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>ttyname()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>ttyname_r()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>twalk()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>tzset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ulimit()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>umask()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>uname()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>ungetc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>ungetwc()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>unlink()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>unlinkat()</td>
<td></td>
<td>X</td>
<td>This function does not use a fully qualified path and is susceptible to potential exploits.</td>
</tr>
<tr class="even">
<td>unlockpt()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>unsetenv()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>uselocale()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>usleep()</td>
<td></td>
<td>X</td>
<td>Developers should use nanosleep() instead of usleep() because interactions between usleep() and certain other calls in POSIX, such as sleep() and nanosleep(), are considered undefined by the standard.</td>
</tr>
<tr class="even">
<td>utime()</td>
<td></td>
<td>X</td>
<td>This function modifies file access and modification times which is a security concern.</td>
</tr>
<tr class="odd">
<td>utimensat()</td>
<td></td>
<td>X</td>
<td>This function modifies file access and modification times which is a security concern.</td>
</tr>
<tr class="even">
<td>va_arg()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>va_copy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>va_end()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>va_start()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vdprintf()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>vfork</td>
<td></td>
<td>X</td>
<td>This function has been declared obsolete and may be removed from a future version of POSIX.</td>
</tr>
<tr class="even">
<td>vfprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>vfscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vfwprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>vfwscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>vscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vsnprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>vsprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vsscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>vswprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vswscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>vwprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>vwscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wait()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>waitid()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>waitpid()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcpcpy()</td>
<td></td>
<td>X</td>
<td>This function is susceptible to buffer overflows.</td>
</tr>
<tr class="odd">
<td>wcpncpy()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="even">
<td>wcrtomb()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcscasecmp()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>wcscasecmp_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>wcscat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcschr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcscmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcscoll()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcscoll_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>wcscpy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcscspn()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcsdup()</td>
<td></td>
<td>X</td>
<td>This function is susceptible for buffer overruns.</td>
</tr>
<tr class="odd">
<td>wcsftime()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcslen()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcsncasecmp()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>wcsncasemcp_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>wcsncat()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcsncmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcsncpy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcsnlen()</td>
<td></td>
<td>X</td>
<td>This function is restricted by PSE54.</td>
</tr>
<tr class="odd">
<td>wcsnrtombs()</td>
<td></td>
<td>X</td>
<td>This function is not thread-safe.</td>
</tr>
<tr class="even">
<td>wcspbrk()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcsrchr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcsrtombs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcsspn()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcsstr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcstod()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcstof()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcstoimax()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcstok()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcstol()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcstold()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcstoll()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcstombs()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcstoul()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcstoull()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wcstoumax()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcswidth()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>wcsxfrm()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wcsxfrm_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>wctob()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wctomb()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wctrans()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wctrans_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>wctype()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wctype_l()</td>
<td></td>
<td>X</td>
<td>The Locale family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="odd">
<td>wcwidth()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>wmemchr()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wmemcmp()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wmemcpy()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wmemmove()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>wmemset()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>wordexp()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result.</td>
</tr>
<tr class="even">
<td>wordfree()</td>
<td></td>
<td>X</td>
<td>The Terminal Device File family of functions are not expected to be used by OMS Services and are restricted as a result. Used in conjunction with wordexp() which is restricted.</td>
</tr>
<tr class="odd">
<td>wprintf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td>write()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>writev()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>wscanf()</td>
<td>X</td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td>y0()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="even">
<td>y1()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
<tr class="odd">
<td>yn()</td>
<td></td>
<td>X</td>
<td>This function is part of the XSI POSIX extension and is restricted as a result.</td>
</tr>
</tbody>
</table>

Acronyms and Symbols
====================

For the list of OMS acronyms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.

Glossary
========

For the glossary of terms, refer to the document OMSC-STD-002,
Abbreviations and Glossary.
