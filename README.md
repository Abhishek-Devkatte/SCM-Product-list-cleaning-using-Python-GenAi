# 🧠 Supply Chain Management (SCM) Product List Cleaning using GenAI (Python + Groq API)

## 📌 Project Overview

This project focuses on automating the cleaning and structuring of raw Supply Chain product master data using Generative AI (Groq API) integrated within a Python ETL pipeline.

The objective was to convert messy and inconsistent product names into structured fields:

- `main_product`
- `product_type`
- `SKU`

The solution uses prompt engineering and structured JSON responses to generate consistent and usable product master data.

---

# 🚀 Problem Statement

The SCM master product list contained:

- Inconsistent naming formats
- Embedded SKU values (e.g., "50g", "Rs.10", "6PCS")
- Mixed casing
- Spelling errors (e.g., "Mashroom", "Agarwatti")
- Random spacing
- Brand + variant merged together

Manual cleaning was:

- Time consuming
- Error prone
- Difficult to scale
- Inconsistent across large datasets

---

# 🛠 Solution Architecture

### 🔹 Technology Stack

- Python
- Groq API
- Generative AI
- Pandas
- JSON parsing
- Prompt Engineering
- Chunk-based saving
- Resume-safe processing logic

---

# 🧠 GenAI Prompt Engineering Logic

The system prompt was designed to:

1. Identify SKU information first, such as numbers, price, weight, or quantity.
2. Extract the main product or primary product identity.
3. Extract the product type or descriptive variant.
4. Correct common spelling errors.
5. Normalize product names and values.
6. Return the result in a structured JSON format.

### Example:

**Input:**

```text
Oyester Mashroom

Output:

{
  "main_product": "Oyster Mushroom",
  "product_type": "",
  "SKU": ""
}

Input:

Parle-G Gold Biscuits -10 RS

Output:

{
  "main_product": "Parle-G",
  "product_type": "Gold Biscuits",
  "SKU": "10 RS"
}
🔄 ETL Pipeline Design
1️⃣ Data Extraction
Loaded the raw CSV product master file using Pandas.
Identified the product name column.
Handled missing or invalid rows before making API calls.
2️⃣ Transformation — AI-Based Cleaning
Sent individual product strings to the Groq API.
Used prompt engineering to extract structured product information.
Requested JSON-formatted responses from the AI model.
Parsed the AI response and converted it into structured fields.
Implemented retry logic for temporary API failures.
3️⃣ Incremental Loading
Implemented incremental/chunk-based saving.
Saved processed records to an output CSV.
Added resume capability so previously processed rows do not need to be processed again.
Helped prevent data loss during long-running processing jobs.
📊 Key Features

✔ AI-based structured product extraction

✔ Automatic spelling correction

✔ SKU detection for weight, price, and quantity

✔ Structured JSON output

✔ Product name normalization

✔ Chunk-based/incremental saving

✔ Resume-safe execution

✔ API error handling and retry mechanism

✔ CSV-based batch processing

📈 Business Impact
Reduced manual product cleaning effort.
Standardized product master naming.
Improved consistency of product data.
Made product data more suitable for downstream analytics.
Enabled structured SKU-level information extraction.
Helped prepare raw SCM product data for inventory, sales, and reporting workflows.
🧪 Example Workflow
Raw Product CSV
       ↓
Read Product Names
       ↓
Validate Input
       ↓
Send Product Name to Groq API
       ↓
AI-Based Cleaning
       ↓
Structured JSON Response
       ↓
Extract Product / Type / SKU
       ↓
Save Cleaned Data
       ↓
Cleaned CSV
🧩 Why This Project is Important

This project demonstrates the practical use of Generative AI in a data engineering and Supply Chain Management workflow.

It demonstrates experience with:

Generative AI API integration
Prompt engineering
Structured data extraction
JSON parsing
Python automation
ETL pipeline design
Data cleaning and standardization
CSV processing
Error handling
Resume-safe batch processing
🏷 Tech Keywords

Python, Groq API, Generative AI, Prompt Engineering, JSON Parsing, ETL Pipeline, Data Cleaning, Supply Chain Analytics, Pandas, Automation, CSV Processing