# 🧠 Shakespeare Text Generator (LSTM)

This project is a **character-level text generation model** built using **TensorFlow/Keras** and an **LSTM (Long Short-Term Memory)** network. It is trained on a subset of Shakespeare’s works to generate human-like text based on learned patterns.

---

## 📌 Features

* Character-level text generation
* LSTM-based deep learning model
* Temperature-controlled text sampling
* Pre-trained model loading for quick generation
* Customizable text length and creativity

---

## 📂 Dataset

The dataset is automatically downloaded from TensorFlow:

* **Source**: Shakespeare text corpus
* **Link**: [https://storage.googleapis.com/download.tensorflow.org/data/shakespeare.txt](https://storage.googleapis.com/download.tensorflow.org/data/shakespeare.txt)

Only a subset of the dataset is used:

```python
text = text[300000:800000]
```

---

## ⚙️ How It Works

### 1. Data Preprocessing

* Convert text to lowercase
* Extract unique characters
* Create mappings:

  * `char_to_index`
  * `index_to_char`
* Generate sequences of fixed length (`SEQ_LENGTH = 40`)

---

### 2. Model Architecture

```text
Input → LSTM (128 units) → Dense → Softmax
```

* **LSTM Layer**: Learns sequential dependencies
* **Dense Layer**: Outputs probabilities for each character
* **Softmax Activation**: Converts outputs into probability distribution

---

### 3. Training (Optional)

Training code is included but commented out.

To train:

```python
model.fit(x, y, batch_size=256, epochs=4)
model.save('textgenerator.keras')
```

---

### 4. Text Generation

* A random seed sentence is selected
* Model predicts next character iteratively
* Output is influenced by **temperature**

---

## 🌡️ Temperature Explained

Temperature controls randomness in predictions:

| Temperature | Behavior                     |
| ----------- | ---------------------------- |
| 0.2         | Very predictable, repetitive |
| 0.4         | Slight variation             |
| 0.6         | Balanced                     |
| 0.8         | Creative                     |
| 1.0         | Highly random                |

---

## 🚀 Usage

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

---

### 2. Run the Script

```bash
python main.py
```

---

## 🧩 Key Functions

### 🔹 `sample(preds, temperature)`

Applies temperature scaling and samples the next character probabilistically.

---

### 🔹 `generate_text(length, temperature)`

Generates text of a given length using the trained model.

---

## 📁 Project Structure

```text
├── main.py
├── textgenerator.keras
├── requirements.txt
└── README.md
```

---

## 🔧 Customization

You can modify:

* `SEQ_LENGTH` → Context window size
* `STEP_SIZE` → Data sampling stride
* `length` → Generated text length
* `temperature` → Creativity level

---

## 🧠 Future Improvements

* Train on larger dataset
* Use word-level modeling
* Add GRU/Transformer models
* Build a web interface (Flask/FastAPI)
* Fine-tune on specific writing styles

---

## 📜 License

This project is for educational purposes. Dataset provided by TensorFlow.
