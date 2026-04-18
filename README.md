# Emotion Detection in Text using Fine-Tuned BERT

## Overview
This project implements an emotion classification system using a fine-tuned BERT model. The model takes a sentence as input and predicts one of six emotions: sadness, love, joy, surprise, anger, and fear.

The project demonstrates the use of transformer-based models for natural language processing tasks, including preprocessing, model fine-tuning, evaluation, and analysis.

---

## Problem Statement
Emotion detection is more detailed than sentiment analysis. Instead of classifying text as positive or negative, it identifies the specific emotion expressed. This is important in applications such as social media monitoring, customer feedback analysis, and conversational AI.

---

## Dataset
The dataset used is GoEmotions, released by Google Research.

- Original format: multi-label
- Converted to: single-label classification
- Selected emotions:
  - sadness
  - love
  - joy
  - surprise
  - anger
  - fear

Final dataset size: approximately 28,000 samples.

---

## Preprocessing
- Filtered dataset to include only 6 emotions
- Converted multi-label data to single-label using `idxmax`
- Kept only `text` and `label` columns
- Mapped labels to numeric values
- Tokenized text using BERT tokenizer
- Maximum sequence length: 128

---

## Model
- Model: bert-base-uncased
- Architecture: BERT with classification head
- Task: multi-class classification (6 classes)

---

## Training
- Epochs: 3
- Batch size: 8
- Optimizer: AdamW
- Training time: approximately 30 minutes

---

## Results
- Accuracy: 77.08%
- Weighted F1-score: 76.98%

### Per-class highlights:
- Love: best performing class
- Anger: strong performance
- Fear: most difficult class

---

## Error Analysis
The model confuses similar emotions such as:
- joy and love
- sadness and anger
- fear and surprise

---

## Limitations
- Multi-label data simplified to single-label
- No neutral class
- Difficulty with sarcasm and short text
- Class imbalance
- No comparison with other models

---

## Project Structure
emotion-detection-bert/
│
├── DL_project.ipynb
├── README.md
└── requirements.txt (optional)

---

## Conclusion
This project shows that fine-tuned BERT models can effectively classify emotions in text, while also highlighting challenges such as ambiguity and overlapping emotional expressions.


-----------------------------------------------------------------

## How to Reproduce the Results

To reproduce the results of this project, follow the steps below.

1. Clone the Repository
Open a terminal and run the following commands:
git clone https://github.com/YOUR_USERNAME/emotion-detection-bert.git
cd emotion-detection-bert
This will download all project files to your local machine.

2. Install Dependencies
Install the required Python libraries using pip:
  pip install transformers datasets torch scikit-learn pandas jupyter
These libraries are required for preprocessing, training, and evaluation.

3. Prepare the Dataset
You have two options:
Option 1: Use the dataset already included in the notebook
  •	The notebook contains preprocessing steps, so no manual preparation is required
Option 2: Use the original GoEmotions dataset
  •	Download the dataset
  •	Filter it to include only the six emotions
  •	Convert multi-label data to single-label using idxmax
  •	Ensure the dataset contains:
    o	a "text" column
    o	a "label" column

4. Run the Notebook
Launch Jupyter Notebook:
jupyter notebook
Open the file:
DL_project.ipynb
Run all cells sequentially.
The notebook includes:
  •	data preprocessing
  •	tokenization
  •	model training
  •	evaluation
  •	demo examples

5. Train the Model
Execute the training cells in the notebook.
  •	The model will train for 3 epochs
  •	Training loss and progress will be displayed
  •	Total training time is approximately 30 minutes

6. Evaluate the Model
After training, the notebook will automatically compute:
  •	accuracy
  •	weighted F1-score
  •	classification report
These metrics should be close to the reported results (~77%).

7. Run Inference Examples
Use the helper function provided in the notebook:
  run_example(text, case_type, expected, explanation)
Example:
  run_example(
  text="I love you so much",
  case_type="Easy case",
  expected="love",
  explanation="Strong positive emotional expression"
  )
You can test:
  •	simple cases
  •	ambiguous cases
  •	edge cases
  •	failure cases

8. Verify Results
To confirm correct reproduction:
  •	accuracy should be around 77%
  •	model should correctly classify clear emotional sentences
  •	model should show limitations on ambiguous or neutral inputs

Notes
  •	Results may vary slightly due to randomness in training
  •	GPU usage (like on Google Colab) is recommended for faster training
  •	The notebook already includes all necessary steps for end-to-end execution


