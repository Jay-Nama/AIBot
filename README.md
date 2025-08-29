# AI-Powered Discord Bot with Handwriting Recognition

This project is a **multi-functional AI Discord Bot** that integrates:
- 🤖 AI-generated chat responses (via Ollama LLaMA-3)
- ✍️ Handwriting recognition (custom CNN+RNN model on IAM dataset)
- 🌍 Text translation (deep_translator API to Google Translate)
- 🖼️ AI image generation (Pollinations.ai API)

It was developed as the **final project for CIS-579 Artificial Intelligence (Fall 2024)** by **Team 8** (Matthew Bryce, Jayanth Nama, and Raj Patel).

---

## 🚀 Features
- **AI Chat**: Uses Ollama (LLaMA-3) for contextual responses to Discord chat prompts.  
- **Handwriting Recognition**:
  - Trained on the IAM Words dataset (~96k samples, 80+ character classes).
  - CNN extracts features → RNN (BiLSTM) handles sequences → CTC loss for prediction.
  - Achieves ~70% word-level accuracy, precision 0.96, F1-score 0.74.  
  - Supports multi-word segmentation (custom images).  
- **Translation**: Translate messages to multiple languages using flags (`!translate`).  
- **Image Generation**: Generate images from text prompts with Pollinations.ai (`!image`).  

---

## 🛠️ Tools & Technologies
- **Discord Bot**: Discord.py, Discord Developer Portal  
- **LLM**: Ollama (LLaMA-3)  
- **Handwriting Recognition**: TensorFlow, Keras, sklearn, OpenCV, NumPy, PIL, Matplotlib  
- **Translation**: deep_translator (Google Translate API)  
- **Image Generation**: Pollinations.ai + Python requests  

---

## 📂 Dataset
- Dataset: **IAM Handwriting Words** dataset ([link](https://git.io/J0fjL))  
- 96,456 samples of handwritten words (32px height, variable width).  
- Preprocessing: resize to 128×32, grayscale, padding, normalization.  
- Split: 75% train / 12.5% validation / 12.5% test.  
- Labels provided in `words.txt`, converted to TensorFlow pipeline.  

---

## 📊 Model Overview (Handwriting Recognition)
- CNN layers for feature extraction (Conv2D + MaxPooling).  
- Reshaping + Dense → RNN input.  
- 2× BiLSTM layers (128 + 64 units).  
- Output: 81 character classes (letters, numbers, symbols, punctuation).  
- Loss: CTC Loss.  
- Metric: Edit distance callback + accuracy/precision/recall/F1.  
- Best results achieved at **50 epochs**:  
  - Accuracy: **70%**  
  - Precision: **0.96**  
  - Recall: **0.70**  
  - F1-score: **0.74**

---
Sample Handwritten Text Prediction:
16 test samples along with its corresponding text prediction.
<img width="720" height="288" alt="Screenshot 2025-08-29 at 3 33 37 PM" src="https://github.com/user-attachments/assets/2c2d6456-b362-411a-ad8c-2da7d79fe389" />

--- 
## 📸 Examples
**AI Chat**  
`!ask What is AI?` → Bot responds with definition + examples.  
<img width="527" height="437" alt="Screenshot 2025-08-29 at 3 35 03 PM" src="https://github.com/user-attachments/assets/fe413e34-317e-4bf3-9fd4-8a6e41474943" />


**Image Generation**  
`!image guy on the beach sipping coconut water` → Generated beach image.  
<img width="332" height="253" alt="Screenshot 2025-08-29 at 3 36 23 PM" src="https://github.com/user-attachments/assets/e701da12-45f4-43cd-8809-7595bafd7862" />

**Translation**  
`!translate Hello, how are you 🇩🇪` → Bot replies in German.  
<img width="261" height="255" alt="Screenshot 2025-08-29 at 3 36 41 PM" src="https://github.com/user-attachments/assets/ab96b189-5ef5-412e-b31a-9d68dac7eda7" />

**Handwriting Recognition**  
Image with `!convert:` → Bot outputs predicted text.  
<img width="491" height="133" alt="Screenshot 2025-08-29 at 3 34 35 PM" src="https://github.com/user-attachments/assets/07310d37-d195-46c9-85c3-7d0d6aa8f51c" />

---

## ⚙️ Setup

### Clone Repo
```bash
git clone https://github.com/YOUR-USERNAME/discord-ai-bot.git
cd discord-ai-bot
```
