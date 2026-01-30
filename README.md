# C# Web API Practice Project

My first backend project for learning MVC architecture and integrating external APIs with ASP.NET Core.

## Learning Goals

- **MVC Layered Architecture**: Controller → Logic → Repository separation
- **Dependency Injection**: Using ASP.NET Core built-in DI Container
- **External API Integration**: Google OAuth 2.0 authentication
- **JWT Authentication**: Token generation and validation
- **Firebase Firestore**: NoSQL database operations

## Project Structure

```
├── Controllers/          # API endpoints
│   ├── AuthController    # Google login
│   └── TestController    # Test endpoints
│
├── LogicLayer/           # Business logic
│   ├── LoginLogic        # Google token validation
│   └── AccountLogic      # Account handling
│
├── DataLayer/
│   ├── Models/           # DTOs
│   └── Repositories/     # Data access (Firebase)
│
├── Providers/            # External services
│   └── Firebase/         # Firestore connection
│
├── Extensions/           # Extension methods
│   ├── DependencyInjection  # DI registration
│   └── JwtService           # JWT service
│
└── Settings/             # Config models
```