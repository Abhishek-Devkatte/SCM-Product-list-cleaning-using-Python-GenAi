# 🧠 SCM Product List Cleaning using GenAI

### AI-Powered Product Master Data Cleaning & Standardization

An AI-assisted Python ETL pipeline that cleans and standardizes messy Supply Chain Management (SCM) product master data using the **Groq API** and Generative AI.

---

## 📌 Project Overview

Supply Chain product master data often contains inconsistent product names, spelling mistakes, mixed formats, embedded prices, weights, quantities, and product variants.

This project automates the cleaning and structuring of such product data using **Generative AI**.

The system takes a raw CSV file containing product names and converts them into structured fields:

- `main_product`
- `product_type`
- `SKU`

The project combines **Python, Pandas, Generative AI, prompt engineering, JSON parsing, and ETL pipeline concepts** to automate the data-cleaning process.

---

# 🚀 Problem Statement

The raw SCM product master data contained several inconsistencies:

- Inconsistent product naming formats
- Embedded SKU information such as `50g`, `1kg`, `Rs.10`, and `6PCS`
- Mixed uppercase and lowercase characters
- Spelling mistakes such as `Mashroom` and `Agarwatti`
- Random or inconsistent spacing
- Brand names and product variants merged together
- Different naming conventions for similar products

Manual cleaning of this data can be:

- Time-consuming
- Error-prone
- Difficult to maintain
- Difficult to scale for large datasets

The goal of this project is to automate this process using Generative AI.

---

# 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **Python** | Core programming and automation |
| **Groq API** | Generative AI processing |
| **Pandas** | CSV and data processing |
| **JSON** | Structured AI responses |
| **Prompt Engineering** | Product information extraction |
| **Python-dotenv** | Secure API key management |
| **tqdm** | Processing progress tracking |
| **CSV** | Input and output data format |

---

# 🏗️ Solution Architecture

```text
                Raw Product CSV
                       │
                       ▼
              Read Product Data
                       │
                       ▼
             Validate Product Names
                       │
                       ▼
              Prompt Engineering
                       │
                       ▼
                  Groq API
                       │
                       ▼
              Generative AI Model
                       │
                       ▼
             Structured JSON Output
                       │
                       ▼
       ┌───────────────┼───────────────┐
       │               │               │
       ▼               ▼               ▼
 main_product     product_type        SKU
       │               │               │
       └───────────────┼───────────────┘
                       ▼
              Save Processed Data
                       │
                       ▼
                Cleaned CSV
```

---

# 🧠 GenAI Prompt Engineering

The AI prompt is designed to understand the structure of a product name and separate it into meaningful components.

The processing logic focuses on:

1. Identifying SKU information such as weight, quantity, price, or pack size.
2. Extracting the main product or brand/product identity.
3. Identifying the product type or variant.
4. Correcting common spelling mistakes.
5. Normalizing product information.
6. Returning the result in a structured JSON format.

---

## 🔍 Example 1

### Input

```text
Oyester Mashroom
```

### AI Output

```json
{
  "main_product": "Oyster Mushroom",
  "product_type": "",
  "SKU": ""
}
```

---

## 🔍 Example 2

### Input

```text
Parle-G Gold Biscuits -10 RS
```

### AI Output

```json
{
  "main_product": "Parle-G",
  "product_type": "Gold Biscuits",
  "SKU": "10 RS"
}
```

---

# 🔄 ETL Pipeline

## 1️⃣ Data Extraction

The pipeline loads the raw SCM product master CSV using Pandas.

### Processing includes:

- Loading the CSV file
- Identifying the product name column
- Reading product records
- Checking for missing or invalid values
- Preparing records for AI processing

---

## 2️⃣ Transformation — AI-Based Cleaning

Each product name is processed using the Groq API.

The AI transformation process:

```text
Raw Product Name
       ↓
AI Prompt
       ↓
Groq API
       ↓
Structured JSON
       ↓
Product / Type / SKU
```

The pipeline also includes:

- Prompt-based data extraction
- JSON response parsing
- Spelling correction
- Product normalization
- API error handling
- Retry logic

---

## 3️⃣ Incremental Loading

The project uses incremental saving to reduce the risk of losing processed data during long-running API operations.

The system:

- Saves processed records periodically
- Creates an output CSV
- Checks whether an output file already exists
- Detects previously processed rows
- Continues processing from where it stopped

This makes the pipeline **resume-safe**.

---

# 📊 Key Features

### 🤖 AI-Based Cleaning
Uses Generative AI to understand and standardize unstructured product names.

