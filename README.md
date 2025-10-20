# CITE V.1: Evidence-Grounded, LLM-Agentic Interpretation of RNA-Seq Clusters

This repository documents **CITE V.1** — a *multi-agent, literature-anchored large-language-model (LLM) framework* designed for **transparent interpretation of RNA-Seq clusters**.  
Developed at the **Complex Adaptive Systems Laboratory (CASL)**, University of Central Florida, CITE V.1 demonstrates how multi-agent reasoning can transform opaque transcriptomic cluster analyses into *auditable, evidence-grounded insights*.

---

## 🧬 Overview

Traditional LLMs often produce speculative biological interpretations when used for gene expression analysis.  
CITE V.1 (Clustering Interpretation) introduces a **Retriever–Interpreter–Critic** architecture that grounds explanations in **PubMed** and **UniProt** evidence, ensuring each claim is traceable and biologically justified.

**Key Contributions**
- Multi-agent reasoning for RNA-Seq interpretation  
- Transparent retrieval from PubMed + UniProt  
- Confidence and critic-agreement scoring  
- Benchmark comparison with Gemini baseline  
- Case study: *Salmonella enterica* RNA-Seq dataset (59 samples × 4700 genes)

---

## 🧠 Framework Design

The **CITE V.1 architecture** integrates knowledge retrieval, agent reasoning, and consensus validation through two agent layers:

### 🔹 Data Layer
- Input: RNA-Seq matrix (59 samples × 4700 genes)
- Genes are grouped into expression clusters; representative genes per cluster are extracted.

### 🔹 Knowledge Layer
- Fetches biological context from:
  - **UniProt** (protein-level information)
  - **PubMed** (literature abstracts)
  - External tools (for ontology, pathway, and GO enrichment)

### 🔹 Agent Layer 1 – Retriever Agent
- Collects relevant PubMed and UniProt evidence per cluster.  
- Returns structured textual contexts to downstream agents.

### 🔹 Agent Layer 2 – Interpreter & Critic Agents
- **Interpreter Agent:** generates initial cluster hypotheses based on literature evidence.  
- **Critic Agent:** evaluates reliability, cross-validates biological coherence, and quantifies uncertainty.  
- A **Consensus Layer** aggregates critic judgments into final confidence scores.

### 🔹 Output Layer
- Produces interpretable cluster annotations linking biological functions (e.g., virulence, ion acquisition, antimicrobial resistance).  
- Outputs include critic-agreement scores and transparency metadata for auditability.

---

## 🧩 System Diagram

![WhatsApp Image 2025-10-17 at 11 35 26 AM](https://github.com/user-attachments/assets/d7b82ccc-033a-4ad0-906f-9669e892f272)


**Figure 1.**  
CITE V.1 integrates retrieval, interpretation, and critic evaluation to generate literature-anchored cluster explanations.  
Each numbered step corresponds to:  
1️⃣ RNA-Seq input → 2️⃣ Clustering → 3️⃣ Context retrieval → 4️⃣ Evidence return →  
5️⃣ Context propagation → 6️⃣ Critic–Interpreter reasoning → 7️⃣ Final interpretation.

---

## 📊 Supporting Analyses

### Evidence Coverage
PubMed-generic and UniProt evidence dominate across clusters, while PubMed-specific hits remain limited.

<img width="746" height="322" alt="image" src="https://github.com/user-attachments/assets/2eb7c2d3-47c3-474d-93db-d43c7e7e1522" />

**Figure 2a.** Distribution of PubMed-specific, generic, and UniProt references per cluster.

### Biological Themes
Keyword analysis identifies recurrent patterns such as *host interaction*, *ion acquisition*, and *antimicrobial resistance*, matching literature-anchored findings.

![WhatsApp Image 2025-10-17 at 11 35 26 AM (1)](https://github.com/user-attachments/assets/33a367ef-a277-4cbb-8a9a-0d4342a3ee2b)

**Figure 2b.** Dominant biological keywords extracted from multi-agent outputs.

---

## 🔍 Results & Comparison

CITE V.1 outperformed a single-LLM (Gemini) baseline by producing verifiable, evidence-anchored explanations:
- Cluster 1 example: linked *abdA* and *rshB* genes to antibiotic stress response, with **confidence = 0.45** (critic-flagged for missing regulatory evidence).  
- Gemini misclassified the same cluster as *Streptomyces*-related due to speculative phrasing.

<img width="689" height="298" alt="image" src="https://github.com/user-attachments/assets/ee9bbe26-5914-4f36-8a9f-9b933f1b5e5e" />
 
**Figure 3.** Structured CITE V.1 outputs versus Gemini baseline responses.

A critic-agreement map highlights how multiple agents converge on stable interpretations.

<img width="663" height="153" alt="image" src="https://github.com/user-attachments/assets/d0656afa-8197-4434-bdef-9abf1f575a91" />

**Figure 4.** Critic consensus map per cluster showing internal reliability of interpretations.

---

## 🧾 Citation

> **Elias Hossain**, **Mehrdad Shoebi**, **Ivan Garibay**, **Niloofar Yousefi**  
> *CITE V.1: Evidence-Grounded, LLM-Agentic Interpretation of RNA-Seq Clusters*  
> MIT Molecular Machine Learning Conference 2025  
> Complex Adaptive Systems Laboratory (CASL), University of Central Florida  
> [arXiv (preprint pending)](https://arxiv.org/abs/25xx.xxxxx)

---

## ⚙️ License
© 2025 Elias Hossain et al. All rights reserved.  
Released for academic viewing and citation under the **Creative Commons Attribution-NonCommercial 4.0 International License**.

---

## 🧾 References
1. Bakk L. et al. *Salmonella enterica transcriptomics and differential expression under stress.* Nucleic Acids Res, 2024.  
2. Hossain E. et al. *CITE V.1: Evidence-Grounded RNA-Seq Interpretation.* (arXiv pending, 2025).  
3. Brown T. et al. *Language Models are Few-Shot Learners.* NeurIPS, 2020.  
4. Gemini Baseline (2024). Google Research, LLM Biological Reasoning Experiments.  
