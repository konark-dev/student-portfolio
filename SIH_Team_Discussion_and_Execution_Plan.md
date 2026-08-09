# SIH 2026 --- Team Project Discussion & Execution Plan

## 1. Purpose

This document is the team's common place to discuss:

-   What problem are we solving?
-   What is the minimum working solution?
-   What extra features can make the solution stronger?
-   Who is responsible for each part?
-   What should we research?
-   What should we build first?
-   What should we test before the final submission?

> **Main principle:** Don't try to build everything at once. Build a
> working core first, then improve it in iterations.

------------------------------------------------------------------------

# 2. Overall Approach

We should follow this cycle:

**Problem Statement → Research → User Problems → Core Solution → MVP →
Integration → Testing → Extra Features → Demo/Presentation**

### Phase 1 --- Understand the Problem

Before writing code, answer:

1.  What exactly is the problem?
2.  Who faces this problem?
3.  How is it currently solved?
4.  What are the limitations of existing solutions?
5.  What data do we have?
6.  What constraints are given in the SIH problem statement?
7.  What would make our solution practically useful?

Do not start by deciding the technology.

------------------------------------------------------------------------

# 3. Research

Research should answer practical questions, not just collect
information.

### Research checklist

-   Existing government/industry solutions
-   Existing applications/platforms
-   Similar SIH projects
-   Research papers or technical approaches
-   Available APIs/datasets
-   Existing open-source projects
-   Security/privacy requirements
-   Scalability requirements
-   Offline/low-connectivity requirements
-   Possible AI/ML use cases
-   Important edge cases

### Research output

Every research item should produce one of:

-   A feature idea
-   A technical decision
-   A limitation we need to solve
-   A dataset/API
-   A risk
-   Evidence supporting our approach

------------------------------------------------------------------------

# 4. Convert the Problem Into User Problems

Instead of immediately writing features, write the actual problems.

Example:

### Problem

Students have low attendance visibility.

### User problems

-   Student does not know current attendance accurately.
-   Student does not know which subjects are risky.
-   Student may not understand how many classes are required to reach a
    target.
-   Faculty may spend time identifying at-risk students.
-   Administration may lack useful analytics.

Then convert these into solutions.

  -----------------------------------------------------------------------
  User Problem            Basic Solution          Possible Advanced
                                                  Solution
  ----------------------- ----------------------- -----------------------
  Attendance is difficult Attendance dashboard    AI-generated
  to understand                                   explanation

  Student doesn't know    Attendance percentage   Risk prediction
  risk                                            

  Student doesn't know    Show required classes   Personalized action
  what to do                                      plan

  Faculty manually checks Faculty dashboard       Automatic alerts
  students                                        

  Data is difficult to    Filters/search          Natural-language AI
  search                                          assistant
  -----------------------------------------------------------------------

------------------------------------------------------------------------

# 5. Define the MVP

The MVP is the smallest version that proves our solution works.

## MVP Rule

If we have 20 possible features, do not build all 20 first.

Choose approximately:

-   1 core problem
-   1 core workflow
-   3--5 essential features
-   1 strong differentiating feature

### MVP should be:

-   Functional
-   Demonstrable
-   Stable
-   Easy to understand
-   Connected end-to-end

### Example

**User logs in → sees attendance → identifies risky subject → gets
recommendation → takes action**

That complete workflow is more valuable than 15 disconnected features.

------------------------------------------------------------------------

# 6. Feature Prioritization

Every proposed feature should be placed into one of these categories.

### P0 --- Must Have

Without it, the solution does not work.

### P1 --- Important

Strongly improves the solution or demo.

### P2 --- Differentiator

Makes the project stand out.

### P3 --- Nice to Have

Build only if time remains.

  Feature            Priority   Why?             Owner   Status
  ------------------ ---------- ---------------- ------- --------
  Authentication     P0         Required                 TODO
  Core dashboard     P0         Main workflow            TODO
  Main backend API   P0         Required                 TODO
  AI assistant       P1/P2      Differentiator           TODO
  Analytics          P1         Useful                   TODO
  Notifications      P2         Extra value              TODO

------------------------------------------------------------------------

# 7. Think in Workflows, Not Just Features

For every major feature, define the complete flow.

### Example

**Attendance AI Assistant**

1.  User asks a question.
2.  AI identifies the intent.
3.  System retrieves relevant attendance data.
4.  AI calculates/uses trusted application data.
5.  AI generates an explanation.
6.  Safety/permission checks run.
7.  Response is shown to the user.

This prevents us from building an AI chatbot that is disconnected from
the actual application.

------------------------------------------------------------------------

# 8. AI Integration Strategy

AI should solve a real problem.

Do not add AI simply because the project needs an "AI feature."

### Good AI use cases

-   Natural-language search
-   Data explanation
-   Personalized recommendations
-   Summarization
-   Question answering over project data
-   Anomaly/risk explanation
-   Assistant for different user roles
-   Report generation
-   Intelligent workflow assistance

### Avoid

