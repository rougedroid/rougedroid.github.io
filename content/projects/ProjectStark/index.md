---
title: Project Stark
date: 2026-06-08
description: This project outlines a modular, multi-model AI system designed to automate PDF ingestion, semantic segmentation, and graph-based knowledge retrieval using specialized, lightweight ML components and a local LLM. Currently, the project is in its early stages with a partially functional Node Finder built on top of a common sense knowledge graph.
summary: This project outlines a modular, multi-model AI system designed to automate PDF ingestion, semantic segmentation, and graph-based knowledge retrieval using specialized, lightweight ML components and a local LLM. Currently, the project is in its early stages with a partially functional Node Finder built on top of a common sense knowledge graph.
tags:
  - AI-ML
  - RAG
  - graphdatabase
  - neo4j
  - python
  - dataprocessing
  - agentic-workflows
categories:
  - Programming
  - in-progress
---
## Project Intent
( Have a Jarvis-Like Personal AI Assistant which was truly intelligent, not a context wrapper on an LLM with RAG )

- Automate the ingestion and structural segmentation of dense PDF documents and other information sources into structured data.
- Dynamically connect common concepts across disparate documents within a unified graph database.
- Optimise retrieval speeds by using highly specialised, tiny ML models for single tasks instead of relying on a massive LLM for reasoning.
- Implement a fully local, privacy-first natural language interface using a small quantized LLM.
- Ultimately, make the tool truly user friendly and useable for day-to-day tasks as well as have it extract scientific information from PDF's and present them to teh user when queried. An additional goal is to include physical world simulation and true equation solving to make the tool capable enough to aid a researcher during work. 

## System Architecture

### Multi-Model Pipeline

The architecture shifts away from a single "all-knowing" model, breaking tasks down into dedicated micro-services:

- **PDF Segmenter:** An ML model optimised for document layout analysis that reads PDFs and splits them into semantic sections.
- **Graph Populator:** A specialised component that establishes conceptual nodes and edges from the segmented text into the graph database.
- **Data Router ML:** A specialised micro-model that translates user intent into graph database queries.
- **Command Classifier ML:** A dedicated model that determines the exact command/tool to use for a specific task. ( Eventually chain a bunch of commands together to execute entire tasks in the command line )
- **Physics Engine:** A dedicated model/segment meant to properly simulate the real world using a world model. 

### Interface & Orchestration

- **Local LLM:** A small, open-source local LLM acts exclusively as the user interface—translating natural language queries into an internal structure and formatting the final extracted graph data back into conversational text/audio.
- **Graph Database:** Serves as the central repository, connecting common concepts, definitions, and relationships extracted across all uploaded documents and interactions with the user and user feedback.

## Limitations

### ML Pipeline & Segmentation

- The node selector selecting the "correct" node from the graph database depends significantly on the "vector embedding" only since it is the most prominent feature of a correct node. This eliminates the need/effectiveness of having any ML model before selecting node. And, this model doesn't really pick the most contextually relevant node either. This is a fault in the CSKG graph, which stores only key words and basic relations. For the pusposes of this model, a RAG-like implementation is more sensible for fact queries, although a different system is required for allowing the system to "think" using the stored data as we do not want to use an LLM for reasoning. 

### Graph & Interface

- The system currently relies on a heavily hard coded "Node Finder" within a common sense knowledge graph rather than dynamic, generalised graph routing.
- The small local LLM occasionally hallucinates or loses track of the context when the retrieved graph payload is too large or complex.
## Project Outcomes

- Understood the Query flow systems required to orchestrate a multi-model AI Reasoning system. 
- Built a working prototype of a Node Finder capable of parsing a common sense knowledge graph.
- **Project is still under development. More Outcomes coming soon :)**

## Future Plan

- Meet the current goals properly
---
## Repositories
1. Project Stark ( current repo for core system, aka. master orchestrator ): https://github.com/rougedroid/ProjectStark
2. PDF Parser ( to be started ): like i said, to be started 
3. Basic ML Search ( initial attempt ): https://github.com/rougedroid/Basic-ML-SearchEngine
