# SAP AI Core: Prompt Optimization Demo

End-to-end workflow demonstrating **Live Orchestration → Evaluation → Optimization** using SAP AI Core.

---

## Getting Started with SAP Business Application Studio

Before running the notebooks, you need to set up your development environment in SAP Business Application Studio (BAS).

### Step 1: Open BAS and Create a Dev Space

Go to your SAP BTP cockpit and open Business Application Studio. Click **Create Dev Space**.

![Welcome to SAP Business Application Studio](images/image1.png)

### Step 2: Configure the Dev Space

Select **SAP HANA Native Application** and make sure to also select **"Python Tools"**. Give the space a recognizable name.

![Select Python Tools](images/image2.png)

![Create a New Dev Space](images/image3.png)

### Step 3: Wait for Dev Space to Start

It will take a few minutes for the Dev Space to start up. The status can be seen beside the name. Once the status changes to **Running**, click on the name to open it.

### Step 4: Close the Welcome Screen

If the Welcome screen for SAP HANA appears, click the **X** icon on the Welcome tab to close it.

![Welcome to SAP HANA screen](images/image4.png)

### Step 5: Clone the Repository

On the Get Started landing page of BAS, select the option **Clone from Git** to import a repository from Github.

Enter the URL: `https://github.com/drettstadt/CareerStarter`

### Step 6: Open the Notebook

Click on **RAG_Example.ipynb** (or your target notebook) to open the workbook.

![RAG_Example.ipynb in explorer](images/image5.png)

### Step 7: Create a Virtual Environment

When asked for a kernel, select **"Python Environments"**.

![Select Another Kernel](images/image6.png)

Select **"Create Python Environment"**.

![Create Python Environment](images/image7.png)

Select **Venv** (Python 3.11.2).

![Select environment type](images/image8.png)

### Step 8: Run the Notebook

Follow the steps in the notebook:
- Execute a cell with `CTRL+ENTER`
- Execute a cell and jump to the next cell with `SHIFT+ENTER`

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

Open `hackathon_minimal.ipynb` and run cells sequentially:

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