### 🧹 Data Standardization
Converts inconsistent product names into structured information.

### ✏️ Spelling Correction
Corrects common spelling mistakes found in raw product data.

### 📦 SKU Detection
Identifies information such as:

- Weight
- Quantity
- Pack size
- Price
- Number of pieces

### 📋 Structured JSON Output
AI responses are converted into structured JSON fields.

### 💾 Incremental Saving
Processed records are saved periodically to reduce data-loss risk.

### 🔄 Resume-Safe Processing
Previously processed records are detected so processing can continue after an interruption.

### ⚠️ Error Handling
The pipeline includes retry handling for temporary API failures and resource limitations.

### 📈 Progress Tracking
`tqdm` is used to monitor the progress of product processing.

---

# 📈 Business Use Case

Clean and standardized product master data can support downstream Supply Chain and analytics activities.

Potential applications include:

- Product master standardization
- Inventory analytics
- Sales reporting
- SKU-level analysis
- Product categorization
- Supply Chain dashboards
- Data quality improvement
- Automated data preparation

---

# 🧪 Example Workflow

```text
1. Load raw product CSV
          ↓
2. Read product names
          ↓
3. Validate input data
          ↓
4. Send product names to Groq API
          ↓
5. Process using Generative AI
          ↓
6. Receive structured JSON
          ↓
7. Extract main_product, product_type and SKU
          ↓
8. Save cleaned records
          ↓
9. Generate cleaned CSV
```

---

# 📂 Project Structure

```text
SCM-Product-List-Cleaning/
│
├── SCM Product List Cleaning using GenAI.ipynb
├── Product List - Miri product master product list.csv
├── requirements.txt
├── README.md
└── .gitignore
```

### Local-only files

The following files are intentionally excluded from GitHub:

```text
.env
venv/
.ipynb_checkpoints/
```

The `.env` file is used to store the API key securely and should never be committed to the repository.

---

# 🔐 Environment Setup

Create a `.env` file in the project directory:

```env
GROQ_API_KEY=your_api_key_here
```

Install the required dependencies:

```bash
pip install -r requirements.txt
```

Then run the Jupyter Notebook.

---

# ▶️ How to Run

### 1. Clone the repository

```bash
git clone https://github.com/Abhishek-Devkatte/SCM-Product-list-cleaning-using-Python-GenAi.git
```

### 2. Open the project

```bash
cd SCM-Product-list-cleaning-using-Python-GenAi
```

### 3. Create and activate a virtual environment

```bash
python -m venv venv
```

Windows:

```bash
venv\Scripts\activate
```

### 4. Install dependencies

```bash
pip install -r requirements.txt
```

### 5. Configure the API key

Create `.env`:

```env
GROQ_API_KEY=your_api_key_here
```

### 6. Run the notebook

Open:

```text
SCM Product List Cleaning using GenAI.ipynb
```

and execute the cells.

---

# 📤 Input & Output

### Input

A CSV file containing raw product names.

Example:

```text
ProductName
Oyester Mashroom
Parle-G Gold Biscuits -10 RS
Banana Chips 50g
Amul Butter 100gm
```

### Output

A cleaned CSV containing structured information:

| ProductName | main_product | product_type | SKU |
|---|---|---|---|
| Oyester Mashroom | Oyster Mushroom | | |
| Parle-G Gold Biscuits -10 RS | Parle-G | Gold Biscuits | 10 RS |
| Banana Chips 50g | Banana Chips | | 50g |
| Amul Butter 100gm | Amul | Butter | 100gm |

---

# 🧩 What This Project Demonstrates

This project demonstrates practical experience with:

- Generative AI API integration
- Python automation
- Prompt engineering
- Structured data extraction
- JSON parsing
- Pandas
- ETL pipeline design
- Data cleaning
- Data standardization
- CSV processing
- API error handling
- Retry mechanisms
- Incremental data processing
- Resume-safe workflows

---

# 🎯 Project Outcome

The project demonstrates how Generative AI can be integrated into a Python ETL workflow to automate the cleaning and standardization of messy Supply Chain product master data.

Instead of manually cleaning product names one by one, the pipeline uses AI to transform unstructured product names into structured and analytics-ready information.

---

# 🏷️ Tech Keywords

**Python · Groq API · Generative AI · Prompt Engineering · Pandas · JSON · ETL · Data Cleaning · Data Standardization · Supply Chain Analytics · CSV Processing · Automation · API Integration**

---

## 👨‍💻 Author

**Abhishek Devkatte**

GitHub:  
https://github.com/Abhishek-Devkatte
