# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h>
#include <string.h>

int main()
{
    int i, j, len, rails, row, dir;
    char str[1000];
    int code[100][1000];

    printf("Enter a Secret Message\n");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';

    len = strlen(str);

    printf("Enter number of rails\n");
    scanf("%d", &rails);

    if (rails < 2 || rails > 100)
    {
        printf("Invalid number of rails\n");
        return 1;
    }

    for (i = 0; i < rails; i++)
    {
        for (j = 0; j < len; j++)
        {
            code[i][j] = 0;
        }
    }

    row = 0;
    dir = 1;

    for (j = 0; j < len; j++)
    {
        code[row][j] = (int)str[j];

        if (row == 0)
            dir = 1;
        else if (row == rails - 1)
            dir = -1;

        row += dir;
    }

    printf("Cipher Text:\n");

    for (i = 0; i < rails; i++)
    {
        for (j = 0; j < len; j++)
        {
            if (code[i][j] != 0)
                printf("%c", code[i][j]);
        }
    }

    printf("\n");
    return 0;
}
```
# OUTPUT
<img width="1512" height="918" alt="image" src="https://github.com/user-attachments/assets/c2bf78e5-2113-49c2-95b0-0edd2e1a5f60" />

# RESULT
the program completed successfully
