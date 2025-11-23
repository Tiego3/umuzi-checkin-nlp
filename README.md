#  Umuzi Student Check-In NLP Analysis

**Natural Language Processing analysis of student feedback to identify trends in wins, losses, and blockers**

[![Python](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/status-complete-success.svg)]()

---

##  Table of Contents

- [Project Overview](#-project-overview)
- [Key Findings](#-key-findings)
- [Project Structure](#-project-structure)
- [Installation & Setup](#-installation--setup)
- [Usage](#-usage)
- [Methodology](#-methodology)
- [Results & Visualizations](#-results--visualizations)
- [Recommendations](#-recommendations)
- [Technologies Used](#-technologies-used)
- [Contributing](#-contributing)
- [License](#-license)

---

##  Project Overview

This project analyzes **372 student check-in responses** from the Umuzi XB1 cohort using Natural Language Processing (NLP) to transform unstructured text into actionable insights for program management.

### Objectives

1. **Identify top trends** in student wins, losses, and blockers
2. **Quantify sentiment** across different response categories
3. **Provide actionable recommendations** for program improvement
4. **Create visualizations** for stakeholder presentations

### Dataset

- **Source:** Google Forms check-in responses
- **Period:** July - November 2025
- **Size:** 372 student responses
- **Categories:** Wins (96.8% response), Losses (81.5%), Blockers (74.5%)

---

##  Key Findings

### Top Themes Identified

#### **Wins (What Students Celebrate)**
1. **ENJOY** (97 mentions, 3.3%) - High engagement
2. **LEARN** (62 mentions, 2.1%) - Active learning
3. **COMPLETE** (52 mentions, 1.8%) - Task success
4. **MANAGE** (46 mentions, 1.6%) - Organization skills
5. **COURSE** (45 mentions, 1.5%) - Content resonance

####  **Losses (Student Challenges)**
1. **TIME** (64 mentions, 2.9%) - Time management
2. **WORK** (46 mentions, 2.1%) - Workload pressure
3. **CHALLENGE** (39 mentions, 1.8%) - General difficulty
4. **GET** (33 mentions, 1.5%) - Execution struggles
5. **PLAN** (25 mentions, 1.1%) - Planning issues

####  **Blockers (What Stops Students)**
1. **TIME** (53 mentions, 3.3%) - Insufficient time
2. **WORK** (36 mentions, 2.2%) - Work/study conflicts
3. **ISSUE** (21 mentions, 1.3%) - Technical problems
4. **DATUM** (20 mentions, 1.2%) - Data/internet access
5. **NETWORK** (18 mentions, 1.1%) - Connectivity issues

### Sentiment Analysis Results

| Category | Average Sentiment | Interpretation |
|----------|-------------------|----------------|
| **Wins** | +0.214 |  Positive |
| **Losses** | +0.035 |  Neutral |
| **Blockers** | -0.006 |  Slightly Negative |

**Key Insight:** Students maintain positive/neutral sentiment even when discussing challenges, demonstrating resilience.

---

##  Project Structure
```
umuzi-nlp-checkin-analysis/
│
├── data/
│   ├── raw/
│   │   └── Umuzi XB1 Check in (Responses) - Form Responses 1.xlsx
│   └── processed/
│       ├── cleaned_checkin_data.csv
│       └── checkin_data_with_sentiment.csv
│
├── notebooks/
│   ├── 01_exploration_preprocessing.ipynb     # Data cleaning & preprocessing
│   └── 02_topic_modeling_sentiment.ipynb      # Analysis & visualizations
│
├── reports/
│   ├── final_summary.md                       # Complete analysis report
│   ├── final_summary.pdf                      # PDF version
│   ├── top_win_themes.csv                     # Exported themes
│   ├── top_loss_themes.csv
│   ├── top_blocker_themes.csv
│   └── charts/
│       ├── sentiment_distribution.png
│       ├── wordcloud_wins.png
│       ├── wordcloud_losses.png
│       └── wordcloud_blockers.png
│
├── requirements.txt                           # Python dependencies
├── README.md                                  # This file
├── .gitignore
└── LICENSE
```

---

##  Installation & Setup

### Prerequisites

- Python 3.10 or higher
- pip package manager
- Jupyter Notebook or JupyterLab

### Step 1: Clone the Repository
```bash
git clone https://github.com/Tiego3/umuzi-nlp-checkin-analysis.git
cd umuzi-nlp-checkin-analysis
```

### Step 2: Create Virtual Environment

**Windows:**
```bash
python -m venv .venv
.venv\Scripts\activate
```

**Mac/Linux:**
```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Step 4: Download NLP Models
```bash
# Download spaCy model
python -m spacy download en_core_web_sm

# Download NLTK data
python -c "import nltk; nltk.download('punkt_tab'); nltk.download('stopwords'); nltk.download('wordnet'); nltk.download('omw-1.4'); nltk.download('brown')"
```

### Step 5: Launch Jupyter
```bash
jupyter lab
```

---

##  Usage

### Running the Analysis

Execute notebooks in order:

#### 1. **Data Preprocessing** (`01_exploration_preprocessing.ipynb`)
```python
# This notebook performs:
# - Data loading and inspection
# - Text cleaning (tokenization, lemmatization)
# - Stopword removal
# - Token frequency analysis
# - Initial visualizations
```

**Output:** `data/processed/cleaned_checkin_data.csv`

#### 2. **Sentiment & Visualization** (`02_topic_modeling_sentiment.ipynb`)
```python
# This notebook performs:
# - Sentiment analysis with TextBlob
# - Word cloud generation
# - Topic frequency tables
# - Executive summary generation
```

**Outputs:** 
- Sentiment scores added to dataset
- Visualizations saved to `reports/charts/`
- Theme tables exported as CSV

### Quick Start
```python
# Load preprocessed data
import pandas as pd
df = pd.read_csv('data/processed/checkin_data_with_sentiment.csv')

# View top themes
win_themes = pd.read_csv('reports/top_win_themes.csv')
print(win_themes)
```

---

## 🔬 Methodology

### NLP Pipeline

1. **Data Cleaning**
   - Remove special characters, URLs, emails
   - Convert to lowercase
   - Handle missing values

2. **Tokenization**
   - Split text into words
   - Remove common stopwords
   - Apply domain-specific filtering

3. **Lemmatization**
   - Reduce words to root form using spaCy
   - Preserve semantic meaning

4. **Sentiment Analysis**
   - TextBlob polarity scoring
   - Scale: -1 (negative) to +1 (positive)

5. **Theme Extraction**
   - Token frequency analysis
   - Top N theme identification
   - Percentage calculation

### Tools & Libraries

- **pandas** - Data manipulation
- **nltk** - Natural language processing
- **spacy** - Advanced NLP (lemmatization)
- **textblob** - Sentiment analysis
- **matplotlib** - Visualizations
- **wordcloud** - Word cloud generation

---

## Results & Visualizations

### Sentiment Distribution

![Sentiment Distribution](reports/charts/sentiment_distribution.png)

*Three-panel visualization showing sentiment score distributions for Wins, Losses, and Blockers*

### Word Clouds

<table>
<tr>
<td><img src="reports/charts/wordcloud_wins.png" alt="Wins" width="300"/></td>
<td><img src="reports/charts/wordcloud_losses.png" alt="Losses" width="300"/></td>
<td><img src="reports/charts/wordcloud_blockers.png" alt="Blockers" width="300"/></td>
</tr>
<tr>
<td align="center"><b>Win Themes</b></td>
<td align="center"><b>Loss Themes</b></td>
<td align="center"><b>Blocker Themes</b></td>
</tr>
</table>

### Detailed Reports

 **[Full Analysis Report](reports/final_summary.md)** - Complete findings with methodology and recommendations

 **[PDF Version](reports/final_summary.pdf)** - Printable executive summary

---

## Recommendations

Based on analysis of 372 student responses, we recommend:

### 1. **Infrastructure Support** 
**Issue:** 60+ students (16%) affected by network, data, electricity issues  
**Action:** Provide data stipends, backup power solutions, network troubleshooting guides

### 2. **Time Management Training** 
**Issue:** 117 mentions of time-related challenges (64 losses + 53 blockers)  
**Action:** Offer productivity workshops, scheduling tools, time blocking techniques

### 3. **Mental Health & Wellness** 
**Issue:** Multiple reports of fatigue, burnout, illness  
**Action:** Implement wellness check-ins, flexible deadlines, mental health resources

### 4. **Platform Access Resolution** 
**Issue:** 10+ students unable to access Financial Foundations course  
**Action:** Immediate tech support,

### 5. **Celebrate Learning Wins** 
**Strength:** High engagement with DataCamp, Coursera, Customer Centricity  
**Action:** Public recognition, peer learning sessions, success story sharing

---

## 🛠️ Technologies Used

| Category | Tools |
|----------|-------|
| **Language** | Python 3.10+ |
| **Data Processing** | pandas, numpy |
| **NLP** | nltk, spacy, textblob |
| **Visualization** | matplotlib, wordcloud |
| **Development** | Jupyter Lab, VS Code |
| **Version Control** | Git, GitHub |

### Dependencies

See [`requirements.txt`](requirements.txt) for complete list:
```
pandas==2.0.3
numpy==1.24.3
matplotlib==3.7.2
scikit-learn==1.3.0
nltk==3.8.1
spacy==3.6.0
textblob==0.17.1
wordcloud==1.9.2
openpyxl==3.1.2
```

---

**Program:** Umuzi Data Science  
**Date:** November 2025

##  Project Status

**Status:**  **COMPLETE**

- [x] Data collection and cleaning
- [x] NLP preprocessing pipeline
- [x] Sentiment analysis
- [x] Theme identification
- [] Visualizations
- [x] Final report
- [x] Documentation

**Last Updated:** November 2025
