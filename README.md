# Aminuteman_Task

🚀 How to Run the Project
Prerequisites
Before running the project, ensure you have the following installed on your system:

Required Software:

Python 3.10 or higher - Download Python

Ollama - Install Ollama

Git (optional, for cloning) - Download Git

Required Accounts:

Gmail account with App Password enabled (for email automation)

Vapi or AI Sensy account (optional, for voice integration)

System Requirements:

OS: Windows 10/11, macOS 10.15+, or Linux (Ubuntu 20.04+)

RAM: Minimum 8GB (16GB recommended for Ollama)

Disk Space: 5GB free (for Ollama models)

Internet: Required for initial setup and email sending

Step-by-Step Installation Guide
Step 1: Clone or Download the Repository
Option A: Using Git

bash
git clone https://github.com/yourusername/luxury-automotive-crm.git
cd luxury-automotive-crm
Option B: Manual Download

Download the ZIP file from GitHub

Extract to a folder (e.g., C:\Projects\luxury-crm or ~/projects/luxury-crm)

Open terminal/command prompt in that folder

Step 2: Create Python Virtual Environment
On Windows:

text
python -m venv venv
venv\Scripts\activate
On macOS/Linux:

bash
python3 -m venv venv
source venv/bin/activate
You should see (venv) prefix in your terminal.

Step 3: Install Python Dependencies
bash
pip install --upgrade pip
pip install -r requirements.txt
Expected Output:

text
Successfully installed flask-3.0.0 flask-cors-4.0.0 langgraph-0.2.0 
langchain-core-0.3.0 ollama-0.3.0 reportlab-4.0.0 pytz-2024.1 
python-dotenv-1.0.0 requests-2.31.0
Troubleshooting:

If requirements.txt is missing, create it with the following content:

text
flask==3.0.0
flask-cors==4.0.0
langgraph==0.2.0
langchain-core==0.3.0
ollama==0.3.0
reportlab==4.0.0
pytz==2024.1
python-dotenv==1.0.0
requests==2.31.0
Step 4: Install and Configure Ollama
Install Ollama:

On Windows:

Download installer from https://ollama.com/download/windows

Run OllamaSetup.exe

Follow installation wizard

On macOS:

bash
curl -fsSL https://ollama.com/install.sh | sh
On Linux:

bash
curl -fsSL https://ollama.com/install.sh | sh
Pull LLaMA Model:

bash
ollama pull llama3.2:3b
Expected Output:

text
pulling manifest
pulling 6a0746a1ec1a... 100% ████████████████ 2.0 GB
pulling 4fa551d4f938... 100% ████████████████ 1.4 KB
pulling 8ab4849b038c... 100% ████████████████ 254 B
pulling 577073ffcc6c... 100% ████████████████ 110 B
pulling ad1518640c43... 100% ████████████████ 483 B
verifying sha256 digest
writing manifest
success
Verify Ollama:

bash
ollama list
Expected Output:

text
NAME              ID              SIZE      MODIFIED
llama3.2:3b       6a0746a1ec1a    2.0 GB    5 minutes ago
Start Ollama Server (if not running):

bash
ollama serve
Step 5: Configure Environment Variables
Create a .env file in the project root directory:

bash
# On Windows
copy .env.example .env
notepad .env

# On macOS/Linux
cp .env.example .env
nano .env
Add the following configuration:

text
# ========================================
# FLASK API CONFIGURATION
# ========================================
API_BEARER_TOKEN=your_secure_random_token_here_min_32_chars
PORT=5000

# ========================================
# GMAIL SMTP CONFIGURATION (REQUIRED)
# ========================================
GMAIL_USER=your-email@gmail.com
GMAIL_APP_PASSWORD=your_16_character_app_password

# ========================================
# VOICE PROVIDER (OPTIONAL)
# ========================================
# Options: "vapi" or "sensy" or leave blank to disable
VOICE_PROVIDER=

# Vapi Configuration (if using)
VAPI_API_KEY=
VAPI_BASE_URL=https://api.vapi.ai
VAPI_FLOW_ID=
VAPI_CALLER_ID=+91XXXXXXXXXX

# AI Sensy Configuration (if using)
SENSY_API_KEY=
SENSY_BASE_URL=https://api.aisensy.com
SENSY_CAMPAIGN_ID=

# Webhook URL for voice callbacks
VOICE_WEBHOOK_URL=http://yourdomain.com/voice/webhook
Generate Secure Token:

bash
# On Windows (PowerShell)
-join ((48..57) + (65..90) + (97..122) | Get-Random -Count 32 | % {[char]$_})

# On macOS/Linux
openssl rand -hex 16
Get Gmail App Password:

Go to https://myaccount.google.com/security

Enable 2-Step Verification

Search for "App Passwords"

Select "Mail" and "Other (Custom name)"

Name it "Luxury CRM"

Copy the 16-character password (e.g., abcd efgh ijkl mnop)

Paste in .env file (remove spaces: abcdefghijklmnop)

Step 6: Initialize Database
bash
python -c "from db import init_db; init_db()"
Expected Output:

text
Database initialized successfully!
Tables created: leads, interactions, scheduled_actions
Verify Database:

bash
python check_crm.py
Expected Output:

text
======================================================================
LUXURY CRM DATABASE STATUS
======================================================================
Total Leads: 0
Hot Leads: 0
Qualified: 0
======================================================================
Step 7: Run the Application
Terminal 1: Start Ollama Server (if not already running)

bash
ollama serve
Terminal 2: Start Flask Application

bash
python app.py
Expected Output:

text
 * Serving Flask app 'app'
 * Debug mode: off
WARNING: This is a development server. Do not use it in production.
Use a production WSGI server instead.
 * Running on http://127.0.0.1:5000
Press CTRL+C to quit
📍 Access the Application
Once the server is running, open your web browser and navigate to:

Frontend Pages:

Main Page: http://localhost:5000/

Customer Form: http://localhost:5000/customerform.html

Dashboard: http://localhost:5000/dashboardwhite.html
