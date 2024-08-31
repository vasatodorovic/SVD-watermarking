# SVD-watermarking-and-robust-watermarking

## Overview 🔎

This project implements an image watermarking technique using Singular Value Decomposition (SVD). The main goal of this project is to embed a watermark into an image in such a way that the watermark remains invisible to the naked eye, yet recoverable even after common image transformations and attacks, such as compression, scaling, brightness adjustment, median filter and noise addition. The project includes two watermarking methods:

1. **Robust Watermarking (D and U Matrices)**: In this method, the watermark is embedded into both the D (diagonal) and U (left singular) matrices obtained from the SVD of an image. The embedding in the D matrix is done using a technique called Dither Quantization. Dither Quantization helps to modify the singular values in a way that the watermark remains imperceptible while maintaining high robustness against various attacks and transformations. By combining this approach with embedding in the U matrix, this method ensures that the watermark is resilient to a wide range of image manipulations.
The implementation of this method can be found in the `/RobustSVD_watermarking` directory.

3. **Basic Watermarking (U Matrix Only)**: In this simpler method, the watermark is embedded only into the U matrix. While this approach is straightforward, it is less robust and may not withstand many image transformations.
The implementation of this method can be found in the `/SVD_watermarking` directory.

## Testing and Transformations 🧪

The watermarking methods were rigorously tested against a variety of image transformations to evaluate their robustness. These transformations include:

- **JPEG Compression**: Evaluated at various quality levels to test how well the watermark survives lossy compression.
- **Resizing**: The image was resized up and down to test the watermark's resilience to changes in image size.
- **Salt-and-Pepper Noise**: Noise was added to the image to simulate degradation and check the watermark's robustness against noise.
- **Filtering**: Median filter was applied to evaluate the watermark's resistance to blurring and smoothing effects.
- **Brightness Adjustment and Gamma Correction**: The brightness of the image was adjusted to test the watermark's visibility under different lighting conditions.

## Evaluation Metrics 📊

To evaluate the performance and robustness of the watermarking techniques, the following metrics were used:

- **Peak Signal-to-Noise Ratio (PSNR)**: This metric is used to measure the visual quality of the watermarked image compared to the original image. Higher PSNR values indicate that the watermarking process introduces less visible distortion, making the watermark imperceptible to the human eye.

- **Bit Error Rate (BER)**: BER measures the number of bits that are incorrectly extracted in the watermark, divided by the total number of bits in the watermark. A lower BER indicates a more accurate extraction of the watermark, which implies better robustness of the watermarking method.

- **Normalized Cross-Correlation (NC)**: NC is used to measure the similarity between the original watermark and the extracted watermark. An NC value close to 1 indicates that the extracted watermark is highly similar to the original, suggesting that the watermarking method is robust.



