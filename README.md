# 🩺 PatientSignal: Diagnosing Diseases Through Noisy Patient Descriptions
**Understanding how real-world conversations affect automated medical diagnosis**

## 📋 **Table of Contents**
- [🎯 Overview](#overview)
- [🖼️ Graphical Abstract](#graphical-abstract)
- [🎪 Problem Statement](#problem-statement)
- [🏆 Key Contributions](#key-contributions)
- [👥 Team](#team)
- [📦 Project Structure](#project-structure)
- [🚀 Quick Start](#quick-start)
- [🏥 Dataset](#dataset)
- [🔧 Data Preparation](#data-preparation)
- [🧠 Models & Methodology](#models--methodology)
- [📈 Results](#results)
- [💡 Insights](#insights)
- [🔬 References](#references)
- [🙏 Acknowledgments](#acknowledgments)

## overview  
When patients talk to doctors, they often describe symptoms with lots of extra information—personal stories, pauses, and even unrelated topics.
PatientSignal investigates how this natural way of speaking affects automated medical diagnosis systems. Using state-of-the-art AI (Llama3.1:8b), we generated realistic patient stories with varying levels of conversational noise, then tested different AI models to see how accurately they could diagnose illnesses from these noisy descriptions.

## Graphical Abstract
![שקופית1 PNG](https://github.com/user-attachments/assets/d5e10271-3547-4dd3-a51d-669665b63dd7)

## How It Works  
1. **Prepare the Data**  
   We load and clean `Train_data.csv` from "https://www.kaggle.com/datasets/krish0202/symptom-based-disease-labeling-dataset?resource=download", removing duplicates and filling any gaps to ensure a solid baseline.  

2. **Add Human-Like Noise**  
   A carefully crafted prompt guides `llama3.1:8b` to generate:  
   - **Medium noise** (80-220 words of friendly small talk)  
   - **Heavy noise** (150-390 words of richer, more detailed storytelling)  

3. **Compare Classifiers**  
   We train Naïve Bayes and BERT, on both clean and noisy versions of the data. By comparing accuracy, we reveal which methods are most resilient to real‑world patient language.

## Dataset at a Glance  

| Field                     | What It Means                                                |
|---------------------------|--------------------------------------------------------------|
| `id`                      | A unique identifier for each example                         |
| `label`                   | The correct diagnosis (e.g., Psoriasis, Eczema)              |
| `text`                    | The original, clean symptom description                      |
| `text_medium_noise`       | Version with short, conversational noise                     |
| `text_heavy_noise`        | Version with longer, anecdotal noise                         |

## Authors  
**Liel Sheri** & **Eden Mama**

