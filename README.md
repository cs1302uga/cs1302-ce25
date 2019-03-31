# cs1302-ce25

> TODO QUOTE

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
   package called `cs1302.ce54`.

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
      
   1. Update the POM so that the project works with Java 8. After that, use Git to track the `pom.xml`, 
      then commit it to the repository, then add and commit the `pom.xml` file to the repository.
   
   1. Delete the Maven-generated driver (i.e., `src/main/java/cs1302/ce25/App.java`) and the unit test files 
      (i.e., everything under `src/test/java`). Finally, add and commit the `src` directory to the repository.
   
## Exercise Steps

1. Create a `cs1302.ce24.Find` class based on code below that provides a
   an implementation of the Unix `find` command:

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
   
   You will need to manually setup the package statement and imports.
    
1. **Next, use Maven to compile and the code.** Please use the `exec:java` phase to run.
   After you've confirmed that it compiles and runs, please add and commit `Find.java`.

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
      
   1. If the file does exist, print the pathname string for the `File` object
      to standard output, then, if the `File` object refers to a directory, 
      use recusion to do the same for all files in the directory. For this
      part, you may use a stream or a for-each loop.

**CHECKPOINT**
implement `DownUp(String str)`. Give example execution with "Dawgs" as input.
**CHECKPOINT**
implement `public static List<String> split(String str, String delim);`
**CHECKPOINT**
<hr/>

[![License: CC BY-NC-ND 4.0](https://img.shields.io/badge/License-CC%20BY--NC--ND%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by-nc-nd/4.0/)

<small>
Copyright &copy; Michael E. Cotterell, Brad Barnes, and the University of Georgia.
This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> to students and the public.
The content and opinions expressed on this Web page do not necessarily reflect the views of nor are they endorsed by the University of Georgia or the University System of Georgia.
</small>
