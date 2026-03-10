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


***Note:***
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

		System.out.println(a==b); --> This will print false, as one is stored in string pool and another in the heap.
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
```
┌─────────────────┬─────────────────────────┬──────────────────┐
│ Type            │ What prints             │ How to fix       │
├─────────────────┼─────────────────────────┼──────────────────┤
│ int[]           │ [I@372f7a8d             │ Arrays.toString()│
│ String[]        │ [Ljava.lang.String;@... │ Arrays.toString()│
│ int[][]         │ [[I@372f7a8d            │ Arrays.deepToString()│
│ ArrayList       │ [1, 2, 3] (good!)       │ Already good     │
│ Your class      │ MyClass@3e8a99e4        │ Override it!     │
└─────────────────┴─────────────────────────┴──────────────────┘
```
### What are Jagged Arrays ?
2D arrays with where each row has different column size.
ex:
```
2 3
1 4 5
6 7
```
# Object Oriented Programming (OOPs)
## What are OOPs ?
Object Oriented Programming is organizing code around objects (things) that have properties (data) and behaviour (actions).

## What is a class ?
Class is a blueprint to create an object.
ex:
```
class Car{
	// These properties
	String brand;
	String model;
	int year;
	int speed;
 
	// we define behaviour of an object as methods, accelerate is an action or behaviour which increases the speed.
	public void accelerate(int increment){
		speed+=increment;
	}
}
```
This is a blueprint of a car, any object of type car can be created using the above blueprint.
ex: Honda builds so it can use the above blueprint to create a model of its own.
```
Car car = new Car();
car.brand = “honda”;
car.model = “civic”;
car.year = 1993;
```

Similarly, Toyota can build a model of its cars like Corolla, supra, fortuner etc.

## There are 4 pillars of OOP
### 1. Encapsulation - Bundling of data and methods in a single unit and hiding the data is called encapsulation. 
ex: we saw that the car class has properties like brand, model etc and a method to accelerate in it.
### 2. Inheritance
### 3. Abstraction
### 4. Polymorphism

Also, encapsulation also means making the properties or data private, meaning we can control what things can be accessed from an object and what things are to be hidden. We can make the properties private and restrict access to them.

ex:
```
public class Car{
	private String brand;
	private String color;
	private int year;
	
	public void setBrand(String brand){
		this.brand = brand;
	}

	public void getBrand(){
		return this.brand;
	}

	public void setColor(String color){
		this.color = color;
	}

	public void getColor(){
		return this.color;
	}
}
```
We restricted access to properties before they were public. Anyone can access any property and also set their own, but now they can only get and access those properties which have a getter and setter.

The property year, we don’t want any changes to it so no one can access it as it is private and there is no getter and setter to it.

### 2. Inheritance
As we humans inherit traits from our parents, similarly in OOPs a class can have a parent class and it can inherit the properties of the parent class.

ex:
```
public class Animal{
	String name;
	String age;
}

public class Cat extends Animal{
	String breed;
}

Cat cat = new Cat();
cat.name = “Bob”; 
```
Since, cat’s parent class is Animal it inherits the properties of the parent class like name, age etc.

### 3. Polymorphism 
Many forms of a single class.
ex: we saw that cat’s parent class or super class is Animal and similarly it will be for dog.
Hence a dog or cat can be created with reference to the Animal class.
ex: `Animal cat = new Cat();` 
This is possible because cats are a form of animal class.

### 4. Abstraction
When we have a TV we operate it using a remote, but we don’t know what happens inside when we press a button, this hidden functionality is called abstraction.
Abstraction basically says to hide the inner implementation to make it easy for the end user.

Programming Paradigms other than oops are
Imperative - In this we write the instructions line by line.
Functional 

