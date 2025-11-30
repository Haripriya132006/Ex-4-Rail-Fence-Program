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

void encryptRailFence(char *msg, int rails) {
    int len = strlen(msg), dir = 1, row = 0;
    char rail[rails][len];

    memset(rail, 0, sizeof(rail));    // fill with 0

    for (int i = 0; i < len; i++) {
        rail[row][i] = msg[i];
        row += dir;

        if (row == rails - 1 || row == 0)
            dir = -dir;
    }

    printf("Encrypted: ");
    for (int r = 0; r < rails; r++)
        for (int c = 0; c < len; c++)
            if (rail[r][c])
                printf("%c", rail[r][c]);
    printf("\n");
}

int main() {
    char msg[100];
    int rails;

    printf("Enter message: ");
    scanf("%s", msg);

    printf("Rails: ");
    scanf("%d", &rails);

    encryptRailFence(msg, rails);
    return 0;
}

```
# OUTPUT
<img width="1557" height="514" alt="image" src="https://github.com/user-attachments/assets/846122ee-a257-4f53-b0f4-196dc3f98239" />

# RESULT
