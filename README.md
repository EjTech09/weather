### Lesson Notes: Key Aspects of Creating an MCP (weather.py Example)

#### 1. **Imports and Dependencies**
- Import all necessary modules at the top (`typing`, `httpx`, and your MCP server class).
- Make sure you have installed any external libraries (e.g., `httpx`).

#### 2. **MCP Server Initialization**
- Initialize your MCP server with a unique name:
  ```python
  mcp = FastMCP("weather")
  ```

#### 3. **Constants**
- Define constants for API endpoints and user agent strings for clarity and reuse:
  ```python
  NWS_API_BASE = "https://api.weather.gov"
  USER_AGENT = "weather-app/1.0"
  ```

#### 4. **Helper Functions**
- Write reusable helper functions for common tasks (like making HTTP requests).
- Use proper error handling to make your code robust:
  ```python
  async def make_nws_request(url: str) -> dict[str, Any] | None:
      ...
  ```

#### 5. **Formatting Functions**
- Create functions to format raw API data into readable strings for users:
  ```python
  def format_alert(feature: dict) -> str:
      ...
  ```

#### 6. **MCP Tool Handlers**
- Use the `@mcp.tool()` decorator to expose functions as MCP tools.
- Each handler should have a clear docstring explaining its purpose and arguments.
- Example:
  ```python
  @mcp.tool()
  async def get_alerts(state: str) -> str:
      ...
  ```

#### 7. **Error Handling**
- Always check for missing or invalid data and return user-friendly error messages.

#### 8. **Readable Output**
- Format output for clarity, especially when returning lists or summaries.

#### 9. **Main Entry Point**
- Use the `if __name__ == "__main__":` block to start your MCP server:
  ```python
  if __name__ == "__main__":
      mcp.run(transport='stdio')
  ```

---

**Summary Table**

| Aspect                | Why It Matters                                      |
|-----------------------|-----------------------------------------------------|
| Imports               | Ensures all dependencies are available              |
| Server Initialization | Registers your MCP with a unique name               |
| Constants             | Keeps configuration organized and reusable          |
| Helper Functions      | Avoids code duplication, improves maintainability   |
| Formatting Functions  | Makes output user-friendly                          |
| Tool Handlers         | Exposes features to the MCP platform                |
| Error Handling        | Prevents crashes, improves user experience          |
| Readable Output       | Easier for users to understand results              |
| Main Entry Point      | Ensures correct startup of your MCP                 |

---

**Tip:**  
When starting a new MCP, use this file as a template and adjust the API endpoints, formatting, and handlers for your new use case!