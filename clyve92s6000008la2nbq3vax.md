---
title: "The Step-by-Step Process When You Enter "google.com" in Your Browser"
datePublished: Sun Jul 21 2024 10:07:15 GMT+0000 (Coordinated Universal Time)
cuid: clyve92s6000008la2nbq3vax
slug: what-happens-when
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721325720443/9ab3c5e6-6c7c-4e46-b69c-75ea5cb7651c.jpeg
tags: dns, browsers, server, https, backend, frontend-development, web-server, firewall

---

Today, I'm going to tell a story. It's a story for both techies and non-techies. Have you ever wondered what happens in the short time between when you type "google.com" in your browser and press "Enter" and when the browser displays Google's search engine? If you answered yes, then today is your lucky day!

I'm going to explain how it works step-by-step, so you understand what happens and the processes involved. Each sub-heading will guide you through the steps (they are in order). Let's dive right in.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721577460666/76043ad6-ca02-4ba5-b8b8-452b71604e3e.jpeg align="center")

### DNS Request

DNS (Domain Name System) is a system that translates human-friendly computer hostnames into IP addresses. You might wonder, what are hostnames and IP addresses? In simple terms, a hostname is a web address. An IP address, on the other hand, is a unique numeric address that identifies a computer or a node on the internet. It is a string of four numbers separated by periods, such as 192.158.1.38, where each number can range from 0 to 255.

