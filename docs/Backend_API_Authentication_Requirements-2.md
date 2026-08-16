# Backend API & Authentication Requirements

## Goal

Provide secure APIs that can be called by the application on behalf of the currently logged-in user.

The backend must remain responsible for **authentication, authorization, and data access**.

---

## 1. Authentication — Main Requirement

The project uses **Supabase Auth**.

For protected APIs, support:

```http
Authorization: Bearer <SUPABASE_ACCESS_TOKEN>
```

The backend should:

1. Validate the Supabase access token.
2. Identify the user from the validated token.
3. Check whether that user is allowed to access the requested resource/action.
4. Return only data that the authenticated user is authorized to access.

### Important

Do **not** trust a `userId` sent in the request as proof of identity.

The authenticated user ID should come from the validated token.

---

## 2. Required Authentication Responses

Please use:

```text
401 Unauthorized
```

when the token is missing, invalid, or expired.

```text
403 Forbidden
```

when the user is authenticated but does not have permission.

```text
404 Not Found
```

when the requested resource does not exist.

---

## 3. APIs Needed

Please provide the required endpoints for:

```text
User
- Get current user/profile

Applications
- Get application
- Get application history
- Get application status

Other project-specific data
- Relevant user-owned data
- Relevant calculations/business operations
```

Example:

```text
GET /api/applications/:id
```

Authentication:

```http
Authorization: Bearer <SUPABASE_ACCESS_TOKEN>
```

---

## 4. API Information Required

For every endpoint, please provide:

```text
HTTP Method
Endpoint
Authentication required
Parameters
Request body (if applicable)
Response JSON
Possible errors
Permission rules
```

Example:

```text
GET /api/applications/:id

Auth:
Supabase access token

Permission:
User can only access applications they are authorized to view.

Response:
{
  "id": "123",
  "status": "pending"
}
```

---

## 5. Existing Backend Functions

If the backend already has functions/business logic such as:

```text
checkEligibility()
calculateBenefit()
getApplicationHistory()
```

please expose the required functionality through APIs/services so it can be called externally.

Do not require another client to duplicate the business logic.

---

## 6. Security Requirements

The backend should independently verify:

```text
Who is the user?
        ↓
Is the token valid?
        ↓
Is the user allowed to perform this operation?
        ↓
Is the requested resource accessible?
        ↓
Return data / perform action
```

The client should never be able to bypass these checks by changing a user ID or resource ID.

---

## 7. Development Access

Please provide:

- Development/staging API base URL
- API documentation or endpoint list
- Test account/user
- Authentication instructions
- Example request and response for each required endpoint

**Do not provide production secrets or service-role keys to the client.**

---

## Short version

The main requirement is:

> **Please expose the required backend functionality through secure APIs that accept and validate the logged-in user's Supabase access token, identify the user from that token, and enforce authorization before returning data or performing any action.**
