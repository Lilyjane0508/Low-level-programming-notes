# Memory Layout of a C Program

## Overview

A running program is divided into different memory segments.

---

## Memory Layout

```
High Address
-------------
Stack
-------------
Heap
-------------
Data (initialized + uninitialized)
-------------
Text (code)
Low Address
```

---

## Text Segment

- stores program code
- read-only

Example:

```c
int main() {
    return 0;
}
```

---

## Data Segment

Stores global and static variables.

### Initialized data

```c
int x = 10;
```

### Uninitialized data (BSS)

```c
int y;
```

---

## Heap

- used for dynamic memory
- controlled by programmer

Example:

```c
int *p = malloc(sizeof(int));
```

---

## Stack

- stores function calls
- stores local variables
- managed automatically

Example:

```c
void foo() {
    int x = 10;
}
```

---

## Example

```c
#include <stdio.h>
#include <stdlib.h>

int global = 10;

int main() {

    int local = 5;
    int *heap_var = malloc(sizeof(int));

    printf("global: %p\n", &global);
    printf("local: %p\n", &local);
    printf("heap: %p\n", heap_var);

}
```

---

## Key Ideas

- stack grows downward
- heap grows upward
- they can collide if memory is exhausted

---

## Why This Matters

Understanding memory layout is important for:

- debugging
- performance
- low-level programming
- binary exploitation
