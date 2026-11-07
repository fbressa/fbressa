# Filipe Bressanelli

Software Engineering student at the University of Brasília (UnB), working on AI systems that run in production.

## DORSAL · AI service for a football shirt recommerce platform
EngNet, for an international client · Python · FastAPI · SigLIP 2 · pgvector · Gemini · Supabase · Google Cloud Run

FastAPI service on Cloud Run, called by a Supabase webhook for each new listing.

**Pipeline**
1. SigLIP 2 (`siglip2-base-patch16-224`) encodes the front photo into a 768-d L2-normalized embedding.
2. pgvector (HNSW, cosine) returns the top 5 kits among 1,786 reference photos of 345 kits.
3. Gemini compares all photos (front, back, label, details) with the candidates' metadata and returns structured output with per-field confidence. A field is only pre-filled when it agrees with the catalog (club, supplier, sponsor, players, sizes); conflicts become suggestions.
4. The same photos feed a condition assessment used by the pricing engine.

**Reliability and performance**
- Production timeouts from 34 in September to 1 since October; median analysis time from 29 s to about 12 s with a warm instance.
- Request failures from 13/40 to 0/40 in regression: model loaded offline at startup, container image from 7.9 GB to 4.8 GB, SigLIP and Supabase calls moved off the event loop, Gemini retries with fallback models inside a time budget.
- Keyset pagination after PostgREST's 1,000-row cap hid 99 of the 345 kits from the service.

**Testing and release**
- 33 attribute tests with no network calls, plus a regression run against live Gemini and Supabase before each release (15/15 compatible responses).
- Embedding compatibility check across library upgrades (cosine 1.000000 on 40 photos, no reindex needed).
- Tagged no-traffic deploys on Cloud Run with a documented rollback revision.

**Next:** a labeled set of real user photos to measure accuracy outside the catalog, and a shorter cold start (currently 75 to 120 s).

Repositories (private, client code): [server_identificador_camisas](https://github.com/dirproj/server_identificador_camisas) · [SigLIP2](https://github.com/dirproj/SigLIP2)

## Other projects

**[Sensitive Data Classifier](https://github.com/fbressa/hackathon-participaDf)** · Python · PyTorch · BERT  
Detects personal data in public information requests with rules and a fine-tuned BERT model. Built end to end for the Participa DF Hackathon.

**[Content Agent](https://github.com/fbressa/criador_de_conteudo)** · Python · Agno · Tavily · FastAPI  
Agent that researches the web, reads video transcriptions and drafts scripts, with tool calling and persistent memory.

**[World Cup Prediction Market](https://github.com/fbressa/txodd_hackathon)** · Rust · Anchor · TypeScript  
Parimutuel market on Solana settled automatically from a live sports data feed, with 12 tests and CI.

**[ChamaControl](https://github.com/unb-mds/2024-2-ChamaControl)** · Node.js · React · MySQL  
Wildfire monitoring platform built by a 6-person team at UnB, live in production.

**[Python-to-C Compiler](https://github.com/fbressa/PyToC)** · C · Flex · Bison  
Translates a subset of Python into C.

**[Go Web Server](https://github.com/fbressa/golangwebserver)** · Go  
REST API with concurrent-safe user management, written with the standard library only.

## Stack
- **Languages:** Python, TypeScript, C, C++, Go, Rust
- **AI:** LLM integration, multimodal LLMs, embeddings and vector search, structured outputs, evaluation
- **Infra and data:** PostgreSQL, Supabase, pgvector, Docker, Google Cloud Run, Linux, Git

Contact: filipeazevedofilho@gmail.com · [LinkedIn](https://www.linkedin.com/in/filipebressanelli)
