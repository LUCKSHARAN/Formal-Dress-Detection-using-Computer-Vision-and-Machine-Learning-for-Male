# Setup Instructions

## Project
Formal Dress Code Detection using Computer Vision and Machine Learning for Male  
Built with YOLOv8m + Flask + HTML5 — Real-time browser-based detection

---


## Prerequisites

Make sure you have the following installed:

| Tool | Version | Download |
|---|---|---|
| Python | 3.10 | https://www.python.org/downloads/ |
| Git | Latest | https://git-scm.com/downloads |
| Docker Desktop | Latest | https://www.docker.com/products/docker-desktop |

---

## Method 1 — Run Without Docker (Direct Python)

### Step 1 — Clone the Repository
```bash
git clone https://github.com/LUCKSHARAN/Formal Dress Code Detection using Computer Vision and Machine Learning for Male.git
cd Formal Dress Code Detection using Computer Vision and Machine Learning for Male
```

### Step 2 — Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3 — Run the Application
```bash
python src/app.py
```

### Step 4 — Open in Browser
```
http://localhost:5000
```

---

## Method 2 — Run With Docker

### Step 1 — Clone the Repository
```bash
git clone https://github.com/LUCKSHARAN/Formal Dress Code Detection using Computer Vision and Machine Learning for Male.git
cd dress-detection-web
```

### Step 2 — Build Docker Image
```bash
docker build -t dress-detector .
```
> First build takes 5–10 minutes

### Step 3 — Run Docker Container
```bash
docker run -p 5000:5000 dress-detector
```

### Step 4 — Open in Browser
```
http://localhost:5000
```

---

## Method 3 — Access Live Deployment (No Setup Required)

The application is deployed on HuggingFace Spaces with free HTTPS:
```
https://lucksharan-dress-code-detection.hf.space
```

- Works on any device — laptop, mobile, tablet
- Camera access works automatically (HTTPS)
- No installation required

---

## How to Use the Application

1. Open the URL in your browser
2. Click **Start Detection** button
3. Allow camera permission when prompted
4. Stand **1.5 to 2 meters** away from camera
5. Full body must be visible — head to toe
6. System shows **FORMAL** (green) or **INFORMAL** (red) verdict in real time

### Controls Available
| Button | Function |
|---|---|
| Start Detection | Opens camera and begins detection |
| Pause / Resume | Temporarily stops detection |
| Flip Camera | Switch front/back camera (mobile only) |
| Fullscreen | Expands to full screen |
| Stop | Closes camera and returns to home |

---

## Project Structure
```
dress-detection-web/
├── src/
│   ├── app.py                  Flask backend server
│   ├── Dockerfile              Docker container config
│   ├── templates/
│   │   └── index.html          Frontend — camera, UI, canvas
│   ├── static/                 Static assets
│   └── models/
│       └── best.pt             YOLOv8m trained weights (52MB)
├── docs/
│   ├── IEEE_paper.pdf          Research paper
│   ├── presentation.pptx       Project presentation
│   └── review_report.docx      2nd review report
├── README.md
├── requirements.txt
├── architecture.png
├── demo_video_link.txt
└── setup_instructions.md
```

---

## Tech Stack

| Layer | Technology |
|---|---|
| AI Model | YOLOv8m (Ultralytics) — custom trained |
| Backend | Python 3.10 + Flask |
| Image Processing | OpenCV Headless |
| Frontend | HTML5 + CSS3 + Vanilla JavaScript |
| Camera | MediaDevices API (browser) |
| Containerization | Docker (python:3.10-slim) |
| Deployment | HuggingFace Spaces |
| Version Control | Git + GitHub + Git LFS |

---

## Model Details

| Parameter | Value |
|---|---|
| Architecture | YOLOv8m (Medium) |
| Training Platform | Google Colab + Tesla T4 GPU |
| Epochs | 80 |
| Image Size | 640 × 640 |
| Confidence Threshold | 0.25 |
| Dataset Size | 1,120 images |
| Classes | 11 clothing classes |
| Model File | best.pt (52 MB) |

### Detection Classes
**Formal Mandatory** (all 3 required for FORMAL verdict):
- formal_shirt_tucked
- formal_pant
- formal_shoes

**Formal Optional:**
- belt
- blazer

**Informal Items** (any one triggers INFORMAL verdict):
- formal_shirt_untucked
- tshirt
- informal_pant
- informal_shoes
- cap
- band

---

## Requirements.txt Contents
```
flask>=2.3.0
opencv-python-headless>=4.8.0
ultralytics>=8.0.0
numpy>=1.24.0
Pillow>=9.5.0
gunicorn>=21.2.0
```

---

## Troubleshooting

| Problem | Solution |
|---|---|
| Camera not opening | Allow camera permission in browser settings |
| Camera blocked on mobile | Use HTTPS URL — HTTP blocks camera on mobile |
| Docker build fails | Check internet connection and run build again |
| Model not found error | Make sure models/best.pt exists in src/models/ |
| Port already in use | Change port: `python app.py --port 5001` |
| Slow detection | Close other applications to free up RAM |

---

## Notes

- Mobile camera requires HTTPS — use the HuggingFace deployment URL
- For best accuracy stand 1.5 to 2 meters away with full body visible
- Good lighting improves detection accuracy significantly
- The system is optimized for male formal attire detection only