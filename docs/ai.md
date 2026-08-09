# AI Architecture

## 1. AI Objective

AI should solve clearly identified user problems. It should not be added
only because it is technically impressive.

## 2. AI Role

Document exactly where AI adds value:

-   Natural-language interaction
-   Information retrieval
-   Analysis
-   Prediction
-   Recommendation
-   Automation
-   Other:

## 3. AI Architecture

``` text
User
 |
 v
AI Chat UI
 |
 v
/api/chat
 |
 v
AI Orchestrator
 |
 +----> LLM
 |
 +----> Approved Tools
           |
           +----> Backend APIs
           |
           +----> Database-backed services
 |
 v
Response
 |
 v
User
```

## 4. Model

-   Provider:
-   Model:
-   Reason for choice:
-   Cost/rate limits:
-   Fallback model:

## 5. AI Context

Define what information the AI is allowed to use.

-   User profile:
-   Domain data:
-   Current page/context:
-   Retrieved documents:
-   Other:

## 6. Tools

Start with a small number of generic capabilities.

  Tool                  Purpose               Read/Write   Risk   Confirmation
  --------------------- --------------------- ------------ ------ --------------
  getStudentProfile     Retrieve profile      Read         Low    No
  getAttendance         Retrieve attendance   Read         Low    No
  getMarks              Retrieve marks        Read         Low    No
  getTimetable          Retrieve timetable    Read         Low    No
  calculateAttendance   Exact calculation     Compute      Low    No

Add tools only when a real use case requires them.

## 7. AI Safety

### Read

Generally automatic, subject to authorization.

### Calculate

Use deterministic application code for important calculations.

### Write

Require authorization and, where appropriate, user confirmation.

### Destructive

Require explicit confirmation and strong authorization.

## 8. Hallucination Control

-   Retrieve authoritative data from backend/database.
-   Do not allow the model to invent database values.
-   Use structured tool outputs.
-   Clearly communicate unavailable data.
-   Validate important outputs.
-   Keep calculations deterministic.

## 9. AI Evaluation

Test: - Correctness - Tool selection - Data grounding - Safety - Failure
handling - Latency - Cost

## 10. AI Feature Roadmap

### P0

-   Basic AI chat
-   Student context
-   One or two useful tools

### P1

-   More domain tools
-   Analysis
-   Recommendations
-   Prediction where justified

### P2

-   Voice
-   Multilingual expansion
-   Advanced agent workflows
-   Other experimental features
