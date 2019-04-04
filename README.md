# cs1302-ce25 - Applications of Recursion

This class exercise futher explores the concept of [recursion](https://github.com/cs1302uga/cs1302-ce25).

## References and Prerequisites

* [`java.io.File` API Documentation](https://docs.oracle.com/javase/8/docs/api/java/io/File.html)
* [`CSCI 1302 Recursion Tutorial`](https://github.com/cs1302uga/cs1302-tutorials/blob/master/recursion.md)

## Questions

In your notes, clearly answer the following questions. These instructions assume that you are 
logged into the Nike server. 

**NOTE:** If a step requires you to enter in a command, please provide in your notes the full 
command that you typed to make the related action happen. If context is necessary (e.g., the 
command depends on your present working directory), then please note that context as well.

### Getting Started

1. Using Maven, create a project directory for this exercise called `cs1302-ce25` with a primary 
   package called `cs1302.ce25`.

1. Change into the `cs1302-ce25` directory that you just created using Maven, then do the
   following:
   
   1. Initialize a new Git repository:
      
      ```
      $ git init
      ```
      
   1. Create a [`.gitignore`](https://git-scm.com/docs/gitignore) (hidden file) with the following contents:
   
      ```
      bin/
      doc/
      target/
      *.class
      hs_err_pid*
      *~
      \#*\#
      core.*
      ```
      
      Add and commit the `.gitignore` file to the repository.
      
   1. Update the POM so that the project works with Java 8. After that, add and commit the `pom.xml` file to 
      the repository.
   
   1. Delete the Maven-generated driver (i.e., `src/main/java/cs1302/ce25/App.java`) and the unit test files 
      (i.e., everything under `src/test/java`). We won't add the `src` folder to the repository at this time
      because it only contains empty subdirectories. Git will not track empty directories.
   
## Exercise Steps

1. For this checkpoint, you will implement your own version of the Unix `find` command.
   Here is an example:
   
   ```
   $ find src
   ```
   
   ```
   src
   src/main
   src/main/java
   src/main/java/cs1302
   src/main/java/cs1302/ce25
   src/main/java/cs1302/ce25/Find.java
   ```
   
1. Create a `cs1302.ce25.Find` class based on code below that provides some
   starter code for your recursive implementation of the Unix `find` command:

   ```java
   public class Find {
   
       public static void printFile(File file) {
           // TODO implement printFile
       } // printFile
    
       public static void main(String[] args) {
           if (args.length == 0) {
               args = new String[] { "." }; // default to "."
           } // if
           // TODO implement stream code
       } // main

   } // Find
   ```
   
   Before this code will compile, you will need to manually setup the package 
   statement and imports.
    
1. **Next, use Maven to compile and run the code.** You won't see any output at
   this point. Please use the `exec:java` phase to run. To provide command-line
   arguments to your program through maven, you will need to specify the 
   command-line arguments as a space-separated
   string with the `-Dexec.args` option (e.g., `-Dexec.args="src target"`) in 
   addition to providing the `-Dexec.mainClass` option. 
   
   * Once you figure out how to run it, please write down that command
     in your notes.
   
   * After you've confirmed that it compiles and runs, please add and commit
     your changes to the repository.

1. Use a stream to map all of the command-line arguments in the `main` method 
   to new [`File`](https://docs.oracle.com/javase/8/docs/api/java/io/File.html)
   objects, then call `printFile` for-each of them. For testing 
   purposes, you may want to put some kind of print statement in the `printFile` method.
   After verifying that your code compiles and works using Maven, 
   please add and commit `Find.java`.
   
1. Implement the `printFile` method. 

   1. If the file or directory denoted by the `File` object does not exists, then
      print an error similar to the following to standard error where `%s` denotes
      the pathname string for the `File` object:
      
      ```
      find: `%s': No such file or directory
      ```
      
   1. the file or directory denoted by the `File` object does exist, print the 
      pathname string for the `File` objectc to standard output. Additionally,
      if the `File` object refers to a directory, then **use recusion** to do the 
      same for all files in the directory. For this part, you may use a stream or a 
      for-each loop.
      
   After verifying that your code compiles and works using Maven, 
   please stage and commit your changes to the repository.

**CHECKPOINT**

1. For this checkpoint, adapt your `Find.java` code to create a 
   `cs1302.ce25.Tree` class that provides a recursive implementation of the 
   Unix [`Tree`](https://en.wikipedia.org/wiki/Tree_(command)) command. 
   Here is an example:
   
   ```
   $ tree src
   ```
   
   ```
   |---src
   |   |---main
   |   |   |---java
   |   |   |   |---cs1302
   |   |   |   |   |---ce25
   |   |   |   |   |   |---Find.java
   |   |   |   |   |   |---Tree.java
   ```
   
   ```
   $ tree src/main/java
   ```
   
   ```
   |---java
   |   |---cs1302
   |   |   |---ce25
   |   |   |   |---Find.java
   |   |   |   |---Tree.java
   ```
   
   Remember, you can add additional parameters to methods, as needed, to
   help you accomplish a given sub-problem.
   
1. **Next, use Maven to compile and run the code.** Please use the `exec:java` phase to run.
   You will need to specify the command-line arguments as a space-separated
   string with the `-Dexec.args` option (e.g., `-Dexec.args="src"`) in addition
   to providing the `-Dexec.mainClass` option. 
   
   * Once you figure out how to run it, please write down that command
     in your notes.
   
   * After you've confirmed that it compiles and runs, please add and commit
     your changes to the repository.

**CHECKPOINT**

1. For this checkpoint, you will implement a recursive method called `shrinkString`.
   Create a `cs1302.ce25.ShrinkString` class that contains a `main` method as well
   as the following method:
   
   ```java
   public static String shrinkString(String str)
   ```

   Given a string, return recursively a "shrinked" string where adjacent characters 
   that are the same have been reduced to a single character. 
   Here are some examples:

   | Example                   | Result  |
   |---------------------------|---------|
   | `shrinkString("yyzzza")`  | `"yza"` |
   | `shrinkString("abbbcdd")` | `"abcd" |
   | `shrinkString("Hello")`   | `"Helo" |
   | `shrinkString("abcd")`    | `"abcd" |
   | `shrinkString("  ")`      | `" "`   |
   | `shrinkString("")`        | `""`    |
   
   In the `main` method, create an array of strings that contains the strings used in the
   eamples above. Next, create another method called `printShrunkString` with the
   following signature:
   
   ```java
   public static printShrunkStrings(String[] array, int i)
   ```
   
   Given an `array` and an index `i`, print the result of calling `shrinkString`
   on the element at index `i`, then recursively print the remaining elements. You
   may assume the first call provides a valid index `i`. You may not assume
   the array is non-empty.
   
   In the `main` method, use your `printShrunkString` method to print the result 
   of calling `shrinkString` on each element of the array.
   
1. **Use Maven to compile and run the code.** Please use the `exec:java` phase to run.
   You will need to specify the command-line arguments as a space-separated
   string with the `-Dexec.args` option (e.g., `-Dexec.args="src"`) in addition
   to providing the `-Dexec.mainClass` option. 
   
   * Once you figure out how to run it, please write down that command
     in your notes.
   
   * After you've confirmed that it compiles and runs, please add and commit
     your changes to the repository.

**CHECKPOINT**

<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
