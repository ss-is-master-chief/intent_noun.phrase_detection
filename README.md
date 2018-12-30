# Intent Detection and Noun-Phrase Detection

## Google Colab Notebook :notebook_with_decorative_cover: 

[Intent Detection and Noun-Phrase Detection Notebook](https://colab.research.google.com/drive/17aeRSr-Phz0bx_DczACfArYOsD-84u97) 

## Dataset
* Training Data: `./dataset/train.txt`
* Testing Data: `./dataset/test.txt`

## Models Trained

* Find trained models in: `./models`

| S.No. |  Model Name (if saved) | Runtime | Epochs | Accuracy |
|---|---|---|---|---|
| 1 | model | CPU | 18 | 81.25 % |
| 2 | model_GPU_acc_80.54 | GPU | 18 | 80.54 % |
| 3 | not saved | GPU |  20 | 77.72 % |

## The Notebook

### 1. Cleaning the data

The `clean_data()` method reads the `file_name` passed onto it and does the following to each line of text
* Split the decision - `Yes` or `No` by `\t` within a sentence and the lines by `\n`
* Converts the contents to lower case
* Expands contractions, e.g. converts `you've` to `you have`
* Removes hyperlinks since they can be arbitrary which might throw our model off track
* Removes email addresses 
* Removes numbers
* Removes punctuations
* Assigns integer value of `1` to `yes` and `0` to `no` for classification purposes
* Extracts noun-phrases from the file

### 2. Generating Word Embeddings using FastText

* Training word embeddings from a training corpus 
* Additional ability to obtain word vectors for out-of-vocabulary words.

### 3. Establishing the Neural Network

* Establishing a neural-network
* Experimentation led to 18 epochs
* Avoiding over-fitting and under-fitting

### 4. Loading the model to run to test dataset

### 5. Noun-Phrase Detection

#### Algorithm:
* stop_words <- list of english stopwords
* punctuations <- list of all punctuations
* noun_phrase <- empty_list
* remove digits
* tokenize sentence
* np <- empty string
* if word not in combined list of punctuations and stop_words, add as noun-phrase to `np` with space
* if word in combined list
    * if `np` is not empty, add phrase to `noun_phrase`
    * np <- empty list
