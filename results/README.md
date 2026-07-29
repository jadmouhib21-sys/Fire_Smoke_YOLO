# Dataset and Google Drive Setup

## Public Roboflow Dataset

Dataset page:

**https://universe.roboflow.com/ashwath-oh952/fire-and-smoke-detection-o4uhv-onyzi**

Use:

- **Dataset version:** 1
- **Export format:** YOLOv8
- **Classes:** Fire and Smoke

Download the dataset automatically using the Roboflow API or download it manually and upload it to Google Drive.
---

## Option 1 — Download Automatically with the Roboflow API

### Step 1: Get a Roboflow API Key

1. Open the dataset link above.
2. Sign in to Roboflow.
3. Open your Roboflow account settings.
4. Copy your private API key.

Do not paste the API key directly into a public notebook or GitHub repository.

### Step 2: Add the Key to Google Colab Secrets

1. Open the notebook in Google Colab.
2. Select the **key icon** on the left side of Colab.
3. Add a new secret named:

   ```text
   ROBOFLOW_API_KEY
   ```

4. Paste the API key as the value.
5. Enable notebook access for that secret.

### Step 3: Enable Roboflow Downloading in the Notebook

Find this line:

```python
USE_ROBOFLOW = False
```

Change it to:

```python
USE_ROBOFLOW = True
```

The notebook will download Version 1 in YOLOv8 format to:

```text
/content/fire_smoke_dataset
```

The notebook uses:

```python
rf.workspace("ashwath-oh952") \
  .project("fire-and-smoke-detection-o4uhv-onyzi") \
  .version(1) \
  .download("yolov8", location="/content/fire_smoke_dataset")
```

### Optional: Copy the Downloaded Dataset to Google Drive

The `/content` directory on Colab is temporary. For saving the dataset, perform the following steps:
```python
from pathlib import Path
import shutil

LOCAL_DATASET = Path("/content/fire_smoke_dataset")
DRIVE_DATASET = Path("/content/drive/MyDrive/fire_smoke_dataset")

if DRIVE_DATASET.exists():
    shutil.rmtree(DRIVE_DATASET)

shutil.copytree(LOCAL_DATASET, DRIVE_DATASET)
print("Dataset saved to:", DRIVE_DATASET)
```

---

## Option 2 — Download Manually and Upload to Google Drive

1. Go to Roboflow’s dataset page.
2. Login if needed.
3. Choose Version 1.
4. Download/export the dataset in **YOLOv8** format.
5. Unzip the file.
6. Rename the unzipped directory: 

   ```text
   fire_smoke_dataset
   ```

7. Upload that entire folder to:

   ```text
   Google Drive/MyDrive/fire_smoke_dataset
   ```

The final structure must look like this:

```text
MyDrive/
└── fire_smoke_dataset/
    ├── data.yaml
    ├── train/
    │   ├── images/
    │   └── labels/
    ├── valid/
    │   ├── images/
    │   └── labels/
    └── test/
        ├── images/
        └── labels/
```

The notebook automatically looks for:

```text
/content/drive/MyDrive/fire_smoke_dataset/data.yaml
```

---

## Speeding up Training: Transfer Dataset from Drive to Local Colab Storage

Accessing Google Drive via YOLO may be inefficient when accessing many small files containing images and labels. After Drive is mounted, it is best to transfer your dataset to local Colab storage:

```python
from pathlib import Path
import shutil
import yaml

DRIVE_DATASET = Path("/content/drive/MyDrive/fire_smoke_dataset")
LOCAL_DATASET = Path("/content/fire_smoke_dataset")

if LOCAL_DATASET.exists():
    shutil.rmtree(LOCAL_DATASET)

shutil.copytree(DRIVE_DATASET, LOCAL_DATASET)

LOCAL_YAML = LOCAL_DATASET / "data.yaml"
config = yaml.safe_load(LOCAL_YAML.read_text(encoding="utf-8"))

config["path"] = str(LOCAL_DATASET)
config["train"] = "train/images"
config["val"] = "valid/images"
config["test"] = "test/images"

LOCAL_YAML.write_text(
    yaml.safe_dump(config, sort_keys=False),
    encoding="utf-8"
)

DATA_YAML = LOCAL_YAML
print("Using fast local dataset:", DATA_YAML)
```

Keep training results in Google Drive, but read the dataset from `/content/fire_smoke_dataset` for better performance.

---

## Test Images and Demonstration Setup

Create this Google Drive folder:

```text
MyDrive/fire_smoke_demo
```

Upload one or more unseen images or short videos to that folder. Supported examples include:

```text
fire_smoke_demo/
├── test.jpg
├── smoke_scene.jpg
├── small_fire.png
└── demo_video.mp4
```

The notebook prediction source is:

```python
DEMO_SOURCE = "/content/drive/MyDrive/fire_smoke_demo"
```

The entire folder is processed when the prediction cell runs.

### Required File for the Side-by-Side Comparison

The comparison cell expects an image named:

```text
test.jpg
```

Place it here:

```text
/content/drive/MyDrive/fire_smoke_demo/test.jpg
```

The predicted version will be written here:

```text
/content/drive/MyDrive/FireSmokeYOLO/predictions/demo/test.jpg
```

The comparison cell uses:

```python
original_path = Path(
    "/content/drive/MyDrive/fire_smoke_demo/test.jpg"
)

predicted_path = Path(
    "/content/drive/MyDrive/FireSmokeYOLO/predictions/demo/test.jpg"
)
```

If the filename of your image is different, then use this new filename in both locations.
### Important Test-Image Rule

Make sure you use images which have not been used for training the model. This way, the demonstration will be more relevant.
