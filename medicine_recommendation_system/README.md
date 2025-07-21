# Medicine Information Recommendation System

An AI-powered medicine recommendation system that helps users find appropriate medications based on their symptoms using natural language processing and retrieval-augmented generation (RAG) technologies.

## Problem Statement
Patients often struggle to find reliable medicine information for their symptoms, leading to confusion and inappropriate self-medication. Traditional internet searches return unreliable results, while medical databases are too technical for general users.

## Dataset
- **Medicine Database**: 11,000+ medications with comprehensive information (Kaggle)
- **URL**: https://www.kaggle.com/datasets/singhnavjot2062001/11000-medicine-details
- **Features**: Medicine name, composition, uses, side effects, manufacturer, reviews, images

## System Architecture

### Multi-Agent Framework
The system employs four specialized AI agents working in sequence:

1. **Grammar Corrector Agent**
   - Fixes spelling and grammar errors in user input
   - Uses Gramformer model for natural language correction
   - Ensures clear communication before processing

2. **Medicine Finder Agent**
   - Retrieves relevant medicines from vector database
   - Falls back to PubMed for additional medical literature
   - Uses semantic similarity search with HuggingFace embeddings

3. **Answer Generator Agent**
   - Converts structured data into user-friendly summaries
   - Generates natural language explanations
   - Maintains conversation context with memory

4. **Hallucination Checker Agent**
   - Validates generated content against source data
   - Detects and corrects unsupported claims
   - Ensures factual accuracy and reliability

### Technical Components

#### Retrieval System
- **Vector Database**: Chroma with HuggingFace embeddings
- **Semantic Search**: Similarity-based medicine matching
- **Fallback**: PubMed retriever for comprehensive coverage

#### Language Models
- **Primary LLM**: GPT-4o for high-quality text generation
- **Grammar Correction**: Gramformer for input preprocessing
- **Embeddings**: HuggingFace sentence transformers

## Key Features

### Intelligent Input Processing
- Automatic grammar and spelling correction
- Natural language understanding for medical terms
- Context-aware symptom interpretation

## Technical Stack

### Core Technologies
```python
langchain, crewai, transformers, sentence-transformers
chroma, gradio, gramformer, torch
```

### APIs & Services
- **OpenAI GPT-4o**: Primary language model
- **HuggingFace**: Embeddings and grammar correction
- **PubMed**: Medical literature fallback
- **LangSmith**: Monitoring and tracing

## Usage

### Basic Query Examples
```python
# Simple symptom
"fever"

# Medical condition
"diabetes"

# Simple medication
"pain killer
```
## Architecture Benefits

### Accuracy & Reliability
- Multi-agent validation prevents misinformation
- Source-grounded responses avoid hallucinations
- Fallback systems ensure comprehensive coverage

### Scalability
- Vector database enables fast similarity search
- Modular agent architecture for easy updates
- API-based services for reliable performance

### Target Users
- Patients seeking medicine information
- Healthcare students and professionals
- Caregivers managing medications
- General public for health education

---
*Note: This model is for research purposes. Clinical decisions should always involve qualified healthcare professionals.*
