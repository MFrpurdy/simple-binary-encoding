Simple Binary Encoding (SBE)
============================

[![Javadocs](https://www.javadoc.io/badge/uk.co.real-logic/sbe-tool.svg)](https://www.javadoc.io/doc/uk.co.real-logic/sbe-tool)
[![Build Status](https://travis-ci.org/real-logic/simple-binary-encoding.svg?branch=master)](https://travis-ci.org/real-logic/simple-binary-encoding)
[![GitHub](https://img.shields.io/github/license/real-logic/simple-binary-encoding.svg)](https://github.com/real-logic/simple-binary-encoding/blob/master/LICENSE)
[![Code Quality: Java](https://img.shields.io/lgtm/grade/java/g/real-logic/simple-binary-encoding.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/real-logic/simple-binary-encoding/context:java)
[![Total Alerts](https://img.shields.io/lgtm/alerts/g/real-logic/simple-binary-encoding.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/real-logic/simple-binary-encoding/alerts)

[SBE](https://github.com/FIXTradingCommunity/fix-simple-binary-encoding) is an OSI layer 6 presentation for 
encoding and decoding binary application messages for low-latency financial applications. This repository contains 
the reference implementations in Java, C++, Golang, and C#.

Further details on the background and usage of SBE can be found on the
[Wiki](https://github.com/real-logic/simple-binary-encoding/wiki).

An XSD for SBE specs can be found
[here](https://github.com/real-logic/simple-binary-encoding/blob/master/sbe-tool/src/main/resources/fpl/sbe.xsd). Please address questions about the specification to the [SBE FIX community](https://github.com/FIXTradingCommunity/fix-simple-binary-encoding).

For the latest version information and changes see the [Change Log](https://github.com/real-logic/simple-binary-encoding/wiki/Change-Log) with **downloads** at [Maven Central](http://search.maven.org/#search%7Cga%7C1%7Csbe). 

The Java and C++ SBE implementations are designed with work very efficiently with the
[Aeron](https://github.com/real-logic/aeron) messaging system for low-latency and
high-throughput communications. The Java SBE implementation has a dependency on
[Agrona](https://github.com/real-logic/agrona) for its buffer implementations.


Binaries
--------
Binaries and dependency information for Maven, Ivy, Gradle, and others can be found at 
[http://search.maven.org](http://search.maven.org/#search%7Cga%7C1%7Csbe).

Example for Maven:

```xml
<dependency>
    <groupId>uk.co.real-logic</groupId>
    <artifactId>sbe-all</artifactId>
    <version>1.13.3</version>
</dependency>
```

Build
-----

The project is built with [Gradle](http://gradle.org/) using this [build.gradle](https://github.com/real-logic/simple-binary-encoding/blob/master/build.gradle) file.

Full clean build:

    $ ./gradlew

Run the Java examples

    $ ./gradlew runJavaExamples


Distribution
------------
Jars for the executable, source, and javadoc for the various modules can be found in the following directories:

    sbe-benchmarks/build/libs
    sbe-samples/build/libs
    sbe-tool/build/libs
    sbe-all/build/libs

An example to execute a Jar from command line using the 'all' jar which includes the Agrona dependency:

    java -Dsbe.generate.ir=true -Dsbe.target.language=Cpp -Dsbe.target.namespace=sbe -Dsbe.output.dir=include/gen -Dsbe.errorLog=yes -jar sbe-all/build/libs/sbe-all-1.13.4-SNAPSHOT.jar my-sbe-input.xml


C++ Build using CMake
---------------------
NOTE: Linux, Mac OS, and Windows only for the moment. See
[FAQ](https://github.com/real-logic/simple-binary-encoding/wiki/Frequently-Asked-Questions).
Windows builds have been tested with Visual Studio Express 12.

For convenience, a script is provided that does a full clean, build, and test of all targets as a Release build.

    $ ./cppbuild/cppbuild

If you are comfortable with using CMake, then a full clean, build, and test looks like:

    $ mkdir -p cppbuild/Debug
    $ cd cppbuild/Debug
    $ cmake ../..
    $ cmake --build . --clean-first
    $ ctest

__Note__: A C generator is included with the C++ build. And is built with the C++ build. Currently, the C generator is a work
in progress.

Golang Build
------------

First build using Gradle to generate the SBE jar and then use it to
generate the golang code for testing

    $ ./gradlew
    $ ./gradlew generateGolangCodecs

For convenience on Linux, a gnu Makefile is provided that runs some
tests and contains some examples

    $ cd gocode
    # make # test, examples, bench

Users of golang generated code should see the [user
documentation](https://github.com/real-logic/simple-binary-encoding/wiki/Golang-User-Guide).

Developers wishing to enhance the golang generator should see the [developer
documentation](https://github.com/real-logic/simple-binary-encoding/blob/master/gocode/README.md)


C# Build
--------
Users of CSharp generated code should see the [user documentation](https://github.com/real-logic/simple-binary-encoding/wiki/Csharp-User-Guide).

Developers wishing to enhance the CSharp generator should see the [developer documentation](https://github.com/real-logic/simple-binary-encoding/blob/master/csharp/README.md)


License (See LICENSE file for full license)
-------------------------------------------
Copyright 2013-2019 Real Logic Limited  
Copyright 2017 MarketFactory Inc

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
