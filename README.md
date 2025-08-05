⚽ TactiTrack
The intelligent toolkit for advanced sports tracking and analytics
Convert raw match footage into structured tracking data. Unlock tactical insights. Enhance performance.

🚀 Introduction
TactiTrack is a modular, high-performance framework for sports video analytics. Designed for both professionals and enthusiasts, it transforms raw video into actionable insights through robust tracking, calibration, and data wrangling tools.

We're starting with soccer, with support for more sports coming soon!

🔧 Features
🧠 Core Capabilities
High-Performance Tracking Algorithms:

SORT

DeepSORT

ByteTrack

TeamTrack (custom implementation)

Flexible Model Integration:

Plug-and-play support for detection and re-identification (ReID) models

Pre-integrated with:

YOLOv8 for detection

Torch-ReID for appearance matching

🧭 2D Pitch Calibration
Convert bounding box coordinates to 2D pitch locations for spatial analytics.

📊 Structured Output with DataFrames
BoundingBoxDataFrame – Encodes bounding boxes with team/player info

CoordinatesDataFrame – Stores calibrated 2D positions

Multi-indexed by Frame, Team, and Player ID

📦 Installation
Install the latest version from PyPI:

bash
Copy
Edit
pip install TactiTrack
⚠️ Note: TactiTrack is in active development. Expect frequent updates and new features.

🧪 Quick Start Example
python
Copy
Edit
import tactitrack as tt
from tactitrack.mot import SORTTracker

# Load your video and models
cam = tt.Camera("path_to_video.mp4")
det_model = tt.detection_model.load("YOLOv8x", imgsz=640)
motion_model = tt.motion_model.load("KalmanFilter", dt=1/30, process_noise=10000, measurement_noise=10)

# Run tracking
tracker = SORTTracker(detection_model=det_model, motion_model=motion_model)
tracker.track(cam[:100])  # Analyze the first 100 frames

# Export tracking results
res = tracker.to_bbdf()
res.visualize_frames(cam.video_path, "assets/tracking_results.mp4")
📈 Output Format
The result is a BoundingBoxDataFrame, a Pandas DataFrame with hierarchical indices:

Frame ID

Team ID

Player ID
Includes bounding box size, position, confidence, and more.

📚 Documentation
📌 Getting Started – Install and run your first tracker

📘 User Guide – Full walkthrough of tracking and analysis tools

🧠 Component Reference – API documentation for each module

🛣️ Roadmap
✅ YOLOv8 + KalmanFilter support

🔍 Event detection: passes, shots, goals

🔄 Unified DataFrame for trajectories + event metadata

📤 Export to common analytics formats (CSV, JSON, Metrica)

🏀 Multi-sport support (basketball, hockey, etc.)

🤝 Contributing
We welcome all contributions! See our Contributing Guide to get started.



📬 Support
For bugs, ideas, or collaborations — please open an issue or submit a pull request.
