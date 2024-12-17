Overview
This project implements a Retrieval-Augmented Generation (RAG) pipeline to enable interactive querying and information extraction from semi-structured data in multiple PDF files. Users can upload PDFs, ask natural language questions, and perform complex tasks such as comparisons or extracting structured data. The system leverages state-of-the-art Large Language Models (LLMs) for generating responses while ensuring accuracy by grounding them in the content retrieved from the uploaded PDFs.

Functional Requirements
1. Data Ingestion
Input: PDF files containing semi-structured data.
Process:
Extract Text: Use a PDF processing tool to extract raw text and relevant structured information from uploaded files.
Segment Text: Split the extracted content into logical chunks for better granularity and efficient retrieval.
Embed Text: Convert these chunks into dense vector embeddings using a pre-trained embedding model (e.g., sentence-transformers/all-MiniLM-L6-v2).
Store Embeddings: Save these embeddings in a vector database (e.g., FAISS) for similarity-based retrieval.

3. Query Handling
Input: A natural language question from the user.
Process:
Convert the user query into a vector embedding using the same embedding model.
Perform a similarity search in the vector database to retrieve the most relevant chunks of text.
Pass the retrieved chunks along with the query to the LLM for generating a detailed response.

4. Comparison Queries
Input: User query requesting a comparison of specific attributes or metrics across multiple PDF files.
Process:
Identify and extract the terms or fields to be compared from the query.
Retrieve relevant chunks from the vector database that contain comparable data.
Aggregate the extracted data for comparison.
Generate a structured response (e.g., a table or bullet-point summary) using the LLM.

5. Response Generation
Input: User query and the relevant information retrieved from the vector database.
Process:
Use the LLM to generate a detailed, context-aware response.
Ensure the response is grounded in retrieved data to improve factuality and reliability.
Incorporate exact values and structured formats, such as bullet points or tables, where necessary.
