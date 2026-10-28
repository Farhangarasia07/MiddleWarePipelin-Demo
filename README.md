# ASP.NET Core Middleware Pipeline Demo

A beginner-friendly ASP.NET Core demo application that illustrates how the middleware pipeline works in .NET web applications. It demonstrates the execution flow of HTTP requests through various middleware components, including sequential processing with `app.Use()`, route branching with `app.Map()`, and conditional routing with `app.MapWhen()`.

## 📋 Description

This project showcases how the ASP.NET Core middleware pipeline works, including:
- Sequential middleware execution with `app.Use()`
- Route branching with `app.Map()`
- Conditional branching with `app.MapWhen()`
- Terminal middleware with `app.Run()`
- Console logging at each step to visualize request flow through the pipeline

## 🚀 Getting Started

### Prerequisites
- .NET 6.0 or higher
- Visual Studio 2022 / VS Code / Rider (or any C# IDE)
- Git

### Installation

1. Clone the repository
```bash
git clone https://github.com/Kingaer04/ASP.NET-Core-Middleware-Pipeline-Demo.git
cd ASP.NET-Core-Middleware-Pipeline-Demo
```

2. Restore dependencies
```bash
dotnet restore
```

3. Run the application
```bash
dotnet run
```

The application will start on `https://localhost:5001` or `http://localhost:5000` (check console for actual port)

## 🧪 Testing the Endpoints

### Default Route
```
GET https://localhost:5001/
Response: "Hello from the middleware component."
```

### Map Branch Route
```
GET https://localhost:5001/usingmapbranch
Response: "Hello from the map branch."
```

### MapWhen Conditional Route
```
GET https://localhost:5001/?testquerystring=anything
Response: "Hello from the MapWhen branch."
```

## 📖 How It Works

### Middleware Pipeline Flow

1. **UseHttpsRedirection** - Redirects HTTP to HTTPS
2. **UseAuthorization** - Handles authorization
3. **Use Middleware** - Logs before/after execution
4. **Map Branch** - Routes `/usingmapbranch` to a separate pipeline
5. **MapWhen Branch** - Routes requests with `testquerystring` query parameter
6. **Run (Terminal)** - Default fallback response
7. **MapControllers** - Maps controller routes

### Console Output Example

When hitting the default route:
```
Logic before executing the next delegate in the Use method
Logic after executing the next delegate in the Use method
Writing the response to the client in the Run method
```

When hitting `/usingmapbranch`:
```
Logic before executing the next delegate in the Use method
Map branch logic in the Use method before the next delegate
Map branch logic in the use method after the next delegate
Map branch response to the client in the Run method
Logic after executing the next delegate in the Use method
```

When hitting `/?testquerystring=value`:
```
Logic before executing the next delegate in the Use method
Logic after executing the next delegate in the Use method
(Response: "Hello from the MapWhen branch.")
```

## 🛠️ Technologies Used

- ASP.NET Core 6.0+
- C# 10+
- Minimal API

## 📚 Key Concepts Demonstrated

- **app.Use()** - Non-terminal middleware that can call the next delegate using `await next.Invoke()`
- **app.Map()** - Branches the pipeline based on request path
- **app.MapWhen()** - Conditionally branches based on request properties (like query strings)
- **app.Run()** - Terminal middleware that ends the pipeline
- **Middleware Execution Order** - Shows how order matters in the pipeline and how middleware wraps around subsequent components

## 📂 Project Structure

```
CompanyEmployees/
├── Program.cs                      # Main application entry point with middleware pipeline
├── CompanyEmployees.csproj         # Project file
├── appsettings.json                # Application configuration
├── appsettings.Development.json    # Development environment configuration
├── Properties/
│   └── launchSettings.json         # Launch profiles
└── README.md                       # This file
```

## ⚠️ Note

This is a learning/demo project focused on understanding middleware concepts. In the current implementation, `app.MapControllers()` is placed after `app.Run()`, which means controllers won't be reachable. In production code, ensure routing middleware like `app.MapControllers()` comes before any terminal middleware.

## 🔗 Repository

GitHub: [https://github.com/Kingaer04/ASP.NET-Core-Middleware-Pipeline-Demo](https://github.com/Kingaer04/ASP.NET-Core-Middleware-Pipeline-Demo)

## 📝 License

This project is open source and available for educational purposes.

## 👤 Author

**Kingaer04**
- GitHub: [@Kingaer04](https://github.com/Kingaer04)

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/Kingaer04/ASP.NET-Core-Middleware-Pipeline-Demo/issues).

## ⭐ Show your support

Give a ⭐️ if this project helped you understand ASP.NET Core middleware!

---

**Happy Learning! 🚀**
