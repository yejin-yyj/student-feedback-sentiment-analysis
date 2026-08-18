# Measurement Framework and UAT Scenarios

The dissertation proposes service-improvement actions but does not report live implementation outcomes. The measures and UAT scenarios below define how the proposed process could be operationalized and validated without presenting unobserved benefits as achieved results.

## Proposed success measures

| Objective | Measure | Definition | Why it matters |
|---|---|---|---|
| Detect recurring concerns earlier | Recurring issue rate | Share of analysis-ready comments linked to a defined target theme within a reporting period | Shows whether a concern is isolated or persistent enough to warrant action |
| Improve issue follow-up | Action ownership rate | Share of prioritized issues with a documented owner and next action | Prevents analysis from ending without accountability |
| Reduce repeated concerns | Post-intervention theme change | Change in the target theme's share between the intervention period and a comparable later period | Connects the intervention to a measurable student-experience signal |
| Maintain reporting reliability | Analysis-ready retention rate | Analysis-ready records divided by collected feedback records, with exclusions categorized | Makes changes in data quality visible rather than hidden |
| Protect representativeness | Response coverage context | Response count and, where available, response rate by module and period | Helps decision-makers interpret whether an apparent trend is supported by broad participation |
| Control ambiguous cases | Manual-review exception rate | Share of comments sent for contextual review because interpretation is ambiguous or potentially complaint-like | Measures how much judgement remains outside the automated classification path |
| Monitor unresolved issues | Persistent issue rate | Share of prioritized themes that remain material across consecutive reporting cycles after action | Highlights where the initial intervention may not have addressed the underlying problem |

## Measurement logic

The measures should be interpreted together. For example, a fall in negative-theme share is not sufficient evidence of improvement if response coverage also falls materially. Likewise, a low exception rate is not automatically desirable if it results from overly aggressive categorization of ambiguous feedback.

A credible reporting cycle would therefore review **outcome, coverage, and control measures together**.

## Example UAT scenarios

These scenarios test the proposed reporting process rather than the dissertation model itself.

### UAT-01: Apply consistent data-quality rules

**Given** a semester dataset contains blank comments, duplicate comments, and responses shorter than the defined minimum length  
**When** the reporting dataset is prepared  
**Then** excluded records are removed consistently  
**And** the number of exclusions is available by exclusion reason  
**And** the analysis-ready record count reconciles to the original input.

### UAT-02: Compare periods using consistent definitions

**Given** at least two academic periods have been processed  
**When** a programme reviewer compares a sentiment or recurring-theme measure  
**Then** both periods use the same inclusion and metric definitions  
**And** the underlying record counts are visible  
**And** the comparison can be traced back to period/module context.

### UAT-03: Review potentially hidden complaints

**Given** a comment is categorized as neutral but contains language that may indicate dissatisfaction  
**When** it is routed to the exception-review process  
**Then** an authorized reviewer can inspect the original context  
**And** record the final interpretation  
**And** preserve the reason for any override.

### UAT-04: Trace an aggregated issue to evidence

**Given** a recurring theme appears in the reporting summary  
**When** a decision-maker requests supporting evidence  
**Then** the theme can be traced to the relevant reporting period and service area  
**And** authorized users can review representative source comments  
**Without** exposing source text in the public portfolio.

### UAT-05: Convert a finding into an accountable action

**Given** a recurring issue is accepted as a priority  
**When** the improvement action is recorded  
**Then** the action has a stakeholder owner, target service area, and follow-up reporting period  
**And** the same issue definition is available for later measurement.

### UAT-06: Evaluate an intervention in a later cycle

**Given** an improvement action was implemented for a defined issue  
**When** the next comparable feedback period is analyzed  
**Then** the target theme is measured using the same definition  
**And** the result is reviewed alongside response coverage  
**And** the issue is marked as improving, persistent, or requiring further investigation.

## Exit criteria for a reporting release

A semester reporting pack should not be treated as decision-ready unless:

1. input and analysis-ready counts reconcile;
2. exclusion rules are applied consistently;
3. reporting-period and module traceability are preserved;
4. ambiguous cases can be reviewed separately;
5. recurring themes can be supported by underlying evidence;
6. prioritized issues have a defined action path;
7. limitations in coverage or interpretation are disclosed.