# 🤖 AI PR Reviewer with GitHub Copilot

An intelligent code analysis tool that combines AI-powered pull request reviews with GitHub Copilot integration for enhanced code quality assessment and automated fixes.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-2.0.0-green.svg)
![GitHub Copilot](https://img.shields.io/badge/GitHub-Copilot-purple.svg)

## ✨ Features

### 🔍 Smart Code Analysis
- **Multi-language support**: JavaScript, TypeScript, Python, Java, C#, PHP, Ruby, Go, Rust, Kotlin, Swift, C++
- **Security vulnerability detection**: SQL injection, XSS, code injection, and more
- **Performance issue identification**: N+1 queries, inefficient loops, memory leaks
- **Logic error detection**: Assignment vs comparison, unreachable code, missing returns

### 🤖 GitHub Copilot Integration
- **AI-powered suggestions**: Enhanced code analysis with Copilot's machine learning
- **Auto-fix capabilities**: One-click application of Copilot's recommended fixes
- **Contextual improvements**: Code quality suggestions based on best practices
- **Demo mode**: Try Copilot features without API access

### 🔗 Multi-Platform Support
- **GitHub**: Direct integration with GitHub PRs using GitHub API
- **GitLab**: Support for GitLab merge requests
- **CLI Tool**: Command-line interface for local development

### 📊 Quality Scoring
- **Comprehensive scoring system**: 0-100 scale based on code quality
- **Severity classification**: Critical, High, Medium, Low issue categorization
- **Real-time feedback**: Instant analysis results with detailed explanations

## 🚀 Quick Start

### 1. Download the HTML File
Save the `code.html` file to your local machine or deploy it to a web server.

### 2. Open in Browser
```bash
# Open directly
open code.html

# Or serve with Python (recommended)
python -m http.server 8000
# Then visit http://localhost:8000/code.html
```

### 3. Configure Platform Integration

#### GitHub Integration
1. Generate a [Personal Access Token](https://github.com/settings/tokens)
2. Enter your token in the GitHub tab
3. Provide repository name and PR number
4. Click "Fetch PR with Copilot Context"

#### GitLab Integration
1. Create an [Access Token](https://gitlab.com/-/profile/personal_access_tokens)
2. Enter your token and project ID
3. Specify merge request number
4. Click "Fetch MR from GitLab"

#### CLI Tool Setup
```bash
# Install the CLI tool (conceptual - not yet published)
npm install -g ai-pr-reviewer-copilot

# Configure with your preferred AI provider
ai-pr-review --provider copilot --file changes.diff
```

## 🔧 Configuration

### GitHub Copilot Setup

#### Demo Mode (No API Required)
```javascript
// Set to demo mode for mock suggestions
copilotEnabled = 'demo'
```

#### API Mode (Requires GitHub Copilot Business)
```javascript
// Configure with your Copilot API token
copilotEnabled = 'api'
// Token: ghs_xxxxxxxxxxxxxxxxxxxx
```

### Environment Variables (for CLI)
```bash
export GITHUB_TOKEN="your_github_token"
export COPILOT_TOKEN="your_copilot_token"
export OPENAI_API_KEY="your_openai_key"  # Alternative provider
```

## 📖 Usage Examples

### 1. Quick Demo
Try the built-in examples to see the tool in action:
- **🔒 Security Issues**: SQL injection, XSS vulnerabilities + Copilot fixes
- **⚡ Performance Issues**: N+1 queries + optimization suggestions
- **🧠 Logic Errors**: Assignment vs comparison + automated corrections
- **✅ Clean Code**: Best practices example with Copilot approval

### 2. Manual Code Analysis
```javascript
// Paste your code in the textarea
const userQuery = `SELECT * FROM users WHERE id = '${userId}'`;
// The tool will detect SQL injection and suggest parameterized queries
```

### 3. GitHub PR Integration
1. Enter repository: `owner/repo-name`
2. Enter PR number: `123`
3. The tool fetches the PR diff and analyzes it automatically

### 4. CLI Integration
```bash
# Analyze a specific file
ai-pr-review --file src/auth.js --provider copilot

# Analyze git diff
git diff HEAD~1 | ai-pr-review --provider copilot --stdin

# Generate report
ai-pr-review --file changes.diff --output json --provider copilot
```

## 🛠️ API Integration

### GitHub API
```javascript
const response = await fetch('https://api.github.com/repos/owner/repo/pulls/123', {
  headers: {
    'Authorization': `token ${githubToken}`,
    'Accept': 'application/vnd.github.v3+json'
  }
});
```

### GitHub Copilot API (Enterprise)
```javascript
const suggestion = await fetch('https://api.githubcopilot.com/chat/completions', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${copilotToken}`,
    'Content-Type': 'application/json'
  },
  body: JSON.stringify({
    model: 'copilot-preview',
    messages: [
      {
        role: 'user',
        content: `Review this code for security issues:\n\n${code}`
      }
    ]
  })
});
```

## 🔒 Security Considerations

### Data Privacy
- **No data storage**: All analysis happens client-side
- **API tokens**: Stored temporarily in browser memory only
- **Secure transmission**: All API calls use HTTPS

### Best Practices
- **Token management**: Use environment variables for production
- **Scope limitation**: Grant minimal required permissions to tokens
- **Regular rotation**: Rotate API tokens periodically

## 🤝 Contributing

### Development Setup
```bash
# Clone the repository
git clone https://github.com/your-org/ai-pr-reviewer-copilot.git

