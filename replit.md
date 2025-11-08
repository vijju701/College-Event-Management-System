# College Events Management System

## Overview
A Java Spring Boot web application for managing college events. Students can register for events, and administrators can create, manage, and approve events. The application features user authentication, event registration, and an admin dashboard for comprehensive event management.

## Features
- User registration and authentication (Student & Admin roles)
- Event creation and management
- Event registration system with approval workflow
- Admin dashboard with statistics and reports
- File upload for event images
- Responsive UI with modern design

## Technology Stack
- **Backend**: Spring Boot 3.5.7 (Java 17)
- **Database**: PostgreSQL (Replit Database)
- **ORM**: Hibernate/JPA
- **Template Engine**: Thymeleaf
- **Build Tool**: Maven
- **Frontend**: Bootstrap 5.3.2, Custom CSS

## Project Structure
```
src/
├── main/
│   ├── java/com/example/sb/demo/
│   │   ├── controller/      # REST controllers
│   │   │   ├── AdminController.java
│   │   │   ├── AuthController.java
│   │   │   ├── EventController.java
│   │   │   └── UserController.java
│   │   ├── dto/             # Data Transfer Objects
│   │   ├── entity/          # JPA entities
│   │   │   ├── Event.java
│   │   │   ├── Registration.java
│   │   │   └── User.java
│   │   ├── repository/      # JPA repositories
│   │   ├── service/         # Business logic
│   │   └── DemoApplication.java
│   └── resources/
│       ├── static/          # CSS, JS, images
│       ├── templates/       # Thymeleaf templates
│       └── application.properties
└── test/
```

## Recent Changes (Replit Import Setup)
**Date**: November 8, 2025

### Database Migration
- Migrated from MySQL to PostgreSQL for Replit compatibility
- Updated `pom.xml` to use PostgreSQL driver
- Configured database connection using Replit environment variables:
  - `PGHOST`, `PGPORT`, `PGDATABASE`, `PGUSER`, `PGPASSWORD`

### Server Configuration
- Configured server to run on port 5000 (Replit standard)
- Set server address to `0.0.0.0` for proper Replit proxy support
- Updated Hibernate dialect to `PostgreSQLDialect`

### Build Fixes
- Removed duplicate constructors in service classes (EventService, RegistrationService)
- Fixed Lombok `@RequiredArgsConstructor` conflicts

### Deployment
- Configured deployment for Replit autoscale
- Build command: `./mvnw clean package -DskipTests`
- Run command: `java -jar target/demo-0.0.1-SNAPSHOT.jar`

## Database Schema
The application uses three main tables:
- **users**: Student and admin user accounts
- **events**: College events with details, venue, dates
- **registrations**: Event registration records linking users to events

## Getting Started

### Prerequisites
- Java 17 or higher
- Maven
- PostgreSQL database (automatically configured in Replit)

### Running the Application
The application runs automatically via the "Spring Boot App" workflow. To manually start:
```bash
./mvnw spring-boot:run
```

### First Time Setup
1. Register an admin account at `/admin/register`
2. Login at `/login`
3. Create events from the admin dashboard
4. Students can register at `/register` and view/join events

## User Roles
- **ADMIN**: Can create events, approve registrations, view reports, manage users
- **STUDENT**: Can view events, register for events, manage their registrations

## Key Endpoints
- `/` - Home page with upcoming events
- `/login` - User login
- `/register` - Student registration
- `/admin/register` - Admin registration
- `/events` - List all events
- `/events/new` - Create new event (requires login)
- `/admin/dashboard` - Admin dashboard
- `/user/home` - Student home page

## Configuration
Main configuration is in `src/main/resources/application.properties`:
- Server runs on port 5000
- Database connection via environment variables
- Session timeout: 30 minutes
- Max file upload: 10MB

## File Uploads
Event images are stored in `uploads/events/` directory.

## Notes
- Passwords are currently stored in plain text (should implement hashing for production)
- The application uses session-based authentication
- Database schema is auto-generated/updated via Hibernate
