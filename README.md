# Ex. No : 1

# IMPLEMENTATION OF SYMBOL TABLE

# Register Number : 212224110061

# Date : 25-08-2025

# AIM:

To write a C program to implement a symbol table.

# ALGORITHM:

1. Start the program.
2. Get the input from the user with the terminating symbol ‘$’.
3. Allocate memory for the variable by dynamic memory allocation function.
4. If the next character of the symbol is an operator then only the memory is allocated.
5. While reading, the input symbol is inserted into symbol table along with its memory address.
6. The steps are repeated till ‘$’ is reached.
7. To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8. Stop the program.

# PROGRAM:

```
// Ex 1 - Implementation of Symbol Table

#include <stdio.h>
#include <stdlib.h>   // for malloc, free
#include <ctype.h>    // for isalpha
#include <string.h>

#define MAX_EXPRESSION_SIZE 100

int main() {
    int i = 0, j = 0, x = 0, n, flag = 0;
    void *add[20];       // store addresses of identifiers
    char b[MAX_EXPRESSION_SIZE], d[20]; // b = expression, d = identifiers
    char c, srch;

    printf("Enter the Expression terminated by $: ");
    while ((c = getchar()) != '$' && i < MAX_EXPRESSION_SIZE - 1) {
        b[i++] = c;
    }
    b[i] = '\0'; // Null terminate
    n = i - 1;

    printf("\nGiven Expression: %s\n", b);

    printf("\nSymbol Table\n");
    printf("Symbol\tAddress\t\tType\n");

    for (j = 0; j <= n; j++) {
        c = b[j];
        if (isalpha((unsigned char)c)) { // check if identifier
            if (j == n || b[j + 1] == '+' || b[j + 1] == '-' || 
                b[j + 1] == '*' || b[j + 1] == '=' || b[j + 1] == '/') {
                
                void *p = malloc(sizeof(char));
                if (p == NULL) {
                    printf("Memory allocation failed\n");
                    return 1;
                }
                add[x] = p;
                d[x] = c;
                printf("%c\t%p\tidentifier\n", c, p);
                x++;
            }
        }
    }

    // clear input buffer
    while ((c = getchar()) != '\n' && c != EOF);

    printf("\nThe symbol to be searched: ");
    srch = getchar();

    for (i = 0; i < x; i++) {
        if (srch == d[i]) {
            printf("Symbol Found\n");
            printf("%c @ address %p\n", srch, add[i]);
            flag = 1;
            break;
        }
    }

    if (flag == 0) {
        printf("Symbol Not Found\n");
    }

    // Free allocated memory
    for (i = 0; i < x; i++) {
        free(add[i]);
    }

    return 0;
}
```

# OUTPUT:

<img width="1133" height="1023" alt="image" src="https://github.com/user-attachments/assets/b3951c86-46e5-4425-aa1e-b5f6d31e5b7b" />


# RESULT:

The program to implement a symbol table is executed and the output is verified.
