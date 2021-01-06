###  Servers vs clients

```
- servers: are simply computers with specialized software that enables servers to provide information to other end devices on the network.
A server can be single-purpose, providing only one service, such as web pages or it can be multipurpose, providing a variety of services such as web pages, email, and file transfers.

- clients: Client computers have software installed that enables them to request and display the information obtained from the server.

```



# Network protocols


##  1- Email protocols (SMTP - POP3 - IMAP )

```
Your ability to send and receive emails is largely due to 3 TCP protocols: SMTP, IMAP, and POP3.

Email protocols are used to transfer emails from one point to another through a series of mail servers along its way to its intended recipient.
so to understand the difference between these protocols, you should know Types of Mail Servers firstly.

Types of Mail Servers:
	1-  Outgoing mail servers: are known as SMTP, or Simple Mail Transfer Protocol, servers.
	2-  Incoming mail servers: come in two main varieties. POP3, or Post Office Protocol, version 3, servers are best known for storing sent and 															 received messages on PCs' local hard drives. IMAP, or Internet Message Access Protocol, servers always store copies 															of messages on servers. Most POP3 servers can store messages on servers, too, which is a lot more convenient.
```



### SMTP

- Enables clients to send email to a mail server and enables servers to send email to other servers. uses port 25 by default.It may also use port 587 and port 465.The latter, which was introduced as the port of choice for secure SMTP

- A sender will use an SMTP server to carry out the process of transmitting an email message.



### POP3

- Enables clients to retrieve email from a mail server and download the email to the client's local mail application.
- Generally speaking, a POP3 client retrieves email in the following manner:
  1. Connects to the mail server on port 110 (or 995 for SSL/TLS connections);
  2. Retrieves email messages; 
  3. Deletes copies of the messages stored on the server; and
  4. Disconnects from the server
- Although POP clients may be configured to allow the server to continue storing copies of the downloaded messages, the steps outlined above is the usual practice. Leaving them on the server is a practice that's usually done via IMAP. Let's talk about it now.



### IMAP

- Enables clients to access email stored on a mail server as well as maintaining email on the server.

- It allows users to group related messages and place them in folders, which can in turn be arranged hierarchically. It's also equipped with message flags that indicate whether a message has been read, deleted, or replied to. It even allows users to carry out searches against the server mailboxes.

- So guess you deal with yahoo through POP3 OR IMAP ??



### The Process of Sending an Email

- Step #1: After composing a message and hitting send, your email client - whether it's Outlook Express or Gmail - connects to your domain's SMTP server. This server can be named many things; a standard example would be smtp.example.com.

- Step #2: Your email client communicates with the SMTP server, giving it your email address, the recipient's email address, the message body and any attachments.

- Step #3: The SMTP server processes the recipient's email address - especially its domain. If the domain name is the same as the sender's, the message is routed directly over to the domain's POP3 or IMAP server - no routing between servers is needed. If the domain is different, though, the SMTP server will have to communicate with the other domain's server.

- Step #4: In order to find the recipient's server, the sender's SMTP server has to communicate with the DNS, or Domain Name Server. The DNS takes the recipient's email domain name and translates it into an IP address. The sender's SMTP server cannot route an email properly with a domain name alone; an IP address is a unique number that is assigned to every computer that is connected to the Internet. By knowing this information, an outgoing mail server can perform its work more efficiently.

- Step #5: Now that the SMTP server has the recipient's IP address, it can connect to its SMTP server. This isn't usually done directly, though; instead, the message is routed along a series of unrelated SMTP servers until it arrives at its destination.

- Step #6: The recipient's SMTP server scans the incoming message. If it recognizes the domain and the user name, it forwards the message along to the domain's POP3 or IMAP server. From there, it is placed in a sendmail queue until the recipient's email client allows it to be downloaded. At that point, the message can be read by the recipient.



## Example of SMTP & IMAP Working Together

- After creating an email and pressing ‘send’, your email client (e.g. Gmail, Thunderbird, Outlook, etc.) will use SMTP to send your message from your email client to an email server.

- Next, the email server will use SMTP to transmit the message to the recipient’s receiving email server.

- Upon a successful receipt of the SMTP transmission (indicated by a 250 OK response code), the recipient’s email client will fetch the message using IMAP and place it in the inbox for the recipient to access.



## 2- Host Config(DHCP & SLAAC)

```
- DHCPv4 (Dynamic Host Configuration Protocol for IPv4): Dynamically assigns IPv4 addressing information to DHCPv4 clients at start-up and allows the addresses to be re-used when no longer needed.

- DHCPv6 (Dynamic Host Configuration Protocol for IPv6): It is similar to DHCPv4. Dynamically assigns IPv6 addressing information to DHCPv6 clients at start-up.

- SLAAC (Stateless Address Autoconfiguration): A method that allows a device to obtain its IPv6 addressing information without using a DHCPv6 server.
```



## 3- File Transfer (FTP - SFTP - TFTP)

