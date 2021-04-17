REST has quickly become the de-facto standard for building web services on the web because they're easy to build and easy to consume.

# Why REST?
REST embraces the precepts of the web, including its architecture, benefits, and everything else.  The web and its core protocol, HTTP, provide a stack of features:
* Suitable actions such as `GET` `POST` `PUT` `DELETE`
* Caching
* Redirection and forwarding
* Security measures such as encryption and authentication

By building on top of HTTP, REST APIs provide the means to build:
* Backwards compatible APIs
* Evolvable APIs
* Scaleable services
* Securable services
* A spectrum of stateless to stateful services

REST is not a standard, per se, but **an approach**, a style, a set of constraints on your architecture that can help you build web-scale systems.

# What makes something RESTful?
"What needs to be done to make the REST architectural style clear on the notion that hypertext is a constraint? In other words, if the engine of application state (and hence the API) is not being driven by hypertext, then it cannot be RESTful and cannot be a REST API. Period. Is there some broken manual somewhere that needs to be fixed?" - Roy Felding

* The side effect of **not** including hypermedia in representations, is that clients *MUST* hard code URIs to navigate the API.
* A critical ingredient to any RESTful service is adding links to relevant operations.
  * Without links, a service that implements CRUD, uses `GET` `POST`, etc, is better described as **RPC (Remote Procedure Call)**
* What is the point of all these links?
  * It makes it possible to evolve REST services over time.
  * Existing links can be maintained while new links can be added in the future
  * Newer clients may take advantage of the new links, while legacy clients can sustain themselves on the old links