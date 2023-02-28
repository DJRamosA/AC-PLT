# AC-PLT (Automatic Codification of PLT)

This project presents a novel algorithm that uses natural language processing (NLP) techniques to perform content analysis on feature listing data. This model is experimental, here you can appreciate some experiments in 2 datasets in Spanish. 

The model has 3 main steps, data cleaning, word embedding and classification.


## Requirements

This project is using `python==3.10.9`, you can install all the libraries using `pip install -r src\requirements.txt`. Also, the model uses the vectors of the [Spanish-word-embedding](https://github.com/dccuchile/spanish-word-embeddings#word2vec-embeddings-from-sbwc), in specific the Binary format (.bin.gz), after the download add to the `data` folder. (Depending on the language that are you working on, you have to change the embedding).

Now you are ready to go.

## Usages

The main model is in the [Generatir.ipynb](\src\CPN120\Generator.ipynb), the same jupyter notebook has the instructions.
For the training of this model, the dataset has to have 3 rows: `concept`, `feature`, and `code`. In this corresponding order to use in the model.

