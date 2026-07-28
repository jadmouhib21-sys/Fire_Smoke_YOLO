# Fire and Smoke Detection Using YOLO11n

## Author

Jad Mouhib

## Project Description

This project develops a fire and smoke detection system using the YOLO11n object detection model. The model was trained in Google Colab using transfer learning on the Fire and Smoke Detection.v1i.yolov8 dataset from Roboflow Universe. The objective is to detect fire and smoke in images accurately while maintaining a lightweight model suitable for real-time applications.

## Dataset

**Fire and Smoke Detection.v1i.yolov8**

Source:
https://universe.roboflow.com/ashwath-oh952/fire-and-smoke-detection-o4uhv-onyzi

## Requirements

Install the required packages:

```bash
pip install -r requirements.txt
```

Main libraries:

- ultralytics
- torch
- opencv-python
- numpy
- matplotlib
- pandas
- roboflow

## Running the Project

1. Clone this repository.
2. Install the required dependencies.
3. Open the notebook (`Fire_Smoke_YOLO.ipynb`) in Google Colab or Jupyter Notebook.
4. Download the dataset from Roboflow.
5. Update the dataset path and Roboflow API key if needed.
6. Run all notebook cells to train or evaluate the model.

## Model

- YOLO11n
- Image size: 640 × 640
- Batch size: 16
- Maximum epochs: 50
- Early stopping after 10 epochs without improvement
- Training completed in 21 epochs

## Results

| Metric | Value |
|--------|------:|
| mAP@0.50 | 0.691 |
| mAP@0.50:0.95 | 0.371 |
| Fire mAP@0.50 | 0.642 |
| Smoke mAP@0.50 | 0.740 |

## Repository Structure

```
Fire_Smoke_YOLO/
├── Fire_Smoke_YOLO.ipynb
├── README.md
├── requirements.txt
├── data/
└── results/
```

## License

This project was developed for educational purposes as part of a computer vision course.