```
- FTP (File Transfer Protocol): Sets the rules that enable a user on one host to access and transfer files to and from another host over a network

- SFTP (SSH File Transfer Protocol): Used to establish a secure file transfer session in which the file transfer is encrypted.

- TFTP (Trivial File Transfer Protocol): A simple and connectionless protocol with best-effort, unrecognized file delivery. 
```



### FTP Server Vs Web Server

- FTP and web servers both transmit information over the Internet, but they do so in different ways.
- An FTP server focuses on sharing files without providing an interface using FTP protocol
- while a web server provides visual pages of information using HTTP protocol.



### FTP clients

FTP clients are used to upload, download and manage files on a FTP server. FTP clients include:

- WinSCP is a Windows FTC client that supports FTP, SSH and SFTP.
- WS FTP is another Windows FTC client which also supports SSH.
- Transmit is an FTP client for Mac, supporting FTP, SSH and FTP.



## 4- Web and Web Service

```
- HTTP (Hypertext Transfer Protocol): A set of rules for exchanging text, graphic images, sound, video, and other multimedia files on the World Wide Web.

- HTTPS (HTTP Secure): A secure form of HTTP that encrypts the data that is exchanged over the World Wide Web.

- REST (Representational State Transfer): A web service that uses application programming interfaces (APIs) and HTTP requests to create web applications
```



### HTTP

- Request response protocol.
- Http is stateless protocol so we use (sessions & cookies)
- HTTP is called as a stateless protocol because each request is executed independently, without any knowledge of the requests that were executed before it, which means once the transaction ends the connection between the browser and the server is also lost.

- Cookies and Sessions: are used to store information. Cookies are only stored on the client-side machine, while sessions get stored on the client as well as a server.

- Cookies are text files stored on the client computer and they are kept of use tracking purpose. Server script sends a set of cookies to the browser. For example name, age, or identification number etc. The browser stores this information on a local machine for future use.When next time browser sends any request to web server then it sends those cookies information to the server and server uses that information to identify the user.





### Cookie Vs. Session

|                           Cookie                            |                           Session                            |
| :---------------------------------------------------------: | :----------------------------------------------------------: |
| Cookies are client-side files that contain user information | Sessions are server-side files which contain user information |
|    Cookie ends depending on the lifetime you set for it     |        A session ends when a user closes his browser         |
|            A cookie is not dependent on Session             |               A session is dependent on Cookie               |



### HTTP request methods

| GET         | **GET is used to request data from a specified resource.**   |
| ----------- | ------------------------------------------------------------ |
| **HEAD**    | **HEAD is almost identical to GET, but without the response body(HTML),only retrieve status code.** |
| **POST**    | **POST is used to send data to a server to create/update a resource.** |
| **PUT**     | **PUT is used to send data to a server to create/update a resource.** |
| **DELETE**  | **The DELETE method deletes the specified resource.**        |
| **OPTIONS** | **The OPTIONS method describes the communication options for the target resource.** |



## 5- Internet Protocol

```
- IPv4 (Internet Protocol version 4): Receives message segments from the transport layer, packages messages into packets, and addresses packets for end-to-end delivery over a network. IPv4 uses a 32-bit address.

- IPv6 (IP version 6): Similar to IPv4 but uses a 128-bit address.

- NAT (Network Address Translation): Translates IPv4 addresses from a private network into globally unique public IPv4 addresses.
```



## 6- Messaging

```
- ICMPv4 (Internet Control Message Protocol for IPv4): Provides feedback from a destination host to a source host about errors in packet delivery.

- ICMPv6 (ICMP for IPv6): Similar functionality to ICMPv4 but is used for IPv6 packets.

- ICMPv6 ND (ICMPv6 Neighbor Discovery): Includes four protocol messages that are used for address resolution and duplicate address detection.
```



## 7- Routing Protocols

```
- OSPF (Open Shortest Path First): Link-state routing protocol that uses a hierarchical design based on areas. OSPF is an open standard interior routing protocol.

- EIGRP (Enhanced Interior Gateway Routing Protocol): A Cisco proprietary routing protocol that uses a composite metric based on bandwidth, delay, load and reliability.

- BGP (Border Gateway Protocol): An open standard exterior gateway routing protocol used between Internet Service Providers (ISPs).
```



## 8- Network Access Layer

```
- Address Resolution - ARP (Address Resolution Protocol): Provides dynamic address mapping between an IPv4 address and a hardware address.

```









## Refernces

```
1- cisco cyber ops
2- https://www.jscape.com/blog/smtp-vs-imap-vs-pop3-difference
3- https://whatismyipaddress.com/mail-server
4- https://www.socketlabs.com/blog/smtp-or-imap
5- https://searchnetworking.techtarget.com/definition/File-Transfer-Protocol-FTP
6- https://www.tutorialspoint.com/What-is-the-difference-between-session-and-cookies
7- https://www.guru99.com/difference-between-cookie-session.html
8- https://www.w3schools.com/tags/ref_httpmethods.asp
```
