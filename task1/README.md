# Lab 1 - Java Calculator with Gradle

## Overview
This project is a simple Java Calculator application built using **Gradle**. It demonstrates how to build, test, and package a Java application using Gradle.

## Features
- Basic calculator operations:
  - Addition
  - Subtraction
  - Multiplication
  - Division
- Unit testing with JUnit 5
- Executable JAR generation

## Project Structure

```
task1/
├── src/
│   ├── main/
│   │   └── java/
│   └── test/
│       └── java/
├── build.gradle
├── settings.gradle
└── README.md
```

## Prerequisites

- Java 17 or later
- Gradle 7+ (or newer)

Verify installations:

```bash
java -version
gradle -v
```

## Clone the Repository

```bash
git clone https://github.com/nadadew20/Ivolve-tasks.git
cd Ivolve-tasks/task1
```

## Run Unit Tests

```bash
gradle test
```

## Build the Project

```bash
gradle build
```

## Run the Application

```bash
java -jar build/libs/calculator.jar
```

## Clean the Project

```bash
gradle clean
```

## Technologies Used

- Java 17
- Gradle
- JUnit 5

## Author

**Nada Hamdallah**