-   AI generating values that should come from the database
-   AI making unauthorized changes
-   AI being the source of truth for calculations
-   A generic chatbot unrelated to the problem

### Important principle

**Database = source of truth**

**Backend/business logic = authority**

**AI = interface/reasoning/explanation layer**

------------------------------------------------------------------------

# 9. AI Safety

The AI should not directly receive unlimited access to the entire
system.

Use controlled tools/functions.

Example:

``` text
User
 ↓
AI Assistant
 ↓
Intent / Permission Check
 ↓
Allowed Tool
 ↓
Backend
 ↓
Database
 ↓
Validated Result
 ↓
AI Explanation
 ↓
User
```

### Important rules

-   Validate user permissions.
-   Validate tool inputs.
-   Keep sensitive data protected.
-   Do not allow arbitrary database queries from the model.
-   Keep important calculations deterministic.
-   Log important AI actions.
-   Return safe fallback responses when data is unavailable.

------------------------------------------------------------------------

# 10. Architecture Discussion

Before implementation, agree on a simple architecture.

``` text
Frontend
   ↓
Backend / API
   ↓
Business Logic
   ↓
Database
   ↓
AI Layer
   ↓
AI Tools / Retrieval
```

Depending on the project, the AI layer can interact with controlled
backend APIs rather than directly accessing the database.

### Decide early

-   Frontend framework
-   Backend framework
-   Database
-   Authentication
-   Hosting
-   AI provider/model
-   AI SDK
-   Vector database if actually required
-   External APIs
-   File/object storage
-   Monitoring/logging

Do not introduce technology unless it solves a real requirement.

------------------------------------------------------------------------

# 11. GitHub Team Workflow

Use separate branches.

``` text
main
│
├── feature/frontend
├── feature/backend
├── feature/ai
├── feature/database
└── feature/analytics
```

### Recommended workflow

1.  Create issue/task.
2.  Create feature branch.
3.  Implement one focused change.
4.  Test locally.
5.  Commit clearly.
6.  Push branch.
7.  Create Pull Request.
8.  Another teammate reviews.
9.  Fix issues.
10. Merge into main/development branch.

### Avoid

-   Everyone editing the same files unnecessarily.
-   Directly pushing experimental code to `main`.
-   Huge commits containing many unrelated changes.
-   Merging code that has not been tested.

------------------------------------------------------------------------

# 12. Team Responsibilities

Each person should own a clear area.

  Area               Responsibility
  ------------------ -------------------------------------------------
  Product/Research   Problem understanding, research, requirements
  Frontend           UI, dashboard, user interaction
  Backend            APIs, business logic
  Database           Schema, queries, security
  AI                 AI integration, tools, prompts, RAG if required
  Testing            Test cases, edge cases, integration testing
  Presentation       Demo flow, PPT, documentation

One person can have multiple roles in a small team.

------------------------------------------------------------------------

# 13. Definition of Done

A feature is NOT done just because the code exists.

A feature is done when:

-   [ ] Code works
-   [ ] UI works
-   [ ] API works
-   [ ] Database integration works
-   [ ] Error handling exists
-   [ ] Permissions are checked
-   [ ] Edge cases are tested
-   [ ] Another teammate can understand it
-   [ ] Changes are committed
-   [ ] Pull Request is reviewed
-   [ ] Feature works with the complete application

------------------------------------------------------------------------

# 14. Testing

Test three levels.

## Functional Testing

Does the feature work normally?

## Edge Cases

What happens when:

-   Data is missing?
-   Data is incorrect?
-   User enters invalid input?
-   API fails?
-   AI returns an unexpected response?
-   User has no permission?
-   Network disconnects?
-   Database is unavailable?

## Integration Testing

Does the complete workflow work?

Example:

``` text
Login
 ↓
Dashboard
 ↓
User asks AI
 ↓
AI calls backend
 ↓
Backend retrieves data
 ↓
AI explains result
 ↓
Correct response displayed
```

------------------------------------------------------------------------

# 15. Extra Feature Brainstorming

After MVP works, brainstorm using these categories.

### A. Automation

Can the system automatically do something that users currently do
manually?

### B. Intelligence

Can the system identify patterns, risks, anomalies, or recommendations?

### C. Personalization

Can different users receive different useful information?

### D. Accessibility

Can the solution work better for users with different needs?

### E. Analytics

Can raw data become useful insights?

### F. Notifications

Can users be informed at the right time?

### G. Natural Language

Can users interact without navigating many screens?

### H. Offline/Low Connectivity

Can important functionality work with poor internet?

### I. Security

Can we improve authentication, authorization, privacy, or auditability?

### J. Scalability

Would this still work with 10x or 100x more users/data?

------------------------------------------------------------------------

# 16. "What Else Can We Add?" Framework

For every core feature, ask:

1.  Can we make it faster?
2.  Can we automate it?
3.  Can we personalize it?
4.  Can we predict something?
5.  Can we explain the result?
6.  Can we notify the user?
7.  Can we make it accessible?
8.  Can we make it work offline?
9.  Can AI make the interaction easier?
10. Can we measure its impact?

