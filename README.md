# DISRPT/sharedtask2021

Repository for DISRPT2021 shared task Discourse Unit Segmentation, Connective Detection and Discourse Relation Classification.

**Please check our [FAQ](https://sites.google.com/georgetown.edu/disrpt2021/faq?authuser=0) page on our main [website](
https://sites.google.com/georgetown.edu/disrpt2021) for more information about the Shared Task, Participation, and Evaluation etc.!**

**Important update:** Stable training and development data ~~will be~~ was released in May 2021, and test data ~~will be~~ was released in July 2021.

**Shared task participants are encouraged to follow this repository in case bugs are found and need to be fixed.** 


## Introduction

The [DISRPT 2021](https://sites.google.com/georgetown.edu/disrpt2021) shared task, co-located with [CODI 2021](https://sites.google.com/view/codi-2021/) at [EMNLP](https://2021.emnlp.org/), introduces the second iteration of a cross-formalism shared task on **discourse unit segmentation** and **connective detection**, as well as the first iteration of a cross-formalism **discourse relation classification** task. 

We provide training, development and test datasets from all available languages and treebanks in the RST, SDRT and PDTB formalisms, using a uniform format. Because different corpora, languages and frameworks use different guidelines, the shared task is meant to promote design of flexible methods for dealing with various guidelines, and help to push forward the discussion of standards for computational approaches to discourse relations. We include data for evaluation with and without gold syntax, or otherwise using provided automatic parses for comparison to gold syntax data.

## Types of Data

The tasks are oriented towards finding the locus and type of discourse relations in texts, rather than predicting complete trees or graphs. For frameworks that segment text into non-overlapping spans covering each entire documents (RST and SDRT), the segmentation task corresponds to finding the starting point of each discourse unit. For PDTB-style datasets, the unit-identification task is to identify the spans of discourse connectives that explicitly identify the existence of a discourse relation. These tasks use the files ending in **.tok** and **.conllu** for the plain text and parsed scenarios respectively.

For relation classification, two discourse unit spans are given in text order together with the direction of the relation and context, using both plain text data and stand-off token index pointers to the treebanked files. Information is included for each corpus in the **.rels** file, with token indices pointing to the **.tok** file, though parse information may also be used for the task. The column to be predicted is the final label column; the penultimate `orig_label` column gives the original label from the source corpus, which may be different, for reference purposes only. This column may not be used. The relation direction column may be used for prediction and does not need to be predicted by systems (essentially, systems are labeling a kind of ready, unlabeled but directed dependency graph).

External resources are allowed, including NLP tools, word embeddings/pre-trained language models, and **other** gold datasets for MTL etc. However, no further gold annotations of the datasets included in the task may be used (example: you may not use OntoNotes coref to pretrain a system that will be tested on WSJ data from RST-DT or PDTB, since this could contaminate the evaluation; exception: you may do this if you exclude WSJ data from OntoNotes during training).

Note that some datasets contain **discontinuous** discourse units, which sometimes nest the second unit in a discourse relation. In such cases, the unit beginning first in the text is considered `unit1` and gaps in the discourse unit are given as `<*>` in the inline text representation. Token index spans point to the exact coverage of the unit either way, which in case of discontinuous units will contain multiple token spans.

## Submitting a System

Systems should be accompanied by a regular workshop paper in the ACL format, as described on the CODI workshop website. During submission, you will be asked to supply a URL from which your system can be downloaded. If your system does not download necessary resources by itself (e.g. word embeddings), these resources should be included at the download URL. The system download should include a README file describing exactly how paper results can be reproduced. Please do not supply pre-trained models, but rather instructions on how to train the system using the downloaded resources and **make sure to seed your model** to rule out random variation in results. For any questions regarding system submissions, please contact the organizers.

## Important Dates

  * ~~Mon, March 1, 2021 - shared task sample data release~~
  * ~~May, 2021 - training data release~~
  * ~~July, 2021 - test data release~~
  * August, 2021 - papers due
  * September, 2021 - notification of acceptance
  * October, 2021 - camera-ready papers due
  * November, 2021 - CODI workshop

## Directories

The shared task repository currently comprises the following directories (to be extended as the task progresses):

  * data - individual corpora from various languages and frameworks. 
    * Folders are given names in the scheme `LANG.FRAMEWORK.CORPUS`, e.g. `eng.rst.gum` is the directory for the GUM corpus, which is in English and annotated in the framework of Rhetorical Structure Theory (RST).
    * Note that some corpora (eng.rst.rstdt, eng.pdtb.pdtb, tur.pdtb.tdb, zho.pdtb.cdtb) **do not contain text** or have some documents without text (eng.rst.gum) and text therefore needs to be reconstructed using `utils/process_underscores.py`.
  * utils - scripts for validating, evaluating and generating data formats. The official scorer for segmentation and connective detection is `seg_eval.py`, and the official scorer for relation classification is `rel_eval.py`.

See the README files in individual data directories for more details on each dataset.

## Surprise language

At the release of the test data, a surprise language dataset was added: Persian RST data from the Persian RST Corpus (PRSTC). 

## Statistics

| corpus | lang | framework | rels | rel_types | discont | train_toks | train_sents | train_docs | dev_toks | dev_sents | dev_docs | test_toks | test_sents | test_docs | total_sents | total_toks | total_docs | seg_style | underscored | syntax | MWTs | ellip |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| deu.rst.pcc | deu | rst | 2,164 | 26 | no | 26,831 | 1,773 | 142 | 3,152 | 207 | 17 | 3,239 | 213 | 17 | 2,193 | 33,222 | 176 | EDU | no | UD | no | no |
| eng.pdtb.pdtb | eng | pdtb | 43,920 | 23 | yes | 1,061,229 | 44,563 | 1,992 | 39,768 | 1,703 | 79 | 55,660 | 2,364 | 91 | 48,630 | 1,156,657 | 2,162 | Conn | yes | UD (gold) | no | no |
| eng.rst.gum | eng | rst | 13,897 | 23 | yes | 116,557 | 6,346 | 128 | 18,172 | 947 | 20 | 18,127 | 999 | 20 | 8,292 | 152,856 | 168 | EDU | no | UD (gold) | yes | yes |
| eng.rst.rstdt | eng | rst | 16,002 | 17 | yes | 166,854 | 6,672 | 309 | 17,309 | 717 | 38 | 21,666 | 929 | 38 | 8,318 | 205,829 | 385 | EDU | yes | UD (gold) | no | no |
| eng.sdrt.stac | eng | sdrt | 9,580 | 16 | no | 41,060 | 8,754 | 33 | 4,747 | 991 | 6 | 6,547 | 1,342 | 6 | 11,087 | 52,354 | 45 | EDU | no | UD | no | no |
| eus.rst.ert | eus | rst | 2,533 | 29 | yes | 30,690 | 1,599 | 116 | 7,219 | 366 | 24 | 7,871 | 415 | 24 | 2,380 | 45,780 | 164 | EDU | no | UD | no | no |
| fas.rst.prstc | fas | rst | 4,100 | 17 | yes | 52,497 | 1,713 | 120 | 7,033 | 202 | 15 | 7,396 | 264 | 15 | 2,179 | 66,926 | 150 | EDU | no | UD | yes | no |
| fra.sdrt.annodis | fra | sdrt | 2,185 | 18 | yes | 22,515 | 1,020 | 64 | 5,013 | 245 | 11 | 5,171 | 242 | 11 | 1,507 | 32,699 | 86 | EDU | no | UD | no | no |
| nld.rst.nldt | nld | rst | 1,608 | 32 | no | 17,562 | 1,156 | 56 | 3,783 | 255 | 12 | 3,553 | 240 | 12 | 1,651 | 24,898 | 80 | EDU | no | UD | no | no |
| por.rst.cstn | por | rst | 4,148 | 32 | yes | 52,177 | 1,825 | 114 | 7,023 | 257 | 14 | 4,132 | 139 | 12 | 2,221 | 63,332 | 140 | EDU | no | UD | yes | no |
| rus.rst.rrt | rus | rst | 28,868 | 22 | yes | 390,375 | 18,932 | 272 | 40,779 | 2,025 | 30 | 41,851 | 2,087 | 30 | 23,044 | 473,005 | 332 | EDU | no | UD | no | no |
| spa.rst.rststb | spa | rst | 2,240 | 28 | yes | 43,055 | 1,548 | 203 | 7,551 | 254 | 32 | 8,111 | 287 | 32 | 2,089 | 58,717 | 267 | EDU | no | UD | no | no |
| spa.rst.sctb | spa | rst | 439 | 24 | yes | 10,253 | 326 | 32 | 2,448 | 76 | 9 | 3,814 | 114 | 9 | 516 | 16,515 | 50 | EDU | no | UD | no | no |
| tur.pdtb.tdb | tur | pdtb | 2,451 | 23 | yes | 398,515 | 24,960 | 159 | 49,952 | 2,948 | 19 | 47,891 | 3,289 | 19 | 31,197 | 496,358 | 197 | Conn | yes | UD | yes | no |
| zho.pdtb.cdtb | zho | pdtb | 3,657 | 9 | yes | 52,061 | 2,049 | 125 | 11,178 | 438 | 21 | 10,075 | 404 | 18 | 2,891 | 73,314 | 164 | Conn | yes | other (gold) | no | no |
| zho.rst.sctb | zho | rst | 439 | 26 | yes | 9,655 | 361 | 32 | 2,264 | 86 | 9 | 3,577 | 133 | 9 | 580 | 15,496 | 50 | EDU | no | UD | no | no |

*Legend*

  * corpus - unique corpus identifier, consisting of the language code, framework acronym and an abbreviation for the corpus name
  * lang - ISO 639-3, 3 letter language code
  * framework - one of pdtb (Penn Discourse Treebank framework), rst (Rhetorical Structure Theory) or sdrt (Segmented Discourse Representation Theory)
  * rels - number of discourse relation instances (note that for tur.pdtb.tdb, only a subset of the data annotated for connectives also has discourse relation types, so there are much fewer relation instances and documents than connectives)
  * rel_types - number of distinct relation types targeted in the shared task 'label' column. Note that for some corpora, these were collapsed from a larger inventory, but the original uncollapsed relation labels are retained in the column orig_label
  * discont - whether the relation classification dataset contains discontinuous discourse units. Note that for segmentation, each part of a discontinous unit constitutes its own segment, so these datasets only differ overtly in the .rels file, where gaps are indicated by `<*>`.
  * underscored - whether all text is contained in the data (`no`), all text needs to be retrieved using the `process_underscores.py` script (`yes`), or part of the text needs to be retrieved by the same script (`part`)
  * syntax - type of syntax trees: automatic Universal Dependencies (UD) or other, and gold standard (manual or converted from manual annotation) or not (automatic). See individual corpus README files for more details.
  * MWTs - whether the corpus uses CoNLL-U Multiword Tokens with hyphens in IDs for complex word forms (e.g. `1-2 don't ... 1 do ... 2 n't`)
  * ellip - whether the corpus uses CoNLL-U ellipsis tokens (a.k.a. null or empty tokens) with decimal IDs (e.g. `8.1`) to reconstruct ellipsis phenomena. Note that such tokens only appear in `.conllu` files, since they are not actually part of the text; they are never the location of a discourse unit segmentation point and are omitted in .tok and .rels files, and they are not counted in the token offsets in .rels files.
