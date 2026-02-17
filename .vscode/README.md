# VS Code Configuration

This folder contains VS Code workspace settings and MCP server configurations.

## MCP Servers

The `settings.json` file configures MCP (Model Context Protocol) servers that extend GitHub Copilot's capabilities.

### Azure MCP Server

The Azure MCP server provides tools for interacting with Azure resources directly from Copilot Chat.

**Package:** `@azure/mcp` (v2.0.0-beta.19)

**Available Tools:**
- Azure Container Registry (ACR)
- Azure Kubernetes Service (AKS)
- App Configuration
- Application Insights
- App Service
- Azure Developer CLI (azd)
- Bicep schema and best practices
- Cosmos DB
- Event Grid & Event Hubs
- Function App
- Key Vault
- Kubernetes (Kusto)
- Monitor
- MySQL & PostgreSQL
- Redis
- Search
- Service Bus
- SignalR
- Speech
- SQL
- Storage
- And many more...

### Azure DevOps MCP Server

The Azure DevOps MCP server provides tools for interacting with Azure DevOps resources.

**Package:** `@azure-devops/mcp` (v2.4.0)

**Available Tools:**
- Projects and repositories
- Pipelines and builds
- Pull requests
- Work items
- Artifacts
- Service endpoints

### MarkItDown MCP Server

The MarkItDown MCP server converts various document formats to Markdown.

**Package:** `markitdown-mcp` (Python)

**Available Tools:**
- `convert_to_markdown(uri)` - Converts documents from HTTP, HTTPS, file:, or data: URIs to Markdown
- Supports multiple file formats including PDF, DOCX, XLSX, PPTX, images, and more

### Authentication

The Azure MCP server uses Azure authentication. Make sure you're logged in:

```bash
az login
```

Or for Azure Developer CLI:

```bash
azd auth login
```

### Reloading Configuration

After modifying `settings.json`, reload VS Code:
- Press `Cmd+Shift+P` (macOS) or `Ctrl+Shift+P` (Windows/Linux)
- Select "Developer: Reload Window"

Alternatively, restart VS Code completely.

### Adding More MCP Servers

To add additional MCP servers, edit `settings.json` and add entries under `github.copilot.chat.mcp.servers`:

```json
{
  "github.copilot.chat.mcp.servers": {
    "azure": {
      "command": "npx",
      "args": ["-y", "@azure/mcp@2.0.0-beta.19"]
    },
    "your-server": {
      "command": "node",
      "args": ["/path/to/server.js"],
      "env": {
        "API_KEY": "your-key"
      }
    }
  }
}
```

### Verifying MCP Tools

Once configured and reloaded, you can verify the MCP tools are available by asking Copilot to:

**Azure MCP:**
- "List my Azure resource groups"
- "Show my Azure subscriptions"
- "Get Azure best practices for [resource]"

**Azure DevOps MCP:**
- "List my Azure DevOps projects"
- "Show recent builds"
- "List open pull requests"

**MarkItDown MCP:**
- "Convert this PDF to markdown: https://example.com/file.pdf"
- "Convert this document to markdown: file:///path/to/document.docx"

The tools will be automatically invoked when relevant to your questions.
