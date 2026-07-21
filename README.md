# GenAI Healthcare Analytics 


## What is this project?

You will play the role of a **healthcare data analyst** who uses Generative AI to analyze patient data — purely by writing good prompts. By the end, you'll know the 5 core prompt engineering techniques that professionals use, and you'll have produced a real analytics report you can show anyone.

## What's in this folder?

| File | What it is |
|------|-----------|
| `README.md` | This file — start here |
| `patient_data.csv` | Your dataset: 50 fake (synthetic) patients with age, condition, BMI, blood pressure, glucose, smoking status, hospital visits, and readmissions |
| `PROMPT_PLAYBOOK.md` | The main course — 6 modules of copy-paste prompts, from "just ask" to a professional report |
| `CHEATSHEET.md` | One-page quick reference of every prompt pattern you learned |

## How to do the project (3 steps)

1. **Open** claude.ai or chat.openai.com in your browser (free accounts work fine).
2. **Upload** `patient_data.csv` into a new chat (or copy-paste its contents).
3. **Follow** `PROMPT_PLAYBOOK.md` module by module. Copy each prompt, paste it, read the result, do the "Your turn" challenge.

Total time: about 1–2 hours, or one module a day for a week.

## About the data (30-second tour)

Each row is one patient. The columns are:

- `patient_id` — a code like P001
- `age`, `gender` — basic demographics
- `condition` — Diabetes, Hypertension, Asthma, Heart Disease, or Healthy
- `bmi` — body mass index (healthy range is roughly 18.5–24.9)
- `systolic_bp` — the top blood pressure number (under 120 is normal, 140+ is high)
- `blood_glucose` — blood sugar (under ~100 is normal, 140+ suggests diabetes)
- `smoker` — Yes/No
- `hospital_visits_last_year` — how many times they came to the hospital
- `readmitted_within_30_days` — whether they returned within 30 days of a stay (hospitals track this closely!)

## Important safety notes

- This data is **100% synthetic** — generated randomly for learning. No real patients.
- **Never** paste real patient data into a public AI chatbot. Real healthcare data is protected by privacy laws (like HIPAA in the US).
- AI outputs about health are for **learning analytics**, not medical advice.

## After you finish

Ideas to level up:

- Re-run the playbook on a public dataset from Kaggle (search "healthcare dataset").
- Save your best prompts — a personal prompt library is a real professional asset.
- When you're ready for Python, ask the AI: *"Teach me to redo Module 3 using Python and pandas, step by step, assuming I'm a total beginner."* Your prompting skills will make learning to code much easier.
