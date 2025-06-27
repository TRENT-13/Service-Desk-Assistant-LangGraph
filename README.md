# Service Desk Assistant with RAG System

A comprehensive AI-powered service desk assistant built with LangChain, Google Gemini, and FAISS vector search. This system provides intelligent ticket management, contextual information retrieval, and automated support with built-in hallucination detection and performance benchmarking.

## Features

### Intelligent Ticket Management
- **Create Tickets**: Automatically generate support tickets with unique IDs and timestamps
- **Update Status**: Modify ticket status (New, Pending, Investigating, Resolved)
- **Search by ID**: Find specific tickets using ticket numbers
- **Search by Description**: Semantic search through ticket descriptions
- **Date Range Queries**: Filter tickets by creation date ranges

### Advanced AI Capabilities
- **Intent Classification**: Automatically categorizes user queries for optimal routing
- **Query Expansion**: Enhances search queries with synonyms and related terms
- **Hallucination Detection**: Validates AI responses for accuracy and relevance
- **Context-Aware Responses**: Retrieves relevant information from knowledge base

### RAG (Retrieval-Augmented Generation) System
- **Vector Search**: FAISS-powered semantic search across tickets and documents
- **Multi-Modal Knowledge Base**: Supports tickets, policies, and product information
- **Similarity Thresholding**: Configurable relevance filtering
- **Document Chunking**: Intelligent text splitting for optimal retrieval

### Performance Benchmarking
- **Response Time Analysis**: Comprehensive performance metrics
- **Success Rate Monitoring**: Track system accuracy and reliability
- **Statistical Reporting**: Mean, median, percentile analysis
- **Visual Analytics**: Automated performance plots and charts

## 🛠Technology Stack

- **AI/ML**: Google Gemini 2.0 Flash, LangChain, HuggingFace Transformers
- **Vector Database**: FAISS (Facebook AI Similarity Search)
- **Embeddings**: Sentence Transformers (all-mpnet-base-v2)
- **Memory Management**: Conversation buffer with sliding window
- **Data Processing**: Pandas, NumPy, Matplotlib
- **File Management**: Text-based storage with automatic persistence

## Prerequisites

```bash
pip install langchain
pip install langchain-openai
pip install langchain-google-genai
pip install langchain-community
pip install faiss-cpu
pip install sentence-transformers
pip install matplotlib
pip install numpy
pip install python-dateutil
```

## Quick Start

### 1. Environment Setup

```python
# Set your Google API key
google_api_key="your-google-api-key-here"
```

### 2. Initialize the System

```python
from your_module import setup_docstore, create_agent, run_llm

# Initialize document store and agent
docstore = setup_docstore("generated_tickets.txt", "./data/generated_tickets.txt")
agent = create_agent()

# Start interactive session
run_llm()
```

### 3. Basic Usage Examples

```bash
# Create a new ticket
> I need to report a printer issue - the office printer is not responding

# Search for tickets
> Show me all tickets about network problems

# Update ticket status
> Change ticket 10001 to Resolved

# Find specific ticket
> What's the status of ticket 10001?

# Date range search
> Show me tickets from 2024-01-01 to 2024-01-31
```

## Project Structure

```
service-desk-assistant/
├── data/
│   ├── generated_tickets.txt    # Ticket storage
│   ├── policies.txt            # Policy documents
│   ├── product_data.txt        # Product information
│   └── chat_history.txt        # Conversation history
├── benchmark_results/          # Performance analysis output
├── main.py                     # Core application logic
└── README.md                   # This file
```

## Core Components

### RAGDocStore
Manages vector-based document storage and retrieval:
- **Ticket Store**: Semantic search through support tickets
- **Policy Store**: Company policies and procedures
- **Information Store**: Product documentation and guides

### TicketTool
Handles all ticket-related operations:
- Auto-incrementing ticket IDs
- Status management
- Multi-criteria search capabilities
- Date range filtering

### Intent Classification
Automatically routes queries to appropriate handlers:
- `ticket_creation`: New ticket requests
- `ticket_information_retrieval`: Search and status queries
- `ticket_status_change`: Status update requests
- `general_inquiry`: Open-ended questions

### Hallucination Detection
Validates AI responses using a secondary verification step:
- Compares generated answers against original queries
- Handles temporal query validation
- Provides confidence scoring for responses

## Benchmarking System

Run performance analysis with built-in benchmarking tools:

```python
from your_module import run_benchmark_suite

# Execute comprehensive benchmark
benchmark = run_benchmark_suite(docstore, ticket_tool, context_tool, agent)
```

### Benchmark Metrics
- **Response Time Analysis**: Mean, median, percentiles
- **Success Rate Tracking**: Query resolution accuracy
- **Error Monitoring**: Exception tracking and analysis
- **Search Performance**: Relevance and speed metrics

##  Configuration

### Vector Search Parameters
```python
# Similarity threshold for ticket search
threshold = 1.35  # Lower = more strict matching

# Embedding model configuration
embeddings = HuggingFaceEmbeddings(
    model_name="sentence-transformers/all-mpnet-base-v2",
    model_kwargs={'device': 'cpu'}
)
```

### Memory Management
```python
# Conversation buffer size
memory = ConversationBufferWindowMemory(
    k=10,  # Remember last 10 interactions
    memory_key="chat_history",
    return_messages=True
)
```

## Advanced Features

### Custom Query Expansion
The system automatically expands search queries with related terms:
```python
# Input: "printer problem"
# Expanded: "printer issue, printing malfunction, printer offline, print queue stuck, printer driver error..."
```

### Intelligent Ticket Validation
Prevents invalid ticket creation with built-in validation:
- Filters out personal/non-work related issues
- Validates technical problem descriptions
- Maintains professional ticket standards

### Multi-Modal Search
Supports searching across different data types:
- Historical tickets
- Policy documents
- Product information
- Combined multi-source results

## Performance Optimization

### Vector Store Optimization
- Efficient similarity search with FAISS
- Configurable similarity thresholds
- Batch document processing

### Memory Management
- Sliding window conversation memory
- Persistent chat history storage
- Optimized context retrieval

## Acknowledgments

- **Google Gemini** for advanced language model capabilities
- **LangChain** for the comprehensive AI framework
- **FAISS** for efficient vector similarity search
- **HuggingFace** for transformer models and embeddings
