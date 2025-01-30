# Text Summarization Models - TOPSIS Evaluation

## Overview
This project implements **TOPSIS (Technique for Order of Preference by Similarity to Ideal Solution)** to evaluate different **pretrained text summarization models**. The models are assessed based on standard evaluation metrics like ROUGE, BLEU, and BERTScore.

## Dataset
- **Test Dataset (`test.csv`)**: Contains articles and their corresponding summaries (highlights).
- **Evaluation Results (`results.csv`)**: Includes the scores of various models across different evaluation metrics.

## Models Evaluated
The following pretrained models were tested:
- **facebook/bart-large-cnn**
- **Falconsai/text_summarization**
- **google/pegasus-cnn_dailymail**
- **csebuetnlp/mT5_multilingual_XLSum**

## Metrics Used
1. **ROUGE (Recall-Oriented Understudy for Gisting Evaluation)**:
   - ROUGE-1, ROUGE-2, ROUGE-L measure similarity between generated and reference summaries.
2. **BLEU (Bilingual Evaluation Understudy)**:
   - Evaluates the precision of generated summaries compared to references.
3. **BERTScore**:
   - Uses contextual embeddings to measure similarity.
4. **TOPSIS Score**:
   - A multi-criteria decision-making method used to rank models based on the above metrics.

## Results
The models were ranked based on the **TOPSIS method**, and the best-performing model was **facebook/bart-large-cnn**.

| Model | ROUGE-1 | ROUGE-2 | ROUGE-L | BLEU | BERTScore | TOPSIS Score | Rank |
|--------|---------|---------|---------|------|------------|--------------|------|
| facebook/bart-large-cnn | 0.296 | 0.113 | 0.296 | 10.17 | 0.867 | 1.000 | 1 |
| google/pegasus-cnn_dailymail | 0.265 | 0.044 | 0.265 | 1.79 | 0.846 | 0.570 | 2 |
| Falconsai/text_summarization | 0.172 | 0.053 | 0.172 | 2.56 | 0.854 | 0.387 | 3 |
| csebuetnlp/mT5_multilingual_XLSum | 0.111 | 0.000 | 0.074 | 1.21 | 0.848 | 0.011 | 4 |

## Visualization
### Model Performance
```python
import matplotlib.pyplot as plt
import pandas as pd

# Load results.csv
df = pd.read_csv("results.csv")

# Plot TOPSIS Scores
plt.figure(figsize=(8, 5))
plt.bar(df['Unnamed: 0'], df['TOPSIS Score'], color=['blue', 'green', 'red', 'purple'])
plt.xlabel("Models")
plt.ylabel("TOPSIS Score")
plt.title("TOPSIS Ranking of Text Summarization Models")
plt.xticks(rotation=45)
plt.show()
```

## How to Use
1. Clone the repository:
   ```sh
   git clone https://github.com/khwaishagarwal/Text-Summarisation-Topsis.git
   ```
   
## Conclusion
- **facebook/bart-large-cnn** outperformed other models based on multiple evaluation metrics.
- TOPSIS provides a systematic way to rank models based on multi-criteria evaluation.
