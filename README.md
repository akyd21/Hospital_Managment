# Hospital Management System

Hospital Management System is a Spring Boot REST API project for managing patients, doctors, appointments, and authentication with role-based access control.

## Overview

This project demonstrates a practical backend architecture using:

- Spring Web for REST APIs
- Spring Data JPA for persistence
- Spring Security with JWT authentication
- OAuth2 login support
- MySQL as the database

The API is exposed under the base context path:

- /api/v1

## Tech Stack

- Java 21
- Spring Boot 3.5.3
- Spring Data JPA
- Spring Security
- Spring OAuth2 Client
- JWT (jjwt)
- MySQL
- Lombok
- ModelMapper
- Maven

## Core Features

- User signup and login
- JWT token-based authentication
- OAuth2 login integration flow
- Role-based authorization (ADMIN, DOCTOR, PATIENT)
- Public doctors listing API
- Patient appointment creation
- Doctor appointments listing
- Admin patient listing with pagination
- Admin doctor onboarding

## Project Structure

- src/main/java/com/codingshuttle/youtube/hospitalManagement/controller : REST controllers
- src/main/java/com/codingshuttle/youtube/hospitalManagement/service : business logic
- src/main/java/com/codingshuttle/youtube/hospitalManagement/repository : JPA repositories
- src/main/java/com/codingshuttle/youtube/hospitalManagement/entity : entities and enums
- src/main/java/com/codingshuttle/youtube/hospitalManagement/security : JWT, OAuth2, and security configuration
- src/main/java/com/codingshuttle/youtube/hospitalManagement/dto : request/response DTOs
- src/main/resources/application.properties : app configuration
- src/main/resources/data.sql : sample seed data

## Security and Access Rules

### Public Routes

- /public/**
- /auth/**

### Protected Routes

- /admin/** : requires ADMIN role
- DELETE /admin/** : requires appointment:delete or user:manage authority
- /doctors/** : requires DOCTOR or ADMIN role
- other routes: authenticated access required

### Roles

- ADMIN
- DOCTOR
- PATIENT

### Permissions

- patient:read
- patient:write
- appointment:read
- appointment:write
- appointment:delete
- user:manage
- report:view

## API Endpoints

### Auth

- POST /api/v1/auth/login
- POST /api/v1/auth/signup

### Public

- GET /api/v1/public/doctors

### Patient

- POST /api/v1/patients/appointments
- GET /api/v1/patients/profile

### Doctor

- GET /api/v1/doctors/appointments

### Admin

- GET /api/v1/admin/patients?page=0&size=10
- POST /api/v1/admin/onBoardNewDoctor

## Database Configuration

Configured database settings in application.properties:

- spring.datasource.url=jdbc:mysql://localhost:3306/hospitalDB
- spring.jpa.hibernate.ddl-auto=create
- spring.jpa.show-sql=true

Before running, set:

- spring.datasource.username
- spring.datasource.password
- jwt.secretKey

## Seed Data

The project includes sample data in data.sql:

- 5 patients
- 3 doctors
- 6 appointments

If you want automatic seed execution, enable the SQL init properties in application.properties.

## Run the Project

1. Create MySQL database named hospitalDB.
2. Update datasource username and password in application.properties.
3. Start the app.

### Windows

mvnw.cmd spring-boot:run

### Linux or macOS

./mvnw spring-boot:run

## Build and Test

### Build

mvnw.cmd clean package

### Run Tests

mvnw.cmd test

## Important Notes

- Current schema strategy is create, so tables are recreated at startup.
- OAuth2 login flow exists in security, but provider credentials must be configured for actual provider use.
- Patient profile endpoint currently uses fixed patient lookup logic in controller and may be updated to resolve authenticated patient dynamically.
