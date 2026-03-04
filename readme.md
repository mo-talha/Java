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

## Lecture - 5 Engineering Digest
### Primitive Data Types - The most basic type of data

### There are 4 Primitive Data Types:
Whole numbers - numbers without decimal points, In java we store the integral numbers (-9, 5000 etc) using the following data types:
- byte
- short
- int 
- Long
```
	byte age = -20;
	short age1 = 21;
	int age2 = 20;
	long age3 = 20;
```

The question might arise if all can store numbers then why so many data types, lets take an example if we want to drink coffee we won’t use a mug we use a cup, if we want to water plants we won’t use a cup but we use a mug. 

Similarly according to our need we will use the data type with the right capacity.
If we do,
`System.out.println(Byte.MIN_VALUE);` → This will show -128
`System.out.println(Byte.MAX_VALUE);` → 127, In byte we can not store anything less than -128 and cannot store more than 127 we have to move for short. Similarly there is a min and max capacity for `short(-32768, 32767)`, `int` and `long`.

Also incase of long numbers, we have to mention l, ex: `long number = 4654l;`
This is because if the number falls in the integer range then the compiler will not throw an error, but once the long number crosses the integer range then we have to attach l to the number.

Decimal numbers - similarly we store decimal numbers using the following data types:
float
When using float we need to use f with the number ex: float no = 4.66f;
because the compiler will take the number as double if not mentioned with f.
double 
Characters 
char
It stores a single letter of any language, single special characters like @,! etc and can store a single value like 4, 2, 1 etc and have to enclose the character in single quotes ex: ‘@’, ‘#’, ‘1’, ‘a’.
Every character has a number mapped to it. So the char ‘@’ gets converted to its numerical value.
Characters are stored as numbers in memory, ex: value of A is 65 in memory the binary value of 65 is stored.
	

If you want to know the value of a character you can type cast it, ex:

char character = ‘@’;
System.out.println( (int) character); → This will return 64, which is the value of @
So in memory the binary value of 64 is stored.

There are a total of 65,536 characters which can be stored in char. These characters can also be represented in unicode values. Ex: char heart = 10084; → This number is mapped to heart emoji, 
you might be thinking how can we store multiple values when it was mentioned above that only a single value can be stored, this was only in case of character literal a character literal is something which is enclosed in ‘ ’ single quotes. 
Also why is the char able to store an integer number ? because the number is mapped to some character, like heart emoji in the above case.

Similarly, in unicode char heart = '\u2764'; unicode is hexadecimal which means 0 - 9 with letters A, B, C, D, E and F, uptill F similarly decimal is 0 - 9
Similarly there is ASCII to encode characters.

All of the above are different ways of letting the compiler know about a character, we can mention Z as a character literal ‘Z’, a number, a unicode value or ASCII value.

Lets say we write a software where we mention that on pressing esc the game should stop how does this happen, how does computer know that it should stop when esc is pressed ?

We can use ASCII value for esc and then let the computer know that when this value is passed you have to stop.

Booleans
Boolean
Boolean has two types true and false.
Ex: boolean isEligible = false;
System.out.println(isEligible); → This will print false only.
We might think false is neither a string nor a character nor an integer, then what is it ? true and false are reserved keywords, these cannot be used as variable names, 
ex: boolean false = false; → This is not possible.
Similarly int long = 5; —> This is not possible as long is a reserved keyword.

Variables - variables store data, the types of data are integral numbers, decimal numbers, character and booleans.

Byte sizes of different data types:
byte = 1 byte = 8 bits, 1 bit means either 0 or 1.
ex: byte num = 10;  since byte can store 8 bits, 10 in bits is 1010, which is 4 bits hence it can store the value.
short = 2 bytes = 16 bits
int = 4 bytes = 36 bits
long = 8 bytes = 64 bits
float = 4 bytes = 36 bits
double = 8 bytes = 64 bits
Boolean = 1 bit = 0 or 1