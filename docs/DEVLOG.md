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
