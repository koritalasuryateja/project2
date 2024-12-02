# ReadMe: Text Search and Retrieval System

## Project Overview
This project is designed to implement a text search and retrieval system that processes HTML files to provide ranked document results based on user queries. The system utilizes algorithms and data structures such as tries, compressed tries, and TF-IDF (Term Frequency-Inverse Document Frequency) for efficient search and ranking.

---

## Key Features
1. **Parsing HTML Files**: Extracts text and links from HTML files for indexing.
2. **Compressed Trie**: Organizes indexed words for fast retrieval of document occurrences.
3. **TF-IDF Computation**: Scores documents based on their relevance to the query.
4. **Interactive Search Interface**: Allows users to input search queries and view ranked results.

---

## Data Structures

### 1. **Trie and Compressed Trie**
   - **Purpose**: Stores words and their occurrences across documents.
   - **Node Design**:
     - `char`: A character from the word.
     - `children`: A dictionary mapping characters to child nodes.
     - `is_end_of_word`: Marks the end of a valid word.
     - `occurrence_list`: Tracks the documents where the word appears.
   - **Compressed Trie**:
     - Combines paths for better memory efficiency.

   **Operations**:
   - **Insert**: Adds a word to the trie along with the document identifier.
   - **Search**: Retrieves a list of documents containing the word.

---

## Algorithms

### 1. **Text Preprocessing**
   - **Steps**:
     1. Convert text to lowercase.
     2. Tokenize text into words.
     3. Remove stopwords (common words like "the", "and").
     4. Lemmatize words to their base forms (e.g., "running" → "run").
   - **Tools**:
     - NLTK library for tokenization, stopword removal, and lemmatization.

### 2. **TF-IDF Scoring**
   - **Term Frequency (TF)**:
     \[
     TF(word) = \frac{\text{Number of occurrences of the word in a document}}{\text{Total number of words in the document}}
     \]
   - **Inverse Document Frequency (IDF)**:
     \[
     IDF(word) = \log\left(\frac{\text{Total number of documents}}{\text{Number of documents containing the word}}\right) + 1
     \]
   - **TF-IDF**:
     \[
     TF-IDF(word) = TF(word) \times IDF(word)
     \]

   **Purpose**:
   - Ranks words higher if they are frequent in a document but rare across all documents.

### 3. **Search and Rank**
   - Processes the query using the same preprocessing pipeline.
   - Searches the trie for documents containing the query terms.
   - Scores documents by summing up their TF-IDF scores for all query terms.
   - Sorts documents by their scores in descending order.

---

## Implementation Workflow

### 1. **Building the Compressed Trie**
   - Read all `.html` files in a directory.
   - Parse text content using BeautifulSoup.
   - Preprocess text to generate tokens.
   - Insert each token into the trie along with its associated document.

### 2. **Computing TF-IDF**
   - Generate word frequency dictionaries for each document.
   - Calculate TF for each word in every document.
   - Compute global IDF values for all words across all documents.
   - Combine TF and IDF to compute the final TF-IDF scores.

### 3. **Search and Rank**
   - Parse and preprocess the query.
   - Search the trie for documents containing query terms.
   - Calculate a relevance score for each document based on query terms' TF-IDF scores.
   - Return a ranked list of documents.

---

## Interactive Interface
- **Widgets**: Built using `ipywidgets`.
- **Components**:
  - A text box for entering search queries.
  - A button to trigger the search.
  - Output display for showing search results.

---

## Usage Instructions
1. Place HTML files in the specified directory (default: `C:\input_files`).
2. Update the `html_files_path` variable to point to your directory.
3. Run the script in a Jupyter environment.
4. Use the interactive interface to enter queries and view ranked results.

---

## Future Improvements
- Implement partial word matching and fuzzy search.
- Introduce pagination for large result sets.
- Optimize trie storage with advanced compression techniques.
- Extend support for multiple languages.

---

This project demonstrates the integration of advanced data structures and algorithms for solving real-world search and retrieval challenges efficiently.
