# Spring
Spring is a framework that makes Java Application development quick and painless.  

## Spring Boot
Spring boot is built on top of the Spring framework, and automates much of the configuration for Spring projects.  By using the tool at https://start.spring.io/ and selecting the relevant dependencies, a package can be created and downloaded to jumpstart much of the tedious configuration, allowing a developer to focus writing code.

## Spring Data
The Spring Data `JpaRepository` makes CRUD operations extremely simple.  By declaring an interface which extends the `JpaRepository` and declaring a domain type and id type, Spring will handle all of the implementation details. Example:

`package payroll;`

`import org.springframework.data.jpa.repository.JpaRepository;`

`interface EmployeeRepository extends JpaRepository<Employee, Long> {`

`}`

## Spring MVC
For wrapping spring projects (like a data repository) with a web layer
* `ResponseEntity` creates a status message, which typically includes a **location** response header

## Spring HATEOAS
A Spring project aimed at helping you write hypermedia-driven outputs
* EntityModel<> is a generic container from Spring HATEOAS that includes not only data, but also a collection of links
* CollectionModel<> is another HATEOAS container; it is aimed at **encapsulating collections** of resources, instead of a single resource entity like EntityModel<>.
  * **IMPORTANT** - encapsulates collections of **resources** 
* Instead of clients parsing the payload, give them links to signal valid actions. Decouple state-based actions from the payload of data. In other words, when CANCEL and COMPLETE are valid actions, dynamically add them to the list of links. Clients only need show users the corresponding buttons when the links exist.
  * This decouples clients from having to know WHEN such actions are valid, reducing the risk of the server and its clients getting out of sync on the logic of state transitions.