# Playwright MCP Configuration

A collection of configuration files and instructions to get started with the Playwright MCP server using various MCP clients.

## Prerequisites

* Node.js v18 or newer
* One of the following MCP-supported clients:

  * VS Code or VS Code Insiders
  * Cursor
  * Windsurf
  * Claude Desktop

## Repository Contents

* `settings.json` — Example client configuration for launching Playwright MCP
* `README.md` — This file
* `.gitignore` — Recommended ignore rules

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/playwright-mcp-config.git
   cd playwright-mcp-config
   ```

2. **Install & Launch the MCP Server:**

   ```bash
   npx @playwright/mcp@latest
   ```

   Add `--help` to see other options:

   ```bash
   npx @playwright/mcp@latest --help
   ```

3. **Configure your MCP client:**

   In your client’s settings (e.g., `settings.json` for VS Code), add:

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

4. **Persistent vs. Isolated Sessions**

   * **Persistent** (default): retains browser profile across sessions.
   * **Isolated**: fresh profile each session, pass `--isolated` and `--storage-state`:

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

5. **Advanced Options**

   Append additional CLI flags in the `args` array:

   * `--port <port>`: specify custom SSE port
   * `--headless`: run without UI
   * `--device "iPhone 15"`: emulate device
   * `--vision`: enable screenshot-based vision mode
   * and more (see `--help`)

## .gitignore

```
node_modules/
.DS_Store
```

## Contributing

Feel free to open issues or submit pull requests.

## License

[MIT](LICENSE)
