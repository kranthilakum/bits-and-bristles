---
title: "Translation"
date: 2020-09-10T09:55:46+05:30
draft: false
categories:
- "translation"
tags:
- "programming"
- "translation"
---

### i18n

Internationalization (i18n) is the process of designing a software application so that it can be adapted to various languages and regions without engineering changes. Localization (l10n) is the process of adapting internationalized software for a specific region or language by adding locale-specific components and translating text.

“i18n” is a numeronym where “18” represents the number of letters between the first letter (“I”) and the last letter (“N”) in the word “internationalization”. As you develop applications, you may also encounter “a11y” which is a numeronym for accessibility.

### Localization

Localization is the process of adapting internationalized software for a specific region or language by adding locale-specific components and translating text.


### Locale

A locale is a set of parameters that defines the user's language, region and any special variant preferences that the user wants to see in their user interface. Usually a locale identifier consists of at least a language identifier and a region identifier.

### RTL

Right-to-left (RTL) is a property of a language script in which the text is written from right to left. Languages that use this property include Arabic, Hebrew, Persian, Urdu, Yiddish, etc.

### LTR

Left-to-right (LTR) is a property of a language script in which the text is written from left to right. Languages that use this property include English, French, German, Spanish, etc.

### Unicode

Unicode is a computing industry standard for the consistent encoding, representation, and handling of text expressed in most of the world's writing systems. The standard is maintained by the Unicode Consortium, and as of March 2020, there is a total of 143,859 characters, with Unicode 13.0 (these characters consist of 143,696 graphic characters and 163 format characters) covering 154 modern and historic scripts, as well as multiple symbol sets and emoji.

### UTF-8

UTF-8 is a variable-width character encoding used for electronic communication. Defined by the Unicode Standard, the name is derived from Unicode (or Universal Coded Character Set) Transformation Format – 8-bit. UTF-8 is capable of encoding all 1,112,064 valid character code points in Unicode using one to four one-byte (8-bit) code units. Code points with lower numerical values, which tend to occur more frequently, are encoded using fewer bytes. It was designed for backward compatibility with ASCII and to avoid the complications of endianness and byte order marks in UTF-16 and UTF-32.

### UTF-16

UTF-16 (16-bit Unicode Transformation Format) is a character encoding capable of encoding all 1,112,064 valid code points of Unicode. The encoding is variable-length, as code points are encoded with one or two 16-bit code units (also see comparison of Unicode encodings for a comparison of UTF-8, -16 & -32).

### UTF-32

UTF-32 (32-bit Unicode Transformation Format) is a fixed-length encoding used to encode Unicode code points that uses exactly 32 bits (four bytes) per Unicode code point (but a number of leading bits must be zero as there are far fewer than 2^32 Unicode code points). UTF-32 is a fixed-length encoding, in contrast to all other Unicode transformation formats, which are variable-length encodings. Each 32-bit value in UTF-32 represents one Unicode code point and is exactly equal to that code point's numerical value. UTF-32 is not widely used because its fixed length requires more space, and thus bandwidth, than UTF-8 and UTF-16 in many cases, and because many applications do not yet support it.

### ASCII

ASCII (American Standard Code for Information Interchange) is a character encoding standard for electronic communication. ASCII codes represent text in computers, telecommunications equipment, and other devices. Most modern character-encoding schemes are based on ASCII, although they support many additional characters.

### ISO-8859

ISO/IEC 8859 is a joint ISO and IEC series of standards for 8-bit character encodings. The series of standards consists of numbered parts, such as ISO/IEC 8859-1, ISO/IEC 8859-2, etc. There are 15 parts, excluding the abandoned ISO/IEC 8859-12. The ISO working group maintaining this series of standards has been disbanded.

ISO/IEC 8859 parts 1, 2, 3, and 4 were originally Ecma International standard ECMA-94.

### BCP47

BCP 47 is a code used to tag language in a way that is useful for computer processing. BCP stands for "Best Current Practice". The BCP 47 standard was published by IETF as RFC 5646 in September 2009, which obsoletes RFC 4646 from September 2006. It offers a uniform way for applications to define language tags for identifying the language content. It also provides a mechanism to register new language tags.

### ICU syntax

ICU is a mature, widely used set of C/C++ and Java libraries providing Unicode and Globalization support for software applications. ICU is widely portable and gives applications the same results on all platforms and between C/C++ and Java software.

ICU syntax is a syntax for specifying locale identifiers. It is used in the Unicode Common Locale Data Repository (CLDR) project, and by extension in the ICU library.

### CLDR

The Unicode Common Locale Data Repository (CLDR) is a project of the Unicode Consortium to provide locale data in the XML format for use in computer applications. CLDR contains locale-specific information, including the native names for scripts, languages, and countries, as well as calendar data and number and currency formatting for the languages represented in the library.