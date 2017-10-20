# [ENGLISH] 07. Basic Image Processing with OpenCV and Python

<img src="/images/OpenCV_and_Python.png" height="400">

As of 1.5+ firmware, Intel® Aero Platform for UAVs comes with OpenCV and Python 3 by default. OpenCV (Open Source Computer Vision) is an image processing library which is often found in researches and commercial products. Its robustness and ease of use contribute to its popularity for being choosen in general applications involving image processing. As of Python, it is one of the most popular scripting languages because it is heavily focused on human-readable aspect. It will make more sense to code in Python than in C/C++ from a beginner's point of view. With those backgrounds, we can make a guess that image processing utilizing both of them should be easy. In this part we will explore some general topics in image processing using OpenCV and Python. The available topics are arranged as below:
* [01. Images]
* [02. Histogram]
* [03. Binary Vision]
* [04. Geometric Transformation]
* [05. Edges]
* [06. Features]
* [07. Recognition]
* [08. Features]
* [09. Video]

Before we start, let us make sure that we have both OpenCV and Python 3 installed in our Intel® Aero Platform for UAVs. Connect HDMI monitor and keyboard to Intel® Aero Platform for UAVs then boot it up. After the terminal opened, type:
```
python3
```

The command above will brings up the Python 3 interpreter, indicated with ```>>>``` sign. After that, Type:
```python
import cv2
cv2.__version__
```
The first line is to include the OpenCV package to our project. The second line will prints out the OpenCV package version. If there are no errors, then we are ready.

Note: Since Intel® Aero Platform for UAVs doesn't include any friendly text editor, it will be easier for us to type our code on desktop/laptop. We can make use of [WinSCP](https://winscp.net/eng/index.php) to transfer our code to Intel® Aero Platform for UAVs.
