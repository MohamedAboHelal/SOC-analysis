- The transport layer is responsible for logical communications between applications running on different hosts. This may include services such as establishing a temporary session between two hosts and the reliable transmission of information for an application.

<img src="D:\Typora\transport_layer.PNG" style="zoom:50%;" />



- The transport layer includes two protocols:
  - TPC
  - UDP

- Transport Layer Responsibilities:

  - Tracking Individual Conversations
  - Segmenting Data and Reassembling Segments
  - Add Header Information
    - For instance, the header information is used by the receiving host to reassemble the blocks of data into a complete data stream for the receiving application layer program.
  - Identifying the Applications
    - To pass data streams to the proper applications, the transport layer identifies the target application using an identifier called a port number.
  - Conversation Multiplexing

  

  ## TCP Header

  ##  <img src="D:\Typora\tcp_header.PNG" style="zoom:90%;" />



| **Source Port**           | A 16-bit field used to identify the source application by port number. |
| ------------------------- | ------------------------------------------------------------ |
| **Destination Port**      | A 16-bit field used to identify the destination application by port number. |
| **Sequence Number**       | A 32-bit field used for data reassembly purposes.            |
| **Acknowledgment Number** | A 32-bit field used to indicate that data has been received and the next byte expected from the source. |
| **Header Length**         | A 4-bit field known as ʺdata offsetʺ that indicates the length of the TCP segment header. |
| **Reserved**              | A 6-bit field that is reserved for future use.               |
| **Control bits**          | A 6-bit field that includes bit codes, or flags, which indicate the purpose and function of the TCP segment. |
| **Window size**           | A 16-bit field used to indicate the number of bytes that can be accepted at one time. |
| **Checksum**              | A 16-bit field used for error checking of the segment header and data. |
| **Urgent**                | A 16-bit field used to indicate if the contained data is urgent. |

- During session setup, an initial sequence number (ISN) is set. This ISN represents the starting value of the bytes that are transmitted to the receiving application. 
- The ISN does not begin at one but is effectively a random number. This is to prevent certain types of malicious attacks.
- The sequence (SEQ) number and acknowledgement (ACK) number are used together to confirm receipt of the bytes of data contained in the transmitted segments.
-  The SEQ number identifies the first byte of data in the segment being transmitted. TCP uses the ACK number sent back to the source to indicate the next byte that the receiver expects to receive. This is called expectational acknowledgement.
-  TCP flow control:  is the amount of data that the destination can receive and process reliably.  Flow control helps maintain the reliability of TCP transmission by adjusting the rate of data flow between source and destination for a given session.To accomplish this, the TCP header includes a 16-bit field called the window size.
-  Maximum Segment Size (MSS) that the destination device can receive.
-  purpose of the TCP sliding window: allows a destination device to inform a source to slow down the rate of transmission.



### selective acknowledgment (SACK)

- If both hosts support SACK, the receiver can explicitly acknowledge which segments (bytes) were received including any discontinuous segments.	

![](D:\github\SOC-analysis\CyberOps Associate\Transport layer\Mics\SACK.PNG)



- ### TCP flags

  - **URG** - Urgent pointer field significant
  - **ACK** - Acknowledgment flag used in connection establishment and session termination
  - **PSH** - Push function
  - **RST** - Reset the connection when an error or timeout occurs
  - **SYN** - Synchronize sequence numbers used in connection establishment
  - **FIN** - No more data from sender and used in session termination



## UDP Header

<img src="D:\Typora\UDP_header.PNG" style="zoom:80%;" />



- UDP is a stateless protocol, meaning neither the client, nor the server, tracks the state of the communication session. If reliability is required when using UDP as the transport protocol, it must be handled by the application.



## Socket Pairs

```
- The combination of the source IP address and source port number, or the destination IP address and destination port number is known as a socket.

- A client socket might look like this, with 1099 representing the source port number: 192.168.1.5:1099
- The socket on a web server might be 192.168.1.7:80
- Together, these two sockets combine to form a socket pair: 192.168.1.5:1099, 192.168.1.7:80
- The source port number acts as a return address for the requesting application. The transport layer keeps track of this port and the application that initiated the request so that when a response is returned, it can be forwarded to the correct application.
```

<img src="D:\Typora\socket.PNG" style="zoom:67%;" />











