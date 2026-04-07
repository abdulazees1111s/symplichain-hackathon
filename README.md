# 🚀 Symplichain Hackathon Submission

Hi! This repository contains my solution for the Symplichain Software Engineering Intern Hackathon.

The goal of this submission is not just to provide answers, but to demonstrate:
- Clear system design thinking
- Practical engineering decisions
- Ability to reason under real-world constraints

---

# 📌 Problem Overview

The hackathon consists of four major components:

1. Shared Gateway Problem (Rate Limiting & Fairness)
2. Mobile Application Architecture
3. CI/CD Pipeline Design
4. Debugging a Distributed System Failure

Each section focuses on building scalable, efficient, and realistic solutions.

---

# 🧩 Part 1: Shared Gateway Architecture

## 🧠 Problem Statement

- 25 customers generate **>20 requests/sec**
- External API allows only **3 requests/sec**
- Need to ensure:
  - No request loss
  - Fairness across customers
  - Reliable retry handling

---

## ⚙️ Architecture Design

Clients
↓
Django API (EC2)
↓
Redis (Customer-specific Queues)
↓
Round Robin Scheduler
↓
Celery Workers (Rate Limited: 3/sec)
↓
External API
↓
Retry + Dead Letter Queue
