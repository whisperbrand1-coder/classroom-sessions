# StudyPal — Grade 5, Session 3, Lesson 4

Open these in **mBlock 5**: `File → Open`.

The G5 track is **Python inside mBlock**, not drag-and-drop blocks. Click a sprite and
switch the editor tab to **Python** to see the code. (Deck slide 2 says "Advanced Python
Programming"; the Teaching Guide's Preparation line says "Familiar with Python syntax".)

## One file per stage

Each file is the project up to that stage, and each one **runs on its own**. Teach from
`0_START` and add lines as you go; if a student falls behind or breaks their project,
hand them the file for the stage the class is on and they carry on without catching up.

| File | StudyPal | What works |
|---|---|---|
| `StudyPal_0_START.mblock` | empty | schedule only — **open this one in class** |
| `StudyPal_1_it_talks.mblock` | 4 lines | click the robot, it speaks |
| `StudyPal_2_it_asks.mblock` | 5 lines | it asks a question and echoes the answer |
| `StudyPal_3_add.mblock` | 9 lines | `add` stores a task in a list |
| `StudyPal_4_show.mblock` | 12 lines | `show` reads the list back, numbered |
| `StudyPal_5_done.mblock` | 16 lines | `done` removes one — **this is the goal** |
| `StudyPal_6_FINAL.mblock` | 31 lines | plus the `else` branch and the two buttons |

Every stage keeps the Lesson-3 schedule working, so a lost project can be restored from
any of them.

All the code lives on **one sprite** (StudyPal). Click the robot, then type `add`, `show`
or `done`. That is deliberate: in mBlock each sprite has its own scope, so a list kept on
a button is invisible to every other button.

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

The staged files fix all three, and the teaching notes in `MY_CHATBOT_GUIDE.html` turn
bugs 1 and 3 into deliberate lesson moments rather than accidents.
