# Dataset Instructions

The full image dataset is not included in this repository because it contains many image and label files and may make the repository unnecessarily large.

## Dataset Used

- Dataset name: `Fire and Smoke Detection.v1i.yolov8`
- Source platform: Roboflow Universe
- Workspace: `ashwath-oh952`
- Project: `fire-and-smoke-detection-o4uhv-onyzi`
- Version: `1`
- Export format: `yolov8`
- Classes: `Fire` and `Smoke`

## Download Procedure

The final notebook downloads the dataset automatically with the Roboflow Python package. Before running the notebook:

1. Create or sign in to a Roboflow account.
2. Obtain a Roboflow API key.
3. In Google Colab, open the **Secrets** panel.
4. Add the key under the name `ROBOFLOW_API_KEY`.
5. Enable notebook access for the secret.
6. Run the dataset-download cell.

The notebook accesses the dataset with the following project identifiers:

```python
rf.workspace("ashwath-oh952") \
  .project("fire-and-smoke-detection-o4uhv-onyzi") \
  .version(1)
```

Do not commit an API key, password, access token, or other credential to this public repository.
