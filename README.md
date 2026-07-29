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

## Dataset

Image data set is not included in this repository due to some reasons related to size and distribution of the data set. For more details, see `data/README.md`.

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
