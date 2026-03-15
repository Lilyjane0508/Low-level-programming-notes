## Overview

Pointers are variables that store memory addresses.  
C provides several operators to work with pointers:

- Address operator `&`
- Dereference operator `*`
- Pointer arithmetic (`+` and `-`)

---

# Address Operator (&)

The `&` operator returns the memory address of a variable.

## Example

```c
#include <stdio.h>

int main() {
    int x = 10;

    printf("%p\n", &x);

    return 0;
}
```

### Explanation

```
x = 10
&x = memory address of x
```

Example output (address will vary):

```
0x7ffeefbff5ac
```

---

# Pointer Declaration

A pointer is declared using `*`.

```c
int *p;
```

This means:

```
p is a pointer to an integer
```

---

# Dereference Operator (*)

The `*` operator accesses the value stored at the memory address.

## Example

```c
#include <stdio.h>

int main() {
    int x = 10;
    int *p = &x;

    printf("%d\n", *p);

    return 0;
}
```

### Explanation

```
x = 10
p = address of x
*p = value stored at that address
```

Output:

```
10
```

---

# Pointer Arithmetic

Pointers can move through memory using `+` and `-`.

Example:

```c
#include <stdio.h>

int main() {

    int arr[3] = {10,20,30};

    int *p = arr;

    printf("%d\n", *p);
    printf("%d\n", *(p+1));
    printf("%d\n", *(p+2));

    return 0;
}
```

Output:

```
10
20
30
```

### Explanation

```
p      → arr[0]
p + 1  → arr[1]
p + 2  → arr[2]
```

Pointer arithmetic moves by the size of the data type.

Example:

```
int pointer + 1 -> moves 4 bytes (usually)
```

---

# Memory Visualization

Example:

```c
int x = 10;
int *p = &x;
```

Memory layout:

```
Variable     Address      Value
-------------------------------
x            0x100        10
p            0x200        0x100
```

```
p   → address of x
*p  → value stored at that address
```

---

# Summary

| Operator | Description |
|--------|-------------|
| `&` | returns the address of a variable |
| `*` | dereferences a pointer |
| `+` `-` | pointer arithmetic |

Pointers are fundamental for:

- memory manipulation
- arrays
- dynamic memory
- low-level programming
