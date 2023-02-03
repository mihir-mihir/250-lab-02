# Lab 2
[Fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo) this repo and clone it to your machine to get started!

## Team Members
- Mihir Singh

## Lab Question Answers

Question 1: 
When 50% loss was added to the local environment, around half of the messages
were dropped; this behavior is expected because UDP does not guarantee that 
messages will reach their destination.

Question 2:
No messages were dropped when using TCP; this behavior was also when using TCP,
the source establishes a connection with the destination before sending messages,
and it has other features that ensure that the message gets to the destination.

Question 3:
The TCP response got slower, this could be because it took some time to resend
messages that didn't get delivered to the destination on the first try.

## tcp server code questions

1.
argc is one plus the number of arguments provided to the program in the command
line (argv[0] is the name of the program you're running), and *argv is a pointer
to the start of the array where the name of the program and the program's
arguments are stored.

2.
A UNIX file descriptor is a small integer that can represent a network socket
/connection, among other things like a file or io stream. These file descriptors
serve as indices for the file descriptor table, where the table entries are 
information about the corresponding socket/file/etc. (https://cs61.seas.harvard.edu/site/ref/file-descriptors/#gsc.tab=0)

3.
A struct consists of a collection of data members asscociated with whatever
the struct represents. For example, a playing card struct could include data
members that represent the suit, color, and rank. The sockaddr_in struct 
represents an internet address, and includes members for the address family,
port number, and IP address. 
(https://linuxhint.com/sockaddr-in-structure-usage-c/)

4.
The first parameter is the domain (either AF_INET for connecting two hosts
across the internet, or AF_UNIX for two processes with a common file system),
the second is the type of socket (either stream or datagram),
and the third is the protocol; using 0 will select the default protocol.
It returns the file descriptor number if there aren't errors, -1 otherwise.
(https://www.cs.rpi.edu/~moorthy/Courses/os98/Pgms/socket.html)

5.
bind() takes the socket fd returned by socket() as its first parameter, the
pointer to a sockaddr struct as its second parameter, and the length of this
struct in bytes as its third parameter.
listen() takes in the same socket fd, and the maximum number of pending/incoming
connections it will hold in queue.
(https://www.ibm.com/docs/en/zos/2.4.0?topic=functions-bind-bind-name-socket#bind,
 https://www.ibm.com/docs/en/zos/2.4.0?topic=functions-listen-prepare-server-incoming-client-requests)

6. 
While(1) might be used to make sure that the server is always listening for 
connections. If there are simultaneous connections, the server might miss out
on one of the connections and not receive the corresponding message. 

7.
The fork() function is used to create processes; you could call fork() at the
start of the while loop so that simultaneous connections can be handled by
different processes.

