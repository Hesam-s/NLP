Here is the `README.md` summary file for your GitHub repository, based on the provided project code and details:

---

# Reproducing the Task Adapter Component of the MAD-X Framework for Cross-lingual NER

> Reproducing the task adapter approach for cross-lingual **Named Entity Recognition (NER)** (inspired by the MAD-X framework) using **XLM-RoBERTa Base** and the **WikiANN** dataset, transferring knowledge from **English** (high-resource) to **Persian** (lower-resource) via zero-shot cross-lingual transfer.
> 
> 

---

## 📌 Project Overview

This project investigates lightweight cross-lingual transfer learning for Named Entity Recognition (NER). By keeping the pre-trained multilingual backbone (**XLM-RoBERTa Base**) frozen, we train a dedicated **Task Adapter** on the English portion of the **WikiANN** dataset and directly evaluate its performance on Persian using **zero-shot cross-lingual transfer** without any target-language fine-tuning.

---

## 🏫 Academic Context

* **Course:** Advanced Natural Language Processing (NLP Advanced)


* **Instructor:** Dr. Nava Eslami


* **University:** Islamic Azad University, North Tehran Branch


* **Semester:** Spring / Second Semester (1404-1405)



---

## 👥 Group Members

| Name & Surname | Student ID |
| --- | --- |
| **Hessam Sarvoti**<br> | `404198788`<br> |
| **Mohammad Mehdi Nosrati**<br> | `404188074`<br> |

---

## 📊 Experimental Setup & Specifications

| Component | Value |
| --- | --- |
| **Framework Approach** | Task Adapter (Inspired by MAD-X)

 |
| **Backbone Model** | `xlm-roberta-base`<br> |
| **Task** | Named Entity Recognition (NER)

 |
| **Dataset** | WikiANN (`unimelb-nlp/wikiann`)

 |
| **Training Language** | English (`en`)

 |
| **Evaluation Language** | Persian (`fa` - Zero-shot)

 |
| **Libraries** | Hugging Face Transformers, Adapters, Datasets, Evaluate

 |
| **Execution Environment** | Google Colab (Free GPU - Tesla T4)

 |

---

## 📈 Summary of Results

| Dataset / Evaluation Split | Precision | Recall | F1-score | Accuracy |
| --- | --- | --- | --- | --- |
| **English Validation**<br> | 0.7611

 | 0.7918

 | 0.7761

 | 0.9104

 |
| **Persian Zero-shot Test**<br> | 0.4163

 | 0.5199

 | 0.4624

 | 0.7455

 |

---

## 🚀 Quick Start / Pipeline Steps

The accompanying Jupyter Notebook (`.ipynb`) follows these 19 structured sequential steps:

1. **Library Installation & Imports**

2. **Project Configuration & Reproducibility Setup** (Fixed Seed = `42`)


3. **Loading the WikiANN Dataset** (`en` & `fa`)


4. **Dataset Label Extraction & Schema Alignment**

5. **Backbone Model Initialization** (`xlm-roberta-base`)


6. **Task Adapter & Tagging Head Creation**

7. **Tokenization & Subword Label Alignment** (ignoring `-100` indices)


8. **Data Collator Setup** for Dynamic Padding


9. **Task Adapter Training** on English Train Split (Frozen Backbone)


10. **Model Validation** on English Validation Split


11. **Zero-shot Cross-lingual Transfer Inference** on Persian Test Data


12. **Evaluation Metrics Computation** (`seqeval` F1, Precision, Recall)


13. **Confusion Matrix Generation & Visualization**

14. **Model Serialization** (Saving Adapter & Prediction Head)


15. **Inference pipeline verification** using custom text inputs in Persian
