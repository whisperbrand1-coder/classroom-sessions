# StudyPal — Grade 5, Session 3, Lesson 4

Open these in **mBlock 5**: `File → Open`.

The G5 track is **Python inside mBlock**, not drag-and-drop blocks. Click a sprite and
switch the editor tab to **Python** to see the code. (Deck slide 2 says "Advanced Python
Programming"; the Teaching Guide's Preparation line says "Familiar with Python syntax".)

## What to open in class

| File | State | Use it for |
|---|---|---|
| `StudyPal_L4_TEACHER.mblock` | everything works | the 2-minute demo at the start, and as your own reference |
| `StudyPal_L4_START.mblock` | schedule works, To-Do is missing | this is the one you code live with the class |

Both start with the day buttons hidden and the To-Do buttons visible. Green flag →
StudyPal says hello. Click **StudyPal** for the schedule, the **green** button to add a
task, the **red** button to tick one off.

## Why these exist

`official_broken/` holds the three project files the Teaching Guide links to
(instructor-only Google Drive links). They are kept for reference — **they do not run**:

- **Chatbot 1** (Lesson 2) — button sprites only, no code at all. That is by design.
- **Chatbot 2** (Lesson 3) — the schedule, mostly working.
- **Chatbot 3** (Lesson 4) — a byte-for-byte copy of Chatbot 2 with two extra hidden
  sprites and **no new code**. There is no official To-Do implementation.

Three failures were reproduced by running the code:

1. The main menu prints `To Do` but compares against `'To do'`, so the prompt as
   displayed always falls through to "Error, wrong option".
2. Four of the five day sprites assign `task = 'ToDo'` without a `global` declaration,
   so the module-level variable never changes and those buttons do nothing.
3. `statusList[status]` indexes a list with the string returned by `input()`, raising
   `TypeError: list indices must be integers or slices, not str`.

The rebuilt files above fix all three, and move the task list onto a single sprite so
every button shares one list instead of each button keeping a private copy.
