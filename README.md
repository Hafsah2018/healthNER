# healthNER
This is the code used for the research in our paper "Recurrent neural networks with specialized word embeddings for health-domain named-entity recognition".
It is a little scattered, but fully functioning.

There code contains three main files:

1.__CRF__: This method is the file where we implement the Conditional Random Field (CRF) model which in the paper's results section has the same name (Do not confuse it with the prediction layer of the B-LSTM-CRF). It contains two main files. The HCRF2.0b open-source tool to train a CRF model and a set of files for data_preparation. Further description [here].

2.__Bidirectional_LSTM-CRF__:

3.__Bidirectional_LSTM-CRF_plus_feature_engineering__:

*Due to the large size of the word embedding files, they have not been provided here. CommonCrawl embeddings are available in the oficial GloVe webpage. In order to obtain the specialized embeddings used in the paper, you can contact: _ijauregi@cmcrc.com_.

# CRF:
It includes the data preparation files for the HCRF2.0b software to train a CRF model.

First, we need to create dataTrain.csv, dataTest.csv (using data_CRF_file_creation.py), labelsTrain.csv and 
labelsTest.csv (using tag_CRF_file_creation.py) with the data preparation python code.

Second, we train and test the CRF model with those files (see the HCRF guideline).

Finally, we obtain the results.txt file from the HCRF software. We convert results.txt to a "conlleval" evaluation format 
(data_conll_preparation.py) and evaluate using the conlleval.pl perl file.

# LSTM:
It includes the B-LSTM and the B-LSTM-CRF models with the character embedding and the pre-trained word embeddings.
Run the train.py file to train and test the model. Previously, select all the input and output parameters required.

INPUT:

-train/dev/test files

-pre-embeddings

-char-embedding

-crf final layer (yes or no)

-(the remaining inputs were left to the default values of the original package)

OUTPUT:

-model name

-experiment description file

-test file

-dev file

# LSTM_plus_feature_engineering:
It includes the same model as the LSTM but, in addition, we can select to add conventional feature engineering to the feature vector.
Run the train.py file to train and test the model. Previously, select all the input and output parameters required.

INPUT:

-train_plus_features/dev_plus_features/test_plus_features files (with precomputed features)

-pre-embeddings

-char-embedding

-crf final layer (yes or no)

-conventional feature engineering

-(the remaining inputs were left to the default values of the original package)

OUTPUT:

-model name

-experiment description file

-test file

-dev file



[here]: https://github.com/ijauregiCMCRC/healthNER/tree/master/CRF
