## Overview

When a function is called, the program uses a **stack** to store information
about the function execution.

This area of memory is called the **call stack**.

Each function call creates a **stack frame**.

---

## Stack Frame

A stack frame usually contains:

- function parameters
- local variables
- return address
- saved registers

Example code:

```c
#include <stdio.h>

void foo() {
    int x = 10;
    printf("%d\n", x);
}

int main() {
    foo();
}
```

---

## What Happens When a Function is Called

When `foo()` is called:

1. Arguments are pushed onto the stack
2. The return address is pushed
3. A new stack frame is created
4. Local variables are allocated

Stack layout example:

```
High Address
------------------
local variables
------------------
saved registers
------------------
return address
------------------
function arguments
------------------
Low Address
```

---

## Stack Growth

In most systems:

```
Stack grows downward
```

Example:

```
High Address
-------------
main()
-------------
foo()
-------------
bar()
Low Address
```

Each function call pushes a new frame onto the stack.

---

## Returning from a Function

When a function finishes:

1. Local variables are destroyed
2. The return address is popped
3. Execution returns to the caller

Example:

```
main() calls foo()
foo() returns
execution continues in main()
```

---

## Why the Call Stack Matters

Understanding the call stack is important for:

- debugging
- performance analysis
- low-level programming
- binary exploitation
