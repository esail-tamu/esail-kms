---
tags:
  - file-management
  - beginner
---

# File Naming Convention

[:material-folder-zip-outline: Download the starter project folder structure](downloads/course-project-template.zip){ .md-button }

## Why it matters

Consistent file naming makes files searchable, sortable, and predictable across teams and tools — a file's name alone should tell you what course it belongs to, which module and topic it covers, and what kind of content it is, without opening it.

Every course project at ESAIL has two sides:

- **SME-Content** — a loosely-organized intake area for whatever the subject-matter expert (instructor) hands off. It isn't enforced; we just want the content.
- **eSAIL-Production** — where ESAIL organizes, edits, and finalizes that content for Canvas, split into a working stage and a finished stage.

## Folder structure

```text
26C-ENGR123-Abbrev-Title-Lastname/
├── 26C-ENGR123-course-map.xlsx
├── 26C-ENGR123-recording-schedule.xlsx
├── 01-SME-Content/
│   ├── Assignments/
│   ├── Discussions/
│   ├── Exams/
│   ├── Labs/
│   ├── Lectures/
│   ├── Other/
│   ├── Projects/
│   ├── Quizzes/
│   └── Slides/
└── 02-eSAIL-Production/
    ├── 01-Syllabus/
    ├── 02-Work/
    │   ├── Assignments/
    │   ├── Discussions/
    │   ├── Exams/
    │   ├── Labs/
    │   ├── Lectures/
    │   ├── Projects/
    │   ├── Quizzes/
    │   └── Slides/
    └── 03-Final/
        ├── Assignments/
        ├── Discussions/
        ├── Exams/
        ├── Labs/
        ├── Lectures/
        ├── Projects/
        ├── Quizzes/
        └── Slides/
```

- `01-SME-Content` and `02-eSAIL-Production` are **numbered** so they always sort in that order in a file browser, regardless of case — same reason `01-Syllabus`, `02-Work`, `03-Final` are numbered rather than alphabetical (which would otherwise read Final, Syllabus, Work).
- `02-Work` and `03-Final` always mirror the same eight content-type categories, so nothing is ever "missing" a folder even if unused for a given course.
- `Other` only exists on the SME side, for anything that doesn't fit one of the eight categories (administrative files, misc handouts).
- `course-map.xlsx` and `recording-schedule.xlsx` live at the very top, outside both sides, since they track the whole project rather than belong to one side.

Download the starter structure above and rename the top folder, course code, and instructor name for your project.

## Naming the project folder

```text
26C   -  ENGR123  -  Abbrev-Title  -  Lastname
term     course      short title     instructor
```

| Field | Rule | Example |
|---|---|---|
| Term | 2-digit year + a letter for the term: `A` = Spring, `B` = Summer, `C` = Fall | `26C` = Fall 2026 |
| Course | Subject + catalog number, **no separator between them** | `ENGR123`, not `ENGR-123` |
| Short title | An abbreviated course title, hyphens between words | `Intro-to-Robotics` |
| Instructor | The instructor's last name | `Smith` |

## The hyphen / underscore rule

Everywhere in this convention:

- **Hyphens (`-`) separate structured fields** — term, course, module, topic, type.
- **Underscores (`_`) join words inside a single free-text field**, like a descriptive title.

This is why a video file name reads `ENGR123-M01-T01-Intro_to_Loops.mp4`: hyphens mark where one field ends and the next begins, and underscores show that `Intro_to_Loops` is one title, not three fields.

## Naming instructional objects

Inside `02-Work` and `03-Final`, individual files follow:

```text
ENGR123 - M01 - T01 - Title_Or_Type.ext
course    mod   topic   title/type
```

| Field | Rule | Example |
|---|---|---|
| Course | Same course code as the project folder, no year | `ENGR123` |
| Module | Two-digit module number | `M01` |
| Topic | Two-digit topic number within the module. `T00` means the item applies to the **whole module**, not one topic | `T01`, or `T00` for a module-wide item |
| Title or type | A descriptive title (underscored) for things like videos and slides, or a type + index (`Quiz01`, `Assignment01`) for repeatable graded items | `Intro_to_Loops`, `Quiz01` |

**Exceptions — Exams and Projects drop the module/topic code entirely**, since they usually span multiple modules or the whole course rather than belonging to one:

```text
ENGR123-Exam01.md
ENGR123-Project01.md
```

**Exception — the Syllabus keeps the term code**, since a syllabus is specific to one term's offering, unlike other inner files:

```text
26C-ENGR123-Syllabus.pdf
```

## Examples

| File name | Meaning |
|---|---|
| `26C-ENGR123-Abbrev-Title-Lastname` | The project folder for ENGR123, Fall 2026, taught by Lastname |
| `26C-ENGR123-course-map.xlsx` | The course map for that same project |
| `26C-ENGR123-Syllabus.pdf` | The syllabus for the Fall 2026 offering |
| `ENGR123-M01-T01-Course_Introduction.mp4` | Module 1, Topic 1 video: "Course Introduction" |
| `ENGR123-M01-T04-Assignment01.md` | Module 1, aligned specifically to Topic 4: Assignment 1 |
| `ENGR123-M02-T00-Discussion01.md` | Module 2, applies to the whole module (not one topic): Discussion 1 |
| `ENGR123-Exam01.md` | Exam 1, course-wide — no module/topic code |

## Tracking content: the course map

The downloadable template includes `26C-ENGR123-course-map.xlsx` — a spreadsheet that inventories every piece of content (week, module, topic, title, file name) alongside an eSAIL production checklist (video editing, captions, ID check, SME review, Canvas upload, etc.), plus links to the source file and its Descript editing project. See its **Legend** tab for a full column-by-column reference.

## Check your understanding

[:material-clipboard-check-outline: Take the 10-question quiz](quiz.md){ .md-button }
