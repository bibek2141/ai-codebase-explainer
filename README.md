# ai-codebase-explainer
AI Codebase Simplifier
AI Codebase Simplifier is a developer tool that analyzes a repository and explains how the codebase works.
It uses embeddings and retrieval-augmented generation (RAG) to answer questions about large codebases and generate architecture summaries.

The goal is to help developers understand unfamiliar repositories faster.

Features
Repository Analysis

Import a GitHub repository and automatically analyze its structure.

AI Code Explanation

Ask questions about the codebase and receive contextual answers.

Example questions:

Where is authentication implemented?
How does the order flow work?
Which services handle payments?
Architecture Summary

Generate a high-level overview of the system architecture.

Example output:

Controllers
↓
Services
↓
Repositories
↓
Database
File-Level Explanation

Click any file and get a plain-English explanation of what the file does.

Feature Locator

Quickly find where specific functionality exists within the repository.

Architecture

The system uses a Retrieval-Augmented Generation (RAG) pipeline.

Repository
↓
Code Parsing
↓
Code Chunking
↓
Embedding Generation
↓
Vector Database
↓
Semantic Retrieval
↓
LLM Explanation

When a user asks a question:

The question is converted into an embedding.

The vector database retrieves relevant code chunks.

The AI model generates an explanation based on those snippets.

Tech Stack

Backend

.NET Web API

Frontend

Angular

Database

PostgreSQL + pgvector

AI

LLM API (Claude / OpenAI)
Embeddings API

Infrastructure

Docker
Cloud deployment
Project Structure
CodebaseSimplifier
│
├── Controllers
│   RepoController.cs
│   ChatController.cs
│
├── Services
│   GitHubService.cs
│   CodeParserService.cs
│   EmbeddingService.cs
│   VectorSearchService.cs
│   AiService.cs
│
├── Models
│   CodeChunk.cs
│   ChatRequest.cs
│
├── Data
│   PostgresContext.cs
How It Works
1. Repository Import

Users provide a GitHub repository URL.

The system clones the repository and scans the source files.

2. Code Chunking

Files are split into logical chunks such as:

Classes
Methods
Functions

This allows the system to process large repositories efficiently.

3. Embedding Generation

Each code chunk is converted into a vector representation using an embeddings model.

4. Vector Storage

Embeddings are stored in a vector database for semantic search.

5. Question Answering

When a user asks a question:

Question
↓
Embedding
↓
Vector Search
↓
Relevant Code
↓
AI Explanation
Example Query

User input

Explain how authentication works.

AI output

Authentication is handled in AuthService.cs.

Flow:
LoginController → AuthService → JwtTokenGenerator
Future Improvements

Architecture diagram generation
Pull request summarization
Dependency graph visualization
Multi-language repository support
IDE integration

Use Cases

Developer onboarding

Understanding legacy codebases

Exploring unfamiliar repositories

Documentation generation

Running the Project

Clone the repository

git clone https://github.com/yourname/codebase-simplifier

Run backend

dotnet run

Run frontend

npm install
npm start
