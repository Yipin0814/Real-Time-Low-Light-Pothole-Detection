# Real-Time Pothole Detection Under Low Light Conditions Using Lightweight Image Enhancement

An end-to-end Computer Vision and AIoT pipeline designed to detect road potholes accurately in nighttime and low-light driving conditions without sacrificing real-time speed.

## Overview
Standard object detectors struggle to spot road hazards at night due to poor lighting, shadows, and headlight glare. Heavy deep-learning image enhancers can brighten dark frames, but they often add too much processing delay for real-time road monitoring.

This project evaluates lightweight, fast image enhancement methods paired with a **YOLOv8n** object detector and a **feature-preserving alpha-blending** technique to recover nighttime visibility while keeping sharp pothole edges intact. Detections are logged into a simulated real-time AIoT pipeline and plotted onto an interactive road hazard map.

## Key Features
* **Lightweight Object Detection:** Built on **YOLOv8n** (PyTorch) for fast, edge-friendly inference.
* **Low-Light Enhancement Comparison:** Benchmarked **Baseline** (unenhanced), **CLAHE**, **AGCWD**, and **SSR** across **Day**, **Night**, and **Combined** test sets (6,108 total experimental images).
* **Feature-Preserving Alpha-Blending:** Tested blending ratios (`alpha = 0.5, 0.6, 0.7, 0.8`) on CLAHE and AGCWD to prevent over-enhancement and edge distortion.
* **Optimal Configuration:** Established **AGCWD with alpha-blending (alpha = 0.6)** as the best balance between nighttime brightness recovery, edge feature preservation, detection accuracy, and low latency.
* **Simulated Real-Time AIoT Deployment:** Streams dashcam video detections with location data to **Firebase Realtime Database** and visualizes pothole hotspots on an interactive **Python Folium** Web-GIS map.

## System Pipeline
1. **Input:** Dashcam video frames captured under daytime and nighttime road conditions.
2. **Preprocessing:** Lightweight low-light enhancement (`AGCWD`) combined with original frame alpha-blending (`alpha = 0.6`).
3. **Detection:** Real-time pothole localization and confidence scoring using `YOLOv8n`.
4. **Cloud Logging:** Automated upload of pothole detections, timestamps, and coordinates to Firebase Realtime Database.
5. **Visualization:** Interactive road hazard mapping using Python `Folium`.

## Tech Stack
* **Language:** Python
* **Deep Learning & Vision:** PyTorch, Ultralytics YOLOv8n, OpenCV
* **Data & Analysis:** NumPy, Pandas
* **Cloud & Mapping:** Firebase Realtime Database, Folium
* **Environment:** Google Colab, VS Code

## Evaluation Metrics
All models and enhancement pipelines were evaluated across Day, Night, and Combined conditions using:
* **Detection Quality:** Precision, Recall, mAP@50, and mAP@50-95
* **Real-Time Efficiency:** Total end-to-end processing latency (enhancement + inference)

## Sample Results
<img width="1462" height="478" alt="image" src="https://github.com/user-attachments/assets/0282a99e-2b68-4ba5-9bda-7f073ba2425f" />
<img width="1524" height="1022" alt="image" src="https://github.com/user-attachments/assets/05bc43de-69d3-43ad-818c-9c16668108c0" />
<img width="1207" height="597" alt="image" src="https://github.com/user-attachments/assets/45c4e154-2351-4c53-98df-fcf82c2f8c72" />


## Author
* **Wong Yi Pin** — B.Eng. / B.Sc. Artificial Intelligence Undergraduate, Xiamen University Malaysia (XMUM)
