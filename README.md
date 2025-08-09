# AgentForce_CodeBlasters
# 🤖 AI PR Reviewer

An **interactive web-based tool** for **automated pull request code review**.  
It analyzes code for **security issues**, **performance bottlenecks**, **logic errors**, and **code quality improvements**.  
Supports **GitHub**, **GitLab**, and **CLI mode**, with optional AI integration (OpenAI, Cohere, etc.).

---

## 🚀 Features

- **Multi-Platform Support**:
  - GitHub PR Analysis
  - GitLab MR Analysis
  - CLI Tool Integration
- **Smart Code Analysis**:
  - Security checks (SQL injection, XSS, unsafe eval, etc.)
  - Performance analysis (N+1 queries, inefficient loops, etc.)
  - Logic error detection (assignment in conditions, missing `await`, etc.)
  - Code quality insights (complexity, documentation presence, etc.)
- **AI Integration**:
  - Optionally use AI providers like **OpenAI GPT-4**, **Cohere Command**
  - Local analysis mode available (no API keys required)
- **Interactive UI**:
  - Tab-based platform selection
  - Quick demo buttons for testing
  - Risk level scoring and severity badges
  - Export results as JSON

---

## 📂 Project Structure

- **The code.html** – Main HTML, CSS, and JavaScript in a single file  
  Includes:
  - UI layout and styling
  - Platform selection logic
  - Demo code examples
  - Code parsing, pattern matching, and scoring
  - Results rendering & export

---

## 🛠 Installation & Usage

### 1. Clone the Repository
```bash
git clone https://github.com/<Vsd1208>/<AgentForce_CodeBlasters>.git
cd <AgentForce_CodeBlasters>

### 2. CLI Tool
Install globally via npm:

```
npm install -g ai-pr-reviewer
```
This allows you to run the tool from the command line for local files or diffs.
### Web Interface
No installation required—just access the web app (e.g., via the hosted version or run locally if self-hosted). The interface includes fields for GitHub/GitLab integration and direct code pasting.

### Dependencies
- Node.js (for CLI)
- Optional: API keys for cloud AI providers (OpenAI, Cohere, etc.)

### GitHub Integration
1. Provide a GitHub Personal Access Token (optional for private repos or higher rate limits).
2. Enter the Repository name and Pull Request Number.
3. Click "Fetch PR from GitHub" to load and analyze the changes.

This uses GitHub's API and webhooks for real-time PR analysis.

### GitLab Integration
1. Provide a GitLab Access Token (optional for private projects).
2. Enter the Project ID and Merge Request IID.
3. Click "Fetch MR from GitLab" to load and analyze the changes.

Integrates with GitLab CI/CD for automated reviews.

### CLI Tool
Run the tool on a diff file:

```
ai-pr-review --file changes.diff --format json
```

Options:
- `--file`: Path to the diff or code changes file (required).
- `--format`: Output format (e.g., json, markdown).
- `--provider`: AI analysis provider (e.g., openai, cohere; default: local).
- `--api-key`: Your API key for cloud providers (stored locally).
- `--lang`: Programming language (e.g., javascript, python).

For full CLI options, run `ai-pr-review --help`.

### Web Interface Usage
1. Select the Programming Language from the dropdown.
2. Enter a descriptive Commit Message.
3. Paste your Code Changes (diff or raw code) into the textarea.
4. Choose an AI Analysis Provider and enter an API Key if needed.
5. Click "Analyze Pull Request" to get insights.

## Quick Demo Examples
- **Security Issues**: Analyzes for SQL injection and weak auth mechanisms.
- **Performance Issues**: Flags N+1 queries and inefficient loops.
- **Logic Errors**: Detects issues like using assignment (`=`) instead of comparison (`==`).
- **Clean Code**: Provides a best practices review on a sample of well-written code.

## Configuration
- **API Keys**: For cloud providers, keys are stored locally and never sent to external servers.
- **Custom Providers**: Support for additional AI models can be added via configuration.

## Contributing
Contributions are welcome! Fork the repository, make your changes, and submit a pull request. Focus on adding new features, bug fixes, or expanding language/AI support.

1. Clone the repo: `git clone https://github.com/your-repo/ai-pr-reviewer.git`
2. Install dependencies: `npm install`
3. Run locally: `npm start`
4. Submit a PR with your changes.
