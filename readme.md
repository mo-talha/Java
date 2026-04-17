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

3. int = 4 bytes = 32 bits

4. long = 8 bytes = 64 bits
5. float = 4 bytes = 32 bits
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
### Understanding 2D Arrays
```
int[][] nums = new int[3][3]
```
The above line creates an int array of 3 blocks in the memory first. Then it creates 3 separate int arrays of size 3 in the memory and then the main
array stores the addresses of these individual arrays in its 0th, 1st and 2nd indices. 

For us it looks like a matrix but internally this is a main array object in the heap storing addresses of other 3 array objects.

### Running a for loop on 2D Array
```
int[][] = {
	{1, 2, 3, 4},
	{5, 6, 7, 8}
};

for (int i = 0; i < nums.length; i++){
	for (int j = 0; j < nums.length; j++){
		System.out.println(nums[i][j]);
	}
}
```

The loop, nums[0][0] goes in the memory and gets into the first array object in the main array, gets its first element and prints it.

### Understanding Random Access in Arrays
```
int[] nums = new int[3];
```
The above statement creates an array of size 3 lets say in heap at memory address 100. Since it is of type int each of the 3 boxes will be of size
4 bytes or 32 bits.

now when we do, 
```
nums[0] = 1;
nums[1] = 2;
nums[3] = 3;
```
The JVM will store the 1, 2 and 3 in binary form in the boxes.

When we try to access one of these, let's understand how is it possible to access elements from array that fast,
```
System.out.println(nums[1]);
```
W.K.T. the base memory address of the array nums is 100 i.e. is the first box. Now when try to access nums[1], JVM does not traverse from 100 linearly
and then get the element at index but 1, instead it does the following,
1. Gets the base address 100
2. Gets the size of the data type of nums i.e. 4 bytes (int)
3. location = 100 + 4 * index 
so, 100 + (4 * 1) = 104, so JVM will directly go to memory address 104 and from there since it has to read an int type it will add 4 more bytes and it 
will read till 108 so 104 - 108 memory address will have the binary of 2.

Similarly if we access nums[0], it will be 
base address + (data type size * index) 
i.e. 100 + (4 * 0) = 100, from 100 - 104 since it is an int type.

**Note: Size of boolean:**
The size of boolean will be decided by the JVM depending upon the platform. The official Java docs mention 1 byte. But boolean needs only 1 bit 0 means true
1 means false, but JVM is designed to read memory in chunks of min 8 bits it will not read single bits on the memory.

When a variable is created and the program runs the variables are loaded into the RAM, and CPU is designed to read memory in chunks usually like 1 byte, 4 bytes
etc due to this oracle has specified boolean size as 1 byte to not disturb CPU optimizations. This is called memory optimization for CPU needs.

### Understanding Array Index Out of Bounds Exception
Taking the above example if we try to access nums[8] then its location will be 100 + (4 * 8) = 132, this will throw the exception because something else might be
there at memory location 132 to be safe it throws the Exception instead of accessing it.

### How does Random Access on Strings work ?
```
String[] arr = new String[3];
arr[0] = "ron";
arr[1] = "taz";
arr[2] = "pep";

System.out.println(arr[1]);
System.out.println(arr[2]);
```
String is a non-primitive so random access is different compared to a primitive type array. Here if the base memory address is 100, jvm will reach 100 and at 1st
index it will get the reference to the memory address of String object "taz", similarly for "pep". It will pick the values "taz", "pep" from the reference and
then print it.

Now references take 4 bytes on memory, so to pick a reference it will reach 100 + (4 * index) i.e. 100 + (4 * 1), 104 so to get the String at 1st index JVM will
read from 104 - 108.

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

## When should we use static methods ?
static methods are mostly used inisde utility classes, these methods can also be called utility methods, methods which can be handy during development.

ex: We can have a class called Utils and inside this class we can have static methods like to check if an email is valid or not, to get min or max from two numbers, to check if a mobile no is valid or not etc. 

These methods can be common across multiple classes hence they are utility methods and can be declared as static methods inside a utility class.

```
public class Utility{
	public static Boolean isEmailValid(String email){
		if (email.contains("@gmail.com")){
			return true;
		}
		return false;
	}

	public static Boolean isMobileValid(String mobileNo){
		if (mobileNo.contains("+91")){
			return true;
		}
		return false;
	}
}
```

