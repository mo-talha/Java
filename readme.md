# Java Notes

## JDK (Java Development Kit)
Consists of tools and libraries which will help us write java code, it also consists of JRE (Java Runtime Environment), also the debugger, javaC compiler etc.

## JRE (Java Runtime Environment)
Provides an environment to run the java program, JRE consists of JVM where the code finally runs, The JVM starts interpreting the bytecode, it detects the frequently executed code (hot code), JIT (Just in time compiler) compiles this byte code into machine code, next time JVM runs the machine code of the frequent code.

The JRE has the compiler which compiles the code to bytecode.
The JRE has the JVM/interpreter which compiles the bytecode to machine code.
The JIT (Just in time interpreter) monitors the bytecode and when it detects a code running repeatedly, JIT compiles the entire method to native machine code bypassing interpretation. This way it avoids reinterpreting the repetitive code again and again giving a performance boost.

## The flow of a Java program:
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

## Summary
So, .java file gets compiled by javac compiler, then the byte code is converted to machine code and interpreted line by line by the jvm.

## What is line by line ?
So the interpreter parses through the machine code first and reads it, and again it parses the second time where it group’s the instructions to run in an orderly manner.

Once the grouping is done it runs the groups one after the other, this is why the interpreter is slower than the compiler.

JIT (Just in Time Compiler) there is also jit within the JVM so this compiler is there to compile if there is any repetitive code, it compiles the repetitive code and interprets it first hand so that the repetitive code is not compiled and interpreted over and over again.

## Understanding the class objects and methods in java

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

## The main method in java
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

# Lecture - 5 Engineering Digest
## Primitive Data Types - The most basic type of data

## There are 4 Primitive Data Types:
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

## Decimal numbers - similarly we store decimal numbers using the following data types:
1. float
When using float we need to use f with the number ex: `float no = 4.66f;` because the compiler will take the number as double if not mentioned with f.

2. double 

## Characters 
### char
It stores a single letter of any language, single special characters like @,! etc and can store a single value like 4, 2, 1 etc and have to enclose the character in single quotes ex: ‘@’, ‘#’, ‘1’, ‘a’.
Every character has a number mapped to it. So the char ‘@’ gets converted to its numerical value.
Characters are stored as numbers in memory, ex: value of A is 65 in memory the binary value of 65 is stored.
	
If you want to know the value of a character you can type cast it, ex:
```
char character = ‘@’;
System.out.println( (int) character); → This will return 64, which is the value of @
```
So in memory the binary value of 64 is stored.

There are a total of 65,536 characters which can be stored in char. These characters can also be represented in unicode values. Ex: `char heart = 10084;` → This number is mapped to heart emoji, 
you might be thinking how can we store multiple values when it was mentioned above that only a single value can be stored, this was only in case of character literal a character literal is something which is enclosed in ‘ ’ single quotes. 
Also why is the char able to store an integer number ? because the number is mapped to some character, like heart emoji in the above case.

Similarly, in unicode `char heart = '\u2764';` unicode is hexadecimal which means 0 - 9 with letters A, B, C, D, E and F, uptill F similarly decimal is 0 - 9
Similarly there is ASCII to encode characters.

All of the above are different ways of letting the compiler know about a character, we can mention Z as a character literal ‘Z’, a number, a unicode value or ASCII value.

Lets say we write a software where we mention that on pressing esc the game should stop how does this happen, how does computer know that it should stop when esc is pressed ?

We can use ASCII value for esc and then let the computer know that when this value is passed you have to stop.

## Boolean
Boolean has two types true and false.
Ex: 
```
boolean isEligible = false;
System.out.println(isEligible); → This will print false only.
```
We might think false is neither a string nor a character nor an integer, then what is it ? true and false are reserved keywords, these cannot be used as variable names, 
ex: `boolean false = false;` → This is not possible.
Similarly `int long = 5;` —> This is not possible as long is a reserved keyword.

## Variables 
variables store data, the types of data are integral numbers, decimal numbers, character and booleans.

## Byte sizes of different data types:
1. byte = 1 byte = 8 bits, 1 bit means either 0 or 1.
ex: byte num = 10;  since byte can store 8 bits, 10 in bits is 1010, which is 4 bits hence it can store the value.

2. short = 2 bytes = 16 bits

3. int = 4 bytes = 36 bits

4. long = 8 bytes = 64 bits
5. float = 4 bytes = 36 bits
7. double = 8 bytes = 64 bits
8. Boolean = 1 bit = 0 or 1

