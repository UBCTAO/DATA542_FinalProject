# DATA 542 Final Project  
### Analyzing AI Coding Agents in GitHub Pull Requests

## 1. Project Overview
This project analyzes the behavior and performance of several AI coding agents (e.g., OpenAI_Codex, Cursor, Claude, Devin, GitHub_Copilot) in real-world GitHub workflows.  
Using the AIDev dataset (~930k PRs), we investigate how often and how quickly different agents get their pull requests (PRs) merged, how PR description length affects merge probability, and whether agent performance changes over time.

This repository contains:
- The full analysis notebook  
- Generated figures for all three research questions  
- A formal written report (submitted separately on Canvas)  

---

## 2. Research Questions

### **RQ1 — How do the five autonomous coding agents differ in pull-request success rate and efficiency?**  
How do different AI coding agents compare in:  
- **Merge rate** (probability that a PR is merged), and  
- **Time to merge** (in hours or days)?  

This question evaluates overall effectiveness and efficiency.

---

### **RQ2 — Does the length of the pull-request description affect the chance of being merged, and does this effect vary across agents? **  
Does writing longer PR descriptions (body_length) increase the probability of being merged?  
Additionally, does this effect differ across AI agents (interaction effect)?

We use logistic regression with interaction terms to answer this.

---

### **RQ3 — Did any of the agents improve over time (Dec 2024 -- Jul 2025)?**  
Do any AI agents show clear improvement or decline over time?  
We analyze monthly merge rates and Spearman correlations to detect trends.

---

## 3. Methods & Analysis Summary
The analysis uses:
- **Data preprocessing**: filtering PRs, selecting relevant columns, constructing time variables  
- **Summary statistics** for merge rate and time-to-merge  
- **Statistical tests**  
  - Kruskal–Wallis test (non-parametric comparison of time-to-merge distributions)  
  - Logistic regression with interaction (`merged ~ body_length * agent`)  
  - Spearman correlation for temporal trends  
- **Visualizations**  
  - Bar plots (merge rates)  
  - Boxplots (time-to-merge)  
  - Quartile comparison for description length  
  - Monthly trend lines  

All figures used in the final report are located in the `figures/` directory.

---

## 4. Repository Structure
DATA542 Final Project/
│── DATA542 FinalProject.ipynb      # Main analysis notebook
│── README.md                       # Project documentation
│── figures/                        # All figures used in the report
│     ├── merge-rate.png
│     ├── quartiles.png
│     ├── ttm-boxplot.png
│     └── monthly.png
└── DATA542 FinalProject Report.pdf # Final written report

---
## 5. Dataset Source  
This project uses the **AIDev dataset**, which contains AI-generated GitHub pull requests from multiple agents.

Dataset link (HuggingFace):  
🔗 **https://huggingface.co/datasets/hao-li/AIDev**

The dataset is not included in this repository due to size constraints.

Dataset fields used include:
- `agent`
- `merged`
- `time_to_merge`
- `body_length`
- `created_at`
- `merged_at`
---
