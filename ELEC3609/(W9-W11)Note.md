# Cloud Services

**"Cloud"**: the collection of software services, hardware, network, storage …. 

**Cloud Types**:

* **IaaS**: Infrastructure as Service (hosting)
* **PaaS**: Platform as Service (building). Eg, AWS Relational Database Service. 
* **SaaS**: Software as Service (consuming). Everything above are combined in this. Full stack. 

**Why Clouding??**

| PROS                               | CONS                                     |
| ---------------------------------- | ---------------------------------------- |
| Easy to run and maintain           | Data security                            |
| Reliable/scalable storage/hardware | Maturity of Cloud Products (潜在之坑)        |
| CHEAPPPPPPPERRRRRRR                | Comparing cost between providers is difficult |




# Web Security

## **It's about HACKING and ANTI-HACKING!**

**Axiom of Information Security （snippet）**:

* All systems are buggy <= folks always find ways to hack your system
* Nothing works in isolation <= isolate your system well!
* Humans are most often the weakest link <= don't do stupid things and follow the best practice!

**What is a 'System'?** Anything from a product/component to infrastructure, applications or users… <= each has its security weaknesses! 

[**OWASP**](https://www.owasp.org/index.php/About_OWASP):  (Open Web Application Security) these guys are there to educate you why systems are hacked and how to prevent it from happening. 

## Vulnerabilities, Vulnerabilities everywhere! 

| ATTACK          | WHY & WHAT                               | mitigation                          |
| --------------- | ---------------------------------------- | ----------------------------------- |
| SQL Injection   | 🔹Failing to sanitise user input before inserting it into DB string; 🔸Triggers malicious SQL query running on server | SanitisationParameteized queries    |
| XSS             | 🔹Failing to sanitise +1 🔸 Triggers malicious code to run on user browser; Reason of Cookie leaks | Transpile HTML syntax in user input |
| CSRF            | 🔹Failing to verify the source of request 🔸Fools user browser to send unauthorised requests with auth cookies (on when user stays authenticated) | Check CSRF token per request        |
| File Inclusion  | 🔹Allowing users to govern what files can be included 🔸Fools the server to respond with server files. | TODO                                |
| Remote Code Exe | The worst type of exploit! The injected code can do anything on server | TODO                                |

## **Password Protection**

**Hashing** is a a common way of <u>*not storing plain text password*</u>s on server to minimise the danger of  password database leakage. 

* **Hash Function**: One way + Unpredictable + Non-collision
* **Salting**: instead of  H(password), use H(<u>***salt***</u> || password). This makes *pre-computed dictionary (like [Rainbow table](https://www.zhihu.com/question/19790488)) attack* harder as each encrypted password is a result of deviated hashing, so the same dict does not apply to all. 

**Authentication Cookies** is a means for post-loggingin authentication. 

* **Statefully**: Valid token is stored in server <= a burden on database; more DB hits; hard to modify auth rules. 
* **Statelessly**: Client still stores the token, but the server validates by re-calculating the token using *hash(secret || validity_ts || user_id)*. Only the server can calculate the token as the secret info is stored at server side <= <u>trade space for time</u>. 

**Managing Cookies**: HTTPS (no HTTP) + [SecureFlag attribute](https://www.owasp.org/index.php/SecureFlag) + [HttpOnly attribute](https://www.owasp.org/index.php/HttpOnly)

# Pre-Packaged Software

> **Packages** typically consists of: Application Code, Configuration Files* and tDatabase*

## Choose the package

<u>*Evaluate*</u> and understand other people's software before making your mind to use it. 

* ***Identify other users***: do other giants like it?
* ***Identify potential support avenues***: how active is community? how responsive is the dev team? 
* ***Check for the frequency of commits***: Is development active?
* ***Scan for vulnerabilities***: the code is also public to attackers :D.

## Configure the package

Figure out what are the configuration <u>*options*</u> prior to deployment

* ***Look through all config options***: don't miss out features;
* ***Search the internet for example configs***: what did other do and find about the config?
* ***Identify all features***
* ***Disable unwanted feature***: to reduce complexity and surface for possible attack

## Setup the Database

Checkpoints are:

* ***Identify database requirements***
* ***Identify database permission***: app should be given minimum set of permissions to run <= AVOID GRANTING ROOT ACCESS!
* ***Evaluate the scope of DB compromise***: DB commands that can run system commands should be locked down if possible
* ***Keep the connections local***: just the app running on local machine should manage the DB.

## Deploy the Pre-packaged Software

**Use RP** (reverse proxy) for the sake of ***scaling***, ***request auth*** (e.g, access to internal services should be blocked) and ***web app firewalls*** (requests are assessed before accepted; *<u>NAXSI</u>* is an good one 😀)

## **Docker** - Build, Ship, Run … 

> Docker is an open-source project to automate the deployment of
> applications inside <u>linux containers</u>

**What is the Linux Container in Docker?** instead of running many virtual OS, containers can be used as a lightweight solution for the need of isolated environments. 

* You can think of a docker container as it's own ***minimalistic Linux hos**t* based off a ***docker image***
* Similar to 'Volumes' as to 'Instances' in AWS, data storage segregation can be achieved by ***mounting volumes*** onto docker containers. 
* Containers can be ***linked*** and have certain *ports* forwarded (similar to how instances are linked in same AWS AZ?)
* ***Docker Hub*** is the pool of pre-built images 👏

## Monitoring - How are we going today 😳?

**Infrastructure Monitoring**: for instances, Network traffic, Server performance… [ Nagios, Graphite ]

**Error Monitoring**: collects errors from website and consolidates them [Sentry]

**User Monitoring**: collects user information; inference user behaviours … [G. Analytics, Kissmetrices]

**Custom Tracking**: Make own monitoring system to better suit your system. 