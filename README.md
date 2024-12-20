# -Skip-gram-Word-Embedding-Model-with-PyTorch
Developed a Skip-gram model from scratch using PyTorch to learn word embeddings for NLP tasks.

The program implements a **Skip-gram neural network** for learning **word embeddings**—dense vector representations of words. It takes a simple text corpus, tokenizes it, generates training pairs (target word and context word), and trains an embedding layer to produce meaningful word representations.

---

### **Key Steps**

1. **Data Preparation**:
    - A small corpus of sentences is defined.
    - **Vocabulary Creation**: Unique words are extracted and mapped to indices.
    - **Training Data Generation**:
        - For each word in a sentence, context words are collected within a specified `window_size`.
        - Training pairs (target word, context word) are generated for Skip-gram learning.
    
    **Example**:
    For the sentence:
    
    `["embeddings", "are", "the", "foundation"]` with `window_size=2`,
    
    the training pairs include:
    
    `(embeddings, are)`, `(embeddings, the)`, `(are, embeddings)`, `(are, the)`, etc.
    
2. **Skip-gram Model**:
    - The model consists of an **embedding layer** and a **linear output layer**.
    - **Input**: Target word index.**Output**: A score for each word in the vocabulary (after projection to vocabulary size).
    - The embedding layer learns dense vector representations of words.
3. **Loss and Optimization**:
    - **CrossEntropyLoss** is used to compare predicted word probabilities to the actual context word index.
    - **Adam Optimizer** updates the model parameters.
4. **Training**:
    - For each target-context word pair:
        - The target word's index is passed into the model.
        - The model predicts the context word.
        - The loss is calculated, backpropagated, and the embedding layer is updated.
5. **Word Embedding Visualization**:
    - After training, the learned embeddings are retrieved from the embedding layer.
    - For selected words, the embeddings are printed as dense numerical vectors.

---

### **Output**:

1. **Training Loss**:
    - The loss reduces over epochs, showing that the model is learning meaningful embeddings.
2. **Word Embeddings**:
    - The program prints the embeddings for a few words (e.g., "nlp", "embeddings", "deep").
    - Each word embedding is a dense vector of size `embedding_dim=50`.
    
    **Example**:
    
    ```makefile
    makefile
    Copy code
    embeddings: [ 0.123 -0.456  0.789 ... -0.321]
    
    ```
    
3. **Saving Embeddings**:
    - Learned embeddings are saved as a `.npy` file for later use.
