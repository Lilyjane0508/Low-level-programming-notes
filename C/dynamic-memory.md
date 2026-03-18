# Dynamic Memory in C

## Overview

Dynamic memory allocation allows a program to allocate memory at runtime.

This memory is stored in the **heap**.

---

## Why Use Dynamic Memory?

- size is not known at compile time
- flexible memory usage
- required for data structures (linked list, tree, etc.)

---

## Main Functions

C provides 4 main functions:

### malloc

```c
void *malloc(size_t size);
```

Allocates memory but does NOT initialize it.

Example:

```c
int *p = malloc(sizeof(int));
```

---

### calloc

```c
void *calloc(size_t n, size_t size);
```

Allocates memory and initializes it to zero.

Example:

```c
int *p = calloc(5, sizeof(int));
```

---

### realloc

```c
void *realloc(void *ptr, size_t new_size);
```

Resizes previously allocated memory.

Example:

```c
p = realloc(p, 10 * sizeof(int));
```

---

### free

```c
void free(void *ptr);
```

Frees allocated memory.

Example:

```c
free(p);
```

---

## Example

```c
#include <stdio.h>
#include <stdlib.h>

int main() {

    int *arr = malloc(3 * sizeof(int));

    arr[0] = 1;
    arr[1] = 2;
    arr[2] = 3;

    for(int i = 0; i < 3; i++){
        printf("%d\n", arr[i]);
    }

    free(arr);

}
```

---

## Common Mistakes

### Memory leak

```c
int *p = malloc(sizeof(int));
```

Forgetting:

```c
free(p);
```

---

### Dangling pointer

```c
free(p);
*p = 10; // ERROR
```

---

### Double free

```c
free(p);
free(p); // ERROR
```

---

## Best Practices

- always free allocated memory
- set pointer to NULL after free

```c
free(p);
p = NULL;
```

---

## Summary

| Function | Purpose |
|--------|--------|
| malloc | allocate memory |
| calloc | allocate + initialize |
| realloc | resize memory |
| free | release memory |
