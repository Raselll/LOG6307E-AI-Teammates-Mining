# LOG6307E — Repository-Level Review Behaviour for AI Coding Agents

This repository contains our analysis for the LOG6307E mining assignment.

The project builds on the AIDev dataset and studies how code-review behaviour changes as repositories gain experience with AI coding agents. The main idea was inspired by the paper *Habituation at the Gate*, which studies changes in the behaviour of individual reviewers. Our analysis looks at a similar question at the repository level.

## Research Objective

The objective of this study is to investigate whether human review behaviour changes over a repository's history of working with AI coding agents, and whether the same changes are observed for human-authored pull requests.

## Research Questions

**RQ1 — Review Coverage**

How does human review coverage of agent-authored pull requests change from the early to the late stages of a repository's agentic history, compared with human-authored pull requests in the same repositories?

**RQ2 — Approval Behaviour**

Among pull requests that receive human reviews, how does the human approval rate change from the early to the late stages of a repository's agentic history, and does this change differ between agent-authored and human-authored pull requests?

## Data

The main source is the [AIDev dataset](https://huggingface.co/datasets/hao-li/AIDev).

For reproducibility, the analysis uses the following AIDev revision: