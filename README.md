# AuthShield

A robust Spring Security implementation with advanced JWT authentication and OAuth2 integration.

## Features

- **JWT Authentication**: Secure token-based authentication system
- **OAuth2 Support**: Seamless login with Google, GitHub, and other providers
- **Role-Based Access Control**: Fine-grained permission management
- **Stateless Session Management**: Enhanced security with no server-side sessions
- **Customizable Security Configuration**: Adaptable to various application needs

## Technology Stack

- Java 17
- Spring Boot 3.2.3
- Spring Security 6.x
- Spring Data JPA
- H2 Database (configurable for production databases)
- JWT for token-based authentication
- OAuth2 for social login

## Project Structure

```
├── src/main/java/com/authshield/security/
│   ├── config/              # Security configuration classes
│   ├── controller/          # REST API endpoints
│   ├── dto/                 # Data Transfer Objects
│   ├── entity/              # JPA entities
│   ├── exception/           # Custom exceptions
│   ├── filter/              # JWT authentication filters
│   ├── handler/             # Auth success/failure handlers
│   ├── repository/          # Spring Data JPA repositories
│   ├── service/             # Business logic services
│   └── util/                # Utility classes
├── src/main/resources/
│   ├── application.yml      # Application configuration
│   └── templates/           # HTML templates (if any)
├── src/test/               # Test classes
└── pom.xml                 # Project dependencies
```

## Getting Started

### Prerequisites

- JDK 17+
- Maven 3.8+
- OAuth2 provider credentials (Google, GitHub, etc.)

### Configuration

1. Clone the repository:
```bash
git clone https://github.com/nehashukla13/auth-shield.git
cd auth-shield
```

2. Configure OAuth2 credentials:
   - Create application credentials on Google Cloud Console and GitHub Developer Settings
   - Update `application.yml` with your client IDs and secrets or set environment variables

3. Set JWT secret:
```bash
export JWT_SECRET=your_secure_secret_key
```

### Running the Application

```bash
mvn spring-boot:run
```

The application will be available at `http://localhost:8080`

## API Documentation

### Authentication Endpoints

- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login and receive JWT token
- `GET /api/auth/me` - Get current user information

### OAuth2 Endpoints

- `GET /oauth2/authorize/google` - Initiate Google authentication
- `GET /oauth2/authorize/github` - Initiate GitHub authentication

### Protected Resources

All endpoints outside of `/api/auth/**` and `/oauth2/**` require authentication.

## Security Features

- JWT tokens are valid for 24 hours by default (configurable)
- Passwords are encrypted using BCrypt with adaptive difficulty
- CSRF protection configuration options
- Built-in protection against common security vulnerabilities
- Token refresh mechanisms

## Production Considerations

- Use environment variables for sensitive information
- Enable HTTPS in production
- Configure proper CORS settings
- Consider implementing rate limiting

## License

This project is licensed under the MIT License - see the LICENSE file for details.