### Methods in Java
A method in Java is a block of code that performs a specific, well-defined task. Methods are essential because they allow you to reuse code, making your program modular and organized.
In Java a method can only be written inside a class.
When writing a software we might want to do a specific task more than once, for this we will end up writing the same code many times, to avoid the writing of duplicate code, we can create a method instead which does the job and call it where it's required instead of re-writing it again.
ex: let’s say we need to print the sum 2 numbers 2 and 3
we write
```
int sum = 2 + 3;
System.out.println(sum); this will print 5.
```
Let’s say we got another requirement to print the sum of 4 and 5, we will need to write it again
```
int sum2 = 4 + 5;
System.out.println(sum2);
```
We can see that the purpose is the same and the outcome as well, to avoid this writing of the same code again and again we can write a method sum.
```
public int sum (int a, int b){
	return a + b;
}
```
now we can simply do,
```
int sum1 = sum(2, 3);
int sum2 = sum(4, 5);
int sum3 = sum(3, 3);
```

This helped us avoid writing the same logic over and over again.
We can have another requirement where we are asked to sum 3 numbers, we can write the same method but with 3 input parameters.
```
public int sum(int a, int b, int c){
	return a+b+c;
}
```
Also, ***a method which has the same name, return type but different parameters is called method overloading***.

### Syntax of a method
```
access modifier return type method name(params){
	//logic
}
```
**access modifier** - public and private. This is nothing but it shows if a method is accessible from outside the class, or it is only accessible to that class. a public method is accessible from outside the class as well but a private method is only accessible inside that class.

**return type** - This shows what the method returns, the above method sum returns an integer. If a method does not return any type, then it will be void in place of return type.

**method name** - is the name of the method, like sum.

**Parameters** - these are the type of data that a method takes, ex sum takes data of type int.

### What is method signature ?
It is the name of the method and the parameters it takes. ex: sum(int a, int b) this is called method signature.

***Note:***
Two methods with the same signature cannot exist, either we change their name or the number of parameters each method takes should be different.
```
public class Test{
	public static void main(String[] args){
		int x = 10;
		System.out.println(multiplyBy10(x)); // A copy of x is being sent to the multiplyBy10 method.
		System.out.println(x); // this will print 10, because x was never altered by the method multiplyBy10 but a copy of it was.
}
```

The x in this param is different from the x in the main, the x here is only accessible inside the method multiplyBy10 and the x of main is only accessible inside the main method.
``` 
public int multiplyBy10(int x){
	return x * 10;
}
```

The multipleBy10 did not change the x of main class because java is strictly pass by value, meaning when a method is called ex: multiplyBy10(5), a separate frame is created for this method in the call stack, this frame will have it’s own local variables like x etc in the stack frame, instead of referring to the x of the main function call frame in the stack.

In case of a String, if we pass a string to a function then the value or the reference is passed to the method, but any modifications a method does to the given string a new string is created in the String Pool inside the heap memory.

Primitive data types like int, float, long, double, boolean etc are all strictly pass by value. String is a class whose reference is passed or the address of the string is passed and since String is immutable, any change on a String object is not directly on that object, but a new object is created with the reference.

ex:
```
public static void main(String[] args){
	String name = “Taz”;
	makeNameUpperCase(name);
	System.out.println(name); → This will still print “Taz” and not “TAZ”
// Because a reference of memory address of name was passed to makeNameUpperCase, makeNameUpperCase will pick the value Taz from the reference in the memory and then create a new object of type String, it does not change the name itself because Strings are immutable.
}

public void makeNameUpperCase(String s){
	s.toUpperCase();
}
```
So, if we want to see the change then makeNameUpperCase must return the object which it creates and then changes.

```
public String makeNameUpperCase(String s){
	return s.toUpperCase();
}
```

Another example,
class Test{
	Cat a = new Cat();
	Cat b = a;

	b.name = “Bob”;
	System.out.println(a.name);
}

here, a.name will print Bob, because b has the reference to the same object as a in the heap memory and since Cat is mutable class, any change done by b will be on the same object which a points, because both a and b point to the same object in the heap memory.

