# Blurred Image Enhancement Using Image Processing Techniques

## Overview

This project focuses on improving the quality of blurred photographs using digital image processing techniques.

The project explores a combination of **image restoration, noise reduction, and image sharpening** to reduce unwanted blur while improving the clarity and quality of image regions that are not intended to remain blurred.

The main restoration method used in this project is **Wiener Deconvolution**, while several preprocessing and sharpening techniques are evaluated to determine which approach provides the best image quality.

The processed images are evaluated using **Peak Signal-to-Noise Ratio (PSNR), Structural Similarity Index (SSIM), and Mean Squared Error (MSE)**.

---

## Objectives

The objectives of this project are to:

- Understand how image processing algorithms can be used to improve the quality of blurred photographs.
- Preserve or improve the artistic characteristics of blurred photographs while enhancing image sharpness.
- Evaluate different image restoration and sharpening techniques.
- Reduce unwanted imperfections caused by factors such as camera movement, defocus, or poor lighting.
- Compare the effectiveness of different preprocessing and sharpening approaches.
- Identify an image enhancement approach that provides a good balance between sharpness and visual quality.

---

## Input Image

The project uses a blurred photograph as the primary input for the image restoration and enhancement process.

The original image and processed results are documented in the project documentation and presentation. The original image files are not included separately in this repository.

---
## Preprocessing

### Normalization

The input image is normalized to a pixel intensity range of **0–255** before further processing.

This step standardizes the pixel intensity values and prepares the image for subsequent enhancement techniques.

### Gaussian Blur

Gaussian Blur is applied as a preprocessing step to reduce unwanted noise and smooth rapid intensity variations in the image.

The filtered image is then used in the subsequent restoration and sharpening processes.

---

## Image Restoration

### Wiener Deconvolution

Wiener Deconvolution is used to reduce the effects of blur and recover image information from the degraded input image.

A Gaussian kernel is used as the Point Spread Function (PSF).

The parameters used are:

| Parameter | Value |
|---|---:|
| PSF Size | 23 |
| PSF Sigma | 3 |

The Gaussian PSF was selected to represent the characteristics of the blur in the input image.

The Wiener Deconvolution stage produced the following results:

| Method | PSNR | SSIM | MSE |
|---|---:|---:|---:|
| Wiener Deconvolution | 18.86 | 0.7460 | 0.01 |

---

## Image Sharpening

Several sharpening approaches were evaluated to improve image clarity after the restoration and preprocessing stages.

The approaches compared in this project include:

- Sharpening without preprocessing
- Bilateral Filter
- Gaussian Blur
- Non-Local Means Denoising

### Bilateral Filter

Bilateral filtering was evaluated as a preprocessing approach before sharpening.

The technique considers both spatial distance and intensity similarity to reduce noise while preserving image edges.

### Gaussian Blur

Gaussian Blur was evaluated as another preprocessing approach before sharpening.

The method smooths the image using a Gaussian kernel before the sharpening operation.

### Non-Local Means Denoising

Non-Local Means (NLM) Denoising was evaluated as a noise reduction approach before sharpening.

The technique uses information from similar regions in the image to reduce noise while preserving structural details.

---

## Image Quality Evaluation

The processed images were evaluated using three image quality metrics:

- **Peak Signal-to-Noise Ratio (PSNR)**
- **Structural Similarity Index (SSIM)**
- **Mean Squared Error (MSE)**

### PSNR

**Peak Signal-to-Noise Ratio (PSNR)** measures the similarity between the processed image and the reference image based on pixel-level differences.

A higher PSNR generally indicates better reconstruction quality.

### SSIM

**Structural Similarity Index (SSIM)** evaluates the structural similarity between the processed image and the reference image.

A value closer to **1** indicates greater structural similarity.

### MSE

**Mean Squared Error (MSE)** measures the average squared difference between corresponding pixels in the processed and reference images.

A lower MSE indicates lower pixel-level error.

---

## Results

The sharpening approaches produced the following evaluation results:

| Sharpening Method | PSNR | SSIM | MSE |
|---|---:|---:|---:|
| Without Preprocessing | 29.34 | 0.9217 | 17.647547 |
| Bilateral Filter | 12.86 | 0.5070 | 114.01 |
| Gaussian Blur | 31.72 | **0.9428** | **14.18** |
| Non-Local Means Denoising | **32.09** | 0.9145 | 16.66 |

---

## Result Analysis

### PSNR

The highest PSNR was achieved by **Non-Local Means Denoising**, with a value of **32.09 dB**.

This indicates that the NLM approach produced the lowest pixel-level reconstruction error according to the PSNR metric among the evaluated sharpening approaches.

### SSIM

The highest SSIM was achieved by **Gaussian Blur preprocessing**, with a value of **0.9428**.

This indicates that the Gaussian Blur approach produced the highest structural similarity to the reference image.

### MSE

The lowest MSE among the sharpening approaches was achieved by **Gaussian Blur**, with a value of **14.18**.

A lower MSE indicates a smaller average squared pixel-level error.

---

## Comparison of Methods

The results show different strengths across the evaluated methods.

| Method | PSNR | SSIM | MSE | Overall Observation |
|---|---:|---:|---:|---|
| Without Preprocessing | 29.34 | 0.9217 | 17.647547 | Provides a reasonable sharpening result without additional preprocessing |
| Bilateral Filter | 12.86 | 0.5070 | 114.01 | Produces the lowest performance among the evaluated approaches |
| Gaussian Blur | 31.72 | **0.9428** | **14.18** | Provides strong structural similarity and low pixel-level error |
| Non-Local Means | **32.09** | 0.9145 | 16.66 | Achieves the highest PSNR but lower SSIM than Gaussian Blur |

Although **Non-Local Means Denoising** achieved the highest PSNR, the visual result showed that the object became less clear after sharpening.

In comparison, **Gaussian Blur preprocessing** produced a better overall visual result while also achieving the highest SSIM and lowest MSE among the sharpening approaches.

Therefore, the quantitative metrics and visual inspection were considered together when selecting the final approach.

---

## Key Findings

### 1. Wiener Deconvolution Reduces the Effect of Blur

Wiener Deconvolution was used to restore image information affected by blur.

### 2. Preprocessing Affects Sharpening Performance

The results demonstrate that the preprocessing technique applied before sharpening can significantly influence the final image quality.

### 3. Gaussian Blur Provides the Best Overall Result

Gaussian Blur preprocessing achieved:

- **PSNR:** 31.72
- **SSIM:** 0.9428
- **MSE:** 14.18

It achieved the highest SSIM and lowest MSE among the evaluated sharpening methods.

### 4. The Highest PSNR Does Not Always Mean the Best Visual Result

Although Non-Local Means Denoising achieved the highest PSNR of **32.09**, the resulting image showed reduced object clarity after sharpening.

This demonstrates that image quality evaluation should not rely on a single quantitative metric.

### 5. Final Selected Approach

Based on the combination of quantitative evaluation and visual inspection, **Gaussian Blur preprocessing followed by sharpening** was considered the most suitable approach for improving the quality of the blurred image.

---

## Limitations

Several limitations should be considered:

- The evaluation was performed on the specific blurred image used in the project.
- The original image files are not included separately in this repository.
- Image enhancement performance may vary depending on the type and severity of blur.
- Different blur patterns may require different Point Spread Functions (PSFs).
- PSNR, SSIM, and MSE do not always fully represent perceived visual quality.
- The method with the highest quantitative score does not necessarily produce the best visual result.
