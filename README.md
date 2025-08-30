# Multi-Agent-System

This project is a **multi-agent system** built using Python and Jupyter Notebook.  
It demonstrates how multiple AI agents can collaborate to solve tasks, leveraging APIs and external tools.

---

## 🚀 Features
- Multi-agent coordination logic
- Integration with external APIs (Google, etc.)
- Memory and feedback handling
- Configurable via `.env` file
- Modular and extensible design

---

## 📂 Project Structure
```
multi_agent.ipynb     # Main notebook
.env.example          # Environment variables template
README.md             # Project documentation
```

---

## ⚙️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/multi-agent-system.git
cd multi-agent-system
```

### 2. Create and Activate a Virtual Environment
```bash
python -m venv venv
source venv/bin/activate   # On Linux/Mac
venv\Scripts\activate      # On Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Configure Environment Variables
Create a `.env` file in the root directory (or copy from `.env.example`):

```env
GOOGLE_API_KEY=your_google_api_key_here
URL=your_service_url_here
USER=your_username_here
USER_ID=your_user_id_here
FEEDBACK_KEY=your_feedback_key_here
```

> ⚠️ **Never commit your `.env` file** to GitHub. Use `.gitignore` to keep it safe.

---

## ▶️ Usage
Run the notebook:

```bash
jupyter notebook multi_agent.ipynb
```

---

## 📌 Notes
- Requires **Python 3.8+**
- Make sure to set valid API keys in `.env` before running
- Extend the system by adding new agents or modifying memory structures

---

## 🛡 License
This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.


---

# .env.example

# API Keys
GOOGLE_API_KEY=your_google_api_key_here

# Service Config
URL=your_service_url_here
USER=your_username_here
USER_ID=your_user_id_here

# Custom Keys
FEEDBACK_KEY=your_feedback_key_here


---

# .gitignore

# Python
__pycache__/
*.pyc
*.pyo
*.pyd
*.so
*.egg-info/
.eggs/
*.log

# Virtual environment
venv/
.envrc
.env

# Jupyter
.ipynb_checkpoints/
*.ipynb_save

# OS files
.DS_Store
Thumbs.db

# IDE files
.vscode/
.idea/

# Data / outputs
*.csv
*.tsv
*.json
*.sqlite
