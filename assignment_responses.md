1.  **Evolution of Embeddings:** Briefly describe the key limitation of TF-IDF that Word2Vec aimed to solve. What limitation of sequential models (like LSTMs) did the Transformer architecture address with its attention mechanism?

TD-IDF analyzed and treated each word in a phrase as a unique instance, severing them from having any relation to one another. This prevented it from being able to understand semantics. Word2Vec essentially remedied this by utilizing low dimension word embeddings, where it captured words relations to each other.

Sequential models processed data one step after another. Processing data in this way was slower, and it limited the ability of the model to reliably process particularly long prompts with lots of semantic density. The attention mechanism allowed for different parts of the input to be analyzed and processed in parallel.  

2.  **BERT's Contribution:** What was the significance of BERT's "bidirectional" pre-training compared to earlier models?

The bidirectional pre-training essentially allowed the model to read inputs in both directions i.e. it could read inputs forward and backward and still be able to process the. This improved the model's grasp of semantics and context.

3.  **BERT vs. Ada:** Create a table summarizing the key differences (pros/cons) between using a locally run Sentence-BERT model versus the OpenAI `text-embedding-ada-002` API for generating embeddings in a project.

| Features |  OpenAI  |   BERT   |
|----------|----------|----------|
| Network Connectivity  | Needs internet | Works offline |
| Scalability  | Highly Scalable | dependent on physical hardware and storage |
| Performance  | Powerful and accurate performance | Good but not as powerful as OpenAI |
| Cost | Uses a token model that requires refilling | Free after one time set up |


4.  **Chunking Scenario:** Imagine you have a large PDF textbook (1000 pages) that you want to use for RAG.
    *   Why is chunking absolutely necessary here (consider model input limits)?

        There is a finite limit on the amount of words that the model can process at once. A textbook that long would have far more words than the model could analyze in one sitting. Chunking allows the data to be broken down into digestible bits. Chunking also allows for the model to better keep track of context throughout such a long text.

    *   Describe *two* different chunking strategies you could use.

        Paragraph based chunking - this strategy breaks the text down by paragraph, which then become chunks that are processed by the model. This is probably the simplest way to go about it.

        Sliding Window Chunking - this works by breaking the text down into chunks that overlap with one another. The model essentially moves over the text, one word at a time creating new chunks as it goes. This allows for a high level of context interpretation.

    *   What factors would influence your choice of chunk *size* and *overlap*?

        It would depend on a few things:

        1) Document Structure - the structure of the writing is important. Textbooks contain breaks between topics and sections, this is important to consider. Prose and novels may have longer sections of writing with connected ideas. In order to maintain the context of the writing, it is important to consider chunk size and length.

        2) Token Limits - If its a model like OpenAI, then there could be a limit on how much data can be process at one time. In order to maximize the use of the available tokens then the chunk size should be greatly considered.

        3) Memory Constraints - How much memory is physically available should be considered. Larger chunks will demand much more memory than lower density chunks.


5.  **Model Selection Rationale:** For each scenario below, which embedding approach (OpenAI Ada vs. Local SBERT) might be more suitable and *why*? Justify your choice based on the factors discussed (cost, privacy, performance, quality, ease of use).
    
    *   A startup building a quick prototype chatbot for public website FAQs.

    Recommendation: Open AI Ada

    OpenAI pprovides a token based model which allows users to pay as they go. For a start up company this could be ideal as they may not have the massive budget necessary to facilitate high level usage. OpenAI is also very easy to use which still performing cutting edge performance (relatively speaking), which makes for ease of deployment.

    *   A hospital developing an internal system to search sensitive patient record summaries (anonymized for the search, of course!).

    Recommendation: Local SBERT

    Local SBERT offers a more sensible cost structure for an organization like a hospital, with an initial investment and no further recurring payments. This will allow for long term use.
    Local SBERT also guarantees a greater level of privacy as data is not sent over the web using an API. This is super important for a hospital which handles sensitive records. Local SBERT also allows for greater contextual understanding, this is important for understanding medical information.
    
    *   A solo developer building a personal note-taking app with semantic search features, running only on their own powerful desktop PC.    

    Recommendation: Local SBERT

    Local SBERT does not have any ongoing costs. This is ideal for a solo devloper who will not be extracting any financial benefit from the application. Pay per use adds up a lot over time.
    Local SBERT also offers greater contextual understanding. This would be great for note-taking.