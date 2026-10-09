# Jal Drishti 🌊👁️
**AI-Powered Underwater Surveillance & Fishery Target Detection**

Developed by **RF AQUA SOLUTIONS**, Jal Drishti (meaning "Water Vision") is a high-performance desktop application designed for real-time underwater monitoring. It utilizes advanced AI (YOLOv11) and computer vision filters to detect aquatic targets, improve low-visibility streams, and record vital telemetry—all while maintaining a zero-latency video feed.

---

## ✨ Key Features

* **Real-Time AI Target Detection:** Integrates Ultralytics YOLOv11 on a dedicated background thread to detect underwater targets without lagging the main video feed.
* **Zero-Latency RTSP Streaming:** Uses highly optimized FFmpeg TCP transport layers via OpenCV to eliminate dropped packets and decoder freezing.
* **Visual Enhancement Modes:**
  * **IR Mode (Simulated):** Converts the feed to high-contrast Grayscale for better structural visibility while keeping AI bounding boxes in color.
  * **Thermal Mode:** Applies an Inferno color map to highlight contrast differences in the water.
  * **Edge Enhancement:** Utilizes Canny edge detection to outline shapes in highly murky environments.
* **Media Capture:**
  * **Snapshots:** Instantly save high-resolution `.jpg` frames with all active overlays.
  * **Smart Recording:** Record `.mp4` video that dynamically syncs playback speed to the live processing FPS, preventing fast-forward/laggy video outputs.
* **Live Telemetry Dashboard:** Displays real-time FPS, water clarity/sharpness variance, active target counts, and hardware statuses.
* **Cinematic Splash Screen:** Features a frameless, 16:9 intro video seamlessly transitioning into the main GUI.

---

## 🛠️ Technology Stack

* **Language:** Python 3.x
* **Computer Vision:** OpenCV (`opencv-python`)
* **AI/Deep Learning:** Ultralytics YOLOv11 (`ultralytics`)
* **GUI Framework:** Tkinter
* **Image Processing:** Pillow (`PIL`)
* **Packaging:** PyInstaller

---

## 🚀 Getting Started (Running from Source)

### 1. Clone the Repository
```bash
git clone https://github.com/yourusername/jal-drishti.git
cd jal-drishti
```

### 2. Install Dependencies
Make sure you have Python installed, then run:
```bash
pip install opencv-python ultralytics pillow
```

### 3. Required Assets
Ensure the following files are placed in the root directory next to `barlus_app.py`:
1. `yolo11n.pt` (The YOLOv11 Nano model)
2. `WhatsApp Image 2026-05-28 at 11.08.14 PM.jpeg` (Company Logo)
3. `splash.mp4` (Intro splash screen video)

### 4. Run the Application
Ensure your RTSP camera is active on the network (Default IP: `192.168.1.88`), then execute:
```bash
python barlus_app.py
```

---

## 📦 Building the Executable (.exe)

To package Jal Drishti as a standalone Windows application for client deployment:

1. Install PyInstaller:
   ```bash
   pip install pyinstaller
   ```
2. Build the application (this prevents the console from opening and creates a folder directory):
   ```bash
   pyinstaller --onedir --windowed barlus_app.py
   ```
3. **CRITICAL STEP:** Once the build is complete, open the newly created `dist/barlus_app` folder. You **must** copy your assets (`yolo11n.pt`, `splash.mp4`, and the logo image) directly into this folder so they sit exactly next to `barlus_app.exe`.
4. Double-click `barlus_app.exe` to launch the software.

---

## 📁 Folder Structure

Once running, the software will automatically generate necessary folders and telemetry logs:

```text
jal-drishti/
├── barlus_app.py             # Main application script
├── yolo11n.pt                # AI Weights
├── splash.mp4                # Intro Video
├── logo.jpeg                 # RF Aqua Solutions Logo
├── telemetry_log.csv         # Auto-generated diagnostics log
└── Media/                    # Auto-generated directory for captures
    ├── snapshot_YYYYMMDD_HHMMSS.jpg
    └── record_YYYYMMDD_HHMMSS.mp4
```

---

## 📝 License & Credits

Developed internally by **RF Aqua Solutions**.
AI Models powered by [Ultralytics](https://ultralytics.com/).