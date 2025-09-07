# anpr-license-plate-recognition

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-green.svg)](https://conventionalcommits.org)
[![Python](https://img.shields.io/badge/python-3.10%2B-blue.svg)](https://www.python.org/)
[![Release](https://img.shields.io/badge/release-v0.1.0-orange.svg)](../../releases)

---

## 📖 Overview

This repository provides an **Automatic Number Plate Recognition (ANPR)** pipeline built with:

* **YOLOv3 (OpenCV DNN module)** for license plate detection.
* **EasyOCR** for character recognition.

The system detects license plates in images, crops them, applies preprocessing, and uses OCR to extract alphanumeric text. This is a **portfolio-ready implementation**, showcasing end-to-end computer vision and text recognition.

---

## 📂 Repository Structure

```
anpr-license-plate-recognition/
├─ src/                 # Source code (main pipeline, utils)
│   ├─ main.py          # Entrypoint with CLI
│   └─ util.py          # Helper functions (NMS, draw, outputs)
├─ configs/
│   └─ default.yaml     # Default configuration (paths, thresholds)
├─ models/              # YOLOv3 model assets
│   ├─ config/          # darknet-yolov3.cfg
│   ├─ weights/         # model.weights
│   └─ classes.names    # classes file
├─ data/                # Sample images (ignored in .git)
│   └─ README.md        # Instructions for placing datasets
├─ notebooks/           # (Optional) experiments, EDA
├─ docs/                # Documentation
│   └─ assets/          # Figures, diagrams
├─ build/               # Outputs (annotated images, logs)
└─ README.md            # Project documentation
```

---

## ⚙️ Getting Started

### Prerequisites

* **Python 3.10+**
* [Tesseract OCR](https://github.com/tesseract-ocr/tesseract) installed and added to PATH (required by EasyOCR on some systems).
* GPU optional (OpenCV DNN runs on CPU by default).

### Installation

```powershell
# Clone repository
git clone https://github.com/AlbertoMarquillas/anpr-license-plate-recognition.git
cd anpr-license-plate-recognition

# (Optional) create virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt

# If requirements.txt not present, install manually
pip install opencv-python easyocr numpy pyyaml matplotlib
```

### Folder setup

* Place YOLOv3 model files in `models/`:

  * `models/config/darknet-yolov3.cfg`
  * `models/weights/model.weights`
  * `models/classes.names`
* Place input images in `data/`.

---

## ▶️ Usage

Run the pipeline with default settings (YAML config):

```powershell
python .\src\main.py --save --show
```

Specify arguments explicitly:

```powershell
python .\src\main.py `
  --input-dir data `
  --model-dir models `
  --cfg config/darknet-yolov3.cfg `
  --weights weights/model.weights `
  --classes classes.names `
  --langs en `
  --save --show
```

Key options:

* `--save` → Save annotated outputs in `build/outputs/`.
* `--show` → Display annotated images interactively.
* `--langs` → Specify EasyOCR languages, e.g., `--langs en es`.

---

## 📊 Example Output

Detected plate text with confidence scores printed in terminal, and annotated images saved in `build/outputs/`.

```
[car1.jpg] 1234ABC (score=0.89)
[car2.png] 4567XYZ (score=0.83)
```

---

## 📁 Dataset & Models

* **Datasets**: not included. Place your own test images in `data/`.
* **Models**: not included. Add YOLOv3 config, weights, and classes to `models/`.
* See `data/README.md` and `models/README.md` for detailed instructions.

---

## ✨ Features

* License plate detection using **YOLOv3 + OpenCV DNN**.
* Non-Maximum Suppression (NMS) for cleaner bounding boxes.
* Plate preprocessing (grayscale, thresholding).
* Text recognition with **EasyOCR**.
* CLI with PowerShell examples.
* Configurable thresholds and model paths via YAML.
* Portfolio-ready repo structure and documentation.

---

## 📚 What I Learned

* Building an **end-to-end ANPR system** combining detection + OCR.
* Using **OpenCV DNN** to load and run YOLO models.
* Handling detection outputs, confidence thresholds, and NMS.
* Integrating **EasyOCR** for multilingual text recognition.
* Designing a **portfolio-friendly project structure** for recruiters.

---

## 🚀 Roadmap

* [ ] Add Dockerfile for reproducible environments.
* [ ] Expand support for YOLOv5/YOLOv8 detection.
* [ ] Integrate video stream input (real-time ANPR).
* [ ] Add unit tests in `test/`.
* [ ] Pretrained model links via GitHub Releases.

---

## 📝 License

This project is licensed under the [MIT License](LICENSE).
