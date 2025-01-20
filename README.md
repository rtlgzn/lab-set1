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

[Video Link](https://your-video-link)

---

## Git Repository
Ensure the repository contains:
1. **Original Commit:** The unmodified NAnt source files.
2. **Modified Commit:** The updated source code with the `--ari` flag.

[GitHub Repository](https://github.com/rtlgzn/lab1-nant)
