# 🧠 Text2SQL-LLM-Finetuning

Fine-tuning a **BART-based Large Language Model (LLM)** to translate **natural-language questions into SQL queries**, enabling intuitive database interaction without manual coding.

---

## 🎯 Goal
To build an **AI-powered Text-to-SQL translator** by fine-tuning `facebook/bart-base` using a synthetic dataset, demonstrating how transfer learning enables domain-specific structured generation.

---

## 💡 Idea
Converting plain English queries (e.g., *"List all orders in 2023"*) into valid SQL code (e.g., `SELECT * FROM orders WHERE YEAR(date)=2023;`) via **LLM fine-tuning** — bridging the gap between human language and database syntax.

---

## ⚙️ Tech Stack
| Component | Tool | Purpose |
|------------|------|----------|
| Model | `facebook/bart-base` | Sequence-to-sequence LLM for generation |
| Frameworks | PyTorch, Hugging Face Transformers | Fine-tuning and training |
| Optimization | Accelerate, PEFT | Efficient GPU usage & parameter tuning |
| Dataset | Gretel Synthetic Text-to-SQL | Labeled natural → SQL pairs |
| Evaluation | BLEU (via `evaluate`) | Measures accuracy of generated SQL |
| Interface | Gradio | Real-time model testing and visualization |

---

## 🧩 Problem & Solution
| Problem | Solution |
|----------|-----------|
| Manual SQL writing limits access to data | Automate SQL generation from natural queries |
| Generic LLMs lack schema/domain understanding | Fine-tune BART on domain-specific Text-to-SQL data |
| Uninterpretable outputs | Use BLEU metrics and side-by-side Gradio UI for transparency |

---

## 🧠 Algorithm
1. **Data Preprocessing** – Tokenize input (`sql_prompt`) and target (`sql`) using `BartTokenizer` with padding/truncation.  
2. **Model Setup** – Load pretrained `facebook/bart-base`.  
3. **Fine-Tuning** – Use `Seq2SeqTrainer` with learning rate `2e-5`, batch size `16`, epochs `4`.  
4. **Evaluation** – Compute BLEU score on 500 test samples.  
5. **Inference** – Deploy model with Gradio to compare base vs fine-tuned predictions.  

---

## 🔍 Why This Tech Stack
- **BART**: Combines BERT’s bidirectional encoder with GPT’s autoregressive decoder → ideal for structured generation.  
- **Hugging Face**: High-level abstractions for fine-tuning and deployment.  
- **PEFT & Accelerate**: Optimize training speed and memory efficiency.  
- **Gradio**: Instant demo UI for testing model outputs.  

---

## 🧮 Implementation Steps
```bash
# 1. Install dependencies
pip install -r requirements.txt

# 2. Run fine-tuning notebook
jupyter notebook LLMFinetuning.ipynb

# 3. Launch Gradio demo
python -m gradio app
```
---
## Key Results

- BLEU Score: ↑ 20.04 (vs base 13.13)

- Correctly generated SQL for aggregation & filtering queries

- Clear improvement in structure learning and keyword accuracy
  
---
## 🚀 Impact

Empowers non-technical users to query databases naturally — applicable in Business Intelligence, Analytics, and Low-Code AI systems.

---

## Author

Sanika Dhayabar
