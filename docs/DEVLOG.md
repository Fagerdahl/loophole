# Project Loophole

A standalone microservice that handles booking logic for Vörderåsgården in Sälen.  
WordPress acts only as a presentation layer.  
Loophole is responsible for all business logic, rules, validation and data storage.

The goal is to:
- Isolate logic away from WordPress
- Improve security
- Provide a clean API for booking workflows
- Enable future features like pricing rules, capacity planning and external integrations
- Provide the costumers a smooth administration panel

In this project, Loophole will become a standalone booking service with its own:
business logic, validation, rules, database and API contract.

WordPress will act only as a frontend client consuming this API.

## Development rulesets 
- Conventional commits (Feat, Chore, Fix, Style)
- Work in dev-branch to protect main

## Tech Stack
- Java 21
- Spring Boot 3.x (Web, Data JPA, Validation, Security)
- PostgreSQL + Flyway
- Thymeleaf (Admin UI)
- Bootstrap (UI layout)
- WordPress (frontend, server-side integration via wp_remote_post)
- REST API (JSON)

## Architecture Overview
Loophole consists of two major parts:
1. **Public Website (WordPress at Loopia)**
    - Renders UI and booking form
    - Sends booking requests server-side to Loophole API via `wp_remote_post`.

2. **Loophole Booking Service (Spring Boot)**
    - Handles availability checks
    - Creates bookings
    - Stores data in PostgreSQL
    - Provides admin UI (Thymeleaf) for room & pricing management
    - Secured with Spring Security

# How I Intend to Apply Object-Oriented Design Principles in the Loophole Booking System

Since the Loophole booking system has not yet been implemented, 
this section describes how the system will be designed and built according to 
fundamental Object-Oriented Design (OOD) principles.
These principles guide the transition from requirements -> design -> 
implementation and ensure that the final solution becomes maintainable, secure and scalable.

### 1. Abstraction — modelling real-world concepts clearly

I will apply abstraction by identifying the essential concepts in the booking domain and modelling them as meaningful objects:

Booking, Guest, Room, Season, PriceRule, User, etc.

Each class will represent a real-world concept without exposing unnecessary technical details.
This abstraction allows the system to reflect the real behaviour of a guesthouse while staying clean and easy to understand.

### 2. Encapsulation: protecting internal data
Encapsulation will be enforced by:
Giving each class private fields with controlled access (getters/setters).
Keeping business logic inside service classes 
instead of controllers or database layers.
Protecting sensitive data, such as admin passwords and guest information, 
through hashing and secure APIs.
Encapsulation will ensure the internal state of objects cannot be misused from outside.

### 3. Modularity: structuring the system into purposeful units
I will divide the Spring Boot application into clear modules:
controller (API endpoints)
service (business rules)
repository (database access)
model (domain entities)
security (authentication and API key validation)
exception (central exception handling)
This modular structure will allow each part of the system to evolve independently.

### 4. Separation of Concerns: keeping responsibilities apart
Responsibilities will be separated across layers and technologies:
WordPress (Loopia) will handle the public interface for guests.
Spring Boot will handle booking logic, validation and data storage.
Thymeleaf will provide the admin interface for the customer.
PostgreSQL will store structured booking information.
By separating concerns, the system becomes easier to maintain and understand.

### 5. Low Coupling: reducing unnecessary dependencies
I plan to minimize coupling by:
Using REST APIs between WordPress and Spring Boot (no shared code).
Using interfaces and dependency injection within the backend.
Keeping admin UI and guest-facing UI independent of each other.
Ensuring the database layer is accessed only via repositories.
Low coupling will make the system flexible and adaptable to future changes.

### 6. High Cohesion: keeping related logic together
To achieve high cohesion:
Each service class will contain logic related to ONE domain concept only.
For example, BookingService handles booking logic, 
RoomService handles rooms, and so on.

Each domain model class will represent one concept without mixing unrelated logic.
This increases readability and prevents bloated classes.

### 7. Reusability: preparing for future extensions
Because the booking system may grow over time, 
I will design components to be reusable:
Price rules and seasons are separate concepts, allowing dynamic pricing in the future.

The API will be designed so that a mobile app or external booking 
channel can be added later.
Room types and capacity rules can be extended without 
rewriting booking logic.
This prepares the system for expansion without major refactoring.

### 8. Applying the OOD Pyramid: methodology from requirements to code
The entire project is structured according to the OOD Pyramid, 
which ensures a logical progression through design steps:

_Level 1: Requirements_
Functional and non-functional requirements have been defined for guest booking, cancellations, admin management, pricing, performance, and security.

_Level 2: Use Cases_
Five primary use cases describe how guests and admins will interact with the system.

_Level 3: Domain Model (Class Diagram)_
I have created a domain-level class diagram showing key objects and relationships, which will guide both implementation and database structure.

_Level 4: Detailed Design_
Before coding begins, I have prepared:
* Sequence Diagram (for booking flow from WordPress → API → DB)
* Activity Diagram (decision logic for booking)
* Architecture Diagram (overall system components)
* Package Diagram (Spring Boot structure)
* ER Diagram (database design)
* Deployment Diagram

These diagrams will serve as the blueprint for implementation.

## Conclusion
Although the application has not yet been implemented, 
the project follows a clear and systematic Object-Oriented Design process.
