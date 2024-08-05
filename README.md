# Object Tracking using SIFT Features in OpenCV

This repository provides a basic implementation of object tracking using Scale-Invariant Feature Transform (SIFT) features in OpenCV with Python. SIFT is a powerful feature detection algorithm that identifies distinctive points in images that are invariant to scale, rotation, and illumination changes.

## Dependencies
- OpenCV (`cv2`)
- NumPy (`numpy`)

You can install these libraries using pip:

```bash
pip install opencv-python numpy
```

## Code Overview
 1. **Initialization:**
   - Load the video using `cv2.VideoCapture()`.
   - Read the first frame and display it to the user.
   - Initialize variables for storing the bounding box coordinates of the object to track.

2. **Bounding Box Selection:**
   - Use mouse events (`cv2.setMouseCallback()`) to allow the user to draw a rectangle around the object of interest in the first frame.
   - The coordinates of the rectangle are stored in `x_min`, `y_min`, `x_max`, and `y_max`.

3. **Feature Extraction (Target Object):**
   - Extract the region of interest (ROI) from the first frame using the bounding box coordinates.
   - Convert the ROI to grayscale.
   - Create a SIFT object (`cv2.SIFT_create()`)
   - Detect and compute SIFT keypoints and descriptors from the grayscale ROI.

4. **Object Tracking:**
   - Loop through the remaining frames of the video.
   - Convert each frame to grayscale.
   - Detect and compute SIFT keypoints and descriptors for the current frame.
   - Use a Brute-Force Matcher (`cv2.BFMatcher()`) to find the best matches between descriptors from the target object (ROI) and the current frame.
   - For each match:
      - Retrieve the corresponding keypoints from both the target object and the current frame.
      - Draw a circle on the current frame at the location of the matched keypoint (from the current frame).
   - Display the processed frame.

5. **Termination:**
   - Break the loop and close all windows when the 'Esc' key is pressed.


## How to Run the Code
1. Replace `"path/to/your/video.mp4"` with the actual path to your video file.
2. Run the script. 
3. Click and drag your mouse on the first frame of the video to select the object you want to track. 
4. Press the middle mouse button to reset the selected region if needed.
5. Press 'Esc' to exit the program. 
