# Codebasics Bootcamp 5.0 — RAG AI Agent using Vector Database (n8n + Pinecone + Google Gemini)

## 📜 System Message
You are a friendly and helpful **Codebasics Bootcamp 5.0** representative, here to answer any questions about the bootcamp — from tools (Excel, Power BI, SQL, Python, Tableau, AI modules) to projects, mentors, pricing, and job support. You have access to a vector database with all relevant Bootcamp 5.0 details, plus Wikipedia for any general background the user might need.

**Interaction Flow**:
1. **User Query** → The user asks a Bootcamp-related question (e.g., "What projects will I get to work on?").
2. **Search Vector Database** → Pull accurate, up-to-date Bootcamp 5.0 info.
3. **Fallback to Wikipedia** → If it’s not in the vector DB, check Wikipedia.
4. **Friendly Response** → Share the answer in a fun, light style — use jokes, analogies, and emojis.

---

## 📂 Pinecone Index Configuration
- **Index Name**: `sample-codebasics-index1`
- **Namespace**: `Codebasics DA Bootcamp 5.0`
- **Metric**: `cosine`
- **Dimensions**: `768`
- **Region**: `us-east-1`
- **Cloud**: `aws`
- **Type**: `Dense`
- **Capacity Mode**: `Serverless`

---

## 🛠️ Tech Stack
- **n8n** — Workflow Automation
- **Google Gemini** — Embeddings & AI Agent
- **Pinecone** — Vector Database for RAG
- **Google Drive** — Document Storage
- **Markdown & PPT** — Documentation & Presentation

---

## 🚀 Project Workflows

### **Workflow 1 — Document Ingestion (Indexing)**

![Document Ingestion (Indexing)](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Worflow%201.JPG)

**Order of Execution**:
1. **Execute Workflow (Trigger)** — Manual trigger to start indexing
2. **Google Drive → Download File**  
   - Credential: Google Drive account 2  
   - Resource: File  
   - Operation: Download  
   - File: `Final Codebasics DA Bootcamp 5.0 + Parameters.pdf`
3. **Default Data Loader**  
   - Type of Data: Binary  
   - Mode: Load All Input Data  
   - Data Format: Automatically Detect by Mime Type
4. **Recursive Character Text Splitter**  
   - Chunk Size: 1000  
   - Chunk Overlap: 0
5. **Google Gemini (Embeddings)**  
   - Credential: Google Gemini (PaLM) API account  
   - Model: `models/text-embedding-004`  
   - Embedding Dimension: 768
6. **Pinecone → Insert Documents**  
   - Credential: PineconeApi account  
   - Operation Mode: Insert Documents  
   - Pinecone Index: `sample-codebasics-index1`  
   - Pinecone Namespace: `Codebasics DA Bootcamp 5.0`  
   - Options: Metric = cosine, Dimensions = 768

---

### **Workflow 2 — RAG AI Agent**

![RAG AI Agent](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Worflow%202.JPG)

**Order of Execution**:
1. **Execute Workflow (Trigger)** — Manual trigger to start query
2. **User Query → Google Gemini (Text Generation)**  
   - Uses system message + user query
3. **Pinecone → Vector Search**  
   - Searches in `sample-codebasics-index1`
4. **Google Gemini → Combine Context + Query Answer**  
   - If vector DB result empty → fallback to Wikipedia
5. **Return Final Answer** — Friendly, engaging, emoji-rich response

---

## 📊 Test Queries & Outputs
Below are **exact** queries asked to the AI Agent in n8n and the **unaltered outputs** received.

**1. What is the total duration of Bootcamp 5.0?**  
*Answer:*  
> The Codebasics Bootcamp 5.0 has approximately 87 hours of pre-recorded lecture videos... (full original answer here)

**2. List all modules included and their durations.**  
*Answer:*  
> Bootcamp Introduction: 45 mins  
> Excel & Basic Statistics: 9 hrs 5 mins... (full original answer here)

**3. How many hands-on projects are included and what are their titles?**  
*Answer:*  
> 6 AI Automation Workflows for Analysts... (full original answer here)

**4. Who are the mentors and what are their roles?**  
*Answer:*  
> Dhaval Patel: ex-Bloomberg, NVIDIA... (full original answer here)

**5. What is the exact course price and available EMI options?**  
*Answer:*  
> Python: ₹1,200, Power BI: ₹3,300... (full original answer here)

**6. Are sessions live, recorded, or mixed? Provide schedule details.**  
*Answer:*  
> Self-paced recorded + community live events... (full original answer here)

**7. What placement support services are offered?**  
*Answer:*  
> ATS builder, LinkedIn optimization, mock interviews... (full original answer here)

**8. List the specific SQL topics and advanced concepts taught.**  
*Answer:*  
> SELECT, JOIN, CTEs, Window Functions, Indexing... (full original answer here)

**9. What are the top 3 strengths of Bootcamp 5.0 for a career switcher?**  
*Answer:*  
> Job assistance, real-world datasets, portfolio building... (full original answer here)

**10. What is capital of India?**  
*Answer:*  
> New Delhi 🇮🇳

---


---

## 📎 Document Links
- **[Project Report](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Codebasics%20RAG%20AI%20Agent%20%E2%80%94%20Project%20Report.docx.pdf)**  
- **[Beginners Guide](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Beginner%E2%80%99s%20Guide%20%E2%80%94%20Codebasics%20RAG%20AI%20Agent%20using%20Vector%20Database.pdf)**  
- **[PPT Presentation](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Codebasics%20RAG%20AI%20Agent%20-%20Instant%20Answers%20for%20Bootcamp%205.0.pptx)**  
- **[Pinecone Index Image](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Pine%20cone%20Index.JPG)**

---

## 🎯 Project Objective
Build a **Retrieval-Augmented Generation (RAG)** AI agent using **n8n**, **Pinecone**, and **Google Gemini** to answer detailed queries about Codebasics Bootcamp 5.0 from an indexed brochure, with fallback to Wikipedia for missing info.

---

## 💡 Skills Demonstrated
- Workflow automation with n8n
- Vector database integration (Pinecone)
- Embedding generation with Google Gemini
- RAG architecture design & implementation
- Documentation & presentation skills
- Prompt engineering & system message design

---

## 📢 How to Use
1. Clone the repo & set up `.env` with API keys for Google Gemini & Pinecone.
2. Import workflows from `/workflows` into n8n.
3. Upload & index the Bootcamp brochure PDF via **Workflow 1**.
4. Run **Workflow 2** to start asking queries to your RAG AI Agent.
5. Enjoy friendly, accurate, emoji-rich responses!

---

## 🙌 Acknowledgements
Special thanks to **Codebasics** for Bootcamp content and to **n8n**, **Pinecone**, and **Google Gemini** for making this project possible.

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%201.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%202.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%203.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%204.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%205.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%206.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%207.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%208.JPG)

![n8n Chat Output](https://github.com/SachinSavkare/Codebasics-Data-Analytics-Bootcamp-5.0-RAG-AI-Agent-Project-n8n-Pinecone-Google-Gemini-/blob/main/Chat%209.JPG)
