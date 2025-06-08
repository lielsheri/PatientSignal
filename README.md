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

## Data Preparation
To better simulate real-life patient-doctor interactions, we created two additional noisy versions for each of the 1,200 original samples using Llama3.1:8b via Ollama.
* 🟠Medium Noise (80–220 words): Includes natural-sounding distractions like repetitions, off-topic comments, or emotional reactions.
* 🔴 Heavy Noise (150–390 words): Contains longer personal stories, hesitations, unrelated memories, and more chaotic flow of thought.

We ensured: No missing values, No duplicates, Label balance across all sets

Final dataset breakdown:

| Type           | Count |
|----------------|-------|
| 🟢 Clean          | 1,200 |
| 🟠 Medium Noise   | 1,200 |
| 🔴 Heavy Noise    | 1,200 |
| **Total**      | **3,600** |

## Models & Methodology

We tested four different models to evaluate how well they classify diseases from symptom descriptions — both clean and noisy:

| Model           | Description                                 | Optimizer     | Special Notes                      |
|------------------|---------------------------------------------|----------------|-------------------------------------|
| 🧪 Naïve Bayes    | Classic baseline using TF-IDF features      | —              | Very lightweight and interpretable |
| 🧠 BERT           | Pretrained transformer model (base)         | AdamP          | Fine-tuned, frozen layers 0–3      |
| 🧬 ClinicalBERT   | BERT variant trained on clinical text       | AdamP + Scheduler | First 165 params frozen          |
| 🔁 FLAN-T5        | Instruction-tuned text-to-label model       | Adafactor       | Text-to-label format + tokenizer  |

Each model was trained separately on:
- 🟢 Clean data
- 🟠 Medium-noise data
- 🔴 Heavy-noise data

We used an 80/20 train-test split across all experiments.

---

## Results

The table below shows how each model performed on clean vs. noisy data. As expected, accuracy generally drops as noise increases. However, some models (like FLAN-T5 and ClinicalBERT) show better robustness to heavy conversational distraction.

| Model          | 🟢 Clean Accuracy | 🟠 Medium Noise | 🔴 Heavy Noise |
|----------------|-------------------|------------------|-----------------|
| Naïve Bayes    | 93.8%              | 79.2%            | 77.5%           |
| BERT           | 98.3%              | 86.7%            | 79.2%           |
| ClinicalBERT   | 97.9%              | 83.8%            | 86.2%           |
| **FLAN-T5**    | 97.1%              | **92.5%**        | **87.1%**       |

### Insights 
- **Conversational noise affects model accuracy**: As expected, all models showed a decline in performance when exposed to noisier, more human-like symptom descriptions.
- **Naïve Bayes struggled the most**: As a simple, keyword-based model, it experienced the sharpest accuracy drop under noise and lacks the contextual understanding needed to handle distractions.
- **BERT led on clean data**, but its accuracy dropped more sharply under heavy noise compared to ClinicalBERT and FLAN-T5.
- **ClinicalBERT showed an interesting pattern**: After dropping on medium-noise data, it improved on heavy-noise inputs. This might be due to repeated clinical terms in longer texts, which help its clinical training kick in.
- **FLAN-T5 was the most robust overall**, outperforming all models on both medium and heavy noise. Its instruction-tuned nature likely helped it adapt to varied sentence structures and linguistic distractions.

These results highlight the importance of **choosing the right model** for real-world applications where patient descriptions are often messy, anecdotal, or unclear.

## References

Our project was inspired and supported by recent works focused on clinical NLP, robustness to noise, and symptom-based disease prediction. Below are the main resources we relied on:

**1. Optimizing Classification of Diseases Through Language Model Analysis of Symptoms** *(2024)*  
Applied Medical Concept Normalization to BERT and used multiple optimizers (AdamP, AdamW) and BiLSTM with Hyperopt on the Symptom2Disease dataset.  
🔗 [Read on Nature](https://www.nature.com/articles/s41598-024-51615-5.pdf)

**2. DiagnoAI – Disease Prediction from Symptom Descriptions** *(2022)*  
Manually generated 50 synthetic patient symptom descriptions per disease based on the Kaggle dataset. Fine-tuned all BERT layers using TensorFlow.  
🔗 [GitHub Repository](https://github.com/FaizalKarim280280/DiagnoAI)

**3. Deep Learning Models Are Not Robust Against Noise in Clinical Text** *(2021)*  
Introduced controlled character- and word-level noise to evaluate transformers like ClinicalBERT, XLNet, and ELMo on tasks such as NER, Relation Extraction, and Semantic Similarity.  
🔗 [Read on arXiv](https://arxiv.org/pdf/2108.12242)

**4. Symptom-Based Disease Labeling Dataset**  
Our primary dataset: 1,200 clean symptom descriptions labeled across 24 diseases.  
🔗 [Kaggle Dataset](https://www.kaggle.com/datasets/krish0202/symptom-based-disease-labeling-dataset)










## 👥 **Team**
- **Liel Sheri**
- **Eden Mama**

  





