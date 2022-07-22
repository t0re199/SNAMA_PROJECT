# README #

This repository hosts a **Sentiment Analysis** on an amazon english reviews dataset using various transformers from [Hugging Face](https://huggingface.co/).   
**PyTorch** has been used as Gradient Computing Library.   

## Used Transformers ##

* [Bert](https://huggingface.co/bert-base-uncased)
* [AlBert](https://huggingface.co/albert-base-v2)
* [RoBerta](https://huggingface.co/roberta-base)
* [XlNet](https://huggingface.co/xlnet-base-cased)
* [Electra](https://huggingface.co/docs/transformers/model_doc/electra)


## Transformerms Pre-Processing ##

### String Manipulation ###

For each record:   
   
* Removed html tags    
* Case folding       

## Multi-Layer Perceptron Pre-Processing ##

### String Manipulation ###

For each record:   
   
* Removed html tags   
* Removed non-alpha strings   
* Removed single characters    
* Case folding      

### Stopwords ####
Stopwords have been removed. The [nltk](https://www.nltk.org/) english stopwords set has been used.

### Lemmatization ###

It was used to reduce the number of tokens since each word is converted to its base form.   
The **WordNetLemmatizer** from nltk has been used.  

### Optimization ###

Preprocessing is done in parallel.    

## Retrieved Information ##

* **No. Records**: 191486   
* **Corpus Size**: 59692   
* **Min Sequence Length**: 5      
* **Max Sequence Length**: 14004   

## Labels ##
Sentiment polarity: 

* 0: Bad
* 1: Neutral
* 2: Positive   

## Transformers Training ##

Pre-trained models has been used for extracting features from text (no fine tuning).   
A classifier has been trained for obtaining predictions from the extracted features.  
Each classifier has been trained for 150 epochs.   
70% of the dataset has been used as **training set** while the other 30% as **test set**.   

### Standard Training ###

The **CrossEntropy** loss function has been used.   
**Adam** was used as optimezer.   

### Weighted Loss Training ###

Since the dataset is imbalanced, it was tried to mitigate this aspect by using a weighed loss function. In particular the **Inverse Number of Samples** (INS) weighting strategy was employed.   
INS weights has been used in the **CrossEntropy** loss function.   
**Adam** was used as optimezer.   
