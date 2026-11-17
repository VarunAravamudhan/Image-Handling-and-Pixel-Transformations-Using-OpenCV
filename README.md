# Image Handling and Pixel Transformations Using OpenCV

**NAME:** Varun A
**REG NO:** 212224240178

## AIM:

Write a Python program using OpenCV that performs the following tasks:

1. Read and display a scenery image.
2. Adjust the brightness of the image.
3. Modify the image contrast.
4. Generate a third image using bitwise operations.
5. Split the image into Blue, Green, and Red components and display the individual channels.

## SOFTWARE REQUIRED:

- Anaconda – Python 3.7
- Jupyter Notebook (for interactive development and execution)
- OpenCV
- NumPy
- Matplotlib

## ALGORITHM:

**Step 1:** Import the required libraries, including OpenCV, NumPy, and Matplotlib.

**Step 2:** Read a scenery image from the local directory using OpenCV's `imread()` function.

**Step 3:** Convert the image from BGR to RGB format and display the original image using Matplotlib.

**Step 4:** Create a matrix of ones with the data type `float64` to adjust the brightness of the image.

**Step 5:** Generate brighter and darker images by adding and subtracting a constant value from the original image.

**Step 6:** Modify the image contrast using scaling factors of 1.1 and 1.2.

**Step 7:** Generate a binary mask and perform a bitwise AND operation between the original image and the mask to produce a third image.

**Step 8:** Split the original image into Blue, Green, and Red channels using OpenCV's `split()` function.

**Step 9:** Display the individual color channels using Matplotlib.

**Step 10:** Display all the resulting images and observe the changes in brightness, contrast, bitwise operations, and color channels.

## PROGRAM DEVELOPED BY:

**NAME:** Varun A  
**REG NO:** 212224240178

## PROGRAM:

### 1. Import the required libraries.

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Read and display the scenery image.

```python
img = cv2.imread("scenery.jpg")

img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Original Scenery Image")
plt.axis("off")
plt.show()
```

### 3. Adjust the brightness of the image.

```python
matrix = np.ones(img.shape, dtype="float64") * 50
```

### 4. Create brighter and darker images.

```python
img_brighter = cv2.add(img, matrix, dtype=cv2.CV_8U)
img_darker = cv2.subtract(img, matrix, dtype=cv2.CV_8U)
```

### 5. Display the original, brighter, and darker images.

```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title("Brighter Image")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title("Darker Image")
plt.axis("off")

plt.show()
```

### 6. Modify the image contrast.

```python
img_higher1 = cv2.convertScaleAbs(img, alpha=1.1, beta=0)
img_higher2 = cv2.convertScaleAbs(img, alpha=1.2, beta=0)
```

### 7. Display the original and contrast-adjusted images.

```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.1")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(img_higher2, cv2.COLOR_BGR2RGB))
plt.title("Contrast 1.2")
plt.axis("off")

plt.show()
```

### 8. Generate a third image using bitwise operations.

```python
mask = np.zeros(img.shape[:2], dtype="uint8")

cv2.rectangle(mask, (100, 100), (400, 400), 255, -1)

bitwise_image = cv2.bitwise_and(img, img, mask=mask)
```

### 9. Display the original image, mask, and bitwise image.

```python
plt.figure(figsize=(15,5))

plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(mask, cmap="gray")
plt.title("Binary Mask")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(bitwise_image, cv2.COLOR_BGR2RGB))
plt.title("Bitwise AND Image")
plt.axis("off")

plt.show()
```

### 10. Split the image into B, G, R components.

```python
B, G, R = cv2.split(img)

plt.figure(figsize=(12,4))

plt.subplot(1,3,1)
plt.imshow(B, cmap="gray")
plt.title("Blue Channel")
plt.axis("off")

plt.subplot(1,3,2)
plt.imshow(G, cmap="gray")
plt.title("Green Channel")
plt.axis("off")

plt.subplot(1,3,3)
plt.imshow(R, cmap="gray")
plt.title("Red Channel")
plt.axis("off")

plt.show()
```

## OUTPUT:

The following outputs are obtained:

1. Original Scenery Image
2. Brighter Image
3. Darker Image
4. Contrast 1.1 Image
5. Contrast 1.2 Image
6. Binary Mask
7. Bitwise AND Image
8. Blue Channel
9. Green Channel
10. Red Channel

<img width="1513" height="817" alt="image" src="https://github.com/user-attachments/assets/3920e189-a247-4fa2-b258-c3ce301877e8" />

<img width="1362" height="462" alt="image" src="https://github.com/user-attachments/assets/807826e1-1f28-4587-8293-0da5a7dfd362" />



## RESULT:

Thus, the scenery image was successfully read and displayed using OpenCV. Brightness and contrast adjustments were performed, a third image was generated using bitwise operations, and the individual Blue, Green, and Red channels were extracted and displayed successfully.
