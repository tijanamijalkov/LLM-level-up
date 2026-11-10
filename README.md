# Business Document Analysis AI Assistant

An advanced, multi-step LLM workflow for automated business document processing, classification, structured data extraction, fact-based summarization, and robust Python validation. 

This project was developed as part of the advanced-level **Prompt Engineering and AI Tools** module at **[Level Up Academy](https://levelup-academy.co/)**.

---

## 🚀 Key Features

- **Automated Document Classification:** Accurately categorizes short business documents into four core types—*Request* (`zahtev`), *Minutes* (`zapisnik`), *Memo* (`dopis`), and *Offer* (`ponuda`)—or flags them as *Unknown* (`nepoznato`) without forced categorization.
- **Structured Data Extraction:** Extracts key entities and metadata into a standardized JSON format, including document date (`YYYY-MM-DD`), organizations, participants, detailed tasks (with activity, responsible party, and deadline), and identified conflicts.
- **Fact-Based Summarization:** Generates concise, informative summaries grounded exclusively in the original document text and extracted structured data, preventing hallucinations.
- **Prompt Injection Defense:** Safely treats instructions embedded within documents as inert content rather than executable commands, successfully neutralizing injection attacks.
- **Contradiction Detection & Self-Check:** Employs an LLM-based self-check mechanism combined with a Python validator to catch conflicting statements (e.g., conflicting meeting dates) and flag them.
- **Automated Workflow & Validation:** Implements a multi-step pipeline where a Python validator checks JSON syntax, required fields, data types, and date formats, automatically assigning an operational status (`ok` or `needs_review`).

---

## 🛠️ Project Architecture & Workflow

The pipeline decouples the document analysis task into distinct, manageable components to ensure high accuracy and reliable validation:

1. **Classification:** Determines the document category using a strict system prompt.
2. **Extraction:** Extracts structured JSON data based on the identified document type.
3. **Summarization:** Combines original text and extracted metadata to synthesize a factual summary.
4. **LLM Self-Check:** Scans for internal contradictions and inconsistencies.
5. **Python Validation & Decision Logic:** Validates the final payload against a strict schema. If missing required fields, invalid dates, or contradictions are found, the status is automatically set to `needs_review`.

---

## 🧰 Tech Stack

- **Language:** Python 3.12+
- **Environment:** Jupyter Notebook (`.ipynb`)
- **LLM Provider:** Groq API
- **Model:** `openai/gpt-oss-20b`
- **Libraries:** `urllib`, `json`, `re`, `time`, `datetime`, `pandas`

---

## 📦 Installation & Usage

### Prerequisites
- Python 3.10 or higher
- A valid **Groq API Key** (obtainable from the [Groq Console](https://console.groq.com/))

### Setup Steps

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/business-document-analysis-ai-assistant.git
   cd business-document-analysis-ai-assistant
   ```

2. Open the Jupyter Notebook environment:
   ```bash
   jupyter lab
   ```
   *(Or open `Domaci.ipynb` using your preferred Jupyter interface).*

3. Run the cells sequentially. When prompted by `getpass`, enter your Groq API key securely:
   ```text
   Unesi Groq API kljuc: [Your Groq API Key]
   ```

---

## 📊 Test Cases & Evaluation

The system was rigorously tested across five synthetic benchmark documents (`D1`–`D5`) covering edge cases:
- **D1 (Complete Request):** Full data extraction, successful classification (`ok`).
- **D2 (Missing Date):** Correctly flags missing mandatory fields and assigns `needs_review`.
- **D3 (Conflicting Information):** Detects and logs contradictory meeting dates, triggering `needs_review`.
- **D4 (Prompt Injection):** Successfully ignores malicious embedded instructions and maintains valid JSON output.
- **D5 (Unknown Document Type):** Classifies unrecognized internal memos correctly without hallucinating tasks.

Compared to a baseline single-prompt approach, the multi-step workflow guarantees structural consistency, enforces robust error handling, and reliably manages automated status flagging.

---

## Authors

* **Vera Vlaški** ([@veravlashki](https://github.com/veravlashki))
* **Tijana Mijalkov** ([@tijanamijalkov](https://github.com/tijanamijalkov))
* **Jelena Vu;kovi'** ([@jelennavuckovic](https://github.com/jelennavuckovic))'
* **Tamara ** ({}())
