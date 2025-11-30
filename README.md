<h1 align="center">How to inQueries</h1>
<h3 align="center">Hint: Click anywhere from below poster to watch the Project Demo</h3>

<p>

  <img src="https://img.shields.io/badge/LLM%20(Large%20Language%20Model)-4B0082?style=for-the-badge&logoColor=white" />

  <img src="https://img.shields.io/badge/RAG%20(Retrieval--Augmented%20Generation)-6A5ACD?style=for-the-badge&logoColor=white" />

  <!-- XAI -->
  <img src="https://img.shields.io/badge/Explainable%20AI%20(XAI)-8A2BE2?style=for-the-badge&logoColor=white" />

  <!-- Python -->
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />

  <!-- IOC -->
  <img src="https://img.shields.io/badge/IOC%20(Indicator%20of%20Compromise)-696969?style=for-the-badge&logoColor=white" />

  <!-- urlscan.io -->
  <img src="https://img.shields.io/badge/urlscan.io-1E90FF?style=for-the-badge&logoColor=white" />

  <!-- VirusTotal -->
  <img src="https://img.shields.io/badge/VirusTotal-1683FF?style=for-the-badge&logo=virustotal&logoColor=white" />

  <!-- Llama 3.2 -->
  <img src="https://img.shields.io/badge/Llama%203.2-FF6F00?style=for-the-badge&logoColor=white" />

  <!-- Docker -->
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" />

  <!-- GPU -->
  <img src="https://img.shields.io/badge/GPU-00B386?style=for-the-badge&logo=nvidia&logoColor=white" />

  <!-- Pinecone -->
  <img src="https://img.shields.io/badge/Pinecone-0E6FFF?style=for-the-badge&logo=pinecone&logoColor=white" />

  <!-- JSON -->
  <img src="https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white" />

  <!-- Google Sheets -->
  <img src="https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white" />

  <!-- Google Drive -->
  <img src="https://img.shields.io/badge/Google%20Drive-4285F4?style=for-the-badge&logo=google-drive&logoColor=white" />

  <!-- mxbai-embed-large -->
  <img src="https://img.shields.io/badge/mxbai--embed--large-5A5A5A?style=for-the-badge&logoColor=white" />

  <!-- Ollama -->
  <img src="https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white" />

  <img src="https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white" />

  <!-- n8n -->
  <img src="https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" />

</p>

<a href="https://www.youtube.com/watch?v=IjKu68dhHCk" target="_blank">
  <img src="https://github.com/user-attachments/assets/fd531a89-9f65-46ed-8535-2cc1badae24e" alt="Academic Poster_page-0001">
</a>

# Project Overview
**inQueries** is a lightweight, explainable scam-link detection system built entirely using open-source components and free-tier services. Designed as a Telegram chatbot, the system allows users to submit URLs and receive structured, human-readable safety assessments in real time.

The project demonstrates how **Retrieval-Augmented Generation (RAG)**, **rule-based classification**, **real-time threat-intelligence APIs**, and a **locally hosted LLM** can be combined into a practical, zero-cost cybersecurity tool suitable for public use.

By embedding both detection and natural-language explanation into a familiar messaging interface, inQueries helps bridge the gap between advanced phishing-detection research and everyday user accessibility.

## ✅ Key Features & Contributions

### **1. Public-Facing Phishing Detection**

* Converts cybersecurity research into a Telegram-based chatbot.
* Integrates RAG and explainable AI to produce user-friendly threat summaries.

### **2. Zero-Cost Automated Detection Workflow**

* Built using **n8n**, **VirusTotal**, **urlscan.io**, and **Ollama-hosted LLMs**.
* Entire pipeline operates without recurring costs or commercial infrastructure.

### **3. Explainable Security Feedback**

* Converts technical metadata into accessible explanations using structured prompts.
* Provides clear, human-readable reasoning for each URL assessment.

### **4. Real-Time Threat Alignment via Vector Retrieval**

* Generates summary embeddings using the **mxbai-embed-large** model.
* Stores results in a Pinecone index for semantic retrieval of previously scanned URLs.
* Enhances explanation specificity and system interpretability.

### **5. Rule-Based Risk Classifier**

* Utilizes verified antivirus engine verdicts for threat severity scoring.
* Ensures reliable and transparent decision logic.

### **6. Validated Responsiveness**

* System performance measured under GPU-accelerated local conditions.
* Confirms feasibility for interactive, real-time use.

## ⚠️ Current Limitations

While the prototype meets its core objectives, several constraints remain:

* **API variability**: VirusTotal and urlscan.io response times may fluctuate, especially for shortened or suspicious URLs.
* **Local model latency**: LLaMA-based inference introduces 6–12s processing time, occasionally pushing total response duration beyond 60s.
* **No multi-user testing**: Concurrent interactions and state management were out of scope.
* **Limited explainability evaluation**: No formal user study on clarity or trustworthiness.
* **Prompting constraints**: LLM explanations depend on a hand-crafted prompt without alternative strategies tested.

