# Tweet Generator

An AI-powered tool that generates highly personalized and contextually relevant tweets by leveraging a sophisticated pipeline of machine learning components. This system is designed to emulate a specific persona's tone, style, and messaging, making it a powerful solution for persona-based tweet generation.

---

## Table of Contents
1. [Overview](#overview)
2. [Technical Architecture](#technical-architecture)
   - [1. Preprocessing](#1-preprocessing)
   - [2. Embedding and Semantic Search](#2-embedding-and-semantic-search)
   - [3. Hypothetical Document Embeddings (HyDe)](#3-hypothetical-document-embeddings-hyde)
   - [4. Advisor Module](#4-advisor-module)
   - [5. Final Inference](#5-final-inference)
3. [Key Features](#key-features)
4. [Tutorial: How to Extract Tweets Using Tweepy](#tutorial-how-to-extract-tweets-using-tweepy)
5. [References](#references)

---

## Overview
The Tweet Generator utilizes a multi-stage pipeline to produce tweets that reflect a specific persona's tone, phrasing, and communication style. By combining vector search, advanced language models, and innovative preprocessing techniques, the system ensures that the generated content is engaging, relevant, and aligned with the persona's narrative.

---

## Technical Architecture

### 1. Preprocessing
- **Dataset:** The system starts with a corpus of over 50,000 Donald Trump tweets.
- **LLM-Based Classification:** Each tweet is analyzed and categorized by tone, context, and relevance using a large language model (LLM).
- **Filtering:** This step narrows the dataset to a smaller, high-quality subset of contextually rich tweets, ensuring precise and fluent output.

---

### 2. Embedding and Semantic Search
- **Vector Database:** FAISS (Facebook AI Similarity Search) is used to store and retrieve tweets as high-dimensional vector embeddings.
- **Embedding Model:** Tweets are embedded using OpenAI’s `text-embedding-3-large` model.
- **Semantic Retrieval:** The system retrieves tweets based on contextual similarity, enabling in-context learning and few-shot examples for enhanced generation.

---

### 3. Hypothetical Document Embeddings (HyDe)
- **LLM Inference Step:** Before semantic search, the system generates hypothetical tweets based on the input context.
- **Purpose:** These intermediary examples enrich the search process and improve retrieval precision by introducing additional contextual signals.
- **Implementation:** Hypothetical tweets are embedded and used to query the FAISS database, increasing accuracy in tweet selection.

---

### 4. Advisor Module
- **Role:** This LLM-driven component refines the output by generating structured talking points aligned with the persona's established stances.
- **Dynamic Adjustment:** Talking points are tailored to match the context of the input content, ensuring consistent messaging across different themes.

---

### 5. Final Inference
- **Combining Inputs:** The system integrates:
  - Curated talking points.
  - Semantically similar tweet examples.
  - User-defined parameters (tone, creativity, etc.).
- **LLM Inference:** A final inference call compiles these cues into a cohesive, personalized tweet that captures the persona’s tone, style, and intent.

---

## Key Features
- **FAISS-Based Vector Search:** Efficient retrieval of semantically similar tweets using advanced embedding models.
- **HyDe Enhancement:** Hypothetical Document Embeddings to enrich context and precision.
- **Advisor Module:** Persona-specific refinement for dynamic and consistent messaging.
- **High Personalization:** User-defined parameters for tone, creativity, and style.

---

## Tutorial: How to Extract Tweets Using Tweepy

Follow these steps to extract tweets from a user using the Tweepy library:

### 1. **Install Tweepy**
Install Tweepy using pip:
```bash
pip install tweepy
```

### 
2. Set Up a Twitter Developer Account
- Sign up at the [Twitter Developer Platform](https://developer.x.com/en).
- Create a new project and generate your API keys and access tokens.

