# Static Code Analyzer

This project is a static code analyzer that performs statistical analysis on object-oriented applications. It allows users to analyze their Java projects by providing metrics and insights into the code's structure and functionality.

## Requirements

* OpenJDK 11 or higher

## Installing OpenJDK 11

If you don't already have OpenJDK installed, you can install it by running:

```bash
sudo apt install openjdk-11-jdk
```

After installation, verify that it's installed by running:

```bash
java -version
```

## Project Setup

### 1. Downloading the Project

You can download the project from the GitHub repository as a `.zip` file. Extract it to your desired location.

## Running the Analyzer

Once the project is set up, you can run the analyzer using the pre-built JAR file.

### 1. Running the Analyzer

Navigate to the directory where the `static-analyzer-0.0.1.jar` file is located, then run the following command:

```bash
java -jar static-analyzer-0.0.1.jar
```

### 2. Enter Project Path

You will be prompted to enter the project path. You can use the sample calculator project located in `/resources/calculator-app/src` by copying and pasting this path into the prompt.

```bash
The project path you want to work on it (src path) :  /resources/calculator-app/src
```

### 3. Enter JDK Path

Next, you will be prompted to provide the JDK path for your environment. You can retrieve this path by running the following command in your terminal:

```bash
echo $JAVA_HOME
```

Copy the output and paste it into the analyzer prompt.

```bash
JDK path : /path/to/your/jdk
```

### 4. View the Analysis Results

Once the paths are provided, the analyzer will start analyzing the project and output the results, including statistical metrics on the object-oriented design and structure of your Java application.