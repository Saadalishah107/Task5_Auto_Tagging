# DevelopersHub_AutoTagging
**DevelopersHub Corporation — AI/ML Engineering Advanced Internship | Task 5**

## Objective
Automatically tag customer support tickets into categories using zero-shot and few-shot NLP techniques inspired by LLM prompting strategies.

## Dataset
- **Name:** Support Ticket Dataset (custom)
- **Source:** Embedded directly in notebook — no download required
- **Size:** 55 labeled tickets across 5 categories
- **Categories:** Billing | Technical | Account | Shipping | General

## Approach / Methodology
| Technique | Description | Analogy |
|-----------|-------------|---------|
| Zero-Shot | Keyword matching — no training data needed | LLM zero-shot prompting |
| Few-Shot | TF-IDF + Logistic Regression on small labeled set | LLM few-shot prompting |
| Top-3 Tags | Probability-ranked top 3 predictions per ticket | LLM ranked outputs |

## Key Results
| Method | Accuracy | F1 Score |
|--------|----------|----------|
| Zero-Shot (Keywords) | ~76% | ~0.75 |
| Few-Shot (TF-IDF + LR) | ~85% | ~0.84 |

**Observations:**
- Zero-shot works well for distinct-vocabulary categories (Shipping, Billing)
- Few-shot significantly improves ambiguous categories (Technical vs Account)
- Top-3 tag output correctly surfaces multiple relevant categories for complex tickets
- Bigrams (e.g., "not working", "credit card") are the most informative features

## Top-3 Tag Output Example
```
Ticket: "My payment failed and now I cannot access my account"
  #1 Billing     ████████   42.3%
  #2 Account     ██████     28.1%
  #3 Technical   ████       18.6%
```

## Production Notes
- Pipeline exported via joblib for integration with ticketing systems (Zendesk, Jira, ServiceNow)
- For higher accuracy: replace TF-IDF with LLM embeddings (OpenAI, Hugging Face) as a drop-in replacement

## Tools & Libraries
Python 3.10 | scikit-learn | pandas | numpy | matplotlib | seaborn | joblib

## How to Run
```bash
pip install scikit-learn pandas numpy matplotlib seaborn joblib jupyter
jupyter notebook Task5_Auto_Tagging.ipynb
```
Run all cells top to bottom. No internet or downloads required.
