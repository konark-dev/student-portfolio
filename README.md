# Our workflow
If your SIH team has multiple people working on the same project, **you should NOT all edit the same files directly on `main`**.

Think of it like this:

```text
                    GitHub Repository
                          │
                       main
                          │
             ┌────────────┼────────────┐
             ↓            ↓            ↓
          your-ai      frontend       backend
           branch       branch         branch
             │            │             │
          your code    UI code       API/DB code
             │            │             │
             └────────────┼────────────┘
                          ↓
                       Pull Request
                          ↓
                         main
```

### The workflow I recommend for your SIH team

Suppose your repository is:

```text
sih-project/
├── frontend/
├── backend/
├── ai/
├── database/
└── README.md
```

Each person gets their **own branch**.

For example:

```text
main
│
├── feature/ai-integration       ← YOU
├── feature/frontend-dashboard  ← teammate 1
├── feature/backend-api         ← teammate 2
└── feature/database            ← teammate 3
```

You work only on:

```bash
feature/ai-integration
```

Your teammate works on:

```bash
feature/frontend-dashboard
```

Another teammate:

```bash
feature/backend-api
```

They can all work **simultaneously**.

---

## 1. First person creates the repository

One teammate should create the GitHub repository.

For example:

```text
SIH-2026
```

Then add the other team members as collaborators.

On GitHub:

**Repository → Settings → Collaborators → Add people**

---

## 2. Everyone clones the repository

Each person does:

```bash
git clone https://github.com/YOUR-TEAM/SIH-2026.git
cd SIH-2026
```

Then:

```bash
git checkout main
git pull origin main
```

---

# 3. You create YOUR branch

Since you're handling the AI integration, for example:

```bash
git checkout -b feature/ai-integration
```

Now verify:

```bash
git branch
```

You'll see something like:

```text
* feature/ai-integration
  main
```

The `*` means **you are currently working on your branch**.

Then push it:

```bash
git push -u origin feature/ai-integration
```

Now GitHub has:

```text
main
feature/ai-integration
```

---

# 4. Your teammate does the same

Frontend person:

```bash
git checkout -b feature/frontend
git push -u origin feature/frontend
```

Backend person:

```bash
git checkout -b feature/backend
git push -u origin feature/backend
```

So GitHub might look like:

```text
Branches

main
feature/ai-integration
feature/frontend
feature/backend
feature/database
```

---

# 5. Now the important part: you can work independently

Suppose you're implementing:

```text
AI Agent
├── chat
├── attendance queries
├── tool calling
├── RAG
└── safety
```

You modify:

```text
ai/
├── agent.ts
├── tools.ts
├── rag.ts
└── safety.ts
```

Meanwhile your frontend teammate modifies:

```text
frontend/
├── components/
├── dashboard/
└── chat/
```

And backend modifies:

```text
backend/
├── routes/
├── controllers/
└── services/
```

**Nobody needs to wait for anyone else.**

That's the main advantage.

---

# 6. When your work is ready → Commit

For example:

```bash
git status
```

Then:

```bash
git add .
```

Then:

```bash
git commit -m "Add AI attendance agent"
```

Then:

```bash
git push
```

Your code goes to:

```text
feature/ai-integration
```

**NOT `main`.**

---

# 7. Then create a Pull Request

On GitHub you'll see something like:

> Compare & pull request

Create:

```text
feature/ai-integration
            ↓
          main
```

Your team can review your code.

If everything is good:

**Merge Pull Request**

Then your code becomes part of `main`.

---

# 8. But here's the important problem

Suppose your teammate changed something in `main` while you were working.

Your branch could now be behind:

```text
main
A ── B ── C
          \
           D ── E    ← your branch
```

You should regularly bring the latest `main` into your branch.

One straightforward approach:

```bash
git checkout main
git pull origin main
```

Then:

```bash
git checkout feature/ai-integration
git merge main
```

If Git finds no conflict:

```text
Already merged successfully
```

If there is a conflict, Git will tell you which files conflict.

---

# 9. What if you and another person edit the SAME file?

This is the part you need to understand.

Suppose you both modify:

```text
src/app/chat/page.tsx
```

Your version:

```text
Hello AI
```

Their version:

```text
Welcome to SIH
```

Git may say:

```text
CONFLICT
```

You manually decide what the final version should be.

Git will show something like:

```text
<<<<<<< HEAD
Hello AI
=======
Welcome to SIH
>>>>>>> main
```

You resolve it:

```text
Welcome to SIH

Hello AI
```

Then:

```bash
git add .
git commit
git push
```

So **branches don't magically prevent conflicts**.

They prevent people from constantly overwriting each other's work and give you a controlled integration process.

---

# ⭐ For your SIH project, I'd actually recommend this structure

Since you told me your role is primarily **AI integration**, I'd organize your team approximately like:

```text
SIH-2026/
│
├── frontend/
│
├── backend/
│
├── ai/
│   ├── agents/
│   ├── tools/
│   ├── rag/
│   ├── prompts/
│   └── safety/
│
├── database/
│
├── docs/
│
├── .env.example
├── .gitignore
├── package.json
└── README.md
```

And branches:

```text
main
│
├── feature/frontend
├── feature/backend
├── feature/ai
├── feature/database
└── feature/auth
```

You would primarily work in:

```text
feature/ai
```

---

## One VERY important rule

### Don't do this:

```bash
git checkout main
# modify code
git add .
git commit
git push
```

Especially for a team project.

Instead:

```bash
git checkout -b feature/ai
```

Work → commit → push → PR → review → merge.

---

# And there's an even better workflow

For a serious SIH project, I would use:

```text
main
  │
  │  ← only stable code
  │
  ├──── Pull Request ← feature/ai
  ├──── Pull Request ← feature/frontend
  ├──── Pull Request ← feature/backend
  │
  ↓
merged
```

You can also protect `main` so that **nobody can directly push to it**.

Then GitHub forces the team to use Pull Requests.

That is much closer to how professional software teams work.

### Your daily workflow becomes

```bash
git checkout feature/ai
git pull origin main
```

Work on your AI code.

Then:

```bash
git add .
git commit -m "Implement attendance AI agent"
git push
```

Open PR → teammate reviews → merge.

Then next day:

```bash
git checkout feature/ai
git merge main
```

Continue working.

---


