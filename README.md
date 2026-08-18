# Student Feedback Service Improvement Analysis

**Business Analytics | Python | Text Analysis | Service Improvement**

This portfolio project is based on my MSc Business Analytics dissertation, **Using Sentiment Analysis to Improve Student Support Services**, completed at Alliance Manchester Business School, The University of Manchester.

The project focuses on a practical question: **how can large volumes of open-ended student feedback be converted into consistent, decision-ready insights that help universities identify recurring concerns, prioritize improvement areas, and monitor whether actions work over time?**

![Student Feedback Analytics Workflow](images/01_feedback_analytics_workflow.svg)

## Business Problem

Universities collect open-ended feedback across modules and semesters, but reviewing large volumes of free-text comments manually makes it difficult to identify recurring issues consistently, compare patterns over time, and determine where intervention may be needed.

The analysis therefore focused on building a repeatable process that could:

- organize unstructured feedback into consistent categories;
- identify recurring satisfaction and dissatisfaction themes;
- distinguish broad patterns from isolated comments;
- flag areas where interpretation requires caution;
- connect findings to practical service improvement actions;
- support follow-up measurement in a later reporting cycle.

## Decision Context

The intended users of the analysis are programme leadership, teaching teams, student-experience teams, and reporting owners who need to understand where student experience issues are recurring and what should happen next.

The analysis supports questions such as:

- Which areas of the student experience show repeated concerns?
- Which positive practices should be protected or expanded?
- Which feedback requires closer review rather than being treated as a simple positive or negative signal?
- Where could teaching, course structure, practical learning, or student interaction be improved?
- Which issues should be acted on first, who should own the action, and how should improvement be measured?

## Business Analysis Case Study

To extend the dissertation from analysis into an implementation-ready case study, I translated the research findings into a set of proposed business analysis artifacts. These are clearly separated from the original research findings: stakeholder interviews, live implementation costs, and post-intervention outcomes were not available and are not presented as observed facts.

| Artifact | What it demonstrates |
|---|---|
| [Stakeholder & Decision Matrix](ba_artifacts/01_stakeholder_decision_matrix.md) | Links stakeholder needs to specific decisions, evidence, and expected outputs. |
| [Future-State Feedback Process](ba_artifacts/02_future_state_process.md) | Converts the feedback problem into a closed-loop process with quality gates, human review, action ownership, and follow-up measurement. |
| [Business Requirements & Acceptance Criteria](ba_artifacts/03_business_requirements.md) | Defines traceable requirements for consistent reporting, exception handling, theme identification, and follow-up. |
| [Improvement Prioritization](ba_artifacts/04_prioritization_framework.md) | Sequences improvement areas using evidence breadth, student relevance, change leverage, and implementation complexity without inventing unsupported ROI or frequency values. |
| [Risk & Controls](ba_artifacts/05_risk_and_controls.md) | Translates data limitations and interpretation errors into decision risks, controls, triggers, and ownership. |
| [Measurement & UAT](ba_artifacts/06_measurement_and_uat.md) | Defines proposed outcome measures, reporting controls, and end-to-end acceptance scenarios. |

[View the full business analysis artifact set](ba_artifacts/README.md)

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

The final dataset contained approximately **53.8% positive**, **27.4% neutral**, and **18.8% negative** feedback. Overall satisfaction was strong, while a substantial amount of critical and suggestion-oriented feedback still warranted deeper review.

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

The analysis showed that negative feedback could sometimes be expressed indirectly, while neutral comments often contained suggestions that were difficult to separate cleanly from criticism. A reporting process should therefore retain context and a manual-review path for ambiguous cases.

## Improvement Priorities

![From Feedback Patterns to Improvement Actions](images/03_insight_to_action_map.svg)

The dissertation translated recurring feedback patterns into four improvement areas:

| Area | Recurring issue | Suggested action |
|---|---|---|
| Teaching interaction | Limited delivery quality or interactivity | Strengthen training around interactive teaching and responsiveness |
| Course structure | Poor pacing or unstructured delivery | Standardize course structure, weekly objectives, and syllabus design |
| Practical learning | Limited practical relevance in labs or course content | Increase applied cases, projects, and practice-oriented activities |
| Student interaction | Limited structured opportunities for questions and feedback | Introduce regular Q&A and mid-semester feedback opportunities |

For implementation planning, the portfolio extension groups **course structure** and **teaching interaction** as earlier intervention candidates because they combine broad relevance with relatively clear actions. Practical learning and structured interaction remain material priorities but may require greater curriculum, assessment, or scheduling coordination. This is an implementation judgement, not a claim that the first two had the highest observed complaint counts.

## Proposed Success Measures

The dissertation proposed improvement actions but did not implement them in a live university process. A future implementation could evaluate both outcomes and reporting quality through measures such as:

- recurring issue rate for a defined target theme;
- proportion of prioritized issues with an accountable owner;
- post-intervention change in the targeted theme across comparable reporting periods;
- analysis-ready data retention and exclusion rates;
- response volume or coverage context by module and period;
- manual-review exception rate for ambiguous comments;
- persistence of previously prioritized issues after action.

A fall in negative feedback alone would not be sufficient evidence of improvement if response coverage also fell materially. Outcome, coverage, and control measures should therefore be reviewed together.

## Supporting Technical Validation

The classification method was treated as a supporting component of the broader analysis rather than the final outcome.

A contextual text-classification approach was compared with a simpler TF-IDF + SVM baseline. Two evaluation scenarios were used:

- **Random split:** stratified 80/10/10 train, validation, and test split.
- **Temporal split:** 2022/23 and 2023/24 used for training and validation, with 2024/25 held out as unseen future-period feedback.

The temporal split tested whether a process built on historical feedback could remain useful when later feedback arrived.

![Model Performance Across Evaluation Scenarios](images/02_model_performance.svg)

| Evaluation | Method | Accuracy | Positive F1 | Negative F1 | Neutral F1 |
|---|---|---:|---:|---:|---:|
| Random split | Contextual classifier | **81%** | **0.92** | **0.63** | **0.63** |
| Random split | SVM baseline | 72% | 0.80 | 0.62 | 0.59 |
| Temporal split | Contextual classifier | **87%** | **0.93** | **0.84** | 0.55 |

The future-period evaluation showed stronger identification of negative feedback, while neutral feedback remained less consistent. The practical implication is to use classification to organize and prioritize feedback while retaining human review for ambiguous or suggestion-oriented comments.

## Limitations

- The dataset represents a single institutional context, limiting broader generalizability.
- Neutral and suggestion-oriented feedback remained more difficult to classify consistently.
- The reported validation metrics cannot be fully reproduced from the public repository because the institutional dataset is not distributed.
- The recommendations were derived from historical feedback and were not implemented or measured as part of the dissertation.
- The stakeholder matrix, requirements, prioritization, controls, measurement framework, and UAT scenarios are proposed portfolio extensions rather than outputs validated through a live university change initiative.
- Classification should support, not replace, qualitative review when decisions affect student experience.
