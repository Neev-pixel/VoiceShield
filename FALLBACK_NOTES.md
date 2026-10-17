# 🛡️ VoiceShield — Current State & Fallback Recovery Notes
**Timestamp:** 2026-10-17 11:15 IST  
**Hackathon Track:** Track 1: Finance (UNCLONE Hackathon)  
**Main Production File:** [`app.py`](file:///c:/Users/Neev/Downloads/unclone/app.py)

---

## 💾 Saved Fallback Files

Two identical, complete fallback copies of your current code have been generated in your workspace:

1. **[`app_notes.txt`](file:///c:/Users/Neev/Downloads/unclone/app_notes.txt)**
   - Plain text notes format containing the exact entire working source code (2,812 lines, 135 KB).
   - Can be opened in Notepad, VS Code, or any text editor without triggering python linter warnings or auto-execution.

2. **[`app_backup_notes.py`](file:///c:/Users/Neev/Downloads/unclone/app_backup_notes.py)**
   - Python format ready to run or swap immediately if needed.

---

## ⚡ Instant 1-Step Recovery Commands

If anything ever goes wrong or an unwanted edit occurs, open PowerShell in this directory and run:

```powershell
# Restore app.py from the backup notes
Copy-Item app_backup_notes.py app.py -Force
```

Or run the backup file directly:
```powershell
python -m streamlit run app_backup_notes.py --server.port 8501
```

---

## 📋 Key Architecture & Calibrated Settings in This Snapshot

### 1. Tab 1: Payment Verification (Dual-Key Gateway)
- **Universal Fintech Branding:** Cleaned of all UPI prefixes. Universally branded as Payment Verification.
- **Mutual Exclusivity:** Uploading an audio file resets and clears the microphone recording widget; recording audio resets and clears the upload widget. Includes `🗑️ Clear Audio` reset button.
- **Cross-Tab Lockdown:** If Sentinel detects AI speech while armed, Tab 1 displays the full-screen lockdown shield and halts transaction processing with `st.stop()`.

### 2. Tab 2: Live Call & Meeting Sentinel
- **Dual Capture Modes:**
  - *Browser/Meeting Stream:* Captures Chrome tab audio (Google Meet, Zoom Web, etc.) and direct audio.
  - *Native WAV Recording:* Streams 16 kHz mono RIFF WAV frames directly to the backend server (`http://127.0.0.1:8502/api/analyze_audio`) so Detectif.AI processes it with 100% format fidelity.
- **Microphone & File Analyzer:** Features mutual exclusivity (`sentinel_rec_idx`, `sentinel_up_idx`) and a `🗑️ Clear Audio` button.
- **Armed vs. Disarmed Gating:**
  - Switch **ON**: AI detection immediately shuts down Tab 1 Payment Gateway.
  - Switch **OFF**: AI detection displays advisory notice in Tab 2; Tab 1 remains active and unaffected.

### 3. Deepfake Detection & Forensic Thresholds
- **Detectif.AI API:**
  - AI verdict strictly requires `verdict in ["fake", "synthetic"]` or `raw_score >= max(threshold, 0.65)`.
  - Organic human voice guarantees `human_authenticity >= 78.0%`, `verdict = "real"`, and `is_ai = False`.
- **Acoustic Forensic Fallback:**
  - Real FFT spectral centroid via NumPy `rfft` with Hanning windowing.
  - Scale-invariant zero-crossings per second ($\text{cps} = \text{zcr} \times \text{framerate}$).
  - Anomaly threshold calibrated to 0.70; normal speech energy and cadence default to **Organic Human Speech** (`84%–94%`, `verdict = "real"`, `action = "CLEAR"`).

---

## 🧪 Test Suite Reference
All 10 unit tests in [`test_app_cases.py`](file:///c:/Users/Neev/Downloads/unclone/test_app_cases.py) are passing:
- Dual Pass release ($>70\%$)
- Step-Up Voice CAPTCHA on Borderline ($40\%-70\%$)
- Immediate Escrow Freeze on Critical Failure ($<40\%$)
- Speaker verification non-zero guarantee
- Sentinel armed/disarmed gating
- Audio input mutual exclusivity (Tab 1 & Tab 2)
- 6-word banking CAPTCHA compliance
- Organic speech non-AI validation
