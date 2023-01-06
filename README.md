# OpenChat - Python chat application 

Simple terminal-based chat application that uses the Python sockets library to communicate between a server and multiple clients

# Summary

Developing a chat application with certificate-based authentication can be a challenging but interesting project. Here are a few things you might consider as you start your project:

1. First, you'll need to decide what kind of chat application you want to build. Do you want a one-to-one chat application, or a group chat application?
2. You'll need to decide how you want to handle the server-side of your chat application. One option is to use a framework like Tornado or Twisted to build a server that can handle multiple connections concurrently. 
3. On the client side, you'll need to implement a way for users to authenticate with the chat server using their certificates. This will likely involve using the Python SSL library to establish secure connections to the server.
4. You'll need to decide on a protocol for your chat application.


## Base Points

The Python chat application consists of the following files:

- `client.py`: This is the main script for the chat client. It handles connecting to the chat server, sending messages, and displaying messages received from other clients.
- `server.py`: This is the main script for the chat server. It listens for incoming connections from clients, handles incoming messages, and broadcasts messages to all connected clients.
- `protocol.py`: This module contains the `ChatProtocol` class, which implements the custom chat protocol used by the server and clients to communicate with each other.
- `utilities.py`: This module contains a few utility functions that are used by the client and server scripts.
- `README.md`: This is a markdown file that contains a description of the chat application and instructions for how to run it.

<aside>
📢 **This part can be changed on the developing parts**

</aside>
