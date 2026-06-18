# RAG-learning-and-concept-notes
The info of RAG systems, the meaning, the use and all stuff related to RAG and concepts to understand it.

## RAG (Retrieval Augmented Generation)

### Problem it solves
AI models don't know business-specific information.
Putting everything in the system prompt doesn't scale.
RAG fetches only relevant info when needed.

### Embeddings
Converting text into numbers that represent meaning.
Similar meaning = similar numbers.
Allows searching by meaning, not just keywords.

Example:
- "root canal cost" and "nerve treatment price" 
  → different words, same meaning → similar numbers → match found

### Vector Databases
This is where the embeddings gets stored. Normal databases store text strings and number. Whereas vector databases store the meaning of the text in the form of numbers. 

When a patient asks a question
- Their question gets converted to embeddings.
- VectorDB finds the stored embedings most similar and closest to it.
- Returns the closest matching text.
Its basically a search engine that understands the meaning.

Popular vector databases: Pinecone, Weaviate, Qdrant, ChromaDB
For your dental clinic project you'd likely use Qdrant (free, can run locally).

## The RAG Pipeline

There are two phases:

---

### Phase 1 — Indexing (done once)
This is where you prepare your knowledge base.

1. Start with your clinic info (PDF/text)
2. Split into chunks
3. Convert each chunk to embeddings
4. Store in Vector DB

Example chunk: "Root canal treatment costs ₹5000-₹8000

and takes 2 sittings of 45 minutes each."

### Phase 2 — Querying (happens every time a patient asks something)

1. Patient sends a question
2. Question gets converted to embeddings
3. Vector DB searched for similar embeddings
4. Relevant chunks returned
5. Chunks + question sent to AI
6. AI generates answer based only on those chunks

---

### Key point
The AI never guesses. It only answers based on what you gave it in those chunks.
That's why RAG is reliable for business use.




