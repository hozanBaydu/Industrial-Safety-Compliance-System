# 🛡️ AI Safety Sentinel Pro
### Multi-Agent RAG System for Industrial Safety Compliance Monitoring

AI Safety Sentinel Pro is an intelligent workplace safety monitoring system that combines **computer vision (YOLO)** with **multi-agent reasoning using LLMs**.

The system automatically detects **safety violations such as missing helmets or harnesses** from workplace images and then analyzes the incident using **multiple AI agents with different roles**.

These agents debate the situation and generate a **final safety decision report**, which can then be reviewed by a **human auditor**.

The goal is to build an **AI-assisted industrial safety monitoring system** that improves compliance, reduces accidents, and supports safety managers with intelligent decision-making tools.

## 🚀 System Overview

The system consists of three main AI layers:

1. **Computer Vision Detection**
   - YOLO11 detects safety equipment compliance in images.
   - Identifies:
     - Helmet usage
     - Harness usage
     - Missing protective equipment

2. **Multi-Agent Safety Analysis**
   - Detection results are passed to multiple AI agents.
   - Each agent analyzes the incident from a different perspective:
     - Strict safety auditor
     - Safety training coach
     - Final decision maker

3. **Human-in-the-Loop Validation**
   - AI results are reviewed by human auditors.
   - Approved incidents are stored in the safety database.
   - Historical trends are visualized in dashboards.

This architecture combines **computer vision + RAG + multi-agent reasoning + human oversight**.

## 📊 Dataset

The dataset used for training the detection model was **synthetically generated** to simulate industrial safety scenarios.

Dataset Source:

https://www.kaggle.com/datasets/hozanbaydu2112/industrial-safety-compliance-system

The dataset includes images representing workplace safety situations such as:

- Workers wearing helmets
- Workers without helmets
- Workers wearing safety harnesses
- Workers without harnesses

### Dataset Classes

| Class | Description |
|-----|-----|
| helmet_on | Worker wearing a safety helmet |
| helmet_off | Worker not wearing a helmet |
| harness_on | Worker wearing a safety harness |
| harness_off | Worker not wearing a harness |

The dataset is annotated in **YOLO format**.

## 🧠 Model Training

The object detection model was trained using **YOLO11n** from the Ultralytics framework.

### Training Configuration

| Parameter | Value |
|------|------|
| Model | YOLO11n |
| Image Size | 640 |
| Epochs | 100 |
| Early Stopping | 15 |
| Framework | Ultralytics YOLO |

### Training Results

| Metric | Value |
|------|------|
| Precision | 0.906 |
| Recall | 0.735 |
| mAP@50 | **0.798** |
| mAP@50-95 | 0.426 |

### Class Performance

| Class | Precision | Recall | mAP50 |
|------|------|------|------|
| helmet_on | 0.982 | 0.787 | 0.906 |
| helmet_off | 0.707 | 0.714 | 0.652 |
| harness_on | 0.934 | 0.885 | **0.975** |
| harness_off | 1.000 | 0.555 | 0.657 |

<div align="center" style="border:1px solid #ddd; padding:15px; border-radius:10px; background-color:#fafafa;">

<table>
<tr>
<td align="center">
<img src="https://github.com/user-attachments/assets/4addc234-75b3-45bc-aa1c-1ac502a61a41" width="480"/>
</td>

<td align="center">
<img src="https://github.com/user-attachments/assets/7cd91dbf-2bfa-461b-a866-e482c5c2f318" width="480"/>
</td>
</tr>
</table>

</div>


These results demonstrate that the model performs well in detecting **helmet and harness compliance in industrial environments**.

## 🤖 Multi-Agent Safety Analysis

After detecting safety violations, the system sends the detection results to a **multi-agent reasoning system powered by LLMs**.

Each agent has a specific role:

### Agent 1 — Strict HSE Auditor

Focuses on **strict safety enforcement**.

Responsibilities:
- Identify rule violations
- Recommend penalties
- Enforce maximum compliance

---

### Agent 2 — Safety Coach

Focuses on **long-term safety culture**.

Responsibilities:
- Suggest training programs
- Identify root causes
- Recommend behavioral improvements

---

### Agent 3 — Senior HSE Director

Acts as the **final decision maker**.

Responsibilities:
- Analyze both agent opinions
- Generate a balanced safety verdict
- Produce a structured safety report

---

This **multi-agent debate mechanism** improves decision quality and prevents overly rigid or overly soft safety decisions.

## 🏗 System Architecture

Pipeline:
Image Upload
↓

YOLO Detection
↓

Violation Analysis
↓

Multi-Agent Debate
↓

Final Verdict
↓

Human Review
↓

Safety Database

## ▶️ Run the Application (Docker)

This project is containerized using **Docker** and **Docker Compose**, allowing the entire system to run with a single command.

### 1. Clone the repository

```bash
git clone https://github.com/hozanBaydu/Industrial-Safety-Compliance-System
cd ai-safety-sentinel
```

### 2. Create an environment variable file

Create a `.env` file in the project root directory and add your Google API key:

```bash
GOOGLE_API_KEY=your_google_api_key_here
```

### 3. Build and run the application

```bash
docker-compose up --build
```

Docker will automatically:

- build the application image  
- install dependencies  
- start the Streamlit safety monitoring system  

### 4. Open the web interface

After the container starts, open the application in your browser:

```
http://localhost:8501
```

### 5. Use the system

Once the application is running you can:

1. Upload a workplace image  
2. Detect safety equipment using the YOLO model  
3. Analyze violations using the multi-agent AI system  
4. Generate an AI safety report  
5. Send the result to the human review queue


The system integrates:

- **YOLO11 (Computer Vision)**
- **LangChain + Gemini (LLM reasoning)**
- **Streamlit (Web interface)**
- **SQLite (Safety logs database)**

## 🛠 Technologies Used

- Python
- Ultralytics YOLO
- Streamlit
- LangChain
- Google Gemini API
- SQLite
- Matplotlib
- Pandas
- Docker
- Docker Compose

