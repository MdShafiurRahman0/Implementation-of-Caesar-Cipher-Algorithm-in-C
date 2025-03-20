# Implementation of Caesar Cipher Algorithm in C

# Presentation Slide : [1078_Shafiur_ISS_Presentation_Slide.pdf](https://github.com/user-attachments/files/19372839/1078_Shafiur_ISS_Presentation_Slide.pdf)

![image](https://github.com/user-attachments/assets/672a1289-8711-4557-960a-2da6ee488dc6)




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

void caesar_encrypt(char *message, int key, char *result) {
    int i = 0;
    while (message[i] != '\0') {
        char ch = message[i];

        // Encrypt uppercase letters
        if (ch >= 'A' && ch <= 'Z') {
            result[i] = ((ch - 'A' + key) % 26) + 'A';
        }
        // Encrypt lowercase letters
        else if (ch >= 'a' && ch <= 'z') {
            result[i] = ((ch - 'a' + key) % 26) + 'a';
        }
        // Keep non-alphabetic characters unchanged
        else {
            result[i] = ch;
        }
        i++;
    }
    result[i] = '\0'; // Add null terminator
}

void caesar_decrypt(char *encrypted, int key, char *decrypted) {
    int i = 0;
    while (encrypted[i] != '\0') {
        char ch = encrypted[i];

        // Decrypt uppercase letters
        if (ch >= 'A' && ch <= 'Z') {
            decrypted[i] = ((ch - 'A' - key + 26) % 26) + 'A';
        }
        // Decrypt lowercase letters
        else if (ch >= 'a' && ch <= 'z') {
            decrypted[i] = ((ch - 'a' - key + 26) % 26) + 'a';
        }
        // Keep non-alphabetic characters unchanged
        else {
            decrypted[i] = ch;
        }
        i++;
    }
    decrypted[i] = '\0'; // Add null terminator
}

int main() {
    char message[100];
    int key;
    char encrypted[100];
    char decrypted[100];

    printf("Enter the message to encrypt/decrypt: ");
    fgets(message, sizeof(message), stdin);
    message[strcspn(message, "\n")] = 0; // Remove trailing newline

    printf("Enter the key (shift value): ");
    scanf("%d", &key);

    caesar_encrypt(message, key, encrypted);
    printf("Encrypted message: %s\n", encrypted);

    caesar_decrypt(encrypted, key, decrypted);
    printf("Decrypted message: %s\n", decrypted);

    return 0;
}
