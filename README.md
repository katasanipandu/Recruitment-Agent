# Recruitment-Agent

# 🧠 AI-Powered Candidate Screening System

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![LangChain](https://img.shields.io/badge/LangChain-Framework-green)
![LangGraph](https://img.shields.io/badge/LangGraph-Workflow-orange)


An intelligent hiring workflow built using **LangGraph** that automates candidate evaluation, skill matching, and interview routing.

---

## 🚀 Overview

This system analyzes job applications and automatically:

- 📊 Classifies candidate experience level  
- 🧩 Evaluates skill match with job requirements  
- 🔀 Routes candidates through hiring stages  
- ❌ Rejects unqualified candidates  
- 📅 Schedules interviews for suitable candidates  

---

## ⚙️ Workflow Architecture
Application → Experience Classification → Skill Matching → Routing → Final Action


---

## 🔀 Routing Logic

| Condition | Action |
|----------|--------|
| ❌ Skill ≠ Match | Reject Application |
| 🧠 Senior + Match | Escalate to Recruiter |
| 📅 Entry/Mid + Match | Schedule HR Interview |

---

## 🧪 Example

### 📝 Input
"I have 2 years of experience with Python, Flask, and SQL"

### ✅ Output
Experience Level: Entry-level
Skill Match: Match
Action: Schedule HR Interview

---

## 🧠 Key Features

- ✅ Automated candidate screening  
- ✅ LLM-based skill evaluation  
- ✅ Dynamic decision routing (LangGraph)  
- ✅ Structured output for reliable execution  
- ✅ Scalable and customizable pipeline  

---

## 🛠️ Tech Stack

- **Python**
- **LangGraph**
- **LangChain**
- **OpenAI / LLM APIs**

---

## 📌 Core Components

### 1️⃣ Experience Classifier
Determines candidate level:
- Entry-level  
- Mid-level  
- Senior-level  

---

### 2️⃣ Skill Matcher
Evaluates alignment with job requirements.

✔ Returns:
Match / No Match

---

### 3️⃣ Router Function

```python
def route_app(state: dict) -> str:
    skill = str(state.get("skill_match", "")).lower()

    if "no match" in skill:
        return "reject_application"

    if "match" in skill:
        exp = str(state.get("experience_level", "")).lower()

        if "senior" in exp:
            return "escalate_to_recruiter"

        return "schedule_hr_interview"

    return "reject_application"

