# 🧠 Deep Research Multi-Agent System using LlamaIndex  _hhh
*A fully agentic, multi-agent research engine powered by LlamaIndex Workflows, OpenAI LLMs, Tavily Search, and event-driven orchestration.*
Project by Arpita Lonakadi

---

## 🚀 Key Features & Issues Tackled

### Multi-Agent Collaboration
- Built a coordinated team of agents (QuestionAgent, AnswerAgent, ReportAgent, ReviewAgent).
- Each agent has specialized responsibilities and communicates via an AgentWorkflow.

### Automated Deep Research Pipeline_dekho

- Converts a broad research topic → sub-questions → parallel answers → a high-quality final report.
- Supports iterative reflection loops for improved coverage.

### Tool-Augmented Intelligence
- Integrated Tavily Web Search API for real-time web information retrieval.
- Agents decide when and how to call tools using LlamaIndex FunctionAgent capabilities.

### Stateful Memory & Context
- Persistent memory via Context + `state` for saving research notes, drafts, feedback.
- Tools can read/write from shared workflow state.

### Event-Driven LLM Orchestration
- Custom event classes power branching, looping, parallelism, and map-reduce style aggregation.
- Real-time introspection into agent decisions, tool calls, and streaming LLM outputs.

### Human-in-the-Loop Support
- Added approval workflows using InputRequiredEvent and HumanResponseEvent.

### Observability & Debugging
  - Full visibility into:
  - AgentInput / AgentOutput
  - Partial LLM streams
  - ToolCall / ToolCallResult
  - Agent handoffs
  - Execution flow diagrams

---

## 🛠️ Technical Implementation

### 📌 Languages & Frameworks
- **Python 3.11+**
- **LlamaIndex (Workflows, AgentWorkflow, FunctionAgent)**
- **OpenAI GPT-4.1-mini**
- **Async Tavily Search Client**
- **Google Colab / Jupyter Notebook**

### 📌 Core Libraries
- `llama-index`
- `tavily-python`
- `llama-index-utils-workflow`
- `pyvis`
- `asyncio`

### 📌 Key Concepts Used (ATS-Optimized)
- Agentic AI  
- Multi-Agent Systems  
- LLM Tool Calling  
- Async Python Programming  
- Contextual Memory  
- Event-Driven Workflows  
- Orchestration Logic  
- Branching & Looping Mechanisms  
- Concurrent Execution (fan-out / fan-in)  
- Human-in-the-Loop Interactions  
- Research Automation  
- Prompt Engineering  
- Observability & Streaming  
- API Integration  
- Workflow Visualization  

---

## 📘 Project Run Through (Step-by-Step)

<img width="1347" height="875" alt="Screenshot 2025-11-19 at 10 13 55 AM" src="https://github.com/user-attachments/assets/8e0231c6-edeb-4734-a1ff-45e0cc42a9cf" />


### **1️⃣ Initialize LLM**
- Load OpenAI API key from Colab.
- Instantiate GPT-4.1-mini using LlamaIndex’s OpenAI wrapper.
- Run a quick test prompt.

### **2️⃣ Build Tools (Tavily Web Search)**
- Installed and configured `tavily-python`.
- Created an async web search function with type hints and docstrings.
- Equipped agents with external search capability.

### **3️⃣ Create a Single-Agent Workflow**
- Used `AgentWorkflow.from_tools_or_functions()`.
- System prompt guides behavior.
- Agent chooses whether to call the web search tool.

### **4️⃣ Add Memory via Context**
- Used Context to persist user state (e.g., storing user name).
- Created stateful tools that modify `ctx.get("state")` and `ctx.set("state")`.

### **5️⃣ Enable LLM Streaming & Debugging**
Captured streaming events:
- `AgentStream` → partial model outputs
- `ToolCall` and `ToolCallResult` → tool usage logs
- `AgentInput` / `AgentOutput` → agent reasoning snapshots

### **6️⃣ Human-in-the-Loop Integration**
- Introduced `InputRequiredEvent` → workflow pauses for human confirmation.
- Human provides answer → workflow continues.

### **7️⃣ Build a Multi-Agent Research Pipeline**
Three core agents:
- **QuestionAgent** → creates sub questions for each topic 
- **ResearchAgent** → web research + note-taking  
- **WriteAgent** → markdown report generation  
- **ReviewAgent** → review/approve/request changes  

Shared state stores:
- `research_notes`
- `report_content`
- `review_feedback`

Agents hand off to each other using `can_handoff_to`.

### **8️⃣ Multi-Agent Execution**
- Parallel searching
- Notes aggregation
- Draft report creation
- Review and feedback

Final output stored in workflow `state`.

### **9️⃣ Advanced Workflows (Low-Level)**
Built custom Workflows using:
- Custom Events
- Step-based orchestration
- Branching logic
- Looping (retry flows)
- Parallel execution via `ctx.send_event`
- Map-reduce with `ctx.collect_events`
- Streaming via `ctx.write_event_to_stream`

### **🔁 Final Module: DeepResearchWorkflow**
Fully automated research flow:
1. Generate sub-questions (QuestionAgent)  
2. Answer them in parallel (AnswerAgent)  
3. Aggregate all answers  
4. Generate polished report (ReportAgent)  
5. Optional reflection loop (ReviewAgent)

---

## 🏆 Achievements

- Implemented a **production-grade multi-agent research engine**.
- Built an end-to-end research automation workflow with tool support.
- Enabled **parallel answering**, resulting in major performance gains.
- Designed a **reflection-driven system** to iteratively enhance report quality.
- Demonstrated mastery of:
  - LlamaIndex Workflows  
  - Multi-agent orchestration  
  - Async tool calling  
  - Human-in-loop logic  
  - Workflow visualization and debugging  

---

## 📦 How to Use This Project

### **1. Install Dependencies**
```bash
pip install llama-index
pip install tavily-python
pip install llama-index-utils-workflow
