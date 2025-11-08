# C Programming Cheat Sheet 📘

A comprehensive reference guide for C programming covering all fundamental and advanced concepts with practical examples.

---

## Table of Contents

### Fundamental Concepts
1. [Introduction and Basic Structure](#1-introduction-and-basic-structure)
2. [Data Types and Variables](#2-data-types-and-variables)
3. [Input/Output Operations](#3-inputoutput-operations)
4. [Operators](#4-operators)
5. [Control Structures](#5-control-structures)
6. [Loops](#6-loops)
7. [Arrays](#7-arrays)
8. [Pointers](#8-pointers)
9. [Strings](#9-strings)
10. [Functions](#10-functions)
11. [Structures and Unions](#11-structures-and-unions)

### Advanced Concepts
12. [File Handling](#12-file-handling)
13. [Dynamic Memory Allocation](#13-dynamic-memory-allocation)
14. [Preprocessor Directives](#14-preprocessor-directives)
15. [Typedef and Enums](#15-typedef-and-enums)
16. [Command Line Arguments](#16-command-line-arguments)
17. [Bitwise Operators](#17-bitwise-operators)
18. [Storage Classes](#18-storage-classes)
19. [Advanced Concepts](#19-advanced-concepts)
20. [Common Standard Library Functions](#20-common-standard-library-functions)
21. [Best Practices and Tips](#21-best-practices-and-tips)
22. [Quick Reference](#22-quick-reference)

---

## 1. Introduction and Basic Structure

### 1.1 Basic Program Structure

**Definition:** Every C program consists of one or more functions, with `main()` being the entry point.

**Explanation:** A C program includes preprocessor directives, declarations, and statements enclosed in functions.

**Example:**
```c
#include <stdio.h>

int main() {
    printf("Hello, World!\n");
    return 0;
}
```

### 1.2 Comments

**Definition:** Non-executable text used to document code.

**Explanation:** 
- Single-line comments: `// comment`
- Multi-line comments: `/* comment */`

**Example:**
```c
#include <stdio.h>

int main() {
    // This is a single-line comment
    
    /* This is a
       multi-line comment */
    
    printf("Comments help explain code!\n");
    return 0;
}
```

### 1.3 Header Files

**Definition:** Files containing function declarations and macro definitions.

**Explanation:** Common header files include:
- `stdio.h` - Input/Output functions
- `stdlib.h` - Standard library functions
- `string.h` - String manipulation functions
- `math.h` - Mathematical functions

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main() {
    printf("Square root of 16: %.2f\n", sqrt(16.0));
    return 0;
}
```

---

## 2. Data Types and Variables

### 2.1 Basic Data Types

**Definition:** Data types specify the type of data a variable can store.

**Explanation:**
- `int` - Integer (typically 4 bytes)
- `float` - Single-precision floating point (4 bytes)
- `double` - Double-precision floating point (8 bytes)
- `char` - Single character (1 byte)

**Example:**
```c
#include <stdio.h>

int main() {
    int age = 25;
    float height = 5.9;
    double pi = 3.14159265359;
    char grade = 'A';
    
    printf("Age: %d\n", age);
    printf("Height: %.1f\n", height);
    printf("Pi: %.10lf\n", pi);
    printf("Grade: %c\n", grade);
    
    return 0;
}
```

### 2.2 Variable Declaration and Initialization

**Definition:** Creating variables and optionally assigning initial values.

**Example:**
```c
#include <stdio.h>

int main() {
    // Declaration only
    int x;
    
    // Declaration with initialization
    int y = 10;
    
    // Multiple declarations
    int a, b, c;
    
    // Multiple declarations with initialization
    int p = 1, q = 2, r = 3;
    
    x = 5;  // Assignment after declaration
    
    printf("x = %d, y = %d\n", x, y);
    printf("p = %d, q = %d, r = %d\n", p, q, r);
    
    return 0;
}
```

### 2.3 Constants

**Definition:** Values that cannot be changed during program execution.

**Explanation:**
- Use `const` keyword
- Use `#define` preprocessor directive

**Example:**
```c
#include <stdio.h>

#define PI 3.14159
#define MAX_SIZE 100

int main() {
    const int MIN_AGE = 18;
    
    printf("PI = %.5f\n", PI);
    printf("MAX_SIZE = %d\n", MAX_SIZE);
    printf("MIN_AGE = %d\n", MIN_AGE);
    
    // MIN_AGE = 20;  // Error: cannot modify const
    
    return 0;
}
```

### 2.4 Type Modifiers

**Definition:** Keywords that modify the properties of basic data types.

**Explanation:**
- `signed` / `unsigned` - Determines if negative values are allowed
- `short` / `long` - Modifies the size of the data type

**Example:**
```c
#include <stdio.h>

int main() {
    unsigned int positiveOnly = 100;
    signed int canBeNegative = -50;
    
    short int smallNumber = 32000;
    long int bigNumber = 2147483647;
    long long int veryBigNumber = 9223372036854775807LL;
    
    printf("Unsigned: %u\n", positiveOnly);
    printf("Signed: %d\n", canBeNegative);
    printf("Short: %hd\n", smallNumber);
    printf("Long: %ld\n", bigNumber);
    printf("Long Long: %lld\n", veryBigNumber);
    
    return 0;
}
```

### 2.5 sizeof Operator

**Definition:** Returns the size of a data type or variable in bytes.

**Example:**
```c
#include <stdio.h>

int main() {
    printf("Size of int: %lu bytes\n", sizeof(int));
    printf("Size of float: %lu bytes\n", sizeof(float));
    printf("Size of double: %lu bytes\n", sizeof(double));
    printf("Size of char: %lu bytes\n", sizeof(char));
    
    int arr[10];
    printf("Size of array: %lu bytes\n", sizeof(arr));
    
    return 0;
}
```

---

## 3. Input/Output Operations

### 3.1 printf() - Formatted Output

**Definition:** Displays formatted output to the console.

**Explanation:** Uses format specifiers to control output format.

**Example:**
```c
#include <stdio.h>

int main() {
    int num = 42;
    float pi = 3.14159;
    char ch = 'X';
    
    printf("Integer: %d\n", num);
    printf("Float: %.2f\n", pi);
    printf("Character: %c\n", ch);
    printf("String: %s\n", "Hello");
    
    // Field width and alignment
    printf("Right aligned: %10d\n", num);
    printf("Left aligned: %-10d\n", num);
    printf("Zero padded: %05d\n", num);
    
    return 0;
}
```

### 3.2 scanf() - Formatted Input

**Definition:** Reads formatted input from the user.

**Explanation:** Uses format specifiers and requires addresses of variables (using &).

**Example:**
```c
#include <stdio.h>

int main() {
    int age;
    float salary;
    char initial;
    
    printf("Enter your age: ");
    scanf("%d", &age);
    
    printf("Enter your salary: ");
    scanf("%f", &salary);
    
    printf("Enter your initial: ");
    scanf(" %c", &initial);  // Space before %c to skip whitespace
    
    printf("\nYou entered:\n");
    printf("Age: %d\n", age);
    printf("Salary: %.2f\n", salary);
    printf("Initial: %c\n", initial);
    
    return 0;
}
```

### 3.3 getchar() and putchar()

**Definition:** Functions for reading and writing single characters.

**Example:**
```c
#include <stdio.h>

int main() {
    char ch;
    
    printf("Enter a character: ");
    ch = getchar();
    
    printf("You entered: ");
    putchar(ch);
    putchar('\n');
    
    return 0;
}
```

### 3.4 gets() and puts()

**Definition:** Functions for reading and writing strings.

**Note:** `gets()` is deprecated; use `fgets()` instead for safety.

**Example:**
```c
#include <stdio.h>

int main() {
    char name[50];
    
    printf("Enter your name: ");
    fgets(name, sizeof(name), stdin);
    
    printf("Hello, ");
    fputs(name, stdout);
    
    return 0;
}
```

---

## 4. Operators

### 4.1 Arithmetic Operators

**Definition:** Operators for mathematical calculations.

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
    
    printf("a + b = %d\n", a + b);  // 13
    printf("a - b = %d\n", a - b);  // 7
    printf("a * b = %d\n", a * b);  // 30
    printf("a / b = %d\n", a / b);  // 3 (integer division)
    printf("a %% b = %d\n", a % b); // 1 (remainder)
    
    float x = 10.0, y = 3.0;
    printf("x / y = %.2f\n", x / y); // 3.33 (float division)
    
    return 0;
}
```

### 4.2 Relational Operators

**Definition:** Operators for comparing values.

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
    int a = 5, b = 10;
    
    printf("a == b: %d\n", a == b);  // 0 (false)
    printf("a != b: %d\n", a != b);  // 1 (true)
    printf("a > b: %d\n", a > b);    // 0 (false)
    printf("a < b: %d\n", a < b);    // 1 (true)
    printf("a >= b: %d\n", a >= b);  // 0 (false)
    printf("a <= b: %d\n", a <= b);  // 1 (true)
    
    return 0;
}
```

### 4.3 Logical Operators

**Definition:** Operators for combining boolean expressions.

**Explanation:**
- `&&` Logical AND
- `||` Logical OR
- `!` Logical NOT

**Example:**
```c
#include <stdio.h>

int main() {
    int a = 1, b = 0;
    
    printf("a && b: %d\n", a && b);  // 0 (false)
    printf("a || b: %d\n", a || b);  // 1 (true)
    printf("!a: %d\n", !a);          // 0 (false)
    printf("!b: %d\n", !b);          // 1 (true)
    
    // Practical example
    int age = 25;
    int hasLicense = 1;
    
    if (age >= 18 && hasLicense) {
        printf("Can drive!\n");
    }
    
    return 0;
}
```

### 4.4 Assignment Operators

**Definition:** Operators for assigning values to variables.

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
    int x = 10;
    
    printf("Initial x = %d\n", x);
    
    x += 5;  // x = x + 5
    printf("After x += 5: %d\n", x);  // 15
    
    x -= 3;  // x = x - 3
    printf("After x -= 3: %d\n", x);  // 12
    
    x *= 2;  // x = x * 2
    printf("After x *= 2: %d\n", x);  // 24
    
    x /= 4;  // x = x / 4
    printf("After x /= 4: %d\n", x);  // 6
    
    x %= 4;  // x = x % 4
    printf("After x %%= 4: %d\n", x); // 2
    
    return 0;
}
```

### 4.5 Increment and Decrement Operators

**Definition:** Operators for increasing or decreasing a variable by 1.

**Explanation:**
- `++` Increment (prefix: `++x`, postfix: `x++`)
- `--` Decrement (prefix: `--x`, postfix: `x--`)

**Example:**
```c
#include <stdio.h>

int main() {
    int a = 5, b = 5;
    
    printf("a = %d, b = %d\n", a, b);
    
    // Prefix increment
    printf("++a = %d\n", ++a);  // Increments first, then returns (6)
    printf("a = %d\n", a);      // 6
    
    // Postfix increment
    printf("b++ = %d\n", b++);  // Returns first, then increments (5)
    printf("b = %d\n", b);      // 6
    
    int x = 10;
    printf("--x = %d\n", --x);  // 9
    printf("x-- = %d\n", x--);  // 9
    printf("x = %d\n", x);      // 8
    
    return 0;
}
```

### 4.6 Ternary Operator

**Definition:** Conditional operator that returns one of two values based on a condition.

**Syntax:** `condition ? value_if_true : value_if_false`

**Example:**
```c
#include <stdio.h>

int main() {
    int a = 10, b = 20;
    int max;
    
    // Find maximum
    max = (a > b) ? a : b;
    printf("Maximum: %d\n", max);  // 20
    
    // Check even or odd
    int num = 7;
    printf("%d is %s\n", num, (num % 2 == 0) ? "even" : "odd");
    
    return 0;
}
```

---

## 5. Control Structures

### 5.1 if Statement

**Definition:** Executes a block of code if a condition is true.

**Example:**
```c
#include <stdio.h>

int main() {
    int age = 20;
    
    if (age >= 18) {
        printf("You are an adult.\n");
    }
    
    return 0;
}
```

### 5.2 if-else Statement

**Definition:** Executes one block if condition is true, another if false.

**Example:**
```c
#include <stdio.h>

int main() {
    int num = 7;
    
    if (num % 2 == 0) {
        printf("%d is even.\n", num);
    } else {
        printf("%d is odd.\n", num);
    }
    
    return 0;
}
```

### 5.3 if-else if-else Ladder

**Definition:** Tests multiple conditions sequentially.

**Example:**
```c
#include <stdio.h>

int main() {
    int marks = 85;
    
    if (marks >= 90) {
        printf("Grade: A+\n");
    } else if (marks >= 80) {
        printf("Grade: A\n");
    } else if (marks >= 70) {
        printf("Grade: B\n");
    } else if (marks >= 60) {
        printf("Grade: C\n");
    } else {
        printf("Grade: F\n");
    }
    
    return 0;
}
```

### 5.4 Nested if Statements

**Definition:** if statements inside other if statements.

**Example:**
```c
#include <stdio.h>

int main() {
    int age = 25;
    int hasLicense = 1;
    
    if (age >= 18) {
        if (hasLicense) {
            printf("You can drive.\n");
        } else {
            printf("You need a license.\n");
        }
    } else {
        printf("You are too young to drive.\n");
    }
    
    return 0;
}
```

### 5.5 switch Statement

**Definition:** Multi-way branch statement that tests a variable against multiple values.

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
        case 4:
            printf("Thursday\n");
            break;
        case 5:
            printf("Friday\n");
            break;
        case 6:
            printf("Saturday\n");
            break;
        case 7:
            printf("Sunday\n");
            break;
        default:
            printf("Invalid day\n");
    }
    
    return 0;
}
```

### 5.6 goto Statement

**Definition:** Unconditional jump to a labeled statement.

**Note:** Use sparingly as it can make code hard to follow.

**Example:**
```c
#include <stdio.h>

int main() {
    int i = 0;
    
    start:
    if (i < 5) {
        printf("%d ", i);
        i++;
        goto start;
    }
    printf("\n");
    
    return 0;
}
// Output: 0 1 2 3 4
```

---

## 6. Loops

### 6.1 for Loop

**Definition:** Loop that repeats a block of code a specific number of times.

**Syntax:** `for(initialization; condition; increment/decrement)`

**Example:**
```c
#include <stdio.h>

int main() {
    // Print numbers 1 to 5
    for (int i = 1; i <= 5; i++) {
        printf("%d ", i);
    }
    printf("\n");
    
    // Calculate sum of first 10 natural numbers
    int sum = 0;
    for (int i = 1; i <= 10; i++) {
        sum += i;
    }
    printf("Sum: %d\n", sum);  // 55
    
    return 0;
}
```

### 6.2 while Loop

**Definition:** Loop that repeats while a condition is true (pre-test loop).

**Example:**
```c
#include <stdio.h>

int main() {
    int i = 1;
    
    while (i <= 5) {
        printf("%d ", i);
        i++;
    }
    printf("\n");
    
    // Find factorial
    int n = 5, factorial = 1;
    int count = 1;
    
    while (count <= n) {
        factorial *= count;
        count++;
    }
    printf("Factorial of %d: %d\n", n, factorial);
    
    return 0;
}
```

### 6.3 do-while Loop

**Definition:** Loop that executes at least once, then repeats while condition is true (post-test loop).

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
    
    // Menu example
    int choice;
    do {
        printf("\nMenu:\n");
        printf("1. Start\n");
        printf("2. Stop\n");
        printf("3. Exit\n");
        printf("Enter choice: ");
        scanf("%d", &choice);
        
        if (choice == 1) printf("Started!\n");
        else if (choice == 2) printf("Stopped!\n");
        else if (choice == 3) printf("Exiting...\n");
        else printf("Invalid choice!\n");
        
    } while (choice != 3);
    
    return 0;
}
```

### 6.4 Nested Loops

**Definition:** Loops inside other loops.

**Example:**
```c
#include <stdio.h>

int main() {
    // Multiplication table
    for (int i = 1; i <= 5; i++) {
        for (int j = 1; j <= 5; j++) {
            printf("%3d ", i * j);
        }
        printf("\n");
    }
    
    // Print pattern
    printf("\n");
    for (int i = 1; i <= 5; i++) {
        for (int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }
    
    return 0;
}
```

### 6.5 break Statement

**Definition:** Exits a loop immediately.

**Example:**
```c
#include <stdio.h>

int main() {
    // Find first number divisible by both 3 and 5
    for (int i = 1; i <= 50; i++) {
        if (i % 3 == 0 && i % 5 == 0) {
            printf("First number divisible by both 3 and 5: %d\n", i);
            break;
        }
    }
    
    return 0;
}
```

### 6.6 continue Statement

**Definition:** Skips the rest of the current iteration and moves to the next.

**Example:**
```c
#include <stdio.h>

int main() {
    // Print odd numbers from 1 to 10
    for (int i = 1; i <= 10; i++) {
        if (i % 2 == 0) {
            continue;  // Skip even numbers
        }
        printf("%d ", i);
    }
    printf("\n");
    
    return 0;
}
// Output: 1 3 5 7 9
```

---

## 7. Arrays

### 7.1 One-Dimensional Arrays

**Definition:** Collection of elements of the same data type stored in contiguous memory.

**Syntax:** `datatype arrayName[size];`

**Example:**
```c
#include <stdio.h>

int main() {
    // Declaration and initialization
    int numbers[5] = {10, 20, 30, 40, 50};
    
    // Accessing elements
    printf("First element: %d\n", numbers[0]);
    printf("Third element: %d\n", numbers[2]);
    
    // Modifying elements
    numbers[1] = 25;
    
    // Print all elements
    printf("Array elements: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", numbers[i]);
    }
    printf("\n");
    
    return 0;
}
```

### 7.2 Array Input and Output

**Example:**
```c
#include <stdio.h>

int main() {
    int arr[5];
    int sum = 0;
    
    printf("Enter 5 numbers:\n");
    for (int i = 0; i < 5; i++) {
        printf("Element %d: ", i + 1);
        scanf("%d", &arr[i]);
        sum += arr[i];
    }
    
    printf("\nYou entered: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    
    printf("\nSum: %d\n", sum);
    printf("Average: %.2f\n", sum / 5.0);
    
    return 0;
}
```

### 7.3 Two-Dimensional Arrays

**Definition:** Array of arrays, representing data in tabular form (rows and columns).

**Syntax:** `datatype arrayName[rows][columns];`

**Example:**
```c
#include <stdio.h>

int main() {
    int matrix[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    
    printf("Matrix:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", matrix[i][j]);
        }
        printf("\n");
    }
    
    return 0;
}
```

### 7.4 Array Operations

**Example:**
```c
#include <stdio.h>

int main() {
    int arr[] = {5, 2, 8, 1, 9, 3};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    // Find maximum
    int max = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    printf("Maximum: %d\n", max);
    
    // Find minimum
    int min = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] < min) {
            min = arr[i];
        }
    }
    printf("Minimum: %d\n", min);
    
    // Linear search
    int search = 8;
    int found = 0;
    for (int i = 0; i < n; i++) {
        if (arr[i] == search) {
            printf("%d found at index %d\n", search, i);
            found = 1;
            break;
        }
    }
    if (!found) {
        printf("%d not found\n", search);
    }
    
    return 0;
}
```

### 7.5 Bubble Sort

**Definition:** Simple sorting algorithm that repeatedly swaps adjacent elements if they're in wrong order.

**Example:**
```c
#include <stdio.h>

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    printf("Original array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    // Bubble sort
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Swap
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    
    printf("Sorted array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    return 0;
}
```

---

## 8. Pointers

### 8.1 Pointer Basics

**Definition:** A variable that stores the memory address of another variable.

**Syntax:** `datatype *pointerName;`

**Example:**
```c
#include <stdio.h>

int main() {
    int num = 10;
    int *ptr;
    
    ptr = &num;  // Store address of num in ptr
    
    printf("Value of num: %d\n", num);
    printf("Address of num: %p\n", (void*)&num);
    printf("Value of ptr: %p\n", (void*)ptr);
    printf("Value at ptr: %d\n", *ptr);  // Dereference
    
    return 0;
}
```

### 8.2 Pointer Arithmetic

**Definition:** Arithmetic operations on pointer addresses.

**Example:**
```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30, 40, 50};
    int *ptr = arr;  // Points to first element
    
    printf("Using pointer arithmetic:\n");
    for (int i = 0; i < 5; i++) {
        printf("arr[%d] = %d\n", i, *(ptr + i));
    }
    
    printf("\nIncrementing pointer:\n");
    ptr = arr;
    for (int i = 0; i < 5; i++) {
        printf("%d ", *ptr);
        ptr++;
    }
    printf("\n");
    
    return 0;
}
```

### 8.3 Pointers and Arrays

**Definition:** Array name acts as a pointer to the first element.

**Example:**
```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int *ptr = arr;
    
    // Different ways to access array elements
    printf("arr[0] = %d\n", arr[0]);
    printf("*arr = %d\n", *arr);
    printf("*ptr = %d\n", *ptr);
    printf("ptr[0] = %d\n", ptr[0]);
    
    printf("\nAll elements:\n");
    for (int i = 0; i < 5; i++) {
        printf("%d ", *(arr + i));
    }
    printf("\n");
    
    return 0;
}
```

### 8.4 Pointers and Functions

**Definition:** Passing addresses to functions to modify original variables (pass by reference).

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
    
    printf("Before swap: x = %d, y = %d\n", x, y);
    swap(&x, &y);
    printf("After swap: x = %d, y = %d\n", x, y);
    
    return 0;
}
```

### 8.5 NULL Pointer

**Definition:** Pointer that doesn't point to any valid memory location.

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = NULL;
    
    // Always check before dereferencing
    if (ptr == NULL) {
        printf("Pointer is NULL\n");
    }
    
    // Allocate memory
    ptr = (int*) malloc(sizeof(int));
    
    if (ptr != NULL) {
        *ptr = 100;
        printf("Value: %d\n", *ptr);
        free(ptr);
        ptr = NULL;  // Good practice
    }
    
    return 0;
}
```

---

## 9. Strings

### 9.1 String Basics

**Definition:** Array of characters terminated by null character '\0'.

**Example:**
```c
#include <stdio.h>

int main() {
    // Different ways to declare strings
    char str1[] = "Hello";
    char str2[20] = "World";
    char str3[] = {'H', 'i', '\0'};
    
    printf("%s\n", str1);
    printf("%s\n", str2);
    printf("%s\n", str3);
    
    return 0;
}
```

### 9.2 String Input/Output

**Example:**
```c
#include <stdio.h>

int main() {
    char name[50];
    
    // Using scanf (reads until whitespace)
    printf("Enter your first name: ");
    scanf("%s", name);
    printf("Hello, %s!\n", name);
    
    // Clear input buffer
    while (getchar() != '\n');
    
    // Using fgets (reads entire line)
    printf("Enter your full name: ");
    fgets(name, sizeof(name), stdin);
    printf("Welcome, %s", name);
    
    return 0;
}
```

### 9.3 String Functions (string.h)

**Definition:** Standard library functions for string manipulation.

**Example:**
```c
#include <stdio.h>
#include <string.h>

int main() {
    char str1[50] = "Hello";
    char str2[50] = "World";
    char str3[50];
    
    // strlen - Get length
    printf("Length of str1: %lu\n", strlen(str1));
    
    // strcpy - Copy string
    strcpy(str3, str1);
    printf("str3: %s\n", str3);
    
    // strcat - Concatenate strings
    strcat(str1, " ");
    strcat(str1, str2);
    printf("Concatenated: %s\n", str1);
    
    // strcmp - Compare strings
    int result = strcmp("abc", "xyz");
    if (result < 0) {
        printf("abc comes before xyz\n");
    }
    
    return 0;
}
```

### 9.4 Common String Operations

**Example:**
```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

int main() {
    char str[] = "Hello World";
    
    // Convert to uppercase
    printf("Uppercase: ");
    for (int i = 0; str[i] != '\0'; i++) {
        printf("%c", toupper(str[i]));
    }
    printf("\n");
    
    // Convert to lowercase
    printf("Lowercase: ");
    for (int i = 0; str[i] != '\0'; i++) {
        printf("%c", tolower(str[i]));
    }
    printf("\n");
    
    // Reverse string
    int len = strlen(str);
    printf("Reversed: ");
    for (int i = len - 1; i >= 0; i--) {
        printf("%c", str[i]);
    }
    printf("\n");
    
    return 0;
}
```

### 9.5 String with Pointers

**Example:**
```c
#include <stdio.h>

int main() {
    char str[] = "Programming";
    char *ptr = str;
    
    // Print using pointer
    printf("String: %s\n", ptr);
    
    // Print character by character
    printf("Characters: ");
    while (*ptr != '\0') {
        printf("%c ", *ptr);
        ptr++;
    }
    printf("\n");
    
    return 0;
}
```

---

## 10. Functions

### 10.1 Function Basics

**Definition:** Block of code that performs a specific task and can be reused.

**Syntax:**
```c
return_type function_name(parameter_list) {
    // function body
    return value;
}
```

**Example:**
```c
#include <stdio.h>

// Function declaration (prototype)
int add(int a, int b);

int main() {
    int result = add(5, 3);
    printf("Sum: %d\n", result);
    return 0;
}

// Function definition
int add(int a, int b) {
    return a + b;
}
```

### 10.2 Function with No Return Value (void)

**Example:**
```c
#include <stdio.h>

void greet(char name[]) {
    printf("Hello, %s!\n", name);
}

void printStars(int n) {
    for (int i = 0; i < n; i++) {
        printf("* ");
    }
    printf("\n");
}

int main() {
    greet("Alice");
    printStars(5);
    return 0;
}
```

### 10.3 Function with No Parameters

**Example:**
```c
#include <stdio.h>

int getRandomNumber() {
    return 42;  // "Random" number
}

void displayMenu() {
    printf("1. Start\n");
    printf("2. Stop\n");
    printf("3. Exit\n");
}

int main() {
    displayMenu();
    int num = getRandomNumber();
    printf("Number: %d\n", num);
    return 0;
}
```

### 10.4 Pass by Value vs Pass by Reference

**Definition:**
- Pass by Value: Function receives a copy of the argument
- Pass by Reference: Function receives the address of the argument

**Example:**
```c
#include <stdio.h>

// Pass by value
void modifyValue(int x) {
    x = 100;
    printf("Inside function: x = %d\n", x);
}

// Pass by reference
void modifyReference(int *x) {
    *x = 100;
    printf("Inside function: *x = %d\n", *x);
}

int main() {
    int num = 10;
    
    printf("Original: num = %d\n", num);
    modifyValue(num);
    printf("After pass by value: num = %d\n\n", num);  // Still 10
    
    printf("Original: num = %d\n", num);
    modifyReference(&num);
    printf("After pass by reference: num = %d\n", num);  // Changed to 100
    
    return 0;
}
```

### 10.5 Recursive Functions

**Definition:** Function that calls itself.

**Example:**
```c
#include <stdio.h>

int factorial(int n) {
    if (n <= 1) {
        return 1;  // Base case
    }
    return n * factorial(n - 1);  // Recursive call
}

int fibonacci(int n) {
    if (n <= 1) {
        return n;
    }
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    printf("Factorial of 5: %d\n", factorial(5));
    
    printf("Fibonacci sequence: ");
    for (int i = 0; i < 10; i++) {
        printf("%d ", fibonacci(i));
    }
    printf("\n");
    
    return 0;
}
```

### 10.6 Array as Function Parameter

**Example:**
```c
#include <stdio.h>

void printArray(int arr[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int sumArray(int arr[], int size) {
    int sum = 0;
    for (int i = 0; i < size; i++) {
        sum += arr[i];
    }
    return sum;
}

int main() {
    int numbers[] = {1, 2, 3, 4, 5};
    int size = sizeof(numbers) / sizeof(numbers[0]);
    
    printArray(numbers, size);
    printf("Sum: %d\n", sumArray(numbers, size));
    
    return 0;
}
```

---

## 11. Structures and Unions

### 11.1 Structure Basics

**Definition:** User-defined data type that groups related variables of different data types.

**Syntax:**
```c
struct structure_name {
    datatype member1;
    datatype member2;
    // ...
};
```

**Example:**
```c
#include <stdio.h>

struct Student {
    char name[50];
    int roll;
    float marks;
};

int main() {
    struct Student s1;
    
    // Assign values
    strcpy(s1.name, "John");
    s1.roll = 101;
    s1.marks = 85.5;
    
    // Access and display
    printf("Name: %s\n", s1.name);
    printf("Roll: %d\n", s1.roll);
    printf("Marks: %.2f\n", s1.marks);
    
    return 0;
}
```

### 11.2 Structure Initialization

**Example:**
```c
#include <stdio.h>
#include <string.h>

struct Book {
    char title[100];
    char author[50];
    int pages;
    float price;
};

int main() {
    // Method 1: Initialize during declaration
    struct Book b1 = {"C Programming", "Dennis Ritchie", 500, 29.99};
    
    // Method 2: Initialize members individually
    struct Book b2;
    strcpy(b2.title, "Data Structures");
    strcpy(b2.author, "Tanenbaum");
    b2.pages = 600;
    b2.price = 39.99;
    
    printf("Book 1: %s by %s\n", b1.title, b1.author);
    printf("Book 2: %s by %s\n", b2.title, b2.author);
    
    return 0;
}
```

### 11.3 Array of Structures

**Example:**
```c
#include <stdio.h>
#include <string.h>

struct Student {
    char name[50];
    int roll;
    float marks;
};

int main() {
    struct Student students[3];
    
    // Input
    for (int i = 0; i < 3; i++) {
        printf("\nStudent %d:\n", i + 1);
        printf("Name: ");
        scanf("%s", students[i].name);
        printf("Roll: ");
        scanf("%d", &students[i].roll);
        printf("Marks: ");
        scanf("%f", &students[i].marks);
    }
    
    // Output
    printf("\n\nStudent Records:\n");
    printf("%-20s %-10s %-10s\n", "Name", "Roll", "Marks");
    printf("----------------------------------------\n");
    for (int i = 0; i < 3; i++) {
        printf("%-20s %-10d %-10.2f\n", 
               students[i].name, students[i].roll, students[i].marks);
    }
    
    return 0;
}
```

### 11.4 Nested Structures

**Definition:** Structure within another structure.

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
    struct Employee emp = {"Alice", 1001, {15, 6, 2020}};
    
    printf("Employee: %s\n", emp.name);
    printf("ID: %d\n", emp.id);
    printf("Join Date: %d/%d/%d\n", 
           emp.joinDate.day, emp.joinDate.month, emp.joinDate.year);
    
    return 0;
}
```

### 11.5 Structure and Pointers

**Example:**
```c
#include <stdio.h>
#include <string.h>

struct Point {
    int x;
    int y;
};

int main() {
    struct Point p1 = {10, 20};
    struct Point *ptr = &p1;
    
    // Access using dot operator
    printf("Using dot: (%d, %d)\n", p1.x, p1.y);
    
    // Access using arrow operator
    printf("Using arrow: (%d, %d)\n", ptr->x, ptr->y);
    
    // Modify using pointer
    ptr->x = 30;
    ptr->y = 40;
    printf("After modification: (%d, %d)\n", p1.x, p1.y);
    
    return 0;
}
```

### 11.6 Unions

**Definition:** Similar to structure but all members share the same memory location.

**Explanation:** Only one member can hold a value at a time. Size equals the largest member.

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
    
    printf("Size of union: %lu bytes\n", sizeof(data));
    
    data.i = 10;
    printf("data.i = %d\n", data.i);
    
    data.f = 220.5;
    printf("data.f = %.2f\n", data.f);
    printf("data.i = %d (corrupted)\n", data.i);  // Value corrupted
    
    data.c = 'A';
    printf("data.c = %c\n", data.c);
    printf("data.f = %.2f (corrupted)\n", data.f);  // Value corrupted
    
    return 0;
}
```

### 11.7 typedef with Structures

**Definition:** Creating an alias for struct to simplify declarations.

**Example:**
```c
#include <stdio.h>
#include <string.h>

typedef struct {
    char name[50];
    int age;
    float salary;
} Employee;

int main() {
    // No need to write 'struct' keyword
    Employee emp1, emp2;
    
    strcpy(emp1.name, "Bob");
    emp1.age = 30;
    emp1.salary = 50000.0;
    
    strcpy(emp2.name, "Alice");
    emp2.age = 28;
    emp2.salary = 55000.0;
    
    printf("Employee 1: %s, Age: %d, Salary: %.2f\n", 
           emp1.name, emp1.age, emp1.salary);
    printf("Employee 2: %s, Age: %d, Salary: %.2f\n", 
           emp2.name, emp2.age, emp2.salary);
    
    return 0;
}
```

---

## 12. File Handling

### 12.1 File Pointers and Opening Files

**Definition:** Working with external files for reading and writing data.

**Explanation:** File operations require a file pointer (`FILE *`). Use `fopen()` to open files with different modes:
- "r" - Read mode
- "w" - Write mode (creates new/overwrites)
- "a" - Append mode
- "r+" - Read and write
- "w+" - Read and write (overwrites)
- "a+" - Read and append

**Example:**
```c
#include <stdio.h>
int main() {
    FILE *fp;
    fp = fopen("data.txt", "w");
    
    if (fp == NULL) {
        printf("Error opening file!\n");
        return 1;
    }
    
    fprintf(fp, "Hello, File!\n");
    fclose(fp);
    printf("File written successfully.\n");
    return 0;
}
```

### 12.2 Reading from Files

**Definition:** Reading data from external files into programs.

**Explanation:** Use functions like `fscanf()`, `fgets()`, `fgetc()`, or `fread()` to read from files.

**Example:**
```c
#include <stdio.h>
int main() {
    FILE *fp;
    char buffer[100];
    
    fp = fopen("data.txt", "r");
    if (fp == NULL) {
        printf("Error opening file!\n");
        return 1;
    }
    
    while (fgets(buffer, 100, fp) != NULL) {
        printf("%s", buffer);
    }
    
    fclose(fp);
    return 0;
}
```

### 12.3 Writing to Files

**Definition:** Writing data from programs to external files.

**Explanation:** Use `fprintf()`, `fputs()`, `fputc()`, or `fwrite()` to write data to files.

**Example:**
```c
#include <stdio.h>
int main() {
    FILE *fp;
    char name[50];
    int age;
    
    fp = fopen("student.txt", "w");
    
    printf("Enter name: ");
    scanf("%s", name);
    printf("Enter age: ");
    scanf("%d", &age);
    
    fprintf(fp, "Name: %s\nAge: %d\n", name, age);
    fclose(fp);
    
    printf("Data written to file.\n");
    return 0;
}
```

### 12.4 File Positioning

**Definition:** Moving the file pointer to specific locations in a file.

**Explanation:**
- `fseek(fp, offset, whence)` - Move file pointer
  - `SEEK_SET` - Beginning of file
  - `SEEK_CUR` - Current position
  - `SEEK_END` - End of file
- `ftell(fp)` - Get current position
- `rewind(fp)` - Move to beginning

**Example:**
```c
#include <stdio.h>
int main() {
    FILE *fp;
    char ch;
    
    fp = fopen("test.txt", "r");
    
    // Read 5th character
    fseek(fp, 4, SEEK_SET);
    ch = fgetc(fp);
    printf("5th character: %c\n", ch);
    
    // Get position
    long pos = ftell(fp);
    printf("Current position: %ld\n", pos);
    
    // Go back to start
    rewind(fp);
    
    fclose(fp);
    return 0;
}
```

### 12.5 Binary File Operations

**Definition:** Reading and writing binary data to files.

**Explanation:** Binary files store data in raw binary format. Use `fread()` and `fwrite()` with mode "rb", "wb", or "ab".

**Example:**
```c
#include <stdio.h>

struct Student {
    char name[50];
    int roll;
    float marks;
};

int main() {
    FILE *fp;
    struct Student s = {"John", 101, 85.5};
    
    // Write binary data
    fp = fopen("student.dat", "wb");
    fwrite(&s, sizeof(struct Student), 1, fp);
    fclose(fp);
    
    // Read binary data
    struct Student s2;
    fp = fopen("student.dat", "rb");
    fread(&s2, sizeof(struct Student), 1, fp);
    printf("Name: %s, Roll: %d, Marks: %.2f\n", 
           s2.name, s2.roll, s2.marks);
    fclose(fp);
    
    return 0;
}
```

---

## 13. Dynamic Memory Allocation

### 13.1 malloc()

**Definition:** Allocates a block of memory dynamically at runtime.

**Explanation:** `malloc(size)` allocates specified bytes and returns a void pointer. Returns NULL if allocation fails.

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr;
    int n, i;
    
    printf("Enter number of elements: ");
    scanf("%d", &n);
    
    ptr = (int*) malloc(n * sizeof(int));
    
    if (ptr == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }
    
    printf("Enter %d numbers:\n", n);
    for (i = 0; i < n; i++) {
        scanf("%d", &ptr[i]);
    }
    
    printf("Numbers entered: ");
    for (i = 0; i < n; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");
    
    free(ptr);
    return 0;
}
```

### 13.2 calloc()

**Definition:** Allocates memory and initializes all bytes to zero.

**Explanation:** `calloc(n, size)` allocates memory for n elements of given size and initializes to zero.

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *arr;
    int n = 5, i;
    
    arr = (int*) calloc(n, sizeof(int));
    
    if (arr == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }
    
    printf("Array elements (initialized to 0):\n");
    for (i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
    
    free(arr);
    return 0;
}
// Output: Array elements (initialized to 0):
//         0 0 0 0 0
```

### 13.3 realloc()

**Definition:** Changes the size of previously allocated memory.

**Explanation:** `realloc(ptr, new_size)` resizes the memory block. Can increase or decrease size.

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr;
    int n = 3, i;
    
    ptr = (int*) malloc(n * sizeof(int));
    
    for (i = 0; i < n; i++) {
        ptr[i] = i + 1;
    }
    
    printf("Original array: ");
    for (i = 0; i < n; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");
    
    // Resize to 5 elements
    n = 5;
    ptr = (int*) realloc(ptr, n * sizeof(int));
    
    for (i = 3; i < n; i++) {
        ptr[i] = i + 1;
    }
    
    printf("Resized array: ");
    for (i = 0; i < n; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");
    
    free(ptr);
    return 0;
}
// Output: Original array: 1 2 3
//         Resized array: 1 2 3 4 5
```

### 13.4 free()

**Definition:** Deallocates previously allocated memory.

**Explanation:** Always free dynamically allocated memory to prevent memory leaks. After freeing, the pointer should not be used.

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    int *ptr = (int*) malloc(sizeof(int));
    
    if (ptr == NULL) {
        printf("Allocation failed!\n");
        return 1;
    }
    
    *ptr = 100;
    printf("Value: %d\n", *ptr);
    
    free(ptr);
    ptr = NULL;  // Good practice
    
    return 0;
}
```

---

## 14. Preprocessor Directives

### 14.1 #include

**Definition:** Includes header files in the program.

**Explanation:**
- `#include <stdio.h>` - System header files
- `#include "myheader.h"` - User-defined header files

**Example:**
```c
#include <stdio.h>
#include <math.h>
#include <string.h>

int main() {
    printf("Square root of 16: %.2f\n", sqrt(16));
    char str[] = "Hello";
    printf("Length: %lu\n", strlen(str));
    return 0;
}
```

### 14.2 #define (Macros)

**Definition:** Defines constants and macros.

**Explanation:** Macros are preprocessor text substitutions. No memory allocated, replaced before compilation.

**Example:**
```c
#include <stdio.h>

#define PI 3.14159
#define SQUARE(x) ((x) * (x))
#define MAX(a, b) ((a) > (b) ? (a) : (b))

int main() {
    printf("PI = %.5f\n", PI);
    printf("Square of 5 = %d\n", SQUARE(5));
    printf("Max of 10 and 20 = %d\n", MAX(10, 20));
    return 0;
}
// Output: PI = 3.14159
//         Square of 5 = 25
//         Max of 10 and 20 = 20
```

### 14.3 Conditional Compilation

**Definition:** Compile code conditionally based on defined macros.

**Explanation:**
- `#ifdef` - If defined
- `#ifndef` - If not defined
- `#if` - If condition true
- `#else` - Alternative
- `#elif` - Else if
- `#endif` - End conditional

**Example:**
```c
#include <stdio.h>

#define DEBUG

int main() {
    int x = 10;
    
#ifdef DEBUG
    printf("Debug mode: x = %d\n", x);
#endif
    
    printf("Program running...\n");
    
#ifndef RELEASE
    printf("Not in release mode\n");
#endif
    
    return 0;
}
```

### 14.4 #undef

**Definition:** Undefines a previously defined macro.

**Example:**
```c
#include <stdio.h>

#define VALUE 100

int main() {
    printf("VALUE = %d\n", VALUE);
    
#undef VALUE
#define VALUE 200
    
    printf("New VALUE = %d\n", VALUE);
    return 0;
}
```

---

## 15. Typedef and Enums

### 15.1 typedef

**Definition:** Creates an alias for existing data types.

**Explanation:** Makes code more readable and maintainable. Commonly used with structures and pointers.

**Example:**
```c
#include <stdio.h>

typedef unsigned long ulong;
typedef int* intptr;

typedef struct {
    char name[50];
    int age;
} Person;

int main() {
    ulong bignum = 1234567890UL;
    printf("Big number: %lu\n", bignum);
    
    Person p1 = {"Alice", 25};
    printf("Name: %s, Age: %d\n", p1.name, p1.age);
    
    intptr ptr;
    int x = 100;
    ptr = &x;
    printf("Value: %d\n", *ptr);
    
    return 0;
}
```

### 15.2 Enumerations (enum)

**Definition:** User-defined data type consisting of named integer constants.

**Explanation:** By default, first value is 0 and increases by 1. Can be explicitly assigned values.

**Example:**
```c
#include <stdio.h>

enum Day {
    SUNDAY,    // 0
    MONDAY,    // 1
    TUESDAY,   // 2
    WEDNESDAY, // 3
    THURSDAY,  // 4
    FRIDAY,    // 5
    SATURDAY   // 6
};

enum Status {
    SUCCESS = 1,
    FAILURE = 0,
    PENDING = -1
};

int main() {
    enum Day today = WEDNESDAY;
    enum Status result = SUCCESS;
    
    printf("Today is day number: %d\n", today);
    
    if (result == SUCCESS) {
        printf("Operation successful!\n");
    }
    
    return 0;
}
// Output: Today is day number: 3
//         Operation successful!
```

---

## 16. Command Line Arguments

### 16.1 argc and argv

**Definition:** Passing arguments to the program from command line.

**Explanation:**
- `argc` - Argument count (number of arguments)
- `argv` - Argument vector (array of string pointers)
- `argv[0]` is always the program name

**Example:**
```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    printf("Number of arguments: %d\n", argc);
    
    printf("Arguments:\n");
    for (int i = 0; i < argc; i++) {
        printf("argv[%d]: %s\n", i, argv[i]);
    }
    
    return 0;
}
// If run as: ./program hello world
// Output: Number of arguments: 3
//         Arguments:
//         argv[0]: ./program
//         argv[1]: hello
//         argv[2]: world
```

### 16.2 Processing Command Line Arguments

**Definition:** Using command line arguments for program input.

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    if (argc != 3) {
        printf("Usage: %s <num1> <num2>\n", argv[0]);
        return 1;
    }
    
    int a = atoi(argv[1]);
    int b = atoi(argv[2]);
    
    printf("%d + %d = %d\n", a, b, a + b);
    printf("%d * %d = %d\n", a, b, a * b);
    
    return 0;
}
// Run as: ./program 5 3
// Output: 5 + 3 = 8
//         5 * 3 = 15
```

---

## 17. Bitwise Operators

### 17.1 Bitwise Operations

**Definition:** Operators that work on individual bits of integer values.

**Explanation:**
- `&` - Bitwise AND
- `|` - Bitwise OR
- `^` - Bitwise XOR
- `~` - Bitwise NOT (complement)
- `<<` - Left shift
- `>>` - Right shift

**Example:**
```c
#include <stdio.h>

int main() {
    unsigned int a = 12;  // 1100 in binary
    unsigned int b = 10;  // 1010 in binary
    
    printf("a = %u, b = %u\n", a, b);
    printf("a & b = %u\n", a & b);  // 1000 = 8
    printf("a | b = %u\n", a | b);  // 1110 = 14
    printf("a ^ b = %u\n", a ^ b);  // 0110 = 6
    printf("~a = %u\n", ~a);
    printf("a << 1 = %u\n", a << 1); // 11000 = 24
    printf("a >> 1 = %u\n", a >> 1); // 110 = 6
    
    return 0;
}
```

### 17.2 Practical Bitwise Applications

**Definition:** Real-world uses of bitwise operations.

**Example:**
```c
#include <stdio.h>

int main() {
    int num = 29;
    
    // Check if even or odd
    if (num & 1)
        printf("%d is odd\n", num);
    else
        printf("%d is even\n", num);
    
    // Swap two numbers without temp variable
    int a = 5, b = 10;
    printf("Before: a=%d, b=%d\n", a, b);
    a = a ^ b;
    b = a ^ b;
    a = a ^ b;
    printf("After: a=%d, b=%d\n", a, b);
    
    // Multiply by 2 using left shift
    int x = 7;
    printf("%d * 2 = %d\n", x, x << 1);
    
    // Divide by 2 using right shift
    printf("%d / 2 = %d\n", x, x >> 1);
    
    return 0;
}
```

---

## 18. Storage Classes

### 18.1 auto

**Definition:** Default storage class for local variables.

**Explanation:** Automatic storage duration. Created when block is entered, destroyed when block is exited.

**Example:**
```c
#include <stdio.h>

int main() {
    auto int x = 10;  // 'auto' is implicit
    printf("x = %d\n", x);
    return 0;
}
```

### 18.2 static

**Definition:** Preserves variable value between function calls.

**Explanation:** Static variables retain their values throughout program execution. Local scope but persistent lifetime.

**Example:**
```c
#include <stdio.h>

void counter() {
    static int count = 0;
    count++;
    printf("Count: %d\n", count);
}

int main() {
    counter();  // Count: 1
    counter();  // Count: 2
    counter();  // Count: 3
    return 0;
}
```

### 18.3 extern

**Definition:** Declares a global variable defined in another file.

**Explanation:** Used for sharing variables across multiple files.

**Example:**
```c
// File1.c
int global_var = 100;

// File2.c
#include <stdio.h>
extern int global_var;

int main() {
    printf("Global variable: %d\n", global_var);
    return 0;
}
```

### 18.4 register

**Definition:** Suggests storing variable in CPU register for faster access.

**Explanation:** Compiler may ignore this suggestion. Cannot use address-of operator (&) with register variables.

**Example:**
```c
#include <stdio.h>

int main() {
    register int i;
    
    for (i = 0; i < 5; i++) {
        printf("%d ", i);
    }
    printf("\n");
    
    return 0;
}
```

---

## 19. Advanced Concepts

### 19.1 Recursion

**Definition:** A function calling itself to solve a problem.

**Explanation:** Must have a base case to prevent infinite recursion. Useful for problems with recursive structure.

**Example:**
```c
#include <stdio.h>

// Factorial using recursion
int factorial(int n) {
    if (n <= 1)
        return 1;
    return n * factorial(n - 1);
}

// Fibonacci series
int fibonacci(int n) {
    if (n <= 1)
        return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

int main() {
    printf("Factorial of 5: %d\n", factorial(5));
    
    printf("Fibonacci series: ");
    for (int i = 0; i < 10; i++) {
        printf("%d ", fibonacci(i));
    }
    printf("\n");
    
    return 0;
}
// Output: Factorial of 5: 120
//         Fibonacci series: 0 1 1 2 3 5 8 13 21 34
```

### 19.2 Function Pointers

**Definition:** Pointers that store addresses of functions.

**Explanation:** Allows passing functions as arguments and creating callback mechanisms.

**Example:**
```c
#include <stdio.h>

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int main() {
    int (*operation)(int, int);
    
    operation = add;
    printf("10 + 5 = %d\n", operation(10, 5));
    
    operation = subtract;
    printf("10 - 5 = %d\n", operation(10, 5));
    
    return 0;
}
// Output: 10 + 5 = 15
//         10 - 5 = 5
```

### 19.3 Pointer to Pointer

**Definition:** A pointer variable that stores the address of another pointer.

**Example:**
```c
#include <stdio.h>

int main() {
    int var = 100;
    int *ptr = &var;
    int **pptr = &ptr;
    
    printf("Value of var: %d\n", var);
    printf("Value using ptr: %d\n", *ptr);
    printf("Value using pptr: %d\n", **pptr);
    
    printf("Address of var: %p\n", (void*)&var);
    printf("Value of ptr: %p\n", (void*)ptr);
    printf("Value of pptr: %p\n", (void*)pptr);
    
    return 0;
}
```

### 19.4 Const Qualifier

**Definition:** Makes variables read-only (constant).

**Example:**
```c
#include <stdio.h>

int main() {
    const int MAX = 100;
    // MAX = 200;  // Error: cannot modify const
    
    printf("MAX = %d\n", MAX);
    
    const int *ptr;  // Pointer to constant int
    int const *ptr2; // Same as above
    int * const ptr3 = &MAX; // Constant pointer to int
    
    return 0;
}
```

### 19.5 Volatile Qualifier

**Definition:** Tells compiler the variable may change unexpectedly.

**Explanation:** Prevents compiler optimization. Used in embedded systems and hardware programming.

**Example:**
```c
#include <stdio.h>

int main() {
    volatile int flag = 0;
    
    // Compiler won't optimize away this variable
    // Useful for hardware registers or multi-threaded code
    
    while (flag == 0) {
        // Wait for flag to change (by hardware or another thread)
    }
    
    return 0;
}
```

---

## 20. Common Standard Library Functions

### 20.1 Math Functions (math.h)

**Example:**
```c
#include <stdio.h>
#include <math.h>

int main() {
    printf("sqrt(16) = %.2f\n", sqrt(16.0));
    printf("pow(2, 3) = %.2f\n", pow(2.0, 3.0));
    printf("ceil(4.3) = %.2f\n", ceil(4.3));
    printf("floor(4.7) = %.2f\n", floor(4.7));
    printf("abs(-10) = %d\n", abs(-10));
    printf("sin(0) = %.2f\n", sin(0.0));
    printf("cos(0) = %.2f\n", cos(0.0));
    printf("log(10) = %.2f\n", log(10.0));
    
    return 0;
}
```

### 20.2 Character Functions (ctype.h)

**Example:**
```c
#include <stdio.h>
#include <ctype.h>

int main() {
    char ch = 'a';
    
    printf("isalpha('a') = %d\n", isalpha(ch));
    printf("isdigit('5') = %d\n", isdigit('5'));
    printf("isupper('A') = %d\n", isupper('A'));
    printf("islower('a') = %d\n", islower('a'));
    printf("toupper('a') = %c\n", toupper(ch));
    printf("tolower('A') = %c\n", tolower('A'));
    printf("isspace(' ') = %d\n", isspace(' '));
    
    return 0;
}
```

### 20.3 Time Functions (time.h)

**Example:**
```c
#include <stdio.h>
#include <time.h>

int main() {
    time_t current_time;
    struct tm *local_time;
    
    time(&current_time);
    local_time = localtime(&current_time);
    
    printf("Current date and time: %s", asctime(local_time));
    printf("Year: %d\n", local_time->tm_year + 1900);
    printf("Month: %d\n", local_time->tm_mon + 1);
    printf("Day: %d\n", local_time->tm_mday);
    printf("Hour: %d\n", local_time->tm_hour);
    printf("Minute: %d\n", local_time->tm_min);
    printf("Second: %d\n", local_time->tm_sec);
    
    return 0;
}
```

### 20.4 Random Number Generation (stdlib.h)

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    // Seed the random number generator
    srand(time(NULL));
    
    printf("5 random numbers:\n");
    for (int i = 0; i < 5; i++) {
        printf("%d ", rand() % 100);  // Random between 0-99
    }
    printf("\n");
    
    return 0;
}
```

---

## 21. Best Practices and Tips

### 21.1 Code Style

- Use meaningful variable and function names
- Indent code consistently (4 spaces or 1 tab)
- Add comments to explain complex logic
- Keep functions small and focused
- Use constants instead of magic numbers

**Example:**
```c
#include <stdio.h>

#define MAX_STUDENTS 50
#define PASSING_MARKS 40

// Good: Descriptive function name
int calculateAverage(int marks[], int count) {
    int sum = 0;
    for (int i = 0; i < count; i++) {
        sum += marks[i];
    }
    return sum / count;
}

int main() {
    int studentMarks[MAX_STUDENTS];
    int numStudents = 5;
    
    // Input marks
    for (int i = 0; i < numStudents; i++) {
        printf("Enter marks for student %d: ", i + 1);
        scanf("%d", &studentMarks[i]);
    }
    
    int avg = calculateAverage(studentMarks, numStudents);
    printf("Average marks: %d\n", avg);
    
    return 0;
}
```

### 21.2 Common Mistakes to Avoid

**Example:**
```c
#include <stdio.h>
#include <string.h>

int main() {
    // Mistake 1: Array index out of bounds
    int arr[5] = {1, 2, 3, 4, 5};
    // arr[5] = 10;  // ERROR: Valid indices are 0-4
    
    // Mistake 2: Uninitialized variable
    int x;
    // printf("%d", x);  // Bad: x has garbage value
    x = 0;  // Always initialize
    
    // Mistake 3: String assignment
    char str[20];
    // str = "Hello";  // ERROR: Cannot assign to array
    strcpy(str, "Hello");  // Correct way
    
    // Mistake 4: Comparing strings with ==
    char s1[] = "test";
    char s2[] = "test";
    // if (s1 == s2)  // Wrong: Compares addresses
    if (strcmp(s1, s2) == 0)  // Correct: Compares content
        printf("Strings are equal\n");
    
    // Mistake 5: Forgetting break in switch
    int choice = 1;
    switch(choice) {
        case 1:
            printf("One\n");
            break;  // Don't forget break!
        case 2:
            printf("Two\n");
            break;
        default:
            printf("Other\n");
    }
    
    return 0;
}
```

### 21.3 Memory Management Tips

**Example:**
```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    // Always check if malloc succeeded
    int *ptr = (int*) malloc(10 * sizeof(int));
    if (ptr == NULL) {
        printf("Memory allocation failed!\n");
        return 1;
    }
    
    // Use the allocated memory
    for (int i = 0; i < 10; i++) {
        ptr[i] = i;
    }
    
    // Always free allocated memory
    free(ptr);
    
    // Set pointer to NULL after freeing
    ptr = NULL;
    
    return 0;
}
```

---

## 22. Quick Reference

### 22.1 Format Specifiers

| Specifier | Data Type |
|-----------|-----------|
| %d, %i | int |
| %u | unsigned int |
| %ld | long |
| %lu | unsigned long |
| %lld | long long |
| %f | float |
| %lf | double |
| %c | char |
| %s | string |
| %p | pointer |
| %x, %X | hexadecimal |
| %o | octal |
| %e, %E | scientific notation |

### 22.2 Escape Sequences

| Sequence | Meaning |
|----------|---------|
| \n | Newline |
| \t | Tab |
| \\ | Backslash |
| \" | Double quote |
| \\' | Single quote |
| \0 | Null character |
| \r | Carriage return |
| \b | Backspace |

### 22.3 Operator Precedence (Highest to Lowest)

1. Parentheses `()`
2. Postfix `++`, `--`
3. Prefix `++`, `--`, `!`, `~`, `-` (unary)
4. `*`, `/`, `%`
5. `+`, `-`
6. `<<`, `>>`
7. `<`, `<=`, `>`, `>=`
8. `==`, `!=`
9. `&`
10. `^`
11. `|`
12. `&&`
13. `||`
14. `?:` (ternary)
15. Assignment `=`, `+=`, `-=`, etc.

---

## Conclusion

This comprehensive C Programming Cheat Sheet covers all fundamental and advanced topics essential for mastering the C programming language. From basic data types to advanced concepts like dynamic memory allocation, file handling, and bitwise operations, this guide provides practical examples and clear explanations for each concept.

**Key Takeaways:**
- Practice regularly with code examples
- Understand memory management and pointers thoroughly
- Follow best practices for clean, maintainable code
- Always test your code with different inputs
- Learn to debug effectively

Happy Coding! 🚀

---

*Last Updated: 2025-11-08*