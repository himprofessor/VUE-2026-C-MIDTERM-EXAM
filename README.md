# 🧩 Vue.js Midterm Practical Exam

### Mini Task Management Application

Welcome to your Vue.js Midterm Practical Exam! 🎉

This exam is your chance to show what you have learned and to build something real with your own hands. Read this README carefully from top to bottom **before** you start coding. Everything you need is right here — no internet required.

> 💡 **Take a deep breath.** You already know the concepts. This exam just asks you to put them together. Build step by step, and you'll do great.

---

## 📚 Table of Contents

1. [Exam Objective](#-1-exam-objective)
2. [Exam Scenario](#-2-exam-scenario)
3. [Application Preview](#-3-application-preview)
4. [Technical Requirements](#-4-technical-requirements)
5. [Required Components](#-5-required-components)
6. [Features to Implement](#-6-features-to-implement)
7. [Starter Data](#-7-starter-data)
8. [Guidelines for Success](#-8-guidelines-for-success)
9. [Evaluation Criteria](#-9-evaluation-criteria)
10. [Submission Instructions](#-10-submission-instructions)
11. [Bonus Challenge (Optional)](#-11-bonus-challenge-optional)

---

## 🎯 1. Exam Objective

The purpose of this exam is to evaluate how well you understand and can apply the **core fundamentals of Vue.js** that we have studied in class.

By completing this project, you will demonstrate your ability to:

- ✅ Understand and use **Vue fundamentals** (template syntax & directives)
- ✅ Build a clean, organized **component-based** application
- ✅ Pass data correctly using **Props**
- ✅ Communicate from child to parent using **Emit**
- ✅ Create reusable layouts using **Slots**
- ✅ Render a clear, working **user interface**
- ✅ Keep your **code organized and readable**

> 🌟 You are not expected to build something perfect or fancy. You are expected to show that you understand *how Vue works*. Focus on correctness and clarity.

---

## 🏢 2. Exam Scenario

You have just joined a small **productivity startup** as a junior frontend developer. 🚀

The team needs a simple **Task Management App** that allows users to see their daily tasks, mark tasks as complete, and remove tasks they no longer need.

Your manager has asked you to build the **first prototype** of this app using **Vue 3** and a clean **component-based architecture**. The data is already provided for you — your job is to bring it to life on the screen.

This is your moment to shine and prove you can build a real, working feature. 💪

---

## 🖼️ 3. Application Preview

Your finished application should contain the following parts. Use this wireframe as a guide for *what to build* — you do **not** need to match it pixel-by-pixel. Functionality matters more than styling.

```text
┌─────────────────────────────────────────────┐
│   📋  My Tasks                                │   ← Header
│   You have 3 tasks today                      │
├─────────────────────────────────────────────┤
│                                               │
│  ┌─────────────────────────────────────────┐ │
│  │ Finish Vue homework        [ ✅ Done ]   │ │   ← Task Card
│  │ Status: ● Pending                        │ │   ← Status Badge
│  │              [ Complete ]   [ Delete ]   │ │   ← Buttons
│  └─────────────────────────────────────────┘ │
│                                               │
│  ┌─────────────────────────────────────────┐ │
│  │ Buy groceries                            │ │
│  │ Status: ● Completed                      │ │
│  │              [ Complete ]   [ Delete ]   │ │
│  └─────────────────────────────────────────┘ │
│                                               │
└─────────────────────────────────────────────┘
```

**Empty state** — when there are no tasks left, show a friendly message instead of an empty screen:

```text
┌─────────────────────────────────────────────┐
│   📋  My Tasks                                │
├─────────────────────────────────────────────┤
│                                               │
│           🎉 No tasks left!                   │
│        Enjoy your free time.                  │
│                                               │
└─────────────────────────────────────────────┘
```

### What your UI must include

| Element | Description |
| --- | --- |
| **Header** | A title for the app (e.g., "My Tasks"). May also show a task count. |
| **Task List** | The container that renders all task cards. |
| **Task Card** | A single card showing one task's title, status, and buttons. |
| **Buttons** | A **Complete** button and a **Delete** button on each task. |
| **Status Badge** | A small label showing whether a task is *Pending* or *Completed*. |
| **Empty State** | A friendly message shown when no tasks remain. |

---

## ⚙️ 4. Technical Requirements

### ✅ You MUST use

- **Vue 3** (Composition API or Options API — your choice)
- **Components** (component-based structure)
- **Props** (to pass data into child components)
- **Emit** (to send events from child to parent)
- **Slots** (at least one reusable component using slots)
- **Directives** — `v-if`, `v-for`, `v-bind`, `v-model`

### 🚫 You MUST NOT use

- ❌ Vue Router
- ❌ Pinia (or Vuex / any state management library)
- ❌ Any API or `fetch` requests
- ❌ `localStorage` / `sessionStorage`
- ❌ External UI frameworks (Bootstrap, Tailwind, Vuetify, Element Plus, etc.)

> ⚠️ **Important:** Using any forbidden tool from the list above may result in point deductions. Keep it simple and use only what we learned in class. Plain CSS is allowed and welcome. 🎨

---

## 🧱 5. Required Components

Organize your project using the structure below. Each component has **one clear responsibility** — this is good practice and part of your grade.

```text
src/
 ├── App.vue                  ← Root component (holds the task data)
 ├── components/
 │    ├── TaskList.vue        ← Renders the list of tasks
 │    ├── TaskCard.vue        ← Displays a single task
 │    └── BaseCard.vue        ← Reusable card wrapper (uses slots)
```

### Component Responsibilities

| Component | Responsibility |
| --- | --- |
| **App.vue** | The "brain" of the app. Holds the `tasks` array, and handles **complete** and **delete** logic when child components emit events. |
| **TaskList.vue** | Receives the tasks array as a **prop**, loops through it with `v-for`, and shows the **empty state** when the list is empty. |
| **TaskCard.vue** | Receives **one task** as a prop, displays its title, status badge, and buttons. **Emits** events when a button is clicked. |
| **BaseCard.vue** | A reusable wrapper that provides a consistent card style. Uses a **slot** so other components can place any content inside it. |

> 💡 **Tip:** Data flows **down** through props (parent → child). Events flow **up** through emit (child → parent). Keep this picture in your head the whole time. ⬇️⬆️

---

## ✅ 6. Features to Implement

Below is your full feature checklist. Each feature lists its **objective**, **expected behavior**, and the **Vue concepts** involved. Work through them one by one.

### Feature 1 — Display the Task List

- [ ] **Objective:** Show all tasks on the screen.
- **Expected behavior:** Each task in the data appears as its own card.
- **Vue concepts:** `props`, `v-for`, component rendering.

### Feature 2 — Use `v-for` to Render Tasks

- [ ] **Objective:** Loop through the tasks array dynamically.
- **Expected behavior:** Adding or removing a task updates the screen automatically. A unique `:key` is used.
- **Vue concepts:** `v-for`, `v-bind` (`:key`).

### Feature 3 — Conditional Rendering (Empty State)

- [ ] **Objective:** Show a friendly message when there are no tasks.
- **Expected behavior:** If the list is empty, the task cards are hidden and the empty-state message appears instead.
- **Vue concepts:** `v-if` / `v-else`.

### Feature 4 — Status Badge

- [ ] **Objective:** Show whether each task is *Pending* or *Completed*.
- **Expected behavior:** The badge text (and ideally color) reflects the task's `completed` value.
- **Vue concepts:** `v-if` / `v-bind`, conditional class or text.

### Feature 5 — Complete Task Button

- [ ] **Objective:** Let the user mark a task as complete.
- **Expected behavior:** Clicking **Complete** on a card flips that task's status to *Completed*. The badge updates.
- **Vue concepts:** `emit`, event handling, parent state update.

### Feature 6 — Delete Task Button

- [ ] **Objective:** Let the user remove a task.
- **Expected behavior:** Clicking **Delete** removes that task from the list. The screen updates immediately.
- **Vue concepts:** `emit`, array filtering in the parent.

### Feature 7 — Emit Events to Parent

- [ ] **Objective:** Communicate from child (`TaskCard`) to parent (`App`).
- **Expected behavior:** `TaskCard` does **not** change the data itself — it emits an event, and `App.vue` performs the actual change.
- **Vue concepts:** `emit`, props-down / events-up pattern.

### Feature 8 — Reusable `BaseCard` with Slots

- [ ] **Objective:** Build one reusable card component used by your tasks.
- **Expected behavior:** `BaseCard` provides the card "frame," and the content placed between its tags is rendered inside via a slot.
- **Vue concepts:** `slots`, component reuse.

> 🧪 **Self-check:** Before submitting, click every button at least once and confirm the UI reacts the way you expect.

---

## 🗂️ 7. Starter Data

Use the following dummy data as the starting point for your app. Place it in **`App.vue`** as the source of truth. You may copy it exactly.

```js
const tasks = [
  {
    id: 1,
    title: "Finish Vue homework",
    completed: false
  },
  {
    id: 2,
    title: "Buy groceries",
    completed: true
  },
  {
    id: 3,
    title: "Call the dentist",
    completed: false
  },
  {
    id: 4,
    title: "Read one chapter of a book",
    completed: false
  }
];
```

> 📝 **Note:** Each task has a unique `id`. Use it as your `:key` in `v-for`, and use it to know which task to complete or delete.

---

## 🌟 8. Guidelines for Success

You have everything you need to succeed. Follow these tips and work calmly. 🧘

1. **🏗️ Start from the component structure.** Create your empty `.vue` files first, then fill them in. A clear structure makes everything easier.
2. **🐾 Build step by step.** Get tasks displaying first. Then add the badge. Then the buttons. Don't try to do everything at once.
3. **🔍 Test props carefully.** When passing data into a component, `console.log` the prop inside the child to confirm it arrived correctly.
4. **📛 Check your emit event names.** The name you `emit` in the child must **exactly match** the name you listen for (`@event-name`) in the parent. A typo here is the #1 cause of "it's not working." 
5. **🎯 Focus on functionality first, styling later.** A working ugly app scores more than a beautiful broken one. Polish the look only after the logic works.
6. **🐞 Use `console.log` for debugging.** When something doesn't work, log values to see what your data actually looks like. This is a professional habit.
7. **💾 Save often and check the browser.** Vue updates live — keep your browser open beside VS Code and watch your changes appear.

> ❤️ **Remember:** Getting stuck is part of programming. Stay calm, re-read the relevant feature above, and check your props and emit names. You've got this!

---

## 🏆 9. Bonus Challenge (Optional)

Finished early and feeling confident? Try one or more of these optional challenges. They are **extra** and will **not** hurt your score if you skip them — but they can earn small bonus recognition and help you grow. 🌱

- ⭐ **Task Counter:** Show how many tasks are *pending* vs *completed* in the header (e.g., "2 pending, 1 completed").
- ⭐ **Filter Buttons:** Add buttons to show *All*, *Pending*, or *Completed* tasks using `v-if`/`v-for`.
- ⭐ **Dynamic Color Badge:** Make the status badge change color based on the task status using `v-bind` on `class` or `style`.

> 🧠 **Note:** Only attempt the bonus once your core features all work. A solid core project is always more important than an incomplete fancy one.

---

### 🍀 Good luck — you've prepared for this. Build calmly, test often, and trust what you know. We can't wait to see what you create!
