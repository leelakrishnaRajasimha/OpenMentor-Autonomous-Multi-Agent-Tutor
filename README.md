# Intelligent Multi-Agent Study System¶
* Capstone Project: KAGGLE 5-Day Intensive AI Agents Course By GOOGLE.
* Author: Leelakrishna Rajasimha Yadav Doddakula

Date: 26 November 2025

# Implementation
- Notebook (code + graphs): [openmentor-autonomous-multi-agent.ipynb](openmentor-autonomous-multi-agent-tutor.ipynb)

# Project Overview
This project implements a multi-agent system designed to act as a personal study assistant. The goal was to build a system where multiple specialized agents cooperate to teach a subject, rather than using a single script.

I chose to implement this using an event-driven architecture because it allows the agents (Retriever, Explainer, Planner) to work independently without blocking the main program execution.

# System Architecture
The system uses Python's threading and queue modules to handle asynchronous communication between agents.

# Agent Workflow
1. Retriever Agent: Searches the in-memory vector store for relevant text chunks based on the user's query.
2. Explainer Agent: Takes the retrieved context and generates a summarized explanation.
3. Planner Agent: Creates a study schedule based on the requested topic.
4. QuizBot Agent: Generates questions to test the user's understanding and calculates a score.

# Requirements Implemented
This project covers 5 key concepts from the course curriculum:

# How to Run
Click "Run All" to execute the notebook. The script will:

1. Initialize the agent system.
2. Ingest the sample Calculus knowledge base.
3. Run a simulation where the agents explain "Definite Integrals" and create a study plan.
4. Generate a performance graph at the end.

# Agent Architecture Diagram

### Agent Architecture Diagram
``````mermaid
flowchart TD
%% Styling Definitions
classDef user fill:#f9f,stroke:#333,stroke-width:2px,color:black
classDef orch fill:#e1bee7,stroke:#8e24aa,stroke-width:2px,color:black,rx:10px,ry:10px
classDef agent fill:#e1f5fe,stroke:#0288d1,stroke-width:2px,color:black,rx:5px,ry:5px

%% Nodes
U(👤 User):::user
O[⚙ Orchestrator]:::orch
R[🔍 Retriever]:::agent
E[🧠 Explainer]:::agent
P[📅 Planner]:::agent
Q[🤖 QuizBot]:::agent

%% Flow
U -->|Query| O
O -->|Delegate| R
R -->|Context| E
E -->|Explanation| O
    
O -->|Request| P
P -->|Plan| O
    
O -->|Start| Q
Q -->|Grade| O
``````

# System Evaluation & Performance Analysis
The visualization above demonstrates the system's ability to evaluate the user, not just teach.

* Pie Chart: Shows that the QuizBot successfully compared the student's input against the answer key and calculated a grade (100% Accuracy).
* Study Plan: The output confirms that the Planner Agent successfully generated a schedule specific to Calculus (Integration formulas), proving that the context-aware logic is functioning correctly.

# Future Roadmap & Improvements
To scale this prototype into a production-grade system, the following features are planned:

1. Real LLM Integration: Replace mock_llm_call with the live Gemini 3.0 Flash API for dynamic reasoning.
2. Vector Database Upgrade: Migrate from in-memory lists to FAISS or Pinecone for handling millions of documents.
3. Multi-Modal Support: Allow the Retriever to ingest PDF diagrams and YouTube lecture transcripts.
4. Voice Interface: Integrate Whisper for Speech-to-Text, allowing students to speak to the tutor.
5. Emotional Intelligence: Add a sentiment analysis layer to detect student frustration and adjust the teaching tone.

# Real-World Logic Validation (AI Studio)
To verify the multi-agent logic before coding, I tested the prompt engineering in Google AI Studio using Gemini 2.0 Flash.

Step 1: Input & Retrieval
The system receives the Calculus query and the Retriever Agent isolates key concepts.

https://i.ibb.co/Z6txZL7X/Screenshot-2025-11-26-164903-Copy.png

Step 2: Explanation & Strategy
The Explainer Agent teaches the concept, followed by the Planner Agent creating a schedule.

https://i.ibb.co/8gFYC595/Screenshot-2025-11-26-165149.png

Step 3: Assessment
The QuizBot Agent generates a custom quiz to verify the student's mastery.

https://i.ibb.co/0jbCPFXX/Screenshot-2025-11-26-170608.png.
