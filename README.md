# Blueprintco.app Assignment

In this assignment, the goal is to develop a Python script that can analyze two PDFs, 'file_1.pdf' and 'file_2.pdf', convert them into images, compare the images, and highlight the differences. We have provided a file called 'expected_output.pdf', which highlights what the result should look like.

## Approach
1. Converting PDFs to images using the pdf2image library in Python.
2. Reading the images using OpenCV.
3. I implemented various approaches, but the final output matched the 'Mathematical Masking' approach:
    1. I experimented with various thresholding techniques, such as adaptive thresholding with and without Gaussian blurring, Otsu thresholding, and binarization, for creating masks. Ultimately, I found that Otsu thresholding with Gaussian blur (to smoothen the image) provided clean masks.
    2. Then, I tried various arithmetic operations on these masks to analyze the images.
    3. Finally, I overlapped the difference between mask1 and mask2 with red color and the difference between mask2 and mask1 with blue over 'img1'. The final operations are marked in 'img2', where the masks were smoothed with Gaussian blur.
4. I also implemented various methods:
    1. One of the methods involved edge detection using the 'createLineSegmentDetector' class and then adding (overlaying) images with relevant weights.
    2. Another method included Canny edge detection with Hough Line Probabilistic Transform, which first detected the edges and then built lines using the Hough transform. After this, overlaying was performed.
    3. Furthermore, I implemented highlighting differences through SSIM (Structural Similarity Index), thresholding, and contour detection.
