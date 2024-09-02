# DevOps Lab - Trisha Balakrishnan

## Exercise 4

### 1. Setting Up a Java Application

1. **Create a New Java Project:**

   In your terminal, navigate to your workspace and create a new directory for your project:

   ```bash
   mkdir MyJavaApp
   cd MyJavaApp
   ```

2. **Initialize a Git Repository:**

   Inside the `MyJavaApp` directory, initialize a new Git repository:

   ```bash
   git init
   ```

3. **Create a Simple Java Application:**

   Create a basic Java application:

   ```bash
   mkdir -p src/main/java/com/trisha/app
   touch src/main/java/com/trisha/app/App.java
   ```

   Edit the `App.java` file to include a simple `Hello, World!` program:

   ```java
   package com.trisha.app;

   public class App {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }
   ```
   ![1-3](../Photos/Ex4/1-3.png?raw=true)
   
4. **Push the Project to GitHub:**

   Create a repository on GitHub named `MyJavaApp` and push your local project to GitHub:

   ```bash
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/trishabala/MyJavaApp.git
   git branch -M main
   git push -u origin main
   ```
   ![1-4](../Photos/Ex4/1-4.png?raw=true)

### 2. Creating a POM File and Experimenting with Inheritance and Aggregation

1. **Create a `pom.xml` File:**

   In the root directory of your project, create a `pom.xml` file to manage your Java project’s dependencies and build configuration:

   ```bash
   touch pom.xml
   ```

   Edit the `pom.xml` to include basic project information:

   ```xml
   <project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
       <modelVersion>4.0.0</modelVersion>

       <groupId>com.trisha</groupId>
       <artifactId>MyJavaApp</artifactId>
       <version>1.0-SNAPSHOT</version>

       <dependencies>
           <!-- Add dependencies here -->
       </dependencies>
   </project>
   ```

2. **Experiment with Inheritance:**

   Create a parent POM file if you plan to manage multiple projects with shared configurations. For example, create a `parent-pom.xml`:

   ```xml
   <project xmlns="http://maven.apache.org/POM/4.0.0">
       <modelVersion>4.0.0</modelVersion>
       <groupId>com.trisha</groupId>
       <artifactId>parent-project</artifactId>
       <version>1.0</version>
       <packaging>pom</packaging>

       <modules>
           <module>MyJavaApp</module>
       </modules>
   </project>
   ```

3. **Experiment with Aggregation:**

   In your `pom.xml`, you can define modules if you are managing multiple projects. For example, if you have multiple Java projects, you can add them as modules in a parent `pom.xml`:

   ```xml
   <modules>
       <module>MyJavaApp</module>
       <!-- Add other modules here -->
   </modules>
   ```

### 3. Running and Building the Project

1. **Compile the Project:**

   Use Maven to compile your project:

   ```bash
   mvn compile
   ```
   ![3-1](../Photos/Ex4/3-1.png?raw=true)

2. **Run the Java Application:**

   Run your Java application using Maven:

   ```bash
   mvn exec:java -Dexec.mainClass="com.trisha.app.App"
   ```

3. **Package the Application:**

   Create a packaged JAR file of your application:

   ```bash
   mvn package
   ```
   ![3-3](../Photos/Ex4/3-3.png?raw=true)