### Variable Arguments
We saw a method to get the sum of 2 numbers, similarly if we wanted to get the sum of 3 numbers we created another method with 3 params. 
If we want to get the sum of 4 numbers then we have to overload the method sum with 4 params.

But there is another approach to this, we can use variable arguments, meaning we can pass multiple arguments of a data type separated by commas in a single method and we can perform operations on those values like getting their sum etc.
```
public int sum(int … a){
	int sum = 0;
	for (int i: a){
		sum+=i;
	}
	return sum;
}
```

Here, int… a can take any number of integer values separated by commas like, sum(1, 2, 3, 4) 
Internally, an array is created and all these values are stored in it, inside the method we traverse over the array and add it to the sum variable.

Similarly, if we consider main method
The main method takes an array of arguments of type string, the arguments passed in the main method are called command line arguments. Because we can compile the java code by doing, 
`javac Test.java`
When running the java code after compilation we can also pass arguments,
`java Test.java hello I am talha`

```
public static void main(String[] args){
	System.out.println(args[0]);
	System.out.println(args[1]);
	System.out.println(args[2]);
	System.out.println(args[3]);
}
```
When the code is run, the words in the command line are printed, we might think how is java able to pick the words separately when we have not separated them with commas, this happens because JVM picks the words separated by space and creates an array of words.

# Packages and Class paths
Package is nothing but a folder which consists of different class files. Packages help in avoiding conflicts when it comes to the same class files. Class files with the same name can be put by creating different packages.

ex: 
A package called animals can have a class called cat.
```
animals
    |__ Cat.java
```
The same package cannot have another class called Cat.java, but let’s say we have a requirement to create Cat class for a family of big cats, we can create a separate package called big cats and create a class Cat.java inside this package, now there won’t be any conflicts.
```
bigcats
     |_ Cat.java 
```
Packages help us in keeping things organized.

### Naming convention of a package
com.koinbasket.userservice
The domain of the company is written in reverse order, followed by the package name.

### Class Path
It is the path of a class where it is located.

ex:
This is the path of the class HashMap, it is called the class path. HashMap is in the java package, inside the java package there is a util package and inside that is the class HashMap.

If we observe we can see that the package names java, util etc are lowercase but when it comes to class it is in camel case that’s how we got to know that HashMap is a class.
`import java.util.HashMap;`
```
class Test{
	public static void main (String[] args){
		HashMap<Integer, Integer> map = new HashMap<>();
	}
}
```
Also, a class can have multiple classes but the file name must always be the name of the public class.
ex:
```
public class Vehicle{

}

class Car{

}
```
This is possible but the class file name inside the package must be Vehicle.java, it cannot be Car.java. Also ***in a single file there cannot be more than 1 public class***.

ex:
```
public class Vehicle{

}

public class Car{ // This is not possible

}
```
Also, this ***second class will only be accessible to other classes inside its own package, classes in other packages cannot access the second class***.

## Encapsulation
Encapsulation is bundling of properties and methods in a class.

ex:
```
class Student{
	// These are called fields or properties or also called instance variables.
	String name;
	int rollNo;
	int age;
}
```
- **Instance variables** - When an object of a class is created, then that object has the properties, these properties are called instance variables, as that object is an instance of a class.

Also, it is always to be taken care that the properties must always be accessed via methods. 
ex: In the above case, anyone can create an object and enter any values corresponding to the properties.
```
Student student1 = new Student();
student1.name = “Taz”;
student1.rollNo = -1;
student1.age = -16;
```

w.k.t the roll no and age is wrong, so to avoid this we make the properties inside the class private and they are only accessible via methods. Private will make sure that the properties are not accessible outside the class. Methods will provide control over the properties of an instance, we can control what is allowed and what not.

ex: we can make sure that if someone enters age or roll no < 0, we can reject that number and keep the rollNo and age as 0.

ex:
```
class Student{
	private String name;
	private int age;
	private int rollNo;

	public void setName(String name){
		this.name = name;
	}

	public void setAge(int age){
		if (age < 0) {
			this.age = 0;
		} else {
			this.age = age;
		}
	}
// similarly for rollNo.
}
```

