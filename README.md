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

- `client.py`: This the folder where you can find the main scripts for the chat client. It handles connecting to the chat server, sending messages, and displaying messages received from other clients.
- `server.py`: This the folder where you can find the main scripts for the chat server. It listens for incoming connections from clients, handles incoming messages, and broadcasts messages to all connected clients.


<aside>
📢 **This part can be changed on the developing parts**

</aside>
