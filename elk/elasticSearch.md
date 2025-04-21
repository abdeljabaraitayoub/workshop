
### intro:
Elasticsearch is a **distributed, RESTful ==search engine==** built on top of **Apache ==Lucene==**. It’s designed for **fast full-text search**.

## 1. architecture:

![[Pasted image 20250418120412.png]]
!Builded Using Java (Jackson, netty, Lucene)
==Let's see the deps in the [code source](https://github.com/elastic/elasticsearch)!==

![[elastic-search Architecture]]


## **2. Lucene**

Lucene is a powerful Java-based full-text search library. It primarily works in two phases:

1. **Indexing **
2. **Searching**

### 1.  Indexing Phase

This phase prepares the data for fast searching.

#### Step-by-step:

#### ➤ Step 1: **Document Creation**

- A document in Lucene is a collection of fields (e.g., title, content, author).

#### ➤ Step 2: **Tokenization**

- The text in each field is passed to an **Analyzer** , which:
    
    - **Splits** text into tokens (words).
        
    - **Removes** stop words like “a”, “the”.
        
	- etc...
#### ➤ Step 3: **Inverted Index Creation**

 Lucene builds an ==**inverted index**== . a map from each term → list of documents it appears in. Like:
 
```java
"youcode" → [doc1, doc3] 
"cegedim" → [doc1, doc2]
"aitayoub" → [doc5, doc3]
"abdeljabar" → [doc4, doc1]
```


#### ➤ Step 4: **Persist the Index**

- The index is stored on disk using segment files (`*.cfs`, `*.fdx`, etc.).


#### ➤ **Example**

##### 1. define the documents:
```json
{
  "Documents": [
    "La pharmacie fait de la PDA avec OPUS , ils travaillent avec 40 EHPAD et ils traitent a peu près 1600 dossiers par semaine.",
    
    "la saisie de l'ordonnance se fait sur OPUS : Opus permet de dupliquer les dossiers de PDA créer (cette fonctionnalité est indispensable pour les pharmaciens)",
    
    "OPUS envoie les ordonnances a Eureka (on peut exploiter l'API vente pour le Nev)",
    
    "OPUS permet de facturer 12 a 15 DOSSIERS PAR HEURE"
  ],
}
```

##### 2. Removing the block words :
```json
{
   "Documents": [
   
    "pharmacie fait pda opus travaillent 40 ehpad traitent peu près 1600 dossiers semaine",
    
    "saisie ordonnance fait opus opus permet dupliquer dossiers pda créer fonctionnalité indispensable pharmaciens",
    
    "opus envoie ordonnances eureka exploiter api vente nev",
    
    "opus permet facturer 12 15 dossiers heure"
  ],
}
```

##### 3. Removing upperCases :
```json
{
   "Documents": [
   
   "pharmacie fait pda opus travaillent 40 ehpad traitent peu près 1600 dossiers semaine",
   
    "saisie ordonnance fait opus opus permet dupliquer dossiers pda créer fonctionnalité indispensable pharmaciens",
    
    "opus envoie ordonnances eureka exploiter api vente nev",
    
    "opus permet facturer 12 15 dossiers heure"
  ],
}
```

##### 3. Create an index :


```json
{
  "index": [
    {
      "document_id": 1,
      "content": "pharmacie fait pda opus travaillent 40 ehpad traitent peu près 1600 dossiers semaine"
    },
    {
      "document_id": 2,
      "content": "saisie ordonnance fait opus opus permet dupliquer dossiers pda créer fonctionnalité indispensable pharmaciens"
    },
    {
      "document_id": 3,
      "content": "opus envoie ordonnances eureka exploiter api vente nev"
    },
    {
      "document_id": 4,
      "content": "opus permet facturer 12 15 dossiers heure"
    }
  ]
}
```

#### inverted Index :

