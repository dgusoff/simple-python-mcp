# Simple Python MCP Server for Azure


This is a bare-bones Python based MCP server made for hosting in Azure App Service.


## Getting Started Locally

1. pull this repo down
2. `uv pip install -e .`
3. run `uvicorn server:app --host 0.0.0.0 --port 8000`
4. run `npx @modelcontextprotocol/inspector` to launch the MCP inspector and connect over Streamable HTTP to `http://localhost:8000/mcp`


## Deploy to Azure

1. Create an Azure App Service on Linux targeting Python 3.12
2. Set the startup command to `uvicorn server:app --host 0.0.0.0 --port 8000 --proxy-headers --forwarded-allow-ips=*`
3. set an environment variable `SCM_DO_BUILD_DURING_DEPLOYMENT` to `true`
4. turn on Always On
5. deploy this code using: az webapp up --name app-name --resource-group resource-group-name
6. run the MCP inspector and connect to `https://simple-web-mcp.azurewebsites.net/mcp/`