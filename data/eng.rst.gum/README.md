# eng.rst.gum

The Georgetown University Multilayer (GUM) corpus

To cite this corpus, please refer to the following article:

Zeldes, Amir (2017) "The GUM Corpus: Creating Multilayer Resources in the Classroom". Language Resources and Evaluation 51(3), 581–612.

## Introduction

a corpus of English texts from twelve text types:

Interviews from Wikimedia
News from Wikinews
Travel guides from Wikivoyage
How-to guides from wikiHow
Academic writing from Creative Commons sources
Biographies from Wikipedia
Fiction from Creative Commons sources
Online forum discussions from Reddit
Face-to-face conversations from the Santa Barbara Corpus
Political speeches
OpenStax open access textbooks
YouTube Creative Commons vlogs

The corpus is created as part of the course LING-367 (Computational Corpus Linguistics) at Georgetown University. 

For more details see: https://corpling.uis.georgetown.edu/gum

## DISRPT 2021 shared task information

For the DISRPT 2021 shared task on elementary discourse unit segmentation, only the 11 open text genres are included (to obtain data in the remaining genre, containing Reddit forum discussions which is not included in the shared task, see the corpus website). The data follows the normal division into train, test and dev partitions used for other tasks (e.g. for the conll shared task on UD parsing).  

POS tags and syntactic parses are the UD version of the manually annotated gold data. 

### Notes on segmentation

GUM RST guidelines follow the RST-DT segmentation guidelines for English, according to which most clauses, including adnominal and nested clauses are discourse units. This dataset contains discontinuous discourse units (split 'same-unit').
