# Copilot Agent Instructions for This Repository

## Project Overview
- **Purpose:** Web app for managing extracurricular activities at Mergington High School.
- **Stack:** FastAPI backend (`src/app.py`), static frontend (HTML/CSS/JS in `src/static/`).
- **Data:** Activities and participants are stored in-memory in Python (see `activities` dict in `src/app.py`).

## Key Components
- **Backend:**
  - `src/app.py`: FastAPI app, exposes endpoints for listing activities, signing up, and unregistering.
  - All activity data is hardcoded in `app.py` (see enhancement issue to move to `activities.json`).
  - Static files served from `/static` (HTML, CSS, JS).
- **Frontend:**
  - `src/static/index.html`: Main UI, lists activities and signup form.
  - `src/static/app.js`: Handles fetching activities, signup, and unregister via API calls.
  - `src/static/styles.css`: UI styling.

## Developer Workflows
- **Run Locally:**
  - Install: `pip install fastapi uvicorn`
  - Start: `uvicorn src.app:app --reload`
  - Access: Open the forwarded port (default 8000) in browser.
- **Debug:**
  - Use VS Code "Run and Debug" with the provided `launch.json` (runs with reload).
- **MCP Integration:**
  - `.vscode/mcp.json` configures the GitHub MCP server for Copilot Agent mode.
  - Use Copilot Chat in Agent mode for issue management and code changes.

## Project Conventions & Patterns
- **Activity Identifiers:** Activity name is the unique key.
- **Student Identifiers:** Email address is used as the unique identifier.
- **No persistent storage:** All data resets on server restart.
- **API Endpoints:**
  - `GET /activities` — List all activities
  - `POST /activities/{activity_name}/signup?email=...` — Sign up
  - `DELETE /activities/{activity_name}/unregister?email=...` — Unregister
- **Frontend-Backend Contract:**
  - JS expects API responses as JSON with `message` or `detail` fields for status.
  - Activities and participants are rendered dynamically.

## Notable Issues & Enhancement Requests
- See `.github/steps/1-step-issues/` for real user feedback and feature requests:
  - Move activities to a JSON file (`activities-file.md`)
  - Add admin/teacher mode for registration control (`admin-mode.md`)
  - UI improvements: filters, search, responsive layout, school colors, mascot, etc.
  - Add missing activities (e.g., GitHub Skills)

## Example: Adding a New Activity
- Update the `activities` dict in `src/app.py` (or `activities.json` if refactored).
- Restart the server to reflect changes.

## Tips for AI Agents
- Always check `.github/steps/1-step-issues/` for user priorities before implementing features.
- When updating data models or endpoints, update both backend and frontend as needed.
- For MCP/Agent workflows, follow the step-by-step instructions in `.github/steps/` and `README.md`.

---
For more, see `src/README.md` and `.github/steps/` for workflow and enhancement context.
