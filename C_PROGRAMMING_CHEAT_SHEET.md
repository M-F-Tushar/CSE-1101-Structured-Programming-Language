# C Programming Comprehensive Cheat Sheet 📚

## Table of Contents
1. [Data Types, Variables and Data Output](#1-data-types-variables-and-data-output)
2. [Getting Input with scanf()](#2-getting-input-with-scanf)
3. [Operators](#3-operators)
4. [Program Control](#4-program-control)
5. [Loops](#5-loops)
6. [Arrays](#6-arrays)
7. [Pointers](#7-pointers)
8. [Characters and Strings](#8-characters-and-strings)
9. [Functions](#9-functions)
10. [Structures](#10-structures)
11. [Unions](#11-unions)

---

## 1. Data Types, Variables and Data Output

### 1.1 Data Types

#### Integer Types (int)
**Definition:** Whole numbers without decimal points.

**Explanation:** The `int` data type stores integer values (positive, negative, or zero). It typically uses 4 bytes of memory and can store values from -2,147,483,648 to 2,147,483,647.

**Example:**
```c
#include <stdio.h>
int main() {
    int age = 25;
    int temperature = -10;
    printf("Age: %d, Temperature: %d\n", age, temperature);
    return 0;
}
// Output: Age: 25, Temperature: -10
```

#### Floating Point Types (float, double)
**Definition:** Numbers with decimal points for representing real numbers.

**Explanation:** `float` (4 bytes) stores single-precision floating-point numbers with ~6-7 decimal digits of precision. `double` (8 bytes) stores double-precision floating-point numbers with ~15-16 decimal digits.

**Example:**
```c
#include <stdio.h>
int main() {
    float pi = 3.14159f;
    double precise_pi = 3.14159265358979;
    printf("Float: %f\n", pi);
    printf("Double: %lf\n", precise_pi);
    return 0;
}
// Output: Float: 3.141590
//         Double: 3.141593
```

#### Character Type (char)
**Definition:** Single character or small integer values.

**Explanation:** The `char` data type stores a single character using 1 byte of memory. Characters are stored as ASCII values (0-255).

**Example:**
```c
#include <stdio.h>
int main() {
    char letter = 'A';
    char digit = '5';
    printf("Letter: %c, Digit: %c\n", letter, digit);
    return 0;
}
// Output: Letter: A, Digit: 5
```

### 1.2 Variables

**Definition:** Named memory locations that store data values.

**Explanation:** Variables must be declared before use, specifying the data type and variable name. Variable names should be meaningful and follow C naming conventions (alphanumeric and underscore, starting with a letter or underscore).

**Example:**
```c
#include <stdio.h>
int main() {
    int count = 10;
    float price = 99.99;
    char grade = 'A';
    
    printf("Count: %d\n", count);
    printf("Price: %.2f\n", price);
    printf("Grade: %c\n", grade);
    return 0;
}
```

### 1.3 Data Output (printf)

**Definition:** Function to display formatted output to the console.

**Explanation:** `printf()` outputs data to the screen using format specifiers: `%d` (int), `%f` (float), `%c` (char), `%s` (string), `%lf` (double).

**Example:**
```c
#include <stdio.h>
int main() {
    int i = 100;
    i = i + i;
    printf("V1:%d V2:%d\n", i+i, i);
    return 0;
}
// Output: V1:400 V2:200
```

### 1.4 Variable Arithmetic

**Definition:** Performing mathematical operations on variables.

**Explanation:** Variables can be used in arithmetic expressions. The result can be stored back in the same variable or a new variable.

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 10, b = 20;
    int sum = a + b;
    int difference = b - a;
    printf("Sum: %d, Difference: %d\n", sum, difference);
    return 0;
}
// Output: Sum: 30, Difference: 10
```

---

## 2. Getting Input with scanf()

### 2.1 scanf() Function

**Definition:** Function to read formatted input from the user.

**Explanation:** `scanf()` reads input from the keyboard and stores it in variables. The `&` operator (address-of operator) is used to pass the memory address of variables to scanf(). Format specifiers must match the variable type.

**Example:**
```c
#include <stdio.h>
int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    printf("You entered: %d\n", num);
    return 0;
}
```

### 2.2 Reading Multiple Values

**Definition:** Reading multiple input values in a single scanf() statement.

**Explanation:** Multiple format specifiers can be used in one scanf() call, separated by spaces or other delimiters. Values are read in the order specified.

**Example:**
```c
#include <stdio.h>
int main() {
    int i;
    float j, sum;
    printf("Enter numbers: ");
    scanf("%d%f", &i, &j);
    sum = i + j;
    printf("Sum: %f\n", sum);
    printf("Triple: %f\n", 3*sum);
    return 0;
}
```

### 2.3 Input Format Specifiers

**Definition:** Special characters that specify the type of data to read.

**Explanation:**
- `%d` - integer
- `%f` - float
- `%lf` - double
- `%c` - character
- `%s` - string

**Example:**
```c
#include <stdio.h>
int main() {
    int age;
    float height;
    char initial;
    
    printf("Enter age, height, and initial: ");
    scanf("%d %f %c", &age, &height, &initial);
    
    printf("Age: %d, Height: %.2f, Initial: %c\n", 
           age, height, initial);
    return 0;
}
```

---

## 3. Operators

### 3.1 Arithmetic Operators

**Definition:** Operators used to perform basic mathematical operations.

**Explanation:** 
- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Division
- `%` Modulus (remainder)

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 10, b = 3;
    printf("Addition: %d\n", a + b);      // 13
    printf("Subtraction: %d\n", a - b);   // 7
    printf("Multiplication: %d\n", a * b);// 30
    printf("Division: %d\n", a / b);      // 3
    printf("Modulus: %d\n", a % b);       // 1
    return 0;
}
```

### 3.2 Relational Operators

**Definition:** Operators that compare two values and return true (1) or false (0).

**Explanation:**
- `==` Equal to
- `!=` Not equal to
- `>` Greater than
- `<` Less than
- `>=` Greater than or equal to
- `<=` Less than or equal to

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 3, b = 5, c;
    a = (a > 3) + (b <= 5);  // (0) + (1) = 1
    b = (a == 3) + ((b-2) >= 3);  // (0) + (1) = 1
    c = (b != 1);  // 0
    printf("%d %d %d\n", a, b, c);
    return 0;
}
// Output: 1 1 0
```

### 3.3 Logical Operators

**Definition:** Operators that perform logical operations on boolean expressions.

**Explanation:**
- `&&` Logical AND (both conditions must be true)
- `||` Logical OR (at least one condition must be true)
- `!` Logical NOT (negates the condition)

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 4, b = 3, c = 5;
    printf("%d\n", (a < b) == !(c > b));
    // (4 < 3) == !(5 > 3)
    // 0 == !1
    // 0 == 0
    // Result: 1
    return 0;
}
// Output: 1
```

### 3.4 Increment and Decrement Operators

**Definition:** Operators that increase or decrease a variable's value by 1.

**Explanation:**
- `++` Increment (adds 1)
  - `++x` Pre-increment: increment first, then use
  - `x++` Post-increment: use first, then increment
- `--` Decrement (subtracts 1)
  - `--x` Pre-decrement
  - `x--` Post-decrement

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 1;
    printf("%d\n", (a > 0) && (--a > 0));
    // (1 > 0) && (0 > 0)
    // 1 && 0
    // Result: 0
    return 0;
}
// Output: 0
```

### 3.5 Assignment Operators

**Definition:** Operators that assign values to variables.

**Explanation:**
- `=` Simple assignment
- `+=` Add and assign
- `-=` Subtract and assign
- `*=` Multiply and assign
- `/=` Divide and assign
- `%=` Modulus and assign

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 4, b = 3, c = 1;
    a += b -= ++c;  // Executed right to left
    // ++c = 2
    // b = b - 2 = 3 - 2 = 1
    // a = a + 1 = 4 + 1 = 5
    printf("%d %d %d\n", a, b, c);
    return 0;
}
// Output: 5 1 2
```

### 3.6 Conditional (Ternary) Operator

**Definition:** A shorthand if-else operator with three operands.

**Explanation:** Syntax: `condition ? expression_if_true : expression_if_false`

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 10, b = 20;
    int max = (a > b) ? a : b;
    printf("Maximum: %d\n", max);
    return 0;
}
// Output: Maximum: 20
```

---

## 4. Program Control

### 4.1 if Statement

**Definition:** Executes a block of code if a condition is true.

**Explanation:** The `if` statement evaluates a boolean expression and executes the code block only if the condition is true (non-zero).

**Example:**
```c
#include <stdio.h>
int main() {
    int age = 18;
    if (age >= 18) {
        printf("You are an adult.\n");
    }
    return 0;
}
// Output: You are an adult.
```

### 4.2 if-else Statement

**Definition:** Executes one block if condition is true, another if false.

**Explanation:** Provides an alternative path of execution when the condition is false.

**Example:**
```c
#include <stdio.h>
int main() {
    int num = 5;
    if (num % 2 == 0) {
        printf("%d is even.\n", num);
    } else {
        printf("%d is odd.\n", num);
    }
    return 0;
}
// Output: 5 is odd.
```

### 4.3 Nested if-else (else if)

**Definition:** Multiple conditions checked in sequence.

**Explanation:** Used when there are multiple mutually exclusive conditions to check.

**Example:**
```c
#include <stdio.h>
int main() {
    float i, j, k;
    printf("Enter grades: ");
    scanf("%f%f%f", &i, &j, &k);
    
    if(i <= j && i <= k) {
        printf("%.2f ", i);
        if(j < k)
            printf("%.2f %.2f\n", j, k);
        else
            printf("%.2f %.2f\n", k, j);
    }
    else if(j <= i && j <= k) {
        printf("%.2f ", j);
        if(i < k)
            printf("%.2f %.2f\n", i, k);
        else
            printf("%.2f %.2f\n", k, i);
    }
    else {
        printf("%.2f ", k);
        if(j < i)
            printf("%.2f %.2f\n", j, i);
        else
            printf("%.2f %.2f\n", i, j);
    }
    return 0;
}
```

### 4.4 switch Statement

**Definition:** Multi-way branch statement that tests a variable against multiple values.

**Explanation:** More efficient than multiple if-else when checking a variable against several constant values. Each case must end with `break` to prevent fall-through.

**Example:**
```c
#include <stdio.h>
int main() {
    int day = 3;
    switch(day) {
        case 1:
            printf("Monday\n");
            break;
        case 2:
            printf("Tuesday\n");
            break;
        case 3:
            printf("Wednesday\n");
            break;
        default:
            printf("Other day\n");
    }
    return 0;
}
// Output: Wednesday
```

### 4.5 Conditional Expressions

**Definition:** Using comparison and logical operators to create conditions.

**Explanation:** Conditions evaluate to 1 (true) or 0 (false) and can be combined using logical operators.

**Example:**
```c
#include <stdio.h>
int main() {
    int x = 5, y = 10;
    if (x > 0 && y > 0) {
        printf("Both positive\n");
    }
    if (x == 5 || y == 5) {
        printf("At least one is 5\n");
    }
    return 0;
}
```

---

## 5. Loops

### 5.1 for Loop

**Definition:** Loop that repeats a block of code a specific number of times.

**Explanation:** Syntax: `for(initialization; condition; increment/decrement)`. The loop continues as long as the condition is true.

**Example:**
```c
#include <stdio.h>
int main() {
    int i;
    for (i = 1; i <= 5; i++) {
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
// Output: 1 2 3 4 5
```

### 5.2 while Loop

**Definition:** Loop that repeats as long as a condition is true.

**Explanation:** The condition is checked before each iteration. If initially false, the loop body never executes.

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 256, b = 4;
    int count = 0;
    while(a != b) {
        b = b * b;
        count++;
    }
    printf("Loop executed %d times\n", count);
    return 0;
}
// Output: Loop executed 2 times
// Iteration 1: b = 4*4 = 16
// Iteration 2: b = 16*16 = 256
```

### 5.3 do-while Loop

**Definition:** Loop that executes at least once, then repeats while condition is true.

**Explanation:** The condition is checked after each iteration, guaranteeing at least one execution.

**Example:**
```c
#include <stdio.h>
int main() {
    int i = 1;
    do {
        printf("%d ", i);
        i++;
    } while (i <= 5);
    printf("\n");
    return 0;
}
// Output: 1 2 3 4 5
```

### 5.4 Nested Loops

**Definition:** Loops inside other loops.

**Explanation:** The inner loop completes all its iterations for each iteration of the outer loop. Commonly used for 2D patterns and matrix operations.

**Example:**
```c
#include <stdio.h>
int main() {
    int i, j;
    for (i = 1; i <= 5; i++) {
        for (j = 1; j <= i; j++) {
            printf("*");
        }
        printf("\n");
    }
    return 0;
}
/*
Output:
*
**
***
****
*****
*/
```

### 5.5 break Statement

**Definition:** Immediately exits the loop.

**Explanation:** Terminates the nearest enclosing loop and transfers control to the statement following the loop.

**Example:**
```c
#include <stdio.h>
int main() {
    int i;
    for (i = 1; i <= 10; i++) {
        if (i == 5) {
            break;
        }
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
// Output: 1 2 3 4
```

### 5.6 continue Statement

**Definition:** Skips the rest of the current iteration and moves to the next.

**Explanation:** Jumps to the next iteration of the loop, skipping any code below it in the current iteration.

**Example:**
```c
#include <stdio.h>
int main() {
    int i;
    for (i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;
        }
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
// Output: 1 2 4 5
```

---

## 6. Arrays

### 6.1 One-Dimensional Arrays

**Definition:** A collection of elements of the same data type stored in contiguous memory locations.

**Explanation:** Arrays are declared with a fixed size and accessed using zero-based indexing. Syntax: `type arrayName[size];`

**Example:**
```c
#include <stdio.h>
int main() {
    int numbers[5] = {10, 20, 30, 40, 50};
    int i;
    
    for (i = 0; i < 5; i++) {
        printf("numbers[%d] = %d\n", i, numbers[i]);
    }
    return 0;
}
/*
Output:
numbers[0] = 10
numbers[1] = 20
numbers[2] = 30
numbers[3] = 40
numbers[4] = 50
*/
```

### 6.2 Array Initialization

**Definition:** Assigning values to array elements at declaration.

**Explanation:** Arrays can be initialized with values in curly braces. If fewer values are provided than the size, remaining elements are set to 0.

**Example:**
```c
#include <stdio.h>
int main() {
    int a[3] = {4, 2, 0};
    int b[3] = {2, 3, 4};
    int i;
    
    printf("Array a: ");
    for(i = 0; i < 3; i++)
        printf("%d ", a[i]);
    printf("\n");
    
    return 0;
}
// Output: Array a: 4 2 0
```

### 6.3 Array Manipulation

**Definition:** Accessing and modifying array elements using indices.

**Explanation:** Array elements can be accessed and modified using the index operator `[]`. Indices start at 0.

**Example:**
```c
#include <stdio.h>
int main() {
    int i, a[3] = {4, 2, 0}, b[3] = {2, 3, 4};
    
    for(i = 0; i < 3; i++)
        a[b[i]-a[2-i]]++;
    
    // Iteration breakdown:
    // i=0: a[b[0]-a[2]] = a[2-0]++ = a[2]++ => a[2]=1
    // i=1: a[b[1]-a[1]] = a[3-2]++ = a[1]++ => a[1]=3
    // i=2: a[b[2]-a[0]] = a[4-4]++ = a[0]++ => a[0]=5
    
    printf("Result: ");
    for(i = 0; i < 3; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
// Output: Result: 5 3 1
```

### 6.4 Two-Dimensional Arrays

**Definition:** Arrays with rows and columns (matrix).

**Explanation:** Declared as `type arrayName[rows][cols];`. Accessed using two indices: `array[row][col]`.

**Example:**
```c
#include <stdio.h>
int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    int i, j;
    
    for(i = 0; i < 3; i++) {
        for(j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    return 0;
}
/*
Output:
1 2 3
4 5 6
7 8 9
*/
```

### 6.5 Array Size

**Definition:** The number of elements an array can hold.

**Explanation:** The size must be a constant expression and is specified at declaration. The total memory used is `size * sizeof(element_type)`.

**Example:**
```c
#include <stdio.h>
int main() {
    int arr[10];
    printf("Array size: %d elements\n", 10);
    printf("Memory used: %lu bytes\n", sizeof(arr));
    printf("Size of each element: %lu bytes\n", sizeof(arr[0]));
    return 0;
}
```

---

## 7. Pointers

### 7.1 Pointer Basics

**Definition:** A variable that stores the memory address of another variable.

**Explanation:** Pointers are declared using the `*` operator. The `&` operator gets the address of a variable, and `*` dereferences (accesses the value at) a pointer.

**Example:**
```c
#include <stdio.h>
int main() {
    int *ptr, i = 10;
    ptr = &i;
    i += 20;
    printf("Val = %d\n", *ptr);
    return 0;
}
// Output: Val = 30
```

### 7.2 Pointer Declaration

**Definition:** Declaring a variable to hold memory addresses.

**Explanation:** Syntax: `type *pointerName;`. The pointer stores addresses of variables of the specified type.

**Example:**
```c
#include <stdio.h>
int main() {
    int num = 100;
    int *ptr;
    ptr = &num;
    
    printf("Value of num: %d\n", num);
    printf("Address of num: %p\n", (void*)&num);
    printf("Value in ptr: %p\n", (void*)ptr);
    printf("Value at address ptr: %d\n", *ptr);
    return 0;
}
```

### 7.3 Address-of Operator (&)

**Definition:** Operator that returns the memory address of a variable.

**Explanation:** The `&` operator is used to get the address of a variable, which can be stored in a pointer.

**Example:**
```c
#include <stdio.h>
int main() {
    int x = 42;
    printf("Value: %d\n", x);
    printf("Address: %p\n", (void*)&x);
    return 0;
}
```

### 7.4 Dereference Operator (*)

**Definition:** Operator that accesses the value at the address stored in a pointer.

**Explanation:** The `*` operator is used to access or modify the value stored at the memory address contained in the pointer.

**Example:**
```c
#include <stdio.h>
int main() {
    int value = 50;
    int *ptr = &value;
    
    printf("Value: %d\n", value);
    printf("Value via pointer: %d\n", *ptr);
    
    *ptr = 100;  // Modify value through pointer
    printf("Modified value: %d\n", value);
    return 0;
}
// Output: Value: 50
//         Value via pointer: 50
//         Modified value: 100
```

### 7.5 Pointers and Functions

**Definition:** Using pointers to pass variables by reference to functions.

**Explanation:** Passing the address of a variable allows a function to modify the original variable (pass by reference).

**Example:**
```c
#include <stdio.h>

void swap(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 10, y = 20;
    printf("Before swap: x=%d, y=%d\n", x, y);
    swap(&x, &y);
    printf("After swap: x=%d, y=%d\n", x, y);
    return 0;
}
// Output: Before swap: x=10, y=20
//         After swap: x=20, y=10
```

### 7.6 Pointers and Arrays

**Definition:** Arrays and pointers are closely related; an array name is a pointer to its first element.

**Explanation:** `arr[i]` is equivalent to `*(arr + i)`. Pointer arithmetic allows traversing arrays.

**Example:**
```c
#include <stdio.h>
int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr;
    int i;
    
    for(i = 0; i < 5; i++) {
        printf("arr[%d] = %d, *(ptr+%d) = %d\n", 
               i, arr[i], i, *(ptr + i));
    }
    return 0;
}
```

---

## 8. Characters and Strings

### 8.1 Character Type

**Definition:** Data type for storing single characters.

**Explanation:** Characters are stored as 8-bit integers representing ASCII codes (0-255). Single quotes are used for character literals.

**Example:**
```c
#include <stdio.h>
int main() {
    char ch = 'A';
    printf("Character: %c\n", ch);
    printf("ASCII value: %d\n", ch);
    return 0;
}
// Output: Character: A
//         ASCII value: 65
```

### 8.2 ASCII Table

**Definition:** Standard encoding system mapping characters to integer values.

**Explanation:** ASCII (American Standard Code for Information Interchange) assigns numbers 0-127 to characters. Extended ASCII uses 0-255.

**Example:**
```c
#include <stdio.h>
int main() {
    int i;
    printf("Some ASCII characters:\n");
    for(i = 65; i <= 90; i++)
        printf("Char = %c, ASCII = %d\n", i, i);
    return 0;
}
// Output: Displays uppercase letters A-Z with their ASCII codes
```

### 8.3 String Basics

**Definition:** Array of characters terminated by a null character (`\0`).

**Explanation:** Strings in C are character arrays. The null terminator marks the end of the string.

**Example:**
```c
#include <stdio.h>
int main() {
    char name[20] = "John";
    printf("Name: %s\n", name);
    printf("First char: %c\n", name[0]);
    return 0;
}
// Output: Name: John
//         First char: J
```

### 8.4 String Input/Output

**Definition:** Reading and displaying strings.

**Explanation:** 
- `scanf("%s", str)` reads a string until whitespace
- `gets()` reads entire line (deprecated, unsafe)
- `fgets(str, size, stdin)` safe alternative
- `printf("%s", str)` displays a string

**Example:**
```c
#include <stdio.h>
int main() {
    char name[50];
    printf("Enter name: ");
    scanf("%s", name);
    printf("Hello, %s!\n", name);
    return 0;
}
```

### 8.5 String Functions (string.h)

**Definition:** Standard library functions for string manipulation.

**Explanation:**
- `strlen(str)` - returns string length
- `strcpy(dest, src)` - copies string
- `strcat(dest, src)` - concatenates strings
- `strcmp(str1, str2)` - compares strings

**Example:**
```c
#include <stdio.h>
#include <string.h>
int main() {
    char str1[20] = "Hello";
    char str2[20] = "World";
    
    printf("Length of str1: %lu\n", strlen(str1));
    strcat(str1, " ");
    strcat(str1, str2);
    printf("Concatenated: %s\n", str1);
    return 0;
}
// Output: Length of str1: 5
//         Concatenated: Hello World
```

### 8.6 Character Classification

**Definition:** Functions to check character properties.

**Explanation:** Functions from `ctype.h`:
- `isalpha(c)` - checks if alphabetic
- `isdigit(c)` - checks if digit
- `isalnum(c)` - checks if alphanumeric
- `toupper(c)` - converts to uppercase
- `tolower(c)` - converts to lowercase

**Example:**
```c
#include <stdio.h>
#include <ctype.h>
int main() {
    char ch = 'a';
    if(isalpha(ch))
        printf("%c is alphabetic\n", ch);
    printf("Uppercase: %c\n", toupper(ch));
    return 0;
}
// Output: a is alphabetic
//         Uppercase: A
```

---

## 9. Functions

### 9.1 Function Basics

**Definition:** A reusable block of code that performs a specific task.

**Explanation:** Functions help organize code, improve readability, and enable code reuse. A function has a return type, name, parameters, and body.

**Example:**
```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(5, 3);
    printf("Sum: %d\n", result);
    return 0;
}
// Output: Sum: 8
```

### 9.2 Function Declaration (Prototype)

**Definition:** Announcing a function before its use.

**Explanation:** Function prototypes tell the compiler about the function's return type, name, and parameters. Syntax: `return_type function_name(parameter_types);`

**Example:**
```c
#include <stdio.h>

// Function prototype
int multiply(int, int);

int main() {
    printf("Product: %d\n", multiply(4, 5));
    return 0;
}

// Function definition
int multiply(int a, int b) {
    return a * b;
}
// Output: Product: 20
```

### 9.3 Function Parameters

**Definition:** Values passed to functions.

**Explanation:** Parameters can be passed by value (copy) or by reference (pointer). C uses pass-by-value by default.

**Example:**
```c
#include <stdio.h>

// Pass by value
void increment(int x) {
    x = x + 1;
    printf("Inside function: %d\n", x);
}

int main() {
    int num = 10;
    increment(num);
    printf("In main: %d\n", num);
    return 0;
}
// Output: Inside function: 11
//         In main: 10
```

### 9.4 Return Statement

**Definition:** Exits a function and optionally returns a value.

**Explanation:** The `return` statement sends a value back to the calling function. The return type must match the function's declared return type.

**Example:**
```c
#include <stdio.h>

int max(int a, int b) {
    if (a > b)
        return a;
    else
        return b;
}

int main() {
    printf("Maximum: %d\n", max(10, 20));
    return 0;
}
// Output: Maximum: 20
```

### 9.5 void Functions

**Definition:** Functions that don't return a value.

**Explanation:** Functions with `void` return type perform actions but don't return values. They can still use `return;` to exit early.

**Example:**
```c
#include <stdio.h>

void greet(char name[]) {
    printf("Hello, %s!\n", name);
}

int main() {
    greet("Alice");
    greet("Bob");
    return 0;
}
// Output: Hello, Alice!
//         Hello, Bob!
```

### 9.6 Recursion

**Definition:** A function that calls itself.

**Explanation:** Recursive functions have a base case (stopping condition) and recursive case. Useful for problems with repetitive subproblems.

**Example:**
```c
#include <stdio.h>

int factorial(int n) {
    if (n <= 1)
        return 1;  // Base case
    else
        return n * factorial(n - 1);  // Recursive case
}

int main() {
    printf("5! = %d\n", factorial(5));
    return 0;
}
// Output: 5! = 120
```

### 9.7 Inline Functions

**Definition:** Functions that suggest to the compiler to insert the function code directly at the call site.

**Explanation:** Inline functions reduce function call overhead for small, frequently called functions. Use `inline` keyword (C99 standard).

**Example:**
```c
#include <stdio.h>

inline int square(int x) {
    return x * x;
}

int main() {
    printf("Square of 5: %d\n", square(5));
    return 0;
}
// Output: Square of 5: 25
```

### 9.8 Function Scope

**Definition:** Visibility and lifetime of variables in functions.

**Explanation:**
- Local variables: declared inside functions, exist only during function execution
- Global variables: declared outside functions, accessible everywhere
- Parameters: local to the function

**Example:**
```c
#include <stdio.h>

int global = 100;  // Global variable

void display() {
    int local = 50;  // Local variable
    printf("Global: %d, Local: %d\n", global, local);
}

int main() {
    display();
    printf("Global in main: %d\n", global);
    return 0;
}
```

---

## 10. Structures

### 10.1 Structure Basics

**Definition:** User-defined data type that groups related variables of different types.

**Explanation:** Structures allow bundling different data types under a single name. Members are accessed using the dot (`.`) operator.

**Example:**
```c
#include <stdio.h>

struct Person {
    char name[50];
    int age;
    float height;
};

int main() {
    struct Person person1;
    strcpy(person1.name, "John");
    person1.age = 25;
    person1.height = 5.9;
    
    printf("Name: %s\n", person1.name);
    printf("Age: %d\n", person1.age);
    printf("Height: %.1f\n", person1.height);
    return 0;
}
```

### 10.2 Structure Declaration

**Definition:** Defining a new structure type.

**Explanation:** Syntax: `struct StructureName { member_declarations };`

**Example:**
```c
#include <stdio.h>

struct Student {
    int roll;
    char name[50];
    float gpa;
};

int main() {
    struct Student s1 = {101, "Alice", 3.8};
    printf("Roll: %d, Name: %s, GPA: %.1f\n", 
           s1.roll, s1.name, s1.gpa);
    return 0;
}
```

### 10.3 Accessing Structure Members

**Definition:** Using the dot operator to access structure members.

**Explanation:** Syntax: `structure_variable.member_name`

**Example:**
```c
#include <stdio.h>

struct Point {
    int x;
    int y;
};

int main() {
    struct Point p1;
    p1.x = 10;
    p1.y = 20;
    
    printf("Point: (%d, %d)\n", p1.x, p1.y);
    return 0;
}
// Output: Point: (10, 20)
```

### 10.4 Array of Structures

**Definition:** Multiple structure variables stored in an array.

**Explanation:** Useful for storing multiple records of the same structure type.

**Example:**
```c
#include <stdio.h>

struct Student {
    int roll;
    char name[50];
    int age;
};

int main() {
    struct Student students[5] = {
        {1, "John Doe", 18},
        {2, "Jane Smith", 19},
        {3, "Alice Brown", 18},
        {4, "Mr. Fox", 19},
        {5, "Ethan Hunt", 20}
    };
    
    int searchRoll = 4, i;
    for (i = 0; i < 5; i++) {
        if (students[i].roll == searchRoll) {
            printf("\nInformation of Roll No: %d\n", searchRoll);
            printf("----------------------------\n");
            printf("Roll No: %d\n", students[i].roll);
            printf("Name: %s\n", students[i].name);
            printf("Age: %d\n", students[i].age);
            break;
        }
    }
    return 0;
}
```

### 10.5 Nested Structures

**Definition:** A structure containing another structure as a member.

**Explanation:** Structures can contain other structures, creating hierarchical data organization.

**Example:**
```c
#include <stdio.h>

struct Date {
    int day;
    int month;
    int year;
};

struct Employee {
    char name[50];
    int id;
    struct Date joinDate;
};

int main() {
    struct Employee emp = {"John", 101, {15, 6, 2020}};
    
    printf("Name: %s\n", emp.name);
    printf("Join Date: %d/%d/%d\n", 
           emp.joinDate.day, emp.joinDate.month, emp.joinDate.year);
    return 0;
}
```

### 10.6 Structures and Pointers

**Definition:** Using pointers to access structure members.

**Explanation:** The arrow operator (`->`) is used to access members through a structure pointer. Equivalent to `(*ptr).member`.

**Example:**
```c
#include <stdio.h>

struct Book {
    char title[50];
    int pages;
};

int main() {
    struct Book book1 = {"C Programming", 500};
    struct Book *ptr = &book1;
    
    printf("Title: %s\n", ptr->title);
    printf("Pages: %d\n", ptr->pages);
    return 0;
}
```

### 10.7 typedef with Structures

**Definition:** Creating an alias for a structure type.

**Explanation:** `typedef` simplifies structure declarations by eliminating the need to use the `struct` keyword.

**Example:**
```c
#include <stdio.h>

typedef struct {
    char brand[30];
    int year;
} Car;

int main() {
    Car myCar = {"Toyota", 2022};
    printf("Brand: %s, Year: %d\n", myCar.brand, myCar.year);
    return 0;
}
```

---

## 11. Unions

### 11.1 Union Basics

**Definition:** A user-defined data type that allows storing different data types in the same memory location.

**Explanation:** Unlike structures where each member has its own memory, all union members share the same memory location. Only one member can hold a value at a time.

**Example:**
```c
#include <stdio.h>

union Data {
    int i;
    float f;
    char c;
};

int main() {
    union Data data;
    
    data.i = 10;
    printf("data.i: %d\n", data.i);
    
    data.f = 220.5;
    printf("data.f: %.1f\n", data.f);
    
    data.c = 'A';
    printf("data.c: %c\n", data.c);
    
    return 0;
}
```

### 11.2 Union Declaration

**Definition:** Defining a union type.

**Explanation:** Syntax is similar to structures: `union UnionName { member_declarations };`

**Example:**
```c
#include <stdio.h>

union un {
    int member1;
    char member2;
    float member3;
};

int main() {
    union un var1;
    var1.member1 = 15;
    printf("The value stored in member1 = %d\n", var1.member1);
    return 0;
}
// Output: The value stored in member1 = 15
```

### 11.3 Union vs Structure

**Definition:** Key differences between unions and structures.

**Explanation:**
- **Structures:** Each member has separate memory; all members can hold values simultaneously
- **Unions:** All members share the same memory; only one member holds a value at a time
- Memory: Union size = size of largest member; Structure size = sum of all members (plus padding)

**Example:**
```c
#include <stdio.h>

struct StructExample {
    int i;
    float f;
    char c;
};

union UnionExample {
    int i;
    float f;
    char c;
};

int main() {
    printf("Structure size: %lu bytes\n", sizeof(struct StructExample));
    printf("Union size: %lu bytes\n", sizeof(union UnionExample));
    return 0;
}
// Typical Output:
// Structure size: 12 bytes (4+4+1+padding)
// Union size: 4 bytes (size of largest member: float/int)
```

### 11.4 Union Use Cases

**Definition:** Practical applications of unions.

**Explanation:** Unions are useful when:
- You need to save memory
- Only one member is used at a time
- Type conversion or interpreting data in different ways
- Implementing variant data types

**Example:**
```c
#include <stdio.h>

union Number {
    int as_int;
    float as_float;
};

int main() {
    union Number num;
    num.as_float = 3.14;
    
    printf("As float: %f\n", num.as_float);
    printf("As int (raw bits): %d\n", num.as_int);
    return 0;
}
```

### 11.5 Accessing Union Members

**Definition:** Using the dot operator to access union members.

**Explanation:** Same syntax as structures (`union_variable.member`), but remember only the last assigned member is valid.

**Example:**
```c
#include <stdio.h>

union Value {
    int integer;
    float decimal;
    char letter;
};

int main() {
    union Value v;
    
    v.integer = 100;
    printf("Integer: %d\n", v.integer);
    
    v.decimal = 99.9;  // This overwrites integer
    printf("Decimal: %.1f\n", v.decimal);
    // v.integer is now invalid
    
    return 0;
}
```

---

## Additional Concepts

### Preprocessor Directives

**Definition:** Instructions to the compiler processed before compilation.

**Explanation:**
- `#include` - includes header files
- `#define` - defines macros/constants
- `#ifdef`, `#ifndef` - conditional compilation

**Example:**
```c
#include <stdio.h>
#define PI 3.14159
#define MAX(a,b) ((a) > (b) ? (a) : (b))

int main() {
    printf("PI = %f\n", PI);
    printf("Max of 10 and 20: %d\n", MAX(10, 20));
    return 0;
}
```

### Type Casting

**Definition:** Converting one data type to another.

**Explanation:** Explicit casting: `(type)expression`. Implicit casting happens automatically in some operations.

**Example:**
```c
#include <stdio.h>
int main() {
    int a = 10;
    float b = 3.5;
    
    float result = a + b;  // Implicit: int to float
    int truncated = (int)b;  // Explicit: float to int
    
    printf("Result: %.1f\n", result);
    printf("Truncated: %d\n", truncated);
    return 0;
}
// Output: Result: 13.5
//         Truncated: 3
```

### const Keyword

**Definition:** Declares a variable whose value cannot be changed.

**Explanation:** `const` makes variables read-only, preventing accidental modification.

**Example:**
```c
#include <stdio.h>
int main() {
    const int MAX_SIZE = 100;
    printf("Max size: %d\n", MAX_SIZE);
    // MAX_SIZE = 200;  // Error: cannot modify const variable
    return 0;
}
```

---

## Summary of Format Specifiers

| Specifier | Data Type | Description |
|-----------|-----------|-------------|
| `%d` | int | Decimal integer |
| `%i` | int | Integer (same as %d) |
| `%f` | float | Floating point |
| `%lf` | double | Double precision |
| `%c` | char | Single character |
| `%s` | char[] | String |
| `%p` | pointer | Pointer address |
| `%u` | unsigned int | Unsigned integer |
| `%x` | int | Hexadecimal |
| `%o` | int | Octal |
| `%e` | float | Scientific notation |

---

## Escape Sequences

| Sequence | Description |
|----------|-------------|
| `\n` | Newline |
| `\t` | Horizontal tab |
| `\\` | Backslash |
| `\"` | Double quote |
| `\'` | Single quote |
| `\0` | Null character |
| `\r` | Carriage return |
| `\b` | Backspace |

---

## Operator Precedence (Highest to Lowest)

1. Parentheses: `()`
2. Postfix: `x++`, `x--`
3. Prefix and Unary: `++x`, `--x`, `!`, `-`, `*`, `&`, `sizeof`
4. Multiplicative: `*`, `/`, `%`
5. Additive: `+`, `-`
6. Relational: `<`, `<=`, `>`, `>=`
7. Equality: `==`, `!=`
8. Logical AND: `&&`
9. Logical OR: `||`
10. Conditional: `?:`
11. Assignment: `=`, `+=`, `-=`, `*=`, `/=`, `%=`

---

## Best Practices

1. **Use meaningful variable names**: `studentAge` instead of `sa`
2. **Comment your code**: Explain complex logic
3. **Initialize variables**: Avoid garbage values
4. **Check array bounds**: Prevent buffer overflow
5. **Use constants**: For values that don't change
6. **Avoid magic numbers**: Use named constants
7. **Free allocated memory**: Prevent memory leaks
8. **Validate input**: Check user input before processing
9. **Use functions**: Break code into reusable pieces
10. **Follow consistent style**: Indentation and naming conventions

---

## Common Errors to Avoid

1. **Uninitialized variables**: Always initialize before use
2. **Off-by-one errors**: Check loop boundaries carefully
3. **Array out of bounds**: Ensure indices are within range
4. **Missing break in switch**: Can cause fall-through
5. **Forgetting null terminator**: In strings
6. **Incorrect pointer usage**: Dereferencing null pointers
7. **Type mismatch**: Using wrong format specifier
8. **Infinite loops**: Ensure loop condition can become false
9. **Memory leaks**: Free dynamically allocated memory
10. **Integer division**: `5/2 = 2` not `2.5` (use floats for precision)

---

## Quick Reference: Common Operations

### Swap two variables
```c
int temp = a;
a = b;
b = temp;
```

### Find maximum of two numbers
```c
int max = (a > b) ? a : b;
```

### Sum of array elements
```c
int sum = 0;
for(int i = 0; i < n; i++)
    sum += arr[i];
```

### String length (without strlen)
```c
int length = 0;
while(str[length] != '\0')
    length++;
```

### Reverse a string
```c
int i, j;
char temp;
int len = strlen(str);
for(i = 0, j = len-1; i < j; i++, j--) {
    temp = str[i];
    str[i] = str[j];
    str[j] = temp;
}
```

---

**End of Cheat Sheet**

*This comprehensive cheat sheet covers all major topics from CSE-1101 Structured Programming Language course, based on the repository content and the textbook "C: From Theory to Practice" by Nikolaos D. Tselikas & George S. Tselikis.*

---

⭐ **Star the repository if you found this helpful!**

For more examples and practice problems, visit the individual lecture folders in the repository.
