# **Colab Space for Group 3**
## Paper in focus
[3 Lost in Transliteration: Bridging the Script Gap in Neural IR. Andreas Chari, Iadh Ounis, and Sean MacAvaney. (SIGIR 2025). ](https://dl.acm.org/doi/10.1145/3726302.3730226)

[>> Their GitHub Repository](https://github.com/andreaschari/transliterations)

## Collaborators
+ Wesp Simon
+ Nico Reiterer
+ Kerner Simon

## **Resources**

+ **Preliminary repo for the beginning**: 
https://github.com/NicoReit54/ExDDS_WS25

+ **Overleaf Template**:
https://www.overleaf.com/3451124583vmvqbbtszgyv#3afd79

+ **mMARCO**: 
https://github.com/unicamp-dl/mMARCO // https://huggingface.co/datasets/unicamp-dl/mmarco#

+ **neuCLIR/1**: 
https://neuclir.github.io/#-task-multilingual-retrieval-mlir ??

+ **Uroman Latin Transliterator**: 
https://aclanthology.org/P18-4003.pdf *(remark: the software itself is not available anymore but a git repo still)*

+ **Translate Train methodology** (3rd chapter): 
https://link.springer.com/chapter/10.1007/978-3-030-99736-6_26#Sec3

+ **BGE-M3 (used as retriever)**: 
https://huggingface.co/BAAI/bge-m3/blob/main/README.md

+ **mT5 (used as reranker)**:
https://github.com/google-research/multilingual-t5

+ **PyTerrier platform (similar to PyTorch etc just for IR)**:
https://github.com/terrier-org/pyterrier

+ **ir-measures (IF with several IR evaluation tools)**:
https://ir-measur.es/en/latest/

+ **ir_datasets (package for accessing the datasets)**
https://github.com/allenai/ir_datasets

****
### **Some interesting forum entries/explanations on top**
**Sparse and dense information**
https://www.reddit.com/r/MachineLearning/comments/z76uel/d_difference_between_sparse_and_dense_information/

**Retriever and Reranker**
https://www.pinecone.io/learn/series/rag/rerankers/
****

## **Q & A**

**What is a retriever?**

A retriever, which retrieves relevant knowledge pieces from a knowledge base given a context, is an important component in many natural language processing (NLP) tasks. Retrievers have been introduced in knowledge-grounded dialog systems to improve knowledge acquisition. Basically finds quickly a candidate set of potentially relevant documents from a huge collection based on the query.

<br/><br/>
**What is a reranker?**

A reranking model — also known as a cross-encoder — is a type of model that, given a query and document pair, will output a similarity score. We use this score to reorder the documents by relevance to our query.

Search engineers have used rerankers in two-stage retrieval systems for a long time. In these two-stage systems, a first-stage model (an embedding model/retriever) retrieves a set of relevant documents from a larger dataset. Then, a second-stage model (the reranker) is used to rerank those documents retrieved by the first-stage model.

We use two stages because retrieving a small set of documents from a large dataset is much faster than reranking a large set of documents — we'll discuss why this is the case soon — but TL;DR, rerankers are slow, and retrievers are fast.

[Good website for explanation on the above two questions](https://www.pinecone.io/learn/series/rag/rerankers/)

<br/><br/>
**What are PyTerrier, ir-measures and ir_datasets?**

**PyTerrier** is a Python framework for building reproducible IR experiments by chaining components such as retrievers and rerankers into pipelines.

**ir-measures** is a library that provides standardized implementations of evaluation metrics like MRR, Recall, and nDCG to ensure consistency across experiments

**ir_datasets** is a library that offers access to benchmark IR datasets (including queries, documents, ...) with standardized preprocessing and versioning. 

Together, these tools form a workflow where ir_datasets basically supplies the data, PyTerrier runs the retrieval pipeline, and ir-measures evaluates the results.

<br/><br/>
**What are the measures used in the paper?**

**MRR@k (Mean Reciprocal Rank)**  
- Measures how quickly the first relevant document appears (within the first *k* retrieved documents)
- Reciprocal of the rank of the first relevant doc, averaged across queries (e.g. first relevant document appeared second >> 1/2 = 0.5)
- Range: 0–1 (higher is better).

**R@k (Recall@k)**  
- Fraction of all relevant documents retrieved within the top *k* results.  
- Shows coverage: did the system find most of the relevant docs?  
- Range: 0–1 (higher is better).

**nDCG@k (Normalized Discounted Cumulative Gain)**  
- Considers multiple relevant documents and their positions in the ranking.  
- Higher relevance and higher rank contribute more.  
- Normalized against the ideal ranking.  
- Range: 0–1 (higher is better).



