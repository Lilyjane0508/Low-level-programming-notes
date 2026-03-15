## What is a Buffer?

A buffer is a block of memory used to store data.

Example:

```c
char buffer[10];
```

This buffer can store **10 characters**.

---

## What is a Buffer Overflow?

A buffer overflow happens when a program writes **more data than the buffer can hold**.

Example:

```c
#include <stdio.h>
#include <string.h>

int main() {

    char buffer[10];

    strcpy(buffer, "this string is too long");

}
```

Here:

```
buffer size = 10
input size  > 10
```

The program writes beyond the buffer.

---

## Why is This Dangerous?

Overflowing a buffer may overwrite:

- other variables
- the stack frame
- the return address

Example stack layout:

```
High Address
-------------
Return Address
-------------
Saved Frame Pointer
-------------
buffer[10]
Low Address
```

If the buffer overflows, it may overwrite the **return address**.

---

## Simple Example

```c
#include <stdio.h>

void vulnerable() {

    char buffer[8];

    gets(buffer);

}

int main() {
    vulnerable();
}
```

The function `gets()` does **not check the buffer size**.

This makes the program vulnerable to overflow.

---

## Why Attackers Use This

If an attacker overwrites the **return address**, they can:

- redirect program execution
- execute malicious code
- gain system access

---

## How Modern Systems Defend Against This

Modern systems use protections like:

- Stack Canaries
- ASLR
- NX bit

But understanding buffer overflows is still essential for:

- exploit development
- reverse engineering
- security research
