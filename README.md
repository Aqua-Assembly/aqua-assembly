![](https://imgur.com/MZlQjJr.png)
# Aqua Language Compiler Documentation

**Version 1.0**

## Table of Contents

- [Introduction](#introduction)
- [Dependencies](#dependencies)
- [Instructions](#instructions)
- [Usage](#usage)
- [Code Examples](#code-examples)
- [Additional Notes](#additional-notes)

## Introduction

Aqua is a simplified assembly language designed for learning and experimentation. This compiler translates Aqua assembly code into binary machine code, allowing users to practice low-level programming and understand basic assembly concepts. Aqua is designed to be approachable and educational, making it a great tool for those new to assembly language.

## Dependencies

To use the Aqua compiler, you need the following dependencies:

- **GCC**: The GNU Compiler Collection, which provides the necessary compiler infrastructure.
- **LD**: The GNU linker, used to link the compiled code.
- **Make** (optional): A build automation tool for managing the build process.

Ensure these tools are installed and accessible from your command line. You can install them using your system’s package manager. For example, on a Debian-based system, you can install them with:

```bash
sudo apt-get install gcc binutils make
```

## Instructions

The Aqua assembly language includes the following instructions:

### Data Movement

- **`MOVE_TO destination, source`**: Move data from the source to the destination.
- **`PUSH_STACK value`**: Push a value onto a custom stack.
- **`POP_STACK`**: Pop a value from the custom stack.
- **`TRANSFER src, dest`**: Transfer data between two locations.

**Example:**
```assembly
MOVE_TO 0x1000, 0x2000    ; Move data from address 0x2000 to address 0x1000
PUSH_STACK 5               ; Push the value 5 onto the stack
POP_STACK                  ; Pop the top value from the stack
TRANSFER 0x3000, 0x4000    ; Transfer data from address 0x4000 to address 0x3000
```

### Arithmetic

- **`SUM a, b, result`**: Compute the sum of `a` and `b`, store in `result`.
- **`DIFFERENCE a, b, result`**: Compute the difference between `a` and `b`, store in `result`.
- **`PRODUCT a, b, result`**: Compute the product of `a` and `b`, store in `result`.
- **`QUOTIENT a, b, result`**: Compute the quotient of `a` divided by `b`, store in `result`.
- **`UP value`**: Increase a value by one.
- **`DOWN value`**: Decrease a value by one.

**Example:**
```assembly
SUM 10, 20, 0x5000         ; Compute the sum of 10 and 20, store in address 0x5000
DIFFERENCE 30, 10, 0x5001  ; Compute the difference between 30 and 10, store in address 0x5001
UP 0x5000                  ; Increment the value at address 0x5000
DOWN 0x5001                ; Decrement the value at address 0x5001
```

### Logic

- **`AND_LOGIC a, b, result`**: Perform a logical AND operation between `a` and `b`, store in `result`.
- **`OR_LOGIC a, b, result`**: Perform a logical OR operation between `a` and `b`, store in `result`.
- **`XOR_LOGIC a, b, result`**: Perform a logical XOR operation between `a` and `b`, store in `result`.
- **`INVERT value`**: Invert all bits in the value.

**Example:**
```assembly
AND_LOGIC 0xFF, 0x0F, 0x6000 ; Perform AND operation between 0xFF and 0x0F, store in address 0x6000
INVERT 0x6000                ; Invert all bits in the value at address 0x6000
```

### Control Flow

- **`GOTO label`**: Unconditional jump to a label.
- **`IF_EQUAL a, b, label`**: Jump to `label` if `a` is equal to `b`.
- **`IF_NOT_EQUAL a, b, label`**: Jump to `label` if `a` is not equal to `b`.
- **`IF_GREATER a, b, label`**: Jump to `label` if `a` is greater than `b`.
- **`IF_LESS a, b, label`**: Jump to `label` if `a` is less than `b`.
- **`CALL_FUNC func`**: Call a function or subroutine.
- **`RETURN_FUNC`**: Return from a function or subroutine.
- **`REPEAT count`**: Repeat a block of code a specified number of times.
- **`WAIT_FOR condition`**: Wait for a specific condition or event to occur.

**Example:**
```assembly
GOTO start        ; Jump to the label "start"
IF_EQUAL 10, 10, end   ; Jump to "end" if 10 is equal to 10
REPEAT 5          ; Repeat the following block 5 times
    UP 0x7000     ; Increment value at address 0x7000
WAIT_FOR condition ; Wait for a specific condition to be met
```

### String Operations

- **`COPY_CHAR src, dest`**: Copy a single character from `src` to `dest`.
- **`COPY_STRING src, dest`**: Copy an entire string from `src` to `dest`.
- **`COMPARE_CHAR a, b`**: Compare two single characters.
- **`COMPARE_STRING str1, str2`**: Compare two strings.

**Example:**
```assembly
COPY_CHAR 0x8000, 0x8001    ; Copy a character from address 0x8001 to address 0x8000
COMPARE_STRING 0x8100, 0x8200 ; Compare the string at address 0x8100 with the string at 0x8200
```

### Miscellaneous

- **`DO_NOTHING`**: Perform no operation.
- **`TRIGGER event`**: Trigger a specific event or exception.
- **`HALT`**: Halt execution of the program.

**Example:**
```assembly
DO_NOTHING             ; No operation performed
TRIGGER error          ; Trigger an error event
HALT                  ; Halt execution
```

## Usage

To compile Aqua assembly code, use the following command:

```bash
aqua-x86 -c <codefile> -o <outputfile> [-f]
```

### Options
- **`-c`**: Specifies the input Aqua assembly source file.
- **`-o`**: Specifies the output binary file.
- **`-f`**: Force overwrite of an existing output file (optional).

## Code Examples

Here are some simple Aqua programs to illustrate the usage of various instructions.

### Example 1: Adding Two Numbers

```assembly
MOVE_TO 0x1000, 10     ; Move the value 10 to address 0x1000
MOVE_TO 0x1001, 20     ; Move the value 20 to address 0x1001
SUM 0x1000, 0x1001, 0x1002 ; Compute the sum of values at 0x1000 and 0x1001, store result at 0x1002
HALT                   ; Halt execution
```

### Example 2: Loop with Conditional Check

```assembly
MOVE_TO 0x2000, 0     ; Initialize counter at address 0x2000
LOOP_START:
UP 0x2000              ; Increment the counter
IF_LESS 0x2000, 10, LOOP_START ; If counter is less than 10, jump to LOOP_START
HALT                   ; Halt execution
```

## Additional Notes

Ensure that the Aqua assembly code is correctly formatted and free of syntax errors before compilation. The compiler will halt and report errors if unknown instructions or syntax issues are encountered. It's important to thoroughly test your code to ensure correct functionality and avoid runtime errors.

---

&copy; 2024 Aqua Language Project
```

This updated documentation now includes a section on dependencies to help users set up their environment before using the Aqua compiler.
