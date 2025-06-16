

-----

# 🛰️ Image Stitching: Mars Rover Panorama

**Overview**

This project creates a seamless panoramic image from two overlapping photos taken by a Mars Rover. Using fundamental computer vision techniques in **MATLAB**, it aligns the images through feature matching, calculates the necessary geometric transformation, and blends them into a single, wide-angle view of the Martian surface. This demonstrates a practical application of image registration and stitching on real-world planetary exploration data.

-----

### 💡 Features

  * Stitches multiple Mars Rover images into a single panoramic view.
  * Uses **feature-based image registration** (SURF features) to automatically align images.
  * Computes a `projective` geometric transformation to accurately map one image onto another.
  * Dynamically creates a panorama canvas large enough to contain the full scene.
  * Blends warped images using `vision.AlphaBlender` for a smooth, seamless result.
  * Provides visualizations for key steps, including matched features and the final stitched image.

-----

### 🧱 Pipeline Structure

The image stitching process is executed within the `ImageStitching.mlx` live script and is broken down into four main stages:

1.  **Load Images**
      * The fixed (reference) and moving (to be aligned) images are loaded from disk.
2.  **Register Images**
      * The local helper function, `registerMarsImages`, identifies corresponding feature points in both images.
      * It uses these matches to calculate the geometric transformation that aligns the `movingImg` with the `fixedImg`.
3.  **Initialize Panorama Canvas**
      * The spatial limits required for the final panorama are calculated based on the dimensions and transformation of both images.
      * A new, empty image canvas (`panorama`) is created with the precise dimensions needed to hold the combined view without cropping.
4.  **Create the Panorama**
      * Both images are warped into the common panorama coordinate system using `imwarp`.
      * A `vision.AlphaBlender` is used to combine the two warped images onto the final canvas, creating the final stitched panorama.

-----

### 📂 File Structure

```
📁 ImageStitchingUsingSURFFeatureMatching/
├── 📄 ImageStitching.mlx                         # Main MATLAB Live Script with all code
├── 📄 sol_..._F0921230NCAM00259M_.JPG           # Input image 1 (fixed)
├── 📄 sol_..._F0921230NCAM00259M_.JPG           # Input image 2 (moving)
└── 📄 mars_panorama.jpg                          # Final stitched output image
```

*Note: The `registerMarsImages` function is included as a local function within the `ImageStitching.mlx` file.*

-----

### 📊 Input Data Schema

The project uses two overlapping images captured by the Mars Rover's navigation camera.

  * **`fixedImg`**: The reference image that remains stationary.
  * **`movingImg`**: The image that is transformed to align with the `fixedImg`.

Both inputs are standard `.JPG` image files.

-----

### 🛰️ Data Source & Attribution

The images used in this project are from the **Mars Curiosity Rover**.

**Courtesy NASA/JPL-Caltech**

**Original Source:** [NASA Mars Curiosity Rover Raw Images](https://mars.nasa.gov/msl/multimedia/raw-images/)

-----

### 🔧 Requirements

  * **MATLAB** (R2022b or newer recommended)
  * **Image Processing Toolbox™**
  * **Computer Vision Toolbox™**

-----

### ⚙️ Installation

Project dependencies are managed through MATLAB Toolboxes. Ensure you have the required toolboxes installed by running `ver('images')` and `ver('vision')` in the MATLAB Command Window. If a toolbox is missing, install it using the **Add-On Explorer**.

-----

### 🛠️ Setup Instructions

1.  Place the `ImageStitching.mlx` Live Script and the two input `.JPG` images in the same directory.
2.  Ensure this directory is set as the current folder in MATLAB.

-----

### 🚀 Usage

1.  Open the `ImageStitching.mlx` file in MATLAB.
2.  Click the **Run** button in the Live Editor tab to execute the entire script.
3.  The script will display figures showing the process:
      * The original two images side-by-side.
      * The matched feature points between the two images.
      * The final, stitched panoramic image.
4.  The output panorama will be saved to the project directory as `mars_panorama.jpg`.

-----

### 👤 Author

**Kirubhakaran Meenakshi Sundaram**

📧 Email: km1079@g.rit.edu  
💼 LinkedIn: [https://www.linkedin.com/in/kirubhakaranm/](https://www.linkedin.com/in/kirubhakaranm/)

-----

### 📚 Additional Resources

  * [Create a Panorama Using Feature-Based Image Registration](https://www.google.com/search?q=https://www.mathworks.com/help/vision/ug/create-a-panorama-using-feature-based-image-registration.html) - Official MATLAB example that covers the core concepts of this project.
  * [Feature Based Image Registration](https://www.google.com/search?q=https://www.mathworks.com/help/vision/ug/feature-based-image-registration.html) - An overview of the feature detection and matching workflow.
  * [detectSURFFeatures function](https://www.mathworks.com/help/vision/ref/detectsurffeatures.html) - Documentation for the SURF feature detector.
  * [matchFeatures function](https://www.mathworks.com/help/vision/ref/matchfeatures.html) - Documentation for matching feature vectors.
  * [estimateGeometricTransform2D function](https://www.mathworks.com/help/vision/ref/estimategeometrictransform2d.html) - Documentation for the function used to find the transformation.
  * [imwarp function](https://www.mathworks.com/help/images/ref/imwarp.html) - Documentation for warping images based on a geometric transform.