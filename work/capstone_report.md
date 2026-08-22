Capstone Report — Search Opportunity Prioritization

Author: Nabtahil Rehman

 Lane: Refresh & Content Opportunity Scoring
 
 Repo: https://github.com/nabtahilrehman/Nabtahil-flyrank-internship
 
 Date: August 2026

0. Abstract

This project investigates whether historical search-performance signals can be used to prioritize pages that may represent SEO opportunities. The analysis uses the FlyRank ML Internship dataset, including impressions, clicks, average position, sessions, and pageviews from anonymized search-performance records. A transparent rule-based opportunity score was developed first and then compared with a machine-learning workflow designed to support prioritization decisions. Special attention was given to data contracts, leakage prevention, validation design, and responsible interpretation of outputs. The resulting framework provides a ranked, reason-coded recommendation system intended for human review and decision support rather than automated decision-making.

1. Problem Framing

This project supports the decision of which content pages should be reviewed first for potential SEO improvement.

Unit of Analysis

One content page on a specific reporting date.

Output

A ranked opportunity score and associated reason codes.

Human Action

SEO analysts review high-priority pages before allocating effort to lower-priority content.

Cost of a Wrong Recommendation

A poor recommendation may:

Waste optimization resources.
Delay review of higher-value opportunities.
Reduce efficiency of SEO workflows.
Why ML Helps

Search performance is influenced by multiple interacting signals such as impressions, clicks, rankings, and engagement. Machine learning provides a structured way to combine these signals and support prioritization decisions.

2. Data Safety
Dataset Used

FlyRank ML Internship Warehouse Dataset.

Tables Referenced
fact_content_daily_performance
dim_content
dim_clients
Time Window

March 2026 warehouse partition.

Features Considered
gsc_impressions
gsc_clicks
gsc_avg_position
ga4_pageviews
ga4_sessions
Excluded Information

The following were intentionally excluded:

client identifiers
content identifiers
future observations
unavailable observations
label-derived variables
Leakage Risks Considered

Potential leakage sources included:

target-derived variables
future-window information
identifiers
post-decision data

No client-identifying information appears anywhere in the project artifacts.

3. Baseline

A transparent opportunity score was created before considering more advanced approaches.

Baseline Logic

Pages with:

high impressions
low click-through rates
measurable visibility

were treated as stronger optimization opportunities.

Example Rule
Plain Text
1
Opportunity Score =
2
Impressions × (1 − CTR)
Show more lines

where:

Plain Text
1
CTR = Clicks ÷ Impressions
Show more lines
Why It Is Fair

The baseline uses only observable information available at recommendation time.

The baseline provides an interpretable comparison against any machine-learning workflow.

4. Model / Analysis

A machine-learning workflow was explored to determine whether observed search-performance signals could support content-prioritization decisions.

Method

Random Forest was selected as an illustrative model because it can capture nonlinear relationships among search-performance variables.

Features Used
gsc_impressions
gsc_clicks
gsc_avg_position
ga4_pageviews
ga4_sessions
Features Excluded
client identifiers
content identifiers
future observations
label-derived variables
Target

The target is a search-opportunity prioritization score intended to support ranking and review decisions.

5. Evaluation
Validation Design

A validation-focused workflow was used during the internship exercises.

Time-aware evaluation approaches were preferred whenever possible to reduce information leakage.

Error Analysis

Potential errors include:

pages affected by temporary search-demand changes
pages influenced by external ranking factors
pages where CTR is affected by SERP features
Honest Interpretation

The framework should be treated as a prioritization system rather than a prediction of future SEO success.

All findings represent observed and measured relationships.

6. Interpretation

Several observations emerged from the analysis.

Key Findings
Search visibility is an important prioritization signal.
Pages with high impressions and limited click performance may warrant additional review.
Multiple search-performance signals provide more context than any individual metric.
Surprises

Some pages receiving substantial impressions showed limited engagement despite strong visibility.

Negative Result

Visibility alone does not guarantee that a page represents an optimization opportunity.

7. Recommendation
Primary Recommendation

Prioritize pages receiving:

high impressions
lower relative CTR
measurable search visibility
Reason Codes
HIGH_IMPRESSIONS_LOW_CTR

The page receives visibility but comparatively limited clicks.

HIGH_VISIBILITY_UNDERPERFORMING

The page appears frequently in search results but engagement is lower than expected.

POSITION_WITH_OPPORTUNITY

The page demonstrates visibility and may benefit from optimization review.

Confidence

Moderate.

Limits

Recommendations should be treated as decision-support rather than guarantees of future improvement.

Human review remains essential.

8. Reproducibility
Repository

https://github.com/nabtahilrehman/Nabtahil-flyrank-internship

Project Components
Research Question Notebook
Data Contract Notebook
Signal Audit Notebook
Baseline Scoring Notebook
Validation Audit Notebook
Action Playbook Notebook
Environment

Primary libraries:

pandas
numpy
scikit-learn
duckdb
Reproduction Steps
Clone the repository.
Install project dependencies.
Run notebooks in sequence.
Generate the ranked opportunity queue.
Review exported artifacts in work/outputs/.

Random seeds and notebook outputs are documented in the project notebooks.

9. Acknowledgments & Data Credit

This project was completed as part of the FlyRank Machine Learning Internship.

Built on the FlyRank ML Internship Dataset.

Data Credit:

https://flyrank.ai/

The author acknowledges FlyRank for providing anonymized search-performance data for educational and research purposes.
