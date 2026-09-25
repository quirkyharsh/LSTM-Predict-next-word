# 🧠 Next Word Prediction Using LSTM

> **A Deep Learning project that predicts the next word in a sequence using an LSTM-based Neural Network trained on Shakespeare's *Hamlet*.**

[![Python](https://img.shields.io/badge/Python-3.x-blue?logo=python)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-Keras-orange?logo=tensorflow)](https://www.tensorflow.org/)
[![Streamlit](https://img.shields.io/badge/Streamlit-App-red?logo=streamlit)](https://streamlit.io/)
[![LSTM](https://img.shields.io/badge/Deep%20Learning-LSTM-purple)]()
[![Status](https://img.shields.io/badge/Status-Deployed-success)]()

---

## 📌 Project Overview

**Next Word Prediction Using LSTM** is a Deep Learning application that predicts the most likely next word based on a sequence of words provided by the user.

The model is trained using the text of Shakespeare's ***Hamlet***. The text is tokenized into numerical sequences and used to train an **LSTM (Long Short-Term Memory)** neural network.

A **Streamlit web application** provides a simple interface where users can enter a sequence of words and receive the model's predicted next word in real time.

### ✨ Example

```text
Input:
To be or not to

Prediction:
be
```

The model learns word relationships and sequence patterns from the training text and uses those patterns to generate the next-word prediction.

---

## 🎯 Objectives

The main objectives of this project are:

* Understand **sequence prediction** using Deep Learning.
* Implement an **LSTM neural network** for Natural Language Processing.
* Convert text into numerical sequences using a **Tokenizer**.
* Train the model to predict the next word.
* Use **padding** to maintain consistent input sequence lengths.
* Implement **Early Stopping** to help prevent overfitting.
* Save and reuse the trained model and tokenizer.
* Build an interactive **Streamlit web application**.
* Deploy the application as a web service.

---

## 🧠 How It Works

The complete workflow can be summarized as:

```text
                 ┌─────────────────┐
                 │  Hamlet Dataset │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Text Preprocess │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │    Tokenizer    │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Create Sequences│
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Padding Sequences│
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  LSTM Network   │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │  Train + Early  │
                 │     Stopping    │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Saved Model +   │
                 │    Tokenizer    │
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Streamlit Web App│
                 └────────┬────────┘
                          │
                          ▼
                 ┌─────────────────┐
                 │ Next Word       │
                 │ Prediction      │
                 └─────────────────┘
```

---

## 📚 Dataset

The project uses the **Shakespeare's *Hamlet*** text available through the NLTK Gutenberg corpus.

During preprocessing:

1. The Hamlet text is loaded.
2. The text is converted to lowercase.
3. A Keras `Tokenizer` creates a numerical index for each word.
4. Word sequences are generated from the text.
5. Sequences are padded to maintain a consistent length.

The project notebook uses:

```python
from nltk.corpus import gutenberg

data = gutenberg.raw('shakespeare-hamlet.txt')
```

The processed dataset is saved as:

```text
hamlet.txt
```

---

## 🤖 Model Architecture

The project uses an **LSTM-based neural network** for sequence prediction.

The architecture consists of:

```text
Input Sequence
      ↓
Embedding Layer
      ↓
LSTM Layer
      ↓
LSTM Layer
      ↓
Dense Layer
      ↓
Softmax
      ↓
Predicted Next Word
```

### Why LSTM?

LSTM networks are designed for sequential data and can learn relationships between words across a sequence.

For this project, the model learns patterns such as:

```text
Previous Words → Next Word
```

For example:

```text
"To be or not to"
              ↓
        Predicted Word
```

---

## ⚙️ Training

The model is trained using the prepared sequences generated from the Hamlet text.

**Early Stopping** is used during training to monitor validation performance and stop training when the model stops improving, helping reduce unnecessary training and potential overfitting.

---

## 💾 Saved Model

After training, the project saves two important files:

### `next_word_lstm.h5`

Contains the trained LSTM model.

### `tokenizer.pickle`

Contains the trained tokenizer and its word-to-index mapping.

The notebook saves them using:

```python
model.save("next_word_lstm.h5")

with open('tokenizer.pickle', 'wb') as handle:
    pickle.dump(tokenizer, handle, protocol=pickle.HIGHEST_PROTOCOL)
```

These files allow the Streamlit application to perform predictions without retraining the model.

---

## 🖥️ Streamlit Application

The web interface is built using **Streamlit**.

Users can:

1. Enter a sequence of words.
2. Click **Predict Next Word**.
3. Get the predicted next word.

The application loads the trained model and tokenizer when it starts.

### Application Flow

```text
User Input
    ↓
Tokenizer
    ↓
Convert Words → Numbers
    ↓
Padding
    ↓
LSTM Model
    ↓
Probability Distribution
    ↓
Highest Probability Word
    ↓
Prediction
```

---

## 📁 Project Structure

```text
Next-Word-Prediction/
│
├── app.py
├── next_word_lstm.h5
├── tokenizer.pickle
├── hamlet.txt
├── experiemnts(1).ipynb
├── requirements.txt
├── Procfile
└── README.md
```

### File Description

| File                   | Description                                    |
| ---------------------- | ---------------------------------------------- |
| `app.py`               | Streamlit application                          |
| `next_word_lstm.h5`    | Trained LSTM model                             |
| `tokenizer.pickle`     | Saved tokenizer                                |
| `hamlet.txt`           | Hamlet training text                           |
| `experiemnts(1).ipynb` | Complete experimentation and training notebook |
| `requirements.txt`     | Python dependencies                            |
| `Procfile`             | Render deployment configuration                |
| `README.md`            | Project documentation                          |

---

## 🛠️ Technologies Used

| Technology            | Purpose              |
| --------------------- | -------------------- |
| 🐍 Python             | Programming language |
| 🧠 TensorFlow / Keras | Deep Learning model  |
| 🔁 LSTM               | Sequence prediction  |
| 🔤 Keras Tokenizer    | Text tokenization    |
| 🔢 NumPy              | Numerical operations |
| 📊 Scikit-learn       | Data preparation     |
| 🎨 Streamlit          | Web application      |
| 📖 NLTK               | Dataset collection   |
| ☁️ Render             | Deployment           |

---

## 🚀 Run Locally

### 1. Clone the repository

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
```

### 2. Navigate to the project

```bash
cd Next-Word-Prediction
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the environment

**Windows:**

```bash
venv\Scripts\activate
```

**Linux / macOS:**

```bash
source venv/bin/activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

### 6. Run the Streamlit application

```bash
streamlit run app.py
```

The application will open in your browser.

---

## ☁️ Deployment on Render

This project can be deployed as a **Render Web Service**.

### Required Files

Make sure the repository contains:

```text
app.py
requirements.txt
Procfile
next_word_lstm.h5
tokenizer.pickle
```

### Render Configuration

**Build Command**

```bash
pip install -r requirements.txt
```

**Start Command**

```bash
streamlit run app.py --server.port $PORT --server.address 0.0.0.0
```

Render will install the dependencies, start the Streamlit application, and expose it through a public URL.

---

## 🔮 Future Improvements

Some possible improvements for future versions include:

* 🔥 Train on a much larger dataset.
* 📚 Use multiple books instead of only *Hamlet*.
* 🧠 Experiment with GRU and Transformer architectures.
* ✍️ Predict multiple words instead of only one.
* 🎯 Add top-k predictions with probability scores.
* ⚡ Optimize the model for faster inference.
* 🎨 Improve the Streamlit UI.
* 📱 Make the interface more responsive.
* 🌐 Support additional datasets and languages.

---

## 📖 What I Learned

Through this project, I worked with:

* Natural Language Processing
* Text preprocessing
* Tokenization
* Sequence generation
* Padding
* LSTM networks
* Word prediction
* Softmax classification
* Early stopping
* Model serialization
* Streamlit
* Machine Learning deployment

---

## 👨‍💻 Author

### Harsh Patil

**Computer Science Engineering Student | Full-Stack & AI/ML Enthusiast**

I'm interested in **Artificial Intelligence, Machine Learning, Deep Learning, NLP, and Full-Stack Development**.

---

## ⭐ Support

If you found this project useful or interesting, consider giving the repository a ⭐ on GitHub!

---

## 📄 License

This project is intended for **educational and learning purposes**.
