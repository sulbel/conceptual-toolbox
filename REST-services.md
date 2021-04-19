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
  * Self-links *and* links to the aggregate root/top level
* What is the point of all these links?
  * It makes it possible to evolve REST services over time.
  * Existing links can be maintained while new links can be added in the future
  * Newer clients may take advantage of the new links, while legacy clients can sustain themselves on the old links

### Evolving REST APIs
An important facet of REST is the fact that it's neither a technology stack nor a single standard.
* REST is a collection of architectural constraints that when adopted make your application much more resilient.
  * A key factor of resilience is that when you make upgrades to your services, your clients don't suffer from downtime.

#### Supporting changes to the API
Suppose the need for splitting a single `name` attribute into 2 attributes, `firstName` and `lastName` arises.
* Straight up replacing the `name` attribute may break clients, causing downtime and lost revenue
  * "Never delete a column in a database"
  * We can always add columns/fields
* Add new fields to the JSON representations, but don't take any away
  * This duplication supports both new clients and old clients
  * Can upgrade the server without requiring clients to upgrade at the same time

# HTTP Codes
Code | Meaning
-----|---------
200 | OK
201 | Created
204 | No content
405 | Method not allowed

