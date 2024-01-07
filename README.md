![Json-Java logo](https://github.com/stleary/JSON-java/blob/master/images/JsonJava.png?raw=true)

<sub><sup>image credit: Ismael Pérez Ortiz</sup></sub>


JSON in Java [package org.json]
===============================

[![Java CI with Maven](https://github.com/openworld42/JSON-Java-Plus/actions/workflows/pipeline.yml/badge.svg)](https://github.com/openworld42/JSON-Java-Plus/actions/workflows/pipeline.yml)
[![CodeQL](https://github.com/openworld42/JSON-Java-Plus/actions/workflows/codeql-analysis.yml/badge.svg)](https://github.com/openworld42/JSON-Java-Plus/actions/workflows/codeql-analysis.yml)

**[Click here if you just want the latest release jar file.](https://search.maven.org/remotecontent?filepath=org/json/json/20231013/json-20231013.jar)**


# Overview

[JSON](http://www.JSON.org/) is a light-weight language-independent data interchange format.

The JSON-Java-Plus package is a fork of [JSON-Java](https://github.com/stleary/JSON-java), which is a reference implementation that demonstrates how to parse JSON documents into Java objects and how to generate new JSON documents from the Java classes.

Therefore, all credits, kudos and attribution goes to the authors, contributors and maintainers of JSON-Java.

**Why is this fork exiting, and what are the advantages and differences compared to JSON-Java:**
* JSON-Java has only basic support for using JSON objects and JSON arrays to store information in files (there is only the
natural order of HashMap for JSON object keys, which creates a somewhat chaotic arrangement of the output, making it difficult
to store, administer and observe the information within these output files)
* Since JSON is widely used and one of the shortest format to store or distribute information, there is a need for 
support to store information as JSON objects in files (several applications do that already)
* JSON-Java is easy to use and the integration in a Java project is straightforward
* An attempt to contribute to JSON-Java, not breaking any previous behavior, together with some code analysis, suggestions and discussion,
failed ("However, the RFC states that objects are unordered, and as a reference app, JSON-Java tries to follow the spec. You have the right idea to fork the repo and make changes that are suitable for your application." Details can be found [here](https://github.com/stleary/JSON-java/issues/822))
* The [RFC](https://datatracker.ietf.org/doc/html/rfc8259) defines "An object is an unordered collection of zero or more name/value
pairs". This is a true definition for JSON input, but never for writing JSON output. There is always an algorithm behind writing, and, by nature, the order is defined by the algorithm - in JSON-Java the natural order of a keyset of a HashMap, dependent on the capacity dependent behavior of the HashMap bin insertion. In short, true JSON output can use any order, so why not use the order of insertion respectively the order of a JSON input file to make the output human-readable.
* There are other issues for writing JSON files: line breaks and formatting (imagine large JSON arrays), according to the definition of JSON resulting in valid JSON output.

Project goals include:
* Stay as close to JSON-Java as possible, with the above enhancements
* Reliable and consistent results
* Adherence to the JSON specification 
* Easy to build, use, and include in other projects
* No external dependencies
* Fast execution and low memory footprint
* Maintain backward compatibility
* Designed and tested to use on Java versions 1.8 - 21


The files in this package implement JSON encoders and decoders. The package can also convert between JSON and XML, HTTP headers, Cookies, and CDL (comma delimited text, CSV).

# If you would like to contribute to this project

For more information on contributions, please see [CONTRIBUTING.md](https://github.com/openworld42/JSON-Java-Plus/blob/master/docs/CONTRIBUTING.md)

Bug fixes, code improvements, and unit test coverage changes are welcome! Because this project is currently in the maintenance phase, the kinds of changes that can be accepted are limited. For more information, please read the [FAQ](https://github.com/openworld42/JSON-Java-Plus/wiki/FAQ).

# Build Instructions

The org.json package can be built from the command line, Maven, and Gradle. The unit tests can be executed from Maven, Gradle, or individually in an IDE e.g. Eclipse.
 
**Building from the command line**

*Build the class files from the package root directory src/main/java*
```shell
javac org/json/*.java
```

*Create the jar file in the current directory*
```shell
jar cf json-java.jar org/json/*.class
```

*Compile a program that uses the jar (see example code below)*
```shell
javac -cp .;json-java.jar Test.java (Windows)
javac -cp .:json-java.jar Test.java (Unix Systems)
```

*Test file contents*

```java
import org.json.JSONObject;
public class Test {
    public static void main(String args[]){
       JSONObject jo = new JSONObject("{ \"abc\" : \"def\" }");
       System.out.println(jo);
    }
}
```

*Execute the Test file*
```shell 
java -cp .;json-java.jar Test (Windows)
java -cp .:json-java.jar Test (Unix Systems)
```

*Expected output*

```json
{"abc":"def"}
```

 
**Tools to build the package and execute the unit tests**

Execute the test suite with Maven:
```shell
mvn clean test
```

Execute the test suite with Gradlew:

```shell
gradlew clean build test
```

# Notes

For more information, please see [NOTES.md](https://github.com/openworld42/JSON-Java-Plus/blob/master/docs/NOTES.md)

# Files

For more information on files, please see [FILES.md](https://github.com/openworld42/JSON-Java-Plus/blob/master/docs/FILES.md)

# Release history:

For the release history, please see [RELEASES.md](https://github.com/openworld42/JSON-Java-Plus/blob/master/docs/RELEASES.md)
