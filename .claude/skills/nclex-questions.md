# NCLEX Question Generator

Generate high-yield, challenging NCLEX-style questions and add them to a topic bank.

## When to use

Invoke with `/nclex-questions` when a bank needs harder questions, or when adding a new
topic. The complaint that triggered this skill: questions were "too easy" — pure recall
that a student can answer by memorizing a lecture. This skill produces application/analysis
items instead.

## The difficulty bar (this is the whole point)

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

Use these — they are the patterns applied across the existing banks. Aim for a mix, plus
**one SATA per batch**.

1. **Priority / triage** — "Four clients; which does the nurse assess first?" Discriminate
   with ABC, acute-vs-chronic, unstable-vs-expected. (e.g., board-like abdomen + tachycardia
   over a routine antacid request.)
2. **Question the order** — one unsafe/contraindicated prescription hidden among appropriate
   ones. Disguise the trap when possible (ketorolac *is* an NSAID; a benzodiazepine in hepatic
   encephalopathy; IV phenytoin in dextrose; IM injection at platelets 16k).
3. **Complication / alarm recognition** — the client is deteriorating and the student must
   name it or act: perforation, hemorrhagic shock, toxic megacolon, thunderclap headache/SAH,
   neutropenic fever, vesicant extravasation, serotonin syndrome, GVHD, HBV reactivation.
4. **Drug-interaction / integration** — requires combining two facts (cimetidine CYP450 across
   warfarin/phenytoin/theophylline; grapefruit–cyclosporine; phenytoin–oral contraceptive;
   methotrexate–NSAID; SSRI–triptan).
5. **Right client / med safety** — withhold or monitor based on a second variable (misoprostol
   in pregnancy; carbamazepine → CBC; tenofovir → renal/phosphate; abacavir → HLA-B*5701).
6. **Teaching / "needs further teaching"** — negative-polarity item; the answer is the *wrong*
   statement the client made.
7. **SATA** — subtle distractors, e.g. one plausible-but-wrong option among corrects.

## Grounding & accuracy

- Base questions on the **same content the target bank already teaches** (read the existing
  `questions/<topic>.json` first) or on the provided source material. Highlighted / red source
  text is highest priority — make those the hardest items.
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
- [ ] Scenario stem with clinical context; asks for judgment, not a definition.
- [ ] Every distractor is plausible; the answer is the *best/priority*, not the only true one.
- [ ] Batch is a mix of the patterns above, including one SATA.
- [ ] Rationales teach (why right / why each is wrong), not just "this is wrong."
- [ ] No "always/never" in the correct answer.
- [ ] `rationale.incorrect` count matches the schema (MC: options−1; SATA: options).
- [ ] New questions prepended to the front of the array.

After building:
- [ ] `python3 build.py` succeeded (no ValueError).
- [ ] Spot-checked rationale→option mapping in `banks.js`.
- [ ] Any newly introduced facts flagged to the user for scope confirmation.
