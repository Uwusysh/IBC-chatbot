# 🧠 IBC Legal Research Assistant

The **IBC Legal Research Assistant** is a web-based AI chatbot designed to answer legal queries using acts, rules, and case laws from the Indian legal ecosystem. The application supports comprehensive multi-source searches and provides summarized responses with reference cases across various courts.

---

## 🚀 How It Works

### 1. **Data Preparation**

To load legal documents and case laws:

```bash
python diffchroma.py
```

* This script downloads and processes PDFs of Acts, Rules, and Case Laws.
* It creates a fresh Chroma vectorstore for each category.
* Existing databases (if any) are replaced to ensure consistency.

---

### 2. **Backend**

The backend is powered by **FastAPI** and serves API routes to answer queries using vector search.

#### Run the backend:

```bash
python check.py
```

* This script runs the FastAPI server, loading all collections (`acts`, `rules`, `supreme_court`, `high_court`, `nclat`, `nclt`).
* It exposes:

  * `POST /api/answer` – Answer legal questions across categories
  * `GET /api/collections` – Health check for available collections

Ensure it's running at: `http://localhost:8000`

---

### 3. **Frontend**

The frontend is a modern React app with a sleek 3-panel interface:

* **Acts & Rules**: Shows chatbot answers for statutory text.
* **Case Laws**: Displays matched cases from courts.
* **Case Details & Notes**: Lets users take notes, copy, or download them.

> 🔧 The UI will auto-detect backend availability and show real-time search status indicators.

---

## 📂 File Structure

```
.
├── diffchroma.py        # Downloads and loads PDFs into vector DB
├── check.py             # Runs the FastAPI backend
├── frontend/
│   └── IBChatbot.js     # Main React chatbot interface
```

---

## ✅ Features

* 🔎 Searches across Acts, Rules, and 4 courts (SC, HC, NCLT, NCLAT)
* 📚 Summarized, contextual legal answers
* 📋 Clipboard for saving answers/case summaries
* 📁 Notes download as `.txt`
* 💡 Responsive and interactive UI
* 🌐 React + FastAPI + LangChain + Chroma + LLM (Groq or compatible)

---

## 🛠️ Requirements

**Backend:**

* Python 3.8+
* FastAPI
* LangChain
* Chroma
* PDF libraries (e.g., PyMuPDF, pdfminer)

**Frontend:**

* Node.js + npm
* React

---

## 🧪 Local Setup

```bash
# Backend
pip install -r requirements.txt
python diffchroma.py
python check.py

# Frontend
cd frontend
npm install
npm start
```

Make sure both servers are running. Access the chatbot UI at `http://localhost:3000`.

---

## 📌 Note

* Always run `diffchroma.py` before starting the backend to ensure fresh and consistent document embeddings.
* The UI will reflect any backend connection issues.

---
