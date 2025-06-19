# Playwright MCP Configuration

A collection of configuration files and step-by-step instructions to help you launch the Playwright MCP server with various supported clients.

## Prerequisites

* Node.js v18 or newer
* One of the following MCP-supported clients:
  * VS Code or VS Code Insiders
  * Cursor
  * Windsurf
  * Claude Desktop

## Repository Contents

* `.vscode/settings.json` — VS Code configuration for launching Playwright MCP
* `package.json` — Defines dependencies including Playwright
* `README.md` — This file
* `.gitignore` — Recommended ignore rules (e.g., `node_modules/`)

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/playwright-mcp-config.git
   cd playwright-mcp-config
   ```

2. **Install Dependencies:**

   This installs Playwright and any other listed dev dependencies.

   ```bash
   npm install
   ```

3. **Launch the MCP Server:**

   ```bash
   npx @playwright/mcp@latest
   ```

   You can add `--help` to see available options:

   ```bash
   npx @playwright/mcp@latest --help
   ```

4. **MCP Client Configuration (VS Code Example):**

   Make sure you have this file in `.vscode/settings.json`:

   ```json
   {
     "mcpServers": {
       "playwright": {
         "command": "npx",
         "args": [
           "@playwright/mcp@latest"
         ]
       }
     }
   }
   ```

   * **command**: How to invoke the MCP server (`npx`)
   * **args**: Package name and any additional flags

5. **Persistent vs. Isolated Sessions**

   * **Persistent** (default): Retains the browser profile across sessions.
   * **Isolated**: Starts a fresh profile each session. Use `--isolated` along with `--storage-state=...` to preserve some session data:

     ```json
     {
       "mcpServers": {
         "playwright": {
           "command": "npx",
           "args": [
             "@playwright/mcp@latest",
             "--isolated",
             "--storage-state=path/to/state.json"
           ]
         }
       }
     }
     ```

6. **Advanced Options**

   You can add more CLI flags in the `args` array:

   * `--port <port>` — Specify a custom SSE port
   * `--headless` — Run without UI
   * `--device "iPhone 15"` — Emulate a specific device
   * `--vision` — Enable screenshot-based vision mode
   * ...and more (see `--help`)

## .gitignore

```gitignore
node_modules/
.DS_Store
```

## Contributing

Feel free to open issues or submit pull requests.

## License

[MIT](LICENSE)
