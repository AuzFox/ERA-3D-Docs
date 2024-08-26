## Introduction

!!! warning
	This page assumes you are already familiar with basic programming concepts and data types.

ERA-3D games are programmed in a scripting language called ERA-C. ERA-C is similar to C in many ways, but has a few key differences that are worth noting.

If you are already familiar with C, see the [Differences From C](#differences-from-c) section.

## Comments

Comments in ERA-C follow the same syntax as C/C++.

```C
// single-line comment
int a = 32; // another comment
/*
multi
line
comment
*/
```

Multi-line comments can be nested.

```C
/*
  this is a comment
  /*
    this is a nested comment
  */
  this is still a comment
*/
```

## Variables

Both local and global variables are declared using the pattern `<data type> <name> ;`.

Variable names must start with a letter and can contain the characters `a-z, A-Z, 0-9, _`

```C
int my_int; // an int variable
float my_float; // a float variable
```

Local variables (variables declared inside a function or loop scope) can be assigned a value when they are declared.

```C
int foo = 42;
```

Global variables must be initialized inside of a function.

The `init()` function is a good place for that. (See the [Hook Functions](#hook-functions) section)

## Primitive Types

Primitive types are data types built into the ERA-C compiler.

### `int`

`int` is a data type that is capable of storing positive and negative whole numbers.

Specifically, they are 32-bit integers. Most operations treat them as signed integers, but some operators treat `int` values as unsigned.

Integer literal values can be given in decimal form, but they can also be represented in hexadecimal and binary form using the `0x` and `0b` prefixes.

Unlike C, leading zeros do not mean a number is in octal format.

```C
int a = 24; // positive value
int b = -24; // negative value
int hex = 0xFF; // hexadecimal value (255)
int binary = 0b10101010; // binary value (170)

// to make large numbers easier to read, underscores can be inserted between digits.
int big_number = 12_345_678;

// character literals are also supported, and are interpreted as int values.
int letter_e = 'E';
```

ERA-C has a special syntax for encoding note values used by the soundchip.

The `0n` prefix followed by a note name (see list below) and an octave number (0-8) define a note.

```C
int c_sharp_4 = 0nC#4; // soundchip note value (note C#, octave 4)
```

All valid note names are listed below. Notes can be written using upper or lower case.

`C, C#, D, D#, E, F, F#, G, G#, A, A#, B`

`int`s support various arithmetic operations, as well as bitwise and logical ones.

`+`, `-`, `*`, `/`, and `%` are the addition, subtraction, multiplication, division, and modulus operators. They follow the same precedence rules as C.

```C
int a = 2 + 2;
int b = 5 - 3;
int c = 9 * 100;
int d = 10 / 2;
int e = 10 % 5;
```

!!! info
	Dividing `int` values does not result in a fractional value, the fractional component is discarded instead.
	
	`5 / 2` returns 2, not 2.5.

ERA-C also supports bitwise operations for integers.

```C
int a = ~0b00001111; // bitwise NOT: a = 0b11110000
int b = 0b10101010 | 0b01010101; // bitwise OR: b = 0b11111111
int c = 0b10101111 & 0b00111100; // bitwise AND: c = 0b00101100
int d = 0b11001100 ^ 0b10101010; // bitwise XOR: d = 0b01100110
int e = 0b00001111 << 2; // bitwise left shift: e = 0b00111100
int f = 0b11110000 >> 4; // bitwise right shift (logical): f = 0b00001111
int g = 0b10000000 >>> 4; // bitwise right shift (arithmetic): f = 0b11111000
```

The logical and comparison operators return an integer value, so their result can be stored in an `int`.

If the comparison is true, a value of 1 is returned. Otherwise, 0 is returned.

```C
int a = 1 < 2; // a = 1 (true)
int b = 1 == 2; // b = 0 (false)
```

### `float`

`float`s are 32-bit floating point values, meaning they are numbers with a fractional component.

```C
float my_float = 2.5;
```

`floats` support the `+`, `-`, `*`, `/`, and `%` operators, as well as the comparison operators.

### `vec2`

`vec2` represents a 2D vector with `x` and `y` components.

`x` and `y` both have the `float` data type.

```C
vec2 v = vec2(1.0, 2.0); // 2D vector with the value (x=1.0, y=2.0)

v.x = 9.0; // assigning a new x value
v.y = 0.25; // assigning a new y value
```

The following table lists special functions used to construct `vec2`s with common values:

Function | `vec2` Return Value
-|-
`vec2Zero()` | `{0.0, 0.0}` (equivalent to `vec2()` with no arguments)
`vec2One()` | `{1.0, 1.0}`
`vec2Up()` | `{0.0, -1.0}`
`vec2Down()` | `{0.0, 1.0}`
`vec2Left()` | `{-1.0, 0.0}`
`vec2Right()` | `{1.0, 0.0}`

### `vec3`

`vec3` represents a 3D vector with `x`, `y`, and `z` components.

`x`, `y`, and `z` all have the `float` data type.

```C
vec3 v = vec3(1.0, 2.0, 3.0); // 3D vector with the value (x=1.0, y=2.0, z=3.0)

v.x = 7.5; // assigning a new x value
v.y = 0.75; // assigning a new y value
v.z = 4.9; // assigning a new z value
```

The following table lists special functions used to construct `vec3`s with common values:

Function | `vec3` Return Value
-|-
`vec3Zero()` | `{0.0, 0.0, 0.0}` (equivalent to `vec3()` with no arguments)
`vec3One()` | `{1.0, 1.0, 1.0}`
`vec3Up()` | `{0.0, 1.0, 0.0}`
`vec3Down()` | `{0.0, -1.0, 0.0}`
`vec3Left()` | `{-1.0, 0.0, 0.0}`
`vec3Right()` | `{1.0, 0.0, 0.0}`
`vec3Forward()` | `{0.0, 0.0, -1.0}`
`vec3Back()` | `{0.0, 0.0, 1.0}`

Both `vec2` and `vec3` support addition, subtraction, multiplication, and division.

Vector types cannot be mixed in vector arithmetic, only vectors of the same dimensions can be added, subtracted, etc.

During a arithmetic operation, the individual members of the vector are operated on. For example, when adding two `vec2` values, the result will be `vec2(a.x + b.x, a.y + b.y)`. The same pattern applies to all arithmetic operators.

```C
vec2 v2 = vec2(1.1, 2.2) + vec2(3.3, 4.4); // v2 = vec2(4.4, 6.6)
vec3 v3 = vec3(1.1, 2.2, 3.3) + vec3(4.4, 5.5, 6.6); // v3 = vec3(5.5, 7.7, 9.9)
```

Vectors can also be multiplied and divided by `int` and `float` values. This will return a vector with each member having been multiplied/divided by the `int`/`float` value.

```C
vec3 a = vec3(1.1, 2.2, 3.3) * 2; // a = vec3(2.2, 4.4, 6.6)
vec2 b = vec2(5.0, 10.0) / 2.5; // b = vec2(2.0, 4.0)
```

Vectors support all comparison operators, and can only be compared with their same type.

Comparing vectors compares each member pair, and the comparison is only true if all pairs satisfy the comparison.

```C
vec2 a = vec2(10.0, 20.0);
vec2 b = vec2(1.0, 2.0);

int result = a < b; // result = 1 (true), as a.x < b.x and a.y < b.y
```

### `string`

The `string` data type is used to hold text.

`string` literals must be enclosed within double-quotes (`"`).

```C
string text = "hello world!";
```

To fetch a character from the string, or to change a character, use the following expression: `<variable> [ <index> ];`.

The characters of a string are zero-indexed, meaning that the first character is stored at index 0.

```C
string text = "hello world!";
int character = text[0]; // fetch a character
```

Internally, `string` is a struct (see the [Structs](#structs) section) that looks like this:

```C
struct string {
  int length;
  void* data;
};
```

!!! warning
	String literals allocate space in cartridge ROM to store their data, so trying to write characters into a `string` initialized using a literal will cause an error and halt the program.

	If a modifiable string is needed, a `string` struct can be manually created to point to somewhere in RAM.

Strings support the `==` and `!=` operators. Two strings are considered equal if the following conditions are met:

1. both strings are the same length
2. both strings point to the same address or the characters in both strings match

### Arrays

Arrays are essentially blocks of memory used to store a list of elements all of a particular data type. For example, you might have an array containing 10 `int` values, or an array containing 5 `vec2` values.

Arrays are fixed in size, once they are declared the cannot be resized.

```C
int my_array[10]; // declare an array of 10 ints
```

Access array elements using the pattern `<array variable> [ <index> ]`, where `<index>` is an integer value.

Array values are zero-indexed; meaning the first element in the array is stored at index 0, the second at index 1, and so on.

```C
int my_array[10];
int x = my_array[0]; // get the first value stored in the array
my_array[1] = 99; // store a new value in the array at index 1
```

### Pointers

ERA-C supports pointers, which behave similarly to pointers in C. To declare a pointer to a type, put a `*` after the data type.

```C
int* int_pointer; // pointer to an int
```

To obtain the memory address of a variable, use the address-of operator. (`&`)

```C
int x = 42; // normal int variable
int* ptr = &x; // ptr now contains the memory address of x 
```

The unary dereference operator (`*`) can be used to fetch the value pointed to by a pointer.

```C
int x = 42;
int* ptr = &x;
int y = *ptr; // y now contains the same value as x
```

Like arrays, pointers can be used to access multiple contiguous values stored next to each other in memory.

```C
int* p = 0; // in this example, p points to memory address 0, which corresponds to general-purpose memory.
int first = p[0]; // get the first value stored at the address p points to
p[1] = 100; // store a new value at the address p points to plus an offset of 1 int. (which would be the address 4. 1 int = 4 bytes)
```

A pointer with the type `void*` is a special type of pointer that can point to any data type. Pointers of this type are called "void pointers".

Void pointers cannot be dereferenced, they are only used as a container for arbitrary memory addresses.

Any pointer type and be assigned the value of a void pointer, and vice versa.

```C
int i = 100;
float f = 32.2;
void* p = &i; // p points to i
int x = *p; // ERROR: cannot dereference void pointers!
p = &f; // p now points to f
```

Pointers can be assigned arbitrary integer values, and thus arbitrary memory addresses.

In C, this is dangerous and discouraged most of the time, but in ERA-C it is needed to access specific parts of memory.

```C
int* p = 0x00800000; // p now points to address 0x00800000, which is the beginning of the system's texture memory
```

!!! warning
	Pointers in ERA-C must be aligned when dereferencing them, meaning the address they contain must be a multiple of the size of the type they point to (or address 0). If a pointer is misaligned when it is dereferenced, en error will be raised and the program will halt.

Pointers can be added to or subtracted from, changing the address they point to. This is referred to as "pointer arithmetic".

Adding a value of 1 to a pointer will increase its address by the size of the data type it points to.

For example, adding 1 to a `int*` will increase its address by 4, since `int`s are 4 bytes in size.

!!! info
	Void pointers do not support pointer arithmetic.

```C
int* p = 0;
p = p + 1; // p now points to the next int in memory
```

The `sizeof()` operator will return the size of a given type in bytes.

```C
int size = sizeof(int); // size = 4
```

`null` is a special constant that represents an invalid memory address. Unlike C's `NULL`, it is not equal to the integer value 0.

Assign a pointer to `null` to signify that it does not currently point to a valid address.

```C
void* p = null;
```

### Structs

Structs are compound data types that are made up of other smaller types. They are useful for representing complex objects with many attributes.

```C
struct MyStruct {
  int a;
  float b;
  int c;
};
```

In the above example, the struct `MyStruct` is declared, and contains an `int` and `float` members.

!!! info
	Structs must be declared outside of any function, and before they are used as a variable type.

To create a struct instance variable, use the struct name as the variable type.

```C
MyStruct instance;
```

Struct instances can be created using the pattern `<struct name> ( <member values...> )`

```C
Mystruct instance = Mystruct(1, 2.5, 3); // create a MyStruct instance with the value (a=1, b=2.5, c=3)
```

C-style struct initializers are also allowed.

These use the pattern `( <struct name> ) { <member values...> }`

```C
Mystruct instance = (Mystruct){1, 2.5, 3}; // create a MyStruct instance with the value (a=1, b=2.5, c=3)
```

If a struct initializer's member value list is left empty, all struct members will be initialized to zero.

```C
MyStruct instance = MyStruct(); // instance = (0, 0.0, 0)
vec3 v = vec3(); // v = (0.0, 0.0, 0.0)
```

To access struct members, use the dot operator. (`.`)

```C
Mystruct instance = MyStruct(1, 2.5, 3);
int x = instance.a; // x now contains 1
instance.b = 10.1; // set the b member of instance to a new value
```

When accessing a struct using a pointer, the arrow operator (`->`) must be used instead of the dot operator.

```C
Mystruct instance = MyStruct(1, 2.5, 3);
MyInstance* p = &instance; // p points to instance
p -> a = 22; // access the a member of instance using the pointer p
```

### Function Pointers

Function pointers are special pointers that point to code, rather than data.

To declare a function pointer, use the pattern `<return type> ( <argument types...> ) <variable name> ;`

```C
void(int, float) func_ptr; // func_ptr points to a function that accepts an `int` and `float` argument and does not return a value.
```

Assign a function pointer by using the name of the function to point to.

```C
void my_function(int a, float b) {
  // ... function code here ...
}

void(int, float) func_ptr = my_function;
```

Function pointers do not support pointer arithmetic, and can only be cast to `void*`.

Function pointers can be assigned `null`.

## Type Casting

Type casting in ERA-C works much like C. To cast an expression to another type, use the pattern `( <type> ) <expression>`.

```C
float f = 2.5;
int i = (int)f; // cast the float value of f to an int
```

`float` to `int` casting discards the fractional component of the `float`. (The value is truncated)

In the above example, `i` would have the value 2 after the cast.

The following table lists all accepted casts:

Original Type | Target Type | Result
-|-|-
`int` | `float` | `float` equal to the original integer value.
`int` | Non-function pointer | Pointer with address equal to the original integer value.
`float` | `int` | `int` containing the truncated integer value of the `float`.
Non-function pointer | `int` | `int` containing the address of the original pointer value.
Function pointer | `void*` | `void*` containing the address of the original function pointer value.
`void*` | Function pointer | Function pointer containing the address of the original void pointer value.

## Enums

Enums are lists of compile-time constants used to represent numerical values.

```C
// declaring an enum
enum {
  VALUE_A = 0, // enum entries can be assigned direct values
  VALUE_B, // when no value is given, an entry is assigned a value that is 1 higher than the previous entry
  VALUE_C
};

// using the enum entries
int x = VALUE_C; // x = 2
```

!!! info
	Enums must be declared outside of any function, and before their members are used in an expression.

## Operators

ERA-C has the following operators:

Operator | Description
-|-
`+` | Addition
`-` | Subtraction
`*` | Multiplication
`/` | Division
`%` | Modulus
`!` | Logical Not (Unary)
`&&` | Logical And
`||` | Logical Or
`==` | Equal-to Comparision
`!=` | Not-Equal-to Comparision
`<` | Less-Than Comparision
`>` | Greater-Than Comparision
`<=` | Less-Than-or-Equal-to Comparision
`>=` | Greater-Than-or-Equal-to Comparision
`~` | Bitwise NOT (Unary)
`&` | Bitwise AND
`|` | Bitwise OR
`^` | Bitwise XOR
`<<` | Bitwise Left Shift
`>>` | Bitwise Logical Right Shift
`>>>` | Bitwise Arithmetic Right Shift
`.` | Struct Member Access
`->` | Struct Member Access (Pointer)
`sizeof()` | Type Size (in bytes)

## Control Flow

`if` statements work just like in C.

```C
int x = 1;

if (x == 1) {
  // do something...
}
else if (x == 2) {
  // do something else...
}
else {
  // no previous conditions were true
}
```

`int` values can be used as conditions. A value of 0 is `false`, all non-zero values are `true`.

Pointers and function pointers can be used as the `if` statement condition to check if they point to valid addresses.

```
void* p = null;

if (p) {
  // p points to a valid address
}
else {
  // p is not valid
}
```

!!! info
	The expression `my_pointer == null` will only be true if `my_pointer` contains exactly the value `null`.

## Loops

ERA-C supports `for` and `while` loops with the same syntax as C.

```C
for (int i = 0; i < 10; i = i + 1) {
  // do something...
}
```
```C
while (a == b) {
  // do something...
}
```

The `break` keyword will end the current loop immediately.

```C
for (int i = 0; i < 10; i = i + 1) {
  if (i == 5) {
    break; // exit the loop body
  }
  
  // do something with i...
}
```

The `continue` keyword will skip to the next loop iteration.

```C
for (int i = 0; i < 10; i = i + 1) {
  if (i == 5) {
    continue; // the rest of the loop body is skipped, and the loop starts again after incrementing i
  }
  
  // do something with i...
}
```

## Functions

Functions in ERA-C follow mostly the same syntax as C.

```C
// declaring a function
void my_function(int a, float b) {
   // do something...
}

// calling the function
my_function(1, 2.0);
```

The `return` keyword returns a value from a function.

```C
int add(int a, int b) {
   return a + b;
}
```

!!! info
	Unlike C, a function that lists no arguments is a function that accepts no arguments.
	
	The C style `void my_function(void)` will not compile in ERA-C.

### Vararg Functions

Functions that accept a variable number of arguments are called "vararg" or "variadic" functions.

The special vararg type (`...`) is used to indicate that a function is variadic.

The vararg type must come after all other non-optional arguments.

```C
// declaring a variadic function
void my_function(int a, float b, ...) {
  // do something...
}

// calling the function
my_function(1, 2.0, 3, 4, 5);
```

To access vararg arguments, use the `vargc()` and `vargv()` API functions.

`vargc()` takes no arguments and returns the remaining number of bytes available in the varargs list.

```C
if (vargc() >= 4) {
  // there are at least 4 bytes of vararg data left.
}
```

`vargv()` returns a `void*` pointing to the current vararg argument, and accepts a size in bytes as an argument.

The size given to `vargv()` is the offset to give the vararg pointer in order to move past the current argument.

It is recommended to use `sizeof()` to get argument size.

```C
int sum(...) {
  int result = 0;
  while (vargc() >= sizeof(int)) {
    int* arg_pointer = (int*) vargv(sizeof(int));
    result = result + *arg_pointer;
  }
  return result;
}

// calling sum()
int value = sum(1, 2, 3, 4, 5); // value = 15
```

The above snippet is an example of a simple sum function that adds a variable number of integers.

## Hook Functions

ERA-3D recognizes special "hook" functions declared in a ERA-C program and will call them at certain times.

At least one hook function must be declared in order for a cart to run.

### `init`

if a function is declared with the signature `void init()`, it will be called once when a cart is ran.

Use this function to initialize game state.

```C
void init() {
  // initialize state here...
}
```

### `update`

if a function is declared with the signature `void update(float delta_time)`, it will be called once every frame.

Use this function to update game state. (check inputs, move objects, etc.)

`delta_time` will be passed to the function automatically, and will contain the amount of time (in seconds) since the last frame.

```C
void update(float delta_time) {
  // update state here...
}
```

!!! info
	The `delta_time` argument for `update()` can be given any other name, but it must be a `float`.

### `draw`

if a function is declared with the signature `void draw()`, it will be called once every frame after the call to `update()`.

Use this function to configure rendering settings and to render graphics to the screen.

```C
void draw() {
  // render graphics here...
}
```

## Built-in Constants

The ERA-C compiler has several built-in constants for use with various functions. The following table lists their names and values:

Name | Value
-|-
`true` | `1`
`false` | `0`
`null` | `0xFFFFFFFF`
`BLEND_ALPHA` | `0`
`BLEND_ADD` | `1`
`BLEND_MULTIPLY` | `2`
`BLEND_ADD_ALT` | `3`
`BLEND_SUBTRACT` | `4`
`BLEND_PREMULTIPLY` | `5`
`BLEND_CUSTOM` | `6`
`BLEND_CUSTOM_EX` | `7`
`BTN_UP` | `0`
`BTN_DOWN` | `1`
`BTN_LEFT` | `2`
`BTN_RIGHT` | `3`
`BTN_TRIANGLE` | `4`
`BTN_CROSS` | `5`
`BTN_SQUARE` | `6`
`BTN_CIRCLE` | `7`
`BTN_L1` | `8`
`BTN_L2` | `9`
`BTN_R1` | `10`
`BTN_R2` | `11`
`BTN_SELECT` | `12`
`BTN_START` | `13`
`BTN_MOUSE_LEFT` | `0`
`BTN_MOUSE_RIGHT` | `1`
`BTN_MOUSE_MIDDLE` | `2`
`CAM_PERSPECTIVE` | `0`
`CAM_ORTHOGRAPHIC` | `1`
`CLEAR_NONE` | `0`
`CLEAR_COLOR` | `0b100`
`CLEAR_DEPTH` | `0b010`
`CLEAR_STENCIL` | `0b001`
`CLEAR_ALL` | `0b111`
`COLOR_NONE` | `0`
`COLOR_R` | `0b1000`
`COLOR_G` | `0b0100`
`COLOR_B` | `0b0010`
`COLOR_A` | `0b0001`
`COLOR_ALL` | `0b1111`
`CULL_BACK` | `0`
`CULL_FRONT` | `1`
`CULL_NONE` | `2`
`EQ_ADD` | `0`
`EQ_SUBTRACT` | `1`
`EQ_SUBTRACT_REVERSE` | `2`
`EQ_MIN` | `3`
`EQ_MAX` | `4`
`FACE_FRONT` | `0`
`FACE_BACK` | `1`
`FACE_BOTH` | `2`
`FACTOR_ZERO` | `0`
`FACTOR_ONE` | `1`
`FACTOR_SRC_RGB` | `2`
`FACTOR_ONE_MINUS_SRC_RGB` | `3`
`FACTOR_DST_RGB` | `4`
`FACTOR_ONE_MINUS_DST_RGB` | `5`
`FACTOR_SRC_ALPHA` | `6`
`FACTOR_ONE_MINUS_SRC_ALPHA` | `7`
`FACTOR_DST_ALPHA` | `8`
`FACTOR_ONE_MINUS_DST_ALPHA` | `9`
`FACTOR_CONSTANT_RGB` | `10`
`FACTOR_ONE_MINUS_CONSTANT_RGB` | `11`
`FACTOR_CONSTANT_ALPHA` | `12`
`FACTOR_ONE_MINUS_CONSTANT_ALPHA` | `13`
`FACTOR_SRC_ALPHA_SATURATE` | `14`
`FONT_WIDTH` | `6`
`FONT_HEIGHT` | `9`
`FUNC_LESS` | `0`
`FUNC_LEQUAL` | `1`
`FUNC_GREATER` | `2`
`FUNC_GEQUAL` | `3`
`FUNC_EQUAL` | `4`
`FUNC_NOTEQUAL` | `5`
`FUNC_ALWAYS` | `6`
`FUNC_NEVER` | `7`
`LIGHT_POINT` | `0`
`LIGHT_DIRECTIONAL` | `1`
`LOOP_OFF` | `0`
`LOOP_FORWARD` | `1`
`LOOP_PINGPONG` | `2`
`LOOP_RANGE` | `3`
`MAT_PROJECTION` | `0`
`MAT_MODELVIEW` | `1`
`MEMORY_HEAP` | `0x00000000`
`MEMORY_TEXMEM` | `0x00800000`
`MEMORY_OBJMEM` | `0x00C00000`
`MEMORY_AOBMEM` | `0x00F60000`
`MEMORY_SYSMEM` | `0x00F62000`
`MEMORY_OBJMAP` | `0x00F62054`
`MEMORY_WAVMAP` | `0x00F63854`
`MEMORY_WAVMEM` | `0x01000000`
`MEMORY_SEQMEM` | `0x01700000`
`MEMORY_TEXBANK0` | `0x01800000`
`MEMORY_TEXBANK1` | `0x01C00000`
`MEMORY_TEXBANK2` | `0x02000000`
`MEMORY_TEXBANK3` | `0x02400000`
`MEMORY_OBJBANK0` | `0x02800000`
`MEMORY_OBJBANK1` | `0x02B60000`
`MEMORY_OBJBANK2` | `0x02EC0000`
`MEMORY_OBJBANK3` | `0x03220000`
`MEMORY_OMPBANK0` | `0x03580000`
`MEMORY_OMPBANK1` | `0x03581800`
`MEMORY_OMPBANK2` | `0x03583000`
`MEMORY_OMPBANK3` | `0x03584800`
`MEMORY_WMPBANK0` | `0x036C0000`
`MEMORY_WMPBANK1` | `0x036C2000`
`MEMORY_WAVBANK0` | `0x03800000`
`MEMORY_WAVBANK1` | `0x03F00000`
`MEMORY_SEQBANK0` | `0x04600000`
`MEMORY_SEQBANK1` | `0x04640000`
`MEMORY_SEQBANK2` | `0x04680000`
`MEMORY_SEQBANK3` | `0x046C0000`
`MEMORY_SEQBANK4` | `0x04700000`
`MEMORY_SEQBANK5` | `0x04740000`
`MEMORY_SEQBANK6` | `0x04780000`
`MEMORY_SEQBANK7` | `0x047C0000`
`MEMORY_ROM` | `0x04800000`
`MEMORY_MEMCARD` | `0x05800000`
`MESH_LINES` | `0`
`MESH_TRIANGLES` | `1`
`MESH_QUADS` | `2`
`POLY_POINT` | `0`
`POLY_LINE` | `1`
`POLY_FILL` | `2`
`SCREEN_WIDTH` | `640`
`SCREEN_HEIGHT` | `360`
`STENCIL_KEEP` | `0`
`STENCIL_REPLACE` | `1`
`STENCIL_INC` | `2`
`STENCIL_INC_WRAP` | `3`
`STENCIL_DEC` | `4`
`STENCIL_DEC_WRAP` | `5`
`STENCIL_ZERO` | `6`
`STENCIL_INVERT` | `7`
`TEXTURE_WRAP` | `0`
`TEXTURE_CLAMP` | `1`
`TEXTURE_NONE` | `2`

## Built-in Structs

ERA-C has multiple built-in struct types for representing various objects. Unlike the vector and `string` types, which behave like structs in certain situations, these built-in structs do not have any custom functionality built into the compiler.

### `matrix`

The `matrix` struct is a 4x4 matrix used for storing transformations like translation, rotation, and scale.

TODO: explain member ordering

```C
struct matrix {
  float scale_x;  float shear_yx; float shear_zx; float translate_x; // first row
  float shear_xy; float scale_y;  float shear_zy; float translate_y; // second row
  float shear_xz; float shear_yz; float scale_z;  float translate_z; // third row
  float wx;       float wy;       float wz;       float ww;          // fourth row
};
```

### `vertex`

The `vertex` struct contains 3D vertex data according to the order that vertex data is stored in OBJMEM and OBJBANKs.

Thus, OBJMEM and OBJBANKs can be treated as arrays of `vertex` structs.

```C
struct vertex {
  vec3 position;
  vec3 normal;
  vec2 uv;
  int color;
};
```

### `cam2d`

In SYSMEM, there are 4 memory-mapped 2D cameras that can be used for configuring the view.

To get a pointer to a 2D camera, use the `getCam2D()` function.

```C
cam2d* cam = getCam2D(0); // get a pointer to 2D camera 0
```

To configure the view to a built-in 2D camera, use the `camera2D()` function.

```C
camera2D(0); // use 2D camera 0
```

!!! info
	When `camera2D()` is called, depth testing is automatically disabled.

The `cam2d` struct has the following definition:

```C
struct cam2d {
  vec2 offset;
  vec2 target;
  float rotation;
  float zoom;
};
```

### `cam3d`

In SYSMEM, there are 4 memory-mapped 3D cameras that can be used for configuring the view.

To get a pointer to a 3D camera, use the `getCam3D()` function.

```C
cam3d* cam = getCam3D(0); // get a pointer to 3D camera 0
```

To configure the view to a built-in 3D camera, use the `camera3D()` function.

```C
camera3D(0); // use 3D camera 0
```

!!! info
	When `camera3D()` is called, depth testing is automatically enabled.

The `cam3d` struct has the following definition:

```C
struct cam3d {
  vec3 position;
  vec3 target;
  vec3 up;
  float fov;
  int projection;
};
```

### `light`

In SYSMEM, there are 8 memory-mapped lights that are used when lighting is enabled.

To get a pointer to a light, use the `getLight()` function.

```C
light* light0 = getLight(0); // get a pointer to light 0
```

The `light` struct has the following definition:

```C
struct light {
  int enabled;
  int type;
  float radius;
  int color;
  vec3 position;
  vec3 direction;
};
```

### Collision Objects

!!! warning
	The physics system is very experimental and subject to change.
	
	Currently, collision detection is only implemented for `colaabb` vs `colaabb`.

ERA-3D has built-in API functions for 3D collision detection. These API functions accept pointers to collision object structs to know what objects to test.

Each collision object struct contains a `type` integer member that must be set to the correct ID value in order for the collision functions to properly identify them.

The compiler will automatically initialize the `type` member of a collision object struct to the correct ID when the struct is created, and does not need to be explicitly set by the user.

```C
colaabb hitbox = colaabb(vec3(), 1.0, 1.0, 1.0); // the value for type is excluded and implicitly set
```

The following table lists all collision object IDs:

ID | Collision Object Struct
-|-
`0` | `colpoint`
`1` | `colaabb`
`2` | `colsphere`
`3` | `colcylinder`
`4` | `coltriangle`

To check for collisions using these structs, use the [`collide()`](api-reference.md#collide) API function.

```C
colaabb box1 = colaabb(vec3(), 1.0, 0.5, 1.0);
colaabb box2 = colaabb(vec3(), 0.5, 1.0, 0.5);

if (collide(&box1, &box2)) {
  // box1 and box2 are colliding!
  // handle collision here...
}
```

#### `colpoint`

A `colpoint` represents a single point in 3D space.

```C
struct colpoint {
  int type;
  vec3 position;
};
```

#### `colaabb`

A `colaabb` represents an Axis Aligned Bounding Box, a 3D box that cannot be rotated.

```C
struct colaabb {
  int type;
  vec3 position;
  float width;
  float height;
  float depth;
};
```

#### `colsphere`

A `colsphere` represents a 3D sphere.

```C
struct colsphere {
  int type;
  vec3 position;
  float radius;
};
```

#### `colcylinder`

A `colcylinder` represents a 3D cylinder.

```C
struct colcylinder {
  int type;
  vec3 position;
  float height;
  float radius;
};
```

#### `coltriangle`

A `coltriangle` represents a 3D triangle.

```C
struct coltriangle {
  int type;
  vec3 point1;
  vec3 point2;
  vec3 point3;
};
```

## Differences From C

The following table lists the main differences between C and ERA-C semantics.

C | ERA-C
-|-
Multi-line comments cannot be nested | Multi-line comments can be nested
Multiple integer and floating-point types of various sizes | Only `int` and `float`, both 32-bit (4 bytes)
Leading zeros indicate octal format | Leading zeros do not indicate octal format, and are ignored
Pointer <-> Integer conversion is not generally recommended | Pointer <-> `int` is 100% legal
`NULL` | `null`
`NULL` == 0 | `null` == `0xFFFFFFFF`
`void foo()` accepts any number of arguments | `void foo()` does not accept any arguments
`void foo(void)` does not accept any arguments | `void foo(void)` is a compile error
`main()` is the program starting point | Hook functions `init()`, `update()`, and `draw()` are called periodically