This gives us extra ideas without randomly adding features.

------------------------------------------------------------------------

# 17. Differentiation

Do not try to win by having the largest number of features.

Try to have:

**One strong core solution + one or two impressive differentiators.**

Possible differentiators:

-   AI agent integrated into the actual workflow
-   Predictive analytics
-   Intelligent recommendations
-   Role-based AI assistant
-   Explainable insights
-   Automation
-   Strong security model
-   Real-world deployment readiness
-   Excellent UX
-   Offline capability
-   Meaningful dashboards

------------------------------------------------------------------------

# 18. Demo Strategy

The final demo should tell a story.

### Recommended flow

``` text
Problem
 ↓
Why existing solutions are insufficient
 ↓
Our solution
 ↓
User enters system
 ↓
Core workflow
 ↓
AI/unique feature
 ↓
Real-world result
 ↓
Impact
```

Do not spend most of the demo explaining code.

Show the solution working.

------------------------------------------------------------------------

# 19. Documentation

Maintain these files:

``` text
docs/
├── problem.md
├── research.md
├── requirements.md
├── architecture.md
├── api.md
├── ai.md
├── database.md
├── testing.md
└── demo.md
```

Also maintain:

``` text
README.md
```

The README should explain:

-   Problem
-   Solution
-   Features
-   Architecture
-   Tech stack
-   Setup
-   Screenshots
-   AI integration
-   Future scope

------------------------------------------------------------------------

# 20. Decision Log

Whenever the team makes an important decision, record it.

  Date   Decision   Reason   Alternatives
  ------ ---------- -------- --------------
                             

Example:

> We chose PostgreSQL because the data is relational and requires strong
> consistency.

This prevents the team from repeatedly discussing the same decision.

------------------------------------------------------------------------

# 21. Risk Register

Track risks before they become problems.

  Risk                    Probability   Impact   Solution
  ----------------------- ------------- -------- --------------------------
  AI API unavailable      Medium        High     Fallback logic
  Dataset incomplete      Medium        High     Synthetic/test dataset
  Integration conflicts   Medium        Medium   Branch + PR workflow
  Feature too large       High          High     Reduce to MVP
  AI hallucination        Medium        High     Tool-based verified data

------------------------------------------------------------------------

# 22. Daily Team Discussion

At the beginning/end of each work session:

### Discuss

-   What did I complete?
-   What am I working on now?
-   What is blocking me?
-   What does another teammate need from me?
-   Did we discover a new requirement?
-   Did we discover a better technical approach?

Keep this short.

------------------------------------------------------------------------

# 23. Weekly/Phase Review

At the end of each major phase:

### Ask

-   Is the core problem still correct?
-   Is our MVP working?
-   What should we remove?
-   What should we add?
-   Are we overengineering?
-   Is AI actually useful?
-   What is our strongest differentiator?
-   What can break during the demo?
-   What should we finish before starting new features?

------------------------------------------------------------------------

# 24. Golden Rules

### Rule 1

**Understand the problem before choosing technology.**

### Rule 2

**Build the smallest complete workflow first.**

### Rule 3

**Do not build 20 incomplete features.**

### Rule 4

**Every feature must solve a user problem.**

### Rule 5

**AI should enhance the product, not exist separately from it.**

### Rule 6

**Keep deterministic logic outside the LLM.**

### Rule 7

**Use Git branches and Pull Requests.**

### Rule 8

**Test integration, not only individual components.**

### Rule 9

**Remove features that do not improve the solution.**

### Rule 10

**A reliable simple feature is better than an impressive broken
feature.**

------------------------------------------------------------------------

# 25. Immediate Next Steps

Before coding heavily, the team should complete:

-   [ ] Finalize problem statement understanding
-   [ ] Identify users
-   [ ] List current pain points
-   [ ] Research existing solutions
-   [ ] Identify available data/APIs
-   [ ] Write requirements
-   [ ] Define MVP
-   [ ] Prioritize features
-   [ ] Decide architecture
-   [ ] Divide responsibilities
-   [ ] Create GitHub issues
-   [ ] Create feature branches
-   [ ] Build the first end-to-end workflow
-   [ ] Test it
-   [ ] Then add differentiating features

------------------------------------------------------------------------

# 26. Final Team Mindset

The project should evolve like this:

``` text
Research
   ↓
Understand
   ↓
Plan
   ↓
MVP
   ↓
Working Demo
   ↓
Improve
   ↓
Differentiate
   ↓
Harden
   ↓
Final Demo
```

**Do not ask:**

> "What technology can we add?"

Ask:

> "What problem can we solve better?"

Then ask:

> "What technology helps us solve it?"

------------------------------------------------------------------------

## Team Discussion Area

## \### Problem Understanding

## \### Research Findings

## \### User Pain Points

## \### MVP Features

## \### Extra Feature Ideas

## \### AI Ideas

## \### Technical Decisions

## \### Risks

## \### Questions for Next Meeting

## \### Decisions Made

### Tasks

-   \[ \]
-   \[ \]
-   \[ \]
