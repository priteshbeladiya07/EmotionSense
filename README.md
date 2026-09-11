# EmotionSense — Deep Learning NLP Emotion Classification

EmotionSense is a Deep Learning based Natural Language Processing (NLP) project that predicts the emotion expressed in a given sentence.

The project compares four recurrent neural network architectures — **RNN**, **LSTM**, **GRU**, and **Bidirectional GRU (BiGRU)** — to determine which model performs best for text emotion classification.

The final **BiGRU** model achieved **91.55% test accuracy**, significantly outperforming the other recurrent models tested.

---

## 🚀 Project Overview

The main goal of this project is to build an emotion classification system that can understand the emotional meaning of text.

The model classifies sentences into the following emotions:

| Emotion | Emoji |
|---|---|
| Happy | 😄 |
| Sad | 😢 |
| Fear | 😨 |
| Surprise | 😮 |
| Angry | 😡 |
| Love | ❤️ |
| Joy | 😊 |

**Project workflow:**

Dataset → Text Preprocessing → Tokenization → Padding → Model Training → Model Comparison → BiGRU Selection → Model Saving → FastAPI Deployment

---

## 📊 Dataset

The project uses an emotion dataset obtained from **Hugging Face**. It contains text sentences along with their corresponding emotion labels. The data is converted into numerical sequences using a tokenizer before being fed into the neural networks.

**Preprocessing steps:**

1. Load the dataset from Hugging Face
2. Separate text and emotion labels
3. Tokenize the text
4. Convert words into integer sequences
5. Pad sequences to a fixed length
6. Prepare the data for Deep Learning models
7. Split data into training and testing sets

---

## 🧠 Models Compared

Four recurrent neural network architectures were trained and evaluated.

### 1. RNN
A basic Recurrent Neural Network used as the initial baseline. It struggled to capture enough information from the text sequences.

### 2. LSTM
Long Short-Term Memory (LSTM) was tested for its ability to handle long-term dependencies in sequential data. It performed better than the basic RNN, but accuracy remained relatively low.

### 3. GRU
Gated Recurrent Unit (GRU) was tested as a simpler alternative to LSTM. It achieved the same test accuracy as LSTM in this experiment.

### 4. Bidirectional GRU (BiGRU)
Unlike a standard recurrent network that processes a sequence mainly in one direction, a Bidirectional GRU uses information from **both directions** of the sequence — making it far more effective at understanding sentence context.

---

## 📈 Model Performance Comparison

| Model | Test Loss | Test Accuracy |
|-------|-----------|----------------|
| RNN | 1.759104 | 13.75% |
| LSTM | 1.777020 | 34.75% |
| GRU | 1.760654 | 34.75% |
| **BiGRU** | **0.23443** | **91.55%** ✅ |

**Key takeaway:** BiGRU had the lowest loss and the highest accuracy by a wide margin — nearly 57 percentage points above LSTM/GRU and over 77 points above the baseline RNN.

---

## 🏆 Best Model

**Bidirectional GRU (BiGRU)** was selected as the final model, achieving **91.55% test accuracy** — a major improvement over every other architecture tested.

### 🔍 Why BiGRU Performed Better

A sentence can carry important contextual information at different positions. For example:

> "I thought the movie would be boring, but it was amazing."

Understanding the *complete* context is essential for correctly identifying the emotion. A Bidirectional GRU processes the sequence in both directions, letting the model draw on information from both earlier and later words when building a sentence representation — helping it understand context far better than a one-directional recurrent network.

---

## 🛠️ Technologies Used

- Python
- TensorFlow / Keras
- Deep Learning
- NLP
- RNN, LSTM, GRU, Bidirectional GRU
- Hugging Face Datasets
- FastAPI
- Uvicorn
- Jupyter Notebook
- VS Code

---

## 📁 Project Structure

```
Deep learning NLP/
│
├── Artifacts/
│   ├── BiGRU_model.h5
│   └── tokenizer.pkl
│
├── static/
│   └── [Frontend files]
│
├── main.py
├── work.ipynb
├── .gitignore
└── README.md
```

**Important files:**

| File / Folder | Description |
|---|---|
| `work.ipynb` | Complete experimentation workflow — dataset loading, preprocessing, tokenization, padding, training (RNN/LSTM/GRU/BiGRU), evaluation, comparison, and model saving |
| `Artifacts/` | Trained BiGRU model and tokenizer used for prediction |
| `main.py` | FastAPI application that serves the trained model |
| `static/` | Frontend/static files for interacting with the application |

---

## 💾 Model Saving

After training, the final BiGRU model and tokenizer are saved so the model doesn't need to be retrained every time the application starts:

```
Artifacts/
├── BiGRU_model.h5
└── tokenizer.pkl
```

The tokenizer is essential — it ensures an input sentence is converted into the same numerical representation used during training.

---

## 🌐 FastAPI Deployment

The trained model is served through a FastAPI application.

**Start the app:**

```bash
uvicorn main:app --reload
```

**Access the API:**

| Endpoint | URL |
|---|---|
| API base | http://127.0.0.1:8000 |
| Interactive docs | http://127.0.0.1:8000/docs |

---

## 🧪 Example

| Input | Predicted Emotion |
|---|---|
| "I am extremely happy today because I got selected for my dream job." | Joy |
| "I am scared because I don't know what will happen next." | Fear |

---

## 🔄 Complete Workflow

```
Hugging Face Dataset
        │
        ▼
 Text Preprocessing
        │
        ▼
     Tokenizer
        │
        ▼
 Sequence Padding
        │
        ▼
┌───────┼───────┐
▼       ▼       ▼
RNN    LSTM    GRU
│       │       │
└───────┼───────┘
        ▼
      BiGRU
        │
        ▼
 Model Evaluation
        │
        ▼
BiGRU – 91.55% Accuracy
        │
        ▼
Save Model + Tokenizer
        │
        ▼
    FastAPI API
        │
        ▼
 Emotion Prediction
```

---

## 📌 Key Learning Outcomes

- Natural Language Processing fundamentals
- Text tokenization and sequence padding
- Word-to-integer representation
- Recurrent Neural Networks (RNN, LSTM, GRU)
- Bidirectional RNN concepts
- Model training, evaluation, and comparison across architectures
- Saving and reusing trained TensorFlow/Keras models and tokenizers
- Building a FastAPI inference API
- Deploying a Deep Learning model for real-time text prediction

---

## 🎯 Future Improvements

- [ ] Improve dataset and class balance
- [ ] Hyperparameter tuning
- [ ] Use pretrained word embeddings
- [ ] Experiment with BiLSTM
- [ ] Experiment with Transformer-based models
- [ ] Add confidence/probability scores for predictions
- [ ] Improve the frontend UI
- [ ] Deploy the API and application online
- [ ] Add batch prediction support

---

## 👨‍💻 Project Summary

**EmotionSense** — AI-based emotion detection from text, built as a Deep Learning NLP project to experiment with and compare different recurrent neural network architectures for emotion classification.

| | |
|---|---|
| **Best Model** | Bidirectional GRU (BiGRU) |
| **Test Accuracy** | 91.55% |
| **Test Loss** | 0.23443 |

---

## ⭐ Conclusion

This project demonstrates that model architecture can have a significant impact on NLP classification performance. While the basic RNN, LSTM, and GRU models achieved relatively low accuracy in this experiment, the Bidirectional GRU produced a substantial improvement, reaching **91.55% test accuracy**. The final BiGRU model was therefore selected for the prediction application and FastAPI integration.
