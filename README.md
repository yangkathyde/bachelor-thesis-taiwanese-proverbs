# Evaluating LLMs on Taiwanese Proverbs

This repository contains the datasets, prompts, model outputs, results, and statistical analyses used in the Bachelor's thesis:

**Evaluating LLMs on Taiwanese Proverbs: A Study of Interpretation and Semantic Understanding**

The study investigates how contemporary large language models (LLMs) interpret and apply Taiwanese proverbs through two complementary evaluation tasks: **Interpretation** and **Context Application**.

## Research Overview

Taiwanese proverbs are culturally embedded expressions whose intended meanings may depend on figurative language, contextual information, and cultural knowledge. This study evaluates whether LLMs can not only interpret the meanings of Taiwanese proverbs, but also select appropriate proverbs for specific conversational situations.

Four LLMs were evaluated:

- Qwen 3.7
- GPT-5.6 Luna
- Gemini 3.6 Flash
- DeepSeek

The evaluation consists of two tasks:

### 1. Interpretation Task

The Interpretation Task evaluates whether an LLM can explain the intended figurative meaning of a Taiwanese proverb in English.

- **Dataset:** 468 Taiwanese proverbs
- **Output:** One-sentence English interpretation
- **Evaluation metric:** BERTScore-F1
- **Reference:** Manually reviewed English interpretations based on Taiwanese dictionary definitions

The detailed BERTScore results for each proverb and model are provided in the `results/` directory, together with model-level performance summaries.

### 2. Context Application Task

The Context Application Task evaluates whether an LLM can select the Taiwanese proverb that best fits a given conversational situation.

- **Dataset:** 100 multiple-choice questions
- **Options:** Four Taiwanese proverbs per question
- **Evaluation metric:** Accuracy
- **Task format:** Select one proverb that best matches the given context

The 100 proverbs used for this task were randomly sampled from the full set of 468 proverbs using a fixed random seed (`random_state = 42`).

The model-level accuracy results are provided in the `results/` directory.

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
├── .gitignore
└── README.md