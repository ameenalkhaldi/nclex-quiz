# NCLEX Question Generator

Generate high-yield, challenging NCLEX-style questions from source material.

## When to use

Invoke with `/nclex-questions` when you have nursing content and need practice questions.

## Source Material Handling

- **Red text / highlighted content**: These are HIGH PRIORITY. Generate more questions from these sections and make them the hardest questions.
- **Regular content**: Generate standard questions, but still at application/analysis level.
- Process content in chunks if needed — this skill maintains consistent quality across sessions.

## Question Structure (NCLEX Format)

Every question must have:
1. **Scenario stem**: A clinical situation with a patient (age, condition, relevant vitals/labs). Never ask "what is X?" — always ask what the nurse should DO.
2. **Question**: Asks for nursing judgment — prioritization, first action, best response, delegation, safety.
3. **4 answer options**: One correct, three plausible distractors. All grammatically consistent with the stem.
4. **Rationale**: Explains why correct answer is right AND why each distractor is wrong.

## What Makes Questions High-Yield

Focus on:
- **Safety/risk**: What could kill the patient? Airway, breathing, circulation.
- **Prioritization**: Which patient first? Which action first?
- **Delegation**: RN vs LPN vs UAP scope.
- **Assessment vs intervention**: When to assess more vs act now.
- **Therapeutic communication**: What to say (and what NOT to say).
- **Medication side effects**: Especially life-threatening ones, teaching points.
- **Lab values**: Critical values that require immediate action.

## What Makes Questions Challenging

- Distractors should be actions a nurse MIGHT consider, not obviously wrong.
- Include "assess" options when intervention is correct (and vice versa) — tests judgment.
- Use "select all that apply" (SATA) for complex topics.
- Prioritization questions where multiple answers seem correct but one is MOST correct.
- Avoid pattern recognition — don't always make the longest answer correct.

## Question Types to Generate

Mix these types:
1. **Priority/First action**: "Which patient should the nurse see first?"
2. **Assessment**: "What is the priority assessment finding?"
3. **Intervention**: "What is the nurse's best action?"
4. **Delegation**: "Which task can be delegated to the UAP?"
5. **Teaching**: "Which statement by the patient indicates understanding?"
6. **SATA**: "Select all that apply" for comprehensive topics.

## Output Format

For each question, output:

```
**Question [N]** [Topic Tag]

[Scenario stem]

[Question]

A. [Option]
B. [Option]
C. [Option]
D. [Option]

**Answer: [Letter]**

**Rationale:**
- Correct ([Letter]): [Why this is right]
- [Letter]: [Why this is wrong]
- [Letter]: [Why this is wrong]
- [Letter]: [Why this is wrong]

---
```

## Quality Checklist

Before finalizing questions, verify:
- [ ] Tests application/analysis, not just recall
- [ ] Stem provides enough clinical context
- [ ] Only ONE best answer (or clear SATA criteria)
- [ ] Distractors are plausible, not obviously wrong
- [ ] No "always" or "never" in correct answers (too obvious)
- [ ] Rationale teaches, doesn't just state "this is wrong"
