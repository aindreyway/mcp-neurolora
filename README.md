# MCP Neurolora

![MCP Server](https://img.shields.io/badge/MCP-Server-blue)
![Version](https://img.shields.io/badge/version-1.4.0-green)
![License](https://img.shields.io/badge/license-MIT-blue)

An intelligent MCP server that provides tools for code analysis using OpenAI API, code collection, and documentation generation.

<a href="https://glama.ai/mcp/servers/j29osinm43"><img width="380" height="200" src="https://glama.ai/mcp/servers/j29osinm43/badge" alt="mcp-neurolora MCP server" /></a>

## 🚀 Installation Guide

Don't worry if you don't have anything installed yet! Just follow these steps or ask your assistant to help you with the installation.

### Step 1: Install Node.js

#### macOS

1. Install Homebrew if not installed:
   ```bash
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
   ```
2. Install Node.js 18:
   ```bash
   brew install node@18
   echo 'export PATH="/opt/homebrew/opt/node@18/bin:$PATH"' >> ~/.zshrc
   source ~/.zshrc
   ```

#### Windows

1. Download Node.js 18 LTS from [nodejs.org](https://nodejs.org/)
2. Run the installer
3. Open a new terminal to apply changes

#### Linux (Ubuntu/Debian)

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Step 2: Install uv and uvx

#### All Operating Systems

1. Install uv:

   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

2. Install uvx:
   ```bash
   uv pip install uvx
   ```

### Step 3: Verify Installation

Run these commands to verify everything is installed:

```bash
node --version  # Should show v18.x.x
npm --version   # Should show 9.x.x or higher
uv --version    # Should show uv installed
uvx --version   # Should show uvx installed
```

### Step 4: Configure MCP Server

Your assistant will help you:

1. Find your Cline settings file:

   - VSCode: `~/Library/Application Support/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json`
   - Claude Desktop: `~/Library/Application Support/Claude/claude_desktop_config.json`
   - Windows VSCode: `%APPDATA%/Code/User/globalStorage/saoudrizwan.claude-dev/settings/cline_mcp_settings.json`
   - Windows Claude: `%APPDATA%/Claude/claude_desktop_config.json`

2. Add this configuration:
   ```json
   {
     "mcpServers": {
       "aindreyway-mcp-neurolora": {
         "command": "npx",
         "args": ["-y", "@aindreyway/mcp-neurolora@latest"],
         "env": {
           "NODE_OPTIONS": "--max-old-space-size=256",
           "OPENAI_API_KEY": "your_api_key_here"
         }
       }
     }
   }
   ```

### Step 5: Install Base Servers

Simply ask your assistant:
"Please install the base MCP servers for my environment"

Your assistant will:

1. Find your settings file
2. Run the install_base_servers tool
3. Configure all necessary servers automatically

After the installation is complete:

1. Close VSCode completely (Cmd+Q on macOS, Alt+F4 on Windows)
2. Reopen VSCode
3. The new servers will be ready to use

> **Important:** A complete restart of VSCode is required after installing the base servers for them to be properly initialized.

> **Note:** This server uses `npx` for direct npm package execution, which is optimal for Node.js/TypeScript MCP servers, providing seamless integration with the npm ecosystem and TypeScript tooling.

## Base MCP Servers

The following base servers will be automatically installed and configured:

- fetch: Basic HTTP request functionality for accessing web resources
- puppeteer: Browser automation capabilities for web interaction and testing
- sequential-thinking: Advanced problem-solving tools for complex tasks
- github: GitHub integration features for repository management
- git: Git operations support for version control
- shell: Basic shell command execution with common commands:
  - ls: List directory contents
  - cat: Display file contents
  - pwd: Print working directory
  - grep: Search text patterns
  - wc: Count words, lines, characters
  - touch: Create empty files
  - find: Search for files

## 🎯 What Your Assistant Can Do

Ask your assistant to:

- "Analyze my code and suggest improvements"
- "Install base MCP servers for my environment"
- "Collect code from my project directory"
- "Create documentation for my codebase"
- "Generate a markdown file with all my code"

## 🛠 Available Tools

### analyze_code

Analyzes code using OpenAI API and generates detailed feedback with improvement suggestions.

Parameters:

- `codePath` (required): Path to the code file or directory to analyze

Example usage:

```json
{
  "codePath": "/path/to/your/code.ts"
}
```

The tool will:

1. Analyze your code using OpenAI API
2. Generate detailed feedback with:
   - Issues and recommendations
   - Best practices violations
   - Impact analysis
   - Steps to fix
3. Create two output files in your project:
   - LAST_RESPONSE_OPENAI.txt - Human-readable analysis
   - LAST_RESPONSE_OPENAI_GITHUB_FORMAT.json - Structured data for GitHub issues

> Note: Requires OpenAI API key in environment configuration

### collect_code

Collects all code from a directory into a single markdown file with syntax highlighting and navigation.

Parameters:

- `directory` (required): Directory path to collect code from
- `outputPath` (optional): Path where to save the output markdown file
- `ignorePatterns` (optional): Array of patterns to ignore (similar to .gitignore)

Example usage:

```json
{
  "directory": "/path/to/project/src",
  "outputPath": "/path/to/project/src/FULL_CODE_SRC_2024-12-20.md",
  "ignorePatterns": ["*.log", "temp/", "__pycache__", "*.pyc", ".git"]
}
```

### install_base_servers

Installs base MCP servers to your configuration file.

Parameters:

- `configPath` (required): Path to the MCP settings configuration file

Example usage:

```json
{
  "configPath": "/path/to/cline_mcp_settings.json"
}
```

## 🔧 Features

The server provides:

- Code Analysis:

  - OpenAI API integration
  - Structured feedback
  - Best practices recommendations
  - GitHub issues generation

- Code Collection:

  - Directory traversal
  - Syntax highlighting
  - Navigation generation
  - Pattern-based filtering

- Base Server Management:
  - Automatic installation
  - Configuration handling
  - Version management

## 📄 License

MIT License - feel free to use this in your projects!

## 👤 Author

**Aindreyway**

- GitHub: [@aindreyway](https://github.com/aindreyway)

## ⭐️ Support

Give a ⭐️ if this project helped you!
