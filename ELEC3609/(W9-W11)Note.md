# Cloud Services

**"Cloud"**: the collection of software services, hardware, network, storage …. 

**Cloud Types**:

* **IaaS**: Infrastructure as Service (hosting)
* **PaaS**: Platform as Service (building). Eg, AWS Relational Database Service. 
* **SaaS**: Software as Service (consuming). Everything above are combined in this. 

TO BE CONTINUED … (If I have time 😁)


# Web Security

## **It's about HACKING and ANTI-HACKING!**

**Axiom of Information Security （snippet）**:

* All systems are buggy <= folks always find ways to hack your system
* Nothing works in isolation <= isolate your system well!
* Humans are most often the weakest link <= don't do stupid things and follow the best practice!

**What is a 'System'?** Anything from a product/component to infrastructure, applications or users… <= each has its security weaknesses! 

[**OWASP**](https://www.owasp.org/index.php/About_OWASP): these guys are there to educate you why systems are hacked and how to prevent it from happening. 

## Vulnerabilities, Vulnerabilities everywhere! 

| ATTACK          | WHY & WHAT                               | mitigation                          |
| --------------- | ---------------------------------------- | ----------------------------------- |
| SQL Injection   | 🔹Failing to sanitise user input before inserting it into DB string; 🔸Triggers malicious SQL query running on server | Sanitisation; Parameteized queries  |
| XSS             | 🔹Failing to sanitise +1 🔸 Triggers malicious code to run on user browser; Reason of Cookie leaks | Transpile HTML syntax in user input |
| CSRF            | 🔹Failing to verify the source of request 🔸Fools user browser to send unauthorised requests with auth cookies (on when user stays authenticated) | Check CSRF token per request        |
| File Inclusion  | 🔹Allowing users to govern what files can be included 🔸Fools the server to respond with server files. | TODO                                |
| Remote Code Exe | The worst type of exploit! The injected code can do anything on server | TODO                                |

## **Password Protection**

**Hashing** is a A common way to <u>*not string plain text password*</u>s on server to minimise the danger of  password database leakage. 

* **Hash Function**: One way + Unpredictable + Non-collision
* **Salting**: instead of  H(password), use H(<u>***salt***</u> || password). This makes *pre-computed dictionary (like [Rainbow table](https://www.zhihu.com/question/19790488)) attack* harder as each encrypted password is a result of deviated hashing, so the same dict does not apply for all. 

**Authentication Cookies** is a means for post-loggingin authentication. 

* **Statefully**: Valid token is stored in server <= a burden on database; more DB hits; hard to modify auth rules. 
* **Statelessly**: Client still stores the token, but the server validates by re-calculating the token using *hash(secret || validity_ts || user_id)*.  <= <u>trade space for time</u>. 

**Managing Cookies**: HTTPS (no HTTP) + [SecureFlag attribute](https://www.owasp.org/index.php/SecureFlag) + [HttpOnly attribute](https://www.owasp.org/index.php/HttpOnly)