## Java Notes

### JDK (Java Development Kit)
Consists of tools and libraries which will help us write java code, it also consists of JRE (Java Runtime Environment), also the debugger, javaC compiler etc.

### JRE (Java Runtime Environment)
Provides an environment to run the java program, JRE consists of JVM where the code finally runs, The JVM starts interpreting the bytecode, it detects the frequently executed code (hot code), JIT (Just in time compiler) compiles this byte code into machine code, next time JVM runs the machine code of the frequent code.

The JRE has the compiler which compiles the code to bytecode.
The JRE has the JVM/interpreter which compiles the bytecode to machine code.
The JIT (Just in time interpreter) monitors the bytecode and when it detects a code running repeatedly, JIT compiles the entire method to native machine code bypassing interpretation. This way it avoids reinterpreting the repetitive code again and again giving a performance boost.

### The flow of a Java program:
.java file is written.
The .java file is compiled to bytecode by the compiler.
JVM starts.
Interpreter executes the bytecode.
JIT detects hot code and compiles hot bytecode to machine code.
Native machine code reused for performance.

Code Example:
Test.java
``` 
Class Test{
	public static void main(String [] args){
		System.out.println(“Hello World!”);
    }
}
```

Then we ask the compiler to compile Test.java using the following cmd
`javac Test.java` → java compile Test.java

After running the above line we get a named → Test.class

Now we tell java to run Test.class file and give us the output
`java Test` → On running this we get the output “Hello World!”


`Note:`
Ok now to clear the confusion `javac` runs the compiler, `java` command runs the JVM which converts the byte code to machine code.

Also one might think when providing a file to javac we specify Test.java, but when providing it to the JVM we just tell java Test, 

This is because by default the JVM accepts only the compiled code, so when we specify java Test.class it will throw an error. So there is no need to mention the extension.

### Summary
So, .java file gets compiled by javac compiler, then the byte code is converted to machine code and interpreted line by line by the jvm.

### What is line by line ?
So the interpreter parses through the machine code first and reads it, and again it parses the second time where it group’s the instructions to run in an orderly manner.

Once the grouping is done it runs the groups one after the other, this is why the interpreter is slower than the compiler.

JIT (Just in Time Compiler) there is also jit within the JVM so this compiler is there to compile if there is any repetitive code, it compiles the repetitive code and interprets it first hand so that the repetitive code is not compiled and interpreted over and over again.

### Understanding the class objects and methods in java

Test.java
``` 
Class Test{
	public static void main(String [] args){
		System.out.println(“Hello World!”);
    }
}
```

Everything in java is written inside a class and we create objects.
Ex: Car is a class, its objects are BMW, Toyota, Suzuki etc
Food is a class, its objects are Indian food, asian food, arabian food etc.

### The main method in java
```
Class Test{
    // The below line public static void main is called signature of the method.
    public static void main(String [] args){
		System.out.println(“Hello World!”);
    }
}
```
The main method is the entry point of the program in java, it has a specific signature:
- `public`: Access modifier indicating the method can be accessed from outside the class. This also indicates that JVM can access this method. JVM cannot access a private method.

- `static`: Indicates the method belongs to the class rather than an Instance of the class. A static method can be used without creating the instance or object of the class. It can be accessed using Test.main() by the jvm and by the user.

- `void`: Indicates the method does not return anything.
- `main`: Name of the method
- `String [] args`: The method accepts an array of strings as parameters. This is where command line arguments can be passed to the program.

`System.out.println(“Hello World!”);`
The above line is responsible for printing the message Hello World! on to the console.
We know that in java everything is inside a class.

`System`: A class in java.lang package that provides access to the system, including the console.

`out`: An instance of the PrintStream class within the System class, representing the standard output stream.

`println`: A method used to print a line of text on the console.

`“Hello World!”`: String to  be printed.

`;` semicolon in java is a crucial element to indicate the end of a statement. It helps the compiler to understand the structure of the code by marking boundaries between different statements.