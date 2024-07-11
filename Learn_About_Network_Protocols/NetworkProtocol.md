## What is Network Protocol
Network Protocol is a way which defines rules to communicate over the network between two machines(Client and Server).

![Client-Serve-Communication](./Client-Server.png)

## What is Client Server Model
* The Client-server model is a distributed application structure that partitions tasks or workloads between the providers of a resource or service, called servers, and service requesters called clients. 
* In the client-server architecture, when the client computer sends a request for data to the server through the internet, the server accepts the requested process and delivers the data packets requested back to the client.
* HTTP or WebSockets are mostly used.

## Peer to Peer Model
* Here each computer machine acts as a server and client both for sharing data within the formed network. 
* This allows the sharing of huge amount of data in a very small time. Each machine connected in the network shares an equal workload.
* WebRTC is used. 

## HTTP vs TCP vs UDP vs FTP vs SMTP(IMAP, POP)

### HTTP
* The Hypertext Transfer Protocol (HTTP) is used to load webpages using hypertext links.
* HTTP is an application layer protocol designed to transfer information between networked devices and runs on top of other layers of the network protocol stack. 
* A typical flow over HTTP involves a client machine making a request to a server, which then sends a response message.

### TCP
* Transmission Control Protocol (TCP) is a communications standard that enables application programs to exchange messages over a network.
* Before it transmits data, TCP establishes a connection between a source and its destination.
*  It then breaks large amounts of data into smaller packets (chunks) and maintain the ordering of data (ensuring data integrity).

### UDP
* User Datagram Protocol (UDP) is a communications protocol for time-sensitive applications like gaming, playing videos, or Domain Name System (DNS) lookups.
* It is very fast as compared to TCP because UDP does not provide error connection or packet sequencing nor does it signal a destination before it delivers data, which makes it less reliable but less expensive.

### FTP
* FTP (File Transfer Protocol) is a standard network protocol used for the transfer of files from one machine to another over a TCP-based network.
* Its establishes two connection, One connection is designated for the commands and replies and other channel handles the transfer of data.

### SMTP
* The Simple Mail Transfer Protocol (SMTP) is an application used by mail servers to send, receive, and relay outgoing email between senders and receivers.

    #### IMAP
    * IMAP allows you to access your email wherever you are, from any device. 
    * When you read an email message using IMAP, you aren't actually downloading or storing it on your computer; instead, you're reading it from the email service.

    #### POP
    * POP works by contacting your email service and downloading all of your new messages from it. 
    * Once they are downloaded onto your PC or Mac, they are deleted from the email service. 
    * This means that after the email is downloaded, it can only be accessed using the same computer. 
    * If you try to access your email from a different device, the messages that have been previously downloaded won't be available to you.

### Examples
HTTP mostly used in : 
    
    > Web Browsing

    > APIs and Web Services

    > Mobile Applications

    > File Transfers

Web Sockets is used for real-time, bidirectional communications.
    
    > Real-Time Chat/Messaging 

    > Live Updates and Notifications

    > Online Gaming

WebRTC ideal for applications requiring

    > Real-Time media(audio/video)

    > Peer-to-Peer data transfer