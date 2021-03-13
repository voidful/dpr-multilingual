# dpr multilingual

## Description

Multilingual DPR Model base on bert-base-multilingual-cased. 
[DPR model](https://arxiv.org/abs/2004.04906)
[DPR repo](https://github.com/facebookresearch/DPR)

## Data

## Training
Using the script from [haystack](https://colab.research.google.com/github/deepset-ai/haystack/blob/master/tutorials/Tutorial9_DPR_training.ipynb)   
After 25 epoch training:
```
 _________ text_similarity _________
loss: 0.02117470788078296
task_name: text_similarity
acc: 0.9973661232704988
f1: 0.8683130428746214
acc_and_f1: 0.9328395830725601
average_rank: 0.8452053486979686
report:
                precision    recall  f1-score   support

hard_negative     0.9987    0.9987    0.9987  11408455
     positive     0.8683    0.8683    0.8683    115243

     accuracy                         0.9974  11523698
    macro avg     0.9335    0.9335    0.9335  11523698
 weighted avg     0.9974    0.9974    0.9974  11523698
```

## Usage

```python
from transformers import DPRQuestionEncoder, DPRQuestionEncoderTokenizer
tokenizer = DPRQuestionEncoderTokenizer.from_pretrained('voidful/dpr-question_encoder-bert-base-multilingual')
model = DPRQuestionEncoder.from_pretrained('voidful/dpr-question_encoder-bert-base-multilingual')
input_ids = tokenizer("Hello, is my dog cute ?", return_tensors='pt')["input_ids"]
embeddings = model(input_ids).pooler_output
```

Follow the tutorial from `haystack`:
[Better Retrievers via "Dense Passage Retrieval"](https://colab.research.google.com/github/deepset-ai/haystack/blob/master/tutorials/Tutorial6_Better_Retrieval_via_DPR.ipynb)
```
from haystack.retriever.dense import DensePassageRetriever
retriever = DensePassageRetriever(document_store=document_store,
                                  query_embedding_model="voidful/dpr-question_encoder-bert-base-multilingual",
                                  passage_embedding_model="voidful/dpr-ctx_encoder-bert-base-multilingual",
                                  max_seq_len_query=64,
                                  max_seq_len_passage=256,
                                  batch_size=16,
                                  use_gpu=True,
                                  embed_title=True,
                                  use_fast_tokenizers=True)
```
