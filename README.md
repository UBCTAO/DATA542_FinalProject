
# DATA 542 Final Project
### Analyzing AI Coding Agents in GitHub Pull Requests

## 1. Project Overview
This project analyzes the behavior and performance of several AI coding agents (e.g., OpenAI_Codex, Cursor, Claude, Devin, GitHub_Copilot) in real-world GitHub workflows.  
Using the AIDev dataset (~930k PRs), we investigate how often and how quickly different agents get their pull requests (PRs) merged, how PR description length affects merge probability, and whether performance changes over time.

This repository contains:
- The full analysis notebook  
- Generated figures for all three research questions  
- A formal written report (submitted separately on Canvas)  
- A requirements.txt file

---

## 2. Research Questions

### **RQ1 — Merge Rate & Time-to-Merge Differences**
How do different AI coding agents compare in:
- **Merge rate** (probability that a PR is merged), and  
- **Time to merge** (in hours or days)?  

This question evaluates overall effectiveness and efficiency.

### **RQ2 — Effect of PR Description Length**
Does writing longer PR descriptions (body_length) increase merge probability?  
Does this effect differ across agents (interaction effect)?  
We use logistic regression with interaction terms to answer this.

### **RQ3 — Trends Over Time (Dec 2024 → Jul 2025)**
Do any AI agents show improvement or decline over time?  
We analyze monthly merge rates and Spearman correlations to detect trends.

---

## 3. Methods & Analysis Summary

The analysis includes:

### **Data preprocessing**
- Filtering PRs  
- Selecting relevant columns  
- Constructing time variables  

### **Statistical tests**
- Kruskal–Wallis test (non-parametric comparison of time-to-merge distributions)  
- Logistic regression with interaction (`merged ~ body_length * agent`)  
- Spearman correlation for temporal trends  

### **Visualizations**
- Bar plots (merge rate and time-to-merge)  
- Boxplots (time-to-merge)  
- Quartile comparison for description length  
- Monthly trend lines  

All figures used in the final report are located in the `figures/` directory.

---

## 4. Repository Structure

```text
DATA542 Final Project/
│── DATA542_FinalProject.ipynb        # Main analysis notebook
│── README.md                         # Project documentation
│── requirements.txt                  # Dependencies
│── figures/                          # All figures used in the report
│     ├── merge-rate.png
│     ├── quartiles.png
│     ├── ttm-boxplot.png
│     └── monthly.png
└── DATA542_FinalProject_Report.pdf   # Final written report

```

##  5. Dataset Source  
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
