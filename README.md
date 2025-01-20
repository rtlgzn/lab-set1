# Lab 1: Code Reading and Tool Modification

## Code Reading

### Selected Projects
1. [NAnt](https://github.com/nant/nant)
2. [Apache Ant](https://github.com/apache/ant)

### Questions and Answers

1. **List of files examined and explanation:**
   - **NAnt:**
     - `CommandLineBuilder.cs` — Handles command-line arguments. Chosen for its relevance to argument processing.
     - `Program.cs` — Entry point of the program; processes arguments passed from the command line.
   - **Ant:**
     - `CommandLineParser.java` — Responsible for parsing command-line arguments.
     - `Main.java` — Entry point of the program; invokes methods from `CommandLineParser`.

2. **First impressions:**
   - **NAnt:** Clear structure, readable code, but limited comments for error handling.
   - **Ant:** Slightly more complex due to Java’s formal syntax, with multiple nested classes.

3. **Code organization:**
   - **NAnt:**
     - **Method level:** Handled in `CommandLineBuilder`.
     - **Class level:** `CommandLineBuilder` processes and organizes argument parsing.
     - **Project level:** `Program.cs` invokes the parsing methods.
   - **Ant:**
     - **Method level:** Processed in `parseArguments()` in `CommandLineParser`.
     - **Class level:** `CommandLineParser` manages argument parsing.
     - **Project level:** `Main` coordinates parsed arguments for execution.

4. **Invalid filenames handling:**
   - **NAnt:** Throws `ArgumentException` with an error message.
   - **Ant:** Uses `try-catch` with `IllegalArgumentException` for error logging.

5. **Two similarities:**
   - Both projects isolate argument parsing into dedicated classes.
   - Arguments flow from the entry point to specialized parsers.

6. **Two differences:**
   - NAnt uses C#, while Ant uses Java, affecting syntax and design patterns.
   - NAnt throws exceptions directly, while Ant logs errors and processes them in `Main`.

---
