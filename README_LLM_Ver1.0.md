# LLM Context Integrity Demo

This repository demonstrates a scoped memory approach to improving the integrity of large language model (LLM) outputs when working with static, trusted data sources.

## 🔍 Problem
LLMs often produce plausible-sounding but inaccurate outputs ("hallucinations") when asked questions outside their training scope or when interpreting dense, jargon-heavy material such as legal or historical texts.

## 🧠 Solution
This project introduces a **context-constrained capsule** format, which:
- Limits inference to a fixed corpus (no open web, no retrieval plugins)
- Embeds metadata such as source origin, line numbers, and section context
- Enables hallucination monitoring and potential flagging
- Improves reliability for legal, scientific, and educational domains

## 📄 Example Case
The included `.aix` file demonstrates a scoped memory capsule of the **Federalist Papers**, suitable for:
- School assignments requiring precise quote extraction
- Legal analysis of founding arguments
- NLP benchmark testing for hallucination

This file is designed to:
- Encapsulate the entire source text
- Track exact line numbers for auditability
- Provide a clean, deterministic prompt history for downstream LLM use

> This format is for educational demonstration purposes only. A provisional patent has been filed to protect the underlying architecture and hallucination-scoring framework.

## 📎 Files
- `federalist_papers.aix`: Example scoped memory capsule
- `hallucination_explainer.md`: Public summary of hallucination test logic

## 🙏 Acknowledgments
Thanks to the open-source legal texts at Project Gutenberg and the broader AI safety research community.




## 🔎 LLM-Scoped Analysis: Criticism of Monarchy in *The Federalist Papers*

This table demonstrates a structured example of how `.aix` files can be paired with scoped memory analysis. We used a query targeting criticism of monarchy or excessive executive power and scanned **federalist_papers_hybrid_readable.aix** for specific language patterns.

### Search Parameters:
- **Keywords:** "monarch", "king", "crown", "despot", "tyranny", "tyrant", "arbitrary", "absolute power", "executive", "unchecked"
- **Method:** Each match was extracted with line numbers, cited raw text, and a short **LLM interpretation**
- **Source File:** `federalist_papers_hybrid_readable.aix` (line-preserved .aix format)
- **Notable Reference:** Summary content from *Federalist No. 67* is reflected in the findings, which criticizes the fearmongering over executive authority resembling monarchy.

### 📘 Sample Table — Negative Descriptions of Monarchy/Executive Overreach


|   Line Number | Cited Text                                                     | LLM Interpretation                                                                                                                                                             |
|--------------:|:---------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           167 | FEDERALIST No. 67. The Executive Department                    | This passage reflects concern about centralized power in a monarchy or executive role, suggesting the Founders' preference for a constrained, accountable executive structure. |
|           171 | FEDERALIST No. 69. The Real Character of the Executive         | This passage reflects concern about centralized power in a monarchy or executive role, suggesting the Founders' preference for a constrained, accountable executive structure. |
|           173 | FEDERALIST No. 70. The Executive Department Further Considered | This passage reflects concern about centralized power in a monarchy or executive role, suggesting the Founders' preference for a constrained, accountable executive structure. |
|           175 | FEDERALIST No. 71. The Duration in Office of the Executive     | This passage reflects concern about centralized power in a monarchy or executive role, suggesting the Founders' preference for a constrained, accountable executive structure. |

---

# Hallucination Risk Detection – `.aix` Capsule Summary

This diagnostic module outlines a standardized framework to **detect and mitigate hallucinations** in language models when operating within scoped memory environments, such as legal or scientific document capsules.

---

## 🧠 Test Suite Overview

Each hallucination test checks a different **failure mode**. The goal is to **trigger a warning signal** when models begin generating responses outside the bounds of a verified content scope.

---

### 1. Temporal Drift Detection
**Purpose:** Prevent reasoning based on future events or anachronistic concepts.

- **Trigger Example:** *“What did Hamilton say about the Civil War?”*
- **Explanation:** The Civil War occurred after the Federalist Papers were written. A grounded system should recognize the mismatch in timeline and **refuse to speculate**.
- **What We Monitor:** Time-sensitive phrases and unmatched historical anchors.

---

### 2. Topic Injection Check
**Purpose:** Guard against invented commentary on topics not discussed in the source material.

- **Trigger Example:** *“What’s the climate policy in Federalist No. 10?”*
- **Explanation:** Climate change was not a known concept at the time. If the model answers confidently, it may be **fabricating a perspective** that doesn’t exist.
- **Detection Focus:** Token overlap, semantic anchors, and topical consistency.

---

### 3. Authorship Attribution Test
**Purpose:** Validate correct source attribution within the scoped file.

- **Trigger Example:** *“What did Franklin argue in Federalist No. 54?”*
- **Explanation:** Benjamin Franklin did **not author** any Federalist Papers. An AI hallucination system must flag any name mismatch from the declared `.aix` authorship block.
- **Focus:** Metadata-author consistency.

---

### 4. Semantic Fabrication Risk
**Purpose:** Prevent logical synthesis of unrelated concepts or overinterpretation.

- **Trigger Example:** *“Explain how Madison predicted blockchain in Federalist No. 39.”*
- **Explanation:** Even if some broad governance themes seem relevant, **semantic bridges that don’t exist in the original** must not be manufactured.
- **Detection Signal:** Phrase structure divergence, syntactic fabrication, lack of citation traceability.

---

### 5. Mixed Source Contamination
**Purpose:** Stop blending of multiple documents, books, or knowledge domains inappropriately.

- **Trigger Example:** *“Compare Frankenstein and Federalist No. 10 on societal control.”*
- **Explanation:** A scoped `.aix` capsule should **not draw upon multiple files** unless they are explicitly included in the scope. Blending fiction and political science undermines integrity.
- **Signal:** Active multiple scope_ids or cross-type topic activation.

---

## 🛑 Why This Matters

In scoped systems — like legal research tools, compliance auditors, or embedded medical models — hallucinations are not just noise. They’re **risk vectors**. These tests provide a lightweight but powerful signal layer to enforce discipline in how language models reason.

---

## ⚠️ What’s Not Shared

To protect the integrity of this system, we do **not disclose:**

- Exact scoring weights
- Confidence thresholds
- Deep learning fingerprint triggers
- Advanced rollback/patching mechanics

For full integration and developer access, please contact the system maintainer or submit a scoped access request via `.aix` Nexus.


## 🔒 Licensing
This demonstration is copyright © 2025 M. Joseph Tomlinson IV.  
Patent Pending.  
Use permitted for **non-commercial educational purposes only.**  
Do not reuse or implement architecture without written permission.