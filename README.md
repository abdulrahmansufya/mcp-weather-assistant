# MCP Weather Assistant

An educational project demonstrating how to build a weather assistant using the Model Context Protocol (MCP).

The project retrieves real-time weather information and forecasts from OpenWeatherMap and exposes them through MCP tools that can be used by multiple clients.

This project includes:

* MCP Weather Server
* Local Testing Client
* Claude Desktop Client
* Ollama Client
* OpenWeatherMap Integration

---

# Overview

The MCP Weather Assistant allows language models and applications to access real-time weather data through MCP tools.

The weather data is provided by OpenWeatherMap and exposed through the following tools:

* `get_current_weather`
* `get_forecast`

The project demonstrates:

* MCP Server Development
* MCP Tools
* MCP Resources
* MCP Prompts
* Tool Calling
* Claude Desktop Integration
* Ollama Integration
* External API Integration
* Async Python Programming

---

# OpenWeatherMap

This project uses OpenWeatherMap to retrieve weather information.

Official Website:

https://openweathermap.org/

API Documentation:

https://openweathermap.org/api

---

# Getting an OpenWeatherMap API Key

Before running the project, you must create your own API key.

## Step 1

Create an account:

https://home.openweathermap.org/users/sign_up

---

## Step 2

Verify your email address.

---

## Step 3

Log in to your account.

---

## Step 4

Open the API Keys page:

https://home.openweathermap.org/api_keys

---

## Step 5

Create a new API key or use the default key generated for your account.

Example:

```text
1234567890abcdef1234567890abcdef
```

---

## Step 6

Replace the placeholder API key inside the weather server configuration.

Example:

```python
return {
    "base_url": "https://api.openweathermap.org/data/2.5",
    "api_key": "YOUR_API_KEY"
}
```

Important:

API key activation may take several minutes after creation.

---

# Project Structure

```text
mcp-weather-assistant/
│
├── README.md
├── LICENSE
├── pyproject.toml
├── uv.lock
├── weather_server.py
├── weather_server_ollama.py
├── weather_client.py
├── weather_client_ollama.py
└── .gitignore
```

---

# Prerequisites

Install the following:

* Python 3.11+
* UV
* Ollama (for the Ollama client)

---

# Installing UV

## Linux / macOS

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

---

## Windows

Using PowerShell:

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Or install from:

https://docs.astral.sh/uv/getting-started/installation/

---

Verify installation:

```bash
uv --version
```

---

# Clone the Repository

```bash
git clone https://github.com/abdulrahmansufya/mcp-weather-assistant.git
cd mcp-weather-assistant
```

---

# Create and Sync the Environment

Create a virtual environment:

```bash
uv venv
```

Activate it.

## Linux / macOS

```bash
source .venv/bin/activate
```

## Windows (Command Prompt)

```cmd
.venv\Scripts\activate.bat
```

## Windows (PowerShell)

```powershell
.venv\Scripts\Activate.ps1
```

Install project dependencies:

```bash
uv sync
```

---

# Running the MCP Weather Server

Start the server:

```bash
uv run weather_server.py
```

The MCP server will start and expose the weather tools.

---

# Available MCP Tools

## get_current_weather

Returns the current weather conditions for a city.

Examples:

```text
Jeddah
Riyadh
Dubai
Muscat
```

---

## get_forecast

Returns forecast information for upcoming weather periods.

Example:

```text
Forecast for Jeddah
```

---

# Client 1 - Local Testing Client

This client is used to manually test MCP communication.

Run:

```bash
uv run weather_client.py
```

Example workflow:

```text
Enter City name: Jeddah

1. Get current weather
2. Get forecast
```

Choose:

```text
1
```

to retrieve current weather.

Choose:

```text
2
```

to retrieve forecast information.

---

# Client 2 - Claude Desktop

This project can be connected directly to Claude Desktop through MCP.

Example MCP configuration:

```json
{
  "mcpServers": {
    "weather": {
      "command": "uv",
      "args": ["run", "weather_server.py"]
    }
  }
}
```

Restart Claude Desktop after saving the configuration.

Claude should automatically discover:

* get_current_weather
* get_forecast

Example prompts:

```text
What is the weather in Jeddah right now?

Give me the forecast for Riyadh.

What will the weather be like in Dubai?
```

---

# Client 3 - Ollama Client

This client combines a local LLM with MCP weather tools.

## Install Ollama

Official Website:

https://ollama.com/

Verify installation:

```bash
ollama --version
```

---

## Download the Model

Pull Llama 3.2:

```bash
ollama pull llama3.2
```

Verify available models:

```bash
ollama list
```

---

## Run the Ollama Client

```bash
uv run weather_client_ollama.py
```

Example prompts:

```text
What is the weather in Jeddah right now?

What is the forecast for Riyadh?

Will it be hot tomorrow in Dubai?
```

The local model classifies the request and automatically calls the appropriate MCP weather tool when weather information is needed.

---

# Learning Objectives

This project was created for educational purposes and demonstrates:

* MCP Fundamentals
* MCP Tool Development
* MCP Resources
* MCP Prompts
* Tool Calling
* Async Python
* HTTP APIs
* Claude Desktop MCP Integration
* Ollama Integration
* Agent Development Concepts

---