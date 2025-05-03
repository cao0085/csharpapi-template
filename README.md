# C# API Framework with JWT, Google OAuth 2.0, and FirebaseDB

This project provides a ready-to-use C# API framework for account authentication using JWT tokens and Google OAuth 2.0, with Firebase as the backend database.

---

## Configuration

### 1. `appsettings.json` / `appsettings.Development.json`

Fill your Google OAuth 2.0 credentials and configure your CORS policy as follows:

```json
"GoogleLogicAuth": {
  "ClientId": "your-google-client-id"
},
"Cors": {
  "AllowOrigins": [
    "your-allowed-origin-urls"
  ]
}
```

### 2. Environment Variables (`.env`)

When you run your application, the program will automatically load sensitive parameters from your `.env` file into the configuration.

Example `.env` file:

```
JWT_KEY=your-random-generated-key
JWT_ISSUER=your-jwt-issuer
JWT_AUDIENCE=your-jwt-audience
FIREBASE_KEY_PATH=/path-to-your-firebase-json-file
FIREBASE_PROJECT_ID=your-firebase-project-id
```

These values will map to your `appsettings` like this:

```json
"FirebaseConfig": {
  "ProjectId": "",
  "ServiceAccountKeyPath": ""
},
"Jwt": {
  "Key": "",
  "Issuer": "",
  "Audience": ""
}
```

The mapping in your `Program.cs`:

```csharp
var envToConfigMap = new Dictionary<string, string>
{
    { "JWT_KEY", "Jwt:Key" },
    { "JWT_ISSUER", "Jwt:Issuer" },
    { "JWT_AUDIENCE", "Jwt:Audience" },
    { "FIREBASE_PROJECT_ID", "FirebaseConfig:ProjectId" },
    { "FIREBASE_KEY_PATH", "FirebaseConfig:ServiceAccountKeyPath" },
};
```

---

## Docker Commands

Build your Docker image:

```bash
docker build -t YourProjectName .
```

### Run in Development Mode

The development mode will read `.env` from `/root/.env` by default:

```bash
docker run -p 8080:8080 YourProjectName
```

### Run in Production Mode

In production mode, specify environment explicitly:

```bash
docker run \
  --env-file .env.production \
  -e ASPNETCORE_ENVIRONMENT=Production \
  -p 8080:8080 YourProjectName
```

---

## Testing

### Check if server is online

```
http://localhost:8080/api/test/test
```

### Verify environment setup and authentication via Google OAuth 2.0

Note: Your frontend application needs to include a token in the request. <br>
Note: Your frontend application needs to include a token in the request. <br>
Note: Your frontend application needs to include a token in the request. <br>

```
http://localhost:8080/api/auth/google
```
Note: Your frontend application needs to include a token in the request. <br>
Note: Your frontend application needs to include a token in the request. <br>
Note: Your frontend application needs to include a token in the request. <br>


this csharp application will:

* Receive the token from your frontend application.
* Use Google OAuth 2.0
* Create account data in FirebaseDB
* Return authentication result

---
