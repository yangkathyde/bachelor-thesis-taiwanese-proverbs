# Evaluating LLMs on Taiwanese Proverbs

This repository contains the datasets, prompts, model outputs, evaluation results, and statistical analyses for the Bachelor's thesis:

> **Evaluating LLMs on Taiwanese Proverbs: A Study of Interpretation and Semantic Understanding**

The study evaluates four large language models (LLMs) on two tasks involving Taiwanese proverbs:

1. **Interpretation Task**: Evaluating the models' ability to interpret Taiwanese proverbs in English.
2. **Context Application Task**: Evaluating the models' ability to select appropriate Taiwanese proverbs for given conversational contexts.

---

## Repository Structure

```text
.
├── data/
│   ├── interpretation_dataset_proverbs_001_468.xlsx
│   ├── context_application_dataset_proverbs_001_100.xlsx
│   └── statistical_tests/
│       ├── interpretation_friedman_test.xlsx
│       ├── interpretation_posthoc_wilcoxon.xlsx
│       ├── context_application_cochran_q_test.xlsx
│       ├── context_application_posthoc_mcnemar.xlsx
│       └── open_vs_closed_source_comparison.xlsx
│
├── results/
│   ├── interpretation_bertscore_results.xlsx
│   ├── interpretation_model_performance_summary.xlsx
│   └── context_application_model_performance_summary.xlsx
│
├── prompts/
│   ├── interpretation_prompt_v1.txt
│   ├── context_application_prompt_v1.txt
│   └── context_application_prompts_proverbs_001_100.xlsx
│
├── model_outputs/
│   ├── interpretation_model_outputs.xlsx
│   └── context_application_model_outputs.xlsx
│
├── notebooks/
│   └── Statistical_significance_tests.ipynb
│
├── .gitignore
└── README.md
```

---

## Models

The study evaluates the following four LLMs:

- Qwen 3.7
- GPT-5.6 Luna
- Gemini 3.6 Flash
- DeepSeek

---

## Evaluation Tasks

### 1. Interpretation Task

The Interpretation Task evaluates whether LLMs can interpret the figurative meanings of Taiwanese proverbs in English.

The dataset contains **468 Taiwanese proverbs**. For each proverb, the models were asked to provide a one-sentence English interpretation of its figurative meaning.

The model-generated interpretations were evaluated against manually reviewed English reference interpretations using **BERTScore-F1**.

### 2. Context Application Task

The Context Application Task evaluates whether LLMs can select an appropriate Taiwanese proverb for a given conversational context.

A subset of **100 proverbs** was sampled from the 468-proverb dataset using a fixed random seed (`random_state = 42`). Each question presents a conversational context together with four proverb options, including one correct answer and three distractors.

Model performance was evaluated using **accuracy**.

---

## Evaluation Results

### Interpretation Task

The mean BERTScore-F1 results were:

| Model | Mean BERTScore-F1 |
|---|---:|
| Qwen 3.7 | 0.9012 |
| GPT-5.6 Luna | 0.8947 |
| Gemini 3.6 Flash | 0.8859 |
| DeepSeek | 0.8825 |

### Context Application Task

The accuracy results were:

| Model | Accuracy |
|---|---:|
| Gemini 3.6 Flash | 98% |
| Qwen 3.7 | 94% |
| DeepSeek | 94% |
| GPT-5.6 Luna | 83% |

---

## Statistical Analysis

The statistical analyses are based on paired model-level results for the same proverb or question items.

### Interpretation Task

A **Friedman test** was used to examine whether there were statistically significant differences among the four models.

Following a significant Friedman test, pairwise **Wilcoxon signed-rank tests** were conducted. **Holm correction** was applied to account for multiple comparisons.

The corresponding statistical results are provided in:

```text
data/statistical_tests/
├── interpretation_friedman_test.xlsx
└── interpretation_posthoc_wilcoxon.xlsx
```

### Context Application Task

A **Cochran's Q test** was used to examine whether there were statistically significant differences among the four models.

Following a significant Cochran's Q test, pairwise **exact McNemar tests** were conducted. **Holm correction** was applied to account for multiple comparisons.

The corresponding statistical results are provided in:

```text
data/statistical_tests/
├── context_application_cochran_q_test.xlsx
└── context_application_posthoc_mcnemar.xlsx
```

### Open-Source and Closed-Source Models

A descriptive comparison was conducted between open-source and closed-source models across the Interpretation Task and the Context Application Task.

The comparison results are provided in:

`data/statistical_tests/open_vs_closed_source_comparison.xlsx`

---

## Prompts

The `prompts/` directory contains the prompts used for the two evaluation tasks:

- `interpretation_prompt_v1.txt`: Prompt used for the Interpretation Task.
- `context_application_prompt_v1.txt`: Prompt used for the Context Application Task.
- `context_application_prompts_proverbs_001_100.xlsx`: Prompts and conversational contexts for the 100 Context Application questions.

---

## Model Outputs

The `model_outputs/` directory contains the raw model-generated responses used in the evaluation:

- `interpretation_model_outputs.xlsx`: Model outputs for the Interpretation Task.
- `context_application_model_outputs.xlsx`: Model outputs for the Context Application Task.

---

## Notebooks

The `notebooks/` directory contains the notebook used for the statistical significance tests reported in the thesis:

- `Statistical_significance_tests.ipynb`: Implements the Friedman test and post-hoc Wilcoxon signed-rank tests for the Interpretation Task, as well as Cochran's Q test and post-hoc exact McNemar tests for the Context Application Task (with Holm correction applied for multiple pairwise comparisons).

---

## Reproducibility

The repository provides the datasets, prompts, model outputs, evaluation results, and statistical analysis files used in the thesis.

A fixed random seed (`random_state = 42`) was used when sampling the 100 proverbs for the Context Application Task.

The repository is intended to provide the materials necessary to inspect and reproduce the evaluation procedure and reported analyses.

---

## Thesis Information

- **Title:** *Evaluating LLMs on Taiwanese Proverbs: A Study of Interpretation and Semantic Understanding*
- **Author:** KaiHui Yang
- **Supervisor:** Dr. Çağrı Çöltekin
- **Institute:** Seminar für Sprachwissenschaft, University of Tübingen
- **Date:** September 23, 2026