Now, no one can randomly set any value to age and rollNo, as we got control over it with the help of a method.

## What is this keyword ?
This keyword is used to refer to the properties and methods of an instance.
ex: 
```
Student student1 = new Student();
student1.setName(“Taz”); 
```

this keyword, makes sure that it sets the name field of object student1 in the heap memory.

Let’s understand Encapsulation with example of a Bank Account
```
class Account{
	private int accountNumber;
	private balance;

	public void deposit(int amount){
		if (amount > 0){
			balance += amount;
			System.out.println(“amount added”);
		} else {
			System.out.println(“Invalid amount”);
		}
	}

	public void withdraw(int amount){
		if (amount > 0 && amount <= balance){
			balance-= amount;
		} else{
			System.out.println(“Low Balance”);
		}
	}
}
```
Here, with the help of encapsulation we can be sure that no invalid amount is deposited into the bank account and also be sure that the amount a user is trying to withdraw is with or within his account balance.

We keep properties private and methods public.

# Lecture 20
## What are Constructors ?
***Constructors are special methods used to initialize an object.***
ex: `Student student = new Student();` 
The method ***Student()*** is called a constructor. It is responsible for creating the object in the ***heap memory***.

The ***constructor's name will be the same as the class name, the above constructor is also called as default constructor***.

Constructors also help us in setting the initial values of properties.

A default constructor creates an object and sets the default values of the instance variables. Like int properties will be set 0 and String properties will be set to null etc.

The default constructor is hidden and is generated by the compiler.

## Points to remember on constructors:
- Their name must be same as the class name
- They do not return anything/ they don’t have any return type.
- The constructors can be overloaded like method overloading.

## What is a parametrized constructor ?
A constructor which takes in arguments or has parameters is called a parameterized constructor.

We can use a custom constructor to set initial values of instance variables.

ex: 
```
class Student {
	private String name;
	private int rollNo;
	private int age;

	public Student(String name, int rollNo, int age){
		this.name = name;
		this.rollNo = rollNo;
		this.age = age;
	}
}

Student student = new Student(“Taz”, 46, 25); 
```
This is a parametrized constructor, it will create an object of student in heap memory with default values as passed in the arguments.

We can also overload the default constructor, 
ex:
```
class Student {
	private String name;
	private int rollNo;
	private int age;

	public Student(){
		this.age = 10;
	}
}

Student student1 = new Student();  
```
This will create an object whose age property will be set to 10.

Also if we write any other constructor, the default constructor will be invalid. This is not the case for when we overload default constructors.

We can also do constructor overloading, we can create a constructor to initialize all the properties of an instance, or a single or only 2.
ex:
```
class Student {
	private String name;
	private int rollNo;
	private int age;

	public Student(String name, int rollNo, int age){
		this.name = name;
		this.rollNo = rollNo;
		this.age = age;
	}

	public Student(String name){
		this.name = name;
	}

	public Student(String name, int age){
		this.name = name;
		this.age = age;
	}
}
```

# Lecture 21
## Inheritance
Inheritance allows a class to inherit properties and methods of another class. It establishes a parent child relationship or IS-A relationship. 
It promotes code reusability.

ex: 
```
class Animal{
	String name;
	int age;

	public void greet(){
		System.out.println();
	}
}
```
Now, the class dog can also have the properties name, age and method greet. But it will be a repetition of code. To avoid this we can inherit the animal class, and get the similar properties, and whatever extra is needed we can write it in dog class. Ex: A person’s father is 6ft tall and has blue iris color. A child can inherit the height but it’s not necessary that he will also inherit the iris color, he can have his own color black.
```
class Dog extends Animal{
	public void greet(){
		System.out.println(“woof”);
	}
}
```
As we learnt above, it’s not necessary that a dog has to inherit the greet class from the parent, he can have his own behavior. This is called method overriding.
Method Overriding is a child class implementing its own version of a method inherited from its parent class.

