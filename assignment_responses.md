1.  **Evolution of Embeddings:** Briefly describe the key limitation of TF-IDF that Word2Vec aimed to solve. What limitation of sequential models (like LSTMs) did the Transformer architecture address with its attention mechanism?

TD-IDF analyzed and treated each word in a phrase as a unique instance, severing them from having any relation to one another. This prevented it from being able to understand semantics. Word2Vec essentially remedied this by utilizing low dimension word embeddings, where it captured words relations to each other.

Sequential models processed data one step after another. Processing data in this way was slower, and it limited the ability of the model to reliably process particularly long prompts with lots of semantic density. The attention mechanism allowed for different parts of the input to be analyzed and processed in parallel.  

2.  **BERT's Contribution:** What was the significance of BERT's "bidirectional" pre-training compared to earlier models?

The bidirectional pre-training essentially allowed the model to read inputs in both directions i.e. it could read inputs forward and backward and still be able to process the. This improved the model's grasp of semantics and context.

3.  **BERT vs. Ada:** Create a table summarizing the key differences (pros/cons) between using a locally run Sentence-BERT model versus the OpenAI `text-embedding-ada-002` API for generating embeddings in a project.

| features |  OpenAI  |   BERT   |
|----------|----------|----------|
| network connectivity  | needs internet         | works offline         |
| Scalability  | dependent on physical hardware and storage         |  highly scalable   |
|          |          |          |


4.  **Chunking Scenario:** Imagine you have a large PDF textbook (1000 pages) that you want to use for RAG.
    *   Why is chunking absolutely necessary here (consider model input limits)?


    *   Describe *two* different chunking strategies you could use.


    *   What factors would influence your choice of chunk *size* and *overlap*?


5.  **Model Selection Rationale:** For each scenario below, which embedding approach (OpenAI Ada vs. Local SBERT) might be more suitable and *why*? Justify your choice based on the factors discussed (cost, privacy, performance, quality, ease of use).
    *   A startup building a quick prototype chatbot for public website FAQs.


    *   A hospital developing an internal system to search sensitive patient record summaries (anonymized for the search, of course!).

    
    *   A solo developer building a personal note-taking app with semantic search features, running only on their own powerful desktop PC.    