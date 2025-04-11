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
