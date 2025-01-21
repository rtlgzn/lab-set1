# Lab 1: Code Reading and Tool Modification

## Objectives
- Learn to read source code.
- Understand the basics of OBS Studio (or another video capture software).
- Modify an open-source project by adding a custom flag and verifying its functionality.

---

## Code Reading (15 Marks)

### Selected Projects
1. [NAnt](https://github.com/nant/nant)
2. [Apache Ant](https://github.com/apache/ant)

### Questions and Answers

1. **List of files examined and explanation:**
   - **NAnt:**
     - `CommandLineBuilder.cs`: Handles command-line arguments. This file was chosen for its role in argument processing.
     - `Program.cs`: The program's entry point, where command-line arguments are parsed and processed.
   - **Ant:**
     - `CommandLineParser.java`: Responsible for parsing command-line arguments in Ant. Selected for its core role in argument handling.
     - `Main.java`: Entry point of the program, which invokes methods from `CommandLineParser`.

2. **First impressions:**
   - **NAnt:** The code is structured and readable. However, there are limited comments for error handling.
   - **Ant:** Slightly more complex due to Java's verbose syntax, with nested classes and extensive method chaining.

3. **Code organization:**
   - **NAnt:**
     - **Method level:** Argument processing occurs in `Parse()` in `CommandLineBuilder`.
     - **Class level:** `CommandLineBuilder` encapsulates argument processing logic.
     - **Project level:** `Program.cs` coordinates argument parsing and program execution.
   - **Ant:**
     - **Method level:** `parseArguments()` in `CommandLineParser` handles command-line arguments.
     - **Class level:** `CommandLineParser` is the central class for parsing logic.
     - **Project level:** `Main.java` serves as the entry point and integrates parsed arguments into the program's execution.

4. **How are invalid filenames handled?**
   - **NAnt:** Throws an `ArgumentException` with an appropriate error message.
   - **Ant:** Uses a `try-catch` block to handle `IllegalArgumentException`, logging the error before exiting gracefully.

5. **Two similarities:**
   - Both projects isolate argument parsing into dedicated classes for modularity.
   - Arguments flow from the entry point (e.g., `Program.cs` or `Main.java`) to specialized parsing methods.

6. **Two differences:**
   - **Language:** NAnt is written in C#, while Ant uses Java, resulting in different syntax and patterns.
   - **Error Handling:** NAnt uses direct exceptions, whereas Ant logs errors and processes them in `Main`.

---

## Tool Modification (5 Marks)

### Selected Tool for Modification
- **NAnt**

### Steps

1. **Build the Tool:**
   - Navigate to the root folder of the NAnt source files.
   - Build the tool using a C# compiler or your development environment.

2. **Create a "Hello World" Program:**
   - **Source File:** `hello.cs`
     ```csharp
     using System;
     class HelloWorld {
         static void Main() {
             Console.WriteLine("Hello, World!");
         }
     }
     ```
   - **Build File:** `build.xml`
     ```xml
     <project name="HelloWorld" default="build">
         <target name="build">
             <csc target="exe" output="hello.exe">
                 <sources>
                     <include name="hello.cs"/>
                 </sources>
             </csc>
         </target>
     </project>
     ```

3. **Add a Custom Flag:**
   - Modify `CommandLineBuilder.cs` to include:
     ```csharp
     if (args.Contains("--ari")) {
         Console.WriteLine("BTP605 - Ari");
     }
     ```
   - Modify `Program.cs` to invoke this logic after parsing:
     ```csharp
     static void Main(string[] args) {
         CommandLineBuilder builder = new CommandLineBuilder(args);
         builder.Parse();

         // Custom flag logic
         if (args.Contains("--ari")) {
             Console.WriteLine("BTP605 - Ari");
         }
     }
     ```

4. **Rebuild the Tool:**
   - Rebuild the project with the modified code.

5. **Test the Tool:**
   - Run the tool without the custom flag:
     ```bash
     nant
     ```
   - Run the tool with the `--ari` flag:
     ```bash
     nant --ari
     ```
   - Verify that it outputs:
     ```
     BTP605 - Ari
     ```

---

## Video Demonstration
Include a walkthrough video showing:
1. The repository structure.
2. Building and running the Hello World program without the `--ari` flag.
3. Building and running the Hello World program with the `--ari` flag.
4. A walkthrough of the changes made to the source code.

[Video Link](https://youtu.be/KC2FXf6sMOc)

---

## Git Repository
Ensure the repository contains:
1. **Original Commit:** The unmodified NAnt source files.
2. **Modified Commit:** The updated source code with the `--ari` flag.

[GitHub Repository](https://github.com/rtlgzn/lab1-nant)