This is also called single level inheritance, where the child is inheriting from the parent.

## Multi level inheritance
There can also be multi level inheritance, where child inherits from parent and parent inherits from grand parent. In this case the child class will have the properties from both parent and grand parent class.

## Hierarchical Inheritance
Multiple subclasses inheriting from a single parent class, is called hierarchical inheritance.
ex: Dog can extend Animal, similarly Cat can also extend Animal. This is called hierarchical inheritance.
2 subclasses Cat and Dog inheriting from a single parent class Animal.

Also if a class child extends parent and parent extends grandparent, then, first grandparent constructor is called to initialize the grandparent object, because parent is dependent on the grandparent class as it is inheriting from it. 

Then the parent class is initialized and finally the child class is initialized as the child is inheriting from both parent and grandparent.

If grandparent is not initialized then what will the parent inherit and if parent is not initialized then what will the child inherit.

## The new keyword
new keyword is used to allocate memory to the object of a class in the heap memory during runtime. It is dynamic memory allocation, because the memory is allocated when the code is running.

When we do javac, this is compiling but memory allocation of objects does not happen at compile time rather it happens at run time, i.e. when we do java Test.java

When we write code in intellij and we see errors when typing this is because intellij keeps compiling the code in the background, hence we can call this stage as compile time.

## Constructor Chaining
When a child class extends a parent class and parent extends the grand parent class, the child class constructor will have the default constructor of its super or parent class. Similarly the super or parent class will have a constructor of its super or grand parent class.

This constructor is required because the child says let parent initialize first then I will initialize as I’m inheriting from parent and parent class will say let grand parent initialize first because I need properties from him.

This constructor of super class is denoted as super() and it is hidden as the default constructor of a class is hidden.

## Best Practices when overriding a method
When overriding a method from the super class, we have to make sure that we use @override annotation.
Because @Override annotation gives information that a method from a super class is being overridden.
Also, @Override will let the constructor know that a method is being overridden, in this case if there is any mistake then the compiler will throw the error.
ex:
```
class Dog{
	@Override
	public void greet1(){
		System.out.println(“Woof”);
	}
}
```
In the above case the compiler will throw an error saying that greet1 method does not exist in the super class, if the annotation is not present then greet1 will be a method on its own, and the user will be thinking the greet method from the super class is overridden.

## Multiple class inheritance
Java supports multi level inheritance where a parent class extends grand parent class and child class extends parent class and hierarchical inheritance where multiple subclasses extend a single parent class, like we saw dog and cat extending animal class.

Lets see multiple class inheritance with an example
```
class Camera{
	public void powerOn(){
		System.out.println(“booting camera”);
	}

	public void clickPicture(){
		System.out.println(“picture clicked”);
	}
}

class Musicplayer{
	public void playMusic(){

	System.out.println(“Playing music”);
	}
}

class Phone{
	public void makePhoneCall(){
		System.out.println(“Making Phone Call”);
	}
}
```
Now, all the above are individual devices, but a smartphone can do all the above
// This is not possible and this is called multiple class inheritance
```
class Smartphone extends Camera, Musicplayer, Phone{

}
```

This is not allowed because a smartphone will have its own method to power on, similarly music player and camera will also have, this creates confusion, hence java does not allow this.

To overcome this issue Java uses interfaces.

# Lecture 22
## Polymorphism
Polymorphism allows methods to do different things based on the object it is acting upon, even though the method name and signature are the same.

Poly - means many, and morph means - forms, hence many forms.

## Polymorphism is of 2 types:
1. Compile time polymorphism
2. Runtime polymorphism

**Compile time Polymorphism**
```
class Math{
	public void sum(int a, int b){
		System.out.println(a+b);
	}

	public void sum(int a, int b, int c){
			System.out.println(a+b+c);
	}

	public void sum(int a, int b, int c, int d){
			System.out.println(a+b+c+d);
	}

	public static void main(String[] args){
		Math math = new Math();
		math.sum(2, 3);
		math.sum(2, 3, 4);
		math.sum(2, 3, 4, 5);
	}
}
```
This is Compile Time Polymorphism, because at compile or at the time of writing code the compiler decides which method of sum needs to be called depending upon the parameters, if the method does not exist it will warn with an error.

