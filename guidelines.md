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

We provide four datasets, for  English, Chinese, Japanese, and Korean. The data is hosted in Zenodo and can be downloaded <a href="https://zenodo.org/records/18777084" target="_blank">here</a>. The datasets can also be accessed via <a href="https://github.com/NTCIR-ToT/ir_datasets" target="_blank">an IR-Dataset fork</a> (attention: we have a public fork of ir_datasets that you can use to programmatically access the data). See [Corpora](#corpora) and [Queries](#queries) for a description of the files and additional access information.

### English Subset

The data for the English subset of the task are:

| Description                                   | Link             | # entries| md5sum |
|-----------------------------------------------|------------------|----------|--------|
| corpus (JSONL)                                | [corpus-en.jsonl.gz](https://zenodo.org/records/18777084/files/corpus-en.jsonl.gz) | 6,407,814 | 3229923fdbc4151fc6911085265713f4 |
| train queries                                 | [queries-train-en.jsonl](https://zenodo.org/records/18777084/files/queries-train-en.jsonl)      | 4000 | f9e3c5e5acbaedb28aa112cef6306c12 |
| train qrels                                   | [qrels-train-en.txt](https://zenodo.org/records/18777084/files/qrels-train-en.txt)  | 4000 | bc8c154d45d6e1583d79e20f8305c449 |
| dev queries                     | [queries-dev-en.jsonl](https://zenodo.org/records/18777084/files/queries-dev-en.jsonl)       | 500 | a1e27e3e85b5521cd4ee76f903f594b1 |
| dev qrels                                    | [qrels-dev-en.txt](https://zenodo.org/records/18777084/files/qrels-dev-en.txt)   | 500 | e4cf9ee4e53be21f90f154fc21cbbe20 |


### Chinese Subset

The data for the Chinese subset of the task are:

| Description                                   | Link             | # entries| md5sum |
|-----------------------------------------------|------------------|----------|--------|
| corpus (JSONL)                                | [corpus-zh.jsonl.gz](https://zenodo.org/records/18777084/files/corpus-zh.jsonl.gz) |  1,384,748| 52e7b7c6d5e21a8184bb46966a34b2cf |
| train queries                                 | [queries-train-zh.jsonl](https://zenodo.org/records/18777084/files/queries-train-zh.jsonl)      | 4000 | 060f17e55f36628935100b6256436676 |
| train qrels                                   | [qrels-train-zh.txt](https://zenodo.org/records/18777084/files/qrels-train-zh.txt)  | 4000 | a1bb49385447332cff472817c5509122 |
| dev queries                     | [queries-dev-zh.jsonl](https://zenodo.org/records/18777084/files/queries-dev-zh.jsonl)       | 500 | b94b704344fa6bacb4f68f27431e9b02 |
| dev qrels                                    | [qrels-dev-zh.txt](https://zenodo.org/records/18777084/files/qrels-dev-zh.txt)   | 500 | d6199d8fc49b0c9929d5730a7693b6e2 |

### Japanese Subset

The data for the Chinese subset of the task are:

| Description                                   | Link             | # entries| md5sum |
|-----------------------------------------------|------------------|----------|--------|
| corpus (JSONL)                                | [corpus-ja.jsonl.gz](https://zenodo.org/records/18777084/files/corpus-ja.jsonl.gz) |  1,389,467| f0515675e955641ffd1fcf7c000a2d9f |
| train queries                                 | [queries-train-ja.jsonl](https://zenodo.org/records/18777084/files/queries-train-ja.jsonl)      | 4000 | 2050e5a0102bfe9c9795759c0a72a113 |
| train qrels                                   | [qrels-train-ja.txt](https://zenodo.org/records/18777084/files/qrels-train-ja.txt)  | 4000 | a3d553ca1290f49757d4a61e697503f7 |
| dev queries                     | [queries-dev-ja.jsonl](https://zenodo.org/records/18777084/files/queries-dev-ja.jsonl)       | 500 | ca591070a075c3460f126c06e3aed04d |
| dev qrels                                    | [qrels-dev-ja.txt](https://zenodo.org/records/18777084/files/qrels-dev-ja.txt)   | 500 | 9cd246fd0654cae4aa1acee740dee770 |


### Korean Subset

The data for the Chinese subset of the task are:



## Submission and evaluation

**Submission form:** Coming soon!
(You must <a href="#registration">register as a participant</a> to submit a run).

All submissions should be in the following runfile format. White space is used to separate columns. The width of the columns in the format is not important, but it is important to have exactly six columns per line with at least one space between the columns.

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
