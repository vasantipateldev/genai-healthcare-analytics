# Prompt Engineering Cheat Sheet — Quick Reference

Keep this open while you work. Every pattern below was practiced in the playbook.

## The universal prompt formula

```
[ROLE]     You are a healthcare data analyst.
[CONTEXT]  I have a dataset of 50 patients (patient_data.csv).
[TASK]     Compare smokers vs non-smokers.
[FORMAT]   Answer as a two-column table, numbers rounded to 1 decimal.
[RULES]    Use only the data in the file. Keep language simple.
```

You don't always need all five parts — but when an answer disappoints you, check which part you left out.

## The patterns

**1. Role prompting** — changes the perspective

```
You are a [healthcare data analyst / public health researcher / hospital manager]...
```

**2. Audience targeting** — changes the language level

```
...explain it to [a hospital manager with no data background / a 10-year-old / an expert].
```

**3. Format control** — you design the output

```
Answer as a table with columns X, Y, Z.
Answer in EXACTLY this format: ... Do not add anything outside this format.
```

**4. Chain-of-thought** — visible reasoning you can check

```
Think step by step. Show your calculation steps, then give a final verdict.
```

**5. Few-shot** — show one example, get consistent copies

```
Here is an example of the style I want: [example]. Now do the same for [items].
```

**6. Anti-hallucination rules** — keep the AI honest

```
Use only the data in the file. Do not invent data.
Every claim must include a number from the dataset.
If the data cannot answer the question, say so.
```

**7. Iteration** — your secret weapon

The first answer is a draft, not a verdict. Reply with:

```
Shorter. / Make it a table. / You missed the asthma patients — redo step 2.
```

## Red flags to watch for in AI answers

- Numbers that aren't in your dataset (recalculate or ask "show your steps")
- Confident medical claims — this is analytics practice, not medicine
- Averages over the wrong group (e.g., including "Healthy" patients in a disease average)

## Golden rule

**Vague prompt → vague answer. Specific prompt → useful answer.**
