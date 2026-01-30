# HILL CIPHER
HILL CIPHER
EX. NO: 3 AIM:
 

IMPLEMENTATION OF HILL CIPHER
 
## To write a C program to implement the hill cipher substitution techniques.

## DESCRIPTION:

Each letter is represented by a number modulo 26. Often the simple scheme A = 0, B
= 1... Z = 25, is used, but this is not an essential feature of the cipher. To encrypt a message, each block of n letters is  multiplied by an invertible n × n matrix, against modulus 26. To
decrypt the message, each block is multiplied by the inverse of the m trix used for
 
encryption. The matrix used
 
for encryption is the cipher key, and it sho
 
ld be chosen
 
randomly from the set of invertible n × n matrices (modulo 26).


## ALGORITHM:

STEP-1: Read the plain text and key from the user. STEP-2: Split the plain text into groups of length three. STEP-3: Arrange the keyword in a 3*3 matrix.

STEP-4: Multiply the two matrices to obtain the cipher text of length three.

STEP-5: Combine all these groups to get the complete cipher text.


## PROGRAM 
```
#include <stdio.h>
 #include <string.h>
 #include <ctype.h>
 #define SIZE 3  


void multiplyMatrix(int key[SIZE][SIZE], int text[SIZE], int result[SIZE]) {
for (int i = 0; i < SIZE; i++) {
    result[i] = 0;
    for (int j = 0; j < SIZE; j++) {
        result[i] += key[i][j] * text[j];
    }
    result[i] = result[i] % 26;
}
}

int main() {

char plainText[100];
int key[SIZE][SIZE];
char cipherText[100] = "";
int len;


printf("Enter the plain text: ");
fgets(plainText, sizeof(plainText), stdin);
plainText[strcspn(plainText, "\n")] = '\0';


for (int i = 0; plainText[i]; i++) {
    if (isalpha(plainText[i]))
        plainText[i] = toupper(plainText[i]);
}


char temp[100];
int idx = 0;
for (int i = 0; plainText[i]; i++) {
    if (isalpha(plainText[i])) {
        temp[idx++] = plainText[i];
    }
}
temp[idx] = '\0';
strcpy(plainText, temp);


len = strlen(plainText);
while (len % 3 != 0) {
    plainText[len++] = 'X';
}
plainText[len] = '\0';


printf("Enter the 3x3 key matrix (row by row):\n");
for (int i = 0; i < SIZE; i++) {
    for (int j = 0; j < SIZE; j++) {
        scanf("%d", &key[i][j]);
    }
}


for (int i = 0; i < len; i += 3) {
    int textVec[SIZE], result[SIZE];


    for (int j = 0; j < SIZE; j++) {
        textVec[j] = plainText[i + j] - 'A';
    }


    multiplyMatrix(key, textVec, result);

 
    for (int j = 0; j < SIZE; j++) {
        char c = result[j] + 'A';
        strncat(cipherText, &c, 1);
    }
}


printf("Cipher Text: %s\n", cipherText);

    return 0;
}

```
## OUTPUT

<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/8a0afa70-2d2a-469d-b5ed-c3d5a5cc6450" />


## RESULT

Thus the implementation of Hill Cipher text is executed successfully.
