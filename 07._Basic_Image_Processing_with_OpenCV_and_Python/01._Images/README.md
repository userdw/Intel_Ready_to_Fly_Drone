# [ENGLISH] 01. Images

<img src="/images/Lenna.jpg" height="400">

In this section, we will use well known image of Lenna above for testing purpose. It will be easier if we make a folder for each practice project, then put our images and codes in it.

Table of contents:
* [01. Displaying an Image](#displaying-an-image)
* [02. Color Spaces](#color-spaces)

### Displaying an Image

<img src="/images/Display_Lenna.jpg" height="400">

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
* ```_images = os.path.join(_projectDirectory, "Lenna.jpg")```. Since we put the image in the same directory as the code, we can add the image's name after the path. But since Windows use ```\``` and Linux use ```/``` as separator, it will be easier for us to let Python decides which is the suitable separator. Therefore we will use ```os.path.join```.
* ```cv2.namedWindow("Image", cv2.WINDOW_AUTOSIZE)``` is to create an empty window named ```Image```.
* ```(python)cv2.imshow("Image", _img)``` is to display the image on the window we created before.
* ```cv2.waitKey(0)``` is needed so that the code will wait for an event first, which is waiting for a keypress, instead of executing next code.
* ```cv2.destroyAllWindows()``` this code will destroy all the windows created before.

That's it, we created some sort of _Hello World_ program for our journey with OpenCV and Python!

### Color Spaces
The image of Lenna we used before is 24-bit depth (8-bit Red, 8-bit Green, 8-bit Blue). RGB is the most usual way to represent a color image, and we usually called it as RGB color space. There are other color spaces available to represent a color image. Every color space has its own advantages, and can give better performance in some cases than the other. In this section we will try converting the image of Lenna to some popular color spaces using built-in OpenCV function ```cv2.cvtColor```.

#### RGB
RGB (Red, Green, Blue) is the most usual way to represent a color image. It came from the phiposophy of everything start from black. A given color can be produced through emitting and combining red, green, and blue light together with specific intensity for each light. OpenCV use BGR instead of RGB. They are basically the same in value, but different in order. As for why OpenCV use BGR, [this article](https://www.learnopencv.com/why-does-opencv-use-bgr-color-format/) might give you the reason. You can get each channel's value with built-in OpenCV function ```cv2.split```. Below is the code to extract BGR values in an image and store them separately in variables.
```python
import os, cv2
import numpy as np

_projectDirectory = os.path.dirname(__file__)
_images = os.path.join(_projectDirectory, "Lenna.jpg")

_img = cv2.imread(_images, cv2.IMREAD_UNCHANGED)
_img1, _img2, _img3 = cv2.split(_img)
_imgRslt = np.concatenate((_img1, _img2, _img3), 1)
cv2.namedWindow("Image", cv2.WINDOW_AUTOSIZE)
cv2.imshow("Image", _imgRslt)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

The output image should be the same as image below, representing blue, green, and red channel respectively.

<img src="/images/BGR_Lenna.jpg" height="200">

The simple explanation for code above is as below:
* ```_img1, _img2, _img3 = cv2.split(_img)``` will get each channel's value in an image then store them to variables. ```_img1``` will store first channel value, ```_img2``` will store second channel value, ```_img3``` will store third channel value.
* ```_imgRslt = np.concatenate((_img1, _img2, _img3), 1)```. Since we want to display all the channels as different images in one window, we will need to concatenate ```_img1```, ```_img2```, and ```_img3```, then display the result to the window.

#### Grayscale
Grayscale is one of the most popular color space used in image processing. Grayscale is simpler to process since it is usually represented in 1 channel, compared to 3 channels in color image (usually 1 channel will be represented in 8-bit). Most information in an image usually can be found through its luminance, and grayscale capture the luminance pretty well. In fact the conversion formula from RGB/BGR to grayscale used in built-in OpenCV function is the same with conversion formula from RGB/BGR to Y (luminance) component in YCrCb color space. Not only grayscale is simpler to compute, but it also captures a lot of information within an image. To convert a BGR image to grayscale we just need to use ```cv2.COLOR_BGR2GRAY``` as ```cv2.cvtColor``` parameter. Below is the code to convert BGR color space to grayscale.

<img src="/images/Gray_Formula.jpg" width="500">

```python
import os, cv2
import numpy as np

_projectDirectory = os.path.dirname(__file__)
_images = os.path.join(_projectDirectory, "Lenna.jpg")

_img = cv2.imread(_images, cv2.IMREAD_UNCHANGED)
_imgGray = cv2.cvtColor(_img, cv2.COLOR_BGR2GRAY)
cv2.namedWindow("Image", cv2.WINDOW_AUTOSIZE)
cv2.imshow("Image", _imgGray)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

The output image should be the same as image below.

<img src="/images/Gray_Lenna.jpg" height="200">

The simple explanation for code above is as below:
* ```_imgGray = cv2.cvtColor(_img, cv2.COLOR_BGR2GRAY)``` will convert the image from BGR to grayscale.

#### HLS
HLS (Hue, Lightness, Saturation) color space is another way to represent colors. HLS color space defines colors more naturally. Hue specifies the base color, the other two values then let you specify the saturation of that color and how bright the color should be. HLS color space is cylindrical, and can be represented as the image below. To convert a BGR image to HLS we just need to use ```cv2.COLOR_BGR2GHLS``` as ```cv2.cvtColor``` parameter.

<img src="/images/HLS_Color_Space.png" height="200">
credits to: https://commons.wikimedia.org/wiki/User:SharkD

Below is the code to convert BGR color space to HLS.

<img src="/images/HLS_Formula.jpg" width="500">

```python
import os, cv2
import numpy as np

_projectDirectory = os.path.dirname(__file__)
_images = os.path.join(_projectDirectory, "Lenna.jpg")

_img = cv2.imread(_images, cv2.IMREAD_UNCHANGED)
_imgHLS = cv2.cvtColor(_img, cv2.COLOR_BGR2HLS)
_img1, _img2, _img3 = cv2.split(_imgHLS)
_imgRslt = np.concatenate((_img1, _img2, _img3), 1)
cv2.imwrite(os.path.join(_projectDirectory, "Out.jpg"), _imgRslt)
cv2.namedWindow("Image", cv2.WINDOW_AUTOSIZE)
cv2.imshow("Image", _imgRslt)
cv2.waitKey(0)
cv2.destroyAllWindows()
```

The output image should be the same as image below, representing hue, lightness, and saturation channel respectively.

<img src="/images/HLS_Lenna.jpg" height="200">

If the value of H after calculation is less than 0, we should add 360 to it. The outputs from the above equation will be:
* 0 <= L <= 1
* 0 <= S <= 1
* 0 <= H <= 360

Since we usually use 8-bit depth for each channel, the value of L and S will be scaled-up to 0 - 255, and H will be divided by 2 so it will fit the 8-bit range.

#### YCrCb
YCrCb 
