# PatientSignal: LLM‑Augmented Medical Text Classifier

**Diagnosing Through the Noise: Understanding Patient Self‑Descriptions**

## Project Overview  
In everyday conversation, patients often describe their symptoms with personal anecdotes, pauses and even unrelated details. PatientSignal shows how this “real-world noise” influences automated medical text classifiers. Starting with 1,200 clean symptom descriptions, we use a T5-based language model to weave in two levels of natural speech patterns—brief chatter and longer anecdotes—then measure how well different algorithms cope.

## How It Works  
1. **Prepare the Data**  
   We load and clean `Train_data.csv` from "https://www.kaggle.com/datasets/krish0202/symptom-based-disease-labeling-dataset?resource=download", removing duplicates and filling any gaps to ensure a solid baseline.  

2. **Add Human-Like Noise**  
   A carefully crafted prompt guides `google/flan-t5-base` to generate:  
   - **Medium noise** (50–80 words of friendly small talk)  
   - **Heavy noise** (100–150 words of richer, more detailed storytelling)  

3. **Compare Classifiers**  
   We train Naïve Bayes, SVM and a simple neural network on both clean and noisy versions of the data. By comparing accuracy, we reveal which methods are most resilient to real‑world patient language.

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

