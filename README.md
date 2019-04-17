---
topic: sample
languages:
    - python
products:
    - azure-functions
    - azure-storage
author: priyaananthasankar
---

# Topic Classification using Latent Dirichlet Allocation

[Latent Dirichlet Allocation](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation) (LDA) is a statistical model that classifies a document as a mixture of topics.
The sample uses a HttpTrigger to accept a dataset from a blob and performs the following tasks:
 - Tokenization of the entire set of documents using NLTK
 - Removes stop words and performs lemmatization on the documents using NLTK.
 - Classifies documents into topics using LDA API's from gensim Python library
 - Returns a visualization of topics from the dataset using PyLDAVis Python library

# Getting Started

## Deploy to Azure

### Prerequisites

- Install Python 3.6+
- Install [Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#v2)
- Install Docker

### Steps

- Click Deploy to Azure Button to deploy resources

[![Deploy to Azure](http://azuredeploy.net/deploybutton.png)](https://azuredeploy.net/)

- Run `python3 download.py` to download dataset, tokenizers and stopwords from NLTK. Typically this will get downloaded to $HOME/nltk_data

- Run `deploy.sh` to deploy function code and content to blob containers

- Run `func azure functionapp publish [functionAppName] --build-native-deps` 

## Test

- Send the following body in a HTTP POST request
```
{
    "container_name" : "dataset",
    "num_topics" : "5" 
}
```
- Click the response HTML link to see the following visualization

Inline-style: 
![alt text](https://github.com/Azure-Samples/functions-python-ldamodeling/blob/master/assets/pyldavis.png "PyLDAVis Topic Visualization")

# References

- [Create your first Python Function](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-function-python)
- [Natural Language Toolkit](https://www.nltk.org/)
- [Gensim](https://radimrehurek.com/gensim/)
- [PyLDAVis](https://github.com/bmabey/pyLDAvis)

