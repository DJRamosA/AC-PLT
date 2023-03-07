# AC-PLT (Automatic Codification of PLT)

This project presents a novel algorithm that uses natural language processing (NLP) techniques to perform content analysis on feature listing data. This model is experimental, here you can appreciate some experiments in 2 datasets in Spanish. Also, there is the option to use it in English.

The model has 3 main steps, data cleaning, word embedding and classification.


## Requirements

This project is using `python==3.10.9`, you can install all the libraries using `pip install -r src\requirements.txt`. Also, the model uses the vectors of the [Spanish-word-embedding](https://github.com/dccuchile/spanish-word-embeddings#word2vec-embeddings-from-sbwc), in specific the Binary format (.bin.gz), after the download add to the `data` folder. (Depending on the language that are you working on, you have to change the embedding, for English use the [word2vec-google-news-300](https://huggingface.co/fse/word2vec-google-news-300/tree/main)).

Now you are ready to go.

## Usages

The main model is in the [CA_PLT.ipynb](\src\CA_PLT.ipynb), the same jupyter notebook has the instructions. To use this model the dataset has to have 3 columns: `concept`, `feature`, and `codification`. In this corresponding order to use in the model.

In the section of **Set of the Language**, there is a section where you can choose the language of your preference (if you download the word2vec specified in [Requirements](##Requirements)).

In the next section, **Important functions** there is the basic function `clean_text()`, which you have to combine with either `normalize()` or `lematize()` depending on your needs in the **Data Cleaning** part.

For the **Word Embedding** section, there are a few changes you have to make in the matrix filling, you have to change the column name to the name in your dataset. In the reduction of the matrix part, have to change the order of the dataset, first 300 columns are the *vector value*, then the *Concept*, *Codification* and *Description* in that exact order.


In **Model**, there is the main algorithm ``CA_PLT()``, where the only parameter is `n_clusters` the number of clusters of the *k*-Means algorithm. The important functions are:
- ``fit()``: receives the training dataset and trains the k-means algorithm.
- ``transform()``: receives the test dataset, and returns a matrix with the top-1 to top-*k* accuracy of the model.

The Following sections **Experiments** and **Search of hyperparameter *k***, if the previous steps are correct you can see the results of the model for your dataset.

