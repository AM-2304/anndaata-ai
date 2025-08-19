# 🌾 AgnnDaata-AI: AI-powered Farmer Support System

Agri-Intellect is a comprehensive AI-driven system designed to empower
farmers with multilingual, multimodal, and offline-first support for
agriculture-related queries. The platform integrates cutting-edge AI
technologies (VLM CDDM, Sarvam AI, Indic ParlerTTS, Whisper), RAG
pipelines, pest/disease image analysis, government scheme retrieval, and
real-time weather-based crop advisory.

------------------------------------------------------------------------

## 📂 Directory Structure

    Agri-Intellect/
    │── data/
    │   ├── Pest_Dataset/              # Pest images (subfolders per pest)
    │   ├── Pesticides.csv             # Pesticide recommendations + dosages
    │   ├── MSP_data.csv               # Minimum Support Price dataset
    │   ├── schemes/                   # PDFs of govt welfare schemes
    │   ├── fundamental-glossary-agriculture-eng-hin-gujarati.pdf
    │
    │── models/
    │   ├── vlm_cddm/                  # Vision-Language Model weights/checkpoints
    │   ├── whisper/                   # Whisper model for STT
    │   ├── parler_tts/                # Indic ParlerTTS model
    │
    │── scripts/
    │   ├── train.py                   # Training (if applicable)
    │   ├── inference.py               # Inference pipeline (query handling)
    │   ├── utils.py                   # Helper functions (translation, weather API, etc.)
    │   ├── reminders.py               # Scheduling & reminder notifications
    │
    │── notebooks/
    │   ├── demo_notebook.ipynb        # Kaggle/Colab demo notebook
    │── requirements.txt
    │── README.md

------------------------------------------------------------------------

## ⚙️ Installation & Setup

### 1️⃣ Clone Repo

``` bash
git clone https://github.com/<your-username>/anndaata-ai.git
cd anndaata-ai
```

### 2️⃣ Install Dependencies

``` bash
pip install -r requirements.txt
```

### 3️⃣ API Keys Setup

Ensure the following environment variables are set: - `WEATHER_API` →
Indian Weather API key from
[indianapi.in](https://indianapi.in/weather-api) - `SERPAPI_KEY` →
[SerpAPI](https://serpapi.com/) for web augmentation - `SARVAM_API_KEY`
→ [Sarvam AI](https://sarvam.ai/) for multilingual translation

``` bash
export WEATHER_API="your_weather_api_key"
export SERPAPI_KEY="your_serpapi_key"
export SARVAM_API_KEY="your_sarvam_key"
```

------------------------------------------------------------------------

## 🚀 Features

-   **🗣 Multilingual Support (Text + Speech)**\
    Farmers can input queries in **Hindi, Gujarati, Punjabi, Marathi,
    Kannada, Telugu, Tamil, English** (speech or text). Queries are
    auto-translated into English for the RAG pipeline.

-   **🔊 STT + TTS**

    -   **Speech-to-Text (STT):** Whisper ASR\
    -   **Text-to-Speech (TTS):** Indic ParlerTTS / Sarvam AI

-   **🖼 Pest & Disease Recognition**\
    Farmers can upload crop/pest images → Identified using **VLM CDDM**,
    matched with `Pest_Dataset`, and mapped to pesticide recommendations
    (`Pesticides.csv`).

-   **🌦 Weather-Aware Crop Recommendation**\
    Uses **Indian Weather API** based on farmer's location to recommend
    suitable crops, irrigation schedules, and harvesting guidance.

-   **💰 MSP & Yield Pricing**

    -   If farmer provides yield → Expected revenue = `MSP * yield`\
    -   If not → Provides just the **MSP value**.

-   **📑 Government Schemes Info Retrieval**\
    Queries about welfare schemes are answered using **RAG on scheme
    PDFs**.

-   **🔔 Reminders & Advisory**\
    Farmers can get notifications for:

    -   Irrigation schedules\
    -   Fertilizer dosage timing\
    -   Harvesting reminders\
    -   Livestock feeding schedules\
    -   Safe storage & crop residue management practices

-   **🌐 Hybrid Online/Offline Mode**

    -   **Online:** Uses RAG + web augmentation (SerpAPI + ChatGPT)\
    -   **Offline:** Falls back to local dataset + pre-downloaded models

------------------------------------------------------------------------

## 🧪 Testing

Run the Kaggle/Colab notebook:

``` bash
notebooks/anndaata-ai.ipynb
```

For direct script testing:

``` bash
python scripts/inference.py --query "बाजरे की सिंचाई कितनी बार करनी चाहिए?"
```

------------------------------------------------------------------------

## 🖥️ UI (Prototype)

Run the Gradio app:

``` bash
gradio run app/ui.py
```

------------------------------------------------------------------------

## 📊 Future Extensions

-   Mobile-first offline app for rural India\
-   Integration with IoT soil sensors for irrigation optimization\
-   Blockchain-based supply chain + crop insurance advisory\
-   Farmer community chatbot for peer-to-peer learning

------------------------------------------------------------------------

## 🤝 Contributors

-   **Akhilesh Magotra** (Project Lead)\
-   **Divyanshu Vashisht**
-   **Aaditya Goel**

------------------------------------------------------------------------

## 📜 License

MIT License © 2025 Agri-Intellect
