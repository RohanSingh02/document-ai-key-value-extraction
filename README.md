# document-ai-key-value-extraction
invoice-Document AI key-value extraction using LayoutLMv3 
# Project Overview
This project implements a scalable Document AI pipeline for extracting structured key-value information from document images using layout-aware deep learning.
Although the final goal is invoice information extraction, the architecture is intentionally designed to be document-agnostic, allowing it to generalize to invoices, receipts, forms, and contracts.
The system uses LayoutLMv3 for token classification, leveraging text + spatial layout information to accurately extract fields without relying on hard-coded rules or regex.
# Problem Statement
Extract structured information (key-value pairs) from document images
Build a scalable model that can be trained for any field
Avoid document-specific or template-specific logic
Output machine-readable structured data (JSON)
# Solution Approach
The problem is modeled as a token-level classification task
Each word in the document is classified as:\
QUESTION\
ANSWER\
HEADER\
or O (outside)\
This approach allows the model to learn relationships between keys and values, rather than just detecting keywords.
# Architecture
Document Image ->
     
OCR / Dataset-provided Text & Bounding Boxes ->
     
LayoutLMv3 Token Classification ->
     
Post-processing (Label Grouping) ->
     
Structured JSON Output
# Tech Stack
Python,
Hugging Face Transformers,
LayoutLMv3,
PyTorch,
Hugging Face Datasets,
Google Colab.
# Dataset Used
FUNSD – Form Understanding Dataset
Platform: Hugging Face
Link: https://huggingface.co/datasets/nielsr/funsd
## Why FUNSD?
Provides word-level annotations
Includes bounding boxes, which are required for layout-aware models
Labels follow a key-value structure
Ideal for token classification
Although FUNSD contains forms, the same architecture applies directly to invoices, because:
Invoices and forms are both semi-structured documents where meaning depends on layout and context.
# Scalability Advantage
<ins>The main objective of this project was scalability, not invoice-specific rule extraction.
Using FUNSD enables scalability in the following ways:
No hard-coded rules\
No invoice-specific assumptions
### New fields can be added by:
Defining new labels\
Providing annotated examples\
Retraining the model
### Example Extensions :
Invoices\
Receipts\
Contracts\
KYC Forms\
Bank Statements
# Future Improvements
Line-item table extraction\
Domain-specific fine-tuning for invoices\
REST API using FastAPI\
Frontend demo for document upload
# Key Takeaway
This project demonstrates how modern Document AI systems are built in industry:
Layout-aware\
Scalable\
Model-driven\
Production-ready
# Author
Rohan Singh\
B.Tech CSE (AI & ML)






