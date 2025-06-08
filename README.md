# 🩺 PatientSignal: Diagnosing Diseases Through Noisy Patient Descriptions
**Understanding how real-world conversations affect automated medical diagnosis**

## 📋 **Table of Contents**
- [🎯 Overview](#overview)
- [🖼️ Graphical Abstract](#graphical-abstract)
- [🎪 Problem Statement](#problem-statement)
- [🏆 Key Contributions](#key-contributions)
- [📦 Project Structure](#project-structure)
- [🚀 Quick Start](#quick-start)
- [🏥 Dataset](#dataset)
- [🔧 Data Preparation](#data-preparation)
- [🧠 Models & Methodology](#models--methodology)
- [📈 Results](#results)
- [💡 Insights](#insights)
- [🔬 References](#references)
- [🙏 Acknowledgments](#acknowledgments)
- [👥 Team](#team)

## overview  
When patients talk to doctors, they often describe symptoms with lots of extra information-personal stories, pauses, and even unrelated topics.
PatientSignal investigates how this natural way of speaking affects automated medical diagnosis systems. Using state-of-the-art AI (Llama3.1:8b), we generated realistic patient stories with varying levels of conversational noise, then tested different AI models to see how accurately they could diagnose illnesses from these noisy descriptions.

## Graphical Abstract
![שקופית1 PNG](https://github.com/user-attachments/assets/d5e10271-3547-4dd3-a51d-669665b63dd7)

## Problem Statement
- **Input**: Patient descriptions (clean/noisy).
- **Output**: Disease classification (24 categories).
- **Challenge**: Maintaining diagnostic accuracy despite conversational distractions.

## Key Contributions
- **Novel Noise Simulation**: Realistic symptom descriptions using Llama3.1.
- **Robustness Testing**: Performance benchmarking across noise levels.
- **Model Evaluation**: Comprehensive analysis across multiple state-of-the-art models.

## Project Structure
```bash
PatientSignal/
├── 📂 data/
│   ├── 📄 Train_data.csv
│   └── 📄 Train_data_with_noise2.csv
├── 📂 notebooks/
│   ├── 📓 Noise_Generation.ipynb
│   └── 📓 PatientSignal.ipynb
└── 📖 README.md
```

## Quick Start
### Clone the repository
```bash
git clone https://github.com/lielsheri/PatientSignal.git
cd PatientSignal
```
### Install dependencies
pip install -r requirements.txt
### Run the notebooks
* jupyter notebook notebooks/Noise_Generation.ipynb
* jupyter notebook notebooks/PatientSignal.ipynb

## Dataset
- **Source**: [Kaggle Symptom-Based Disease Labeling Dataset](https://www.kaggle.com/datasets/krish0202/symptom-based-disease-labeling-dataset)
- **Original size**: 1,200 clean symptom descriptions across 24 disease categories.
- **The original dataset includes**: Concise, clinical-like descriptions written in plain text and A balanced distribution of disease labels.

## 🔧 Data Preparation
We started with 1,200 **clean** symptom descriptions from a Kaggle dataset, each labeled with one of 24 diseases.
To simulate real-world conversations, we generated two additional versions of each description using the Llama3.1:8b model via Ollama:
- **Medium Noise** (80–220 words): Added friendly chatter, repetitions, and slight distractions.
- **Heavy Noise** (150–390 words): Included longer personal anecdotes, hesitations, and more off-topic tangents.

The result is a final dataset of 3,600 examples:
- 1,200 clean
- 1,200 with medium noise
- 1,200 with heavy noise









## 👥 **Team**
- **Liel Sheri**
- **Eden Mama**

  





