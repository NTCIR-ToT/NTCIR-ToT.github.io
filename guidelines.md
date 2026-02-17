---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# NTCIR 2026 Tip-of-the-Tongue (ToT) Shared Task

Welcome to the guidelines for the upcoming 2026 edition of the NTCIR ToT shared task!

# Guidelines

## Important dates
* **February:** Release corpus and training queries
* **May:** Release test queries
* **June 1st:** Deadline for registration
* **July:** Deadline for submitting runs

## Registration

Organizations wishing to participate in NTCIR 2026 must <a href="https://research.nii.ac.jp/ntcir/ntcir-19/howto.html" target="_blank">register</a>.

Any questions about task registration must be sent to ntc-secretariat (at) nii.ac.jp.
Task specific enquiries must be directed to diazf (at) acm.org.

## Task definition

In terms of input and output, the ToT known-item identification task is relatively straightforward—given an input ToT request, output a ranked list of items.
So, each item can be any entity and must be identified by its Wikipedia page id and the correct item should be ranked as high as possible.
For each query, runs should return a ranked list of 1000 Wikipedia page ids.
Runs will be evaluated using IR metrics that are appropriate for IR tasks with one relevant document, such as discounted cumulative gain, reciprocal rank, and success@k.

The retrieval task is multilingual.
Separate datasets will be provided to participants in English, Chinese, Japanese, and Korean.
Participants can submit runs for one or more languages.

## Datasets
(Coming soon!)

## Submission and evaluation

**Submission form:** Coming soon!
(You must <a href="#registration">register as a participant</a> to submit a run).

We will be following the TREC submissions format, which is repeated below. White space is used to separate columns. The width of the columns in the format is not important, but it is important to have exactly six columns per line with at least one space between the columns.

```text
1 Q0 pid1    1 2.73 runid1
1 Q0 pid2    2 2.71 runid1
1 Q0 pid3    3 2.61 runid1
1 Q0 pid4    4 2.05 runid1
1 Q0 pid5    5 1.89 runid1
```

, where:

* The first column is the query (topic) ID.
* The second column is currently unused and should always be "Q0".
* The third column is the official identifier of the retrieved document.
* The fourth column is the rank the document is retrieved.
* The fifth column is the score (integer or floating point) that generated the ranking. This score must be in descending (non-increasing) order.
* The sixth column is the ID of the run you are submitting.

Runs will be evaluated using metrics appropriate for retrieval scenarios with one relevant document. In particular, **our primary evaluation metric for this year's track will be discounted cumulative gain (DCG)** but we may also compute other metrics such as reciprocal rank (RR) and success@k.
