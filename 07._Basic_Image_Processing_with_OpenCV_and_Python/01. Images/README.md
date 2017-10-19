# [ENGLISH] 01. Images

<img src="/images/Lenna.jpg" height="400">

In this section, we will use well known image of Lenna above for testing purpose. It will be easier if we make a folder for each practice project, then put our images and codes in it.

Displaying image in OpenCV can be done in just 9 lines of code. It can get simpler, but we included some lines so the code can be more "universal". The code is as shown below:
```python
import os, cv2
import numpy as np

_projectDirectory = os.path.dirname(__file__)
_images = os.path.join(_projectDirectory, "Lenna.jpg")

_img = cv2.imread(_images, cv2.IMREAD_UNCHANGED)
cv2.namedWindow("Image", cv2.WINDOW_AUTOSIZE)
cv2.imshow("Image", _img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```


```
python3
```

The command will brings up Python 3 interpreter. To check whether OpenCV is installed or not, type:

```python
import cv2
cv2.__version__
```

The last command should tell you the version of OpenCV.

Since we don't have a friendly text editor in Intel® Aero Platform for UAVs, we could make use of [WinSCP](https://winscp.net/eng/index.php). We can type our code on Windows based desktop/laptop then transfer the code to Intel® Aero Platform for UAVs. [add more step, making folder ]

