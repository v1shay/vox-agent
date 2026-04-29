<div align="center">

<img width="1526" height="1030" alt="PNG image" src="https://github.com/user-attachments/assets/a024d807-f010-4bce-82d2-e2b69c928c8d" />

---

**Vox-agent is a hardware-integrated audio intelligence system** with near-0 I/O overhead, a <1s processing loop, and continuous real-time output.

It runs entirely from the command line, converting live speech into structured markdowns with low latency.

</div>

---

## Features

- Real-time microphone streaming via macOS CoreAudio (AirPods / Mac input)  
- Incremental speech-to-text using Whisper (local CPU inference)  
- Rolling transcript accumulation with chunked processing  
- Mode-based structured formatting (meeting, study, recitation, interview)  
- Sub-second formatting loop using an OpenAI API  
- Markdown session export for persistent structured notes  
- CLI configuration for chunk size and formatting interval  
- Secure API key management via environment variables  

---

## Architecture

| Layer | Purpose | Stack |
|---|---|---|
| Input | Live audio capture from hardware | CoreAudio + sounddevice |
| Buffering | Chunking + rolling window management | Python streaming loop |
| Transcription | Speech → text (incremental) | Whisper (local inference) |
| Processing | Transcript accumulation + timing control | Python |
| Formatting | Semantic structuring of text | OpenAI API (gpt-4o-mini) |
| Output | Console + Markdown export | CLI + file system |

---

## Anatomy

```txt
vox-agent/
├── app/
│   ├── stream.py        # audio capture and buffering
│   ├── transcribe.py   # whisper inference pipeline
│   ├── llm.py          # formatting + API calls
│   └── run_live.py     # orchestration loop
├── out/                # markdown session outputs
├── requirements.txt
├── .env
└── README.md<img width="1526" height="1030" alt="PNG image" src="https://github.com/user-attachments/assets/f23c7184-2169-4a13-a9fd-d182536ddcbd" />
```

## Install

```bash
git clone https://github.com/your-username/vox-agent.git
cd vox-agent
pip install -r requirements.txt
python app/run_live.py
```

## Install missing dependencies

```bash
brew install portaudio
```
