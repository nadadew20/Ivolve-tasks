# Lab 2 - Building and Packaging Java Application with Maven

## Objective

Build and package a Java application using Apache Maven.

---

## Requirements

- Java JDK
- Apache Maven
- Git

---

## Steps

### 1. Install Maven

```bash
sudo apt update
sudo apt install maven -y
```

Verify the installation:

```bash
mvn -version
```

---

### 2. Clone the Repository

```bash
git clone https://github.com/Ibrahim-Adel15/calculator-maven.git
cd calculator-maven
```

---

### 3. Run Unit Tests

```bash
mvn test
```

Expected result:

```
BUILD SUCCESS
```

---

### 4. Build the Application

```bash
mvn clean package
```

Expected result:

```
BUILD SUCCESS
```

The generated artifact will be located at:

```
target/calculator.jar
```

> Depending on the project configuration, the JAR file may include a version number (e.g., `calculator-1.0.jar`).

---

### 5. Run the Application

```bash
java -jar target/calculator.jar
```

or

```bash
java -jar target/*.jar
```

---

### 6. Verify

Verify that:

- Unit tests pass successfully.
- The project builds without errors.
- The JAR file is generated in the `target` directory.
- The application runs successfully.

---

## Project Structure

```
lab2/
├── pom.xml
├── src/
├── target/
│   └── calculator.jar
└── README.md
```

---

## Technologies Used

- Java
- Apache Maven
- Git
- GitHub

---

## Author

**Nada Hamdallah**
