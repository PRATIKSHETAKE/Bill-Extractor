# ⚡ Electricity Bill Extraction & Automation System

## 🚀 Overview

This project is an end-to-end automation tool that extracts structured data from electricity bills (images/PDFs) using AI and stores it in a centralized dataset.

It supports:

* 📄 Single file upload
* 📂 Multiple file upload
* 🗂️ Batch processing via folder path
* 📊 Automatic CSV generation

The system is built using:

* **FastAPI** (backend API)
* **Bootstrap** (frontend UI)
* **Gemini Multimodal AI** (data extraction)

---

## 🎯 Problem Statement

Manually extracting data from electricity bills is:

* Time-consuming (15–30 minutes per bill)
* Error-prone
* Not scalable

This tool automates the process:

> Upload bill → Extract data → Store in structured format

---

## 🧠 Solution Approach

### 🔥 AI-Based Extraction (Gemini)

Instead of traditional parsing, this system uses **Gemini Multimodal AI** to:

* Read images and PDFs directly
* Understand document layout
* Extract structured information

Fields extracted:

* Consumer ID
* Customer Name
* Billing Date
* Units Consumed
* Total Amount
* Due Date

---

## 🔍 OCR vs AI (Design Decision)

### 🧪 OCR-Based Approach (Tesseract)

I initially explored using OCR.

**How it works:**

* Converts image → raw text
* Requires regex/rule-based extraction

**Limitations:**

* ❌ No layout understanding
* ❌ Sensitive to image quality
* ❌ Frequent character errors
* ❌ Requires custom rules for each bill format
* ❌ Not scalable

---

### 🧠 Gemini Multimodal Approach (Final Choice)

Gemini directly processes images and understands context.

**Advantages:**

* ✅ Works across different bill formats
* ✅ No rule-based parsing required
* ✅ Better accuracy
* ✅ Faster development
* ✅ Handles semi-structured documents

---

### ⚖️ Final Decision

OCR was tested but not used as the primary method.

👉 The system uses **Gemini as the main extraction engine**, with OCR considered only as a fallback.

---

### 💡 Key Insight

> OCR extracts text.
> Gemini understands documents.

---

## 🏗️ System Architecture

```text id="arch1"
User Input (File / Multiple / Folder)
                ↓
        FastAPI Backend
                ↓
     Gemini Multimodal API
                ↓
       Structured JSON Output
                ↓
        CSV Append Storage
                ↓
         Frontend Display
```

---

## 📁 Project Structure

```text id="struct1"
bill-extractor/
│
├── app.py
├── config.py
├── batch_processor.py
├── requirements.txt
│
├── extractor/
│   └── gemini_extractor.py
│
├── utils/
│   └── csv_writer.py
│
├── frontend/
│   └── index.html
│
├── output/
│   └── all_bills.csv
│
├── uploads/
└── .env
```

---

## ⚙️ Features

### ✅ 1. AI-Based Data Extraction

* Uses Gemini multimodal model
* Extracts structured fields from bills

---

### ✅ 2. Unified API

**Endpoint:**

```http id="api1"
POST /extract-bill
```

Supports:

* Single file upload
* Multiple file upload
* Folder path processing

---

### ✅ 3. Batch Processing

Process entire folders automatically:

```text id="batch1"
Folder → Loop → Extract → Append CSV
```

---

### ✅ 4. CSV Storage

All extracted data is stored in:

```text id="csv1"
output/all_bills.csv
```

Includes:

* File name
* Extracted fields
* Duplicate handling

---

### ✅ 5. Frontend UI (Bootstrap)

* Upload files
* Enter folder path
* View results
* Clean interface

---

## 🛠️ Setup Instructions

### 🔹 1. Clone Project

```bash id="clone1"
git clone <your-repo-url>
cd bill-extractor
```

---

### 🔹 2. Create Virtual Environment

#### Windows:

```bash id="venv1"
python -m venv venv
venv\Scripts\activate
```

#### Mac/Linux:

```bash id="venv2"
python3 -m venv venv
source venv/bin/activate
```

---

### 🔹 3. Install Dependencies

```bash id="deps1"
pip install -r requirements.txt
```

If no requirements file:

```bash id="deps2"
pip install google-generativeai pandas fastapi uvicorn python-dotenv openpyxl pillow
```

---

## 🔑 Gemini API Key Setup

This project requires a **Gemini API Key**.

### Step 1: Go to Google AI Studio

https://aistudio.google.com/

### Step 2: Sign In

Login with your Google account

### Step 3: Create API Key

* Click **Get API Key**
* Click **Create API Key**
* Copy the key

---

### Step 4: Create `.env` File

In project root:

```text id="env1"
.env
```

---

### Step 5: Add Your Key

```env id="env2"
GEMINI_API_KEY=your_api_key_here
```

---

### ⚠️ Important

* Do NOT share your API key
* Do NOT push `.env` to GitHub

Add to `.gitignore`:

```text id="gitignore1"
.env
```

---

## ▶️ Running the Application

### 🔹 Start Backend

```bash id="run1"
uvicorn app:app --reload
```

Open:

```text id="run2"
http://127.0.0.1:8000/docs
```

---

### 🔹 Run Frontend

Open:

```text id="run3"
frontend/index.html
```

---

## 🧪 Usage

### 🔹 Single File

Upload one bill

---

### 🔹 Multiple Files

Upload multiple bills

---

### 🔹 Batch Folder

Enter path:

```text id="use1"
C:\Users\YourName\Desktop\bills
```

---

## 📊 Sample Output (CSV)

```csv id="sample1"
file_name,consumer_id,name,billing_date,units,amount,due_date
bill1.png,267767122167,John Doe,01-04-2026,320,1450,15-04-2026
```

---

## ⚠️ Limitations

* Requires internet (Gemini API)
* Accuracy depends on image clarity
* Folder processing works locally only

---

## 🚀 Future Improvements

* Excel automation (solar calculation template)
* Database integration
* Cloud deployment
* UI enhancements
* Confidence scoring

---

## 💬 Summary

This project demonstrates:

* AI-poIred document processing
* Backend API development
* Batch automation
* Full-stack integration

👉 It transforms a manual workflow into a fully automated pipeline.

---

## 👨‍💻 Author

Pratik Shetake
---
