# Autonomous-Vehicle-AV-Lane-Line-Detection
Autonomous Vehicle (AV) Lane Line Detection using Computer Vision: Udacity Self-Driving Car Dataset

Main Objective of the Project - To develop a machine-learning (ML) that will instantly identify lane lines. This will be implemented with Python (on JupyterLab) and the OpenCV library, utilising computer vision techniques. The application context is the white and yellow markings on either side of the road for the detection of lane lines. 

**Process Objectives**
	Put together a pipeline to detect the line segments in the image, 
	Extrapolate the lines and draw them onto the image for display;
	Test the pipeline on a video stream.
	To help reduce the time complexity involved in gathering real-world datasets to create lane-detecting systems for autonomous vehicles (AVs).

The implementation tools will be color selection, region of interest selection, grayscaling, Gaussian smoothing, Canny Edge Detection, and Hough Transform line detection on the Udacity self-driving car dataset.


**Process Flow Steps**
Steps involved in the Process flow: 
	Capture video as input;
	Convert them into images or frames;
	Choose image (s) as input entries;
	Use grayscaling to convert images into grey color;
	Use Gaussian smoothing to reduce noise or disturbance;
	Use Canny Edge Detection to detect edges;
	Use Region of Interest (ROI) selection to mask unwanted regions or areas;
	Lastly, Hough Transformation ignores shapes or circles. The primary basis for lane detection is the frequency of traffic accidents and the need to provide basic lanes for all vehicles to ensure a safe journey. The vision model involves a good prototype with algorithms that produce outcomes that are precise and effective.


Figure 1: Computer Vision (CV)-Based Lane Detection Approach (Source: Analyst Concept)
![image](https://github.com/user-attachments/assets/01eeacc5-e026-4e37-bd37-a88d2fbc4e4c)


**Table 1. Experimental Setup**
| Technologies  | Configuration |
| ------------- | ------------- |
| Operating system | Windows 11 Pro 64-bit  |
| RAM  | Windows 11 Pro 64-bit  |
| CPU | 11th Gen Intel(R) Core (TM) i5-1135G7 @ 2.40GHz   2.42 GHz CPU  |
| Python version  | 3.12.4  |
| Code Environment  | JupyterLab  |
| OpenCV version  | 4.10.0  |
| Libraries  | Numpy and Matplotlib (pyplot and image)  |



**Methodology 
Background**
A Charge-coupled device (CCD) camera mounted on the front-view mirror captures the road's topography. To make things easier and guarantee that the horizon of the image is aligned with the x-axis, the baseline is anticipated to be lined up horizontally. If not, the image captured by the camera can be modified using the calibration data. The pair of edge lines that make up each lane border marking are frequently roughly rectangular shapes. It was intended for this study that the algorithm's input would be an RGB image with apex dimensions of 480x290. 

As a result, the algorithm tries to convert the image to grayscale to shorten processing time (Kuo et al. 2019). Second, when noise is present, it will be challenging to accurately distinguish edges in the image.

Next, the line detector receives the image and generates a segment of the left and right lane border. The anticipated intersection point of these two-line segments was determined to be the horizon. The lane boundary scan was carried out using the data from the edge picture that was acquired by the Hough transform (Lopez et al. 2010). The scan yielded a list of spots on the left and right sides. Eventually, two hyperbolas fit these data values and served as the representation of the lane borders (Kim, 2006).

This section covers evaluation meters, methods, upgrades, and tools and technology. Table 1 shows the single view depicting the lane detection method. The investigator provides more information below.


**Tools and Technologies**
Python version 3.12.4 was used for implementation, given that it is the most recent stable version. JupyterLab development environment was used to process the data (images and videos) and run the code. The integration of Python 3.12.4 and JupyterLab gave the investigator a facility of code readability and the capability to provide core data type concepts such as colour selection criteria for red, green, and blue thresholds. The other tools and technologies used are Numpy, Matplotlib, and OpenCV.

NumPy is a Python library used to calculate numerical quantities. This provides sophisticated array and matrix manipulation features. It has various routines for performing mathematical computations on arrays and creating random numbers. NumPy is a general-purpose toolkit for manipulating arrays. It provides an array of dimensional objects with remarkable speed as well as the ability to interact with these arrays. It is the primary Python package for scientific computing. The application is open-source for all interfaces.

Matplotlib is a popular Python data visualisation library, frequently used for building static, dynamic, and animated visualisations.

OpenCV is a free, open-source software library for computer vision (CV) and machine learning (ML). OpenCV was established to provide a standardised framework for applications that use computer vision. The collection contains around 2,500 optimised algorithms, which include a variety of conventional and innovative CV and ML methods.

These algorithms can be used to recognise faces, identify objects, categorise human behaviours in films, follow camera movements, track moving objects, extract 3D models of objects, create clouds of 3D points from stereo cameras, fill together images to generate a high-resolution image of the entire scene, detect related images in an image database, fix eyes that are red in flash photos, track eye movement, identify scenery, and create markers for augmented reality overlays.


**Image Processing**
a. Camera Calibration
Many cameras suffer from lens distortion. Distortion, also known as camera sectioning, refers to the process of determining the characteristics of a lens's image sensor, as seen in Figure 2. In this investigation, camera calibration was employed to solve this issue (Kanan and Cottrell, 2012).

b. Grayscale
In the first phase, a greyscale filter is utilised to put together the information for Canny edge detection. This stage calculates the magnitude (norm) of the gradients for each pixel using Sobel determinants in the x and y directions. Using the Canny edges for every single channel might slow down the image processing method. Figure 3 is one of the greyscale images from the test data. For further information on the greyscale technique of averaging the values in the green, blue, and red channels, see (Kanan and Cottrell, 2012).

c. Noise Removal and optimised region masking
Because the primary image processing elements utilised for line detection are Canny edges and the Hough transform, mathematical procedures such as derivatives are required. Such operations increased sensitivity to picture noise. To avoid this problem, the researcher must first address the noise issue before moving on with lane detection. In this, noise was removed using a basic Gaussian filter. Because the procedure is sensitive and might result in image blurring and data loss, choosing the appropriate window size for the Gaussian filter to operate is also critical. Experiments revealed that the dimension of the filter known as the Gaussian differs between cameras. To address this problem, the investigator employed a larger size kernel of 5 to smoothen and average out over a large area, as an optimisation method (Monfared and Rada, 2022).

The kernel sizes are 3 x 3, 5 × 5, 9 × 9, 15 × 15, and 20 × 20. Two recommendations were made as alternatives for the initial camera setup. The first choice is for a scenario in which test data and correct detection of lines are provided, but the second scenario lacks such data. In this regard, the investigator worked on creating a completely automated approach (Monfared and Rada, 2022). Fig. 3 depicts the outcome of the Gaussian filter, which was previously used in this study, on one of the processed images. 

		





