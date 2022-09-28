**Title:** Arquitetura Limpa na Prática

**Author:** Otávio Lemos

## Chapter III: A Arquitetura Limpa

### Clean Architecture in frontend

_There is no reason to follow the CA concepts in depth in the frontend because the main objective is to separate the business rules (backend) from the external parts (including the backend)_ (author's opinion). A good architecture to apply in the frontend is **Humble Object**. Khalil Stemmler have been treating this topic is depth and wrote an [article in his blog](https://khalilstemmler.com/articles/client-side-architecture/introduction/) and a [continuation article](https://khalilstemmler.com/articles/typescript-domain-driven-design/ddd-frontend/).

## Chapter IV: Study Case: theWisePad

A study case of an simple notepad application using the CA principles.

### Entities

- Using _Value Objects_ to bring more behavior and complexity to the application's entities (as the entities, as well as the application domain, are very simple). In other words, all the entity properties (like user email, password, note title) are classes and its equality is given by its values instead of identities (like the same memory address)
- The data validation can be made in the external layers or directly in the entities. The first approach take off the complexity and responsibility from the entities, but it open gaps for creating entities with invalid data. I think (and the author too) that data validation (since this data is related with the application domain) must be done in the entities layer. _“Make illegal states unrepresentable!”_ (Yaron Minsky)

## Chapter VIII: Interface Adapters

- Normally, that layer contains the adapters which transform the data to and from the usecases to the more external layers, like database gateways that don't communicate with the database yet, and normally there are not framework or that type of code here.
- It's common to add the framework integrations code directly in this layer in small projects
- The adapters in this layer carries that name because of the Adapter design pattern
- The MVC (model-view-controller) can be implemented entirely in this layer
- In the study case, this layer will contains the web controllers and the middleware that verifies the access token for some API endpoint. In that point is already defined that the application will be a web API, but that adapters will be generic and framework-agnostic

## General Annotations

- The obsession for primitive types is considered a code smell. Always that is possible, try to use Value Objects
- The definition about what is a business rule (entities layer) and an application rule (application/usecases layer) is variable, depends of the application
- The Repository pattern is from _Patterns of Enterprise Application Architecture_ (Martin Fowler). Also is mentioned in the _Domain Driven Design_ (Eric Evans)
