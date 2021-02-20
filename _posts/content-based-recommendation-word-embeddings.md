---
layout: post
title: "Content-Based Recommendation System Using Word Embeddings"
---

### Contents
{:.no_toc}

* A markdown unordered list which will be replaced with the ToC, excluding the "Contents header" from above
{:toc}

## Content-Based Recommendation System Using Word Embeddings

In his [article](https://medium.com/towards-artificial-intelligence/content-based-recommendation-system-using-word-embeddings-c1c15de1ef95) Dhilip Subramanian describes a book recommendation engine based on goodreads data. He explains that "a content-based recommendation system recommends books to a user by taking similarity of books based on the description. It also considers the user's previous book history in order to recommend a similar book. Cosine similarity is used in our recommender system to recommend the books."

The repository is at [https://github.com/sdhilip200/Content-Based-Recommendation---Good-Reads-data](https://github.com/sdhilip200/Content-Based-Recommendation---Good-Reads-data).

The code is given in a Python notebook. When I ran the code, I faced a few errors and had to change the code, as follows:

Cell \[2\] : `df = pd.read_csv("test.csv")`\
I replaced test.csv with data.csv\
`df = pd.read_csv("data.csv")`

Cell \[9\] : `google_model.build_vocab(line_of_sentance)`\
I replaced `line_of_sentance` with `corpus`\
`google_model.build_vocab(corpus)`

Cell \[9\] : `%%time`\
SyntaxError: invalid syntax\
I commented it.

Cell \[13\] : `cosine_similarities = cosine_similarity(array_embeddings, array_embeddings)`\
I replaced `array_embeddings` with `word_embeddings`\
`cosine_similarities = cosine_similarity(word_embeddings, word_embeddings)`

I forked the repository and made the changes.\
It can be accessed at: [https://github.com/mh-github/Content-Based-Recommendation---Good-Reads-data](https://github.com/mh-github/Content-Based-Recommendation---Good-Reads-data)



