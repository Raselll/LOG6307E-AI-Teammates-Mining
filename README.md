# LOG6307E — Repository-Level Review Behaviour for AI Coding Agents

This repository contains the replication package for our LOG6307E Mining Software Repositories assignment.

The project builds on the AIDev dataset and studies how human code-review behaviour changes as software repositories gain experience working with AI coding agents.

The study was inspired by *Habituation at the Gate*, which examines changes in reviewer behaviour over time. While that work focuses on individual reviewers, our analysis investigates similar patterns at the repository level and compares agent-authored pull requests with human-authored pull requests.

## Team

- Rasel Chowdhury
- Maxim Laurin
- Thomas Chanu
- Riad Baroudi

## Research Objective

The objective of this study is to investigate whether human review behaviour changes over a repository's history of working with AI coding agents, and whether similar changes are observed for human-authored pull requests in the same repositories.

## Research Questions

### RQ1 — Review Coverage

How does formal review coverage of agent-authored pull requests change from the early to the late stages of a repository's agentic history, compared with human-authored pull requests in the same repositories?

### RQ2 — Approval Behaviour

Among formally reviewed pull requests, how does approval behaviour change from the early to the late stages of a repository's agentic history, and does that change differ between agent-authored and human-authored pull requests?

## Metrics

### Review Coverage

Review Coverage = PRs receiving at least one formal human review / total PRs

This metric measures how frequently pull requests receive direct human review.

### Approval Rate

Approval Rate = approved human review events / total human review events

This metric measures the proportion of formal human review events that result in approval.

## Data

The main data source is the AIDev dataset:

https://huggingface.co/datasets/hao-li/AIDev

For reproducibility, the analysis uses the following fixed AIDev revision:

`68ed5f4b`

The analysis uses:

- `pull_request.parquet` for agent-authored pull requests
- `human_pull_request.parquet` for human-authored pull requests
- `pr_reviews.parquet` for review information associated with agent-authored pull requests

Detailed review-event data for human-authored pull requests were previously collected and are stored directly in this repository.

## Final Study Sample

The final analysis contains:

- 46 repositories
- 6,147 pull requests
- 4,113 agent-authored pull requests
- 2,034 human-authored pull requests

Repositories with unavailable detailed human review data were excluded symmetrically from both the Agentic and Human groups.

## Early and Late Periods

Each repository's history with AI coding agents is divided into Early and Late periods.

The analysis compares review behaviour within the same repositories across these periods.

Human-authored pull requests from the same repositories are used as the comparison group.

## Statistical Analysis

The analysis uses paired Wilcoxon signed-rank tests.

For each research question, we compare:

1. Agentic Early vs Agentic Late
2. Human Early vs Human Late
3. The Early-to-Late change for Agentic PRs vs the Early-to-Late change for Human PRs

For RQ2, the primary analysis requires at least five human review events per repository/origin/period cell.

Sensitivity analyses are also performed using thresholds of:

- 3 reviews
- 5 reviews
- 10 reviews

## Main Findings

### RQ1 — Review Coverage

The distributions show differences in review coverage between Agentic and Human pull requests and between Early and Late periods.

However, the paired statistical tests do not show a statistically significant Early-to-Late change in review coverage for either Agentic or Human pull requests.

The difference between the two trajectories is also not statistically significant.

### RQ2 — Approval Behaviour

The approval-rate distributions vary across PR origin and period.

However, the paired statistical tests do not show a statistically significant Early-to-Late change in approval rate for either Agentic or Human pull requests.

The difference between the two trajectories is also not statistically significant.

The sensitivity analyses using thresholds of 3, 5, and 10 reviews per cell lead to the same overall conclusion.

## Repository Structure

```text
.
├── data/
│   ├── cleaned_pr_data.csv
│   ├── human_pr_inline_comments.jsonl
│   ├── human_pr_review_events.jsonl
│   ├── human_pr_reviews.jsonl
│   ├── repository_metrics.csv
│   └── rq2_sensitivity.csv
│
├── figures/
│   ├── rq1_review_coverage.png
│   └── rq2_approval_rate.png
│
├── notebooks/
│   ├── 01_exploration.ipynb
│   └── 02_analysis.ipynb
│
├── README.md
└── requirements.txt
```

## Notebooks

### `notebooks/01_exploration.ipynb`

Contains the initial dataset exploration, dataset-version investigation, sample-selection process, and feasibility checks.

### `notebooks/02_analysis.ipynb`

Contains the final analysis used for the assignment.

It performs:

- data loading
- data cleaning
- repository selection
- Early/Late classification
- review metric calculation
- RQ1 analysis
- RQ2 analysis
- Wilcoxon statistical tests
- sensitivity analysis
- CSV exports
- figure generation

## Output Files

### `data/cleaned_pr_data.csv`

Final cleaned PR-level dataset.

### `data/repository_metrics.csv`

Repository-level metrics used for the Agentic/Human and Early/Late comparisons.

### `data/human_pr_review_events.jsonl`

Detailed human-authored PR review-event data.

### `data/rq2_sensitivity.csv`

RQ2 sensitivity-analysis results.

### `figures/rq1_review_coverage.png`

Visualization of human review coverage across:

- Agentic Early
- Agentic Late
- Human Early
- Human Late

### `figures/rq2_approval_rate.png`

Visualization of human approval rates across the same four groups.

## Reproducing the Analysis

Clone the repository:

```bash
git clone https://github.com/Raselll/LOG6307E-AI-Teammates-Mining.git
cd LOG6307E-AI-Teammates-Mining
```

Create a virtual environment.

Windows:

```bash
python -m venv .venv
.venv\Scripts\activate
```

macOS/Linux:

```bash
python3 -m venv .venv
source .venv/bin/activate
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Start Jupyter:

```bash
jupyter notebook
```

Open:

```text
notebooks/02_analysis.ipynb
```

Then restart the kernel and run all cells from the beginning.

No GitHub API token is required for the final analysis.

## Generated Outputs

Running `02_analysis.ipynb` generates or updates:

```text
data/cleaned_pr_data.csv
data/repository_metrics.csv
data/rq2_sensitivity.csv
figures/rq1_review_coverage.png
figures/rq2_approval_rate.png
```

## Reproducibility Notes

The fixed AIDev revision `68ed5f4b` is used so that future changes to the upstream dataset do not change the study sample or results.

The detailed human review-event data required for the comparison are stored in the repository, so the final analysis does not depend on live GitHub API calls.

One repository with unavailable detailed human review data was excluded from both Agentic and Human groups to preserve a symmetric within-repository comparison.