```json 
{
  "inverted_index": {
    "pharmacie": [1],
    "fait": [1, 2],
    "pda": [1, 2],
    "opus": [1, 2, 3, 4],
    "travaillent": [1],
    "40": [1],
    "ehpad": [1],
    "traitent": [1],
    "peu": [1],
    "près": [1],
    "1600": [1],
    "dossiers": [1, 2, 4],
    "semaine": [1],
    "saisie": [2],
    "ordonnance": [2],
    "permet": [2, 3, 4],
    "dupliquer": [2],
    "créer": [2],
    "fonctionnalité": [2],
    "indispensable": [2],
    "pharmaciens": [2],
    "envoie": [3],
    "ordonnances": [3],
    "eureka": [3],
    "exploiter": [3],
    "api": [3],
    "vente": [3],
    "nev": [3],
    "facturer": [4],
    "12": [4],
    "15": [4],
    "heure": [4]
  }
}


```

#### sort it + add the TF :

```json 
{
  "inverted_index": {
    "12": [
      {"document_id": 4, "tf": 1}
    ],
    "15": [
      {"document_id": 4, "tf": 1}
    ],
    "40": [
      {"document_id": 1, "tf": 1}
    ],
    "api": [
      {"document_id": 3, "tf": 1}
    ],
    "dupliquer": [
      {"document_id": 2, "tf": 1}
    ],
    "dossiers": [
      {"document_id": 1, "tf": 1},
      {"document_id": 2, "tf": 1},
      {"document_id": 4, "tf": 1}
    ],
    "envoie": [
      {"document_id": 3, "tf": 1}
    ],
    "ehpad": [
      {"document_id": 1, "tf": 1}
    ],
    "eureka": [
      {"document_id": 3, "tf": 1}
    ],
    "exploiter": [
      {"document_id": 3, "tf": 1}
    ],
    "facturer": [
      {"document_id": 4, "tf": 1}
    ],
    "fait": [
      {"document_id": 1, "tf": 1},
      {"document_id": 2, "tf": 1}
    ],
    "fonctionnalité": [
      {"document_id": 2, "tf": 1}
    ],
    "indispensable": [
      {"document_id": 2, "tf": 1}
    ],
    "nev": [
      {"document_id": 3, "tf": 1}
    ],
    "opus": [
      {"document_id": 1, "tf": 1},
      {"document_id": 2, "tf": 1},
      {"document_id": 3, "tf": 1},
      {"document_id": 4, "tf": 1}
    ],
    "permet": [
      {"document_id": 2, "tf": 1},
      {"document_id": 3, "tf": 1},
      {"document_id": 4, "tf": 1}
    ],
    "pharmacie": [
      {"document_id": 1, "tf": 1}
    ],
    "pharmaciens": [
      {"document_id": 2, "tf": 1}
    ],
    "pda": [
      {"document_id": 1, "tf": 1},
      {"document_id": 2, "tf": 1}
    ],
    "près": [
      {"document_id": 1, "tf": 1}
    ],
    "saisie": [
      {"document_id": 2, "tf": 1}
    ],
    "semaine": [
      {"document_id": 1, "tf": 1}
    ],
    "traitent": [
      {"document_id": 1, "tf": 1}
    ],
    "travaillent": [
      {"document_id": 1, "tf": 1}
    ],
    "vente": [
      {"document_id": 3, "tf": 1}
    ],
    "1600": [
      {"document_id": 1, "tf": 1}
    ],
    "créer": [
      {"document_id": 2, "tf": 1}
    ],
    "ordonnance": [
      {"document_id": 2, "tf": 1}
    ],
    "ordonnances": [
      {"document_id": 3, "tf": 1}
    ],
    "peu": [
      {"document_id": 1, "tf": 1}
    ],
    "heure": [
      {"document_id": 4, "tf": 1 , "rank":}
    ]
  }
}
```


---

### 2.  Searching Phase

This phase retrieves documents based on a query.
#### Step-by-step:

##### ➤ Step 1: **Query Parsing**

- User enters a query like: `"lucene AND search"`.

##### ➤ Step 2: **Query Execution**

- Lucene searches the **inverted index** for documents matching the query terms.
  
##### ➤ Step 3: **Scoring & Ranking**

- Each document is scored based on:
    
    - **Term Frequency (TF)** – How often the term appears.
        
    - **Inverse Document Frequency (IDF)** – How rare the term is.
        
	- Results are sorted by score.
	  
	  
	  
	  
	  

==Ready for some math?==

##### ➤ Step 4: **Return Results**

- Top N results are returned with metadata like document ID, title, and score.

## **3. Sql indexation vs ElasticSearch indexation :**

