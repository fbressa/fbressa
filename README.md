# Filipe Bressanelli

Software Engineering student at the University of Brasília (UnB), working on AI systems that run in production.

## DORSAL · AI service for a football shirt recommerce platform
EngNet, for an international client · Python · FastAPI · SigLIP 2 · pgvector · Gemini · Supabase · Google Cloud Run

Identifies a shirt from photos in two steps: SigLIP 2 embeddings searched with pgvector over 1,786 reference photos, then a Gemini step that picks the kit and returns structured fields with per-field confidence. The same pipeline produces a condition assessment used in pricing.

- Cold start failures from 13/40 to 0/40, median latency from 29.1 s to 17.2 s, container image from 7.9 GB to 4.8 GB
- Pagination fix that made 99 hidden kits visible to the service
- 33 attribute tests and a regression run against the live models before each release

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
