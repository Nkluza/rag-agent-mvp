# RAG Agent MVP  

## Overview  
This app is a Retrieval‑Augmented Generation (RAG) chat system built with Next.js (App Router) and TypeScript. It answers questions using uploaded documents only. It uses OpenAI's Responses API with File Search (OpenAI‑managed vector stores) to retrieve relevant document snippets and generate answers.  

## Uploading Documents  
Uploaded documents should be placed in the `docs/` directory of this repository. When deployed, these PDFs will be ingested into an OpenAI vector store. Follow these steps:  
- Place your PDF files in the `docs/` folder.  
- Deploy the app; on startup it will upload PDFs to OpenAI and build a vector store.  
- The API uses `file_search` with the vector store to find relevant passages.  

## How RAG Works  
The `/api/ask` endpoint accepts a JSON body `{ "question": "..." }`. It uses the OpenAI Responses API with `file_search` enabled and attaches the project’s vector store containing your PDFs. The system prompt instructs the model to only use retrieved documents and cite sources. If the answer isn’t found, it will respond: “I don’t know based on the provided documents.”  

## Deployment  
To deploy on Vercel:  
1. Create a project in Vercel and import this GitHub repository.  
2. Set the `OPENAI_API_KEY` environment variable in your Vercel project settings.  
3. Deploy. The app will ingest files from `docs/` and be ready to answer questions.  

## Example Questions  
- "What is the summary of section 2 of my uploaded paper?"  
- "According to the policy document, when does coverage start?"  
- "I don’t know based on the provided documents." (when asked something not in the docs)
