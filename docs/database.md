# Database

## 1. Database Objective

The database is the authoritative source of persistent application data.

## 2. Database Technology

-   Database:
-   Hosting:
-   ORM/query layer:
-   Authentication:
-   Storage:

## 3. Core Entities

Document only entities actually required by the problem.

### Users / Students

  Field        Type   Required   Description
  ------------ ------ ---------- -------------
  id                  Yes        
  name                Yes        
  email               Yes        
  department                     
  semester                       

### Domain Tables

Add tables relevant to the PS.

  Table   Purpose
  ------- ---------
          

## 4. Relationships

``` text
User / Student
      |
      +---- Attendance
      |
      +---- Marks
      |
      +---- Timetable
```

Replace this with the actual ER structure once finalized.

## 5. Security

-   Row-level/resource-level authorization:
-   Sensitive fields:
-   Access rules:
-   Admin access:
-   Audit requirements:

## 6. Data Lifecycle

-   Creation:
-   Update:
-   Deletion:
-   Retention:
-   Backup/recovery:

## 7. AI Data Access

The AI must not bypass authorization.

``` text
AI
 |
 v
Backend tool/service
 |
 v
Authorized database query
 |
 v
Structured result
```

## 8. Database Migration Strategy

-   Migration tool:
-   Migration naming:
-   Seed/demo data:
-   Production migration process:
