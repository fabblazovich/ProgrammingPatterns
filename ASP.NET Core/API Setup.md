# ASP.NET Core Web API Setup


## Program.cs

```csharp
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers();

builder.Services.AddEndpointsApiExplorer();
builder.Services.AddSwaggerGen();

var app = builder.Build();

if (app.Environment.IsDevelopment())
{
    app.UseSwagger();
    app.UseSwaggerUI();
}

app.MapControllers();

app.Run();
```

---

## Create Controller

```csharp
using Microsoft.AspNetCore.Mvc;

namespace MyApi.Controllers;

[ApiController]
[Route("api/[controller]")]
public class TaskController : ControllerBase
{
    [HttpGet]
    public async Task<IActionResult> Get()
    {
        return Ok("Hello World");
    }
}
```

---

## Run Application

```bash
dotnet run
```

Example URL:

```text
https://localhost:5001/api/task
```

---

# HTTP Methods

## GET

Retrieve data.

```csharp
[HttpGet]
public async Task<IActionResult> Get()
{
    return Ok();
}
```

---

## GET By Id

```csharp
[HttpGet("{id}")]
public async Task<IActionResult> GetById(Guid id)
{
    return Ok();
}
```

---

## POST

Create data.

```csharp
[HttpPost]
public async Task<IActionResult> Create(TaskItem task)
{
    return Ok(task);
}
```

---

## PUT

Update existing data.

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Update(Guid id, TaskItem task)
{
    return NoContent();
}
```

---

## DELETE

Delete data.

```csharp
[HttpDelete("{id}")]
public async Task<IActionResult> Delete(Guid id)
{
    return NoContent();
}
```

---



# Swagger

Swagger provides API documentation and testing.

Available after starting:

```text
https://localhost:5001/swagger
```

---

# Dependency Injection Example

## Register Service

```csharp
builder.Services.AddScoped<ITaskService, TaskService>();
```

---

## Use Service

```csharp
public class TaskController : ControllerBase
{
    private readonly ITaskService taskService;

    public TaskController(ITaskService taskService)
    {
        this.taskService = taskService;
    }
}
```

---

# Typical Project Structure

```text
API
│
├── Controllers
│   └── TaskController.cs
│
├── Models
│   └── TaskItem.cs
│
├── Services
│   ├── ITaskService.cs
│   └── TaskService.cs
│
├── Data
│   └── AppDbContext.cs
│
├── appsettings.json
│
└── Program.cs
```

---

# Best Practices

- Use async/await for database operations.
- Keep controllers thin.
- Move business logic into services.
- Use Dependency Injection.
- Return proper HTTP status codes.
- Use Swagger during development.
- Store configuration in appsettings.json.