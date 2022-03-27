# Building a Backend Service in Go

## Contents
- Overview
- Caveats
- Planning
  - Requirements
  - Architecture
- Execution
  - API Documentation
  - Models
  - Service
  - Server
  - Integration
- Bonus
  - Containerization using Docker
  - Automation with Makefile
  - Project documentation

## Overview
This project is an attempt to discover and articulate best practices for creating a backend-service in Go.
The [Course Manager Service](https://github.com/tomasdembelli/course-manager) will be used as an example for explaining 
the objectives.

## Caveats
Running backend services behind an 
[API gateway](https://docs.microsoft.com/en-us/azure/architecture/microservices/design/gateway#what-is-an-api-gateway) 
and giving the user authentication to it is a very common practice. 
Therefore, we won't be investigating user management in this document.

## Planning
Poor planning will cost very expensive correction operations as the project grows.

### Requirements
The mission of the service should be clarified with the stakeholders.

### Architecture
A diagram showing the separation of concerns, and the relation of the entities undertaking these concerns will help
to make crucial decisions at an early stage. This will also enable sharing the work between team members.

## Execution