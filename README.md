# Google QUEST QA Labeling

This respository contains my code for competition in kaggle.


16th Place Solution for [Google QUEST QA Labeling](https://www.kaggle.com/c/google-quest-challenge "Google QUEST QA Labeling")

Team: [Abhishek Thakur](https://www.kaggle.com/abhishek), [Duy](https://www.kaggle.com/pvduy23), [Yuval Reina](https://www.kaggle.com/yuval6967), [atfujita](https://www.kaggle.com/atsunorifujita)

All models(Team)    
Public LB: 0.0.47302(7th)   
Private LB: 0.42048(16th)

##### Note: This repository contains only my models and only train script.


My models(5 Model averaging)   
Public LB: 0.94719   
Private LB: 0.94651

Thanks to Abhishek and Duy's wonderful models and support, I was able to get better results.

### Set up
- Particularly important libraries are listed in requirements.txt


### Models
I created 5 models

- LSTM
  - Based on the [Quora competition model](https://github.com/AtsunoriFujita/Quora-Insincere-Questions-Classification)
  - Architecture: LSTM + GRU + Self Attention + Max pooling
  - Word embeddings: concat glove and fasttext.
  - Optimizer: AdamW
  - Train:
    - max_len = 220
    - n_splits = 10
    - batch_size = 512
    - train_epochs = 7
    - base_lr, max_lr = 0.0005, 0.003
    - Weight Decay = 0.0001
    - Learning schedule: CyclicLR


- BERT
  - The model is based on [yuval reina](https://www.kaggle.com/yuval6967)'s graet [kernel](https://www.kaggle.com/yuval6967/toxic-bert-plain-vanila)
  - Changes are loss function and preprocessing.
  - I created 4 BERT models.
    - BERT-Base Uncased
    - BERT-Base Cased
    - BERT-Large Uncased(Whole Word Masking)
    - BERT-Large Cased(Whole Word Masking)
  - Train:
    - max_len = 220
    - train samples = 1.7M, val samples= 0.1M
    - batch_size = 32(Base), 4(Large)
    - accumulation_steps = 1(Base), 16(Large)
    - train_epochs = 2
    - lr = 2e-5

