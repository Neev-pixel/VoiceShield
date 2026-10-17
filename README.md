# 🛡️ VoiceShield — Dual-Key Voice Biometrics & Real-Time Call Fraud Gateway

> **Track 1: Finance** | Production-Grade Streamlit Application  
> An autonomous voice fraud prevention gateway defending high-value financial transfers (UPI, NEFT, RTGS) and continuous live calls from AI voice cloning, deepfake audio injection, and social engineering fraud.

---

## 🌟 Key Features

### 1. 🔐 Dual-Key Biometric Gateway (Tab 1)
- **Key 1 · Organic Human Authenticity**: Analyzes audio signals for synthetic vocoder carrier leak, zero-crossing anomalies, spectral clamp, and deepfake artifacts powered by Detectif.AI engine.
- **Key 2 · Speaker Biometric Verification**: Compares acoustic voiceprints against an enrolled biometric reference audio (`reference_speaker.wav`) to prevent identity impersonation.
- **Strict Decision Matrix**:
  | Status | Criteria | Action |
  | :--- | :--- | :--- |
  | **Case 1: Dual Pass** | Both Key 1 & Key 2 $\ge 85.0\%$ | Instant settlement released (₹85,000.00) |
  | **Case 2: Borderline** | Scores between $40.0\% - 85.0\%$ | Adaptive 6-word dynamic Voice CAPTCHA step-up challenge |
  | **Case 3: CAPTCHA Fail** | CAPTCHA scores $< 85.0\%$ | Replay/clone attack confirmed $\rightarrow$ 2-Hour Guardian Escrow |
  | **Case 4: Critical Failure** | Either Key 1 or Key 2 $< 40.0\%$ | Immediate transaction lock $\rightarrow$ 2-Hour Guardian Escrow |

### 2. 🎙️ Live Call & Meeting Sentinel (Tab 2)
- **Real-Time Meeting Capture**: Captures ongoing browser tabs, Google Meet, Zoom, or Teams audio directly via Web Audio API.
- **Automated Fraud Gateway Lock**: Flags AI-generated voices in real-time ($<40\%$ authenticity) and instantly locks the Tab 1 payment gateway in Guardian Escrow.

---

## 🚀 Quickstart & Local Setup

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
```

### 2. Create and Activate a Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the Streamlit Application
```bash
streamlit run app.py
```
Open your browser at `http://localhost:8501`.

### 5. Run the Test Suite
```bash
python test_app_cases.py
```

---

## 🌐 Deploy to Streamlit Community Cloud (Free 1-Click Hosting)

1. Push your repository to GitHub (follow the deployment steps below).
2. Go to [share.streamlit.io](https://share.streamlit.io/) and sign in with GitHub.
3. Click **"New app"**.
4. Select your repository, branch (`main`), and set the main file path to:
   ```text
   app.py
   ```
5. *(Optional)* In **Advanced settings** $\rightarrow$ **Secrets**, configure your API keys:
   ```toml
   DETECTIFAI_API_KEY = "your-detectifai-key"
   GEMINI_API_KEY = "your-gemini-key"
   ```
6. Click **Deploy!** Your app will be live on a public `*.streamlit.app` URL.

---

## 📁 Repository Structure

```text
├── app.py                  # Main Streamlit application
├── reference_speaker.wav   # Enrolled reference voiceprint sample
├── requirements.txt        # Python package dependencies
├── test_app_cases.py       # Automated unit test suite (10/10 tests)
├── .gitignore              # Ignored files, cache, and secrets
└── README.md               # Project documentation & deployment guide
```

---

## 📜 License
MIT License. Built for hackathon demonstration.
