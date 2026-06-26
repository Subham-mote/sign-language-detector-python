<div align="center">

# 🤟 Sign Language Detector

### Real-time hand-sign recognition using your webcam — built with OpenCV, MediaPipe & Scikit-learn

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![OpenCV](https://img.shields.io/badge/OpenCV-4.7-green.svg)](https://opencv.org/)
[![MediaPipe](https://img.shields.io/badge/MediaPipe-0.9-orange.svg)](https://google.github.io/mediapipe/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](License)




</div>

---

## ✨ What is this?

This project recognizes **hand signs in real time** using your webcam. It uses **MediaPipe** to detect 21 hand landmarks per frame, then feeds those landmark coordinates into a **Random Forest classifier** that predicts which sign is being shown — no deep learning model or GPU required!

Currently trained to recognize **3 signs**: `A`, `B`, and `L` — but it's fully extensible to any number of custom signs you want to teach it.

---

## 🧠 How it Works

<p align="center">
 
</p>

| Step | Script | What it does |
|------|--------|---------------|
| 1️⃣ | `collect_imgs.py` | Captures images of your hand for each sign class via webcam |
| 2️⃣ | `create_dataset.py` | Uses MediaPipe to extract normalized (x, y) hand-landmark coordinates from each image |
| 3️⃣ | `train_classifier.py` | Trains a Random Forest model on the landmark data and reports accuracy |
| 4️⃣ | `inference_classifier.py` | Runs the trained model live, drawing a bounding box + predicted letter on screen |

---

## 📦 Tech Stack

- **OpenCV** — webcam capture & frame rendering
- **MediaPipe** — hand detection & 21-point landmark extraction
- **Scikit-learn** — Random Forest classifier, train/test split, accuracy scoring
- **NumPy / Pickle** — data handling & model persistence

---

## 🚀 Getting Started

### 1. Clone & install dependencies

```bash
git clone https://github.com/<your-username>/sign-language-detector-python.git
cd sign-language-detector-python
pip install -r requirements.txt
```

### 2. Collect your training data

```bash
python collect_imgs.py
```
> 📸 Press **Q** when ready, then hold each sign steady — 100 images are captured automatically per class.

### 3. Build the landmark dataset

```bash
python create_dataset.py
```
> This converts raw images into a `data.pickle` file of normalized hand-landmark coordinates.

### 4. Train the classifier

```bash
python train_classifier.py
```
> Outputs classification accuracy and saves the trained model to `model.p`.

### 5. Run live detection 🎥

```bash
python inference_classifier.py
```
> Show a hand sign to your webcam and watch the predicted letter appear on screen in real time!

---

## 🎯 Customizing for Your Own Signs

Want to recognize more than `A`, `B`, `L`? Easy:

1. Open `collect_imgs.py` and change `number_of_classes` to however many signs you want.
2. Re-run the full pipeline (steps 2–5 above).
3. Update the `labels_dict` in `inference_classifier.py` to map class indices to your new sign names.

---

## 📁 Project Structure

```
sign-language-detector-python/
├── collect_imgs.py          # Step 1: Webcam image collection
├── create_dataset.py        # Step 2: Landmark extraction → data.pickle
├── train_classifier.py      # Step 3: Model training → model.p
├── inference_classifier.py  # Step 4: Real-time prediction
├── requirements.txt
└── data/                    # Collected images (per class)
```

---

## 💡 Why MediaPipe + Random Forest?

Instead of training a heavy CNN on raw pixels, this project leverages **MediaPipe's pre-trained hand-landmark model** to extract just 21 key points per hand. This drastically reduces the input dimensionality, meaning a lightweight, fast-to-train **Random Forest** can achieve strong accuracy — all running smoothly on a CPU, with no GPU needed.

---

## 🤝 Contributing

Pull requests are welcome! Feel free to open an issue if you'd like to suggest more signs, improve detection robustness, or extend this to full ASL alphabet support.

---

## 📄 License

This project is licensed under the MIT License — see the [License](License) file for details.

<div align="center">

**Built with 🤟 for accessible communication**

</div>
