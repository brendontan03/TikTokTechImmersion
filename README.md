# assignment_demo_2023

![Tests](https://github.com/TikTokTechImmersion/assignment_demo_2023/actions/workflows/test.yml/badge.svg)

# Done by: Chew Jing Xiang

This repository contains the backend implementation of an Instant Messaging (IM) system, designed and implemented in Golang. The system focuses on core message features without the front-end part and the account/authentication functionality.

# Overview
The HTTP server receives HTTP requests from clients and communicates with the RPC server through an RPC call. The RPC server accesses a Redis database to read messages and update the database when an HTTP request is sent. The messages that are read or written are then sent back to the HTTP server and provided as feedback to the client.

In the http-server's main.go file, it initializes itself and utilizes the API defined in the idl_http.proto file. It determines whether the request is for sending a message (api/send) or pulling messages (api/pull) and includes the relevant details such as the message content and the chat/roomID. This information is transmitted to the rpc-server for further processing.

The main.go file in the rpc-server initializes itself and sets up the redis database and client using the docker-compose.yml file.

The redis.go file in the rpc-server serves as the database client. It is responsible for saving and retrieving messages from the redis database based on the requests send by the server.

The handler.go file in the rpc-server handles the incoming requests by parsing their details, such as the message and sender. It then instructs the database client to either save or retrieve messages from the database accordingly.
