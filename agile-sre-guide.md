# Agile Methodology & Google SRE: 5 Whys Guide

---

## 📌 Agile Methodology Overview

Agile is an **iterative and incremental** approach to software development and project management that emphasizes **flexibility, collaboration, and continuous improvement**.

### 🔑 Key Principles

1. **Customer Collaboration** over contract negotiation.
2. **Working Software** over comprehensive documentation.
3. **Individuals and Interactions** over processes and tools.
4. **Responding to Change** over following a rigid plan.

---

## 🚀 Agile Frameworks

### ✅ Scrum
- Uses **sprints** (time-boxed iterations, usually 1–4 weeks).
- Defined roles:
  - **Product Owner**
  - **Scrum Master**
  - **Development Team**
- Artifacts:
  - Product Backlog
  - Sprint Backlog
  - Increment

### 📊 Kanban
- **Visualizes work** using a board with columns (e.g., To Do, In Progress, Done).
- Focus on **continuous delivery**.
- Emphasizes **Work-In-Progress (WIP) limits**.

---

## 🔄 Combining Scrum & Kanban: *Scrumban*

Yes, Scrum and Kanban **can be used together** in a hybrid called **Scrumban**.

### 🛠️ How to Implement Scrumban

1. **Use a visual Kanban board** to track tasks.
2. **Retain Scrum's sprint cadence** (optional).
3. **Set WIP limits** to reduce bottlenecks.
4. **Conduct daily standups** and sprint retrospectives.
5. **Pull tasks continuously** based on team capacity.
6. **Focus on flow and adaptability** over rigid planning.

---

## 🧠 Google SRE: The 5 Whys Technique

The **"5 Whys"** is a **root cause analysis** technique used by Site Reliability Engineers (SREs) at Google to drill down into the underlying causes of an incident.

### 🔍 Steps to Apply the 5 Whys

1. **Identify the problem** clearly.
2. **Ask "Why?"** the issue occurred.
3. For each answer, **ask "Why?" again**.
4. Repeat **until you reach the root cause** (typically 5 times).
5. **Document and fix the root issue** to prevent recurrence.

### 📘 Example

**Problem**: Website is down.

1. **Why?** Servers overloaded.
2. **Why?** Sudden spike in traffic.
3. **Why?** A blog linked to our site.
4. **Why?** Auto-scaling failed.
5. **Why?** Thresholds were misconfigured.

🎯 **Root Cause**: Auto-scaling configuration was too conservative.

✅ **Action**: Adjust thresholds and test autoscaling.

---

## 🧩 Benefits of These Approaches

| Agile Methodology               | 5 Whys Technique                   |
|--------------------------------|------------------------------------|
| Faster time to market          | Prevents recurring incidents       |
| Improved collaboration         | Promotes deep problem understanding|
| Continuous delivery            | Enables systemic improvements      |
| Enhanced product quality       | Fosters a learning culture         |

---

## 📚 References

- *Google SRE Handbook* – https://sre.google
- *Agile Manifesto* – https://agilemanifesto.org
- *Scrum Guide* – https://scrumguides.org

---

