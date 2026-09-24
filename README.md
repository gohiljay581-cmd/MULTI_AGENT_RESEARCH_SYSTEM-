🔬 ResearchMind — Multi-Agent AI Research System

A LangChain-powered multi-agent research assistant that searches the web, extracts relevant information, generates a structured research report, and critiques the final result.







✨ Overview

ResearchMind is a multi-agent AI research system built with LangChain and Streamlit.

Instead of relying on a single LLM call, the system divides the research workflow into specialized stages:

                         ┌─────────────────────┐
                         │   Research Topic    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    🔎 Search Agent  │
                         │  Web research       │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    📄 Reader Agent  │
                         │ Scrape & extract    │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    ✍️ Writer Chain  │
                         │ Generate report     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │    🧐 Critic Chain  │
                         │ Review & feedback   │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │  📑 Final Research  │
                         │       Report        │
                         └─────────────────────┘

The application provides a polished Streamlit interface where users can enter a research topic and run the complete pipeline.

🚀 Features

🔎 Web Search Agent — searches for recent and relevant information.

📄 Reader Agent — selects a relevant resource and extracts deeper content.

✍️ AI Research Writer — creates a structured research report.

🧐 AI Critic — reviews the generated report and provides strengths, improvements, and a score.

🖥️ Streamlit UI — clean interactive interface for running the pipeline.

📥 Report Download — download the generated research report as Markdown.

🔐 Environment-based API Keys — secrets are loaded through .env.

🧩 Modular Architecture — agents, tools, pipeline, and UI are separated into individual files.

🧠 Multi-Agent Workflow

1. 🔎 Search Agent

The Search Agent uses the Tavily search tool to find recent and reliable information about the requested topic.

User Topic
    ↓
Tavily Web Search
    ↓
Titles + URLs + Snippets

2. 📄 Reader Agent

The Reader Agent receives the search results, selects a relevant URL, and uses the scraping tool to retrieve deeper content.

Search Results
    ↓
Select Relevant URL
    ↓
Web Scraping
    ↓
Clean Text Content

3. ✍️ Writer Chain

The Writer Chain combines the search results and scraped content and generates a professional research report containing:

Introduction

Key Findings

Conclusion

Sources

4. 🧐 Critic Chain

The Critic Chain reviews the generated report and returns:

Score: X/10

Strengths:
- ...

Areas to Improve:
- ...

One line verdict:
...

🛠️ Tech Stack

Technology

Purpose

🐍 Python

Core programming language

🦜 LangChain

Agent and LLM orchestration

⚡ Groq

LLM inference

🔎 Tavily

Web search

🌐 Requests

HTTP requests

🍲 BeautifulSoup

HTML parsing and text extraction

🎨 Streamlit

Web application UI

🔐 python-dotenv

Environment variable management

📁 Project Structure

Multi-Agent-Research-System/
│
├── app.py                  # Streamlit user interface
├── agents.py               # Search/Reader agents + Writer/Critic chains
├── pipeline.py             # End-to-end research pipeline
├── tools.py                # Tavily search & URL scraping tools
│
├── requirements.txt        # Python dependencies
├── .env.example            # Environment variable template
├── .gitignore              # Files excluded from Git
└── README.md               # Project documentation

Local-only files

The following files/folders should not be committed to GitHub:

.env
.venv/
__pycache__/

⚙️ Installation & Setup

1. Clone the repository

git clone https://github.com/YOUR_USERNAME/Multi-Agent-Research-System.git
cd Multi-Agent-Research-System

2. Create a virtual environment

Windows:

python -m venv .venv

Activate it:

.venv\Scripts\activate

3. Install dependencies

pip install -r requirements.txt

4. Configure environment variables

Create a .env file in the project root:

TAVILY_API_KEY=your_tavily_api_key
GROQ_API_KEY=your_groq_api_key
GEMINI_API_KEY=your_gemini_api_key

Note: Never commit .env or expose API keys publicly. Use .env.example as the template.

5. Run the Streamlit application

streamlit run app.py

The application will open in your browser.

🖥️ Using the Application

Open the Streamlit application.

Enter a research topic.

Click Run Research Pipeline.

The system performs:

Web search

Resource scraping

Research writing

Report criticism

Review the generated research report.

Download the report as a .md file.

Example Topics

LLM agents in 2026

CRISPR gene editing

Fusion energy progress

🔑 Environment Variables

Variable

Purpose

TAVILY_API_KEY

Enables web search

GROQ_API_KEY

Provides the LLM used by the agents

GEMINI_API_KEY

Reserved for Gemini integration

🔄 Pipeline Architecture

                         USER
                          │
                          ▼
                  ┌───────────────┐
                  │   Streamlit   │
                  │      UI       │
                  └───────┬───────┘
                          │
                          ▼
                  ┌───────────────┐
                  │ Search Agent  │
                  └───────┬───────┘
                          │
                    Web Search
                          │
                          ▼
                  ┌───────────────┐
                  │ Reader Agent  │
                  └───────┬───────┘
                          │
                    Web Scraping
                          │
                          ▼
                  ┌───────────────┐
                  │ Writer Chain  │
                  └───────┬───────┘
                          │
                   Research Report
                          │
                          ▼
                  ┌───────────────┐
                  │ Critic Chain  │
                  └───────┬───────┘
                          │
                          ▼
                   Final Feedback

🧩 Core Components

agents.py

Contains:

Search Agent

Reader Agent

Writer Chain

Critic Chain

The agents are created using LangChain's agent functionality, while the writer and critic use LangChain prompt chains.

tools.py

Contains the external tools used by the agents:

web_search()

scrape_url()

The search tool uses Tavily, while the reader tool uses Requests + BeautifulSoup.

pipeline.py

Provides the programmatic end-to-end pipeline:

run_research_pipeline(topic)

This allows the research workflow to be executed independently of the Streamlit UI.

app.py

Provides the interactive Streamlit application, including:

Research topic input

Pipeline status

Agent outputs

Final report

Critic feedback

Markdown report download

🔒 Security

API keys are loaded from environment variables:

from dotenv import load_dotenv

load_dotenv()

Never commit:

.env
API keys
Access tokens
Passwords
Private credentials

Before pushing the project to GitHub, verify:

git status

and make sure .env is not included.

🧪 Run the Pipeline Without Streamlit

You can also run the command-line pipeline:

python pipeline.py

Then enter a research topic when prompted.

📌 Future Improvements

Potential extensions for the system include:

Parallel research agents

Source quality evaluation

Multiple search providers

Citation verification

PDF/document research

Persistent research history

Vector database integration

RAG-based knowledge retrieval

Agent memory

Export to PDF

More specialized research agents

🎯 Project Goal

The goal of ResearchMind is to demonstrate how multi-agent AI systems can decompose a complex research task into specialized, coordinated steps rather than relying on a single model response.

It combines:

Agents + Tools + LLMs + Web Search + Web Scraping + Prompt Chains + Streamlit

to create an end-to-end AI research workflow.

👨‍💻 Author

Gohil Jay

Computer Science & Engineering — Data Science

GitHub: @gohiljay581-cmd

⭐ If You Find This Project Useful

Give the repository a ⭐ on GitHub and feel free to explore, fork, and improve the project.

<p align="center">
  <b>🔬 ResearchMind</b><br>
  <i>Search. Read. Write. Critique. Research smarter.</i>
</p>