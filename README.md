# Build an MCP Client

An MCP (Model Context Protocol) client application built to connect to a running MCP server, discover its tools and resources, and invoke them over STDIO. This project also implements client-side roots and LLM sampling callback handlers to fully participate in the MCP protocol.

---

## 🎯 Learning Objectives

By the end of this project, the client demonstrates how to:

* Connect to a running MCP server using `ClientSession` over STDIO.
* Implement a **roots callback** to tell the server which directories it can access.
* Implement a **sampling callback** to handle LLM requests delegated from the server.
* Call all three server tools through the MCP protocol and inspect their output.

---

## ⚙️ Environment Setup

Create a virtual environment to keep dependencies isolated.

```bash
pip install virtualenv
virtualenv .venv
source .venv/bin/activate
```

**Note:** On Windows, activate the virtual environment using:

```powershell
.venv\Scripts\Activate.ps1
```

### Install Dependencies

Install the required Python libraries:

```bash
pip install fastmcp==3.1.0 anthropic==0.84.0 mcp==1.25.0
```

---

## 📂 Data and Server Files Setup

Download the required data files and MCP server script.

### 1. Unstructured California Culinary Map

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/R1bTvMI9pdxeQANMlG0FLw/California-Culinary-Map.txt
```

### 2. Structured Restaurant Data

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/7ICBa26h8hCd5ILknBWmqw/structured-restaurant-data.json
```

### 3. Augmented User Reviews

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/suT2dk9gavK-xt2Fo3vodg/augmented-user-review.json
```

### 4. MCP Server Script

```bash
curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/RLIJ4mhqVkQKybAVPrOjow/server.py
```

Ensure that all downloaded files are available in the project directory before running the client.

---

## 🚀 Running the MCP Client

Execute the client script to verify the connection and run the demonstration suite.

```bash
python client.py
```

Make sure the `client.py` file is present in your project directory and that the required environment variables, including your Anthropic API key, are configured.

---

## 🔑 Key Components Implemented

### 1. Roots (`list_roots`)

Declares a root URI pointing to the project directory, allowing the server to understand which filesystem locations the client makes available as roots.

### 2. Sampling (`handle_sampling`)

Handles LLM sampling requests originating from the server through the Anthropic API using the `claude-sonnet-4-20250514` model and returns a `CreateMessageResult`.

### 3. Tool Invocations

Automatically discovers and tests the following MCP server tools:

* `get_restaurant_info` — Retrieves structured information about a restaurant.
* `recommend_by_vibe` — Recommends restaurants based on their atmosphere and vibe.
* `get_review` — Retrieves reviews and related restaurant information.

These tools are invoked through the MCP protocol over STDIO transport.

---

## 🛠️ Technologies Used

* **Python**
* **Model Context Protocol (MCP)**
* **FastMCP**
* **Anthropic API**
* **Claude Sonnet**
* **STDIO Transport**
* **Asynchronous Python**

---

## 👨‍💻 Author

**Abdul Fatir | Data Scientist @ IBM**

Author profile: [Abdul Fatir on Skills Network](https://author.skills.network/instructors/abdul_fatir)
