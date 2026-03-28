Since you are setting up a professional repository for your ThinkingEngine MCP (Model Context Protocol) integration, here is a polished English version of the `README.md`. It is structured to help other developers (or your AI agents) understand exactly how to use these tools.

---

# ThinkingEngine MCP Server

This repository provides a **Model Context Protocol (MCP)** server for the ThinkingEngine (数数科技) data platform. It enables AI models (such as Claude or GPT-based agents) to interact directly with your data analytics environment to perform event analysis, metadata exploration, and custom SQL queries.

## 🚀 Key Features

The MCP server exposes several tools that the AI can call dynamically:

* **Metadata Exploration**:
    * `get_events`: Retrieve all available events reported in the project.
    * `get_properties`: Fetch event and user properties, essential for grouping and filtering in queries.
* **Data Analysis**:
    * `event_analyze`: Perform complex event-based analysis, supporting time ranges, metrics, and multi-dimensional filtering.
    * `sql_analyze`: Execute raw SQL queries using **Trino-standard** syntax for deep-dive data investigation.
* **Productivity Tools**:
    * `generate_sql_template`: Quickly generate SQL templates for common scenarios (e.g., daily active users for specific books or learning modules).
    * `get_today`: Returns the current date to ensure time-sensitive queries are accurate.

## 🛠️ Configuration

### 1. Environment Variables
To ensure security, sensitive information such as the API base URL and Project IDs should be managed via environment variables.

```bash
TE_API_BASE_URL=http://your-internal-gateway.com
TE_PROJECT_ID=3
```

### 2. Integration with Claude Desktop
To add this server to your Claude Desktop environment, update your `claude_desktop_config.json` file:

```json
{
  "mcpServers": {
    "thinking-engine": {
      "command": "npx",
      "args": ["-y", "@your-username/te-mcp-server"],
      "env": {
        "TE_API_BASE_URL": "http://your-sanitized-gateway.com",
        "TE_PROJECT_ID": "3"
      }
    }
  }
}
```

## 📖 Example Usage

Once connected, you can use natural language to interact with your data:

> * "Show me the total count of `handle_pay_success` events over the last 7 days."
> * "List all available user properties in the current project."
> * "Generate a SQL query to find the number of unique learners for 'Word Memorization' yesterday."

## ⚠️ Security & Privacy

* **Sanitization**: Ensure that the `servers.url` in your OpenAPI spec and any specific `eventUuid` values are replaced with placeholders before pushing to a public repository.
* **Access Control**: It is highly recommended to use a read-only API account for the MCP server to prevent accidental data modification.
* **SQL Standards**: All queries passed to the `sql_analyze` tool must comply with **Trino SQL** syntax.

---

### Would you like me to add a "Troubleshooting" section or more specific SQL examples for your education app's data?
