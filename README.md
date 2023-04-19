# Edge-Linking-using-Hough-Transform
## Aim:
To write a Python program to detect the lines using Hough Transform.

## Software Required:
Anaconda - Python 3.7

## Algorithm:
### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load a image using imread() from cv2 module.

### Step 3:
Convert the image to grayscale.

### Step 4:
Using Canny operator from cv2,detect the edges of the image

### Step 5:
Using the HoughLinesP(),detect line co-ordinates for every points in the images.Using For loop,draw the lines on the found co-ordinates.

### Step 6:
Display the image and end the program.

## Program:
```
import cv2
import matplotlib.pyplot as plt
import numpy as np

# Read image and convert it to grayscale image

image=cv2.imread("road.jfif")
gray_img=cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)
img=cv2.GaussianBlur(gray_img,(3,3),0)
plt.imshow(image)

# Find the edges in the image using canny detector and display

edges = cv2.Canny(image,160, 200)
plt.figure(figsize=(16,16))
plt.subplot(1,2,1)
plt.imshow(img,cmap='gray')
plt.title('Gray')
plt.subplot(1,2,2)
plt.imshow(edges,cmap='gray')
plt.title("Canny_edges")
plt.xticks([])
plt.yticks([])
plt.show()

# Detect points that form a line using HoughLinesP

lines=cv2.HoughLinesP(edges,1,np.pi/180,threshold=80,minLineLength=50,maxLineGap=250)

# Draw lines on the image

for line in lines:
    x1,y1,x2,y2=line[0]
    cv2.line(image,(x1,y1),(x2,y2),(0,205,255),2)

# Display the result

plt.imshow(image)
plt.title('HOUGH')
plt.axis('off')

```
## Output

### Input image and grayscale image
![dip8 1](https://user-images.githubusercontent.com/94165415/233111615-fd65c7a7-05a4-4abb-b851-54fd7c451cb1.png)


### Canny Edge detector output

![dip8 2](https://user-images.githubusercontent.com/94165415/233114482-69a57442-6bd8-43e1-8f09-1275d9b3badf.png)

### Display the result of Hough transform

![dip8 3](https://user-images.githubusercontent.com/94165415/233117217-fdf21a42-01cc-45b3-bbf6-dbd1cfb5b6be.png)

## Result:
Thus the program is written with python and OpenCV to detect lines using Hough transform. 