**URL Entry:** When a user enters a URL (e.g., [www.google.com](http://www.example.com)) in the browser, the browser first checks its cache to see if it has a recently retrieved DNS record for the domain.

**Local DNS Cache:** If not found, the request is forwarded to the operating system's DNS cache.

**DNS Query:** If still not found, the OS sends a DNS query to the configured DNS server (typically provided by the ISP or a public DNS service like Google DNS or Cloudflare).

**Recursive Query:** The DNS server checks its cache; if not found, it performs a recursive query to find the IP address. It contacts root DNS servers, which direct it to TLD (Top-Level Domain) servers, which in turn direct it to authoritative DNS servers for the domain.

**Response:** Once the authoritative DNS server is reached, it returns the IP address associated with the domain to the DNS resolver. The resolver caches this information and sends it back to the client (browser).

### TCP/IP

TCP/IP stands for Transmission Control Protocol/Internet Protocol. It is a set of rules for how data is sent and received over the Internet and similar networks. The main protocols in this set are TCP, UDP (User Datagram Protocol), and IP.

TCP/IP makes sure data is sent from one computer to another correctly. It breaks data into packets, addresses them, sends them, routes them, and makes sure they are received. There are four layers in this system:

1. **Link Layer**: Handles data within a single network.
    
2. **Internet Layer**: Connects different networks.
    
3. **Transport Layer**: Manages communication between computers.
    
4. **Application Layer**: Manages data exchange for applications.
    

The processes involved in this section are:

**Connection:** With the IP address from DNS, the browser needs to establish a connection. This involves the IP address and a specific port number (default port 80 for HTTP and 443 for HTTPS).

**Three-Way Handshake:**

* **SYN:** The client sends a TCP SYN (synchronize) packet to the server to start a connection.
    
* **SYN-ACK:** The server responds with a SYN-ACK (synchronize-acknowledge) packet.
    
* **ACK:** The client sends an ACK (acknowledge) packet back to the server, completing the handshake and establishing a TCP connection.
    

**Data Transmission:** The TCP connection ensures reliable data transmission, handling packet ordering, error correction, and retransmission if needed.

### Firewall

Oh! This is an easy one. Most of you have probably heard this term at least once. If not, a firewall is a network security system that monitors and controls incoming and outgoing network traffic based on set security rules. A firewall usually creates a barrier between a trusted network and an untrusted network, like the Internet.

Firewalls inspect packets (chunks of data broken up by TCP/IP) for security threats, filtering out any malicious or unauthorized traffic. They ensure only legitimate traffic reaches the server.

### HTTPS/SSL

When creating or registering a domain name, the default network protocol is HTTP (Hyper Text Transfer Protocol). However, this protocol is not secure because third parties can intercept information during transmission. That's where the extra letter "S" comes in, standing for "Secure." HTTPS is more secure because it encrypts data in transit using session keys with an SSL (Secure Sockets Layer) certificate.

Below is how secure communication happens:

**SSL Handshake:**

* **ClientHello**: The client sends a message to the server, suggesting SSL protocol version, cipher suites, and other settings.
    
* **ServerHello**: The server replies with a message, choosing the protocol version and cipher suite.
    
* **Server Certificate**: The server sends its SSL certificate to the client to verify its identity.
    
* **Key Exchange**: The client and server swap cryptographic keys using methods like RSA, Diffie-Hellman, or ECDHE.
    
* **Session Keys**: Both the client and server create session keys to encrypt data.
    
* **Finished Messages**: Both the client and server send messages to confirm the handshake is complete.
    

**Encrypted Communication:** All subsequent communication is encrypted using the established session keys.

### Load Balancer

Load balancing is the process of spreading tasks across multiple resources (computing units) to make processing more efficient. It helps improve response time and prevents some computing nodes from being overloaded while others are idle.

For easy understanding (I love you, non-techies!), load balancers basically decide which web servers should handle client requests (like browser webpage requests) based on a set of predefined rules.

The load balancer works by:

**Request Routing:** The load balancer gets the incoming request and sends it to one of the available servers based on the load balancing algorithm (e.g., round-robin, least connections, IP hash).

**Health Checks:** The load balancer regularly checks the health of servers and only sends traffic to healthy ones.

**Session Persistence:** The load balancer can use session persistence (sticky sessions) to make sure that future requests from the same client go to the same server.

### Web Server

A web server is computer software and underlying hardware that accepts requests via HTTP or its secure variant HTTPS. A user agent, commonly a web browser or web crawler, initiates communication by making a request for a web page or other resource using HTTP, and the server responds with the content of that resource or an error message. A web server can also accept and store resources sent from the user agent if configured to do so.

The web server handles requests by:

**Processing Requests:** The web server (e.g., Apache, Nginx) receives the HTTP request from the load balancer.

**Static Content:** If the request is for static content (e.g., HTML, CSS, JavaScript, images), the web server serves it directly from the filesystem.

**Dynamic Content:** If the request requires dynamic content, the web server forwards it to the application server.

### Application Server

An application server hosts applications or software that delivers a business application through a communication protocol. For a typical web application, the application server is located behind the web servers.

An application server framework is a service layer model. It includes software components available to developers through an application programming interface. An application server may have features like clustering, fail-over, and load-balancing. The goal is for developers to focus on the business logic.

Business logic execution:

* **Query Execution:** The application server sends a SQL query (for relational databases like MySQL, PostgreSQL) or a request (for NoSQL databases like MongoDB) to the database server.
    
* **Data Retrieval:** The database processes the query, retrieves the required data, and sends it back to the application server.
    
* **Data Integrity:** Databases ensure data integrity, consistency, and security through ACID (Atomicity, Consistency, Isolation, Durability) properties for relational databases or BASE (Basically Available, Soft state, Eventual consistency) principles for NoSQL databases.
    

### Database

In computing, a database is a structured collection of data. It uses a database management system (DBMS) to interact with users, applications, and the database itself to capture and analyze data. The DBMS also includes tools to manage the database. Together, the database, the DBMS, and related applications are called a database system. Sometimes, the term "database" is used to refer to the DBMS, the database system, or an application linked to the database.

Database Management:

* **Query Execution**: The application server sends a SQL query (for relational databases like MySQL, PostgreSQL) or a request (for NoSQL databases like MongoDB) to the database server.
    
* **Data Retrieval**: The database processes the query, retrieves the required data, and sends it back to the application server.
    
* **Data Integrity**: Databases ensure data integrity, consistency, and security through ACID (Atomicity, Consistency, Isolation, Durability) properties for relational databases or BASE (Basically Available, Soft state, Eventual consistency) principles for NoSQL databases.
    

### Final Steps

**Response Assembly and Delivery:**

* **Response Generation**: The application server compiles the data into an HTTP response (e.g., HTML, JSON) and sends it back to the web server.
    
* **Serving Response**: The web server forwards the response to the load balancer, which routes it back to the client.
    
* **Client Rendering**: The client's browser receives the HTTP response, processes the content (HTML, CSS, JavaScript), and renders the web page for the user to see.
    

### Conclusion

I hope this detailed yet easy-to-understand article has given you some insight into what happens between the time you enter google.com (or any other web address) and when the browser displays the web page or application. If this article wasn't clear enough for you, please send me a DM on [My LinkedIn](https://www.linkedin.com/in/ikechukwu-ashimonye-262944283/).

Interested in Software Engineering? A great place to start is by learning about the Shell. Luckily for you, I have a Software Engineering series where you can follow one article after another, gaining knowledge step by step. You can begin by learning about the shell [here](https://techgecko.hashnode.dev/shell-basics).

If you found this post helpful, consider following us or subscribing to our newsletter for more similar content. Also, liking and sharing this topic might help others.

If you have any questions, feel free to comment below!