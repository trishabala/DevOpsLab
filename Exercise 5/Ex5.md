# DevOps Lab - Trisha Balakrishnan

## Exercise 7

### Creating and Managing a Java Project Manually and with Maven

### 1. Creating a Java Project (Without Maven)

1. **Open Terminal** on your laptop.

   ![1-1](../Photos/Ex5/1-1.png?raw=true)

3. Navigate to your desired directory:

   ```bash
   cd path/to/your/directory
   ```

4. Create a new directory for your Java project:

   ```bash
   mkdir MyJavaProject
   cd MyJavaProject
   ```

   ![1-3](../Photos/Ex5/1-3.png?raw=true)

5. Create the necessary directory structure for a Java project:

   ```bash
   mkdir -p src/main/java/com/example
   ```

   ![1-4](../Photos/Ex5/1-4.png?raw=true)

6. Create a simple Java class inside the `src/main/java/com/example` directory:

   ```bash
   nano src/main/java/com/example/App.java
   ```

   ![1-5](../Photos/Ex5/1-5.png?raw=true)

   Add the following code to the file:

   ```java
   package com.example;

   public class App {
       public static void main(String[] args) {
           System.out.println("Hello, World!");
       }
   }
   ```

   Save the file and exit the editor.

### 2. Packaging the Project with Dependencies (Without Maven)

1. If you need external libraries (dependencies), you'll have to download the JAR files manually and include them in your project. For example, download a library like `commons-lang3` from [Apache Commons](https://commons.apache.org/proper/commons-lang/download_lang.cgi).

2. Place the downloaded JAR files in a `lib` directory within your project:

   ```bash
   mkdir lib
   cp path/to/commons-lang3-3.12.0.jar lib/
   ```

   ![2-2](../Photos/Ex5/2-2.png?raw=true)

3. Compile the project with the dependencies:

   ```bash
   javac -cp lib/commons-lang3-3.12.0.jar -d . src/main/java/com/example/App.java
   ```

   ![2-3](../Photos/Ex5/2-2.png?raw=true)

### 3. Compiling and Building the JAR File Manually (Artifact 1 without Maven)

1. **Create a Manifest File:**

   Create a `manifest.txt` file:

   ```bash
   echo "Main-Class: com.example.App" > manifest.txt
   ```

   ![3-1](../Photos/Ex5/3-1.png?raw=true)

2. **Package the JAR File:**

   Use the `jar` command to package the compiled classes and the manifest file into a JAR:

   ```bash
   jar cvfm MyJavaProject.jar manifest.txt com/example/*.class -C lib .
   ```

   ![3-2](../Photos/Ex5/3-2.png?raw=true)

3. **Verify the JAR File:**

   Check that the JAR file has been created successfully:

   ```bash
   ls MyJavaProject.jar
   ```

   ![3-3](../Photos/Ex5/3-3.png?raw=true)

4. **Run the JAR File:**

   To run your JAR file, use:

   ```bash
   java -cp MyJavaProject.jar:lib/commons-lang3-3.12.0.jar com.example.App
   ```

   ![3-4](../Photos/Ex5/3-4.png?raw=true)

### 4. Checking Your Installed Maven Version

1. Now that you've manually built the project, check your Maven version:

   ```bash
   mvn -v
   ```

   ![4-1](../Photos/Ex5/4-1.png?raw=true)

### 5. Creating `pom.xml`

1. **Initialize the Maven Project:**

   Move your project to a Maven structure:

   ```bash
   mvn archetype:generate -DgroupId=com.example -DartifactId=MyJavaProject -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
   ```

   ![5-1](../Photos/Ex5/5-1.png?raw=true)

2. **Copy Your Files** into the newly generated Maven structure.

3. **Add Dependencies** in the `pom.xml`:

   ```xml
   <dependencies>
       <dependency>
           <groupId>org.apache.commons</groupId>
           <artifactId>commons-lang3</artifactId>
           <version>3.12.0</version>
       </dependency>
   </dependencies>
   ```

   ![5-3](../Photos/Ex5/5-3.png?raw=true)

### 6. Executing the Clean Lifecycle

1. Run the `clean` lifecycle in Maven:

   ```bash
   mvn clean
   ```

   ![6-1](../Photos/Ex5/6-1.png?raw=true)

2. Verify that the `target` directory and its contents are removed:

   ```bash
   ls target/
   ```

   ![6-2](../Photos/Ex5/6-2.png?raw=true)

### 7. Exploring Plugins and Goals Associated with `clean`

1. Explore the plugins and goals associated with the `clean` lifecycle:

   ```bash
   mvn help:describe -Dcmd=clean
   ```

   ![7-1](../Photos/Ex5/7-1.png?raw=true)

2. Review the output to understand the available goals and plugins.
