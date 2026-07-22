# The Prompt Playbook — GenAI Healthcare Analytics

This is the heart of the project. Work through the 6 modules in order. Each module teaches you **one prompt engineering skill**, gives you **copy-paste prompts** to try, and tells you **what to notice** in the AI's answer.

**How to use this playbook:**

1. Open Claude (claude.ai) or ChatGPT in your browser.
2. Start a new chat and upload the `patient_data.csv` file (or copy-paste its contents).
3. Copy a prompt from a module below, paste it into the chat, and press Enter.
4. Read the answer, then read the "What to notice" section.
5. Try the "Your turn" challenge before moving to the next module.

> All the data in this project is **fake (synthetic)**. No real patients. That's important — never paste real patient data into a public AI chatbot.

---

## Module 1 — Ask a Simple Question (Baseline Prompting)

**Skill:** Just ask. Before learning fancy techniques, see what a plain question gets you.

### Prompt 1.1 — First look at the data

```
I have uploaded a dataset called patient_data.csv.
What information does this dataset contain? Explain it to me like I am new to data analysis.  
```

### Prompt 1.2 — Basic count

```
How many patients are in this dataset, and how many have each medical condition? Could you perform some task like 
how many smokers, or how readmission relates to conditions?
```

**What to notice:**
- The AI can read the file and explain each column in plain English.
- Even simple prompts work — but the answers are generic. The AI decides the format, length, and depth for you.

---

## Module 2 — Give the AI a Role (Role Prompting)

**Skill:** Telling the AI *who to be* changes *how it answers*. This is called role prompting.

### Prompt 2.1 — Same question, with a role

```
You are a healthcare data analyst at a small hospital.
Look at patient_data.csv and give me a summary of the overall health of these 50 patients.
Keep it short and use simple language, as if explaining to a hospital manager with no data background.
```

### Prompt 2.2 — Change the role, watch the answer change

```
You are a public health researcher.
Look at patient_data.csv and tell me what patterns you find interesting from a
disease-prevention point of view.
```

**What to notice:**
- Run 2.1 and 2.2 in separate chats. The same data produces different insights depending on the role.
- Formula so far: **Role + Task + Audience** = a much better answer than just a question.

---

## Module 3 — Control the Output (Format Instructions)

**Skill:** Tell the AI exactly what shape the answer should be — a table, a list, three bullet points, one paragraph. This is the most useful everyday skill.

### Prompt 3.1 — Ask for a table

```
You are a healthcare data analyst.
From patient_data.csv, create a table with one row per medical condition, showing:
- number of patients
- average age
- average BMI
- average blood glucose
Round all numbers to 1 decimal place.
```
### Prompt 3.2 — Ask for a two columns table 
```
You are a healthcare data analyst.
From patient_data.csv, create a two columns table for smokers vs. non-smokers, with one row per medical condition.
```
### Prompt 3.3 — Ask for a strict structure

```
You are a healthcare data analyst.
Analyze patient_data.csv and answer in EXACTLY this format:

TOP FINDING: (one sentence)
SUPPORTING NUMBERS: (2-3 bullet points with numbers from the data)
RECOMMENDED ACTION: (one sentence a hospital could act on)

Do not add anything outside this format.
```

**What to notice:**
- The AI follows your structure. You designed the report; the AI filled it in.
- Words like "EXACTLY" and "Do not add anything outside this format" keep the answer tight.



---

## Module 4 — Think Step by Step (Chain-of-Thought Prompting)

**Skill:** For questions that need reasoning (not just counting), ask the AI to show its steps. You catch mistakes, and answers get more reliable.

### Prompt 4.1 — Risk analysis with visible reasoning

```
You are a clinical data analyst.
Using patient_data.csv, identify which patients look like the highest risk for
hospital readmission. Think step by step:

Step 1: List the factors in this dataset that could relate to readmission risk.
Step 2: Explain your reasoning for each factor.
Step 3: Give me the top 5 highest-risk patient IDs with a one-line reason each.

Important: this is a learning exercise on fake data, not real medical advice.
```

### Prompt 4.2 — Verify a claim

```
Someone claims: "In this dataset, smokers have more hospital visits than non-smokers."
Check whether this is true in patient_data.csv. Show your calculation steps,
then give a clear yes/no verdict with the numbers.
```

### Prompt 4.3 — Risk Analysis for high blood sugar (over 120)

```
You are a clinical data analyst.
Using patient_data.csv, identify whether patients with high blood glucose (over 120 ) are mostly diabetic. 
Think step by step:

Step 1: List the patients in this dataset who have diabetes and high glucose level (over 120).
Step 2: Explain the corelation between both conditions for each factor.
Step 3: Give a clear yes/no verdict with the numbers
```

