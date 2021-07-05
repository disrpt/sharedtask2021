# Persian RST Corpus

This is the first version of the Persian RST corpus, a corpus of 150 journalistic texts annotated in the framework of Rhetorical Structure Theory [1]. The annotation was mainly based on the English RST Discourse Treebank [2] guideline [3]. The relations used in the corpus are the coarse-grained relations introduced in RST Discourse Treebank tagging guideline, which are *Span*, *Joint*, *Elaboration*, *Same*-*Unit*, *Contrast*, *Explanation*, *Attribution*, *Cause*, *Background*, *Evaluation*, *Topic*, *Comment*, *Condition*, *Temporal*, *Summary*, *Enablement*, *Comparison*, *Topic*, *Change*, *Manner*-*Means*. We have annotated the corpus using [rstweb](https://github.com/amir-zeldes/rstWeb) [4] and recommend you use this tool if you want to see RST trees graphically. The name of each document contains the source of the news; e.g. etemad001 was taken from Etemad newspaper. For more information about corpus articles, see [the source repository](https://github.com/hadiveisi/PersianRST), which provides information about the source, date, author and link of each article. This corpus is published under a [CC-BY-NC](https://creativecommons.org/licenses/by-nc/4.0/) license. 

If you find this work useful in your research, please cite: [arxiv.org/abs/2106.13833](https://arxiv.org/abs/2106.13833)


[1] Mann, W. C., & Thompson, S. A. (1987). Rhetorical structure theory: A theory of text organization (pp. 87-190). Los Angeles: University of Southern California, Information Sciences Institute.

[2] Carlson, L., Marcu, D., & Okurowski, M. E. (2003). Building a discourse-tagged corpus in the framework of rhetorical structure theory. In Current and new directions in discourse and dialogue (pp. 85-112). Springer, Dordrecht.

[3] Carlson, L., & Marcu, D. (2001). Discourse tagging reference manual. ISI Technical Report ISI-TR-545, 54(2001), 56.

[4]  Zeldes, A. (2016, June). rstWeb-a browser-based annotation interface for Rhetorical Structure Theory and discourse relations. In Proceedings of the 2016 Conference of the North American Chapter of the Association for Computational Linguistics: Demonstrations (pp. 1-5).

## DISRPT 2021 shared task information

This is the surprise dataset for DISRPT 2021, for which training, development and test data is released during the test period. Tokenization, sentence splits, POS tags, morphology and syntactic parses were added using Stanza's default `fa` model. 

### Notes on segmentation

This dataset contains discontinuous discourse units (split 'same-unit').
