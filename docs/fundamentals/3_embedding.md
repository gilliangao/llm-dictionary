Embedding is a high-dimensional represenatation of text. 
Embedding = turning text into numbers that capture meaning

From 2_tokenization, there are numbers/tokens to feed to the model. Therefore, vectors are used to make these numbers meaningful. 

*TF-IDF
    Term Frequency - Inverse Document Frequency
    It is a weight scheme that reflects how important a word is to a specific document within a large collection of documents.
    tf-idf (t, d) =  tf(t,d)*idf(t,d)
    TF: how often a word appears in a single document
        Term frequency formula:

        tf(t, d) = f_{t,d} / \sum_{t' \in d} f_{t',d}
        where:
        - `f_{t,d}` is the raw count of how often term `t` appears in document `d`
        - the denominator is the total number of terms in document `d`
    IDF: how rare/common a word is across all the documents in the corpus
        Inverse document frequency formula:

        idf(t, D) = log( N / |{d : d \in D and t \in d}| )
        where:
        - `N` is the total number of documents in the corpus `D`
        - `|{d : d \in D and t \in d}|` is the number of documents containing term `t`




