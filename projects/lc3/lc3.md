---
layout: post
title: /lc3-assembly
permalink: /projects/lc3/
categories: projects
---
# Project Title: LC3 Encryption Decryption Module
# Project Description
This LC-3 assembly program is a Vigenere and Ceaser cipher implementation. It prompts the user to input a plain text message to be encrypted or decrypted, and then asks whether the user wants to encrypt or decrypt the message. The input message can be up to 10 characters in length.

If the user selects to encrypt the message, the program prompts the user to enter a key that will be used to encrypt the plain text message using the Vigenere cipher algorithm. If the user selects to decrypt the message, the program simply outputs an error message, since the decryption algorithm has not been implemented in this code.

After the user inputs a message and selects to encrypt it, the program proceeds to encrypt the message using the Vigenere cipher algorithm. The Vigenere cipher is a type of polyalphabetic substitution cipher where each letter of the plaintext is shifted by a certain number of places down the alphabet using a keyword. The keyword is repeated as many times as necessary to match the length of the plaintext.

The program uses the key entered by the user to generate a keystream that will be used to encrypt the message. It then encrypts the message by XORing each character of the plaintext message with a corresponding character of the keystream. The encrypted message is stored in memory starting at location x7000.

Overall, this program prompts the user to input a plain text message, asks whether the user wants to encrypt or decrypt the message, and if the user selects to encrypt the message, encrypts it using the Vigenere cipher algorithm and outputs the encrypted message.

# Code Snippet for Vigenere Cipher
`+-------------------------------------------------------------------------------------+`
```java
; *** Step 4 ***
; Encryption
;
; Vigenere cipher
;
Vigenere
    LEA R0, keySt
    LDR R1, R0, 1      ; load x1 into K
    ST  R1, k
    STI R1, kst
    AND R4, R4, 0      ; clear R4
    ADD R4, R4, 10     ; counter for string
    ; check end of string
    LEA R0, edToSt
xloop
    LDR R6, R0, 0      ; 1st char
    LDI R1, kst         ; x1 char
    LD  R3, 0
    LD  R3, negZero
    ADD R3, R3, R1
    BRz Ceaser
    LD  R3, 0
    LD  R3, negEnt      ; load -10 <enter>
    ADD R3, R3, R6      ; CHECK FOR <enter>
    BRz endString
    JSR xor             ; perform XOR on 2 numbers
Estore
    STR R3, R0, 0      ; store in edToSt for now
    ADD R0, R0, 1      ; increment
    ADD R4, R4, -1     ; decrement -10
    BRnz endString
    BRnzp xloop
endString
    ;BRnzp read
```
`+-------------------------------------------------------------------------------------+`
# About LC-3
The LC3 Simulator project is a web-based application that simulates the behavior of the LC-3 (Little Computer 3) assembly language. The purpose of this project is to help users learn and understand how the LC-3 works by providing a visual representation of the CPU registers and memory.

The LC-3 is a computer architecture used in many computer science courses to teach assembly language programming. However, learning assembly language can be challenging, especially for beginners. This simulator aims to make the learning process more interactive and engaging.

The simulator allows users to write assembly language code and run it on the simulated LC-3 machine. Users can see the values of CPU registers and memory locations change as their program runs. The simulator also provides a step-by-step execution mode, which allows users to understand how each instruction is executed by the machine.

# Technologies Used
- LC-3 Assembly Language

# Features
- Simulated CPU registers and memory
- Ability to write and run LC-3 assembly language code
- Step-by-step execution mode
- Interactive interface with visual representation of the machine state
- User-friendly error messages
- Cross-platform compatibility