Also we can see that since email, mobileNo are of type String we are able to access the contains() method using dot(.) because contains is a static method inside the String class.


## Static inisde a singleton class
static can be used inside a singleton class, if we have a requirement that there should be only one object of school then we can make use of static.

```
public class School{
	private static School school = new School();

	private School(){

	}

	public School getSchool(){
		return school;
	}
}
```

Now no matter what we create we will get the same school object everytime, since the constructor is private we won't be able to create an object.

```
School school = new School(); // This will not be able to invoke the constructor, as the constructor is private and a private field cannot be accessed outside the class.
```

Hence we have to use the getSchool() method, this will return the object.

<!-- Check if a class can be static or not ?? -->

## Difference b/w static and singleton
Static classes and singleton serve different purposes. Static classes are for utility functions without state, like `MathUtils` or `StringUtils`. They are loaded at class loading time.

Singletons are for managing shared resources that need exactly one instance but with full OOP capabilities. They can implement interfaces, support inheritance, be lazy-loaded and testable with dependency injection.

***Note:***
Use static for stateless utilities, use singleton for stateful resources that need controlled access. Singletons are objects static classes are not.

# Lecture 26
## final Keyword
final keyword is used to prevent inheritance. It can be used on reference variables, methods and classes.

When a variable is made final then the value given to the variable cannot change, the value given to it when initializing it will be its final value. We cannot alter by setter or by accessing via class.

ex:
```
public class MathUtils{
	public static final double pi = 3.1495;

	public void setPi(double value){
		pi = value; // this will also not work
	}
}

MathUtils.pi = 2.22; // This is not possible
```

So if we have any constant values we can create a variable and make it final.

### final on Methods
```
public class AxisBank{
	public final int calculateInterest(int amount, int years){
		// critical business logic here
	}
}

public class SavingsAccount extends AxisBank{
	@override
	public final int calculateInterest(int amount, int years){
		// critical business logic here
	}
}
```

Here we see savings account trying to override the critical method calculateInterest but since the method is final in the parent class the subclasses won't be able to override it.

Hence we can use final to protect critical business logic, this will also indicate to the subclasses that this method cannot be overidden.

Similarly we can make a template methods final, meaning a method in class which is responsible to call other methods to complete an operation in a required sequence can be made final, this way the extending classes won't be able to alter this method. This helps in keeping the flow of main algorithm consistent across other subclasses.

ex:
public abstract class Scraper{
	public final void flow(){
		openBrowser();
		getData();
		loadData();
		processData();
		cleanup();
	}

	public abstract openBrowser();
	// similarly other methods, now scrapers like insta scraper, amazon scraper etc will extend the Scraper abstract class and will override the abstract methods but won't be able to override the flow method, it remains constant maintaing the state of algorithm.
}

