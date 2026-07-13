https://nclex-quiz.pages.dev/


# NCLEX Practice

A small, free study tool I built to help nursing students practice NCLEX-style
questions. It runs entirely in the browser — no accounts, no installs, no
internet connection required once you have the files.

I made this while studying for Pathopharmacology and wanted a fast, no-frills
way to drill practice questions with clear rationales for every answer choice.

## What's inside

The app currently has **353 practice questions** across six topic banks:

| Topic | Questions |
| --- | --- |
| Upper GI | 65 |
| Lower GI | 79 |
| Neoplasms & Cancer | 99 |
| Migraine · Insomnia · Seizures | 70 |
| Med-Surg: Anemia | 20 |
| Med-Surg: Lower GI | 20 |

The four Pathopharm banks and the two Med-Surg banks are kept separate — the
Med-Surg Lower GI bank is distinct from the Pathopharm Lower GI bank.

Every question is written in NCLEX style and includes:

- A realistic client scenario or knowledge stem
- An **explanation for every option** — not just the right one — so you learn
  why the wrong answers are wrong
- **Select all that apply (SATA)** questions where appropriate
- Answer shuffling so you can't memorize positions

## How to use it

**Option 1 — just open it.** Download or clone the repo and open `index.html`
in any web browser. That's it. It works straight from your file system.

**Option 2 — GitHub Pages.** If you host this repo with GitHub Pages, the quiz
is available at your Pages URL and you can study from your phone.

## For studying vs. adding your own questions

The questions live as plain, human-readable files in the `questions/` folder —
one JSON file per topic. If you want to add or edit questions:

1. Edit the relevant file in `questions/` (e.g. `questions/upper-gi.json`).
2. Run the build script to regenerate the file the app loads:
   ```
   python3 build.py
   ```
3. Open `index.html` to see your changes.

Each question follows this shape:

```json
{
  "stem": "A client reports ... Which finding should the nurse expect?",
  "options": ["Option A", "Option B", "Option C", "Option D"],
  "answer": 1,
  "rationale": {
    "correct": "Why Option B is right.",
    "incorrect": [
      "Why Option A is wrong.",
      "Why Option C is wrong.",
      "Why Option D is wrong."
    ]
  }
}
```

For SATA questions, add `"type": "sata"` and make `answer` a list of the
correct option indexes.

## A note

These questions were written for personal study and are not affiliated with the
NCLEX or the NCSBN. They're meant as a practice aid — always study from your
course materials and verified resources too. Good luck on your exams! 🩺