Since sum is method overloaded, ***we can also say method overloading is compile time polymorphism***.

**Runtime Polymorphism**
```
class Animal{
	public void greet(){
		System.out.println(“...”);
	}
}

class Dog extends Animal{
	@Override
	public void greet(){
		System.out.println(“Woof”);
	}
}

class Cat extends Animal{
	@Override
	public void greet(){
		System.out.println(“Meow”);
	}
}

class Test{
	public static void main(String[] args){
		// child class can be created by referencing the super class, but super class cannot be created by referencing the child class.
		Animal dog = new Dog();
		Animal cat = new Cat();
		dog.greet();
		cat.greet();
	}
}
```
Now, in the above code the new keyword will dynamically allocate memory when the code runs or at runtime for the object dog and cat.
JVM sees that greet method is being called, it will pick the greet method from the dog object and same for cat even though they are referencing the Animal class, the JVM is smart enough to know that it has initialized an object of class Dog and a separate object of class Cat as new keyword is used.

Also, the greet method in both Dog and Cat class are overridden hence, this happens at runtime when the objects are initialized, hence ***method overriding is at runtime***.

So, ***Method Overloading is at Compile time and Method Overriding is at Runtime***.

So we can see examples of polymorphism. We are referencing both Cat and Dog objects with Animal class but both are different objects.
Similarly the greet method looks the same for both the objects of Dog and Cat but their behaviour is different.

## What is Dynamic Method Dispatch ?
We saw that at runtime it was decided by JVM which method to call for Dog and Cat, this decision during runtime is called Dynamic Method Dispatch. Dispatch is nothing but calling a method.

## What is Upcasting ?
We saw that child class objects can be referenced to super class, this is upcasting. 
Similarly there is Downcasting, but we know that this is not possible Dog dog = new Animal(); then how ??
```
Animal dog = new Dog();
Dog myDog = (Dog) dog; // This is downcasting
```
or 
```
float num = 2.344;
int num1 = (int) num; // Downcasting
```
***Note:***
We cannot call all the child class methods using a super class reference. Meaning, 
```
class Animal{
	public void sayHello(){
		System.out.println(“...”);
	}
}

class Dog extends Animal{
	@Override
	public void sayHello(){
		System.out.println(“Woof”);
	}

	public void sayBye(){
		System.out.println(“Bye Bye”);
	}
}

Animal bob = new Dog();
bob.sayHello(); // This is possible because it’s there in the reference class Animal.
bob.sayBye(); // This is not possible because it’s not there in the reference class Animal.
```

Since bob is referencing Animal class it can only access methods in the Animal or referencing class.

# Lecture 23
## Abstraction
Abstraction is the way of hiding inner details.

Methods can be abstract. But abstract methods can only be written inside an abstract class. The abstract class can also have concrete methods.

## What is an Abstract method ?
A method without the function body is called the abstract method.

## What is a concrete method ?
A method with definition or a proper function body is called a concrete method.

## Syntax of an abstract method
`access modifier abstract keyword return type method name ();` The abstract keyword sits b/w the access modifier and the return type.

## Why is an abstract method used ?
When we want a method without definition, then we have to declare that method as abstract. An abstract method cannot be written inside a normal class.

ex:
```
public abstract class Animal{
	// abstract method
	public abstract void makeSound();
	
	// concrete method
	public void sleep(){
		System.out.println(“zzz…”);
	}
}
```

W.K.T every animal sounds different, with the help of abstraction any class extending Animal class will be alerted to implement their own version makeSound or the abstract method.

Previously in the Animal class we had a concrete method makeSound, which we were overriding in the Cat and Dog class. But since every child class needs to implement this we can leave this method abstract and the classes extending will be notified to implement those methods.

