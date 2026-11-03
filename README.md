## **AIM:**

Write a Python program using OpenCV that performs the following tasks:

1. Read and Display an Image.
2. Adjust the brightness of an image.
3. Modify the image contrast.
4. Generate a third image using bitwise operations.

## **Software Required:**

- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## **Algorithm:**

### **Step 1:**

Load an image from your local directory and display it.

### **Step 2:**

Create a matrix of ones (with data type float64) to adjust brightness.

### **Step 3:**

Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### **Step 4:**

Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2.  
Display the original, lower contrast, and higher contrast images.

### **Step 5:**

Split the image into B, G, R components and display the channels.

## **Program Developed By:**

- **Name:** [Your Name Here]
- **Register Number:** [Your Register Number Here]

### **Ex. No. 01**

#### **1. Read the image ('images.jpg') using OpenCV imread() as a grayscale image.**

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

img = cv2.imread('images.jpg', cv2.IMREAD_GRAYSCALE)
```

#### **2. Print the image width, height & Channel.**

```python
height, width = img.shape

print("Width:", width)
print("Height:", height)
print("Channel:", 1)
```

#### **3. Display the image using matplotlib imshow().**

```python
plt.imshow(img, cmap='gray')
plt.title("Grayscale Image")
plt.axis('off')
plt.show()
```

#### **4. Save the image as a PNG file using OpenCV imwrite().**

```python
cv2.imwrite('Mountain_Grayscale.png', img)
```

#### **5. Read the saved image above as a color image using cv2.cvtColor().**

```python
img_color = cv2.imread('Mountain_Grayscale.png')
img_color = cv2.cvtColor(img_color, cv2.COLOR_BGR2RGB)
```

#### **6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.**

```python
height, width, channel = img_color.shape

print("Width:", width)
print("Height:", height)
print("Channel:", channel)

plt.imshow(img_color)
plt.title("Color Image")
plt.axis('off')
plt.show()
```

#### **7. Crop the image to extract a specific object (Mountain and lake reflection) from the image.**

```python
cropped_img = img_color[20:310, 70:550]

plt.imshow(cropped_img)
plt.title("Cropped Mountain and Lake")
plt.axis('off')
plt.show()
```

#### **8. Resize the image up by a factor of 2x.**

```python
resized_img = cv2.resize(
    cropped_img, None, fx=2, fy=2,
    interpolation=cv2.INTER_CUBIC
)

plt.imshow(resized_img)
plt.title("Resized Image")
plt.axis('off')
plt.show()
```

#### **9. Flip the cropped/resized image horizontally.**

```python
flipped_img = cv2.flip(resized_img, 1)

plt.imshow(flipped_img)
plt.title("Horizontally Flipped Image")
plt.axis('off')
plt.show()
```

#### **10. Read in the image ('images.jpg').**

```python
img_original = cv2.imread('images.jpg')
```

#### **11. Add text to the dark area at the bottom of the image (centered on the image).**

```python
text = 'Mountain and Lake Reflection'
font_face = cv2.FONT_HERSHEY_PLAIN

font_scale = 2
thickness = 2

text_size = cv2.getTextSize(
    text, font_face, font_scale, thickness
)[0]

text_x = (img_original.shape[1] - text_size[0]) // 2
text_y = img_original.shape[0] - 20

cv2.putText(
    img_original, text, (text_x, text_y),
    font_face, font_scale, (255, 255, 255),
    thickness
)
```

#### **12. Draw a magenta rectangle that encompasses the mountain and lake reflection.**

```python
rect_color = (255, 0, 255)

cv2.rectangle(
    img_original, (70, 20), (550, 310),
    rect_color, 3
)
```

#### **13. Display the final annotated image.**

```python
img_rgb = cv2.cvtColor(img_original, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.title("Annotated Mountain Image")
plt.axis('off')
plt.show()
```

#### **14. Read the image ('images.jpg').**

```python
img = cv2.imread('images.jpg')
```

#### **15. Adjust the brightness of the image.**

```python
# Create a matrix of ones (with data type float64)
matrix_ones = np.ones(img.shape, dtype=np.float64) * 50
```

#### **16. Create brighter and darker images.**

```python
img_brighter = cv2.add(img, matrix_ones, dtype=cv2.CV_8U)
img_darker = cv2.subtract(img, matrix_ones, dtype=cv2.CV_8U)
```

#### **17. Display the images (Original Image, Darker Image, Brighter Image).**

```python
plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(cv2.cvtColor(img_darker, cv2.COLOR_BGR2RGB))
plt.title("Darker Image")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(img_brighter, cv2.COLOR_BGR2RGB))
plt.title("Brighter Image")
plt.axis('off')

