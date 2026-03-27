---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---

# NTCIR 2026 Tip-of-the-Tongue (ToT) Shared Task

Welcome to the guidelines for the upcoming 2026 edition of the NTCIR ToT shared task!

# Guidelines

## Important dates
* **February:** March 27
* **May (tentative):** Release test queries
* **June 1st:** Deadline for registration
* **July (tentative):** Deadline for submitting runs

## Registration

Organizations wishing to participate in NTCIR 2026 must <a href="https://research.nii.ac.jp/ntcir/ntcir-19/howto.html" target="_blank">register</a>.

Any questions about task registration must be sent to ntc-secretariat (at) nii.ac.jp.
Task specific enquiries must be directed to ntcir-tot-organizers (at) googlegroups.com.

## Task definition

In terms of input and output, the ToT known-item identification task is relatively straightforward—given an input ToT request, output a ranked list of items.
So, each item can be any entity and must be identified by its Wikipedia page id and the correct item should be ranked as high as possible.
For each query, runs should return a ranked list of 1000 Wikipedia page ids.
Runs will be evaluated using IR metrics that are appropriate for IR tasks with one relevant document, such as discounted cumulative gain, reciprocal rank, and success@k.

The retrieval task is multilingual.
Separate datasets will be provided to participants in English, Chinese, Japanese, and Korean.
Participants can submit runs for one or more languages.

### Corpora

For each of our four languages, we use Wikipedia (in the corresponding language) as corpus. Each document in the corpus will be described by the following fields:

- **doc_id**: the primary identifier, the Wikipedia page ID.
- **url**: the wikipedia page URL.
- **title**: wikipedia page title.
- **text**: (full) text of the wikipedia page.

An example document is described below.

#### Example Document

```json

{
  "id": "846",
  "url": "https://en.wikipedia.org/wiki/Museum%20of%20Work",
  "title": "Museum of Work",
  "text": "The Museum of Work (Arbetets museum) is a museum ..."
}

```

This year, the corpus is also available via our <a href="github.com/NTCIR-ToT/ir_datasets" target="_blank">IR-Dataset Fork</a>.

#### Access corpora through IR-Datasets

Please install the ir_datasets datasets from our <a href="github.com/NTCIR-ToT/ir_datasets">fork</a>, and then run the following sample code.

```python
import ir_datasets
# the pattern is ntcir-tot/2026/<LANGUAGE>/<SPLIT>
# <LANGUAGE> is either en, zh, ja, or ko
# <SPLIT> is either train, dev, or test
dataset = ir_datasets.load("ntcir-tot/2026/en/train")

for query in dataset.queries_iter():
    print(query)
    break

for doc in dataset.docs_iter():
    print(doc.doc_id)
    break
```

### Queries

Participating groups will be given a JSONL file (or can access the queries via our ir_datasets fork described above) consisting of a random sample of queries each for training, development, and test. The query format for this year has two fields: **query_id** and **query**. An example query is described below.

```json
{
  "query_id": "763",
  "query": "Super Rare Surreal Dystopian Masterpiece .\n Very rare movie that is scifi/dystopian/experimental/surreal. It\u2019s like Stalker meets el Topo meets Holy Mountain meets Alphaville meets Delicatessen meets Hard to be a God, like Kurosawa, Tarkovsky, and Lynch had a kid together. It was color, possibly Russian, and I don\u2019t really remember the decade but want to say 60s or 70s, though could easily be more recent. It is VERY rare, there is only one crappy partial print of it, and that is what the youtube version is from. Lot of wide shots in a surreal wilderness, winter settings, strange bleeding saturation in some shots. Crazy costumes. Seriously one of the strangest films I\u2019ve ever seen and my favorite films are strange/weird ones. If you\u2019ve ever seen what you\u2019re thinking of on a \u201cbest weird movies\u201d or \u201cyou\u2019ve never seen this!\u201d list, that\u2019s NOT it. I don\u2019t think this film even has a cult following of ten people. It\u2019s an actual rare gem. Have been looking through selections at 366 Weird Movies and not found it yet (btw the way most of those titles are exactly the kind of not-actually-rare movies this film is definitely not)."
}

```

## Datasets

We provide four datasets, for  English, Chinese, Japanese, and Korean. The data is hosted in Zenodo and can be downloaded <a href="https://zenodo.org/records/18777084" target="_blank">here</a>. The datasets can also be accessed via <a href="https://github.com/NTCIR-ToT/ir_datasets" target="_blank">an IR-Dataset fork</a> (attention: we have a public fork of ir_datasets that you can use to programmatically access the data). See [Corpora](#corpora) and [Queries](#queries) for a description of the files and additional access information.


**Test queries:** Coming soon! (the corpus will be the same, you can already develop your system with the training and dev queries/qrels.)

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

The data for the Japanese subset of the task are:

| Description                                   | Link             | # entries| md5sum |
|-----------------------------------------------|------------------|----------|--------|
| corpus (JSONL)                                | [corpus-ja.jsonl.gz](https://zenodo.org/records/18777084/files/corpus-ja.jsonl.gz) |  1,389,467| f0515675e955641ffd1fcf7c000a2d9f |
| train queries                                 | [queries-train-ja.jsonl](https://zenodo.org/records/18777084/files/queries-train-ja.jsonl)      | 4000 | 2050e5a0102bfe9c9795759c0a72a113 |
| train qrels                                   | [qrels-train-ja.txt](https://zenodo.org/records/18777084/files/qrels-train-ja.txt)  | 4000 | a3d553ca1290f49757d4a61e697503f7 |
| dev queries                     | [queries-dev-ja.jsonl](https://zenodo.org/records/18777084/files/queries-dev-ja.jsonl)       | 500 | ca591070a075c3460f126c06e3aed04d |
| dev qrels                                    | [qrels-dev-ja.txt](https://zenodo.org/records/18777084/files/qrels-dev-ja.txt)   | 500 | 9cd246fd0654cae4aa1acee740dee770 |


### Korean Subset

The data for the Korean subset of the task are:

| Description                                   | Link             | # entries| md5sum |
|-----------------------------------------------|------------------|----------|--------|
| corpus (JSONL)                                | [corpus-ko.jsonl.gz](https://zenodo.org/records/18777084/files/corpus-ko.jsonl.gz) | 647,897 | b8007b99a5b9730677cbfa4ce32389e0 |
| train queries                                 | [queries-train-ko.jsonl](https://zenodo.org/records/18777084/files/queries-train-ko.jsonl)      | 4000 | 60e177bb7163a70ba7be3605389acdcb |
| train qrels                                   | [qrels-train-ko.txt](https://zenodo.org/records/18777084/files/qrels-train-ko.txt)  | 4000 | 46cc66a66aad9ce41c9285a47e49732f |
| dev queries                     | [queries-dev-ko.jsonl](https://zenodo.org/records/18777084/files/queries-dev-ko.jsonl)       | 500 | fa5d243756d253ac1b980ad9442f4c5e |
| dev qrels                                    | [qrels-dev-ko.txt](https://zenodo.org/records/18777084/files/qrels-dev-ko.txt)   | 500 | ead40835c0b461e433948834dd27516b |

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
