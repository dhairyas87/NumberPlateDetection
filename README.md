# 🚘 License Plate Detection and Recognition from Video (Classical CV + OCR)

This project implements a **classical computer vision–based pipeline** for detecting license plates from video streams and extracting plate numbers using **EasyOCR**.  
The system is designed to work on **day and night videos**, produce **clean visual outputs**, and log recognized plates into an **Excel file** for further analysis.

---

## 📌 Key Features

- 🎥 Processes video input frame-by-frame
- 📦 Detects license plates using **OpenCV (edge + contour based)**
- 🟩 Draws bounding boxes on detected plates in output video
- 🔤 Performs OCR using **EasyOCR**
- 🧹 Filters OCR outputs using **strict plate-format validation**
- 📊 Saves **unique detected plates** with confidence and frame index to Excel
- 🖼️ Saves **high-confidence plate images** for visual verification
- 📓 Prints detected plate numbers in Jupyter Notebook output
- ⚙️ No deep learning detection models (YOLO, Faster R-CNN, etc.)

---

## 🧠 Pipeline Overview

Video Frame
↓
Preprocessing (Grayscale + Blur)
↓
Edge Detection (Canny)
↓
Contour Detection
↓
Geometric Filtering (Aspect Ratio, Area)
↓
Plate Region Cropping
↓
OCR Preprocessing (Zoom, Contrast, Sharpen)
↓
EasyOCR Text Recognition
↓
Plate Validation & Normalization
↓
• Draw Bounding Box on Video
• Print Plate in Notebook
• Save Plate to Excel
• Save High-Confidence Plate Images



---

## 🧪 License Plate Validation Logic

Due to OCR limitations in detecting whitespace reliably, the system accepts **two valid formats**:

### ✅ Accepted Formats
- **7 alphanumeric characters** (no space)  
  Example: `AB12345`
- **8 characters with exactly one space at index 4**  
  Example: `AB12 345`

All other OCR outputs are rejected to reduce false positives.

---

## 📂 Project Outputs

After execution, the following files/folders are generated:




---

## 📊 Excel Output Format

The Excel file (`detected_plates.xlsx`) contains:

| Column Name | Description |
|------------|-------------|
| Plate      | Validated license plate number |
| Confidence | OCR confidence score |
| Frame      | First frame where plate was detected |

Duplicate plates are automatically removed, keeping the **highest-confidence detection**.

---

## 🖼️ High-Confidence Plate Images

Plate images are saved only when:
- OCR confidence ≥ **0.5**
- Plate has not been saved before

This keeps the dataset clean and GitHub-friendly.

---

## ⚙️ Technologies Used

- **Python 3**
- **OpenCV**
- **EasyOCR**
- **NumPy**
- **Pandas**
- **Matplotlib**
- **Jupyter Notebook**

---

## 🚀 How to Run

1. Place your input video in the project directory
2. Update the `VIDEO_PATH` variable in the notebook/script
3. Run all cells sequentially
4. Check generated outputs:
   - Processed video
   - Excel file
   - Cropped plate images

---

## ⚠️ Limitations

- Classical CV approach may miss:
  - Very small or distant plates
  - Heavily occluded or blurred plates
- OCR accuracy depends on:
  - Plate resolution
  - Motion blur
  - Lighting conditions
- No object tracking (each frame processed independently)

---

## 🔮 Future Improvements

- Temporal OCR aggregation (majority voting)
- Plate tracking across frames
- EU-specific regex validation
- Night-time glare suppression
- Deep learning–based plate detection (YOLO)

---

## 📜 Conclusion

This project demonstrates a **complete end-to-end ANPR pipeline** using **classical computer vision techniques**, producing clean, explainable outputs suitable for academic projects, demonstrations, and GitHub presentation.

---

### 👨‍💻 Author
Developed as part of a learning and experimentation project on computer vision–based automatic number plate recognition.
