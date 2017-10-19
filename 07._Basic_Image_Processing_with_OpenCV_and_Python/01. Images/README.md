# [ENGLISH] 01. Images

<img src="/images/Lenna.jpg" height="400">

In this section, we will use well known image of Lenna above for testing purpose. It will be easier if we make a folder for each practice project, then put our images and codes in it.

Displaying image in OpenCV can be done in just 9 lines of code. It can get simpler, but we included some lines so the code can be more _universal_. The code is as shown below:
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

The simple explanation for code above is as below:
 * ```import os, cv2``` and ```import numpy as np``` will include the packages needed in our project.
 * ```_projectDirectory = os.path.dirname(__file__)``` is for getting the code's path, then store it in ```_projectDirectory```.
 * ```_images = os.path.join(_projectDirectory, "Lenna.jpg")``` since we put the image in the same directory as the code, we can add the image's name after the path. But since Windows use ```\``` and Linux use ```/``` as separator, it will be easier for us to let Python decides which is the suitable separator. Therefore we use ```os.path.join```.
 * ```cv2.namedWindow("Image", cv2.WINDOW_AUTOSIZE)``` is to create an empty window named ```Image```.
 * ```cv2.imshow("Image", _img)``` is to display the image on the window we created before.
 * ```cv2.waitKey(0)``` is needed so that the code will wait for an event first, which is waiting for a keypress, instead of executing next code.
 * ```cv2.destroyAllWindows()``` this code will destroy all the windows created before.
