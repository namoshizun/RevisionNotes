# Backend Web Development

#### **Data modelling**:

**Keywords**: data modelling, normalisation, ERD(entity-relationship model)

**Process**: Identifying the detailed system requirements 👉 [Normalising](https://en.wikipedia.org/wiki/Database_normalization) the entities 👉 Writing the [data model](https://en.wikipedia.org/wiki/Data_model) 

**Model**: describes the fields which hold information about a particular entity. Typically, each model has a unique key known as the <u>primary key</u>. 

*  Relationships: One <=> One / One <=> Many / Many <=> Many

**MVC Design Pattern**:

* Model: manages the data
* View: renders data into views
* Controller: interprets requests and encapsulates business logic

**ORM**: [Object-relational mapping](https://en.wikipedia.org/wiki/Object-relational_mapping) is a programming technique for converting data between incompatible type systems in OO programming languages. Models become Classes, and each instance becomes an object, on which methods can be called. 

# Client-Server interoperation

### **Concepts:**

**XML**: Extensible Markup language, is a <u>markup language</u> defines a set of rules for encoding documents. 

**DTD**: Document Type Definition; is a set of markup declarations that define a document type for an SGML-family markup language (XML, HTML...).

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML4.01//EN" "..."> 
<!-- This is an (incomplete) example of telling the browser to use HTML4, and therefore HTML4 DTD is used to check html validity -->
```

**JSON**: JavaScript Object Notation is a language-independent data encoding structure. Useful for API communications and [Serialisation](https://en.wikipedia.org/wiki/Serialization) (converting object into byte string).

### **HTTP Anatomy**:

**MIME Types**: known as the 'media type'. Server uses it to convey client browser the type of transmitted resource, so that  the browser knows which default action to do to the resource. 

- <u>Syntax</u>: type/subtype  <= defined in '***Content-Type' header***
- <u>Common ones</u>: text/html, application/json, image/png

**Referer**: tell the server how a browser arrived at a particular page.

**User-Agent**: tells the server what type of software the client is using. 

* *Syntax*:  [ Browser, Rendering Engine, OS ]
* Why? the server knows which content to choose to respond. 

**Cookies**: a small piece of temp data stored in the user's browser. 

* Cookies can authenticate the user's browser to the server <= Gotcha! a potential security breach

## **Security (*):**

**CSRF (Cross-site request forgery)**

* Happens when the *browser is authenticated* the and logged-in state maintains, then malicious website can embed code to *trigger sending unauthorised requests*. 
* **Mitigation**:
  * Embed a *<u>CSRF token</u>* in HTML resources, and the server verifies if the request is sent from trusted origin by checking the token. 
  * Set the token in cookies is not good enough, as the cookies might be stolen by XSS attack.

# **Frontend Development**

…  …  … 

**AJAX**: **A**synchronous **J**avaScript **A**nd **X**ML

* Allow the page to be updated with external data without a full refresh of the page  <= Send AJAX request to obtain the new data which is then used to update a subset of DOM. 
* jQuery is a lovely helper 😁

**Bower** - a package manager for the web <= similar to pip

**Grunt** - a Javascript task runner; does repetitive tasks such as bundle and build  <= similar to makefile

**Single Page Application**: HTML is loaded once and all updates are done via manipulation to DOM using Js !! 

* **Pros**: Smoother user experience (hardly feel the page is loading) & removes load from server & easy binding of data to the view - no need for a mess of jQuery & separation of concerns 

* **Cons**: harder to implement & may increase security risks & add burdens to browser & Slower initial page load & ***<u>SEO problem</u>*** (Google crawler only recognises the homepage and ignores the dynamically loaded components by Js)

  See this [post](http://adkgroup.com/insights/single-page-applications-spa-and-seo-problem) for why SEO problem is a major drawback 