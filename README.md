# 🤖 SmartSupport: AI Customer Ticket Desk

An automated, multi-model AI pipeline that reads incoming customer support tickets, classifies the issue, detects customer sentiment to assign priority, and drafts a customized email response using Generative AI. 

Built entirely in Python, this project features a fully interactive web interface powered by Gradio.

## 🌟 Features

* **Intelligent Routing:** Uses Zero-Shot Classification to instantly categorize tickets (e.g., Billing, Technical Support, Shipping).
* **Automated Triage:** Analyzes the sentiment of the customer's message to automatically escalate frustrated users to `🔴 HIGH` priority.
* **Generative Auto-Responder:** Utilizes an instruction-tuned Large Language Model (TinyLlama) to read the context and draft a professional, context-aware email reply.
* **Interactive Web UI:** A sleek, user-friendly dashboard built with Gradio, allowing non-technical users to test the AI models in real-time.

## 🛠️ Tech Stack

* **Language:** Python
* **Web Framework:** Gradio
* **Machine Learning / NLP:** Hugging Face `transformers`, PyTorch
* **Models Used:**
  * *Zero-Shot Classification:* `facebook/bart-large-mnli`
  * *Sentiment Analysis:* `distilbert-base-uncased-finetuned-sst-2-english`
  * *Text Generation (LLM):* `TinyLlama/TinyLlama-1.1B-Chat-v1.0`

## 📸 Dashboard Preview

> **💡 Note to Self:** *Take a screenshot of your Gradio app running in Colab and upload it to your GitHub repository. Replace this text with the image link, like this: `![App Preview](link_to_image.png)`*

## 🚀 How It Works (The Pipeline)

Unlike standard text generators, this application orchestrates **three distinct neural networks** simultaneously to simulate a real-world business workflow:

1. **The Input:** The user pastes a customer complaint into the UI.
2. **The Analysis (Models 1 & 2):** The text is passed to DistilBERT to check if the customer is angry (Negative Sentiment), and to BART to determine which department handles the issue.
3. **The Logic:** Python business rules dictate that if the sentiment is Negative, the priority is escalated.
4. **The Generation (Model 3):** The category, the priority, and the original text are formatted into a structured prompt and fed to TinyLlama, which types out the final email draft.

## 💻 Run it Yourself

This project is optimized to run in a Google Colab notebook with GPU acceleration.

1. Open the `.ipynb` notebook in Google Colab.
2. Go to **Runtime > Change runtime type** and select **T4 GPU**.
3. Run the cells to install the dependencies (`transformers`, `gradio`, `torch`).
4. Run the final cell to launch the web server. Click the generated `gradio.live` public URL to view the app in full screen!
