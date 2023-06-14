# assignment_demo_2023

![Tests](https://github.com/TikTokTechImmersion/assignment_demo_2023/actions/workflows/test.yml/badge.svg)

# Done by: Brendon Tan

This repository contains the backend implementation of an Instant Messaging (IM) system using Golang. It focuses on core message features, excluding the front-end and account/authentication functionality.

# Overview
The system consists of an HTTP server that receives client requests and communicates with an RPC server. The RPC server interacts with a Redis database to read and update messages in response to HTTP requests. The retrieved or modified messages are then sent back to the HTTP server as feedback for the clients.

In the main.go file of the HTTP server, it initializes itself and utilizes the API defined in the idl_http.proto file. It determines the nature of the request, whether it's for sending a message (api/send) or pulling messages (api/pull), and includes relevant details such as the message content and the chat/room ID. This information is then transmitted to the RPC server for further processing.

The main.go file of the RPC server initializes itself and sets up the Redis database and client using the docker-compose.yml file.

The redis.go file in the RPC server acts as the database client. It handles the saving and retrieval of messages from the Redis database based on the requests sent by the server.

The handler.go file in the RPC server processes incoming requests by parsing their details, such as the message content and sender. It then instructs the database client to either save or retrieve messages from the database accordingly.
