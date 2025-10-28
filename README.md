# AI Chat Agent – Deep Learning Project (Spring 2025)

## 📘 Overview
This project is a **Deep Learning AI Agent** designed as part of the *Deep Learning Course – Spring 2025* at **Sharif University of Technology**.  
The project focuses on building an **intelligent conversational agent** using **Large Language Models (LLMs)** that can perform interactive, memory-based, and retrieval-augmented conversations, along with executing external functions and handling games.

---

## 🧠 Project Goals
The aim of this project is to **develop an intelligent chat-based AI agent** capable of:
- Maintaining **conversation history** and context over time.
- Using **Retrieval-Augmented Generation (RAG)** to improve answer quality.
- Integrating **live web search** for up-to-date information (via Exa API or similar).
- Supporting **function calling** to execute external tasks or fetch data.
- Handling **interactive tasks**, such as the *20 Questions Game*.
- Providing a **user-friendly GUI** using **Gradio** or **Streamlit**.

---

## 🚀 Project Phases and Components

### **1. Conversation History Management**
- Implemented a **context-aware chat system** using an LLM backbone (e.g., OpenAI, Hugging Face models).
- The system stores and retrieves previous conversation turns to maintain continuity.
- Uses **context window management** to summarize or truncate old messages when memory is full.

**Key Features:**
- Persistent memory (user-specific or session-based)
- Context summarization
- Dynamic context updates after each message

---

### **2. Retrieval-Augmented Generation (RAG)**
- Integrates external **document knowledge** using a **vector database**.
- Allows the model to answer questions based on PDFs or stored knowledge, not just its pre-trained data.

**Implementation Steps:**
1. Process and chunk PDF documents (e.g., using `PyMuPDF` or `pdfminer`).
2. Create **embeddings** using a model such as `all-MiniLM-L6-v2`.
3. Store embeddings in a **FAISS** index (`IndexFlatL2`).
4. During user queries:
   - Compute query embedding.
   - Retrieve top-k similar chunks.
   - Inject the retrieved text into the model prompt for context.
5. Generate an enriched response using the combined context.

---

### **3. Function Calling and Web Integration**
- The agent can automatically detect when a query requires **external information** or **function execution**.

**Capabilities:**
- Detects when to trigger a **web search** (e.g., via Exa API).
- Can call specific functions, such as retrieving weather, stock prices, or executing a computation.
- Automatically summarizes retrieved web results and injects them into the model.

**Example Flow:**
1. User asks: “What’s the weather in Tehran today?”
2. Agent classifies this as needing external data.
3. The system calls the web API.
4. The summarized result is provided back in natural language.

---

### **4. Game Interaction – “20 Questions”**
- Implements an interactive **20 Questions game** using a validation model.
- The agent asks up to 20 yes/no questions to guess a user-chosen word.

**Evaluation Script Example:**
```bash
python evaluate_20Q.py -N 100
```
This script measures how well the model identifies the target word through reasoning and question strategy.

---

### **5. Graphical User Interface (GUI)**
- Designed a simple and intuitive web interface using **Gradio** or **Streamlit**.
- The interface allows:
  - Text-based chat
  - File upload (for RAG documents)
  - Web search toggle
  - Game initiation button

**GUI Features:**
- Chat window with scrolling conversation history
- Real-time response updates
- Modular design for future features

---

## 🧩 Technologies Used
| Component | Technology |
|------------|-------------|
| Core Model | Large Language Model (e.g., OpenAI, Hugging Face Transformers) |
| Embeddings | `sentence-transformers/all-MiniLM-L6-v2` |
| Vector Search | FAISS (`IndexFlatL2`) |
| PDF Parsing | PyMuPDF / pdfminer |
| Frontend | Gradio / Streamlit |
| Web Search | Exa API / custom search API |
| Programming Language | Python 3.10+ |

---

## ⚙️ How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/AI_Agent_Project.git
   cd AI_Agent_Project
   ```
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Run the agent:
   ```bash
   python app.py
   ```
4. (Optional) Launch the GUI:
   ```bash
   streamlit run app.py
   # or
   gradio app.py
   ```

---

## 🤖 What the AI Agent Does
An **AI Agent** is an intelligent system built on top of an LLM that can:
- Understand and generate human-like text.
- Remember and reference past interactions.
- Retrieve and reason over external knowledge (via RAG).
- Execute functions or call APIs automatically.
- Interact dynamically — through chat, search, or games.

In short:  
> 🧠 The AI Agent acts as a **personal assistant** combining memory, knowledge retrieval, reasoning, and interactivity.

---

## 👩‍💻 Contributors
Developed as part of the **Deep Learning Course (Spring 2025)**  
**Instructor:** Dr. Bajand  
**Student:** [Your Full Name]
