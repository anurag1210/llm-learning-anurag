RAG notes
---------

What Are Embeddings?

Embeddings are a way to convert complex data into numbers — specifically, dense vectors — that a machine learning model can easily understand and work with.

Think of them as compressed meaning.

⸻

📍 Why Are They Important?

Most ML models can’t directly understand:
	•	Text like “apple”
	•	Audio like your voice
	•	Products or movies

Embeddings translate those things into vectors (e.g., [0.13, -1.42, 3.01, ...]) that capture their meaning, features, and relationships.

---
🧠 What is Cosine Similarity?

Cosine similarity is a way to measure how similar two vectors are by looking at the angle between them — not their size.

Imagine two arrows (vectors) starting from the same point:
- If they point in the same direction → Very similar → Cosine similarity = +1
- If they are completely unrelated (90°) → Cosine similarity = 0
- If they point in opposite directions → Very different → Cosine similarity = -1

🎯 Analogy:
- "I love dogs" and "I like puppies" → Similar vectors → High cosine similarity
- "I love dogs" and "I crashed my car" → Very different → Low cosine similarity

📐 Why “Cosine”?
It uses the cosine of the angle between vectors:
- 0° → cos(0) = 1 → same direction
- 90° → cos(90) = 0 → unrelated
- 180° → cos(180) = -1 → opposite direction

🤖 In LLMs and vector databases:
Cosine similarity is used to compare the query vector with document vectors and find the most semantically similar ones.

✅ TL;DR:
Cosine similarity = How close in direction two data points are in vector space. It's essential in NLP, vector search, and semantic similarity tasks.
---

