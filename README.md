## 📝 AI Meeting Preparation Agent
This Streamlit application leverages multiple AI agents to create comprehensive meeting preparation materials. It uses OpenAI's models (configurable) and the Serper API for web searches to generate context analysis, industry insights, meeting strategies, and executive briefings.

### Features

- Multi-agent AI system for end-to-end meeting preparation
- Upload supporting PDFs/TXT/MD files and fold them into every analysis
- Persistent meeting library to revisit and clone prior briefs
- Web search capability using Serper API with optional compliance and localization callouts
- Rehearsal simulation with persona-driven objections and coaching guidance
- Post-meeting activation kit with action tracker and ready-to-send follow-up messaging

### How to get Started?

1. Clone the GitHub repository

```bash
git clone https://github.com/Shubhamsaboo/awesome-llm-apps.git
cd advanced_ai_agents/single_agent_apps/ai_meeting_agent
```
2. Install the required dependencies:

```bash
pip install -r requirements.txt
```

3. Get your OpenAI API Key

- Sign up for an OpenAI account and obtain your API key.

4. Get your SerpAPI Key

- Sign up for an [Serper API account](https://serper.dev/) and obtain your API key.

5. Run the Streamlit App
```bash
streamlit run meeting_agent.py
```

Extras:
- Use the sidebar to select the LLM model and temperature.
- Adjust the document preview length slider for longer or shorter snapshots.
- Load a saved brief back into the form from the Meeting Library.
- Clear your local Meeting Library via the sidebar (with confirmation).

Notes:
- This app is configured to use a cost-efficient OpenAI model by default (for example `gpt-4.1-nano`) to reduce API costs while keeping good output quality.
- Uploaded files are stored in memory for the current run and persist only as titles in the meeting library.
- Make sure your `requirements.txt` is installed and that `crewai`, `crewai-tools`, and `pypdf` are available in your Python environment.