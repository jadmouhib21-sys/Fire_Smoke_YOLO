# Fire and Smoke Detection Using YOLO11n

**Author:** Jad Mouhib  
**Course:** CAI2840C – Introduction to Computer Vision  
**Institution:** Miami Dade College  
**Project type:** Individual final research project

## Project Description

This project evaluates a lightweight pretrained Ultralytics YOLO11n object detector for detecting and localizing fire and smoke in images. The model was fine-tuned in Google Colab using transfer learning on a public two-class Roboflow dataset. The final experiment used a maximum of 25 epochs, an image size of 640 × 640, a batch size of 16, patience of 10, and a random seed of 42. No separate custom data-augmentation experiment was performed.

## Research Question

To what extent can a lightweight pretrained YOLO11n model accurately detect and localize fire and smoke in public real-world images using transfer learning?

## Main Results

- Precision: approximately 0.736
- Recall: approximately 0.627
- mAP@0.50: 0.691
- mAP@0.50–0.95: 0.371
- Fire mAP@0.50: 0.642
- Smoke mAP@0.50: 0.740

These results describe an educational prototype and not a certified fire-alarm or life-safety system.

## Repository Structure

```text
Fire_Smoke_YOLO/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── Fire_Smoke_YOLO_Colab_Final_25_Epochs.ipynb
├── data/
│   └── README.md
└── results/
    └── README.md
```

## How to Run the Project

1. Open `notebooks/Fire_Smoke_YOLO_Colab_Final_25_Epochs.ipynb` in Google Colab.
2. In Colab, select **Runtime → Change runtime type → T4 GPU** when available.
3. Open the Colab **Secrets** panel.
4. Create a secret named `ROBOFLOW_API_KEY`.
5. Paste your Roboflow API key into that secret and enable notebook access.
6. Run the notebook cells from top to bottom.
7. The notebook installs the required packages, downloads the dataset, trains YOLO11n, validates the best checkpoint, creates prediction examples, and exports results to Google Drive.

## Dependencies

The main Python dependencies are listed in `requirements.txt`. Google Colab already includes several scientific Python packages and typically provides PyTorch and GPU support.

## Dataset

The image dataset is not stored directly in this repository because of repository size and dataset-distribution considerations. See `data/README.md` for the exact dataset source and download procedure.

## Reproducibility Notes

- Model checkpoint: `yolo11n.pt`
- Maximum epochs: 25
- Image size: 640
- Batch size: 16
- Early-stopping patience: 10
- Random seed: 42
- Custom augmentation experiment: not performed

## Safety and Limitations

This model was evaluated on one public dataset and one training run. Performance may decrease under difficult lighting, fog, steam, reflections, occlusion, small flames, faint smoke, or other conditions outside the training distribution. It should not be used as a replacement for certified fire-detection systems.
