# RAG on Firestore without a vector database

*A small-corpus retrieval setup that added zero infrastructure, and the moment I'd change it.*

The assistant in the inspection platform I run answers questions about the company's own procedures: what the standard says about a double-tapped breaker, how the house phrases a recommendation about a cracked chimney crown, which statement goes with which finding. That needs retrieval over the company's documents, which means embeddings, which usually means a vector database.

I didn't add one. Here's the setup, why it works, and where it stops working.

## The setup

- **Chunking and ingest.** The SOP and reference material are split into chunks and written to a Firestore collection. Each chunk carries its text, metadata, and an embedding from a small embedding model stored as a Firestore vector field.
- **Query.** The user's question is embedded with the same model. Firestore's native nearest-neighbor query runs against the vector index with cosine distance and returns the top chunks.
- **Fallback.** If the vector path returns nothing or errors, a keyword search over the same collection runs instead. The fallback fires on empty results and on errors, which matters: the first version only handled errors, and an empty result quietly produced an answer with no grounding.
- **Prompt.** Retrieved chunks go into the system prompt with the house style rules. Answers stream to the client token by token.

One collection, one index, one function. The retrieval lives under the same security rules as the rest of the org's data, so an inspector from one organization cannot retrieve another's documents by construction.

## Why it was the right call here

The corpus is small: a few hundred chunks. At that size a dedicated vector database is a second system to pay for, secure, back up, and keep running, for a capability the existing database now provides. The cost of being wrong was low too: if native vector search had been inadequate, migrating a few hundred documents is an afternoon.

The less obvious win was operational. Every incident in the platform's first year traced back to one of a small number of services. Not adding a service is the cheapest reliability improvement there is.

One verification I'd recommend before trusting any retrieval setup: ask something that shares no keywords with the answer. "Two wires under one screw" retrieving the double-tap statement was the moment this one earned its keep.

## What I'd change, and when

- **Corpus size.** Past tens of thousands of chunks, a purpose-built index will be faster and cheaper to query. The trigger is written in the design notes so nobody has to rediscover it.
- **Re-embedding.** Changing embedding models means re-embedding everything. A few hundred documents is a script. A few million is a migration plan.
- **Hybrid ranking.** The fallback is keyword-or-vector, not a blended score. A real hybrid retriever would help on short, jargon-heavy queries. Not needed yet.
- **Index creation.** The vector index had to be created through the admin API rather than the CLI config at the time. Budget an hour for that the first time.

## The general lesson

The question isn't "what's the best vector database." It's "do I need a database for this at all." For a small business with one AI feature and a few hundred documents, the answer was no, and the platform has run on that answer for over a year.

*Ryan Faber builds AI applications and business software for operations. Case studies at [github.com/Redthreepro](https://github.com/Redthreepro).*
