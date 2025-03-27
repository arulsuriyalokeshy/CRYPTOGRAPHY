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

def get_key_matrix():
    key_matrix = np.zeros((2, 2), dtype=int)
    print("Enter the 2x2 key matrix (values between 0-25):")
    for i in range(2):
        for j in range(2):
            key_matrix[i][j] = int(input(f"Element [{i+1}][{j+1}]: "))
    return key_matrix

def to_upper_case(text):
    return text.upper()

def remove_spaces(text):
    return text.replace(" ", "")

def encrypt(text, key_matrix):
    text = to_upper_case(remove_spaces(text))
    
    if len(text) % 2 != 0:
        text += 'X'  # Padding if needed
    
    text_vector = [ord(char) - ord('A') for char in text]
    cipher_text = ""
    
    for i in range(0, len(text_vector), 2):
        vector = np.array(text_vector[i:i+2]).reshape(2, 1)
        encrypted_vector = np.dot(key_matrix, vector) % 26
        cipher_text += ''.join(chr(num + ord('A')) for num in encrypted_vector.flatten())
    
    return cipher_text

def main():
    key_matrix = get_key_matrix()
    
    print("Key Matrix:")
    print(key_matrix)
    
    text = input("Enter plaintext: ")
    cipher_text = encrypt(text, key_matrix)
    
    print(f"Ciphertext: {cipher_text}")

if __name__ == "__main__":
    main()



```


## OUTPUT:
![image](https://github.com/user-attachments/assets/c14ab2ff-75c1-4d98-bb13-779812834864)




## RESULT
The program Hill Cipher is executed successfully
