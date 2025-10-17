# Packmind MCP Server

MCP server for Packmind API integration, providing AI assistants access to your organization's knowledge base.

## Installation

### Option 1: Using NPX (Recommended)

You can use the package directly via NPX from GitHub Packages:

```bash
npx @PackmindHub/packmind-mcp-server
```

For GitHub Copilot (VSCode), add this to your `.vscode/mcp.json`:
```json
{
  "servers": {
    "packmind": {
      "command": "npx",
      "args": [
        "@PackmindHub/packmind-mcp-server"
      ],
      "env": {
        "PACKMIND_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

For Cursor, go to "Settings -> MCP -> Add a new global MCP server":
```json
{
  "mcpServers": {
    "packmind": {
      "command": "npx",
      "args": [
        "@PackmindHub/packmind-mcp-server"
      ],
      "env": {
        "PACKMIND_API_KEY": "YOUR_API_KEY"
      }
    }
  }
}
```

### Option 2: Building from Source

# Setup
1. Use node 20
2. Run the following command
```
npm install
npm run build
```
# Github Copilot (VSCode)
3. Create a .vscode/mcp.json file
Add a new block `protomind`
```json
{
  "servers": {
      "protomind": {
          "command": "node",
          "args": [
              "<PATH_TO_YOUR_HOME>/mcp-server/build/index.js"
          ]
      }
  }
}
```
# Cursor
3. Go to "Settings -> MCP -> Add a new global MCP server"
Add a new block `packmind`
```json
{
  "mcpServers": {
      "packmind": {
          "command": "node",
          "args": [
              "<PATH_TO_YOUR_HOME>/packmind-mcp-server/build/index.js"
          ],
          "env": {
            "PACKMIND_API_KEY": "YOUR_API_KEY"
          }
      }
  }
}
```

## Publishing

The package is automatically published to GitHub Packages when:
- A new tag starting with `v` is pushed (e.g., `v1.0.1`)
- The workflow is manually triggered via GitHub Actions

To publish a new version:
1. Update the version in `package.json`
2. Create and push a git tag:
   ```bash
   git tag v1.0.1
   git push origin v1.0.1
   ```

