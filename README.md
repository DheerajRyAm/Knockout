# Knockout

**Knockout** is a computer vision pipeline designed to analyze video footage of ball impacts in order to evaluate the effectiveness of new materials, such as safety equipment. The model tracks the motion of a ball across video frames, estimates its trajectory, and computes motion-based metrics including distance traveled, displacement, and real-world velocity estimations.

## Features

- 🎯 Ball detection and tracking using OpenCV's template matching and CSRT tracker.
- 📌 Automatic detection of stable reference anchors in video frames.
- 📐 Conversion of pixel motion to real-world measurements using camera parameters.
- 🧠 Generation of an averaged origin template for consistent spatial reference.
- 🎥 Visual annotations and video output for easy interpretation.
- 📊 Export metrics to CSV:
  - Total path traveled
  - Net displacement
  - True maximum distance in 3D space
  - Time elapsed

## Workflow

### 1. Input

- Two sets of `.mov` videos: e.g., `wht/` for *with hardhat* and `woht/` for *without hardhat*.
- Snapshot templates of the ball stored in `templates/`.

### 2. Preprocessing

- Each video is scanned to locate a stable anchor using optical flow.
- Reference patches are averaged into a template image for alignment.

### 3. Tracking

- Ball and origin are tracked across frames using CSRT tracker.
- Ball position is converted to 3D world coordinates using perspective math.

### 4. Output

- Annotated video saved to `tracked_videos/`.
- Summary metrics exported to `tracking_results.csv`.

## Output Format

`tracking_results.csv` contains:

| video_filename | category         | total_path_traveled | net_displacement | true_max_distance | time_elapsed |
|----------------|------------------|----------------------|------------------|-------------------|--------------|
| sample.mov     | with hardhat     | 124.6                | 85.3             | 4.3               | 2.5          |

# AI Assistance

Parts of the code and documentation for this project were developed with the help of AI tools, including ChatGPT, for tasks such as debugging, implementation guidance, and cleaning the code for when the implementation was complete. The majority of the implementation was written by me.

## ⚠️ Warning

Data is not included in this repository due to privacy concerns. If you wish to test the implementation, please refer to the associated research paper and replicate the experiment independently.

**Paper Status:** Under review



## Dependencies

- Python 3.x
- [OpenCV](https://opencv.org/)
- NumPy

Install them via:

```bash
pip install opencv-python numpy
