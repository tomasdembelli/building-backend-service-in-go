# Building a Backend Service in Go


## Overview
This document lays out the required steps for creating a backend service in Go.
The [Course Manager Service](https://github.com/tomasdembelli/course-manager) will be used for demonstrating the key points.

Running backend services behind an 
[API gateway](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/gateway#what-is-an-api-gateway) 
and giving user authentication to it is a very common practice. 
Therefore, we won't be investigating user management in this document.

## Contents
- [Planning Phase](#planning-phase)
  - [Gathering Requirements](#gathering-requirements)
  - [Architecture](#architecture)
- [Execution](#execution)
  - [API Documentation](#api-documentation)
  - [Models](#models)
  - [Service](#service)
  - [Server](#server)
  - [Integration](#integration)
- [Bonus](#bonus)
  - [Containerization](#containerization)
  - [Automation](#automation)
  - [Project documentation](#project-documentation)

## Planning Phase
Poor planning will cost very expensive correction operations as the project grows.

### Gathering Requirements
The mission of the service should be clarified with the stakeholders.

### Architecture
A diagram showing the separation of concerns, and the relation of the entities undertaking these concerns will help
to make crucial decisions at an early stage. This will also enable sharing the work between team members.

## Execution

### API Documentation
Creating the API document upfront will:
- help visualize the end product,
- unblock development of other services depending on our backend service, i.e. a front-end consumer application,
- enable creating more detailed tasks and sharing the work between team members.

[OpenAPI Specifications](https://spec.openapis.org/oas/latest.html) (OAS) is one of the most common interface description standards for HTTP APIs.

### Models
Models are the definitions of the objects that are used to realize business logic.
For a bank application, possible models would be `account`, `user`, etc.
The API specs could dictate, or, at least, be a starting point when designing the models' structures.

### Service
Service is where the entire business logic lives, which should NOT leak into any other part of the code, i.e, models, DB client.
The Service should be technology-agnostic. That means that it should not care how data persists i.e. type of DB/messaging/caching.
For that, Go provides [interfaces](https://go.dev/tour/methods/9).
It also makes mocking the tools, that service depends on, a very simple task.
This allows testing the Service without running the actual dependencies.

### Server
Go standard library provides an [HTTP server](https://pkg.go.dev/net/http).
However, there are some third-party web frameworks as well, i.e, [echo](https://echo.labstack.com/).

### Integration
This is where the Service is connected to the actual dependencies, such as DB/caching/messaging clients, and runs within a web server.

## Bonus
The followings are necessary for the efficient development and maintenance of the project.

### Containerization
[Docker](https://www.docker.com/) is the most common technology used.

### Automation
This might have different meanings depending on where it is used.
In this context, it refers to automating processes that are run frequently.
For example, building the application or running the tests.
Apart from convenience, it also enables standardization across the team, i.e., using the same flags when testing.

### Project Documentation
How to build/start the application, what the dependencies are, etc. should be well documented.
Documentation helps to share the knowledge within the team. 
It also gives information about the product to the stakeholders outside the technical team.
