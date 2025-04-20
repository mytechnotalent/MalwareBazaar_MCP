# MalwareBazaar_MCP
An AI-driven MCP server that autonomously interfaces with Malware Bazaar, delivering real-time threat intel and sample metadata for authorized cybersecurity research workflows.

<br>

## MCP Tools
#### `get_recent`: Get up to 10 most recent samples from MalwareBazaar.
#### `get_info`: Get detailed metadata about a specific malware sample.
#### `get_file`: Download a malware sample from MalwareBazaar.
#### `get_taginfo`: Get malware samples associated with a specific tag.

<br>

## Step 1: Create a MalwareBazaar APIKEY
https://auth.abuse.ch/user/me

## Step 2: Create `.env`
```bash
MALWAREBAZAAR_API_KEY=<APIKEY>
```

## Step 3a: Create Virtual Env & Install Requirements - MAC/Linux
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
cd MalwareBazaar_MCP
uv init .
uv venv
source .venv/bin/activate
uv pip install -r requirements.txt
```

## Step 3b: Create Virtual Env & Install Requirements - Windows
```bash
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
cd MalwareBazaar_MCP
uv init .
uv venv
.venv\Scripts\activate
uv pip install -r requirements.txt
```

## Step 4a: Add Config to the MCP Client - MAC/Linux
```bash
{
    "mcpServers": {
        "malwarebazaar": {
            "description": "Malware Bazaar MCP Server",
            "command": "/Users/XXX/.local/bin/uv",
            "args": [
                "--directory",
                "/Users/XXX/Documents/MalwareBazaar_MCP",
                "run",
                "malwarebazaar_mcp.py"
            ]
        }
    }
}
```

## Step 4b: Add Config to the MCP Client - Windows
```bash
{
    "mcpServers": {
        "malwarebazaar": {
            "description": "Malware Bazaar MCP Server",
            "command": "uv",
            "args": [
                "--directory",
                "C:\Users\XXX\Document\MalwareBazaar_MCP",
                "run",
                "malwarebazaar_mcp.py"
            ]
        }
    }
}
```

## Step 5: Run MCP Server
```bash
uv run malwarebazaar_mcp.py
```

## Step 6: Run MCP Client & Query
```
Help me understnad the latest hash from Malware Bazaar.
```

## Step 7: Run Tests
```
python -m unittest discover -s tests

uv pip install coverage==7.8.0
coverage run --branch -m unittest discover -s tests
coverage report -m
coverage html
open htmlcov/index.html  # MAC
xdg-open htmlcov/index.html  # Linux
start htmlcov\index.html  # Windows
coverage erase
```

<br>

## License
[Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0)
