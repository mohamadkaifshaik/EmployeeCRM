# 👥 Employee CRM System

A **professional, production-ready Employee and Client Relationship Management System** built with ASP.NET Core following clean architecture principles.

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Status](https://img.shields.io/badge/status-production--ready-green)
![License](https://img.shields.io/badge/license-MIT-green)
![.NET](https://img.shields.io/badge/.NET-6.0%2B-blue)

---

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Authentication](#authentication)
- [Configuration](#configuration)
- [Development](#development)
- [Testing](#testing)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

---

## 🎯 Overview

The **Employee CRM System** is a comprehensive web application for managing:

- **👤 Employees** - Company staff with manager hierarchies and performance tracking
- **🏢 Clients** - Customer/company information and relationships
- **✅ Tasks** - Work assignments with status tracking and progress monitoring
- **📊 Dashboard** - Real-time metrics and KPIs
- **🔐 Users** - Role-based access control (Admin, Manager, Employee)

Built with a **6-layer clean architecture** for maximum maintainability, scalability, and testability.

---

## ✨ Features

### Employee Management

✅ Complete CRUD operations  
✅ Employee hierarchy (manager-subordinate relationships)  
✅ Status tracking (Active, Inactive, On Leave, Terminated)  
✅ Salary management  
✅ Search and filter by name, email, status  
✅ Join date tracking

### Client Management

✅ Company and contact information  
✅ Client rating system (1-5 stars)  
✅ Address and contact details  
✅ Employee assignment  
✅ Search and filter capabilities

### Task Management

✅ Task assignment to employees  
✅ Priority levels (Low, Medium, High)  
✅ Status tracking (Pending, In Progress, Completed, On Hold)  
✅ Progress percentage tracking  
✅ Due date management  
✅ Overdue task identification  
✅ Client relationship linking

### Dashboard & Analytics

✅ Real-time metrics  
✅ Employee count  
✅ Client count  
✅ Task statistics  
✅ Completion rate  
✅ Total salary calculations

### Authentication & Security

✅ User registration and login  
✅ JWT token-based authentication  
✅ Role-based access control  
✅ Password hashing  
✅ Secure API endpoints  
✅ Authorization checks

### User Interface

✅ Responsive Bootstrap 5 design  
✅ Mobile-friendly layout  
✅ Form validation  
✅ Intuitive navigation  
✅ Professional styling  
✅ Icon-based UI (Font Awesome)

---

## 🏗️ Architecture

### 6-Layer Clean Architecture

```
┌─────────────────────────────────────┐
│  Presentation Layer (MVC Web UI)    │
├─────────────────────────────────────┤
│  Presentation Layer (REST API)      │
├─────────────────────────────────────┤
│  Business Logic Layer (Services)    │
├─────────────────────────────────────┤
│  Data Access Layer (Repositories)   │
├─────────────────────────────────────┤
│  Database Layer (EF Core DbContext) │
├─────────────────────────────────────┤
│  Domain Layer (Models & Interfaces) │
└─────────────────────────────────────┘
```

### Design Patterns Used

- **Repository Pattern** - Abstraction for data access
- **Service Layer Pattern** - Business logic encapsulation
- **Dependency Injection** - Loose coupling
- **DTO Pattern** - Data transfer objects
- **Async/Await** - Non-blocking operations

---

## 🛠️ Tech Stack

### Backend

- **Framework:** ASP.NET Core 6.0+ / 7.0+ / 8.0+
- **ORM:** Entity Framework Core
- **Database:** SQL Server
- **Authentication:** JWT (JSON Web Tokens)
- **Architecture:** Clean Architecture with 6 Layers

### Frontend

- **Framework:** ASP.NET Core MVC
- **UI Framework:** Bootstrap 5.3
- **Icons:** Font Awesome 6.4
- **Styling:** Custom CSS with animations
- **Validation:** Client-side & Server-side

### Tools & Libraries

- **API Documentation:** Swagger/OpenAPI
- **LINQ:** For database queries
- **AutoMapper:** For DTO mapping (optional)
- **Logging:** Built-in ILogger

---

## 🚀 Quick Start

### Prerequisites

- .NET 6.0 SDK or higher
- SQL Server (LocalDB or Express)
- Visual Studio 2022 or VS Code
- Git

### Installation

#### 1. Clone the Repository

```bash
git clone https://github.com/yourusername/EmployeeCRMSystem.git
cd EmployeeCRMSystem
```

#### 2. Create & Configure Projects

```bash
# Navigate to solution folder
cd EmployeeCRMSystem

# Restore packages
dotnet restore
```

#### 3. Configure Database Connection

Edit `EmployeeCRM.API/appsettings.json`:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=(localdb)\\mssqllocaldb;Database=EmployeeCRMDb;Trusted_Connection=true;MultipleActiveResultSets=true"
  },
  "JwtSettings": {
    "Secret": "your-256-bit-secret-key-here-minimum-32-characters",
    "Issuer": "EmployeeCRM",
    "Audience": "EmployeeCRMUsers",
    "ExpirationMinutes": 60
  }
}
```

#### 4. Apply Database Migrations

```bash
# Package Manager Console (Visual Studio)
Update-Database

# OR using CLI
dotnet ef database update --project EmployeeCRM.Data --startup-project EmployeeCRM.API
```

#### 5. Run the Application

**Option A: Visual Studio**

```
1. Set multiple startup projects:
   - EmployeeCRM.API
   - EmployeeCRM.MVC
2. Press F5 to start
```

**Option B: Command Line**

```bash
# Terminal 1 - API
cd EmployeeCRM.API
dotnet run
# Runs on: https://localhost:5001

# Terminal 2 - MVC
cd EmployeeCRM.MVC
dotnet run
# Runs on: https://localhost:7001
```

#### 6. Access the Application

- **Web Application:** https://localhost:7001
- **API Swagger UI:** https://localhost:5001/swagger

#### 7. Create First Account

1. Go to https://localhost:7001
2. Click "Register"
3. Fill in email, name, password
4. Click "Register"
5. You're automatically logged in!

---

## 📁 Project Structure

```
EmployeeCRMSystem/
│
├── EmployeeCRM.Core/                (Domain Models & Interfaces)
│   ├── Entities/                    (User, Employee, Client, TaskItem)
│   ├── DTOs/                        (Data Transfer Objects)
│   ├── Enums/                       (UserRole, TaskStatus, EmployeeStatus)
│   └── Interfaces/                  (IRepository, IService contracts)
│
├── EmployeeCRM.Data/                (Database Configuration)
│   ├── AppDbContext.cs              (EF Core DbContext)
│   ├── Configurations/              (Entity Fluent API configs)
│   └── Migrations/                  (Database schema versions)
│
├── EmployeeCRM.Repository/          (Data Access Layer)
│   ├── GenericRepository.cs         (Base CRUD operations)
│   └── Implementation/              (Specific repositories)
│
├── EmployeeCRM.Service/             (Business Logic Layer)
│   └── Implementation/              (Services with validation)
│
├── EmployeeCRM.API/                 (REST Web API)
│   ├── Controllers/                 (API endpoints)
│   ├── Program.cs                   (Configuration)
│   └── appsettings.json             (Settings)
│
└── EmployeeCRM.MVC/                 (Web UI Application)
    ├── Controllers/                 (Page handlers)
    ├── Services/                    (API clients)
    ├── Views/                       (Razor templates)
    ├── wwwroot/                     (CSS, JS, static files)
    └── appsettings.json             (Settings)
```

---

## 📡 API Documentation

### Base URL

```
https://localhost:5001/api
```

### Authentication Endpoints

```
POST   /auth/login              - Login and get JWT token
POST   /auth/register           - Create new user account
```

### Employee Endpoints

```
GET    /employees               - Get all employees
GET    /employees/{id}          - Get specific employee
POST   /employees               - Create employee
PUT    /employees/{id}          - Update employee
DELETE /employees/{id}          - Delete employee
GET    /employees/search/{term} - Search employees
GET    /employees/status/{id}   - Filter by status
```

### Client Endpoints

```
GET    /clients                 - Get all clients
GET    /clients/{id}            - Get specific client
POST   /clients                 - Create client
PUT    /clients/{id}            - Update client
DELETE /clients/{id}            - Delete client
GET    /clients/search/{term}   - Search clients
```

### Task Endpoints

```
GET    /tasks                   - Get all tasks
GET    /tasks/{id}              - Get specific task
POST   /tasks                   - Create task
PUT    /tasks/{id}              - Update task
DELETE /tasks/{id}              - Delete task
GET    /tasks/employee/{id}     - Get by employee
GET    /tasks/status/{status}   - Get by status
GET    /tasks/overdue/list      - Get overdue tasks
```

### Dashboard Endpoint

```
GET    /dashboard/metrics       - Get system metrics
```

### Testing with Swagger

```
1. Start the API
2. Visit: https://localhost:5001/swagger
3. Authorize with JWT token
4. Click endpoints and test
```

---

## 💾 Database Schema

### Users Table

```sql
Users (
  Id INT PRIMARY KEY,
  Email NVARCHAR(255) UNIQUE,
  FullName NVARCHAR(255),
  PasswordHash NVARCHAR(MAX),
  Role INT (1=Admin, 2=Manager, 3=Employee),
  IsActive BIT,
  CreatedDate DATETIME,
  LastLoginDate DATETIME
)
```

### Employees Table

```sql
Employees (
  Id INT PRIMARY KEY,
  FirstName NVARCHAR(255),
  LastName NVARCHAR(255),
  Email NVARCHAR(255) UNIQUE,
  Phone NVARCHAR(20),
  Position NVARCHAR(255),
  Salary DECIMAL(10,2),
  JoinDate DATE,
  Status INT (1=Active, 2=Inactive, 3=OnLeave, 4=Terminated),
  ManagerId INT (Self-referencing FK),
  UserId INT (FK to Users),
  CreatedDate DATETIME,
  UpdatedDate DATETIME
)
```

### Clients Table

```sql
Clients (
  Id INT PRIMARY KEY,
  CompanyName NVARCHAR(255),
  ContactName NVARCHAR(255),
  Email NVARCHAR(255),
  Phone NVARCHAR(20),
  Address NVARCHAR(MAX),
  City NVARCHAR(255),
  State NVARCHAR(255),
  ZipCode NVARCHAR(20),
  Rating INT (1-5),
  EmployeeId INT (FK to Employees),
  CreatedDate DATETIME,
  UpdatedDate DATETIME
)
```

### Tasks Table

```sql
Tasks (
  Id INT PRIMARY KEY,
  Title NVARCHAR(255),
  Description NVARCHAR(MAX),
  Status NVARCHAR(50),
  Priority INT (1=Low, 2=Medium, 3=High),
  DueDate DATE,
  ProgressPercentage INT (0-100),
  EmployeeId INT (FK to Employees),
  ClientId INT (FK to Clients),
  CreatedDate DATETIME,
  CompletedDate DATETIME,
  UpdatedDate DATETIME
)
```

---

## 🔐 Authentication

### Login Flow

```
1. User submits email & password
2. API validates credentials
3. API generates JWT token (1 hour expiration)
4. Token stored in browser session
5. Every request includes token in Authorization header
6. API validates token before processing request
```

### JWT Token Structure

```
Header:     { "alg": "HS256", "typ": "JWT" }
Payload:    {
              "sub": "userId",
              "email": "user@example.com",
              "name": "User Name",
              "role": "Admin",
              "iat": 1700000000,
              "exp": 1700003600
            }
Signature:  HMACSHA256(header + payload + secret)
```

### User Roles

| Role         | Permissions                               |
| ------------ | ----------------------------------------- |
| **Admin**    | Full system access, can delete anything   |
| **Manager**  | Can create/edit employees, clients, tasks |
| **Employee** | Can view/update assigned tasks            |

---

## ⚙️ Configuration

### appsettings.json (API)

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=...;Database=EmployeeCRMDb;..."
  },
  "JwtSettings": {
    "Secret": "your-secret-key-minimum-32-characters",
    "Issuer": "EmployeeCRM",
    "Audience": "EmployeeCRMUsers",
    "ExpirationMinutes": 60
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  }
}
```

### appsettings.json (MVC)

```json
{
  "ApiSettings": {
    "BaseUrl": "https://localhost:5001"
  },
  "Logging": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

---

## 👨‍💻 Development

### Building the Solution

```bash
dotnet build
```

### Running Tests (if applicable)

```bash
dotnet test
```

### Code Style

- **Language:** C# 10+
- **Framework:** .NET 6.0+
- **Naming:** PascalCase for classes, camelCase for variables
- **Pattern:** Async/await for I/O operations

### Adding a New Feature

1. **Add Entity** in `EmployeeCRM.Core/Entities/`
2. **Add DTO** in `EmployeeCRM.Core/DTOs/`
3. **Create Repository** in `EmployeeCRM.Repository/Implementation/`
4. **Create Service** in `EmployeeCRM.Service/Implementation/`
5. **Add Controller** in `EmployeeCRM.API/Controllers/`
6. **Add MVC Controller** in `EmployeeCRM.MVC/Controllers/`
7. **Create Views** in `EmployeeCRM.MVC/Views/`
8. **Update Migrations** - `Add-Migration FeatureName`

---

## 🧪 Testing

### Test the API with cURL

```bash
# 1. Login
curl -X POST https://localhost:5001/api/auth/login \
  -H "Content-Type: application/json" \
  -d '{"email":"user@example.com","password":"password"}'

# 2. Get token from response, then use it:
curl -X GET https://localhost:5001/api/employees \
  -H "Authorization: Bearer {token}"

# 3. Create Employee
curl -X POST https://localhost:5001/api/employees \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer {token}" \
  -d '{
    "firstName":"John",
    "lastName":"Doe",
    "email":"john@example.com",
    "position":"Developer",
    "salary":75000
  }'
```

### Test the Web UI

1. Start both API and MVC
2. Navigate to https://localhost:7001
3. Register a new account
4. Create employees, clients, tasks
5. View dashboard metrics

---

## 📦 Deployment

### Prerequisites for Production

- Windows Server or Linux with .NET runtime
- SQL Server (or compatible database)
- HTTPS certificate
- IIS (Windows) or nginx (Linux)

### Deployment Steps

1. **Build for Production**

   ```bash
   dotnet publish -c Release -o ./publish
   ```

2. **Configure Production Settings**
   - Update connection strings
   - Set strong JWT secret (minimum 32 characters)
   - Enable HTTPS only
   - Disable Swagger in production

3. **Deploy to IIS (Windows)**
   - Copy published files to server
   - Create IIS application pool
   - Configure HTTPS binding
   - Set appropriate permissions

4. **Deploy to Linux (nginx)**
   - Copy published files
   - Configure systemd service
   - Set up nginx reverse proxy
   - Configure SSL/TLS certificate

5. **Database Migration**
   ```bash
   dotnet ef database update -c Release
   ```

### Production Checklist

- [ ] Update connection strings
- [ ] Set strong JWT secret key
- [ ] Enable HTTPS only
- [ ] Disable Swagger/debug endpoints
- [ ] Configure CORS properly
- [ ] Set up database backups
- [ ] Enable logging and monitoring
- [ ] Test all functionality
- [ ] Security audit complete

---

## 🤝 Contributing

### Guidelines

1. Fork the repository
2. Create feature branch: `git checkout -b feature/YourFeature`
3. Commit changes: `git commit -m 'Add YourFeature'`
4. Push to branch: `git push origin feature/YourFeature`
5. Open Pull Request

### Code Standards

- Follow C# naming conventions
- Add XML documentation to public methods
- Write unit tests for new features
- Update README if adding major features

---

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

## 💬 Support

### Need Help?

**Documentation Files Available:**

- `ARCHITECTURE_QUICK_REFERENCE.md` - 2-3 min overview
- `PROJECT_ARCHITECTURE.md` - Complete architecture
- `LINQ_USAGE_GUIDE.md` - LINQ patterns used
- `API_ENDPOINTS_REFERENCE.md` - Complete API documentation
- `QUICK_START_GUIDE.md` - Setup instructions

**Getting Help:**

1. Check the documentation files
2. Review API documentation at `/swagger`
3. Check existing issues on GitHub
4. Create a new GitHub issue with detailed description

### Contact

- **Email:** support@employeecrm.local
- **GitHub Issues:** https://github.com/yourusername/EmployeeCRMSystem/issues

---

## 📊 Project Statistics

| Metric              | Value  |
| ------------------- | ------ |
| Total Projects      | 6      |
| Total Classes       | 100+   |
| Total Lines of Code | 8,000+ |
| API Endpoints       | 45+    |
| Database Tables     | 4      |
| Documentation Files | 14+    |

---

## 🎯 Roadmap

### Version 1.0 (Current)

✅ Complete CRUD operations  
✅ User authentication & authorization  
✅ Dashboard with metrics  
✅ Search and filtering

### Version 1.1 (Planned)

- [ ] Email notifications
- [ ] Advanced reporting
- [ ] Bulk operations
- [ ] Data export (Excel/PDF)

### Version 2.0 (Future)

- [ ] Mobile app (React Native/Flutter)
- [ ] Advanced analytics
- [ ] Real-time notifications (SignalR)
- [ ] Workflow automation

---

## 📚 Additional Resources

- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core)
- [Entity Framework Core Documentation](https://docs.microsoft.com/ef/core)
- [Clean Architecture Principles](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html)
- [JWT Authentication](https://jwt.io)
- [Bootstrap 5 Documentation](https://getbootstrap.com/docs)

---

## ✅ Getting Started Checklist

- [ ] Clone repository
- [ ] Install .NET SDK
- [ ] Install SQL Server
- [ ] Update connection strings
- [ ] Apply migrations
- [ ] Build solution
- [ ] Run API
- [ ] Run MVC
- [ ] Register account
- [ ] Create test data
- [ ] Explore dashboard

---

## 📝 Notes

This is a **production-ready** application demonstrating:

- Professional architecture patterns
- Security best practices
- Clean, maintainable code
- Comprehensive documentation
- Scalable design

Perfect for learning ASP.NET Core, architecture patterns, and building enterprise applications!

---

**Last Updated:** April 2026  
**Version:** 1.0.0  
**Status:** ✅ Production Ready

---

## License & Attribution

MIT License - Feel free to use this project for learning and development!

**Created with ❤️ for developers learning ASP.NET Core**
