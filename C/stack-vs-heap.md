# Stack vs Heap in C

## Overview

C programs use two main types of memory:

- Stack
- Heap

---

## Stack

### Characteristics

- automatic memory management
- fast
- limited size
- stores local variables

Example:

```c
int main() {
    int x = 10;
}
```

---

## Heap

### Characteristics

- manual memory management
- slower than stack
- large size
- used for dynamic memory

Example:

```c
int *p = malloc(sizeof(int));
```

---

## Key Differences

| Feature | Stack | Heap |
|--------|------|------|
| Allocation | automatic | manual |
| Speed | fast | slower |
| Size | small | large |
| Lifetime | function scope | until freed |

---

## Example

```c
#include <stdio.h>
#include <stdlib.h>

int main() {

    int x = 10;               // stack
    int *p = malloc(sizeof(int)); // heap

    *p = 20;

    printf("%d\n", x);
    printf("%d\n", *p);

    free(p);

}
```

---

## Common Errors

### Stack overflow

Too many recursive calls:

```c
void f() {
    f();
}
```

---

### Memory leak

```c
int *p = malloc(sizeof(int));
```

without:

```c
free(p);
```

---

## Summary

- stack → automatic, fast, limited
- heap → manual, flexible, larger