# Number System
## Base-10 or decimal= 10^3 ,10^2, 10^1, 10^0 etc
Decimal is used by us humans for ex:
123 - Is read as hundred and twenty three, 
because 1 is in 10^2 place which is 100 so 100 * 1 = 100, 
2 is in 10^1 place which is 10 so 10*2 = 20,
3 is in 10^0 place which is 1 so 1*3 =3 , which is now hundred twenty three

## Base-2 = 2^4, 2^3, 2^2, 2^1, 2^0 etc
In the computer world a byte or 8 bits are used as a standard to represent a decimal number, a character etc. 
A bit i.e. 0 or 1 is not sufficient to represent characters, values etc. Hence 8 bits the standard going upto 16, 32 bits.

### Also modern languages like java use two’s complement to represent numerics in binary.
### One’s complement:
Invert all the binary values i.e. 0-> 1 and 1 -> 0
Has two zeros, a positive 0 and a negative 0, this is why one’s complement is not used as two zeros make arithmetic operations complicated.

### Two’s complement:
Invert all the binary values and add 1 for -ve representation of a number.
Has only one zero.
Used by java and most modern languages.
Ex: 
In binary - 1 0 0 0 0 0 1 = 65
In binary positive 65 = 0 1 0 0 0 0 0  1 = +65
Invert all the bits of +65 = 1 0 1 1 1 1 1 0 (1's complement)
Add 1 to 1s complement = 1 0 1 1 1 1 1 0 + 1 = 1 0 1 1 1 1 1 1 = -65

Also in two’s complement the MSB (Most significant bit) the first bit from left side is used to represent a sign either +ve i.e. 0 or -ve i.e. 1.

### CS50
ASCII - American Standard Code for Information Interchange
Anytime our computer shows us the capital letter A, underneath the hood it stores a pattern of 0’s and 1’s that represent the number 65.

This is the system known as ASCII.

Unicode - It’s the superset of ASCII where ASCII might use only 8 bits or a byte to represent characters. Unicode uses 16 or even 32 bits sometimes, hence giving it the ability to represent over 4 billion characters. 

It is also used to represent letters of different languages etc.

Unicode is the one behind emojis today which take more than 8 bits in binary representation.

Unicode uses base-16 as there will be a lot of 0’s and 1’s in base-2. 
Ex: U+1F602 is the unicode for the popular smiling with tears emoji - but under the hood the memory either the ram or disk will have its binary representation.

So the unicode will be sent to the OS where the OS will pick the binary value of each hex digit, like U will have its own binary value, + will have its own etc.

# Variable Naming in Java
Variable names in java are case sensitive. I.e. animal != Animal these two are seen as different variable names.
Variable names can be letters, dollar sign($) or underscore(_)
Must begin with a letter, dollar sign or underscore.
Cannot use java keywords as variable names. Ex: int, public, String etc.
Keep the variable names meaningful, avoid using names like int x, String s etc
Make use of camel case in variable names, ex: fullName, myPassword etc.

# Arithmetic Operators in Java
1. Addition + - Used to add two numbers
2. Subtraction - = subtraction of two numbers
3. Division / - Used to divide to numbers.
4. Multiplication * - Operator used to multiply two numbers.
5. Modulo %  - This returns the remainder after dividing 2 numbers. Ex: 5/2 = 2, remainder = 1

# Bitwise Operators
These are operators used directly on bits and these operators can be used only on integral data types like byte, short, int and long. 
These are not used on decimal numbers because the bits of decimal numbers get divided into parts so it is difficult to manipulate them.

Also since they apply directly on bits they are faster than arithmetic operators.

Ex: 00000101
1 if we want to change a particular bit like shown we make use of these operators.

## Bitwise operators are as follows:
1. and &
2. or |
3. xor ^
4. not ~
5. left shift <<
6. right shift >>
7. unsigned right shift >>>

Ex:
### & Operator
`int c = 5 & 4;`
`sout(c)` → This will give 4.
How did we get 4, As we know that bitwise operators manipulate the bits hence to understand this we have to print the bits of 5 and 4 

If we do,
`sout(Integer.toBinaryString(5));` → 101
`sout(Integer.toBinaryString(4));` → 100
As we know the operations happen on bits so & will happen between separate bits meaning,
```
1 | 0 | 1   In & operator even if one bit is 0 in a pair, the result is 0, similar to multiplication 
&   &   &   where anything multiplied by 0 is 0. So 1 & 0 = 0.
1 | 0 | 0     
—-----
1 | 0 | 0 =  4

4 | 2 | 1 = (1*4) + (0*2) +(0*1) = 4
2^2, 2^1, 2^0
```
### OR | operator
In or operator, in pair of bits if any bit among the pair is 1 then their result is also 1
int c = 5 | 4
sout(c); → 2
sout(Integer.toBinaryString(5)); → 1| 0 | 1
sout(Integer.toBinaryString(7)); → 1 | 1 | 1
```
1| 0 | 1
1| 1 | 1
—-------
1   1   1 -> 7
4   2   1 = (4*1) + (2*1) + (1*1) = 7
```

### XOR ^ Operator
In XOR operator if two bits are different only then, the result will be 1 else if two bits are same then it is 0
```
int c = 4 ^ 5;
sout(c); → 2
1   0   1
1   1   1
—--------
0   1    0
4   2    1 = (4*0) + (2*1) +(1*0) = 2
```

### NOT ~ Operator
~ operator inverts the bit, i.e. it makes 1 -> 0 and 0 -> 1.
It does not need a pair of bits or two bits to operate.
Ex:
```
int a = 5;
int b = ~a;
sout(b); → This will give -6
```

### Why -6 when a was 5 ?
Because let’s say in binary 101 = 5
When the bits are inverted 0 1 0 now this will be -6, its just a hypothetical example bits of 5 and -6 might be different.

### Left Shift << Operator
The operator is responsible to shift the bits to the left side and fill the right side with zeros.
We can also specify the number of bits to shift like in below ex.
Ex:
```
int c = 5 << 2.
```
If the bits of 5 are 
0000101
0010100 → This will be the modified bit where the one zero was replaced with 1 marked in red and the other 0 is replaced by zero marked in green and two zeros are added after marked in orange.

### Right Shift >> Operator
It shifts the bits on the right side by canceling out if there are any bits ahead.
Ex:
```
int a = 10;
System.out.println(Integer.toBinaryString(a));
int b = a >> 2;
System.out.println(b);
System.out.println(Integer.toBinaryString(b));
```

```
Output:
1010 - The binary of 10.
2 - Integer value after shifting.
10 - Two bits shifted to the right side, hence the from 1010 -> 10 remains which is the binary of number 2 in decimal.
```

Also in the right shift operator the sign before the number plays a vital role in changing the most significant bit .i.e. The first bit.

Ex:
```
int a = -10;
System.out.println(Integer.toBinaryString(a));
int b = a >> 2;
System.out.println(b);
System.out.println(Integer.toBinaryString(b));
```

In the above example there is a -ve sign before 10, hence the first bit of 10 will become 1 as shown below in red.

Output:
```
Also as we are shifting two bits to the right we can see that 10 marked in green is gone and 01 is there in the result.
11111111111111111111111111110110 = 10
11111111111111111111111111111101 = -3
```

### Unsigned Right Shift >>>
This operator no matter the sign of the operand it keeps the MSB positive.

Ex:
```
int a = -10;
System.out.println(Integer.toBinaryString(a));
int b = a >>> 2;
System.out.println(b);
System.out.println(Integer.toBinaryString(b));
```
```
Output:
11111111111111111111111111110110
1073741821
111111111111111111111111111101 
```

# Difference b/w println, printf and print statement
1. println - will print a statement in new line, has same methods as printf.
2. printf - helps to keep the print statement and the arguments clean, formatted and easy to read and does not print in a new line.
3. print - Has same methods as println, just that prints in the same line does not use a new line.

Ex:
```
int a = 5
int b = 5
System.out.println(“The Sum of  ” + a +“and ” +b +”is: ”+ a+b);
System.out.printf(“The Sum of %s and %s is: %s”,a, b, (a+b));
The one with is more readable than string concatenation in the println statement.
```

# Lecture - 9 Strings Engineering Digest
If we have to store a single character then we use char and ‘ ’ single quotes to store the value. Ex: `char a = ‘s’`;

If we have to store a sequence or multiple characters together we use String and “ ” double quotes. Ex: `String = “Taz”;`.

***String is a class and not a primitive data type.***

When we assign a primitive data type to a variable, ex: `int num = 1;`
Then in the memory, space is allocated for num and its value also is stored in the same place.

`Student student = new Student();`
Whenever a ***new keyword is used, an object is created in heap memory***.
The student variable holds the address of the object which is created in heap memory, it does not store the object student.
Hence Student is a ***reference variable***.

Heap means a place to store objects, this is created by the OS in case of Java to store new objects in memory.

### There are two ways to create Strings: 
2. `String name = “Taz”;`
This method will create a String object and store its value Taz inside ***String pool*** in Heap memory, and the name will store the string pool address of Taz.

1. `String name1 = new String(“Taz”);`
This method creates a new object Taz and stores it in heap memory, name1 will store the heap mem address of the object Taz.

```
public static void main(String[] args) {
   String a = "Taz";
   String b = "Taz";


   /* a == b will return true, as b will point to the location of a in String pool inside heap mem. */
   System.out.println(a == b);


   String c = new String("Taz");
   String d = new String("Taz");

   System.out.println(c == d);
}
```
`System.out.println(c == d);`
c == d will return false, as b will create a new object in heap and c will hold the specific address and d will also create a new object in heap because of new keyword and d hold the specific address.
***String objects created with new keyword are created in heap and not string pool.***

Also == in case String compares the addresses of heap mem and string pool.
a == b, a & b variables a and b will hold addresses of Strings in string pool and heap.

When an object of a Class is created i.e. `String name = “Taz”;`
The object name with its value Taz is stored in string pool inside heap memory, and the name variable stores the address of value Taz in string pool inside the heap memory. This is a reference variable as it stores the address of the value in the heap memory.

### Lecture - 9 Summary
1. Reference Variable
2. Methods of creating strings, String , new String
3. String pool and heap memory
4. == operator in case of String checks mem address and the String values.
5. Space allocation for primitive data types and classes.

## equals() method
== in Java checks the memory address, but equals() method checks if the value of reference variable same as another.
But == can be used to check equality of values for primitve types.

```
public class Main{
	public static void main(String[] args){
		String a = "Taz";
		String b = new String("Taz");

		System.out.println(a==b); --> This will print false, as one is stored in 
		System.out.println(a.equals(b)) --> This will print true, as it is checking the values.
	}
}
```

# Memory Management in Java
## Primitives
### 1. Local Variables (Inside Methods)
Local variables live inside the stack
```
public void calculate(){
	int x = 10; // Stack local primitive
	double y = 20.5; // stack local primitive
	boolean flag = true; // stack local primitive
}
``` 
When the method ends the x, y and flag vanish from stack.

### 2. Instance Variables (Inside Objects)
```
public class Person{
	int age = 30;
	double salary = 50000;

	public void work(){

	}
}
Person p = new Person();
```
age and salary live in heap because they belong to the Person p object.

### 3. Static Variables (Class variables) --> Method Area (Special heap)
```
public class Config{
	static int MAX_USERS = 1000;
	static double VERSION = 1.5;
}
```
Both MAX_USERS and VERSION live in the Method Area (not stack, not regular heap)

# Arrays
Arrays are created in the heap, arrays are stored in a continous sequence inside the heap.

### Creating an Array
```
int[] arr = new int[5];
int[] arr1 = {1, 2, 3, 4};
```

arr is a reference variable which will be on the stack and it stores the heap address of first integer of array inside the heap.
The actual numbers 1, 2, 3 etc will be on the heap.

Also in case of an array we can get the length using, `arr.length` but in case of String we do `str.length()` because String is a class and length is a method, but in case of arr length is a property or class variable. Field access is faster compared to a method call.

### Printing an Array
int[] arr = {1, 2, 3};


System.out.println(arr); // This will print [I@372f7a8d, [ means its an array, I means of type integer and from @ is the hashcode of the array object arr, in Java every object is denoted by a hashcode.

// If the array was of type float then its hashcode would be [F@372f7a8d.

int[] arr = {1, 2, 3, 4, 5};
System.out.println(arr); 
// Prints: [I@372f7a8d

// Breakdown:
// [  = one-dimensional array
// I  = integer type
// @  = separator
// 372f7a8d = hashcode in hexadecimal

System.out.println(Arrays.toString(arr));

The toString() method returns a string representation of the object. The hexcode is difficult to understand when printed so we can override the toString method to print the textual representation of the object.

Every object inherits the toString() method from the object class. The default implementation returns classname@hashcode in hexadecimal.

Arrays don't override toString(), so printing an array directly gives [I@372f7a8d where [I means integer array. To get the actual contents, we use Arrays.toString() for 1D arrays and Arrays.deepToString() for multi-dimensional arrays.

Collections like ArrayList do override toString() to show their contents, which is why System.out.println(list) actually prints useful information.

In my own classes, I always override toString() to return meaningful state information. It's invaluable for debugging, logging, and stack traces."

┌─────────────────┬─────────────────────────┬──────────────────┐
│ Type            │ What prints             │ How to fix       │
├─────────────────┼─────────────────────────┼──────────────────┤
│ int[]           │ [I@372f7a8d             │ Arrays.toString()│
│ String[]        │ [Ljava.lang.String;@... │ Arrays.toString()│
│ int[][]         │ [[I@372f7a8d            │ Arrays.deepToString()│
│ ArrayList       │ [1, 2, 3] (good!)       │ Already good     │
│ Your class      │ MyClass@3e8a99e4        │ Override it!     │
└─────────────────┴─────────────────────────┴──────────────────┘


