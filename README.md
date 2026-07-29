# Fire and Smoke Detection Using YOLO11n

**Author:** Jad Mouhib  
**Course:** CAI2840C – Introduction to Computer Vision  
**Institution:** Miami Dade College  
**Project type:** Individual final research project

## Project Description

In this research, a pre-trained lightweight Ultralytics YOLO11n object detection model is assessed for the detection of fires and smoke from images. The model was trained through transfer learning using a public two-class dataset from Roboflow in Google Colab. The final experiment involved the use of up to 25 epochs, 640 × 640 image size, 16 batch size, 10 patience, and random seed of 42. There was no additional data augmentation experiment carried out.

## Research Question

To what extent can a lightweight pretrained YOLO11n model accurately detect and localize fire and smoke in public real-world images using transfer learning?

## Main Results

- Precision: approximately 0.736
- Recall: approximately 0.627
- mAP@0.50: 0.691
- mAP@0.50–0.95: 0.371
- Fire mAP@0.50: 0.642
- Smoke mAP@0.50: 0.740

These results apply to an educational prototype and not to a tested fire alarm system.

## Dataset 

The dataset can be accessed publicly through Roboflow Universe at the following link:

https://universe.roboflow.com/ashwath-oh952/fire-and-smoke-detection-o4uhv-onyzi

Please use the version 1 of the above dataset and export it in the YOLOv8 format. There are two classes in the dataset – Fire and Smoke.

The entire image dataset cannot be uploaded to this GitHub repository because it has thousands of images and corresponding labels. All the necessary details have been provided in data/README.md file.

## Google Drive Folder Setup
Before running the notebook, create this structure in Google Drive:
```text
MyDrive/
├── fire_smoke_dataset/
│   ├── data.yaml
│   ├── train/
│   │   ├── images/
│   │   └── labels/
│   ├── valid/
│   │   ├── images/
│   │   └── labels/
│   └── test/
│       ├── images/
│       └── labels/
├── fire_smoke_demo/
│   └── test.jpg
└── FireSmokeYOLO/

```- `fire_smoke_dataset/` holds the downloaded Roboflow dataset.
- `fire_smoke_demo/`  holds new/unseen images or videos used to demonstrate.
- `FireSmokeYOLO/` folder is generated automatically by the notebook and holds all training outputs such as weights and predictions.


**## Test Image Setup**

1. In Google Drive, create a folder named:

   ```text
   MyDrive/fire_smoke_demo
   ```

2. Upload at least one untested fire or smoke picture.
3. Label one image "test.jpg" so that the comparison table will work without changes.
4. The notebook will load the original image from: 

   ```text
   /content/drive/MyDrive/fire_smoke_demo/test.jpg
   ```

5. After prediction, the annotated image is saved to:

   ```text
   /content/drive/MyDrive/FireSmokeYOLO/predictions/demo/test.jpg
   ```

It is also possible to put more than one file type such as `.jpg`, `.jpeg`, `.png`, or short video files inside `fire_smoke_demo`.  


## How to Run the Project

1. Open `notebooks/Fire_Smoke_YOLO_Colab_Final_25_Epochs.ipynb` in Google Colab.
2. In Colab, select **Runtime → Change runtime type → T4 GPU** when available.
3. Open the Colab **Secrets** panel.
4. Create a secret named `ROBOFLOW_API_KEY`.
5. Paste your Roboflow API key into that secret and enable notebook access.
6. Run the notebook cells from top to bottom.
7. The notebook installs the required packages, downloads the dataset, trains YOLO11n, validates the best checkpoint, creates prediction examples, and exports results to Google Drive.

## Dependencies

List of dependencies of python are given in `requirements.txt`. Google colab provides several scientific python packages along with PyTorch and GPU access.  


## Reproducibility Notes

- Model checkpoint: `yolo11n.pt`
- Maximum epochs: 25
- Image size: 640
- Batch size: 16
- Early-stopping patience: 10
- Random seed: 42
- Custom augmentation experiment: not performed

## Safety and Limitations

This algorithm was tested on one publicly available data set and with one experiment. The efficiency of the algorithm can reduce if the working conditions are hard because of lighting, fog, steam, reflection, occlusion, small fire, thin smoke, and others. This algorithm can't be used instead of professional fire detectors.   
