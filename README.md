# EXPERIMENT 4
---
# Geometric Transformations Using OpenCV
---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using cv2.warpAffine()  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use cv2.resize()  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using cv2.warpAffine()  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using cv2.flip():
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use cv2.getRotationMatrix2D() and cv2.warpAffine()  
- Display original and rotated images  

---

##  Program

### Developed By:
### Name: Sivaprasath R
### Register No: 212224243007
```
import cv2
import numpy as np
import matplotlib.pyplot as plt
```
# Load the image
```
image = cv2.imread('nature.jpg')
image_rgb = cv2.cvtColor(image, cv2.COLOR_BGR2RGB)  # Convert BGR to RGB for Matplotlib
```
# 1. Image Translation
```
rows, cols, _ = image.shape
M_translate = np.float32([[1, 0, 50], [0, 1, 100]])  # Translate by (50, 100) pixels
translated_image = cv2.warpAffine(image_rgb, M_translate, (cols, rows))
```
# 2. Image Scaling
```
scaled_image = cv2.resize(image_rgb, None, fx=1.5, fy=1.5, interpolation=cv2.INTER_LINEAR)  # Scale by 1.5x
```
# 3. Image Shearing
```
M_shear = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shear with factor 0.5
sheared_image = cv2.warpAffine(image_rgb, M_shear, (int(cols * 1.5), int(rows * 1.5)))
```
# 4. Image Reflection (Flip)
```
reflected_image = cv2.flip(image_rgb, 1)  # Horizontal reflection (flip along y-axis)
```
# 5. Image Rotation
```
M_rotate = cv2.getRotationMatrix2D((cols / 2, rows / 2), 45, 1)  # Rotate by 45 degrees
rotated_image = cv2.warpAffine(image_rgb, M_rotate, (cols, rows))
```
# 6. Image Cropping
```
cropped_image = image_rgb[50:300, 100:400]  # Crop a portion of the image
```
# Plot the original and transformed images
```
plt.figure(figsize=(12, 8))

plt.subplot(2, 3, 1)
plt.imshow(image_rgb)
plt.title("Original Image")
plt.axis('off')

plt.subplot(2, 3, 2)
plt.imshow(translated_image)
plt.title("Translated Image")
plt.axis('off')

plt.subplot(2, 3, 3)
plt.imshow(scaled_image)
plt.title("Scaled Image")
plt.axis('off')

plt.subplot(2, 3, 4)
plt.imshow(sheared_image)
plt.title("Sheared Image")
plt.axis('off')

plt.subplot(2, 3, 5)
plt.imshow(reflected_image)
plt.title("Reflected Image")
plt.axis('off')

plt.subplot(2, 3, 6)
plt.imshow(rotated_image)
plt.title("Rotated Image")
plt.axis('off')

plt.tight_layout()
plt.show()
```
# Plot cropped image separately as its aspect ratio may be different
```
plt.figure(figsize=(4, 4))
plt.imshow(cropped_image)
plt.title("Cropped Image")
plt.axis('off')
plt.show()
```
---

##  Output

### Original Image
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/230da91b-1e57-41c3-a004-ff954edd4734" />

### Image Translation
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/aa027d00-ccb8-4ca8-b1b9-7fec3d82a8b0" />
### Image Scaling
<img width="515" height="238" alt="download" src="https://github.com/user-attachments/assets/741fb601-b751-47e3-92c8-139d1effbe26" />

### Image Shearing
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/6587a1ec-0411-48bb-a805-a94281d6cf14" />

### Image Reflection
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/3e34924d-3ece-4da6-826a-ae21675d094d" />

### Image Rotation
<img width="389" height="409" alt="download" src="https://github.com/user-attachments/assets/3288c75b-ee6e-4076-b693-4ecf08eb641c" />
### Image Cropped
<img width="512" height="409" alt="download" src="https://github.com/user-attachments/assets/9b7573f9-06ac-4326-a6e7-4c5c3af57785" />


---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
