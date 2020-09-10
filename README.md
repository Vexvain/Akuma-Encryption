# Symmetric Encryption

A custom symmetric encryption algorithm I created. <br/>

Use it to make plaintext unreadable by encrypting it with a key. <br/>

256 bit encryption; the key and IV must be 256 bits/32 bytes.

OpenSSL Library required for Code compilation.

____________________________________________

# Compilation   
    $ cd examples/
    $ gcc -o encrypt encrypt.c -I ../ -lcrypto
    $ gcc -o decrypt decrypt.c -I ../ -lcrypto
    
# Usage
`Code/encrypt.c` <br/>
**AND** <br/>
`Code/decrypt.c` are examples on how to encrypt and decrypt data using this cipher.


I have included two example files in the `Code/Files` folder:

- `Code/Files/plaintext.txt` is an example plaintext message which can be read. Put anything you want. 

- `Code/Files/key.bin` is an example key file that contains random hex characters which have been randomly generated. You can generate your own key file.

To encrypt your file, use: `./encrypt [PLAINTEXT FILE] [KEY FILE] [OUT FILE]`. 

Example:

    $ ./encrypt  Files/plaintext.txt  Files/key.bin  encrypted.bin

The program then reads the plaintext and encrypts it using the key. <br/>

This program generates a random initialization vector, which you need to keep hold of if you're manually using the `akuma.h` header file. <br/>

**This example program does it automatically.** <br/>

It will save the encrypted text (ciphertext) to your specified output filename (third argument) and puts the initialization vector as the last 32 bytes of the ciphertext for the decryption program to use. It is important to keep the key and initialization vector when encrypting. If you are using the example programs, do not edit the generated ciphertext file after encryption, or you will not be able to decrypt it.

To decrypt the ciphertext file, use: `./decrypt [CIPHERTEXT FILE] [KEY FILE] [OUT FILE]`. 

Here's an example:

    $ ./decrypt  encrypted.bin  Files/key.bin  decrypted.txt
    
The program then reads the ciphertext file and decrypts it using the key. <br/>
It saves the decrypted text to `decrypted.txt` and is readable again.

# This is a test version #

TODO: Add options for base64 encoding.

TODO: Provide alternative for manual pkcs#7 padding (pkcs7pad())