plt.show()
```

#### **18. Modify the image contrast.**

```python
# Create two higher contrast images using scaling factors
matrix1 = np.ones(img.shape, dtype=np.float64) * 1.1
matrix2 = np.ones(img.shape, dtype=np.float64) * 1.2

# Higher contrast images
img_higher1 = cv2.multiply(img, matrix1, dtype=cv2.CV_8U)
img_higher2 = cv2.multiply(img, matrix2, dtype=cv2.CV_8U)

# Lower contrast image
matrix3 = np.ones(img.shape, dtype=np.float64) * 0.8
img_lower = cv2.multiply(img, matrix3, dtype=cv2.CV_8U)
```

#### **19. Display the images (Original, Lower Contrast, Higher Contrast).**

```python
plt.figure(figsize=(15, 5))

plt.subplot(1, 4, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 4, 2)
plt.imshow(cv2.cvtColor(img_lower, cv2.COLOR_BGR2RGB))
plt.title("Lower Contrast")
plt.axis('off')

plt.subplot(1, 4, 3)
plt.imshow(cv2.cvtColor(img_higher1, cv2.COLOR_BGR2RGB))
plt.title("Higher Contrast 1.1")
plt.axis('off')

plt.subplot(1, 4, 4)
plt.imshow(cv2.cvtColor(img_higher2, cv2.COLOR_BGR2RGB))
plt.title("Higher Contrast 1.2")
plt.axis('off')

plt.show()
```

#### **20. Split the image into the B, G, R components & Display the channels.**

```python
B, G, R = cv2.split(img)

plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(B, cmap='gray')
plt.title("Blue Channel")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(G, cmap='gray')
plt.title("Green Channel")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(R, cmap='gray')
plt.title("Red Channel")
plt.axis('off')

plt.show()
```

#### **21. Merge the R, G, B channels and display along with the original image.**

```python
merged_img = cv2.merge([B, G, R])

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged_img, cv2.COLOR_BGR2RGB))
plt.title("Merged Image")
plt.axis('off')

plt.show()
```

#### **22. Split the image into the H, S, V components & Display the channels.**

```python
hsv_img = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)

H, S, V = cv2.split(hsv_img)

plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(H, cmap='gray')
plt.title("Hue")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(S, cmap='gray')
plt.title("Saturation")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(V, cmap='gray')
plt.title("Value")
plt.axis('off')

plt.show()
```

#### **23. Merge the H, S, V channels and display along with the original image.**

```python
merged_hsv = cv2.merge([H, S, V])

merged_image = cv2.cvtColor(
    merged_hsv, cv2.COLOR_HSV2BGR
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged_image, cv2.COLOR_BGR2RGB))
plt.title("Merged HSV Image")
plt.axis('off')

plt.show()
```

#### **Bitwise Operation – Generate a Third Image.**

```python
# Create a mask
mask = np.zeros(img.shape[:2], dtype=np.uint8)

height, width = mask.shape

cv2.rectangle(
    mask,
    (width // 4, height // 4),
    (3 * width // 4, 3 * height // 4),
    255,
    -1
)

# Perform bitwise AND operation
bitwise_img = cv2.bitwise_and(img, img, mask=mask)

plt.figure(figsize=(15, 5))

plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')

plt.subplot(1, 3, 2)
plt.imshow(mask, cmap='gray')
plt.title("Mask")
plt.axis('off')

plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(bitwise_img, cv2.COLOR_BGR2RGB))
plt.title("Bitwise AND Image")
plt.axis('off')

plt.show()
```

## **Output:**

- **i)** Read and Display an Image.
- **ii)** Adjust Image Brightness.
- **iii)** Modify Image Contrast.
- **iv)** Generate Third Image Using Bitwise Operations.

## **Result:**

Thus, the image was read and displayed, brightness and contrast adjustments were performed, and bitwise operations were successfully applied using the Python program.