## The below is an example of a banking system explaining where and how final can be used 
```
/**
 * Base class for all bank accounts
 * Demonstrates proper use of final methods
 */
public abstract class BankAccount {
    
    // Core state - protected but not directly modifiable
    private String accountNumber;
    private BigDecimal balance;
    private String accountHolder;
    private LocalDateTime openedDate;
    private List<Transaction> transactionHistory;
    
    // Constructor - sets up immutable account data
    public BankAccount(String accountNumber, String accountHolder, BigDecimal initialDeposit) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
        this.balance = initialDeposit;
        this.openedDate = LocalDateTime.now();
        this.transactionHistory = new ArrayList<>();
        
        // Record initial deposit
        recordTransaction("OPEN", initialDeposit);
        
        // Validate account after construction
        validateAccount();
    }
    
    // FINAL - Core banking logic must be consistent across all account types
    public final boolean withdraw(BigDecimal amount) {
        // Validate inputs
        if (amount == null || amount.compareTo(BigDecimal.ZERO) <= 0) {
            throw new IllegalArgumentException("Invalid withdrawal amount");
        }
        
        // Check sufficient funds (uses abstract method - different per account)
        if (!hasSufficientFunds(amount)) {
            return false;
        }
        
        // Apply withdrawal (final - must be consistent)
        BigDecimal newBalance = balance.subtract(amount);
        setBalance(newBalance);
        
        // Record transaction
        recordTransaction("WITHDRAW", amount.negate());
        
        // Notify account holder
        notifyWithdrawal(amount);
        
        return true;
    }
    
    // FINAL - Deposit logic must be consistent
    public final void deposit(BigDecimal amount) {
        if (amount == null || amount.compareTo(BigDecimal.ZERO) <= 0) {
            throw new IllegalArgumentException("Invalid deposit amount");
        }
        
        BigDecimal newBalance = balance.add(amount);
        setBalance(newBalance);
        
        recordTransaction("DEPOSIT", amount);
        notifyDeposit(amount);
    }
    
    // FINAL - Getter for immutable data
    public final String getAccountNumber() {
        return accountNumber;
    }
    
    // FINAL - Getter for immutable data
    public final String getAccountHolder() {
        return accountHolder;
    }
    
    // FINAL - Getter for immutable data
    public final LocalDateTime getOpenedDate() {
        return openedDate;
    }
    
    // FINAL - Thread-safe balance access
    public final synchronized BigDecimal getBalance() {
        return balance;
    }
    
    // FINAL - Transaction history must be consistent
    public final List<Transaction> getTransactionHistory() {
        return Collections.unmodifiableList(transactionHistory);
    }
    
    // Protected final - Child classes can use but not override
    protected final void setBalance(BigDecimal newBalance) {
        this.balance = newBalance;
    }
    
    // Protected final - Record transactions consistently
    protected final void recordTransaction(String type, BigDecimal amount) {
        Transaction txn = new Transaction(
            UUID.randomUUID().toString(),
            type,
            amount,
            LocalDateTime.now(),
            balance
        );
        transactionHistory.add(txn);
    }
    
    // Private final - Internal validation, can't be overridden
    private final void validateAccount() {
        if (accountNumber == null || accountNumber.trim().isEmpty()) {
            throw new IllegalStateException("Account number required");
        }
        if (accountHolder == null || accountHolder.trim().isEmpty()) {
            throw new IllegalStateException("Account holder required");
        }
        if (balance == null || balance.compareTo(BigDecimal.ZERO) < 0) {
            throw new IllegalStateException("Initial balance invalid");
        }
    }
    
    // ABSTRACT - Must be implemented by subclasses
    protected abstract boolean hasSufficientFunds(BigDecimal amount);
    
    // Hook methods - Optional customization
    protected void notifyWithdrawal(BigDecimal amount) {
        // Default: do nothing
    }
    
    protected void notifyDeposit(BigDecimal amount) {
        // Default: do nothing
    }
    
    // Inner class for transactions (immutable)
    public static final class Transaction {
        private final String id;
        private final String type;
        private final BigDecimal amount;
        private final LocalDateTime timestamp;
        private final BigDecimal balanceAfter;
        
        public Transaction(String id, String type, BigDecimal amount, 
                          LocalDateTime timestamp, BigDecimal balanceAfter) {
            this.id = id;
            this.type = type;
            this.amount = amount;
            this.timestamp = timestamp;
            this.balanceAfter = balanceAfter;
        }
        
        // FINAL getters for immutable data
        public final String getId() { return id; }
        public final String getType() { return type; }
        public final BigDecimal getAmount() { return amount; }
        public final LocalDateTime getTimestamp() { return timestamp; }
        public final BigDecimal getBalanceAfter() { return balanceAfter; }
    }
}

/**
 * Concrete implementation - Savings account
 */
public class SavingsAccount extends BankAccount {
    
    private BigDecimal interestRate;
    private int minimumBalance;
    
    public SavingsAccount(String accountNumber, String accountHolder, 
                          BigDecimal initialDeposit, BigDecimal interestRate) {
        super(accountNumber, accountHolder, initialDeposit);
        this.interestRate = interestRate;
        this.minimumBalance = 1000; // Minimum ₹1000
    }
    
    // Must implement abstract method
    @Override
    protected boolean hasSufficientFunds(BigDecimal amount) {
        // Savings accounts can't go below minimum balance
        BigDecimal balanceAfter = getBalance().subtract(amount);
        return balanceAfter.compareTo(BigDecimal.valueOf(minimumBalance)) >= 0;
    }
    
    // Can override hook methods
    @Override
    protected void notifyWithdrawal(BigDecimal amount) {
        if (amount.compareTo(BigDecimal.valueOf(50000)) > 0) {
            sendSMS("Large withdrawal: " + amount);
        }
    }
    
    private void sendSMS(String message) {
        System.out.println("SMS: " + message);
    }
    
    // Calculate interest - not final, can be customized
    public BigDecimal calculateInterest() {
        return getBalance().multiply(interestRate).divide(BigDecimal.valueOf(100));
    }
}

// Usage example:
public class BankingDemo {
    public static void main(String[] args) {
        SavingsAccount account = new SavingsAccount(
            "ACC123", "John Doe", new BigDecimal("50000"), new BigDecimal("3.5")
        );
        
        // Core operations are FINAL - consistent across all account types
        account.withdraw(new BigDecimal("10000"));
        account.deposit(new BigDecimal("20000"));
        
        // Can't override withdraw() - banking logic is safe!
        // account.withdraw = new implementation? NO - final prevents this
        
        System.out.println("Balance: " + account.getBalance());
        System.out.println("Interest: " + account.calculateInterest());
    }
}
```
# Lecture - 14 (Coder Army)
## Objects Deep Dive (Size of an object, call by value, call by reference, shallow vs deep copy)
```
public class Student{
	int rollNo;
	String name;
	int age;
	String parentName;
	
	public Student(int rollNo, String name, int age, String parentName){
		this.rollNo = rollNo;
		this.name = name;
		this.age = age;
		this.parentName = parentName;
	}
	
	public static void main(String[] args){
		Student student1 = new Student(1, "Mohammed Talha", 13, "Hashmathulla");
	}
}
```
To determine the size of object `student1` we it is not how we do it for primitives. Here we will take sizes of data types of each individual field in the
class, like rollNo is of type int so it takes 4 bytes, name is type of String, String stores reference and reference takes either 4 bytes or 8 bytes here let's
consider 4 bytes, similarly 4 bytes for age and 4 bytes for parentName.
so, 
4 bytes + 4 bytes + 4 bytes + 4 bytes = 16 bytes, but the object takes more than this on memory lets see why.

