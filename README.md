# CRYPTOGRAPHY
HILL CIPHER
EX. NO: 1(C) AIM:
 

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

STEP-1: Read the plain text and key from the user.<br>
STEP-2: Split the plain text into groups of length three.<br>
STEP-3: Arrange the keyword in a 3*3 matrix.<br>
STEP-4: Multiply the two matrices to obtain the cipher text of length three.<br>
STEP-5: Combine all these groups to get the complete cipher text.<br>

## PROGRAM :
```
import numpy as np
import string

def encode_triplet(a, b, c, keymat):
    alphabet = string.ascii_uppercase
    posa, posb, posc = alphabet.index(a), alphabet.index(b), alphabet.index(c)
    
    result = np.dot(keymat, [posa, posb, posc]) % 26
    return "".join(alphabet[i] for i in result)

def decode_triplet(a, b, c, invkeymat):
    alphabet = string.ascii_uppercase
    posa, posb, posc = alphabet.index(a), alphabet.index(b), alphabet.index(c)
    
    result = np.dot(invkeymat, [posa, posb, posc]) % 26
    result = [(i + 26) % 26 for i in result]  
    return "".join(alphabet[i] for i in result)

def hill_cipher(message):
    keymat = np.array([[1, 2, 1], [2, 3, 2], [2, 2, 1]])
    invkeymat = np.array([[-1, 0, 1], [2, -1, 0], [-2, 2, -1]])
    alphabet = string.ascii_uppercase
    
    message = message.upper().replace(" ", "")
    n = len(message) % 3
    if n != 0:
        message += "X" * (3 - n)
    
    encoded_message = ""
    for i in range(0, len(message), 3):
        encoded_message += encode_triplet(message[i], message[i+1], message[i+2], keymat)
    
    decoded_message = ""
    for i in range(0, len(encoded_message), 3):
        decoded_message += decode_triplet(encoded_message[i], encoded_message[i+1], encoded_message[i+2], invkeymat)
    
    return message, encoded_message, decoded_message

if __name__ == "__main__":
    message = input("Enter the message to encrypt: ")
    padded, encoded, decoded = hill_cipher(message)
    print("Input message:", message)
    print("Padded message:", padded)
    print("Encoded message:", encoded)
    print("Decoded message:", decoded)


```


## OUTPUT:
![image](https://github.com/user-attachments/assets/c83f7247-81f2-414a-807c-493af420f8a7)


## RESULT
The program Hill Cipher is executed successfully
