# Implementation of Caesar Cipher Algorithm in C

# Check out the Practical Video demonstration in Bangla : https://youtu.be/UTzdD5VXIzs

# Caesar Cipher Implementation in C

This C program demonstrates a simple implementation of the Caesar Cipher algorithm, a substitution cipher that shifts letters by a fixed number of positions.

## Prerequisites

Before running the code, ensure you have a basic understanding of:

1.  **Basic C Syntax:** Familiarity with variables, data types, operators, and control flow.
2.  **Functions:** Ability to define and call functions in C.
3.  **Pointers:** Understanding how pointers work in C for string manipulation.

## Key Features

* **Encryption and Decryption:** Encrypts and decrypts text using a user-defined shift value.
* **Case Handling:** Handles both uppercase and lowercase letters correctly.
* **Non-Alphabetic Preservation:** Preserves non-alphabetic characters in the input text.
* **Readability:** Clear and concise code designed for easy understanding.

## How It Works

1.  **Input:** The program takes input text and a shift value.
2.  **Character Processing:** For each character in the input text:
    * If it's an uppercase letter, it's shifted within the uppercase range (A-Z).
    * If it's a lowercase letter, it's shifted within the lowercase range (a-z).
    * Non-alphabetic characters remain unchanged.
3.  **Output:** The shifted characters form the encrypted or decrypted output.

## Example

* **Input Text:** `Hello, World!`
* **Shift Value:** `3`
* **Encrypted Output:** `Khoor, Zruog!`


## Code Snippet

```c
#include <stdio.h>
#include <string.h>
#include <ctype.h>

void caesarCipher(char *text, int shift, int encrypt) {
    int length = strlen(text);
    for (int i = 0; i < length; i++) {
        if (isalpha(text[i])) {
            char base = isupper(text[i]) ? 'A' : 'a';
            if(encrypt){
                text[i] = (text[i] - base + shift) % 26 + base;
            } else {
                text[i] = (text[i] - base - shift + 26) % 26 + base;
            }
        }
    }
}

int main() {
    char text[1000];
    int shift;
    int encrypt;

    printf("Enter the text: ");
    fgets(text, sizeof(text), stdin);

    printf("Enter the shift value: ");
    scanf("%d", &shift);

    printf("Encrypt (1) or Decrypt (0)? ");
    scanf("%d", &encrypt);

    text[strcspn(text, "\n")] = 0;

    caesarCipher(text, shift, encrypt);

    if(encrypt){
        printf("Encrypted text: %s\n", text);
    } else {
        printf("Decrypted text: %s\n", text);
    }

    return 0;
}