### Object Size depends on,
1. Header Size/Object headers
2. Exact fields (16 bytes which we just calculated above)
3. Padding

### Header Size/ Object headers:
This is data like Mark Words and Class Pointer. Under Mark Words there is information like what locks are being used, synchronization mechanism, garbage collection.
Class Pointer is a memory reference of the object.
So Mark Words take - 8 bytes
Class Pointer (since it is a reference) - it can take 4 bytes/8bytes (we consider 4 bytes).

### Exact Data 
We just saw above the total size taken by the variables and their data types.

### Padding
Since CPU is optimized to read in chunks of 8 bytes padding allows us to support this optimization. If we consider the total size of the above object `student1`
till now i.e. Header size + Exact field = 12 + 16 = 28. 

Now 28 is not a multiple of 8 the closest multiple of 8 to 28 is 32, hence we pad 28 with 4 more bytes to make it 32 bytes. 

So overall the `student1` object takes 32 bytes of memory.

Another example if there is a class,
```
public class Person{
	byte age;
}
```
Header Size would be - 12 bytes
Exact size - 1 byte for age
Padding - 12 + 1 = 13, this not a multiple of 8 the next closest multiple is 16 hence we pad this object with 3 more bytes making it ***16 bytes***.

### Call by Value and Call by Reference in Java (Note: Java is only call by Value)
```
public class Main{
	public static void main(String[] args){
		int a = 3;
		int b = 4;
		
		System.out.println(a, b); // 3, 4
		
		addTen(a, b);	
		
		System.out.println(a, b); // 3, 4
	}
	
	public static void addTen(int a, int b){
		a + 10;
		b + 10;
	} 
}
```
In the above code the first print statement will print 4, 5
Second print statement will also print 4, 5. The addTen method has no effect on variable a and b inside the main method because when we call addTen and pass
a and b, addTen in its own call stack it will have its own a and b which will have values 3 and 4 so addition will be on these own variables of addTen a and b
which are separate from a and b of the main method.

Since Java is call by value, when we called addTen values of a and b were separately copied or picked up addTen or sent to addTen, addTen never referenced a and b
of main method but values of a and b from main method were passed to the a and b of addTen.

