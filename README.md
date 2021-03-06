# Assembly-encryption-functions-
In this project I wanted to implement some functions of encryption or processing of a string to gain a better understanding of how to think and program in assembly. 
   This repository contains the implementation of several functions of encryption or processing of a string.
The function parameters are placed in the registers. The result of each function will be placed in the first parameter of the function and the final exercise makes the display without using the PRINTF32 macro,external functions or system calls. 
   The otp1.asm algorithm consists in performing the XOR operation between a message (plain) and a key (key),of the same length as the message. The similar C header of the function implemented in the assembly is: 
void otp(char *ciphertext, char *plaintext, char *key, int length)
   Another well-known algorithm, called Caesar Cipher, receives a message and a key, represented by a number,and moves each letter in the message in a circle with the value specified by the key. The similar C header of the function implemented in the assembly is:
void caesar(char *ciphertext, char *plaintext, int key, int length)
For the implementation of the Caesar Cipher algorithm I needed the test_character label in which I check if I'm dealing with a letter or non-letter type character to treat these 2 cases differently in the is_not_letter, is_upper_letter, is_lower_letter labels. If I was dealing with a large or small letter that after adding a key became non-letter I performed the wrap_around process, that means I subtract from the key,the value 26, to make it possible to further display a letter and not a random character other than the letter. 
   The next algorithm I implemented in the assembly is the Vigenere Cipher, which receives the messageto be encrypted and a key, represented by a string of capital letters. If the key is shorter than the message,it extends to the length of the message by repeating the original key. Then, each letter in the message is moved
circularly to the right a number of times equal to the position in the alphabet (starting from position 0) of the corresponding letter in the key. Also, characters that are not letters will be ignored. The similar C header of the function implemented in the assembly is:
void vigenere(char *ciphertext, char *plaintext, int plaintext_len, char *key, int key_len)
For the implementation of the Vigenere Cipher algorithm I used a procedure similar to the one used to implement the algorithm previous only that this time I had to go through the key and if it ends we will start going throughit again when we have a letter in our unencrypted message. 
   The last algorithm implemented, called my_strstr.asm, implements the strstr function in C. It finds the first occurrence of a substring in a string. In the first parameter of the function, the index of the first occurrence of the substring in the given string will be retained. If the subsequent sequence is not found in the original string,I will return the length of the original string + 1. The similar C header of the function implemented in the assembly is:
void my_strstr(int *substr_index, char *haystack, char *needle, int haystack_len, int needle_len)
In order to implement the StrStr algorithm, I had to check the string and the substring in parallel, and if at a certain moment the verified characters no longer met the condition to be equal, I continue the process of searching the string until I find a matching substring. If I reached the end of the string and this does not happen I return to the edi register the length of the haystack string to which I add the value 1. 
