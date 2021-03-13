# dpr multilingual data

## data statistic
`question pairs for train`： 719,378
`question pairs for dev`： 115,243

## Data source
1. [NQ](https://github.com/facebookresearch/DPR/blob/master/data/download_data.py)
2. [Trivia](https://github.com/facebookresearch/DPR/blob/master/data/download_data.py)
3. [SQuAD](https://github.com/facebookresearch/DPR/blob/master/data/download_data.py)
4. [DRCD*](https://github.com/DRCKnowledgeTeam/DRCD)
5. [MLQA*](https://github.com/facebookresearch/MLQA)
6. [ComplexQuestions*](https://github.com/alontalmor/MultiQA)
7. [DuoRC*](https://github.com/alontalmor/MultiQA)
8. [HotpotQA*](https://github.com/alontalmor/MultiQA)
9. [WikiHop*](https://github.com/alontalmor/MultiQA)
10. [ComplexWebQuestions*](https://github.com/alontalmor/MultiQA)
11. [ComQA*](https://github.com/alontalmor/MultiQA)

## Description
Here will describe How data will be processed for DPR training/evaluation.  
We will have 3 kind of data cauterize by their format, all the data format will be converted from the top to the bottom:  
- SQuAD format: DRCD, MLQA, ComplexQuestions, DuoRC, HotpotQA, WikiHop, ComplexWebQuestions, ComQA
- DPR original format: NQ, Trivia, SQuAD
- DPR jsonl format

Convert SQuAD to DPR original format: [squad_to_dpr.py](https://github.com/deepset-ai/haystack/blob/master/haystack/retriever/squad_to_dpr.py)
