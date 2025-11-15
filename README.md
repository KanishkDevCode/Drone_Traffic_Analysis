# 🚁 Drone-Based Multi-Vehicle Detection & Traffic Flow Analysis

An AI-powered system for automatic **vehicle detection**, **multi-object tracking**, and **lane-wise traffic flow analysis** using aerial drone videos.  
The pipeline uses **YOLOv8 + DeepSORT** along with **automatic lane extraction**, producing a fully visualized output video and Excel traffic report — without any manual lane marking.

---

## 📌 Features
- Automatic lane detection (no manual drawing)
- YOLOv8 vehicle detection
- DeepSORT tracking with unique vehicle IDs
- Lane-wise vehicle assignment
- Direction estimation (straight / right-turn)
- Debug output video with overlays (lanes + bounding boxes + IDs)
- Final Excel report with lane-wise traffic counts

---

## 🛠️ Tech Stack
- Python  
- YOLOv8 (Ultralytics)  
- DeepSORT  
- OpenCV  
- Shapely  
- Pandas  

---

---

## 🚀 How It Works
1. Upload any drone traffic video.  
2. Lanes are extracted automatically → `lanes.json`.  
3. YOLO detects vehicles frame-by-frame.  
4. DeepSORT tracks each vehicle with a unique ID.  
5. Vehicles get mapped to lanes + direction classification.  
6. Output:
   - `debug_output.mp4` (video with overlays)
   - `traffic_counts.xlsx` (final count)
   - `tracks_output.csv` (full movement log)

---

## ▶️ Usage (Google Colab)
### 1️⃣ Upload video
```python
from google.colab import files
uploaded = files.upload()
video_path = next(iter(uploaded.keys()))
````

### 2️⃣ Auto-generate lane polygons

```python
lanes_file = auto_generate_lanes(video_path)
```

### 3️⃣ Run detection + tracking + counting

```python
run_analysis(video_path, lanes_file, "results")
```

---

## 📊 Example Output Summary

| Lane | Straight | Right Turn |
| ---- | -------- | ---------- |
| 1    | 24       | 6          |
| 2    | 31       | 3          |
| 3    | 19       | 8          |
| 4    | 27       | 5          |

---

## 🔮 Future Improvements

* Left-turn detection
* Per-class (car/bike/bus/auto) traffic analysis
* GIS exporting for QGIS
* Drone-specific lane segmentation with RIT++
