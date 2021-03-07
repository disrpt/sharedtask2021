# DISRPT/sharedtask2021

Repository for DISRPT2021 shared task Discourse Unit Segmentation, Connective Detection and Discourse Relation Classification.

**Important:** The data in this repository is currently still in development and is likely to change before being finalized. It should only be used as a sample of the data formats used in the shared task. Stable training and development data will be released in May 2021, and test data will be released in July 2021.

## Introduction

The [DISRPT 2021](https://sites.google.com/georgetown.edu/disrpt2021) shared task, co-located with [CODI 2021](https://sites.google.com/view/codi-2021/) at [EMNLP](https://2021.emnlp.org/), introduces the second iteration of a cross-formalism shared task on **discourse unit segmentation** and **connective detection**, as well as the first iteration of a cross-formalism **discourse relation classification** task. 

We provide training, development and test datasets from all available languages and treebanks in the RST, SDRT and PDTB formalisms, using a uniform format. Because different corpora, languages and frameworks use different guidelines, the shared task is meant to promote design of flexible methods for dealing with various guidelines, and help to push forward the discussion of standards for computational approaches to discourse relations. We include data for evaluation with and without gold syntax, or otherwise using provided automatic parses for comparison to gold syntax data.

https://sites.google.com/georgetown.edu/disrpt2021

**Shared task participants are encouraged to follow this repository in case bugs are found and need to be fixed** 

## Types of data

The tasks are oriented towards finding the locus and type of discourse relations in texts, rather than predicting complete trees or graphs. For frameworks that segment text into non-overlapping spans covering each entire documents (RST and SDRT), the segmentation task corresponds to finding the starting point of each discourse unit. For PDTB-style datasets, the unit-identification task is to identify the spans of discourse connectives that explicitly identify the existence of a discourse relation. These tasks use the files ending in **.tok** and **.conllu** for the plain text and parsed scenarios respectively.

For relation classification, two discourse unit spans are given in text order together with the direction of the relation and context, using both plain text data and stand-off token index pointers to the treebanked files. Information is included for each corpus in the **.rels** file, with token indices pointing to the **.tok** file, though parse information may also be used for the task. External resources are allowed, including NLP tools, word embeddings/pre-trained language models, and **other** gold datasets for MTL etc. However, no further gold annotations of the datasets included in the task may be used (example: you may not use OntoNotes coref to pretrain a system that will be tested on WSJ data from RST-DT or PDTB, since this could contaminate the evaluation; exception: you may do this if you exclude WSJ data from OntoNotes during training).

Note that some datasets contain **discontinuous** discourse units, which sometimes nest the second unit in a discourse relation. In such cases, the unit beginning first in the text is considered `unit1` and gaps in the discourse unit are given as `<*>` in the inline text representation. Token index spans point to the exact coverage of the unit either way, which in case of discontinuous units will contain multiple token spans.

## Submitting a system

Systems should be accompanied by a regular workshop paper in the ACL format, as described on the CODI workshop website. During submission, you will be asked to supply a URL from which your system can be downloaded. If your system does not download necessary resources by itself (e.g. word embeddings), these resources should be included at the download URL. The system download should include a README file describing exactly how paper results can be reproduced. Please do not supply pre-trained models, but rather instructions on how to train the system using the downloaded resources and **make sure to seed your model** to rule out random variation in results. For any questions regarding system submissions, please contact the organizers.

## Important dates

  * Mon, March 1, 2021 - shared task sample data release
  * May, 2021 - training data release
  * July, 2021 - test data release
  * August, 2021 - papers due
  * September, 2021 - notification of acceptance
  * October, 2021 - camera-ready papers due
  * November, 2021 - CODI workshop

## Directories

The shared task repository currently comprises the following directories (to be extended as the task progresses):

  * data - individual corpora from various languages and frameworks. 
    * Folders are given names in the scheme `LANG.FRAMEWORK.CORPUS`, e.g. `eng.rst.gum` is the directory for the GUM corpus, which is in English and annotated in the framework of Rhetorical Structure Theory (RST).
    * Note that some corpora (eng.rst.rstdt, eng.pdtb.pdtb, tur.pdtb.tdb, zho.pdtb.cdtb) **do not contain text** and text therefore needs to be reconstructed using `utils/process_underscores.py`.
  * utils - scripts for validating, evaluating and generating data formats. The official scorer for segmentation and connective detection is `seg_eval.py`.

See the README files in individual data directories for more details on each dataset.

