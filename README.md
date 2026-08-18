# Student Feedback Service Improvement Analysis

**Business Analytics | Python | Text Analysis | Service Improvement**

This portfolio project is based on my MSc Business Analytics dissertation, **Using Sentiment Analysis to Improve Student Support Services**, completed at Alliance Manchester Business School, The University of Manchester.

The project focuses on a practical question: **how can large volumes of open-ended student feedback be converted into consistent, decision-ready insights that help universities identify recurring concerns and improve student support services?**

![Student Feedback Analytics Workflow](images/01_feedback_analytics_workflow.svg)

## Business Problem

Universities collect open-ended feedback across modules and semesters, but reviewing large volumes of free-text comments manually makes it difficult to identify recurring issues consistently, compare patterns over time, and determine where intervention may be needed.

The analysis therefore focused on building a repeatable process that could:

- organize unstructured feedback into consistent categories;
- identify recurring satisfaction and dissatisfaction themes;
- distinguish broad trends from isolated comments;
- flag areas where interpretation requires caution;
- connect findings to practical service improvement actions.

## Decision Context

The intended users of the analysis are programme leadership, teaching teams, and student-support decision-makers who need to understand where student experience issues are recurring and where improvement efforts may be most useful.

The analysis is designed to support decisions such as:

- Which areas of the student experience show repeated concerns?
- Which positive practices should be protected or expanded?
- Which feedback requires closer review rather than being treated as a simple positive or negative signal?
- Where could teaching, course structure, practical learning, or student interaction be improved?

## Data

The study used **1,178 anonymized student feedback responses** collected through The University of Manchester's official lecture evaluation system across **six semesters from 2022/23 to 2024/25**.

The feedback covered multiple aspects of the learning experience, including lecture quality, assessment methods, instructor interaction, learning resources, and course delivery.

The original feedback text and labeled derivatives are **not included in this public repository**. Although the source data were anonymized, public redistribution permission was not assumed. A small **synthetic sample** is included only to demonstrate the expected data structure and workflow.

## Data Quality and Preparation

Before analysis, missing and blank responses, duplicate comments, and comments shorter than three words were removed. This reduced the analysis-ready dataset from **1,178 to 1,022 comments**, retaining **86.76%** of the original responses.

The cleaning rules were kept explicit because they determine which records contribute to downstream reporting and affect the consistency of semester-level comparisons.

A three-category coding scheme was used for positive, negative, and neutral feedback. A 5% re-check of manually labeled feedback produced **98.35% intra-coder agreement**, providing an additional quality check on the classification standard used throughout the analysis.

## Key Findings

### 1. Most feedback was positive, but a meaningful share still required attention

The final dataset contained approximately **53.8% positive**, **27.4% neutral**, and **18.8% negative** feedback. The distribution showed that overall satisfaction was strong, while a substantial amount of critical and suggestion-oriented feedback still warranted deeper review.

### 2. Negative feedback tended to contain more detail

Negative comments averaged **46.56 words**, compared with **20.01 words** for positive comments and **12.25 words** for neutral comments. Longer negative comments often contained more specific explanations of dissatisfaction, making them particularly useful for identifying service issues.

### 3. Recurring strengths and weaknesses appeared around the same service areas

Positive feedback frequently highlighted:

- active and responsive instructors;
- well-structured classes;
- useful and accessible learning materials;
- opportunities for interaction and discussion.

Negative feedback repeatedly pointed to the absence or weakness of those same factors, including poor pacing, limited interactivity, low practical relevance, and assessment or lab structure issues.

### 4. Some feedback remained difficult to classify consistently

The analysis showed that negative feedback could sometimes be expressed indirectly, while neutral comments often contained suggestions that were difficult to separate cleanly from criticism. This means a reporting process should not rely on a single classification output without considering context.

## Improvement Priorities

![From Feedback Patterns to Improvement Actions](images/03_insight_to_action_map.svg)

The recurring feedback patterns were translated into four practical areas for improvement:

| Area | Recurring issue | Suggested action |
|---|---|---|
| Teaching interaction | Limited delivery quality or interactivity | Strengthen training around interactive teaching and responsiveness |
| Course structure | Poor pacing or unstructured delivery | Standardize course structure, weekly objectives, and syllabus design |
| Practical learning | Limited practical relevance in labs or course content | Increase applied cases, projects, and practice-oriented activities |
| Student interaction | Limited structured opportunities for questions and feedback | Introduce regular Q&A and mid-semester feedback opportunities |

These recommendations come directly from the strength-and-weakness mapping developed in the dissertation rather than from the classification results alone.

## Proposed Success Measures

The dissertation proposed improvement actions but did not implement them in a live university process. If the framework were operationalized, I would recommend tracking measures such as:

- frequency of repeated negative themes across semesters;
- proportion of feedback reviewed within the reporting cycle;
- change in targeted module satisfaction after an intervention;
- number of recurring issues escalated for action;
- change in negative feedback related to the specific service area being addressed.

These measures would help determine whether recommended interventions actually improve the student experience rather than stopping at insight generation.

## Analytical Workflow

The project followed a structured workflow from problem definition through deployment:

1. **Problem definition**: define how open-ended feedback could support service improvement.
2. **Data collection**: consolidate multi-year feedback across six semesters.
3. **Data cleaning**: establish a consistent analysis-ready population.
4. **Feature representation and labeling**: create a consistent sentiment classification standard.
5. **Classification**: organize comments into positive, negative, and neutral categories.
6. **Validation**: test reliability using both random and future-period evaluation.
7. **Service mapping**: connect recurring patterns to improvement areas.
8. **Deployment concept**: use the process for recurring semester-level monitoring and reporting.

## Technical Validation

The classification method was treated as a supporting component of the broader analysis rather than the final outcome.

A fine-tuned DistilBERT classifier was compared with a TF-IDF + SVM baseline. Two evaluation scenarios were used:

- **Random split:** stratified 80/10/10 train, validation, and test split.
- **Temporal split:** 2022/23 and 2023/24 used for training and validation, with 2024/25 held out as unseen future-period feedback.

The temporal split was particularly important because it tested whether a process built on historical feedback could remain useful when later feedback arrived.

![Model Performance Across Evaluation Scenarios](images/02_model_performance.svg)

| Evaluation | Method | Accuracy | Positive F1 | Negative F1 | Neutral F1 |
|---|---|---:|---:|---:|---:|
| Random split | DistilBERT | **81%** | **0.92** | **0.63** | **0.63** |
| Random split | SVM | 72% | 0.80 | 0.62 | 0.59 |
| Temporal split | DistilBERT | **87%** | **0.93** | **0.84** | 0.55 |

The future-period evaluation showed stronger identification of negative feedback, while neutral feedback remained less consistent. This supports using classification to organize and prioritize feedback, while retaining human review for ambiguous or suggestion-oriented comments.

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
├── images/
│   ├── 01_feedback_analytics_workflow.svg
│   ├── 02_model_performance.svg
│   └── 03_insight_to_action_map.svg
├── requirements.txt
└── .gitignore
```

## Limitations

- The dataset represents a single institutional context, limiting broader generalizability.
- Neutral and suggestion-oriented feedback remained more difficult to classify consistently.
- The reported validation metrics cannot be fully reproduced from the public repository because the institutional dataset is not distributed.
- The recommendations were derived from historical feedback and were not implemented or measured as part of the dissertation.
- Classification should support, not replace, qualitative review when decisions affect student experience.
