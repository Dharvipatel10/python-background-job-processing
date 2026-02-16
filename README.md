# ⚡ FastAPI Background Job Engine

### *Asynchronous Processing with Redis • RQ • Pydantic*

> **Not just another API demo.**
> This project is a compact, production-style prototype showing how modern backend systems handle **non-blocking workloads**, **validated data pipelines**, and **scalable job execution** — the same principles used in real AI platforms and high-performance web services.

---

## 🧠 Why This Project Exists

Modern applications should never freeze while heavy tasks run.
This project demonstrates how to:

✔️ Accept API requests instantly
✔️ Validate structured data using **Pydantic**
✔️ Offload processing to **background workers**
✔️ Use **Redis** as a fast in-memory queue
✔️ Keep the API responsive and scalable

It reflects real backend patterns used in AI tools, automation platforms, and distributed systems.

---

## 🚀 Tech Stack

| Layer      | Technology | Purpose                          |
| ---------- | ---------- | -------------------------------- |
| API        | FastAPI    | High-performance async endpoints |
| Validation | Pydantic   | Structured request models        |
| Queue      | Redis      | In-memory job broker             |
| Worker     | RQ         | Background execution engine      |
| Runtime    | Uvicorn    | ASGI server                      |

---

## 🏗️ Architecture Overview

Client Request
⬇
FastAPI Endpoint
⬇ *(Pydantic Validation)*
Redis Queue
⬇
RQ Worker
⬇
Background Job Execution

**Goal:** Immediate response to client while processing runs asynchronously.

---

## 📂 Project Structure

```
python-background-job-processing/
│
├── main.py        # FastAPI application & routes
├── job.py         # Background task logic
├── worker.py      # RQ worker configuration
├── requirements.txt
└── README.md
```

---

## 🐳 Running Redis (Docker)

```
docker run -d --name redis -p 6379:6379 redis:7-alpine
```

Verify:

```
docker ps
```

---

## 🧪 Local Setup

Create virtual environment:

```
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

---

## ▶️ Start the API

```
uvicorn main:app --reload
```

Interactive Docs:

```
http://127.0.0.1:8000/docs
```

---

## ⚡ Start Worker (Windows)

Windows does not support `os.fork()`, so use:

```
rq worker -w rq.worker.SimpleWorker task_queue
```

---

## 📬 Example Request

**POST** `/job`

```json
{
  "lowest": 10,
  "highest": 17
}
```

Workflow:

1. FastAPI receives request
2. Pydantic validates payload
3. Job is pushed into Redis queue
4. Worker processes it asynchronously

---

## 🧩 Key Engineering Decisions

* **Async-first API design** — prevents blocking operations
* **Pydantic models** — ensures predictable data contracts
* **Queue-based architecture** — easily extendable to AI workloads
* **Dockerized Redis** — portable and environment-agnostic

---

## 🎯 What This Demonstrates to Reviewers

This repository highlights understanding of:

* API design patterns
* Distributed job processing
* Backend scalability concepts
* Clean Python project structuring
* Real-world development workflow (Docker + Git)

Rather than focusing on complexity, the emphasis is on **clarity of architecture** — showing how small systems can be built using professional patterns.

---

## 👨‍💻 Author

**Dharvi Patel**
M.Sc. Automotive Software Engineering — TU Chemnitz

Building systems at the intersection of **engineering, automation, and intelligent software**.
