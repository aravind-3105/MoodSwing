# MoodSwing - Lyrics Classification

### Overview
The goal of this project is to classify song lyrics into emotional categories: **Happy**, **Sad**, **Angry**, and **Relaxed**. This classification aims to enhance music recommendation systems by aligning songs with the listener's mood, potentially offering insights into mental health. With advancements in NLP, this project explores the use of AI to create mood-based recommendations that analyze lyrical content.

### Data
We utilized the **MoodyLyricQ dataset**, containing 2000 songs evenly distributed across four mood categories. Since the dataset lacked lyrics due to copyright constraints, we used the **Genius API** to retrieve song lyrics based on title and artist name.

### Architecture

#### GPT-2 Architecture
- Structured a dataset with song IDs, preprocessed lyrics, and mood labels.
- Split the data into 80% training and 20% validation sets.
- Fine-tuned **GPT-2** for sequence classification using Cross Entropy Loss, Adam optimizer, and a StepLR scheduler.
- Employed gradient accumulation, mixed precision, and a batch size of 4 across 20 epochs.

<p align="center">
  <img src="https://github.com/ece1786-2023/MoodSwing/assets/114831340/4a4b8842-3bca-4923-8168-2509e8e90032" />
</p>

#### GPT-3.5 Architecture
- Preprocessed the data to include system prompts, mood labels, and lyrical text.
- Generated training, validation, and test sets in JSONL format.
- Fine-tuned **GPT-3.5** on OpenAI with default hyperparameters and evaluated its performance using the test dataset.

<p align="center">
  <img src="https://github.com/ece1786-2023/MoodSwing/assets/114831340/1a88b6ed-5ae9-49b4-8310-8fed1da44de2" />
</p>

### Interesting Findings
- **BERT outperformed GPT-2**: BERT’s bidirectional context capture helped in better mood classification by understanding nuanced sentiments in lyrics.
- **Minimal Pre-processing**: Preserving the raw text improved performance, as stemming/lemmatization removed important emotional nuances.
- **Misclassification of "Relaxed"**: The model often confused "Relaxed" with "Happy," likely due to the subtle differences in valence and arousal between the two emotions.

<p align="center">
  <img src="https://github.com/ece1786-2023/MoodSwing/assets/114831340/aee26e92-4ef7-41f3-9bcf-059f6354ce3c" />
</p>
