# vibe_matcher_prototype

Task: Prototype a "Vibe Matcher" Notebook
Context: Build a mini rec system: Input vibe query → Embed products → Match top-3 via cosine similarity. Use sample fashion data (5-10 items w/ descriptions).

Data Prep (45-60 min): Create a Pandas DF w/ 5-10 mock products (e.g., {"name": "Boho Dress", "desc": "Flowy, earthy tones for festival vibes"}). Tag vibes (e.g., ["boho", "cozy"]).
Embeddings (1 hr): Use OpenAI API (free tier) to generate embeddings (text-embedding-ada-002) for descs & sample query ("energetic urban chic").

Vector Search Sim (1-1.5 hr): Compute cosine sim (sklearn) for matches. Output top-3 ranked products w/ scores. Handle edge (e.g., no match → fallback prompt).

Test & Eval (45 min): Run 3 queries; log metrics (e.g., sim score >0.7 as "good"). Plot latency (timeit).
Reflection (30 min): 3-5 bullets: Improvements (e.g., Pinecone integration)? Edge cases handled?

Why AI at Nexora? - I’m drawn to AI at Nexora because of its focus on solving real-world problems through intelligent automation and data-driven insights. I’m particularly excited by the intersection of retrieval systems and sustainability — areas where thoughtful model design can reduce inefficiencies and create measurable social impact. Building the “Vibe Matcher” prototype reinforced my belief that good AI balances creativity with rigor, and Nexora’s culture of experimentation and applied learning aligns perfectly with that philosophy.

A mini project in collaboration with AI Nexora. Concept is
