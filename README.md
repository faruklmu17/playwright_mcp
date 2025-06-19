# Playwright MCP Configuration

This repository contains everything needed to launch and connect to a working Playwright MCP (Model Context Protocol) server.

## ✅ Overview

This setup allows you to automate and inspect web pages using **structured data** instead of screenshots — ideal for LLM-powered tools like Claude, Cursor, and VS Code AI agents.

---

## 🛠️ Prerequisites

* [Node.js](https://nodejs.org/) v18 or newer
* One of the following MCP-compatible clients:

  * VS Code or VS Code Insiders
  * Cursor
  * Claude Desktop

---

## 📁 Repository Contents

* `.vscode/settings.json` — VS Code configuration to launch Playwright MCP
* `package.json` — Includes required MCP dependencies
* `README.md` — This file
* `.gitignore` — Basic Node project ignore rules

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/faruklmu17/playwright_mcp.git 
cd playwright-mcp-config
```

### 2. Install Dependencies

```bash
npm install
```

This installs all required packages, including `@playwright/mcp`.

---

### 3. Start the MCP Server

```bash
npx playwright-mcp --port 3550
```

You should see output like:

```
MCP Server started
Web server started
```

> You can change the port if needed, e.g. `--port=4000`

---

### 4. VS Code MCP Client Configuration

Add this to your `.vscode/settings.json`:

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest",
        "--port=3550"
      ]
    }
  }
}
```

This tells VS Code (or Cursor) how to launch and connect to the MCP server.

---

### 5. Optional: Use Persistent or Isolated Sessions

#### Persistent (default)

The browser state is preserved across sessions.

#### Isolated Example

```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest",
        "--isolated",
        "--storage-state=storage/state.json"
      ]
    }
  }
}
```

---

### 6. Additional Flags

You can enhance your MCP server using optional flags:

| Flag            | Description                                   |
| --------------- | --------------------------------------------- |
| `--port <port>` | Custom port (default is random/OS-assigned)   |
| `--headless`    | Run without browser UI                        |
| `--device`      | Emulate a device (e.g., "iPhone 15")          |
| `--vision`      | Enable screenshot-based vision (if supported) |

Check available flags with:

```bash
npx playwright-mcp --help
```

---

## 📅 Note About Browsers

You do **not** need to install `playwright` or run `npx playwright install` separately. The MCP package handles everything required for browser automation.

---

## 📄 .gitignore

```gitignore
node_modules/
.DS_Store
```

---

## 🤝 Contributing

Pull requests and suggestions are welcome!

---

## 📄 License

[MIT](LICENSE)