### What happens when objects of user defined classes are passed ?
```
class Random{
	int a;
	int b;
	
	public Random(int a, int b){
		this.a = a;
		this.b = b;
	}
	
	public Random(Random r){
		this.a = r.a;
		this.b = r.b;
	}
}

public class Main{
	public static void main(String[] args){
		Random num = new Random(3, 4);
		
		System.out.println(num.a, num.b); // 3, 4
		
		addTen(num);	
		
		System.out.println(num.a, num.b); // 13, 14
	}
	
	public static void addTen(Random r){
		r.a = r.a + 10;
		r.b = r.b + 10;
	} 
}
```
This is still call by value, but the value this time is the address of num we are sending the address of num to addTen, and internally addTen will
now be pointing to same object num in the heap and any changes done by addTen will be on a and b of the same object.

### Deep Copy vs Shallow Copy
```
class Random{
	int a;
	int b;
	
	public Random(int a, int b){
		this.a = a;
		this.b = b;
	}
	
	public Random(Random r){
		this.a = r.a;
		this.b = r.b;
	}
}

public class Main{
	public static void main(String[] args){
		Random num = new Random(3, 4);
		Random num2 = new Random(num);

		System.out.println(num.a, num.b); // 3, 4
		
		addTen(num2);	

		System.out.println(num.a, num.b); // 3, 4
		System.out.println(num2.a, num2.b); // 13, 14
	}
	
	public static void addTen(Random r){
		r.a = r.a + 10;
		r.b = r.b + 10;
	} 
}
```

In the above code snippet `num2` gets the reference of num but still num.a and num.b won't be changed as num2 is a different object in the memory and num1 is a 
separate object. So even though num2 receives the reference value of num still the constructor of num2 is just picking the values of num.a and num.b and setting
those values to num2.a and num2.b.

Hence we run `addTen(num2)` then 10 is added to num2s variables a and b which are part of a separate random object in the heap.

***This is called Deep Copy***

### Shallow Copy
```
class Random{
	int a;
	int b;
	
	public Random(int a, int b){
		this.a = a;
		this.b = b;
	}
	
	public Random(Random r){
		this.a = r.a;
		this.b = r.b;
	}
}

public class Main{
	public static void main(String[] args){
		Random num = new Random(3, 4);
		Random num2 = num;

		System.out.println(num.a, num.b); // 3, 4
		
		addTen(num2);	

		System.out.println(num.a, num.b); // 3, 4
		System.out.println(num2.a, num2.b); // 13, 14
	}
	
	public static void addTen(Random r){
		r.a = r.a + 10;
		r.b = r.b + 10;
	} 
}
```
In the above code num2 is pointing to num and any changes done by num2 will affect the same object hence this is called a shallow copy.

So,
Deep Copy - Creates a new object along with separate copies of all referenced objects, ensuring complete independence b/w original and copied objects. Any change
made to one object does not affect the other.

Shallow Copy - Creates a new object but does not duplicate referenced objects, instead it copies their references. Both the original and copied objects point to
the same memory location for reference fields.

Default behaviour of Object.clone() method is shallow copy.
Primitive fields are copied, while non-primitives are shared.

# Lecture - 18 (Coder Army) Autoboxing, Abstract classes and Pojos
## Why only 1 public class per file ?
```
Main.java
public class Main{
	public static void main(String[] args){
		// code here
	}
}

class Person{
	String name;
}
```

In java we can have only one public class per file, we can also have multiple sub classes within a file but public file must always be only one, also the name of
the public class must be same as that of the file name.
This is because JVM can only access public classes from packages and if the class is public and main method is public it will easily access it.
If there are multiple public classes then JVM will get confused from which public class it should call the main method. To avoid and keep things simple one public class and one public main method.

Now JVM has access to only one public class and when the file is run it will easily pick the main method of the public class.

### Why the public class name and file name must be same ?
This is because when JVM runs main method, that it loads the file for example Main.java in the memory, and since the file name and class name are same it will simply use the file name Main (.) dot operator and will call the main method of the file `Main.main()`.

That's why Java has the rule to keep file name and class name same so that it is easier for JVM to directly know the class name by just looking at the file name and it can call the main method easily.

