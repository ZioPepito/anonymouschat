# Anonymous Chat on P2P Networks

This project is developed and supported for the University of Salerno master class of Distributed Systems. It aims to show an example of the P2P framework/library [TomP2P](https://tomp2p.net/).

## Description

A simple p2p anonymous chat where members (peers) can create and/or join a chat room and send messages in it. 

## Implementation

### Basic operations

- Create a chat room by specifying a unique name
- Join one of the created chat rooms by specifying the name
- Leave a chat room you joined by specifying the name
- Send a message in a room you joined (type room's name and then the message)

### Additional operation

- Delete a room specifying the name, only if you are the creator
- List the rooms you joined
- Leave the network

### Technologies

The project has been implemented with:
- Java 8
- Apache Maven
- Eclipse IDE
- Tom p2p
- JUnit
- Docker

## Project Structure

The main program is structured in six Java classes cotained in the package ```src/main/java/it/unisa/gianmarcorusso/anonymouschat/```: 

- _AnonymousChat_ the interface that define all the operations of the project.
- _AnonymousChatImpl_ the implementation of the previous interface.	
- _Room_ a class that contains all the information about a chat room.
- _MessageListener_ a interface for listener of messages received
- _MessageListenerImpl_ the iplementation of the previous interface
- _Program_ a text terminal to interact with the system.

The project provide also the class _AnonymousChatTest_ in the package ```src/test/java/it/unisa/gianmarcorusso/anonymouschat/``` which is a JUnit test case.

## Build app in a Docker container

An example application is provided using Docker container, running on a local machine. See the Dockerfile, for the builing details.

First of all you can build your docker container:

```docker build --no-cache -t anonymouschat  .```

#### Start the master peer

After that you can start the master peer, in interactive mode (-i) and with two (-e) environment variables:

```docker run -i --name MASTER-PEER -e MASTERIP="127.0.0.1" -e ID=0 anonymouschat```

The MASTERIP envirnoment variable is the master peer ip address and the ID environment variable is the unique id of your peer. Rember you have to run the master peer using the ID=0.

#### Start a generic peer

When master is started you have to check the ip address of your container:

- Check the docker <container ID>: ```docker ps```
- Check the IP address: ```docker inspect <container ID>```

Now you can start your peers varying the unique peer id:

```docker run -i --name PEER-1 -e MASTERIP="172.17.0.2" -e ID=1 anonymouschat```

### Developed by:

Gianmarco Russo
0522500542
