# SAP AI Core: Prompt Optimization Demo

End-to-end workflow demonstrating **Live Orchestration → Evaluation → Optimization** using SAP AI Core.

---

## Getting Started with SAP Business Application Studio

Before running the notebooks, you need to set up your development environment in SAP Business Application Studio (BAS).

### Step 1: Open BAS and Create a Dev Space

1. Open **[Business Application Studio](https://innovation-hub-ai.eu12cf.int.applicationstudio.cloud.sap/)**
2. Click **Create Dev Space**

### Step 2: Configure the Dev Space

1. Select **SAP HANA Native Application**
2. Also select **Python Tools**
3. Give the space a recognizable name
4. Click **Create Dev Space**

### Step 3: Wait for Dev Space to Start

1. Wait for the status to change to **Running** (takes a few minutes)
2. Click on the Dev Space name to open it

### Step 4: Close the Welcome Screen

If the SAP HANA Welcome screen appears, click the **X** icon to close it.

### Step 5: Clone the Repository

1. On the Get Started page, select **Clone from Git**
2. Enter the URL: `https://github.com/Batke96/benchmarking-tutorial`

### Step 6: Open the Notebook

Click on **hackathon_minimal.ipynb** to open the workbook.

### Step 7: Create a Virtual Environment

1. When prompted for a kernel, select **Python Environments**
2. Select **Create Python Environment**
3. Select **Venv** (Python 3.11.2)

### Step 8: Run the Notebook

- Execute a cell: `Ctrl+Enter`
- Execute and advance: `Shift+Enter`

---

## Prerequisites

- Python 3.10+
- SAP AI Core instance with Generative AI Hub enabled
- AWS S3 bucket for dataset storage
- Orchestration service deployment URL

## Setup

Create a `.env` file in the same directory as the notebook:

```env
AICORE_AUTH_URL=<your-auth-url>
AICORE_CLIENT_ID=<your-client-id>
AICORE_CLIENT_SECRET=<your-client-secret>
AICORE_BASE_URL=<your-aicore-url>
AICORE_RESOURCE_GROUP=default
ORCHESTRATION_DEPLOYMENT_URL=<your-orchestration-url>
AWS_ACCESS_KEY_ID=<your-aws-key>
AWS_SECRET_ACCESS_KEY=<your-aws-secret>
AWS_REGION=<your-region>
AWS_S3_BUCKET=<your-bucket>
```

## Running the Notebook

Open `hackathon_perplexity_shk.ipynb` and run cells sequentially:

| Section | What it does |
|---------|--------------|
| **1. Setup** | Loads environment variables and initializes configuration |
| **2. Prompt & Dataset** | Defines the base prompt template and 30 training examples |
| **3. Live Test** | Tests the orchestration service with a sample customer message |
| **4-5. AI Core Client** | Initializes the API client and uploads datasets to S3 |
| **6. Register Prompts** | Registers prompt templates for optimization and evaluation |
| **7. Evaluation** | *(Optional)* Runs evaluation metrics on the base prompt |
| **8. Optimization** | Executes prompt optimization (~10 min) |
| **9. Results** | Displays baseline vs. optimized prompt scores |

## Expected Output

The optimization improves the prompt's semantic similarity score:

```
Baseline Score: 0.552
Optimized Score: 0.759  (+0.138 improvement)
```

## Customization

- **Prompt Template**: Modify `PROMPT_SPEC` in cell 4
- **Training Data**: Update `DATASET` with your own examples (minimum 25)
- **Target Model**: Change `TARGET_MODEL` in cell 16

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Authentication errors | Verify `.env` credentials |
| Optimization status "DEAD" | Check AI Core logs via SAP BTP cockpit |
| S3 upload fails | Confirm bucket permissions and region |