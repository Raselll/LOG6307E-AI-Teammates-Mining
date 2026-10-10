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

How does human review coverage of agent-authored pull requests change from the early to the late stages of a repository's agentic history, compared with human-authored pull requests in the same repositories?

### RQ2 — Approval Behaviour

Among formally reviewed pull requests, how does human approval behaviour change from the early to the late stages of a repository's agentic history, and does that change differ between agent-authored and human-authored pull requests?

## Metrics

We use two main metrics.

### Review Coverage

Review Coverage = PRs receiving at least one formal human review / total PRs

This metric measures how frequently pull requests receive direct human review.

### Approval Rate

Approval Rate = approved human review events / total human review events

This metric measures the proportion of formal human review events that result in an approval.

## Data

The main data source is the AIDev dataset:

https://huggingface.co/datasets/hao-li/AIDev

For reproducibility, the analysis uses the following fixed AIDev revision: