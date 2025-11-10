# vibe_matcher_prototype

Task: Prototype a "Vibe Matcher" Notebook

Context: Build a mini rec system: Input vibe query → Embed products → Match top-3 via cosine similarity. Use sample fashion data (5-10 items w/ descriptions).
The Vibe Matcher is a mini recommendation system designed to understand the vibe of a user’s query and suggest the most relevant fashion items. Instead of keyword search, it uses semantic similarity to match the mood or style — for example, a query like “energetic urban chic” finds items that share that same fashion tone.


Data Preparation: Create a Pandas DF w/ 5-10 mock products (e.g., {"name": "Boho Dress", "desc": "Flowy, earthy tones for festival vibes"}). Tag vibes (e.g., ["boho", "cozy"]).
We created a Pandas DataFrame of 8 sample products, each with:
•	Name (e.g., “Boho Dress”)
•	Description (e.g., “Flowy, earthy tones for festival vibes”)
These descriptions act as the text input for our embeddings. In a larger system, we could also add tags or attributes like season, color, or material to enrich vibe-based recommendations.


Embeddings: Use OpenAI API (free tier) to generate embeddings (text-embedding-ada-002) for descs & sample query ("energetic urban chic").
To capture semantic meaning, we used text embeddings that convert text into numerical vectors:
1.	OpenAI Embeddings (text-embedding-ada-002) — capture deep contextual relationships between words.
2.	TF-IDF Fallback — a simpler, local approach used when the OpenAI API key isn’t available.
All embeddings are L2-normalized so that cosine similarity can measure how “close” a query is to each product in vibe space.


Vector Search Sim: Compute cosine sim (sklearn) for matches. Output top-3 ranked products w/ scores. Handle edge (e.g., no match → fallback prompt).
Using cosine similarity from scikit-learn, we compared the query vector with all product vectors.
The system outputs:
•	Top-3 product matches ranked by similarity score
•	A fallback message if no confident match (e.g., score < 0.35 for TF-IDF or < 0.7 for OpenAI)
This helps avoid false confidence in irrelevant results and improves interpretability.


Test & Eval: Run 3 queries; log metrics (e.g., sim score >0.7 as "good"). Plot latency (timeit).
We tested the model with three vibe-based queries:
1.	“energetic urban chic”
2.	“cozy autumn outfit”
3.	“minimalist evening elegance”
For each query, we recorded:
•	The top 3 most similar products
•	Their cosine similarity scores
•	The total time taken (latency)
•	Whether the top match exceeded the “good” similarity threshold
We also visualized query latency with matplotlib to check how efficient the search is.


Reflection: 3-5 bullets: Improvements (e.g., Pinecone integration)? Edge cases handled?
Key learnings and improvements:
•	Integrate a vector database like Pinecone or Weaviate for scalable, persistent retrieval.
•	Combine text + visual + metadata embeddings for richer vibe matching.
•	Improve edge-case handling (ambiguous or very short queries).
•	Add precision@k and MRR metrics to evaluate match quality.
•	Extend this into a real-time fashion recommendation API or app demo.


Why AI at Nexora? - I’m drawn to AI at Nexora because of its focus on solving real-world problems through intelligent automation and data-driven insights. I’m particularly excited by the intersection of retrieval systems and sustainability — areas where thoughtful model design can reduce inefficiencies and create measurable social impact. Building the “Vibe Matcher” prototype reinforced my belief that good AI balances creativity with rigor, and Nexora’s culture of experimentation and applied learning aligns perfectly with that philosophy.

A mini project in collaboration with AI Nexora.
