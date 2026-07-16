# 🤖 Enterprise-Grade AI Multi-Agent System (n8n)

An advanced, production-ready multi-agent orchestration ecosystem built entirely on **n8n**. This system leverages a central "coordinator" agent that dynamically routes user requests (via Telegram text or audio) to specialized sub-workflows: **Finance**, **Customer Support**, and **Customer Success**.

---

## 📷 System Architecture

![Main Orchestrator Workflow](./flowchart.png)

*Visual representation of the central coordinator routing requests to specialized agent branches.*

---

## 🧠 How the Ecosystem Works

Instead of using a single LLM to solve every problem, this system implements a **hub-and-spoke multi-agent architecture**:

1. **Ingestion & Processing:** The user sends a message via Telegram (Text or Voice). Voice messages are automatically routed, processed via **AssemblyAI** with dynamic polling/waiting, and transcribed.
2. **Central Orchestration (The Coordinator):** The main AI Agent (powered by **Groq** for ultra-low latency) analyzes the intent of the message and decides which tool to call.
3. **Specialized Sub-Workflows:**
   * 💰 **Financial Agent:** Triggered when the intent relates to invoices, payments, or financial inquiries.
   * 🛠️ **Support Agent:** Triggered for technical troubleshooting, bug reports, and standard customer service.
   * 🤝 **Customer Success Agent:** Triggered for account management, onboarding, retention, or feedback loops.
4. **Active Memory:** The system retains conversational context using a **Simple Memory** node, ensuring natural, multi-turn interactions.

---

## 📂 Repository Structure

This repository contains the complete modular structure of the project:

* 📄 `Principal Workflow.json` — The central orchestrator routing requests and handling Telegram/Audio ingestion.
* 📄 `Financial Workflow.json` — Specialized sub-workflow for financial transactions and queries.
* 📄 `Suport Workflow.json` — Specialized sub-workflow for IT and technical support.
* 📄 `Customer Success Workflow.json` — Specialized sub-workflow for customer relationship and satisfaction.

---

## 🛠️ Tech Stack

* **Workflow Engine:** [n8n](https://n8n.io/)
* **Central LLM Model:** Groq (LLaMA-3 or similar) for blazing-fast orchestration.
* **Audio Transcription:** AssemblyAI API.
* **UI Interface:** Telegram Bot API.
* **Memory Management:** n8n Window Buffer Memory.

---

## 🚀 How to Run this Project

### 1. Prerequisites
* An active **n8n** instance.
* A Telegram Bot token (created via [@BotFather](https://t.me/BotFather)).
* API keys for **Groq** and **AssemblyAI**.

### 2. Import Instructions
1. Import all 4 `.json` files into your n8n workspace.
2. Inside the **Principal Workflow**, configure your Telegram Trigger and HTTP Requests (AssemblyAI).
3. Update the **AI Agent** tools so they correctly target the active Webhook URLs of your imported sub-workflows (`Financial`, `Suport`, and `Customer Success`).
4. Activate all workflows.

---

>🚀