These limitations do not undermine the proof-of-concept, but identify areas for improvement—particularly for scaling, usability testing, and more advanced retrieval or explanation methods.

# 🛠️ Set Up inQueries on Your Own Machine

### Step 1: Set Up Ngrok (Webhook Tunnel)

1.  Go to [https://ngrok.com](https://ngrok.com), register, and log in.
2.  Download and install Ngrok for Windows.
3.  Open a terminal and add your auth token (found in your Ngrok dashboard):
    ```bash
    ngrok config add-authtoken <YOUR_AUTH_TOKEN>
    ```
4.  In your Ngrok dashboard, set up a **static subdomain** (to avoid reconfiguration after restarts).

5.  **Start the Ngrok tunnel:**
    ```bash
    ngrok http --domain=<your-static-subdomain>.ngrok.io 5678
    ```
    *Note: Replace `5678` with your local n8n port*

### Step 2: Clone the Repository

Clone this project repository and navigate into the directory.

```bash
git clone https://github.com/inqsyira/inQueries.git
cd inQueries/Source Code/self-hosted-n8n_inqVer
````

### Step 3: Run n8n with Docker Compose

Select the appropriate profile based on your hardware. This uses **Ollama** containers to manage the Llama 3.2 model.

  * **For NVIDIA GPU:**
    ```bash
    docker compose --profile gpu-nvidia up 
    ```
  * **For CPU-only:**
    ```bash
    docker compose --profile cpu up 
    ```

### Step 4: Access n8n and Import Workflows

1.  Visit **`http://localhost:5678`** or your **Ngrok URL** in your browser.
2.  Register an account with your email and password.
3.  Create a new workflow and **import** the following files (found in this repository):
      * `Source Code/inQueriesFrontEnd-ver1.json`
      * `Source Code/inQueriesBackEnd-ver1.json`

### Step 5: Configure Node Authentication

#### a. Telegram Setup

1.  Search for **BotFather** on Telegram and create a new bot using `/newbot`. **Copy the API token.**
2.  Open **`docker-compose.yml`** and under the `n8n` service, add the following environment variable:
    ```yaml
    WEBHOOK_URL=https://<your-static-ngrok-subdomain>.ngrok.io
    ```
3.  **Restart Docker** to apply the new environment variable:
    ```bash
    docker compose down
    docker compose up -d
    ```
4.  In the n8n visual editor, open the **Telegram Trigger** node in the imported workflow and verify the webhook URL.
5.  Click **Test** on the node, then send a message to your bot on Telegram to confirm a successful connection.

#### b. API Keys for External Services

  * **VirusTotal:** Register and add your API key in the respective node configuration.
  * **URLScan.io:** Register and configure the key in the respective node configuration.
  * **Google APIs:** Authorize nodes accessing Google Drive, Sheets, and/or Gemini individually. Use valid **OAuth credentials**.

#### c. Pinecone Setup

1.  Go to [https://www.pinecone.io/](https://www.pinecone.io/), sign up, and log in.
2.  **Create an Index** with the following specific configuration for the RAG chain:
      * **Model:** `llma-text-embed-v2`
      * **Dimension:** `1024`
      * **Metric:** `cosine`
      * **Capacity Mode:** `serverless`
      * **Provider/Region:** AWS, `virginia us-east-1` (or your preferred region)
3.  Generate the **API Key** under the **API keys** tab.
4.  In n8n, open the **Pinecone** node in the workflow: paste the API key, select your Pinecone node, and select your index name.

### Step 6: Download and Run LLaMA 3.2 Model via Ollama

1. Go to [https://ollama.com/library/llama3.2:latest](https://ollama.com/library/llama3.2:latest).
2. Copy the command to install or run the model
3. In the Docker container shell:
   ```bash
    docker compose down
    docker compose up -d
    ```

### Step 7: Verify and Activate

1.  Ensure all Telegram nodes use the same bot token created in Step 5.
2.  Use the **Test** button on all individual nodes to confirm all configurations are successful.
3.  **Activate** the `inQueriesFrontEnd-ver1` workflow in n8n.

### Step 8: Start Using inQueries

Send a message or suspicious link to your Telegram bot to initiate the detection workflow.

## 💡 Tip for Future Use

To restart inQueries later:

1.  **Restart Docker Compose** with the correct profile:
    ```bash
    docker compose --profile gpu-nvidia up 
    # OR
    docker compose --profile cpu up 
    ```
2.  **Start Ngrok**:
    ```bash
    ngrok http --domain=<your-static-subdomain>.ngrok.io 5678
    ```
3.  **Open** the Ngrok URL in your browser and log in to n8n.

