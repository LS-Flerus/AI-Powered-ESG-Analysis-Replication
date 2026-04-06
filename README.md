# 🌿 AI-Driven ESG Analysis in Bangladesh's Textile & Apparel Industry

## Overview
The global Textile and Apparel (T&A) industry faces growing pressure to reduce its environmental footprint — producing **92 million tons of waste annually** and contributing to **20% of global water pollution**.  
As a major apparel exporter, **Bangladesh** must integrate transparent **Environmental, Social, and Governance (ESG)** practices to remain globally competitive and meet sustainability standards.

This project presents an **AI and Machine Learning-based framework** to analyze ESG practices among **LEED-certified Bangladeshi T&A factories**, leveraging **Natural Language Processing (NLP)** and **Topic Modeling** to extract, classify, and interpret ESG information.

---

## 🔍 Key Features
- **Automated ESG Text Analysis** using NLP pipelines  
- **Topic Extraction** via Non-Negative Matrix Factorization (NMF)  
- **ESG Category Classification** using Random Forest (achieving 87% accuracy)  
- **Centrality Analysis** linking ESG focus areas with LEED certification levels  
- **Data-Driven Insights** for sustainable manufacturing and responsible sourcing  

---

## 📊 Core Findings
| ESG Category | Focus (%) | Example Themes |
|---------------|------------|----------------|
| 🌱 Environmental Sustainability | 46% | Energy conservation, waste management |
| 🧍‍♀️ Social I – Workplace Safety & Compliance | 28% | Worker safety, compliance standards |
| 🎓 Social II – Education & Community Programs | 16% | Training, community outreach |
| ⚖️ Governance | 10% | Transparency, management accountability |

Factories with **higher certification levels (Platinum)** show a **balanced ESG focus**, while lower-certified ones primarily emphasize **environmental efforts**.

---

## 🧠 Methodology

**1. Data Collection:**  
Textual ESG data extracted from LEED-certified factory reports and sustainability disclosures.  

**2. Preprocessing:**  
- Tokenization and lemmatization  
- Stopword removal and TF-IDF vectorization  

**3. Topic Modeling:**  
- NMF-based topic extraction to uncover latent ESG themes  

**4. Classification:**  
- Random Forest model trained to predict ESG categories  
- Achieved **86% accuracy**, outperforming rule-based and keyword-driven baselines  

**5. Network & Centrality Analysis:**  
- Examined correlations between certification levels and ESG category distributions

## 📦 Requirements
 
```
pandas>=1.3.0
numpy>=1.21.0
scikit-learn>=0.24.0
nltk>=3.6.0
matplotlib>=3.4.0
seaborn>=0.11.0
networkx>=2.6.0
jupyter>=1.0.0


## 🔄 Pipeline Execution Order
 
| Step | Stage | Description |
|---|---|---|
| 1 | Environment Setup | Import libraries and configure settings |
| 2 | Data Loading | Load ESG report dataset, inspect shape and columns |
| 3 | Text Preprocessing | Tokenize, lemmatize, remove stopwords, TF-IDF vectorize |
| 4 | Topic Modeling (NMF) | Extract latent ESG topics, inspect top keywords per topic |
| 5 | Classification (RF) | Train/test split, fit Random Forest, evaluate performance |
| 6 | Network Analysis | Build ESG–LEED correlation network, compute centrality scores |
| 7 | Results & Export | Save plots, export classification report, document findings |
 
## ⚙️ Installation & Setup
 
### Prerequisites
 
- Python 3.8 or higher
- pip package manager
- Jupyter Notebook or JupyterLab
 
### 1. Clone the Repository
 
```bash
git clone https://github.com/your-username/Textile_ML_Pipeline.git
cd Textile_ML_Pipeline
```
 
### 2. (Recommended) Create a Virtual Environment
 
```bash
python -m venv venv
source venv/bin/activate        # Mac/Linux
venv\Scripts\activate           # Windows
```
 
### 3. Install Dependencies
 
```bash
pip install -r requirements.txt
```
 
Or install manually:
 
```bash
pip install pandas numpy scikit-learn nltk matplotlib seaborn networkx jupyter
```
 
### 4. Download NLTK Resources
 
Run this once in a Python shell or notebook cell:
 
```python
import nltk
nltk.download('stopwords')
nltk.download('wordnet')
nltk.download('punkt')
```
 
---
 
## ▶️ Running the Notebook
 
### Option A — Run All Cells (Recommended for Full Pipeline)
 
```bash
jupyter notebook
```
 
Open `Textile_ML_Pipeline.ipynb` in your browser, then go to:
 
```
Kernel → Restart & Run All
```
 
This executes all cells sequentially from a clean state, ensuring full reproducibility.
 
### Option B — Run Cells Individually (Recommended for Debugging)
 
Use `Shift + Enter` to run one cell at a time and inspect intermediate outputs at each stage.