## What are Wrapper classes ?
```
int     --> Integer
long    --> Long
float   --> Float
double  --> Double
boolean --> Boolean
byte    --> Byte
```
In Java every primitve data type has a Wrapper class for itself. 
A Wrapper class can also be use to store an integer and also the primitive type int, both help us store an integer type. But the necessity to have wrapper classes is,
1. Collection Framework - Collections are designed to work with Wrapper classes.
2. OOPs - Since Java is an Object oriented programming language it needs to have class substitutes of primitives.

### Why do primitves exist then ?
Primitives exist because of legacy, since Java was around at the time of C and C++ and these 2 languages had primitive data types in them, so Java to make it easier for the devs transition from C and C++ they also decided to keep primitives.

And most important primitives are way faster compared to wrapper classes, because a primitive is initialized in the stack memory and a wrapper class object is initialized in the heap memory.

```
int x = 10 // Inside Stack Memory
Integer x = new Integer(10); // We know about the whole object creation phase and then the object gets created in the heap and x stores the reference to the object.
```

Also Wrapper classes help us to have custom methods and fields which can be handy when dealing with a certain data type, like Integer class has a property/field with which we can use the max integer value, like `Integer.MAX_VALUE`, it has a method to get a max number among 2 numbers like `Integer.max(1, 2);` etc 

### Autoboxing and Unboxing
```
// Autoboxing
int a = 10;
Integer b = a;

// Unboxing
Integer a = 10;
int b = a;
```
Here int a will be automatically converted to object of Integer internally by the compiler. The compiler will use the static method valueOf() of class Integer.
`Integer.valueOf(10);` this automatic conversion of a primitive to a Wrapper type is called autoboxing.

In unboxing int b will use the instance or object method of Integer a intValue() and it will get the primitive version 10. 
`a.intValue();` this is a get method which returns the primitive value of the Wrapper object.

Autoboxing works at 3 places:
1. Assignments (we just saw this above)
2. Method calls
3. Arithmetic operations

```
public void printInteger(Integer x){
	System.out.println(x);
}

int a = 10;
printInteger(a); // here x would do x = Integer.valueOf(x) and then print it this is autoboxing.

// Arithmetic Operations
Integer a = 5;
Integer b = 3;

int sum = a + b; // here compiler will do sum = a.intValue() + b.intValue();
```

### NullPointerException in Unboxing
```
Integer a = null;
int b = a;

// Internally b will do a.intValue() but this will return null and in Java int can store 0 but it cannot store null hence a NullPointerException will be raised.
```
The Wrappers since they are objects can reference null but primitives cannot, so we must be careful because in this case of Unboxing we will not get any warning.

### == operator vs equals()
```
int a = 4;
int b = 4;

System.out.println(a == b);

Integer c = 200;
Integer d = 200;

System.out.println(c == d);

System.out.println(c.equals(d));
```

== in case of primitives checks the actual values so it checks 4 == 4 and prints True. 
== in case of objects checks for reference, is c and d both pointing to the same reference which in this case is false as both are separate Integer objects on heap because. Hence it will print false.

The last line will print True. Because equals() method checks the actual values. So equals() for non primitives and == checks for their reference values.

== checks the same thing in case of primitives as well but primitives are values themselves and in case of non primitives the real objects are on heap and variables stores references and references for objects in heap are different thats why it prints false.

### Edge Case (Caching of Integers)
Java caches commonly used integers from -127 to 128 so even if we do,
```
Integer a = 100;
Integer b = 100;

System.out.println(a == b); // This will print true
```
This will print true because Java internally creates objects of commonly used integers and there reference variables are stored in stack.

Now we create a and b which are in the common range, then the constructor of Integer class will check in the memory and lets say it finds a variable h pointing towards 100 in the memory it will assign a = h and b = h. Now a and b are pointing to the same object and a and b have same references hence we get true as the output.

200 was out of this range so new objects were created and we got false.

So the Integer Wrapper class would look something like this,
```
public class Integer{
	int value;
	public Integer valueOf(int x){
		//
	}

	public int intValue(Integer val){
		return val.value;
	}

	public boolean equals(Integer a, Integer b){
		if (a.intValue == b.intValue){
			return true;
		} else {
			return false;
		}
	}
}
``` 