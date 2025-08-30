# Multi-Agent Music Store Assistant

This repository demonstrates a multi-agent system for a digital music store using LangChain, LangGraph, and related libraries. It features agents for music catalog queries, invoice retrieval, customer verification, and long-term memory management.

## Agent Architecture

The system is built around several specialized agents, each responsible for a distinct domain:

### 1. Music Catalog Sub-Agent

- **Purpose:** Handles queries about songs, albums, artists, and playlists in the music catalog.
- **Tools:**  
	- `get_albums_by_artist`: Fetches albums by artist name.
	- `get_tracks_by_artist`: Fetches tracks by artist name.
	- `get_songs_by_genre`: Fetches songs by genre.
	- `check_for_songs`: Checks if a song exists by title.
- **Flow:** Receives user queries, invokes relevant tools, and returns music-related information.

### 2. Invoice Information Sub-Agent

- **Purpose:** Handles queries about customer invoices and purchases.
- **Tools:**  
	- `get_invoices_by_customer_sorted_by_date`: Retrieves invoices for a customer, sorted by date.
	- `get_invoices_sorted_by_unit_price`: Retrieves invoices sorted by unit price.
	- `get_employee_by_invoice_and_customer`: Retrieves employee info associated with an invoice.
- **Flow:** Processes invoice-related queries and returns purchase information.

### 3. Supervisor Agent

- **Purpose:** Routes user queries to the appropriate sub-agent (music or invoice) based on query content.
- **Flow:** Analyzes message history and decides which sub-agent should handle the next step.

### 4. Verification Node

- **Purpose:** Verifies customer identity using customer ID, email, or phone number.
- **Flow:** Extracts identifier from user input, matches it against the database, and confirms account verification.

### 5. Memory Nodes

- **Load Memory:** Loads user preferences (e.g., music interests) from long-term memory.
- **Create Memory:** Updates or creates a user profile based on conversation history and stores music preferences.

### 6. Human Input Node

- **Purpose:** Handles interruptions when additional user input is required (e.g., missing customer ID).

## Graph Structure

The agents and nodes are composed into directed graphs using LangGraph:

- **Music Catalog Sub-Agent Graph:** Handles music queries and tool invocations.
- **Invoice Information Sub-Agent Graph:** Handles invoice queries and tool invocations.
- **Supervisor Graph:** Orchestrates routing between sub-agents.
- **Multi-Agent Verification Graph:** Adds customer verification and memory management to the workflow.
- **Final Multi-Agent Graph:** Integrates verification, memory loading, supervisor routing, and memory updating.

## Configuration

- **API Keys:**  
	- Uses Google Generative AI (`GOOGLE_API_KEY`) loaded from `.env`.
- **Database:**  
	- Loads the Chinook SQLite database into memory for music and invoice data.
- **Memory Store:**  
	- Uses `InMemoryStore` for long-term user profile storage.
- **Checkpointer:**  
	- Uses `MemorySaver` for graph checkpointing.

## How to Run

1. **Install Dependencies:**  
	 - Python 3.8+
	 - `langchain`, `langgraph`, `langchain_google_genai`, `sqlalchemy`, `sqlite3`, `requests`, `pydantic`, `typing_extensions`, `openevals`, `langsmith`

2. **Set Up API Keys:**  
	 - Add your Google Generative AI API key to `.env` as `GOOGLE_API_KEY`.

3. **Run Notebook:**  
	 - Open `multi_agent.ipynb` in VS Code or Jupyter.
	 - Execute cells to initialize agents, run test queries, and view results.

## Evaluation

- **Final Response Evaluation:**  
	- Uses LangSmith datasets and LLM-as-a-judge evaluators to assess agent responses.
- **Single Step Evaluation:**  
	- Tests supervisor routing decisions.
- **Trajectory Evaluation:**  
	- Tracks and evaluates the sequence of agent/node executions.

## Customization

- **Add New Tools:**  
	- Define new functions and decorate with `@tool`.
- **Modify Prompts:**  
	- Update agent/system prompts for different behaviors.
- **Change Routing Logic:**  
	- Adjust supervisor logic to support new sub-agents or workflows.

## File Overview

- `multi_agent.ipynb`: Main notebook with all agent definitions, graph construction, and evaluation logic.
- `.env`: Stores API keys.
