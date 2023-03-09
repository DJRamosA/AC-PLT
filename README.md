# AC-PLT (Automatic Codification of PLT)

This project presents a novel algorithm that uses natural language processing (NLP) techniques to perform content analysis on feature listing data. This model is experimental, here you can appreciate some experiments in 2 datasets in Spanish. Also, there is the option to use it in English.

The model has 3 main steps, data cleaning, word embedding, and classification.


## Requirements

This project runs under `python==3.10.9`. You can install all the libraries using `pip install -r src\requirements.txt`. The original code uses the vectors of the [Spanish-word-embedding](https://github.com/dccuchile/spanish-word-embeddings#word2vec-embeddings-from-sbwc) (specifically the Binary format .bin.gz). After you download the file, add it to the data folder. In the case of an English dataset, you can use the [word2vec-google-news-300](https://huggingface.co/fse/word2vec-google-news-300/tree/main). However, this has not been tested yet.

## Usages

### Suggestion 
The jupyter notebook file [AC_PLT.ipynb](/src/AC_PLT.ipynb) has the main code and the corresponding instructions. To use this model the dataset needs to be in a csv file with the three following columns: `concept`, `feature`, and `codification` (please keep the order of the columns, but the names of the head columns are not important). 

In the **Important Variables** section, there are the main variables for the model, modify depending on your necessities, those are:
- `pathTrainData`: The file for the training dataset.
- `pathData`: The path of the data to apply the AC_PLT.
- `numberCluster`: The number of clusters you want.
- `numberCodes`: The number of suggested codes for your data.
- `outputFile`: The path to save the result of the dataframe.

The section **Setting the Language** can manage Spanish and English. For other languages, please modify the code at your own risk.

The section **Important functions** implement the function for **Data Cleaning** section. 

The **Word Embedding** section applies the embedding process based on the selected embeddings. The final In the reduction of the matrix part, have to change the order of the dataset, first 300 columns are the *vector value*, then the *Concept*, *Description*, and *Codification* in that exact order. In the case of the data to codify, we should not have the *Codification* column.


In **Model**, there is the main algorithm ``AC_PLT()``, where the only parameter is `n_clusters` the number of clusters of the *k*-Means algorithm. The important functions are:
- ``fit()``: receives the training dataset and trains the k-means algorithm with n_clusters clusters.
- ``transform()``: receives the test dataset, and returns a matrix with the top-1 to top-*p* accuracy of the model.
- ``suggestions()``: Receives the data to codify and the number of suggestions defined in the variable section. It returns a data frame with the number of suggestions required.

Finally, the **Codification Suggested** section is the process to create a CSV with all the suggested codifications by the AC-PLT model, which is saved in the defined path.

### Replicant

The file [Replication.ipynb](/src/Replication.ipynb) has the experimentation of the model applied in the *CPN 2*7 and *CPN 120*. This code allows you to calculate the p-top accuracy when this model is used on a single CSV file. It does not generate the codification in a CSV file. Two new sections were added **Experiments** and **Search of hyperparameter *k***. If run properly, you can replicate the results of the paper using the original datasets.

