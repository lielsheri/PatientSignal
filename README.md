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
-jupyter notebook notebooks/Noise_Generation.ipynb
-jupyter notebook notebooks/PatientSignal.ipynb












## 👥 **Team**
- **Liel Sheri**
- **Eden Mama**

  





