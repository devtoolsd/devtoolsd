---
name: LangChain
slug: langchain
language: python
description: Framework for building LLM-powered applications — chains, agents, retrieval-augmented generation, and tool use.
logo: https://langchain.com/static/images/branding/langchain-logo-full-dark.svg
website: https://langchain.com
github: langchain-ai/langchain
year: 2022
pricing: free
open_source: true
license: MIT
tool_type: data
tags: [ai, llm, rag, agents, tools, python, generative-ai]
related_frameworks: [langraph, llama-index]
features:
  - "Prompt templates with variable substitution and few-shot examples"
  - "LCEL (LangChain Expression Language) for composing chains with `|` operator"
  - "Retrieval-augmented generation (RAG) pipeline components"
  - "Agent framework — LLM decides which tool to call next"
  - "Integrations: OpenAI, Anthropic, Ollama, Cohere, 50+ LLM providers"
  - "Vector store integrations: Chroma, Pinecone, pgvector, Weaviate"
  - "Memory — conversation history, summary, entity tracking"
  - "LangSmith for tracing, debugging, and evaluating chains"
install:
  pip: "pip install langchain langchain-openai"
---

LangChain provides composable building blocks for LLM applications — prompt templates, retrieval pipelines, tool-calling agents, and memory. Its integration library connects to OpenAI, Anthropic, local models, vector databases, and dozens of data sources. LangGraph extends it with stateful, graph-based agent orchestration for more complex multi-step AI workflows.

## Quick start

```bash
pip install langchain langchain-openai python-dotenv
```

```python
# .env
# OPENAI_API_KEY=sk-...

import os
from dotenv import load_dotenv
from langchain_openai import ChatOpenAI
from langchain.prompts import ChatPromptTemplate
from langchain.schema.output_parser import StrOutputParser

load_dotenv()

# Simple chain
llm = ChatOpenAI(model="gpt-4o-mini")
prompt = ChatPromptTemplate.from_template("Tell me a fun fact about {topic}.")
chain = prompt | llm | StrOutputParser()

result = chain.invoke({"topic": "Python"})
print(result)
```

```python
# RAG pipeline
from langchain_community.document_loaders import TextLoader
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain_openai import OpenAIEmbeddings
from langchain_community.vectorstores import Chroma
from langchain.chains import RetrievalQA

# Load and split documents
loader = TextLoader("knowledge_base.txt")
docs = loader.load()
splitter = RecursiveCharacterTextSplitter(chunk_size=1000, chunk_overlap=100)
chunks = splitter.split_documents(docs)

# Create vector store
vectorstore = Chroma.from_documents(chunks, OpenAIEmbeddings())

# Build QA chain
qa = RetrievalQA.from_chain_type(
    llm=ChatOpenAI(model="gpt-4o-mini"),
    retriever=vectorstore.as_retriever(search_kwargs={"k": 3}),
)

answer = qa.invoke("What is the refund policy?")
print(answer["result"])
```

## When to use

LangChain is the most feature-complete framework for LLM applications and the best choice when you need pre-built integrations for vector stores, data loaders, and LLM providers. It's well-suited for RAG pipelines and tool-using agents. For simpler use cases, calling the LLM API directly with a prompt template may be sufficient. For complex stateful agent graphs, LangGraph is the recommended extension. LlamaIndex is a strong alternative with a focus on data indexing and retrieval.
