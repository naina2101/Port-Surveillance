# Port-Surveillance
EdgeAI-enabled Port Surveillance
🚧 This project is an early-stage proof-of-concept. 🚧

The code is experimental and designed to demonstrate the core detection logic. It is not yet ready for production use.

This repository contains the foundational work for an intelligent port surveillance system. The goal is to build a solution using an Edge AI architecture for real-time monitoring.

Currently, the project's core function is to process individual images (photos) to detect and classify vessels. This capability serves as the essential building block for analyzing video, which can be done by first extracting frames from a video file.

!
(A good image here would show a single photo with your model's bounding boxes drawn on it.)

## The Vision: The "Why" Behind the Project
The architecture is designed with Edge AI as the guiding principle. The long-term vision is to create a system that is:

⚡ Real-Time: To process live video feeds on-site for instantaneous alerts.

📉 Bandwidth-Efficient: To analyze video locally and transmit only minimal data.

🔒 Private & Secure: To keep all sensitive video footage on-premise.

🌐 Reliable: To function continuously, even without a stable internet connection.

## Current State & Capabilities
As a work in progress, the system's core script can:

Analyze Static Images: Process single image files (.jpg, .png, etc.) to identify vessels.

Detect & Classify Objects: Uses a YOLOv8 model to draw bounding boxes around vessels in a supplied photo.

Provide a Foundation for Tracking: The detection logic provides the per-frame data (bounding boxes and coordinates) necessary for video tracking algorithms. By running this script on a sequence of extracted video frames, one can build a tracking and event-logging system.

## Proposed Architecture
The current pipeline is simple, focused on single-image analysis.

Core Logic:
$$\text{Image File} \rightarrow \text{Detection (YOLOv8)} \rightarrow \text{Annotated Image Output}$$

Application to Video (Conceptual Workflow):
$$\text{Video} \rightarrow \text{Frame Extraction} \rightarrow \text{Run Detection on each Frame} \rightarrow \text{Compile Frames into Video}$$

## Tech Stack
Language: Python

Core Libraries: OpenCV, PyTorch, Pillow

Object Detection: YOLOv8

Future Hardware Targets: NVIDIA Jetson Series, Raspberry Pi, Google Coral

## Getting Started
Clone the repository:

Bash

git clone https://github.com/your-username/EdgeAI-enabled-Port-surveillance.git
cd EdgeAI-enabled-Port-surveillance
Install dependencies (preferably in a virtual environment):

Bash

pip install -r requirements.txt

Usage
Run the detection script on a single image. The output with bounding boxes will be saved in the runs/detect/ directory.

Bash

# Run detection on a single photo
python main.py --source "/path/to/your/port_image.jpg"
To process a video: you must first extract its frames into a directory. You can use a tool like FFmpeg for this:

Bash

# Example: Extracts 1 frame per second into a folder named 'frames'
mkdir frames
ffmpeg -i your_video.mp4 -vf fps=1 frames/frame_%04d.png
Then, you can run the detection on the directory of frames:

Bash

python main.py --source "frames/"
## Roadmap & How to Contribute
We welcome contributions! This project is in its early stages, and there is a lot to do.

Immediate Goals
[ ] Video Processing Wrapper: Create a script to automate the frame extraction, detection, and re-compilation into an output video.

[ ] Real-Time Stream Support: Integrate a module to handle live feeds from RTSP or webcams.

[ ] Performance Optimization: Begin testing model optimizations (e.g., TensorRT) for edge hardware.

[ ] Documentation: Add more code comments and expand on the setup instructions.

To contribute, please fork the repo, create a feature branch, and submit a pull request!