# Navigate to project
cd ai-pr-reviewer-copilot

# Open in your preferred editor
code .
```

### Adding New Language Support
1. Add language patterns to `languagePatterns` object
2. Define security, performance, and logic rules
3. Add language to dropdown options
4. Update documentation

### Example: Adding Go Support
```javascript
languagePatterns.go = {
  security: [
    {
      pattern: /fmt\.Sprintf\(.*%s.*\)/gi,
      severity: 'medium',
      title: 'Potential Format String Vulnerability',
      description: 'Using user input in format strings can be dangerous.',
      suggestion: 'Validate and sanitize user input before formatting.',
      score: -10,
      copilotFix: true
    }
  ]
};
```

## 📊 Supported Issue Types

| Category | Issue Types | Copilot Fixes |
|----------|-------------|---------------|
| **Security** | SQL Injection, XSS, Code Injection, Command Injection | ✅ |
| **Performance** | N+1 Queries, Inefficient Loops, Memory Leaks | ✅ |
| **Logic** | Assignment vs Comparison, Type Coercion, Unreachable Code | ✅ |
| **Quality** | Documentation, Naming Conventions, Code Style | ✅ |

## 🔄 Changelog

### Version 2.0.0 (Current)
- ✨ Added GitHub Copilot integration
- ✨ Multi-platform support (GitHub, GitLab, CLI)
- ✨ Enhanced security vulnerability detection
- ✨ Auto-fix functionality with Copilot suggestions
- 🐛 Improved error handling and user feedback

### Version 1.0.0
- 🎉 Initial release with basic code analysis
- 📊 Quality scoring system
- 🔍 Multi-language support

## 📞 Support

### Documentation
- [GitHub API Documentation](https://docs.github.com/en/rest)
- [GitLab API Documentation](https://docs.gitlab.com/ee/api/)
- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)

### Issues and Bugs
Please report issues on our [GitHub Issues](https://github.com/your-org/ai-pr-reviewer-copilot/issues) page.

### Community
- 💬 [Discussions](https://github.com/your-org/ai-pr-reviewer-copilot/discussions)
- 📧 Email: support@ai-pr-reviewer.com
- 🐦 Twitter: [@AICodeReviewer](https://twitter.com/AICodeReviewer)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **GitHub Copilot** for AI-powered code suggestions
- **GitHub API** for seamless PR integration
- **GitLab API** for merge request support
- **Open Source Community** for inspiration and feedback

---

**Made with ❤️ by CODEBLASTERS, for developers**

*Enhance your code review process with AI-powered insights and automated improvements.*
