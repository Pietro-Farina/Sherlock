## **Assignment 4: Knowledge Discovery and Pattern Extraction**

### **1. Problem Attempted to Solve**

The goal of this assignment was to analyze the OpenReview scientific review dataset to **extract patterns and recommendations** that could increase the likelihood of a paper being accepted. Specifically, the work aimed to understand:

* What features distinguish accepted papers from rejected ones.
* Which topics, keywords, or title styles are more associated with acceptance.
* How to improve a paper based on concrete comparisons between accepted and rejected versions.

---

### **2. Definition of Success**

Success was defined as the ability to:

* Identify **significant and interpretable patterns** between accepted and rejected papers.
* Build **topic modeling and NLP pipelines** to detect recurring themes linked to acceptance.
* Extract **qualitative and quantitative insights** using LLMs through comparative analysis of paper pairs (accepted vs. rejected).
* Provide **concrete and generalizable recommendations** for writing stronger scientific papers.

---

### **3. Dataset Used**

The dataset consisted of six Excel sheets (Sheet1–Sheet6) covering different years of a conference’s submission and review process. Each sheet contained information such as titles, abstracts, reviews, decisions, reviewer scores, and metadata. The sheets differ in structure and granularity:

* Sheets 1–4: **Review-per-row** (each row represents a reviewer’s evaluation).
* Sheets 5–6: **Paper-per-row** (each row represents a paper, with one column per reviewer).

Total number of papers analyzed: **\~23,000**.

---

### **4. Experiments Done**

#### a. **Data Cleaning & Preprocessing**

* Standardization of column names (e.g., `abstract_field` → `abstract`).
* Removal of noisy, redundant, or low-coverage columns.
* Normalization of decision labels (`0/1`, `Accept`, `Reject`) into consistent categories.
* Basic text preprocessing for NLP (lowercasing, removing symbols, etc.).

#### b. **Statistical Analysis**

* Distribution of scores for accepted vs. rejected papers.
* Analysis of average title length.
* Keyword frequency and distribution.
* Frequent bigrams and trigrams in paper titles.

#### c. **NLP – BERTopic**

* Topic modeling on paper titles.
* Thematic classification of accepted vs. rejected papers.
* Identification of **high-acceptance probability topics**.

#### d. **Pairwise LLM-based Analysis**

* Selection of 8 paper pairs (rejected and accepted versions).
* Comparative analysis using GPT-4o to evaluate differences in:

  * Abstract, introduction, methodology, results.
  * Quantitative metrics (datasets, baselines, performance).
  * Structure and writing style.
* Extraction of **recurring improvements and patterns** in accepted versions.

---

### **5. Findings**

#### a. **Quantitative Patterns**

* **Average scores**: accepted 6.5, rejected 4.1.
* **Shorter and clearer titles** are more common in accepted papers.
* Topics with **100% acceptance** included keywords like:

  * *recursion*, *retinal*, *execution*, *prosthesis*.
* High-acceptance keywords: *Deep Learning*, *Reinforcement Learning*, *NLP*.
* Titles with *neural networks*, *deep learning* were very common but not decisive.

#### b. **Qualitative Patterns (from LLM Analysis)**

Accepted papers were found to be:

* Clearer in problem framing.
* Richer in experiments, ablation studies, and statistical analysis.
* Better at literature positioning.
* More visually supported and technically precise in language.

#### c. **General Insights**

| Theme                                | Description                                          |
| ------------------------------------ | ---------------------------------------------------- |
| **Stronger Experiments**             | More datasets, metrics, baselines, ablation studies. |
| **Clear Novelty Framing**            | Explicitly defined scope, novelty, and motivation.   |
| **Theoretical Rigor**                | Proofs, conditions, and mathematical support.        |
| **Algorithm & Architecture Clarity** | Diagrams, pseudocode, training details.              |
| **Human-Centric Validation**         | User studies or deployment feedback when applicable. |

---

### **6. Limitations**

Pairwise comparison:
* **Data Scarcity**: Very few papers had both accepted and rejected versions available, limiting the generalizability of pairwise analysis.
* **Computational and Economic Cost**: LLM-based analysis of PDFs is expensive (up to \~\$0.44 per paper pair).
* **Manual Overhead**: Downloading and preparing each pair of papers required manual work.

NLP pipelines:
* **Data Inconsistency**: Heterogeneous formats, missing column names, and multilingual entries made preprocessing more complex.
* **Missing Full Text**: Many papers lacked full text, preventing in-depth analysis beyond titles and reviews.
