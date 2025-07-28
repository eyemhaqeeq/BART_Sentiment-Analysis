# BART Sentiment Analysis - Binary Classification

## Project Overview
This project implements a BART-based sentiment analysis model for binary classification of product reviews into positive or negative categories. The model was trained on Amazon product reviews, specifically excluding neutral 3-star reviews to focus on clear positive/negative sentiment distinction.

## Key Features
- **Model Architecture**: `facebook/bart-base` fine-tuned for binary classification
- **Dataset**: Amazon product reviews (`Reviews.csv`)
- **Data Processing**:
  - Removed neutral 3-star reviews
  - Converted to binary labels: 1-2 stars = Negative (0), 4-5 stars = Positive (1)
- **Train-Test Split**: 80% training, 20% validation
- **Training**:
  - Batch size: 16
  - Epochs: 2
  - Max sequence length: 128 tokens

## Performance Results
| Metric          | Score               |
|-----------------|--------------------|
| Accuracy        | 95.73%             |
| Precision       | 97.29%             |
| Recall          | 97.67%             |
| F1 Score        | 97.48%             |
| Training Time   | 679.56 seconds     |
| Testing Time    | 24.75 seconds      |


## Model Summary

Model: BART (facebook/bart-base)
Task: Binary Sentiment Classification (Positive vs Negative)
Dataset: Amazon Product Reviews
Sample Size Used: 5000 reviews
Max Sequence Length: 128 tokens
Training Epochs: 2
Batch Size: 16 (train), 64 (eval)
Tokenizer: BartTokenizer from Hugging Face

## Libraries Used

transformers
scikit-learn
pandas
torch

## Workflow

1. Load the Amazon product reviews dataset
2. Remove neutral reviews (Score == 3)
3. Map scores to binary labels: 0 for negative (1-2 stars), 1 for positive (4-5 stars)
4. Tokenize using BART tokenizer with max_length = 128
5. Create a PyTorch Dataset compatible with Hugging Face Trainer
6. Fine-tune BartForSequenceClassification
7. Evaluate using scikit-learn metrics

## File Structure

- BART_Sentiment_Analysis.ipynb: Jupyter notebook with training and evaluation steps
- Reviews.csv: Dataset file
- README.md: Project documentation and summary

## Future Work

- Compare BART with BERT and RoBERTa
- Add multi-class classification including neutral reviews
- Deploy as a web service using FastAPI

## License

MIT License

Copyright (c) [2025] [Haqeeq Ahmed]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

