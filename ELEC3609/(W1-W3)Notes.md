# **Concepts**:

**DHCP**: Dynamic Host Configuration Protocol;

**IP**: Internet Protocol;

**LB**: Load Balancer;

**DNS**: Domain Name Server;

**UDP**: User Datagram Protocol - port 53;

**TCP**: Transmission Control Protocol

**DDoS Mitigation Services**

**App Servers**: handles processing of HTTP requests **[** Backend website code + Business Logic + Database interface methods + Caching Layers.**]**

**Master <=> Slaves**: Write to master <=> Read from slaves [ Improving parallelizability of DB reads]

- **Issue**: **[**Slave drift: time delay between W & R, Race Condition**]**

**DOM**: Document Object Model

**HTML**: Hyper Text Markup Language

**CSS**: Cascading Style Sheets

**Browser Rendering**: done by web browser engines, e.g, WebKit of Safari

---

**OSI Model**: Operating System Interconnection Model;

- Physical: bits (0 / 1)
- Data link: bits => frames, Ethernet & LAN (Local Area Network)
- Network: IP & WAN (Wide Area Network)
- Transport: TCP & UDP
- Session: DNS
- Presentation: 
- Application: HTTP & FTP

----

##### **HTTP**(S): Hyper Transport (or Transfer) Protocol (Secure);

- Port: HTTP=80, HTTPS=443
- Request Components:


<img src="HttpRequest.png" height="65%" width="65%">

* Status Code:

<img src="StatusCode_1.png" height="65%" width="65%">

<img src="StatusCode_2.png" height="65%" width="65%">



----

##### **Web Server Software**

One of the most common stack: LAMP

* Linux + Apache + MySQL + PHP

<img src="WebServerSoftware.png" height="65%" width="65%">



# **Project Management**

**Process**:  Identify Problem <problem statement> 👉 Determine Use Cases <Action & Actors> 👉 Wireframes<UI & UX design> 👉  Software Requirement Specification<SRS> 

**What's in a Use Case Documentation**:

<img src="UseCase.png" height="65%" width="65%">

**Sequence Diagram**: 

* Useful for communicating how serveral systems interact.
* Shows how objects operate with another by time sequence. 

**State & Flow Diagram**:

* Useful for communicating how abstract concepts progress through the system
* Explain a state machine.

**SRS**: 

* Specifies the scope of the project <= checks when project is finished & prevents scope creep. 
* <u>Components</u>:
  * Introduction: business recognition; overall assessment of the project necessity
  * Overall Description: System structure (brief) + Dependencies + Constraints
  * Specific Requirements: Functional & Non-Functional requirements + other highly granular requirements. 

# **Web Servers and Application Architecture**



> [What is the difference between application server and web server????](http://stackoverflow.com/questions/936197/what-is-the-difference-between-application-server-and-web-server)

##### **Two Ubiquitous Stacks**

| LAMP       | LEMP      |
| ---------- | --------- |
| Linux      | Linux     |
| **Apache** | **Nginx** |
| MySQL      | MySQL     |
| PHP        | PHP       |

**ASP**: Active Server Pages

**<u>WSGI</u>**: [Web Server Gateway Interface](https://ruslanspivak.com/lsbaws-part2/).

* It was created as a ***<u>low-level interface between web servers and web applications</u>*** or frameworks to promote common ground for portable web application development..
* If an application (or framework or toolkit) is written to the WSGI spec then it will run on any server written to that spec 

<img src="WSGI.png" height="50%" width="50%">

**Relational Database**: enforcing and maintaining relationships, MySQL + PostgreSQL + SQLite

**Non-relational Database** (NoSQL): storing data like pages,  MongoDB (document based), Redis (K-V based), Cassandara (Column based) …. 

* Redis is useful for rapidly changing data with a foreseeable database size 
* MongoDB is good for dynamic queries / defining indexes. 

| <img src="SingleServer.png">          | <img src="SeparateDbServer.png">         |
| ------------------------------------- | ---------------------------------------- |
| 👆 Web/App/Database Server all in ONE | 👆 Increase security; No contention  by App Server; But more complex and less independent on network connection |
| <img src="LoadBalancer.png">          | 👈  Useful for horizontal scaling; Imposing a single point of failure; LB can become the performance bottleneck; |
| <img src="SlaveMasterServer.png">     | 👈 Brings great performance Improvement on database system that performs <u>many reads compared to writes</u>; Additional attention to asynchronous issues |