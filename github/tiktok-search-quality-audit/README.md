# TikTok Search Quality Audit

## Overview

TikTok has become a major search platform for younger users, but the quality of its search results is still underexplored.

This project builds a simple manual search quality audit for TikTok Search. The goal is to evaluate whether search results actually match what users are looking for, identify common failure patterns, and suggest practical improvements.

The project focuses on real search behavior by manually collecting TikTok search results and scoring them using a plain-English relevance rubric.

---

## Project Goals

- Evaluate how well TikTok search results satisfy user intent
- Identify common search failure cases
- Measure how often English queries return non-English results
- Compare search quality across different query intent categories
- Provide practical recommendations for improving search relevance

---

## Dataset

This project does not use a pre-existing dataset. Instead, data is collected manually from TikTok's live search interface. 

### Query Setup
The project uses **80 English-language search queries** across four intent categories:

- **Informational**: user wants to learn something
- **Navigational**: user wants to find a specific account or page
- **Transactional**: user wants to take an action
- **Commercial**: user is comparing options before deciding :contentReference[oaicite:2]{index=2}

### For each query, the dataset records:
- query text
- query language
- top 5 TikTok search results
- video title
- creator handle
- description snippet
- result language
- intent label
- relevance score
- failure flag
- ideal result note for weak results :contentReference[oaicite:3]{index=3}

Total expected size: **400 rows**  
(80 queries × 5 results) 

---

## Methodology

## 1. Framework Design
Before collecting data, the project defines:
- four query intent categories
- a **0 to 3 relevance scoring guide**
- automatic 0-score triggers such as:
  - wrong language
  - clickbait
  - spam
  - outdated content :contentReference[oaicite:5]{index=5}

### Relevance Scale
- **0** = Skip it
- **1** = Meh
- **2** = Pretty good
- **3** = Perfect 

The core question behind the scoring is: **Did this result actually answer what was searched for?** 

## 2. Data Collection
- Finalize 80 queries across the 4 intent categories
- Record the top 5 results for each query
- Store all metadata in a CSV file for scoring and analysis 

## 3. Manual Scoring
Each of the 400 results is manually scored from 0 to 3.

For low-scoring results, the dataset also includes:
- a short failure flag
- a one-sentence note describing what the ideal result should have looked like 

## 4. Analysis and Visualization
Using Python, the project analyzes:
- average score by intent category
- how often results score 0 or 1
- how often English queries return non-English results
- most common failure reasons

Tools:
- pandas
- matplotlib
- seaborn :contentReference[oaicite:11]{index=11}
