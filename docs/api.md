# API Contract

This document defines the interface between frontend, backend,
database-backed services, and AI features.

## 1. API Principles

-   APIs should return predictable JSON.
-   Authentication should be enforced server-side.
-   Users should only access resources they are authorized to access.
-   The AI should consume backend APIs/services rather than directly
    exposing database credentials.
-   Keep response structures stable once the AI integration depends on
    them.

## 2. Authentication

### Current User

Document how the backend identifies the authenticated user.

-   Authentication:
-   User ID:
-   Session:
-   Roles:

## 3. Student / User APIs

### Get Profile

`GET /api/student/profile`

Example response:

``` json
{
  "id": "student_id",
  "name": "Student Name",
  "email": "student@example.com",
  "department": "CSE",
  "semester": 4
}
```

### Get Attendance

`GET /api/student/attendance`

Example response:

``` json
{
  "overall": 42,
  "subjects": [
    {
      "subject": "DSA",
      "attended": 14,
      "total": 40,
      "percentage": 35
    }
  ]
}
```

### Get Marks

`GET /api/student/marks`

Example response:

``` json
{
  "subjects": [
    {
      "subject": "DSA",
      "marks": 78
    }
  ]
}
```

### Get Timetable

`GET /api/student/timetable`

Example response:

``` json
{
  "classes": [
    {
      "subject": "DSA",
      "day": "Monday",
      "time": "10:00"
    }
  ]
}
```

## 4. Additional APIs

  Method      Endpoint   Purpose   Auth   Status
  ----------- ---------- --------- ------ --------
  GET                                     ⬜
  POST                                    ⬜
  PUT/PATCH                               ⬜
  DELETE                                  ⬜

## 5. Error Format

Use a consistent error response.

``` json
{
  "error": {
    "code": "ERROR_CODE",
    "message": "Human-readable message"
  }
}
```

## 6. API Contract Changes

Record breaking changes here.

  Date   Endpoint   Change   Reason
  ------ ---------- -------- --------
                             