The extending class must either implement the method or make itself abstract, indicating that even it does not want to implement and keep the method inherited from the parent class abstract.

ex:
``` 
public class Cat extends Animal{
	@Override 
	public void makeSound(){
		System.out.println(“meow”);
	}
}
```
Or
```
public abstract class Cat extends Animal{
	@Override 
	public abstract void makeSound();
}
```

We can implement all the things in an abstract class like we do in a normal class. But the advantage of an abstract class is we can have methods without definition inside it, which the extending classes can override or leave it abstract.

***Note:***
But, we cannot create an object of the abstract class, because it does not make sense. We will have methods without definition, so initializing an object which has methods with no definition is not possible. 

We cannot do, `Animal animal = new Animal();`
Abstract classes are useful when we know that there can be a hierarchical inheritance of a single class and every child class can have its own methods which are different from each other, in such cases abstract class will have only abstract method signatures in it and child classes will have their implementation of the abstract methods and they can also have their own separate specific methods which belong to that class only.

Lets say we have a class called Car now w.k.t every car has common things such as accelerate, brake, power on etc We can implement these common methods inside the abstract class Car and every object extending this class like Toyota, Honda, BMW etc can have these methods ready, this helps in avoiding writing repeated methods.

***Abstract methods need to be public, only then they can be implemented by the extending class.***

## Access Modifiers
These are keywords in Java, which decide the visibility of a class, properties and methods.

### These are:
1. public
2. private
3. Protected

### Public
Any class, property or method if it is public it can be accessed from any package.

### Private
If a property or method in a class is private then it is only accessible within that class. Classes can be only public and default.

ex:
public class Student{
	private int rollNo;
	private int age;

	// Both age and rollNo and method sayHello can only be accessed within the student class.
	private void sayHello(){
	
	}
}

Similarly, a constructor can also be private, but if a constructor is private then the object of that class cannot be created. 

Then, ***what’s the use of making a constructor private ?***
There are many cases where creating an object of the class is not required, but there will be methods in that class which will be needed.

In such cases, the constructor of the class will be private but the methods will be static, static methods can be accessed without initializing an object of that class.

Non-static methods are bound to the object or instance of a class. 
Static methods are bound to a class itself.

Meaning to access non static methods we need to create an object of the class first, only then we will be able to use its methods.
ex:
```
class Math{
	public int sum(int a, int b){
			return a+b;
	}	

		public int multiply(int a, int b){
			return a*b;
	}
}
```
To access the above methods, we need to create an object of the Math class,
```
Math math = new Math();
int ans = math.sum(2, 3);
```

But, in Java there are classes which are called utility classes, meaning they consist of static methods, and creating an object of that class is not required. 
ex: Math, Arrays etc
We can directly use methods like,
`Math.pow(a, b);` to get a number raised to b
`Math.abs(int x);` to get an absolute value of a number;
`Arrays.sort();` sorts an array in ascending order.

These classes have their constructors private. So when someone tries to create an object of a utility class, they will be warned that they cannot do so. The private constructor will prevent the object instantiation.

Another use case of a Private Constructor
If we want only one object of a class to be instantiated, we can use a Private Constructor.

ex:
```
public class School{
	private static School school;

	private School(){

	}
}

public static School getInstance(){
	if (school == null){
		school = new School(); // the constructor can be called even though it is private because it is being called from the same class, private methods and properties can be accessed only within the same class.
	}
	return school;
	}
}
```

now when we do,
`School school = new School();` // This is not possible because constructor is private

W.K.T its method getInstance is static, we can use that to get an object of School
`School.getInstance();` 

Since, we are calling getInstance() for the first time, the if check in the getInstance method knows that school is null, hence a new instance or object is created and returned.

`School.getInstance();`
Now, the instance won’t be created, because school is not null, hence the same instance will be returned.

3. Default
Any property, class, method without an access modifier is considered default. Default classes, properties and methods can only be accessed from the same package.

ex:
```
class Animal{
	String name;
	int age;

	String getName(){
		return this.name;
	}
}
```
The above example shows a default class, default properties and a default method.

```
Access Modifier                      private   default   protected  public
Same class                           Yes       Yes       Yes        Yes
Same Package                         No        Yes       Yes        Yes
Subclass (Same Package)              No        Yes       Yes        Yes
Subclass (different package)         No        No        Yes        Yes
Different Package (non - subclass)   No        No        No         Yes
```

# Lecture 25
## Static 
When ever we use static with any field, method name etc it becomes part of a class not an instance. Meaning such a property can be directly accessed using the class, there is no need to create an object or instance of it.

ex: If we have to access properties of a class, we usually create an object of the class and access the properties via the object, because the properties are instance properties.

```
public class Student{
	public String Name;
	public int age;
	public int rollNo;

	public static void main(String[] args){
		Student student = new Student();
		student.name = "Taz";
		student.age = 23;
	}
}
```

But static gives us the ability to access properties or methods of a class directly via class.

```
public class Student{
	public static String Name;
	public int age;
	public int rollNo;

	public static void main(String[] args){
		Student.name = "Taz";
	}
}
```

## When should we use ***static*** ?
static is mostly used on properties which will be common among all objects, like school name, count of students etc It also helps save memory as there will be no need to initialize the same property for every object.

ex:
```
public class Student{
	public static count;
	public static schoolName = "St. John's High School";

	public int age;
	public int rollNo;

	public Student(){
		count+=1;
	}

	public static void main(String[] args){
		Student.name = "Taz";
	}
}
```
Now, the properties count and schoolName can be accessed directly via Student.count or Student.schoolName, also since count is a common property which holds the number of students in the school, every time a new object is created of class Student the count increases.

In the below example the count property is not static, meaning now it is an instance property, hence everytime a student object is created the count increases to 1 but it won't store collective count of students objects as it is not a common property but an instance property.

```
public class Student{
	public count;
	public static schoolName = "St. John's High School";

	public int age;
	public int rollNo;

	public Student(){
		count+=1;
	}

	public static void main(String[] args){
		Student.name = "Taz";
	}
}
```

Static method cannot use non-static data member or cannot call a non static method directly.

similarly this and super cannot be used in static context, because this refers to an object but static only deals with the class and super refers to the constructor of the parent but constructor means object and static is at the class level.

***Note***: 
Before any instance of a class is created the static variables are already initialized.

## static block
A static block is a block of code that runs once when the class is first loaded into the memory by the JVM.

```
class Test{
	public static void main(String[] args){
		System.out.println("Hello World!");
	}
}
```
JVM needs the main method to be static as it will not create an instance of class Test to run main method. It will directly use class name and run the main method, like Test.main()

Similarly a static block can be created in a class to initialize any complex variable initialization, validating config at startup etc which needs to be initialized when ever the class is first loaded into the memory.

ex: A database manager, it needs to initalize the size of connection pool, the url etc these can be put under the static block as these are to be used throughout the application lifecycle.

```
public class DatabaseConfig {
    
    private static Properties config = new Properties();
    private static Connection connection;
    
    // Static block for complex initialization
    static {
        try {
            // Load configuration file
            FileInputStream fis = new FileInputStream("config.properties");
            config.load(fis);
            
            // Establish database connection
            String url = config.getProperty("db.url");
            String user = config.getProperty("db.user");
            String password = config.getProperty("db.password");
            
            connection = DriverManager.getConnection(url, user, password);
            
            System.out.println("Database connected successfully");
            
        } catch (Exception e) {
            System.err.println("Failed to initialize database: " + e.getMessage());
            // Handle critical failure
        }
    }
    
    public static Connection getConnection() {
        return connection;
    }
}
```

In the above class we can directly get the database connection using,
```
DatabaseConfig.getConnection();
```
When we call the method getConnection() the class gets loaded in the memory and the static block is run first creating the db connection and the getConnection() method will return it to us.

