# Taskify API

Taskify is a simple and extensible **ASP.NET Core Web API** designed for managing tasks and assigning them to users.  
The API supports task creation, assignment, details tracking, and user-task relationships.

## 📌 Features

- Create and manage tasks (`TodoTask`)
- Add extra notes to each task (`TaskDetail`)
- Assign tasks to users (`UserTask`)
- Support for one-to-one, one-to-many, and many-to-many relationships
- Ready for expansion with authentication, database integration, and front-end support

---

## 🧩 Data Models

### `TodoTask`
Represents a task that can be assigned to users.

```csharp
public class TodoTask {
    public int Id { get; set; }
    public string Title { get; set; }
    public string Description { get; set; }
    public DateTime DueDate { get; set; }
    public string Status { get; set; } // "Pending", "Completed", etc.
    public TaskDetail TaskDetail { get; set; } // One-to-One
    public ICollection<UserTask> UserTasks { get; set; } // One-to-Many
}
TaskDetail
Represents additional details for each task, like extra notes.
public class TaskDetail
{
    public int Id { get; set; }
    public string ExtraNotes { get; set; }

    public int TaskId { get; set; }
    public TodoTask Task { get; set; }
}
User
Represents the users who can be assigned tasks.
public class User
{
    public int Id { get; set; }
    public string Name { get; set; }
    public ICollection<UserTask> UserTasks { get; set; } // Many-to-Many
}
UserTask
Represents the task assigned to a user.
public class UserTask
{
    public int Id { get; set; }
    public int UserId { get; set; } // Refers to the User's ID
    public int TaskId { get; set; } // Refers to the Task's ID

    public TodoTask Task { get; set; }
    public User User { get; set; } // Refers to the User
}
🛠️ Future Enhancements
Add authentication (JWT, OAuth, etc.)

Integrate with a real database (SQL Server, MongoDB, etc.)

Develop a front-end interface (React, Angular, etc.)


