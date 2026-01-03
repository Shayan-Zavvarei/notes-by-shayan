# Qwen Code CLI - Complete Guide & Tutorial

## Table of Contents
1. [Introduction](#introduction)
2. [Installation](#installation)
3. [Getting Started](#getting-started)
4. [Core Features](#core-features)
5. [Usage Examples](#usage-examples)
6. [Essential Commands](#essential-commands)
7. [Best Practices](#best-practices)
8. [Command Reference](#command-reference)

---

## Introduction

**Qwen Code** is an AI-powered command-line workflow tool for developers that brings intelligent code assistance directly to your terminal. Built on the Qwen3-Coder models, it helps you understand codebases, automate tasks, generate code, and accelerate development workflows.

### Key Capabilities
- **Code Understanding & Editing** - Query and edit large codebases beyond traditional context window limits
- **Workflow Automation** - Automate operational tasks like handling pull requests and complex rebases
- **Vision Model Support** - Analyze images and screenshots in your development workflow
- **Intelligent Testing** - Generate comprehensive unit tests and documentation

---

## Installation

### Prerequisites
Ensure you have Node.js version 20 or higher installed.

### Quick Install
```bash
npm install -g @qwen-code/qwen-code@latest
qwen --version
```

### Alternative Installation Methods

**From Source:**
```bash
git clone https://github.com/QwenLM/qwen-code.git
cd qwen-code
npm install
npm install -g .
```

**Using Homebrew (macOS/Linux):**
```bash
brew install qwen-code
```

---

## Getting Started

### Initial Setup

1. **Launch Qwen Code:**
   ```bash
   qwen
   ```

2. **Authenticate with Qwen OAuth (Recommended):**
   - The CLI will automatically open your browser
   - Login with your qwen.ai account
   - Credentials are cached locally for future use
   - **Free Tier:** 2,000 requests/day, 60 requests/minute

3. **Start in a Project Directory:**
   ```bash
   cd your-project/
   qwen
   ```
   ⚠️ **Note:** Always run Qwen Code in your project directory, not your home directory, for best results.

### Alternative Authentication (OpenAI-Compatible API)

Create a `.env` file in your project root:
```bash
OPENAI_API_KEY=your_api_key_here
OPENAI_BASE_URL=your_api_endpoint
OPENAI_MODEL=your_model_choice
```

**Example for OpenRouter:**
```bash
export OPENAI_API_KEY="your_api_key_here"
export OPENAI_BASE_URL="https://openrouter.ai/api/v1"
export OPENAI_MODEL="qwen/qwen3-coder:free"
```

---

## Core Features

### 1. Code Understanding

Analyze and understand complex codebases:

```bash
> Describe the main pieces of this system's architecture
> What are the key dependencies and how do they interact?
> Find all API endpoints and their authentication methods
```

### 2. Code Generation & Refactoring

Generate new code or improve existing code:

```bash
> Create a REST API endpoint for user management
> Refactor this function to improve readability and performance
> Convert this class to use dependency injection
```

### 3. Testing & Documentation

Automate testing and documentation tasks:

```bash
> Generate unit tests for the authentication module
> Write comprehensive JSDoc comments for all public APIs
> Create API documentation in OpenAPI format
```

### 4. File-Specific Operations

Work with specific files or folders using the `@` symbol:

```bash
> @src/utils/auth.js, explain what this file does
> @tests/, generate additional test cases for this folder
> @components/Button.tsx, add TypeScript types
```

### 5. Workflow Automation

Automate repetitive development tasks:

```bash
> Analyze git commits from the last 7 days, grouped by feature
> Create a changelog from recent commits
> Find all TODO comments and create GitHub issues
```

---

## Usage Examples

### Example 1: Understanding a New Codebase

```bash
cd new-project/
qwen

> What are the core business logic components?
> How does the data flow through the system?
> What are the main design patterns used?
> Generate a dependency graph for this module
```

### Example 2: Debugging and Performance

```bash
> Identify performance bottlenecks in this React component
> Find all N+1 query problems in the codebase
> Check for potential SQL injection vulnerabilities
```

### Example 3: Code Development

```bash
> Create a new Express middleware for rate limiting
> Add error handling to all database operations
> Convert callbacks to async/await pattern
> Implement caching for expensive operations
```

### Example 4: Working with Images

```bash
# Qwen Code can analyze screenshots and diagrams
> @screenshot.png, convert this UI design into React components
> @architecture-diagram.png, explain this system architecture
```

---

## Essential Commands

### Session Management Commands

| Command | Description |
|---------|-------------|
| `/help` | Display all available commands |
| `/clear` | Clear conversation history and start fresh |
| `/compress` | Compress conversation history to save tokens |
| `/stats` | Check current token usage and session limits |
| `/exit` or `/quit` | Exit Qwen Code |
| `/auth` | Switch to Qwen OAuth authentication |

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+C` | Cancel current operation |
| `Ctrl+D` | Exit Qwen Code (on empty line) |
| `Up/Down Arrow` | Navigate through command history |

---

## Best Practices

### 1. Be Specific in Your Requests
❌ **Bad:** "Fix the code"  
✅ **Good:** "Refactor the authentication function in @src/auth.js to use async/await and add proper error handling"

### 2. Use Project-Specific Context
Always run Qwen Code from your project directory to give it full context of your codebase.

### 3. Review Before Applying Changes
Qwen Code operates in "human-in-the-loop" mode by default - always review suggested changes before confirming.

### 4. Manage Token Usage
- Use `/stats` to monitor token consumption
- Use `/compress` when approaching session limits
- Configure session token limits in `.qwen/settings.json`

### 5. Leverage File References
Use the `@` symbol to reference specific files or folders:
```bash
> @src/components/, what components need PropTypes?
> @package.json, what dependencies are outdated?
```

---

## Command Reference

### Quick Command Cheatsheet

```bash
# Start Qwen Code
qwen

# Start with specific vision model behavior
qwen --vlm-switch-mode once     # Switch to vision model for one query
qwen --vlm-switch-mode session  # Switch for entire session
qwen --vlm-switch-mode persist  # Never switch automatically

# In-session commands
/help         # Show all commands
/clear        # Clear conversation history
/compress     # Compress history to save tokens
/stats        # Show token usage statistics
/auth         # Switch authentication method
/exit         # Exit Qwen Code
```

### Common Task Commands

#### Code Analysis
```bash
> Describe the architecture of this codebase
> What are the main dependencies?
> Find all unused imports
> Identify code smells and anti-patterns
```

#### Code Generation
```bash
> Generate a CRUD API for [entity name]
> Create unit tests for @src/utils/helper.js
> Add TypeScript interfaces for this module
> Implement error handling for all async functions
```

#### Refactoring
```bash
> Refactor this component to use hooks
> Convert this code to follow SOLID principles
> Split this large file into smaller modules
> Remove code duplication in this directory
```

#### Documentation
```bash
> Generate README for this project
> Add JSDoc comments to all functions
> Create API documentation
> Explain complex algorithms with comments
```

#### Security & Performance
```bash
> Check for security vulnerabilities
> Find performance bottlenecks
> Identify memory leaks
> Audit dependencies for known issues
```

#### Git & Workflow
```bash
> Generate changelog from recent commits
> Create pull request description
> Find all TODOs and FIXMEs
> Analyze commit history for this feature
```

---

## Configuration

### Session Token Limit

Create or edit `.qwen/settings.json` in your home directory:

```json
{
  "sessionTokenLimit": 32000
}
```

### Vision Model Configuration

Configure automatic vision model switching:

```json
{
  "experimental": {
    "vlmSwitchMode": "once",
    "visionModelPreview": true
  }
}
```

**Vision modes:**
- `"once"` - Switch to vision model for one query, then revert
- `"session"` - Switch for entire session
- `"persist"` - Continue with current model (no switching)

### Disable Vision Models

```json
{
  "experimental": {
    "visionModelPreview": false
  }
}
```

---

## Tips & Tricks

1. **Chain Commands:** You can ask follow-up questions to refine results
2. **Use Context:** Reference previous responses by saying "the function you just showed me"
3. **Iterate:** Start with broad questions, then drill down into specifics
4. **Save Tokens:** Use `/compress` when having long conversations
5. **Custom Instructions:** Create `QWEN.md` files in your project to customize behavior

---

## Troubleshooting

### Issue: Permission Denied
**Solution:** Change npm global directory or use sudo (not recommended)

### Issue: High Token Usage
**Solution:** 
- Use `/compress` to compress history
- Use `/clear` to start fresh
- Configure `sessionTokenLimit` in settings

### Issue: Vision Model Not Working
**Solution:** Check that `visionModelPreview` is enabled in settings

### Issue: Slow Response
**Solution:** 
- Ensure you're in the correct project directory
- Check your internet connection
- Verify API key/authentication status

---

## Resources

- **Official Documentation:** https://qwenlm.github.io/qwen-code-docs/en/
- **GitHub Repository:** https://github.com/QwenLM/qwen-code
- **NPM Package:** https://www.npmjs.com/package/@qwen-code/qwen-code
- **Issue Tracker:** https://github.com/QwenLM/qwen-code/issues

---

## Summary

Qwen Code is a powerful AI assistant for developers that lives in your terminal. With its ability to understand large codebases, generate code, automate workflows, and provide intelligent assistance, it can significantly accelerate your development process.

**Get started in 3 steps:**
1. Install: `npm install -g @qwen-code/qwen-code@latest`
2. Navigate to your project: `cd your-project/`
3. Launch: `qwen`

Happy coding! 🚀

---

*Last updated: January 2026*
*Version: Compatible with Qwen Code v0.2.0+*