### Prompt 4.4 — Risk Analysis for Diabetics (high blood sugar (over 140))

```
You are a clinical data analyst.
Using patient_data.csv, identify whether patients with high blood glucose (over 140 ) are mostly diabetic. Think step by step:

Step 1: List the patients in this dataset who have diabetes and high glucose level (over 140).
Step 2: Explain the corelation between both conditions for each factor.
Step 3: Give a clear yes/no verdict with the numbers
```

**What to notice:**
- "Think step by step" / "Show your calculation steps" makes the reasoning visible.
- Prompt 4.2, 4.3, 4.4 are a **fact-checking pattern** — you'll reuse this constantly in real analytics work.
---

## Module 5 — Show an Example (Few-Shot Prompting)

**Skill:** Instead of describing the output you want, *show one example of it*. The AI copies the pattern. This is called few-shot prompting.

### Prompt 5.1 — Patient summary cards

```
You are a healthcare analyst. I want a short "patient card" for some patients in patient_data.csv.

Here is an example of the exact style I want:

---
PATIENT P001 | Male, 64
Condition: Heart Disease | Risk flags: BMI 29.8, readmitted within 30 days
Story: A 64-year-old male with heart disease and frequent hospital visits
(6 last year), including a recent readmission. Monitor closely.
---

Now create cards in this exact style for patients P005, P012, and P020,
using their real values from the dataset.
```

**What to notice:**
- You never described the format in words — you just showed it once, and the AI matched the layout, tone, and length.
- Few-shot is the fastest way to get consistent output across many items.

---

## Module 6 — The Capstone: A Full Analytics Report (Combining Everything)

**Skill:** Combine role + task + format + reasoning + constraints into one professional "mega-prompt". This is what real prompt engineering looks like.

### Prompt 6.1 — The full report for Hospital leadership

```
You are a senior healthcare data analyst preparing a report for hospital leadership.

DATA: Use patient_data.csv (50 patients, synthetic data).

TASK: Write a one-page "Population Health Report" with these sections:

1. EXECUTIVE SUMMARY — 3 sentences max, plain English, no jargon.
2. KEY METRICS — a small table: total patients, average age, % smokers,
   % readmitted within 30 days.
3. CONDITION BREAKDOWN — a table by condition: patient count, average age,
   average glucose, average systolic BP.
4. TOP 3 INSIGHTS — numbered list. Each insight must include a real number
   from the data. Think through the data carefully before choosing them.
5. RECOMMENDATIONS — 2 practical actions the hospital could take, based only
   on what the data shows.

RULES:
- Use simple language a non-technical manager understands.
- Every claim must be backed by a number from the dataset.
- Do not invent data that is not in the file.
- End with one line noting this is synthetic data for learning purposes.
```

### Prompt 6.2 — The full report for Medical Authority

```
You are a nurse preparing a report for Medical authority.

DATA: Use patient_data.csv (50 patients, synthetic data).

TASK: Write a small report "wchich patients need follow-up calls" with these sections:

1. NARRATIVE SUMMARY — 3 sentences max, plain English, no jargon.
2. KEY METRICS — a small table: total patients, average age, % smokers,
   % readmitted within 30 days.
3. CONDITION BREAKDOWN — a table by condition: patient count, average age,
   average glucose, average systolic BP.
4. TOP 3 INSIGHTS — numbered list. Each insight must include a real number
   from the data. Think through the data carefully before choosing them.
5. RECOMMENDATIONS — Based ON DATA, which patients needs follow-up call mention with patient IDs.
   

RULES:
- Use simple language a non-technical manager understands.
- Every claim must be backed by a number from the dataset.
- Do not invent data that is not in the file.
- End with one line noting this is synthetic data for learning purposes.
```

### Prompt 6.3 — Turn the report into a chart

```
Based on your report, create a simple bar chart of the average blood glucose
per condition.
```

(Claude and ChatGPT can both generate charts — try it!)

**What to notice:**
- Every module you learned is inside prompt 6.1: role (Module 2), format (Module 3), reasoning (Module 4), and strict rules that prevent the AI from making things up.
- "Do not invent data that is not in the file" is a real technique for reducing AI **hallucinations** — a word you'll hear a lot in GenAI.


---

## What You Just Learned

| Module | Technique | One-line summary |
|--------|-----------|------------------|
| 1 | Baseline prompting | Just ask — your starting point |
| 2 | Role prompting | "You are a..." changes the whole answer |
| 3 | Format control | You design the output; AI fills it in |
| 4 | Chain-of-thought | "Think step by step" = visible, checkable reasoning |
| 5 | Few-shot | Show one example, get consistent copies |
| 6 | Mega-prompt | Combine everything like a professional |

When you can comfortably write a Module-6-style prompt without looking, you're no longer a beginner. 🎓
