# OpenChat - Python chat application 

<p align="center" width="100%">
    <img width="70%"src="https://i.imgur.com/vp7dkmA.gif)"> 
</p>

Simple terminal-based chat application that uses the Python sockets library to communicate between a server and multiple clients

# Summary

Developing a chat application with certificate-based authentication can be a challenging but interesting project. Here are a few things you might consider as you start your project:

1. First, you'll need to decide what kind of chat application you want to build. Do you want a one-to-one chat application, or a group chat application?
2. You'll need to decide how you want to handle the server-side of your chat application. One option is to use a framework like Tornado or Twisted to build a server that can handle multiple connections concurrently. 
3. On the client side, you'll need to implement a way for users to authenticate with the chat server using their certificates. This will likely involve using the Python SSL library to establish secure connections to the server.
4. You'll need to decide on a protocol for your chat application.

# Consideration

The purpose of this project was to learn how to incorporate encryption, Diffie-Hellman key exchange, digital signatures, and SSL certificates into a Python application. Please note that this application is not intended for use in a production environment or for transmitting sensitive data. As such, the GUI may be unattractive and simplified, and some important security considerations may not have been addressed. This application should not be used for sensitive data.

This project includes the following security features and measures:

1. End-to-end encrypted messaging between clients using Fernet, which is a method that combines AES-128-CBC encryption with a SHA256 HMAC authentication code.
2. A multi-client version of the Elliptic curve Diffie-Hellman (ECDH) key exchange.
3. An SSL socket connection between clients and server, with the server acting as both a server and a certificate authority (CA).
4. Digital signatures using elliptic curves.

# Security issues:
A potential issue with the current verification process for clients on a server is that the client initially sends their public key to the server. 

To address this, an alternative solution could be implementing a login/registration system for clients, which would generate a public key and store it in a database for the server to check during each challenge. 

Additionally, it has been noted that the SSL certificate verification from the client currently lacks an implemented callback function, and further research is necessary to make this aspect of the verification process secure.

## Base Points

The Python chat application consists of the following files:

### 1. client
This the folder where you can find the main scripts for the chat client. It handles connecting to the chat server, sending messages, and displaying messages received from other clients.

#### 1.1. `sign.py`:
This code appears to contain a collection of functions related to public key cryptography and digital signing.

The function `createSignature` takes in two parameters, `pathToPrivateKey` and prehashed. It opens a private key file, and prompts the user to enter a password. It then attempts to use the private key to create a digital signature of the prehashed input using the ECDSA algorithm with SHA256. If the password is incorrect, it will prompt the user again.

The function `verifySignature` takes in three parameters, `serialized_public`, `signature`, and `prehashed`. It loads the public key from the serialized input and verifies the signature of the prehashed input using the ECDSA algorithm with SHA256.

The function `createSerializedKeys` takes in one parameter, `password`, it generates a private/public key pair using the SECP384R1 curve and saves the serialized key pair to private.pem and public.pem

The function `signMessage` takes in three parameters, a socket, `s`, `username`, and `password`. It receives data from the socket in json format, if the data is not empty, it will create a new serialized key pair, sign the message using the private key, and send the username, public key, and signature to the server as a json object.

The function `getPublicKey` takes in one parameter, `pathToPublicKey`, it opens a public key file and returns the serialized public key.

### 2. Server
This the folder where you can find the main scripts for the chat server. It listens for incoming connections from clients, handles incoming messages, and broadcasts messages to all connected clients.

#### 1.1. `sign.py`:
This code defines several functions related to digital signatures and key generation using the cryptography library in Python. The main functions are:
- `createSignature(pathToPrivateKey, prehashed)`: This function takes the path to a private key in PEM format and a pre-hashed message as input, loads the private key, prompts the user for a password, and then uses the private key to create a digital signature of the pre-hashed message using the ECDSA algorithm with a SHA256 hash. It returns the signature.
- `verifySignature(serialized_public, signature, prehashed)`: This function takes a serialized public key, a signature, and a pre-hashed message as input, loads the public key, and then verifies the signature using the ECDSA algorithm with a SHA256 hash. It returns true if the signature is valid and false otherwise.
- `createSerializedKeys(password)`: This function takes a password as input and generates a new private-public key pair using the SECP384R1 curve. It then serializes the private key and writes it to a file called "private.pem", and serializes the public key and writes it to a file called "public.pem".
- `signMessage(s, username, password)`: This function takes a socket object, a username, and a password as input, receives data over the socket, generates a new key pair, creates a signature of the received message using the private key, and then sends a JSON object containing the username, the public key, and the signature to the server over the socket.
- `getPublicKey(pathToPublicKey)`: This function takes the path to a public key in PEM format as input, reads the key from the file, and returns the serialized public key.

# Usage

To connect to the server, the user must first create a password for encrypting their private key used in digital signatures. Upon initial connection to the server, the user will be presented with options to either create a new chat room, join an existing one by name, or view a list of all active chat rooms.


