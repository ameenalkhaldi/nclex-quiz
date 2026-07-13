---
name: nclex-questions
description: Generate high-yield, application-level NCLEX-style questions and add them to a topic bank in this repo. Use when a bank needs harder questions or a new topic is added.
---

# NCLEX Question Generator

Generate high-yield, challenging NCLEX-style questions and add them to a topic bank.

## When to use

Invoke with `/nclex-questions` when a bank needs harder questions, or when adding a new
topic. The complaint that triggered this skill: questions were "too easy" — pure recall
that a student can answer by memorizing a lecture. This skill produces application/analysis
items instead.

## The difficulty bar (this is the whole point)

The instructor's target is **Bloom's comprehension, analysis, and synthesis** — never
recall or "plain facts." Every strong item answers some slice of the same clinical loop:
*what is the issue → how do I assess it → what do I do about it → how do I know it worked.*
Keep stems short and NCLEX-tight.

A recall question tests one fact ("what is the term for black tarry stools?", "how does
omeprazole work?"). It is too easy. Rewrite every question so that:

- The stem is a **clinical scenario** (client age/condition, relevant vitals or labs), and
  it asks what the nurse should **DO, prioritize, question, or conclude** — never "what is X?"
- **Every option is plausible.** The answer is the *priority / first action / safest / best
  response / biggest risk*, not the only true statement. A student who memorized the lecture
  still has to reason to pick it.
- Distractors are actions a real nurse might consider, or statements that are true but not
  the priority. No throwaway wrong answers, no "always/never" giveaways.

## Question patterns that hit the bar

Aim for a **mix**, plus **one SATA per batch**. Exam 2 is **primary/chronic care** — so
balance the acute-emergency patterns (1–4) with the chronic-management, teaching, and
health-promotion patterns (5–8). Do not make every stem a deteriorating patient; the
instructor weights self-management, follow-up, and lifestyle/medication teaching heavily.

1. **Priority / triage** — "Four clients; which does the nurse assess first?" Discriminate
   with ABC, acute-vs-chronic, unstable-vs-expected. (e.g., board-like abdomen + tachycardia
   over a routine antacid request.)
2. **Question the order** — one unsafe/contraindicated prescription hidden among appropriate
   ones. Disguise the trap when possible (ketorolac *is* an NSAID; a benzodiazepine in hepatic
   encephalopathy; IV phenytoin in dextrose; IM injection at platelets 16k; blood hung with
   LR/dextrose instead of 0.9% NS; oral B12 for pernicious anemia).
3. **Complication / alarm recognition** — the client is deteriorating and the student must
   name it or act: perforation/peritonitis, toxic megacolon, hypovolemic shock, transfusion
   reaction, neutropenic fever, thromboembolism in polycythemia, B12 ataxia/fall risk.
4. **Drug-interaction / integration** — requires combining two facts (iron absorption blocked
   by calcium/antacids/dairy; iron enhanced by vitamin C; methotrexate–NSAID; SSRI–triptan).
5. **Medication reasoning** — for any drug, test one of three angles the instructor named:
   *why give it* (indication / expected effect), *how you know it worked* (the evaluation —
   Hgb & reticulocyte rise on iron; Hct falling to goal after phlebotomy; fewer flares on
   maintenance mesalamine; neuro symptoms improving on B12), or *when to hold it* (safety, on a
   second cue — aspirin/NSAIDs at low platelets, hold based on a lab or vital sign). This
   absorbs the old "right client / med safety" pattern.
6. **Lab interpretation** — give the values, ask for the conclusion or the next action. This
   exam leans hard on labs: anemia work-up (↓MCV + ↓ferritin + ↑TIBC = iron deficiency;
   ↑MCV + ↓B12 vs ↑MCV + ↓folate; reticulocyte response; ferritin = most sensitive iron store),
   CBC lines (pancytopenia, thrombocytopenia, neutropenia), and trend/marker items (Hgb
   severity bands, Hct goal in polycythemia, CRP/ESR tracking IBD activity). Any lab named in a
   slide deck is fair game — that is the instructor's explicit ask.
7. **Health promotion & self-management teaching** — the core of primary/chronic care.
   Lifestyle coaching (iron/B12/folate food sources, low-FODMAP for IBS, low-residue during IBD
   flares, exercise, smoking cessation, alcohol reduction, CRC screening at 45 with colonoscopy
   as gold standard, vaccination) and **medication adherence** — the highest-yield sub-theme:
   take meds routinely, never skip or stop abruptly (IBD maintenance meds in remission, lifelong
   IM B12, finishing iron even after symptoms improve). Also self-care and follow-up (ostomy/
   stoma care, IBD flare action plan, when to call the provider).
8. **"Needs further teaching" / negative-polarity** — the answer is the *wrong* statement the
   client made; pairs naturally with pattern 7.
9. **SATA** — subtle distractors, e.g. one plausible-but-wrong option among corrects.

## Rationales: teach with the Clinical Judgment Model

The instructor requires that every question carry a rationale for the correct answer **and**
for why each other option is wrong — and that the reasoning be tied to the NCSBN **Clinical
Judgment Measurement Model** (the same reasoning the Next-Gen NCLEX tests): *recognize cues →
analyze cues → prioritize hypotheses → generate solutions → take action → evaluate outcomes.*

Don't recite the six steps — write the rationale in their **shape**:
- A priority/triage item turns on *recognize → analyze → prioritize* ("the board-like abdomen
  and tachycardia are the cues that make perforation the priority hypothesis over the routine
  antacid request").
- A medication/intervention item turns on *generate solutions → take action*.
- A "how do you know it worked" item turns on *evaluate outcomes*.
- Every distractor is wrong for a **nameable** reason — right action/wrong priority,
  correct-but-not-yet, or unsafe given a second cue — never just "false."

## Exam 2 scope & bank layout

Exam 2 (weeks 5–8) covers **anemia, lower GI, renal, and endocrine/weight management**. The two
new Med-Surg PDFs supply a full **anemia/hematology** module (CBC & RBC indices, iron-deficiency,
B12/pernicious, folate, aplastic, anemia of chronic disease, acute vs chronic blood loss,
transfusion nursing, polycythemia) and a Med-Surg **lower-GI** module (IBS, chronic constipation
+ laxative step-up, IBD/Crohn vs UC, peritonitis, toxic megacolon, bowel obstruction, colorectal
cancer & screening, ostomy/WOC care).

**Keep the new Med-Surg banks separate from the four existing Pathopharm banks.** The Med-Surg
lower-GI content does **not** merge into `lower-gi.json`. Create two new banks —
`med-surg-anemia.json` and `med-surg-lower-gi.json` — with distinct `topic`/`label` values (e.g.
"Med-Surg: Anemia", "Med-Surg: Lower GI") so the app lists them as their own sections. Renal and
endocrine are in scope but not in these PDFs — they'll be added later. Health-promotion and
medication-adherence teaching run through every topic and should appear in every bank.

## Grounding & accuracy

- Base questions on the **same content the target bank already teaches** (read the existing
  `questions/<topic>.json` first) or on the provided source material. Highlighted / red / ⭐
  source text is highest priority — make those the hardest items.
- Every clinical claim must be correct. When you introduce a fact the bank did not already
  cover, flag it in your summary so the user can confirm it is in scope for their exam.

## Repo pipeline (how questions actually get added)

Source of truth is `questions/<topic>.json`. The app loads a generated `questions/banks.js`
(never edit that by hand). Workflow:

1. Edit `questions/<topic>.json`, **prepending** new questions to the `questions` array.
   Per-topic play order is *not* shuffled, so front = shown first; existing easier questions
   move to the back. ("All questions" mode shuffles, and options are randomized per question at
   render, so do **not** hand-balance answer positions — it has no effect on the learner.)
2. Run `python3 build.py` from the repo root. It validates rationale counts and writes
   `banks.js`. A `ValueError` means a rationale count is wrong (see schema below).
3. Verify the build mapped rationales to options (keyed rationale lands at the answer index;
   SATA has one rationale per option). A quick check: load `banks.js`, confirm
   `explanations[answer]` matches the correct option for an MC, and `len(explanations) ==
   len(options)` for a SATA.
4. Commit the `.json` and `banks.js` together and push. Do **not** add a Claude co-author
   trailer to commits in this repo.

Default batch size: ~12 challenging questions per bank per pass.

## JSON schema

**Standard multiple choice** — `answer` is the correct index; `rationale.incorrect` holds the
explanations for the **non-answer** options **in option order** (i.e. `len(options) - 1`
entries). `build.py` reinserts `rationale.correct` at the answer index.

```json
{
  "stem": "A nurse receives report on four clients. Which client should the nurse assess first?",
  "options": [
    "A client requesting a PRN antacid for 3/10 burning pain",
    "A client with a rigid, board-like abdomen and a heart rate of 124",
    "A client reporting heartburn after a large meal",
    "A client asking when their new PPI will start working"
  ],
  "answer": 1,
  "rationale": {
    "correct": "A rigid, board-like abdomen with tachycardia signals perforation with peritonitis — a surgical emergency and the priority.",
    "incorrect": [
      "A PRN antacid request for mild, expected pain is routine.",
      "Heartburn after a large meal is an expected trigger, not urgent.",
      "Teaching about PPI onset is important but not time-sensitive."
    ]
  }
}
```

A **"needs further teaching" / negative-polarity** item is standard MC: `answer` is the index
of the *wrong* statement, and `rationale.correct` explains why that option is the one requiring
teaching.

**Select all that apply** — add `"type": "sata"`; `answer` is an array of correct indices;
`rationale.incorrect` has **one entry per option** (`len(options)` entries), each starting
`Correct—…` or `Incorrect—…`. `rationale.correct` is a short summary (not shown per option, but
required).

```json
{
  "stem": "A client is admitted with acute pancreatitis. Which prescriptions does the nurse anticipate? Select all that apply.",
  "options": ["Maintain NPO status", "NG tube to low suction", "IV fluids and opioid analgesia", "Position supine and flat", "Start a high-fat oral diet now"],
  "answer": [0, 1, 2],
  "type": "sata",
  "rationale": {
    "correct": "Acute pancreatitis is managed with bowel rest — NPO, NG suction, IV fluids and analgesia; the client sits up and leans forward, and feeding (especially fat) is withheld.",
    "incorrect": [
      "Correct—NPO rests the pancreas.",
      "Correct—NG suction relieves vomiting and distention.",
      "Correct—IV fluids treat third-spacing and opioids control pain.",
      "Incorrect—lying flat worsens pain; sit up and lean forward.",
      "Incorrect—the client is kept NPO and fat stimulates the pancreas."
    ]
  }
}
```

## Quality checklist

Before building:
- [ ] Scenario stem with clinical context; asks for judgment, not a definition (Bloom's
      comprehension/analysis/synthesis, not recall).
- [ ] Every distractor is plausible; the answer is the *best/priority*, not the only true one.
- [ ] Batch is a mix of the patterns above, including one SATA, and **balances** acute items
      with chronic-management / teaching / health-promotion / medication-adherence items.
- [ ] At least a couple of lab-interpretation items using values the slide decks flagged.
- [ ] Rationale is framed in the Clinical Judgment Model (cues → hypotheses → action →
      evaluate); explains why right AND why each distractor is wrong for a nameable reason.
- [ ] No "always/never" in the correct answer.
- [ ] `rationale.incorrect` count matches the schema (MC: options−1; SATA: options).
- [ ] New questions prepended to the front of the array.

After building:
- [ ] `python3 build.py` succeeded (no ValueError).
- [ ] Spot-checked rationale→option mapping in `banks.js`.
- [ ] Any newly introduced facts flagged to the user for scope confirmation.
