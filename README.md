# Student Feedback Sentiment Analysis

**Business Analytics | Python | NLP | DistilBERT | SVM**

This portfolio project is based on my MSc Business Analytics dissertation, **Using Sentiment Analysis to Improve Student Support Services**, completed at Alliance Manchester Business School, The University of Manchester.

## Business Problem

Universities collect large volumes of open-ended student feedback, but free-text comments are difficult to review consistently at scale. The business question was therefore not simply whether a model could classify sentiment, but whether feedback could be converted into a repeatable decision-support process that helps identify emerging concerns, validate service strengths, and prioritize improvement actions.

## Project Objective

The analysis was designed to:

1. turn unstructured feedback into a consistent positive / negative / neutral classification;
2. compare a contextual NLP model with a simpler baseline to justify model choice;
3. test whether the model remained useful on future, unseen feedback rather than only a random sample;
4. investigate classification errors that could hide genuine student concerns;
5. translate recurring patterns into practical recommendations for student-support services.

## Data

The original study used **1,178 anonymized student feedback responses** collected through The University of Manchester's official lecture evaluation system across **six semesters from 2022/23 to 2024/25**. The university provided the data for research purposes.

The original feedback text and labeled derivatives are **not included in this public repository**. Although the source data were anonymized, anonymization does not by itself grant permission for public redistribution. A small **synthetic sample** is included only to demonstrate the expected schema and workflow.

## Analytical Approach

### 1. Data quality and preparation

Before modeling, I assessed whether the feedback was usable for consistent analysis. Missing and blank responses, duplicates, and comments shorter than three words were removed while preserving linguistic context needed by transformer models. This reduced the analytical dataset from **1,178 to 1,022 comments**.

**BA perspective:** cleaning decisions were treated as business rules because they determine what counts as valid evidence in downstream reporting.

### 2. Reliable ground truth

A three-class coding scheme was used for positive, negative, and neutral sentiment. A 5% re-check of manually labeled feedback produced **98.35% intra-coder agreement**, providing a quality check on the target labels used for model evaluation.

**BA perspective:** the model is only as reliable as the classification standard it is trained against, so label consistency was validated before comparing algorithms.

### 3. Model comparison for decision support

The main model was a fine-tuned `distilbert-base-uncased` classifier, compared with a TF-IDF + SVM baseline. The objective was not to maximize technical complexity, but to determine whether contextual language understanding materially improved classification quality.

### 4. Future-period validation

Two evaluation scenarios were used:

- **Random split:** stratified 80/10/10 train, validation, and test split.
- **Temporal split:** historical feedback from 2022/23 and 2023/24 used for training/validation, with 2024/25 held out as unseen future data.

**BA perspective:** temporal validation better reflects a real reporting use case, where a model trained on historical feedback must support decisions on newly arriving comments.

### 5. Error analysis and root-cause thinking

Aggregate accuracy was not treated as sufficient evidence of success. Misclassified comments were reviewed to understand where the model could mask complaints or confuse neutral suggestions with other sentiment classes.

**BA perspective:** this step focuses on operational risk, not only model score. A high overall accuracy can still be problematic if important negative feedback is systematically missed.

### 6. Translating analysis into actions

Recurring strengths and weaknesses were mapped to specific student-support actions, including faculty teaching practices, course structure, practical learning content, and structured student interaction.

## Results

| Evaluation | Model | Accuracy | Positive F1 | Negative F1 | Neutral F1 |
|---|---|---:|---:|---:|---:|
| Random split | DistilBERT | **81%** | **0.92** | **0.63** | **0.63** |
| Random split | SVM | 72% | 0.80 | 0.62 | 0.59 |
| Temporal split | DistilBERT | **87%** | **0.93** | **0.84** | 0.55 |

### Decision-relevant interpretation

DistilBERT outperformed the SVM baseline on the random split, supporting the use of contextual NLP for nuanced feedback. On unseen 2024/25 data, overall accuracy increased to **87%** and negative-class F1 improved to **0.84**, but neutral F1 declined to **0.55**.

The key takeaway is therefore not simply that the model achieved 87% accuracy. The more useful business conclusion is that it became stronger at identifying complaints, while neutral and suggestion-oriented feedback remained a monitoring risk that would still require human review.

## Business / Service Recommendations

The analysis linked recurring feedback patterns to actions such as:

- strengthen faculty training around interactive teaching and responsiveness;
- standardize syllabus structure and weekly learning objectives where course organization is a recurring issue;
- expand practice-oriented cases, projects, and lab activities where students perceive low practical value;
- introduce structured Q&A and mid-semester feedback opportunities to surface concerns earlier;
- retain human review for neutral or ambiguous feedback rather than fully automating decisions.

## Repository Structure

```text
student-feedback-sentiment-analysis/
├── README.md
├── notebooks/
│   ├── 01_data_preprocessing.ipynb
│   └── 02_distilbert_modeling_and_evaluation.ipynb
├── data/
│   └── sample_feedback.csv
├── results/
│   └── model_performance.csv
├── requirements.txt
└── .gitignore
```

## Notebook Notes

The notebooks are **portfolio-cleaned versions** of the original dissertation workflow. Exploratory cells, local file paths, private student feedback, and intermediate experiments were removed. The public notebooks are organized around the final analytical logic and emphasize the reasoning behind data quality, validation, error analysis, and decision implications.

## Limitations

- The dataset represents a single institutional context, limiting external generalizability.
- Neutral feedback remained more difficult to classify on unseen future data.
- The reported model metrics cannot be fully reproduced from the public repository because the institutional dataset is not distributed.
- Sentiment classification should support, not replace, qualitative review when decisions affect student experience.
