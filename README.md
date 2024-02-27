# speed estimation


## 💻 install

- clone repository and navigate to example directory

  ```bash
  cd /speed_estimation
  ```

- setup python environment and activate it [optional]

  ```bash
  python3.10 -m venv venv
  source venv/bin/activate
  ```

- install required dependencies

  ```bash
  pip install -r requirements.txt
  ```

- download `vehicles.mp4` file

  ```bash
  python3.10 video_downloader.py
  ```

## 🛠️ script arguments

- `--roboflow_api_key` (optional): The API key for Roboflow services. If not provided
  directly, the script tries to fetch it from the `ROBOFLOW_API_KEY` environment
  variable. Follow [this guide](https://docs.roboflow.com/api-reference/authentication#retrieve-an-api-key)
  to acquire your `API KEY`.
- `--model_id` (optional): Designates the Roboflow model ID to be used. The default
  value is `"yolov8x-1280"`.

- `--source_weights_path`: Required. Specifies the path to the YOLO model's weights
  file, which is essential for the object detection process. This file contains the
  data that the model uses to identify objects in the video.
- `--source_video_path`: Required. The path to the source video file that will be
  analyzed. This is the input video on which traffic flow analysis will be performed.
- `--target_video_path`: The path to save the output video with
  annotations. If not specified, the processed video will be displayed in real-time
  without being saved.
- `--confidence_threshold` (optional): Sets the confidence threshold for the YOLO
  model to filter detections. Default is `0.3`. This determines how confident the
  model should be to recognize an object in the video.
- `--iou_threshold` (optional): Specifies the IOU (Intersection Over Union) threshold
  for the model. Default is 0.7. This value is used to manage object detection
  accuracy, particularly in distinguishing between different objects.

## ⚙️ run

- yolo-nas

  ```bash
    python yolo_nas_example.py \
    --source_video_path data/vehicles.mp4 \
    --target_video_path data/vehicles-result-yolo.mp4 \
    --confidence_threshold 0.3 \
    --iou_threshold 0.5
  ```

- inference

  ```bash
    python inference_example.py \
    --roboflow_api_key <ROBOFLOW API KEY> \
    --source_video_path data/vehicles.mp4 \
    --target_video_path data/vehicles-result.mp4 \
    --confidence_threshold 0.3 \
    --iou_threshold 0.5
  ```

- ultralytics

  ```bash
    python ultralytics_example.py \
    --source_video_path data/vehicles.mp4 \
    --target_video_path data/vehicles-result-ultra.mp4 \
    --confidence_threshold 0.3 \
    --iou_threshold 0.5
  ```