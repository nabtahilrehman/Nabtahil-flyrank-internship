Search Opportunity Prioritization Using Historical Search Performance Signals
Abstract

This project investigates whether historical search performance signals can be used to identify pages that may represent SEO optimization opportunities. Using the FlyRank ML Internship dataset, search performance observations including impressions, clicks, average position, and engagement-related metrics were examined. A rule-based opportunity prioritization framework and a machine learning workflow were explored to support content review decisions. Particular attention was given to data contracts, leakage prevention, validation design, and responsible interpretation of model outputs. The resulting framework is intended as a decision-support tool that helps prioritize pages for review rather than automate SEO decisions.

Introduction

Large websites often contain thousands of indexed pages, making manual SEO analysis difficult and time-consuming. Teams responsible for SEO and content optimization must determine which pages deserve attention first while working with limited resources.

Traditional workflows often involve manually reviewing reports and identifying optimization opportunities through expert judgement. While valuable, this approach can become difficult to scale as websites grow.

This project explores whether historical search performance data can support a structured content-prioritization process. The objective is to identify pages that may represent SEO opportunities based on observed performance patterns.

The goal is not to predict Google's ranking algorithms or guarantee future performance improvements. Instead, the project aims to provide a consistent and data-informed framework for prioritizing content review activities.

Research Question
Primary Research Question

Can historical search performance signals be used to prioritize pages that may represent SEO opportunities?

Decision Supported

Which pages should be reviewed first for potential SEO improvement?

Intended Action

SEO analysts and content managers can review high-priority pages before investing resources in lower-priority content.

Cost Of A Wrong Recommendation

Incorrect recommendations may result in:

Time spent reviewing pages with limited opportunity
Missed opportunities on higher-value pages
Reduced efficiency of optimization efforts
Dataset
Dataset Source

FlyRank ML Internship Warehouse Dataset

Tables Reviewed
fact_content_daily_performance
dim_clients
dim_content
Time Window

The analysis focused primarily on warehouse data available during the internship exercises, including the March 2026 partition used for exploratory analysis and validation activities.

Unit Of Analysis

One row represents:

One content item for one client on one report date.

Dataset Grain

The grain was verified as:

Plain Text
1
(report_date,
2
client_hash_id,
3
content_hash_id)
Show more lines

Duplicate checks were performed to confirm the expected structure.

Excluded Information

The following were excluded from predictive use:

Client identifiers
Content identifiers
Future observations
Label-derived variables
Unavailable observations

All analysis used anonymized data and public-safe reporting practices.

Methodology
Feature Selection

The project examined several historical search-performance signals, including:

Google Search Console impressions
Google Search Console clicks
Average search position
Pageviews
Sessions

These variables are available before content review decisions are made and therefore support decision-time recommendations.

Baseline Opportunity Framework

A rule-based prioritization approach was created using observed search performance.

Pages receiving relatively high visibility but limited click activity were ranked higher because they may represent optimization opportunities.

Example reasoning included:
High impression + Low click-through rate = Potential optimization opportunity

Machine Learning Exploration

A machine learning workflow was explored as part of the internship exercises.

The purpose was not to create a production system but to understand:

Feature selection
Data contracts
Leakage prevention
Validation strategies
Model interpretation

Random Forest was selected as an example modeling approach because it can capture nonlinear relationships between search-performance features.

Validation Design

Special attention was given to validation design.

Where applicable, time-aware evaluation strategies were preferred over simple random splits because future information should not influence training data.

The emphasis of the project was placed on honest evaluation rather than maximizing reported performance.

Validation And Leakage Audit
Research Paper Reflection

As part of the validation audit exercise, findings from the FlyRank research paper were reviewed from a methodological perspective.

Finding 1

Machine learning may improve prioritization compared with simple rules.

Methodology Question

How is the target label defined, and does the label remain independent from future information?

Finding 2

Multiple signals may outperform individual metrics.

Methodology Question

Does the validation design provide sufficient evidence for the reported claim across different clients and periods?

Leakage Audit

The final feature set was reviewed to identify potential leakage risks.

The review checked for:

Future observations
Label-derived variables
Identifier leakage
Post-decision information

Excluded variables were removed from consideration whenever they could not reasonably be known at recommendation time.

This process helps maintain the integrity of model evaluation.

Results

The project successfully demonstrated a complete workflow for transforming raw search-performance observations into a prioritized review framework.

The internship exercises showed how:

Search-performance data can be structured
Data contracts can be verified
Features can be evaluated
Leakage can be identified
Validation designs can be improved
Recommendations can be generated responsibly

The resulting prioritization framework provides a repeatable process for identifying pages that may deserve additional investigation.

Because the emphasis of this work was educational and methodological, the focus remains on transparent evaluation and interpretation rather than reporting a production-ready optimization score.

Content Action Playbook
Primary Recommendation

Identify pages that receive substantial visibility but relatively weak click performance.

These pages may warrant additional review because user interest appears higher than observed engagement.

Reason Codes
HIGH_IMPRESSIONS_LOW_CTR

The page receives search visibility but comparatively fewer clicks.

HIGH_VISIBILITY_UNDERPERFORMING

The page appears regularly in search results but generates limited engagement.

POSITION_WITH_OPPORTUNITY

The page demonstrates measurable visibility and may benefit from additional optimization.

Human Review Requirements

Recommendations should always be reviewed by a human analyst before action is taken.

Suggested review process:

Check search intent alignment
Review content quality
Verify business relevance
Consider recent content updates
Evaluate current ranking context
No-Go List

The following actions should never be automated solely on the basis of model output:

Publishing content changes
Deleting content
Redirecting pages
Changing site architecture
Making business decisions without review

The framework is intended to support human judgement rather than replace it.

Monitoring And Retraining

The recommendation framework should be revisited periodically.

Potential monitoring signals include:

Changes in search demand
Declining recommendation usefulness
Shifting feature distributions
Significant ranking volatility

Retraining or reevaluation may be appropriate when new data becomes available or when observed search patterns change substantially.

Limitations And Honest Framing

Several limitations should be considered.

The dataset contains observational search-performance data rather than experimental evidence.

The project cannot determine:

Causation
Content quality
Future ranking behavior
Competitor actions
Future search demand

The framework should therefore be interpreted as:

Observed
Measured
Directional
Decision-support

rather than predictive certainty.

Recommendations indicate potential opportunities for review, not guaranteed outcomes.

Reproducibility
Repository

https://github.com/nabtahilrehman/Nabtahil-flyrank-internship 

Project Artifacts

The workflow is documented through the internship notebooks, including:

Research question development
Data contract verification
Signal audit
Baseline scoring
Modeling workflow
Validation audit
Action playbook creation

These artifacts provide traceability from raw observations to final recommendations.

Acknowledgments And Data Credit

This project was completed as part of the FlyRank Machine Learning Internship.

Built on the FlyRank ML Internship Dataset.

Data Credit:
  https://flyrank.ai

The author acknowledges FlyRank for providing the anonymized search-performance warehouse used for educational and research purposes.
