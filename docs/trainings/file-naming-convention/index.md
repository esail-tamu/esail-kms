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
26C-ENGR123-Abbrev_Title-SMELastname/
├── ENGR123-Course_Map-26C.xlsx
├── ENGR123-Recording_Schedule-26C.xlsx
├── ENGR123-Syllabus-26C.pdf
├── 01-SME-Content/
└── 02-eSAIL-Production/
    ├── Work/
    └── Final/
```

- `01-SME-Content` and `02-eSAIL-Production` are **numbered** so they always sort in that order in a file browser, regardless of case. `Work` and `Final` aren't — with only the two of them, numbering doesn't buy much, so they're left simple.
- **No enforced subfolders inside `SME-Content`, `Work`, or `Final`.** With file naming carrying the type code (`VID`, `QIZ`, `ASG`, etc.), a folder-level category isn't doing much extra work — so these are left flat. Using subfolders to group things by content type is a fine recommendation if it helps you browse, just not a requirement; a strong file name should make a file identifiable on its own either way.
- The **Syllabus is a plain top-level file**, not its own folder, alongside `Course_Map-26C.xlsx` and `Recording_Schedule-26C.xlsx` — all three track the whole project rather than living inside the SME or eSAIL side. Notice the term code `26C` only ever leads a name on the project folder itself; on every file, it trails at the end instead — see [Naming instructional objects](#naming-instructional-objects).

Download the starter structure above and rename the top folder, course code, and instructor name for your project.

## Naming the project folder

```text
26C   -  ENGR123  -  Abbrev_Title  -  SMELastname
term     course      course title     instructor
```

| Field | Rule | Example |
|---|---|---|
| Term | 2-digit year + a letter for the term: `A` = Spring, `B` = Summer, `C` = Fall | `26C` = Fall 2026 |
| Course | Subject + catalog number, **no separator between them** | `ENGR123`, not `ENGR-123` |
| Course title | An abbreviated course title, **underscores between words, each word capitalized** — this is the one place a title keeps its capitalization, since it's the course's own name, not a content descriptor | `Intro_Robotics` |
| Instructor | The instructor's (the SME's) last name — the template placeholder says `SMELastname` specifically so it doesn't get mistaken for the eSAIL producer's name | `Smith` |

## The hyphen / underscore rule

Everywhere in this convention:

- **Hyphens (`-`) separate structured fields** — term, course, module, topic, type.
- **Underscores (`_`) join words inside a single field** — a descriptive title, or a multi-word category label.
- **Free-text content descriptors are lowercase** (what a video or reading is *about*) — **but category labels are capitalized** (what *kind* of thing it is): the course title in the project folder name, type codes, and labels like `Homework`/`Exam`/`Project`/`Part-A`.

This is why a video file name reads `ENGR123-M01-T01-VID-intro_to_loops.mp4`: hyphens mark where one field ends and the next begins, `VID` is capitalized because it names a category (the Canvas tool), and `intro_to_loops` is lowercase because it's describing content, not a category.

## Naming instructional objects

Every file name leads with the course code, then whatever locates it, then a 3-letter **type code** — not just a label, but the actual Canvas tool the content uses. Slides reuse `VID` (they're not a distinct Canvas tool, and it keeps them sorted next to their video), and `UNK` is a placeholder for when the tool hasn't been decided yet.

| Code | Canvas tool |
|---|---|
| `VID` | Video (also used for a video's accompanying slide deck) |
| `QIZ` | Quiz |
| `ASG` | Assignment — also covers Homework, Exam, and Project, since Canvas implements all of those as an Assignment under the hood |
| `DIS` | Discussion |
| `FIL` | Files / attachment tool — standalone distributable documents (readings, professor notes) |
| `UNK` | Tool not yet decided |

There are two shapes, depending on whether the content belongs to one point in the course or to the course as a whole:

**Topic-anchored** — the locator leads, straight after the course code:

```text
ENGR123 - M01 - T01 - VID - intro_to_loops.mp4
course     mod   topic type   descriptor
```

**Absolute, course-wide** — no Module/Topic, ever. These are numbered globally, so "Quiz 5" always means the same file no matter which module it came up in — the course map spreadsheet is the source of truth for exactly which module/topic something relates to, not the file name:

```text
ENGR123 - QIZ - 01 . md
course    type  index

ENGR123 - ASG - Homework - 01 - differential_equations.md
course    type   label    index    descriptor
```

A label after the type code (`Homework`, `Exam`, `Project`) is optional, and only earns its place when the type code alone is ambiguous about which flavor this is — which is mostly `ASG`, since it covers several different kinds of submission. `QIZ` or `DIS` rarely need one. A redundant label (`QIZ-Quiz-01`) isn't wrong, just unnecessary.

Descriptors are always optional, but strongly recommended for `VID`.

**Multi-part** content gets a `-Part-A` / `-Part-B` suffix — capitalized, since it's hierarchical/structural, not content. Use it for genuine sequential parts, or just to tell apart two items that would otherwise land on an identical name:

```text
ENGR123-M01-T01-VID-intro_to_loops-Part-A.mp4
ENGR123-ASG-Exam-01-Part-A.md
```

**Exception — the Syllabus keeps the term code**, as a trailing qualifier after the label (not a leading prefix like the project folder). That way, if a designer keeps several draft versions of the syllabus around while updating it for a new term, they all sort together under `ENGR123-Syllabus-...`:

```text
ENGR123-Syllabus-26C.pdf
```

## Examples

| File name | Meaning |
|---|---|
| `26C-ENGR123-Abbrev_Title-Lastname` | The project folder for ENGR123, Fall 2026, taught by Lastname |
| `ENGR123-Course_Map-26C.xlsx` | The course map for that same project |
| `ENGR123-Syllabus-26C.pdf` | The syllabus for the Fall 2026 offering |
| `ENGR123-M01-T01-VID-intro_to_loops.mp4` | Module 1, Topic 1 video: "Intro to Loops" |
| `ENGR123-M01-T01-VID-intro_to_loops.pptx` | That same video's slide deck — same name, different extension |
| `ENGR123-QIZ-01.md` | Quiz 1, course-wide — no module/topic code |
| `ENGR123-DIS-05-ethics_in_ai.md` | Discussion 5, course-wide: "Ethics in AI" |
| `ENGR123-ASG-Homework-01-differential_equations.md` | Assignment, labeled as homework since "Assignment" alone wouldn't tell you that: Homework 1 |
| `ENGR123-ASG-Exam-01.md` | An exam — implemented as an Assignment in Canvas, labeled `Exam` so a human can tell at a glance |
| `ENGR123-M01-T01-VID-intro_to_loops-Part-A.mp4` | Part A of a multi-part video for Module 1, Topic 1 |

## Tracking content: the course map

The downloadable template includes `ENGR123-Course_Map-26C.xlsx` — a spreadsheet that inventories every piece of content (week, module, topic, title, file name) alongside an eSAIL production checklist (video editing, captions, ID check, SME review, Canvas upload, etc.), plus links to the source file and its Descript editing project. See its **Legend** tab for a full column-by-column reference.

## Check your understanding

[:material-clipboard-check-outline: Take the 10-question quiz](quiz.md){ .md-button }
