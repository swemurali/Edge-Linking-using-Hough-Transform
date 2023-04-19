# Edge-Linking-using-Hough-Transform
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step1:
Import all the necessary modules for the program.

### Step2:
Load a image using imread() from cv2 module.

### Step3:
Convert the image to grayscale.

### Step4:
Using Canny operator from cv2,detect the edges of the image.

### Step5:
Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.Display the image.

## Program:
```
### DEVELOPED BY :M.Suwetha
### REGISTER NUMBER : 212221230112
```
```
# Read image and convert it to grayscale image

import numpy as np
import cv2
import matplotlib.pyplot as plt
inputimage = cv2.imread("chess.png")
inputimage = cv2.cvtColor(inputimage,cv2.COLOR_BGR2RGB)
plt.axis('off')
plt.imshow(inputimage)
plt.show()

grayimage=cv2.cvtColor(inputimage,cv2.COLOR_BGR2GRAY)
newimage=cv2.GaussianBlur(grayimage,(3,3),0)


# Find the edges in the image using canny detector and display
#CANNY EDGE DETECTOR
canny_edge=cv2.Canny(newimage,120,150)
plt.figure(figsize=(8,8))
plt.subplot(1,2,1)
plt.imshow(newimage)
plt.title('grey')
plt.subplot(1,2,2)
plt.imshow(canny_edge)
plt.title('Canny Edges')
plt.yticks([])
plt.show()


# Detect points that form a line using HoughLinesP

lines=cv2.HoughLinesP(canny_edge,1,np.pi/180, threshold=105, minLineLength=70,maxLineGap=300)

# Draw lines on the image
for line in lines:
    x1, y1, x2, y2 = line [0] 
    cv2.line(canny_edge,(x1, y1),(x2, y2),(255, 0, 0),3)
# Display the result

plt.imshow(canny_edge)

```
## Output

### Input image and grayscale image

![1a](https://user-images.githubusercontent.com/94165336/233023055-c117e094-7308-4f0c-9aa3-fe28d09ebeeb.png)

### Canny Edge detector output

![2a](https://user-images.githubusercontent.com/94165336/233023079-4f411698-4bca-4c9a-bd9b-e724381017cd.png)

### Display the result of Hough transform

![3a](https://user-images.githubusercontent.com/94165336/233023120-1f21ae30-7d37-4389-b5ea-bc0612140295.png)


## Result:
Thus the program is written with python and OpenCV to detect lines using Hough transform. 
