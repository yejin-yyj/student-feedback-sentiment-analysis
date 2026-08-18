# Proposed Business Requirements and Acceptance Criteria

These requirements are a portfolio extension of the dissertation. They translate the research findings and deployment concept into a structured reporting process. They are not presented as requirements formally elicited from university stakeholders.

## Requirement set

| ID | Requirement | Rationale | Priority | Acceptance criteria |
|---|---|---|---|---|
| BR-01 | The process must retain academic year, semester, and module/unit context for each feedback record. | Trend and period comparison require traceability. | Must | Every analysis-ready record can be linked to its reporting period and module/unit. |
| BR-02 | The process must apply consistent inclusion rules before reporting. | Missing, duplicate, and very short responses can distort comparisons. | Must | Defined quality rules are applied consistently and excluded records are countable by reason. |
| BR-03 | The process must distinguish positive, negative, and neutral feedback using a documented classification standard. | The dissertation uses a three-category coding scheme and validates labeling consistency. | Must | Each included record has one documented category and the coding definitions are available to reviewers. |
| BR-04 | The process must preserve access to original comment context for authorized reviewers. | Indirect criticism and suggestion-oriented comments may be misunderstood when reduced to a category. | Must | Reviewers can trace an aggregated issue back to the underlying comment and reporting context. |
| BR-05 | The process must support comparison across reporting periods. | The study spans six semesters and tests later-period feedback separately. | Must | Users can compare the same measure or theme across at least two academic periods using consistent definitions. |
| BR-06 | The process must support manual review of ambiguous or potentially hidden complaints. | Error analysis found that negative feedback can be expressed indirectly and neutral comments can be difficult to interpret. | Must | A reviewer can identify and inspect exception cases before final reporting or escalation. |
| BR-07 | The process should identify recurring themes beyond sentiment totals. | Service recommendations were derived from repeated strengths and weaknesses, not classification alone. | Should | Reporting includes recurring themes linked to service areas such as teaching interaction, course structure, practical learning, and student interaction. |
| BR-08 | The process should connect material recurring issues to a recommended action or review owner. | The dissertation's service mapping translates findings into improvement actions. | Should | Each prioritized issue has an action category and proposed accountable stakeholder group. |
| BR-09 | Reporting should include volume and response-coverage context alongside findings. | Uneven participation can limit representativeness. | Should | Reports show the denominator or coverage context needed to interpret trend and theme results. |
| BR-10 | The process should support post-intervention monitoring in a later reporting cycle. | A service-improvement process requires evidence that issues improved after action. | Should | A selected issue can be re-measured using the same definition in a later period. |
| BR-11 | Public portfolio outputs must not expose institutional feedback text. | The source data were provided for research and public redistribution permission was not assumed. | Must | Public files contain no original institutional feedback text or personally identifying information. |
| BR-12 | Technical performance metrics should be treated as validation evidence, not as the service outcome. | Classification quality supports reporting reliability but does not itself demonstrate student-experience improvement. | Must | Service reporting separates classification validation from intervention success measures. |

## Example functional interpretation

The dissertation itself was not a production reporting system, but the requirements imply a future reporting experience with capabilities such as:

- filter by academic period and module/unit;
- review sentiment distribution and recurring themes;
- inspect the source context behind a flagged issue;
- distinguish routine aggregated reporting from comments requiring manual review;
- assign an issue to an improvement area;
- compare the same issue in a later period.

## Traceability example

| Business need | Supporting requirement(s) | Evidence produced |
|---|---|---|
| Identify recurring concerns | BR-05, BR-07 | Period comparison and recurring-theme summary |
| Avoid missing indirect complaints | BR-04, BR-06 | Manual-review exception set |
| Turn findings into action | BR-08, BR-10 | Improvement action and follow-up measure |
| Maintain reporting credibility | BR-02, BR-09 | Data-quality summary and coverage context |

This traceability helps prevent the analytical method from becoming disconnected from the decision it is intended to support.