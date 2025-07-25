## Hybrid Search with Azure AI: Combining Keyword & Vector Queries
Artificial intelligence is evolving rapidly, giving us powerful tools that bring human-like understanding to software systems. One of the most exciting advancements in this space is vector search, a form of semantic search. Unlike traditional keyword-based search, which looks for exact word matches, vector search understands the meaning behind a query and returns results that are contextually relevant, even when the wording differs.

In this blog post, we’ll explore how to integrate vector search into your application to make search smarter, more intuitive, and user-friendly.

## Traditional Keyword Search :
In traditional keyword-based search, the system looks for exact keyword matches in the document and ranks results based on how often those keywords appear. The more frequently a keyword shows up, especially in prominent places like titles or headings, the higher the document ranks.

## Example: Searching for Shoes on an E-commerce Site

### Product Descriptions:
1. Top-rated running shoes for marathon training
2. Men’s lightweight running shoes for optimal performance
3. Best sneakers for jogging and daily wear
4. Top-rated sneakers for running

### Query Results
1. Search: `sneakers` -> Matches descriptions 3 and 4, because they include the exact word `sneakers`.
2. Search: `running` -> Matches 1, 2, and 4, as these explicitly mention `running`.
3. Search: `Best running shoes` -> Returns all four, because each document contains `best`, `running`, or `shoes` and will return results accordingly
4. Search: `sneakars` ->  It will not return anything as the spelling mistake is there. 

## Vector Search / Semantic Search:
Enhancing search engines to return more relevant results based on the meaning of queries rather than just keyword matching.

Now when we are searching for Best Running Shoes it should have returned products with following order based on semantic meaning of product description: 

  #1 – `Top‑rated running shoes for marathon training` – strongest match: `running shoes`, `top-rated` (synonym for `best`).

  #2 – `Men’s lightweight running shoes for optimal performance` – very close match (`running shoes`, performance-related).

  #3 – `Top‑rated sneakers for running` – matches `top-rated` + `running` even though it says `sneakers`.

  #4 – `Best sneakers for jogging and daily wear` – includes `best` and `sneakers` aligned with running/casual wear.

Before diving deeper into the implementation of vector search lets understand few terminologies related to vector search:

## Vectorization/ Vector Embeddings:

Vectorization is simply turning things like words, sentences, pictures, or even whole documents into lists of numbers that computers can work with—so one piece of text becomes something like [0.32, 0.42, …], and another text with a similar meaning ends up with numbers that are close to it. It's like placing ideas on a map: “sneakers” and “shoes” sit near each other because they're alike, while “heels” is farther away. This makes it easy for a computer to group similar items, find synonyms, or rank search results by meaning rather than just exact words.
There are different models which we can use to do vector embedding for queries and also for storing data in vector format. 

## Text-embedding-ada-002

This is text embedding model provided by Open AI. It is used to transform text into fixed length vectors.It can be used for various applications like Semantic Search, Clustering and Classification or Recommendation system.
In this blog post we will be using this model to generate vector embeddings.

## Distance and Similarity Matrix:

A distance matrix tells you how different two items are. The smaller the value, the more similar the items. A similarity matrix tells you how similar two items are. The higher the value, the more similar the items.

1. *Cosine Similarity*: Measures the angle between two vectors, focusing on direction over length. Its great for text comparisons.
2. *Euclidean Distance*: The straight-line distance between points. Useful but less effective in high dimensions.
3. *Dot Product*: Captures both direction and magnitude. It is commonly used inside models.

## k-NN and ANN

1. *k-Nearest Neighbors (k-NN)*: Finds exact closest vectors by comparing to every point—accurate but slow for large data.
2. *Approximate Nearest Neighbors (ANN)*: Sacrifices a bit of accuracy for huge speed gains using smart indexing.

Lets see how all of this concepts connects :

## Pre-requisite
1. You must have azure subscription acess
2. Your account must be approved for Azure OpenAI

## Create Azure Open AI resource in Azure Portal

1. [Go to azure portal](https://portal.azure.com) and Search for `Azure OpenAI`.
2. Create a new resource of Azure OpenAI.
3. Follow the prompt as mentioned in below image and wait till deployment is completed.
4. Go to the AzureFoundry Azure AI Playground.
5. Go to Deployment Model and deploy `Text-embedding-ada-002` model by following the prompt as shown below.
6. Once deployment is completed we can consume the APi to generate the text embeddings using the `api-endpoint` and `api-key`.

## Create Azure Search Index

1. On Azure Portal create the Search Service Resource
2. Using the API endpoint and key we can create the new indexes in the search service

## Generate the data for Azure Search Index store embedded vectors for the vector fields

## Keyword Based Query

## Vectory Search Query

## Hybrid Query


   

    

   
