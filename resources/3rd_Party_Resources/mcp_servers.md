# Model Context Protocol (MCP) Servers

## What is a Model Context Protocol (MCP) Server?

The Model Context Protocol (MCP) is an open standard introduced by Anthropic that enables developers to build secure, two-way connections between AI models and external data sources or tools.

An **MCP Server** acts as a bridge or proxy between an AI assistant (the MCP client) and specific local or remote resources. Instead of an AI being restricted to only the information it was trained on, or relying on ad-hoc integrations for every single tool, MCP provides a unified, standardized interface. When an AI needs to read a file, query a database, or perform an action, it asks the MCP Server to do it on its behalf.

### Key Capabilities of MCP Servers:

1.  **Resources (Data Access):** Servers can expose files, database records, API responses, or other data sources as "resources" that the AI can read. This allows the AI to have real-time context about a user's local environment or private systems.
2.  **Tools (Actions):** Servers can define specific functions or actions that the AI can execute. For example, a GitHub MCP server might expose a tool to "create a pull request" or a local file system server might expose a tool to "write to a file".
3.  **Prompts (Templates):** Servers can provide pre-defined prompt templates that help guide the AI's behavior for specific tasks within the context of the server's domain.
4.  **Standardization:** Because MCP is standardized, any MCP-compatible client (like Claude Desktop, Cursor, or an AX agent) can connect to any MCP Server without needing custom integration code for that specific server.

### How it Works (Briefly):

1.  An **MCP Client** (e.g., Claude) connects to an **MCP Server** over a transport layer (like standard input/output (stdio) for local servers, or Server-Sent Events (SSE) for remote servers).
2.  The client discovers what tools, resources, and prompts the server offers.
3.  When a user asks the AI a question that requires external data, the AI decides to use one of the server's tools or resources.
4.  The client sends a standard MCP request to the server.
5.  The server executes the request (e.g., queries a database) and returns the result in a standard format.
6.  The AI uses that result to generate a response for the user.

---

## Resources for Learning and Building MCP Servers

If you want to dive deeper into how MCP servers work or build your own, these resources are invaluable:

*   **Official MCP Documentation:** [https://modelcontextprotocol.io/](https://modelcontextprotocol.io/)
    *   The definitive guide to the protocol, including quickstarts, tutorials, and full API references.
*   **Anthropic's Introduction to MCP Course:** [https://anthropic.skilljar.com/introduction-to-model-context-protocol](https://anthropic.skilljar.com/introduction-to-model-context-protocol)
    *   A structured course by Anthropic covering MCP architecture, building servers in Python, and using the MCP Inspector.
*   **MCP GitHub Organization:** [https://github.com/modelcontextprotocol](https://github.com/modelcontextprotocol)
    *   Contains the core SDKs (TypeScript, Python, Java, Kotlin) and official server implementations.
*   **Building Your First Server (Python):** [https://modelcontextprotocol.io/quickstart/server](https://modelcontextprotocol.io/quickstart/server)
    *   A practical guide to getting a basic server running.
*   **MCP Inspector:** [https://github.com/modelcontextprotocol/inspector](https://github.com/modelcontextprotocol/inspector)
    *   A crucial tool for testing and debugging your custom MCP servers before connecting them to an AI client.

---

## Popular MCP Servers

The ecosystem of MCP servers is growing rapidly. Here are some of the most popular and useful servers available today, many of which can be found in the official [MCP Servers Repository](https://github.com/modelcontextprotocol/servers):

### Developer & Version Control
*   **GitHub (`@modelcontextprotocol/server-github`)**: Allows AI to interact with GitHub APIs to read repositories, create issues, review PRs, and manage branches.
*   **GitLab (`@modelcontextprotocol/server-gitlab`)**: Similar to the GitHub server, but for GitLab repositories and CI/CD pipelines.

### File System & Local Environment
*   **Filesystem (`@modelcontextprotocol/server-filesystem`)**: Gives the AI secure, controlled access to read and write files within specific directories on your local machine.
*   **Memory (`@modelcontextprotocol/server-memory`)**: A knowledge graph memory server that allows the AI to store, remember, and retrieve information across sessions.

### Databases & Search
*   **PostgreSQL (`@modelcontextprotocol/server-postgres`)**: Enables the AI to connect to a PostgreSQL database, inspect the schema, and run read-only queries to analyze data.
*   **SQLite (`@modelcontextprotocol/server-sqlite`)**: Similar to the Postgres server, but for local SQLite databases.
*   **Brave Search (`@modelcontextprotocol/server-brave-search`)**: Gives the AI the ability to perform web searches to retrieve real-time, up-to-date information from the internet.

### Productivity & Tools
*   **Google Drive (`@modelcontextprotocol/server-gdrive`)**: Allows the AI to search, read, and interact with documents stored in Google Drive.
*   **Slack (`@modelcontextprotocol/server-slack`)**: Enables reading messages from channels and interacting within Slack workspaces.
*   **Puppeteer (`@modelcontextprotocol/server-puppeteer`)**: Allows the AI to control a headless browser to navigate websites, scrape data, or perform automated web tasks.

*(Note: The community is constantly building new servers for platforms like Notion, Jira, Linear, and more. Checking the official repository or community directories is the best way to find new integrations.)*
