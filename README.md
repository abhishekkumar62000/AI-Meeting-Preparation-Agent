<img width="1024" height="1024" alt="Logo" src="https://github.com/user-attachments/assets/678dcc73-0be6-4105-a8e6-7884c159bf78" />

Live App:-- https://github.com/abhishekkumar62000/AI-Meeting-Preparation-Agent

Uploading App Demo.mp4…

<img width="1912" height="938" alt="app page" src="https://github.com/user-attachments/assets/7df59a8e-2793-47ef-b1ad-6299e2699b65" />


````markdown
# AI Meeting Preparation Agent 📝

**Multi-agent intelligence for real meetings — Turn meetings into momentum.**

**Live / Demo:** _Already deployed_  
**Repo:** https://github.com/abhishekkumar62000/AI-Meeting-Preparation-Agent

---

## Overview

**AI Meeting Preparation Agent** is a Streamlit application that helps meeting owners and participants prepare for, rehearse, and act on real meetings. It uses a multi-agent pipeline to analyze context and documents, produce an executive brief, generate rehearsal prompts, and provide post-meeting activation guidance — then stores briefs in a local meeting library.

Built for speed and practicality: one-file Streamlit entry (`meeting_agent.py`) plus a small supporting set of files. Designed to be extended into richer workflows (calendar integrations, team-shared libraries, PPTX export, and more).

---

## Key Features

- **Simple API key setup** in the sidebar (OpenAI + Serper).
- **Appearance themes**: theme preset selector and custom CSS injection for visual polish.
- **Model settings**: choose LLM model and temperature.
- **Meeting form**: company, meeting objective, attendees, meeting duration, focus areas.
- **Advanced preparation**:
  - Upload supporting docs (PDF / TXT / MD).
  - Paste historical notes, attendee personas, rehearsal focus, follow-up channels.
  - Toggle live updates & regulatory insights.
  - Paste calendar invite / ICS and auto-extract fields.
- **Document ingestion**: PDF parsing (pypdf) + robust text decoding -> digested content for agents.
- **Multi-agent pipeline (CrewAI)**:
  - Agents such as Meeting Context Specialist, Industry Expert, Meeting Strategist, Communication Specialist, Rehearsal Coach, and Post-Meeting Activation Partner operate sequentially to produce a consolidated meeting brief.
- **Prepare Meeting**: run the multi-agent crew to produce a full brief, downloadable as `.md` and optionally `.pptx` (if `python-pptx` installed).
- **Practice Mode**: text-only rehearsal simulation with session log, objection generation, scoring, and saveable practice history.
- **Meeting Library**: saved briefs persisted to `meeting_history.json`, list/load/clear saved briefs.
- **Transcript support**: paste transcripts to extract summary + action items; optionally save to library or download summary.

---

## Files

- `meeting_agent.py` — Full Streamlit app (single entrypoint).
- `requirements.txt` — Python dependencies.
- `meeting_history.json` — Created when saving meeting history (persisted library).
- `README.md` — Project overview (this file).

---

## Inputs & Outputs

**Inputs**
- Text fields: company, objective, attendees, focus areas, personas, rehearsal focus, follow-up channels.
- Numeric: meeting duration.
- File uploads: supporting docs (PDF / TXT / MD).
- Paste fields: transcripts, calendar invite text.
- API keys: OpenAI, Serper.

**Outputs**
- Interactive Markdown meeting brief shown in-app.
- Downloadable `.md` meeting brief.
- Optional PPTX deck (requires `python-pptx`).
- Downloadable transcript summary (`.md`).
- Saved brief entries persisted to `meeting_history.json`.

---

## Architecture & Data Flow

1. **User completes form / uploads files** in the Streamlit UI.
2. Uploaded files processed by `_extract_supporting_documents`:
   - PDFs via `pypdf`, text files via decoding; special handling to preserve structure where possible.
3. Documents are digested into `documents_digest` used as context for agents.
4. **Multi-agent Crew**:
   - Several Agent instances each have a role-specific task (context, industry analysis, strategy, communication, rehearsal, activation).
   - Tasks are executed sequentially (Process.sequential) and outputs are combined into a single meeting brief.
5. **Persistence**:
   - Generated briefs and transcript summaries written to `st.session_state["meeting_history"]`.
   - `_write_history_file` persists history to `meeting_history.json`.
   - Practice sessions stored in `st.session_state["practice_history"]` (session-ephemeral by default).

---

## How to run (development)

