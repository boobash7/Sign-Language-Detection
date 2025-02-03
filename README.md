# Sign Language Recognition using LSTM

This project focuses on recognizing sign language gestures using an LSTM (Long Short-Term Memory) model trained on extracted keypoints from sign videos. The model processes real-time webcam input to predict sign language gestures corresponding to seasons (Summer, Winter, Spring, Autumn, and Monsoon).

---

## 📂 Project Structure
```
SignLanguageRecognition/
│── dataset/                           # Raw video dataset (if applicable)
│   ├── Seasons/
│   │   ├── Summer/
│   │   │   ├── video1.mp4
│   │   │   ├── video2.mp4
│   │   ├── Winter/
│   │   ├── Spring/
│   │   ├── Autumn/
│   │   ├── Monsoon/
│── Keypoints/                         # Extracted keypoints directory
│   ├── Seasons/
│   │   ├── Summer/
│   │   │   ├── video1.npy
│   │   │   ├── video2.npy
│   │   ├── Winter/
│   │   ├── Spring/
│   │   ├── Autumn/
│   │   ├── Monsoon/
│── models/
│   ├── sign_language_model.h5         # Trained LSTM model
│── extract_keypoints.py                # Extracts keypoints from video
│── train_lstm.py                        # Trains LSTM model on keypoints
│── test_realtime.py                     # Tests the model in real-time
│── README.md                            # This file
```

---

## 🚀 How to Run the Project

### 1️⃣ Install Dependencies
```bash
pip install numpy tensorflow opencv-python mediapipe sklearn
```

### 2️⃣ Extract Keypoints from Videos
```bash
python extract_keypoints.py
```
* This script extracts pose keypoints from videos in `dataset/Seasons` and saves them as `.npy` files in `Keypoints/Seasons`.

### 3️⃣ Train the LSTM Model
```bash
python train_lstm.py
```
* This script loads the keypoints, preprocesses them, trains an LSTM model, and saves it as `models/sign_language_model.h5`.

### 4️⃣ Run Real-Time Sign Recognition
```bash
python test_realtime.py
```
* This script loads the trained model and uses a webcam to classify sign language gestures in real time.

---

## 📜 Step-by-Step Breakdown

### **1️⃣ extract_keypoints.py (Extracting Keypoints)**
- Loads videos from `dataset/Seasons`.
- Uses **MediaPipe** to extract 33 pose keypoints per frame.
- Saves extracted keypoints as `.npy` files in `Keypoints/Seasons`.

**What happens?**
- Each `.npy` file contains a sequence of keypoints for a video.

### **2️⃣ train_lstm.py (Training the Model)**
- Loads `.npy` keypoints from `Keypoints/Seasons`.
- Normalizes and pads sequences to a fixed length (30 frames per video).
- Encodes labels (Summer, Winter, etc.) into numerical values.
- Trains an **LSTM neural network** on the keypoints.
- Saves the trained model as `models/sign_language_model.h5`.

### **3️⃣ test_realtime.py (Testing in Real-Time)**
- Loads the trained LSTM model.
- Captures real-time frames using OpenCV.
- Extracts keypoints from each frame.
- Passes the keypoints to the LSTM model for prediction.
- Displays the predicted season on the screen.

---

## 🛠️ Troubleshooting

🔹 **Model predicts only one label (e.g., Spring)**
- Ensure the dataset has a **balanced** number of videos for each category.
- Increase the number of training epochs in `train_lstm.py`.
- Try **data augmentation** (e.g., mirroring, rotating videos).

🔹 **Webcam not detecting gestures properly**
- Ensure good lighting and clear gestures.
- Adjust keypoint extraction parameters.

---

## 🏆 Future Improvements
✅ Increase dataset size for better accuracy.
✅ Optimize LSTM architecture (try CNN+LSTM or Transformer models).
✅ Implement a **user-friendly GUI** for easier interaction.

---

This guide provides a **step-by-step** approach for running and understanding the project. Let me know if you need any improvements! 🚀

