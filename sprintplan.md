## ⏱️ 00:00–00:08 (8 min)

### ✅ Supabase Project + Local Setup

| Task                    | How to Speed Up                  |
| ----------------------- | -------------------------------- |
| Create Supabase project | Use web GUI (no CLI delay)       |
| Run `supabase init`     | Autocomplete `.env` with Copilot |
| Open VS Code workspace  | Pre-load Supabase + SQL plugins  |

> 🔧 **Prompt AI:** “Generate `.env` template for Supabase + Vite + Prisma (optional) setup.”

---

## ⏱️ 00:08–00:20 (12 min)

### ✅ Auto-Generate Schema with Copilot/Cody

**Strategy:** Instead of hand-writing SQL, use structured prompts to output enums and tables fast.

**Prompt AI:**

```
Create SQL for a Supabase-compatible task manager with the following:
- users, tasks, reminders, events, recurring_rules
- use UUIDs as PK
- enums for status, priority, mood, integration
- timestamp fields
- relational constraints and JSONB for preferences
```

| Step                       | Tool Usage                                    |
| -------------------------- | --------------------------------------------- |
| Paste into `schema.sql`    | Let Copilot auto-complete missing constraints |
| Use SQL editor in Supabase | Copy + run the whole script                   |
| Check schema browser       | Verify relationships visually                 |

---

## ⏱️ 00:20–00:30 (10 min)

### ✅ AI-Generated RLS & Policies

**Prompt AI:**

```
Write Row Level Security (RLS) policies for Supabase to ensure:
- users can only read/update their own tasks, reminders, and mood logs
```

| Task                   | Output                            |
| ---------------------- | --------------------------------- |
| Enable RLS via UI      | Manual click, or SQL              |
| Apply AI-generated SQL | Copilot often gets this 90% right |

> 🔐 Pro Tip: Prompt for both **RLS syntax** and **Supabase auth integration** in policies

---

## ⏱️ 00:30–00:45 (15 min)

### ✅ API Layer: AI-Scaffolded Routes

**Goal:** Auto-generate the backend logic to connect Supabase → your app.

**Prompt AI:**

```
Create Next.js API route to:
- fetch all tasks for current Supabase user
- insert new task with title, priority, due date
```

| Stack        | Shortcut                                               |
| ------------ | ------------------------------------------------------ |
| Node/Express | Use `supabase-js` and let AI scaffold routes           |
| Next.js      | Use `/api/tasks.ts` with Supabase client logic         |
| Astro/Solid  | AI prompt: “Supabase task POST handler in X framework” |

---

## ⏱️ 00:45–00:55 (10 min)

### ✅ Quick Frontend UI (Optional)

| Goal             | Tool Prompt                                                        |
| ---------------- | ------------------------------------------------------------------ |
| Add Task Form    | “React form to add a task (title, due date) using Supabase client” |
| List Tasks       | “Component to list tasks grouped by status, fetched from Supabase” |
| Tailwind Styling | “Apply minimalist Tailwind styling to task list”                   |

Use **AI autocompletion** for:

* Supabase hooks (`useEffect` + `supabase.from()`)
* Form handlers
* Schema-based form validation (Zod/Yup)

---

## ⏱️ 00:55–01:00 (5 min)

### ✅ Local Testing + Git Commit

| Action         | Notes                                                        |
| -------------- | ------------------------------------------------------------ |
| Seed test data | Copilot: “Insert test tasks with different due dates/status” |
| Run UI         | Test task CRUD via browser                                   |
| Git commit     | Push schema + `/api` + `/components` scaffolds               |

---

## 🧠 Summary: What You Accomplish in 1 Hour

| Layer            | Delivered        |
| ---------------- | ---------------- |
| Supabase Project | ✅                |
| DB Schema (Core) | ✅ via AI         |
| RLS & Policies   | ✅ AI generated   |
| REST API         | ✅ AI scaffolded  |
| Basic UI         | ⚪ Optional       |
| Test Data        | ✅ Seeded         |
| Git Repo         | ✅ Initial commit |

---

## 🧩 Suggested Prompt Library

| Feature       | AI Prompt                                                          |
| ------------- | ------------------------------------------------------------------ |
| Task Model    | “PostgreSQL schema for a task with due date, status, and category” |
| Reminder Flow | “Generate SQL for recurring reminders tied to task table”          |
| API Route     | “Express POST endpoint to add a task to Supabase”                  |
| Auth Flow     | “Check if Supabase user is authenticated, then fetch user tasks”   |
| UI Form       | “React form with Tailwind to add a Supabase task”                  |

---

## 🚀 Bonus: AI Pairing Strategy

| Role  | Developer       | AI Assistant                                     |
| ----- | --------------- | ------------------------------------------------ |
| Dev A | Schema/modeling | Review/enrich Copilot-generated SQL              |
| Dev B | API/Client      | Prompt AI to scaffold handlers, insert docs      |
| Dev ⟳ | Rotate roles    | Every 20 mins, switch AI prompter vs implementer |


