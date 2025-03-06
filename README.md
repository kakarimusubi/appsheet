# appsheet

Here is the ER diagram for my project:

```mermaid
erDiagram
    UserList {
        string UserID PK
        string Name
        string Role
        boolean IsDeleted
        datetime CreatedAt
        string CreatedBy FK
        datetime UpdatedAt
        string UpdatedBy FK
    }

    TaskList {
        string TaskID PK
        string TaskName
        string Status
        text Details
        datetime StartDate
        datetime DueDate
        datetime ExpectedDate
        string Assignee FK
        decimal WorkHours
        string FileLink
        string ReferenceLink
        boolean IsDeleted
        datetime CreatedAt
        string CreatedBy FK
        datetime UpdatedAt
        string UpdatedBy FK
        string MilestoneID FK
        string ProjectID FK
    }

    MilestoneList {
        string MilestoneID PK
        string MilestoneName
        string Status
        string ProjectID FK
    }

    ProjectList {
        string ProjectID PK
        string ProjectName
        string Leader FK
    }

    MemoList {
        string MemoID PK
        text MemoContent
        string TaskID FK
        boolean IsDeleted
        datetime CreatedAt
        string CreatedBy FK
        datetime UpdatedAt
        string UpdatedBy FK
    }

    UserList ||--o{ TaskList : "Assignee"
    TaskList }o--|| MilestoneList : "BelongsTo"
    MilestoneList }o--|| ProjectList : "BelongsTo"
    TaskList ||--o{ MemoList : "Has"
    ProjectList ||--o{ TaskList : "Includes"