1. Clone:
   ```bash
   git clone https://github.com/abhishekkumar62000/AI-Meeting-Preparation-Agent.git
   cd AI-Meeting-Preparation-Agent
````

2. Create venv & install:

   ```bash
   python -m venv .venv
   source .venv/bin/activate      # macOS / Linux
   .venv\Scripts\activate         # Windows
   pip install -r requirements.txt
   ```

3. Set API keys (in sidebar at runtime) — you can also export as env vars if you prefer.

4. Run:

   ```bash
   streamlit run meeting_agent.py
   ```

**Optional**: to enable PPTX exports install `python-pptx`:

```bash
pip install python-pptx
```

---

## Security & Privacy

* The app requires **OpenAI API key** for LLM calls — do not commit keys to the repo.
* Uploaded documents and generated briefs are stored locally in `meeting_history.json`. Treat that file as sensitive if it contains private meeting content.
* Consider adding encryption, user-auth, or server-side storage for team deployments.

---

## Limitations & Known Issues

* PDF parsing may lose some layout and table structure. For complex documents, pre-process to simpler text where possible.
* Performance depends on model chosen and document size; large digests may require truncation or chunking.
* No built-in user authentication or multi-user sharing in this repo’s current scope.
* PPTX generation is optional and requires additional dependency.

---

## Future Work / Roadmap

* Add calendar API integration (Google / Microsoft) to auto-populate invites.
* Team-shared library with role-based permissions and encryption.
* Real-time live-transcription ingestion (Zoom / Teams / Meet integrations).
* Expand to a server-based architecture for shared team access and job queues.
* Add unit tests and CI for main ingestion & doc parsing functions.

---

## Developer notes

* Entrypoint: `meeting_agent.py`. It contains the Streamlit UI, ingestion helpers, Crew definitions, and persistence helpers.
* History JSON structure: saved briefs are stored as list entries in `meeting_history.json`.
* To reset library: delete `meeting_history.json` or use the app's Clear Library button.

---

## Contributing

1. Fork the repo.
2. Create a branch: `git checkout -b feature/your-feature`.
3. Open a PR describing your change.

---

## License

Add a license file (e.g., `MIT`) if you want to open-source. Example:

```
MIT License
```

---

## Contact

For questions or support: open an issue on the repo or DM me on GitHub.

```

---

# Release / Changelog entry (paste to Releases or CHANGELOG.md)

```

## v0.1 — Initial Release — 2025-11-05

**AI Meeting Preparation Agent** first public release.

Highlights:

* Streamlit single-file app `meeting_agent.py` implementing multi-agent meeting preparation pipeline (CrewAI-driven).
* Document ingestion for PDF/TXT/MD, transcription summary, and rehearsal practice mode.
* Local meeting library persistence (`meeting_history.json`) with save/load/clear.
* Downloadable meeting brief (`.md`) and optional `.pptx` export (if `python-pptx` present).
* Sidebar API key entry + model & appearance configurability.

Notes:

* Keep your OpenAI API key secure.
* PDF parsing uses `pypdf`. Large docs may require chunking.

```

---

# Commit message (single-line + longer body)

**Commit title**
```

feat: add AI Meeting Preparation Agent Streamlit app (initial release)

```

**Commit body**
```

Add meeting_agent.py (Streamlit single-file app) and supporting files.

* Multi-agent pipeline for meeting prep (context, industry, strategy, rehearsal, activation).
* PDF/TXT/MD ingestion, transcript summary, practice mode, local meeting library persistence.
* requirements.txt + README updates and meeting_history.json support.

```

---

# PR description (copy into Pull Request)

```

### Summary

This PR introduces the AI Meeting Preparation Agent — a Streamlit app that helps teams and individuals prepare for meetings by ingesting supporting documents, running multi-agent analyses, producing executive briefs, and enabling rehearsal.

### Included

* `meeting_agent.py` — full Streamlit entrypoint
* `requirements.txt` — dependency list
* `README.md` — in-depth project overview
* meeting library persistence logic (writes to `meeting_history.json` when saving)

### How to test

1. Install deps and run `streamlit run meeting_agent.py`.
2. Enter OpenAI API key in the sidebar.
3. Fill form, upload sample docs, and click Prepare Meeting to generate brief.

### Notes

* Optional PPTX export requires `python-pptx`.
* Please do not commit API keys.

```

---

# Social post (tweet / LinkedIn short)

```

Launched: AI Meeting Preparation Agent 📝 — a Streamlit app that turns meeting prep from chaos into clarity. Upload docs, run a multi-agent analysis, get an executive brief, rehearse objections and save meeting briefs to a local library. Try it 👉 [https://github.com/abhishekkumar62000/AI-Meeting-Preparation-Agent](https://github.com/abhishekkumar62000/AI-Meeting-Preparation-Agent)
(Released 2025-11-05)

````

---

# Git commands to apply & push changes locally

```bash
# after editing README or adding release notes
git add README.md
git add meeting_agent.py
git add requirements.txt
git commit -m "feat: add AI Meeting Preparation Agent Streamlit app (initial release)"
git push origin main
````

---
