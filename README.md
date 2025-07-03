# Sentimental Text Analyser

This is a GUI-based application for analyzing and transforming the emotional tone of text using machine learning and GPT-4. It includes multiple NLP tasks such as emotion classification, rephrasing text into different emotional tones, sentiment analysis, topic modeling, and LIME-based reasoning.

---

## How to Set Up

### 1. Run `Main.py` to prepare your model:

Before launching the GUI, run the `Main.py` file to:
- Preprocess the dataset (`step2_preprocessing.py`)
- Train and evaluate emotion classification models (`step3_classification.py`)
- Optionally run EDA (`step1_eda.py`) or topic modeling (`step4_topic_modeling.py`)

This process generates:
- TF-IDF vectorizer (`outputs/step2/tfidf_vectorizer.pkl`)
- Trained classifier (`outputs/step3/ExtraTrees_model.pkl`)
- Label encoder (`outputs/step3/label_encoder.pkl`)

> ⚠ These `.pkl` files are already included in the repo, so running `Main.py` is optional unless you want to retrain using your own dataset.

---

## ▶Running the Application

After the model files are generated (or already available), launch the main GUI:
```bash
python user_gui.py
```

The GUI provides multiple functionalities split into tabs:

---

##  Features

### 1. **Classify + Rephrase**
- Automatically detects the emotion of your input sentence.
- Allows the user to input a target emotion to rephrase the sentence.
- Uses GPT-4 to rewrite the sentence with the new emotional tone.

### 2. **Emotion Classification**
- Detects the dominant emotion of the input sentence using a trained ML model (Extra Trees).

### 3. **Classification + Reasoning**
- Visualizes model reasoning with LIME.
- Shows class probabilities and top influential words.
- Includes scrollable interface to handle large visualizations and explanations.

### 4. **Sentiment Analysis**
- Uses rule-based NLP (e.g., TextBlob or similar) to provide:
  - Sentiment (Positive / Negative / Neutral)
  - Polarity score
  - Subjectivity score

---

## GPT Integration

All OpenAI GPT-related operations (e.g., rephrasing) are handled inside `step7_style_transfer.py`, which holds the API key and prompt logic securely in one place.

If you're using this system:
- Set your OpenAI key inside `step7_style_transfer.py` if it's not already set.
- Make sure you have internet access and OpenAI access enabled.

---

## File Structure Overview

```
├── Main.py                    # Orchestrates all steps: preprocessing, training, etc.
├── user_gui.py                # Runs the GUI application
├── step1_eda.py               # Exploratory Data Analysis
├── step2_preprocessing.py     # Text preprocessing and TF-IDF generation
├── step3_classification.py    # Model training, evaluation, and saving
├── step4_topic_modeling.py    # Optional topic modeling module
├── step5_sentiment_analysis.py# Rule-based sentiment analysis
├── step6_reasoning.py         # LIME explanation logic
├── step7_style_transfer.py    # GPT logic for rephrasing and emotion manipulation
├── outputs/
│   ├── step2/
│   │   └── tfidf_vectorizer.pkl
│   ├── step3/
│   │   ├── ExtraTrees_model.pkl
│   │   └── label_encoder.pkl
│   └── step6/
│       └── lime_explanation.png
```

---

##  Customization Tips

- Replace or expand your dataset in `Main.py` to retrain the model.
- Modify the prompt template in `step7_style_transfer.py` to change GPT behavior.
- Adjust model parameters in `step3_classification.py` for fine-tuning.


