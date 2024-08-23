# SVD-watermarking-and-robust-watermarking

## Overview 🔎

This project implements an image watermarking technique using Singular Value Decomposition (SVD). The main goal of this project is to embed a watermark into an image in such a way that the watermark remains invisible to the naked eye, yet recoverable even after common image transformations and attacks, such as compression, scaling, rotation, and noise addition. The project includes two watermarking methods:

1. **Robust Watermarking (D and U Matrices)**: In this method, the watermark is embedded into both the D (diagonal) and U (left singular) matrices obtained from the SVD of an image. The embedding in the D matrix is done using a technique called Dither Quantization. Dither Quantization helps to modify the singular values in a way that the watermark remains imperceptible while maintaining high robustness against various attacks and transformations. By combining this approach with embedding in the U matrix, this method ensures that the watermark is resilient to a wide range of image manipulations.
The implementation of this method can be found in the `/RobustSVD_watermarking` directory.

3. **Basic Watermarking (U Matrix Only)**: In this simpler method, the watermark is embedded only into the U matrix. While this approach is straightforward, it is less robust and may not withstand many image transformations.
The implementation of this method can be found in the `/SVD_watermarking` directory.

## Testing and Transformations 🧪

The watermarking methods were rigorously tested against a variety of image transformations to evaluate their robustness. These transformations include:

- **JPEG Compression**: Evaluated at various quality levels to test how well the watermark survives lossy compression.
- **Scaling**: The image was resized up and down to test the watermark's resilience to changes in image size.
- **Rotation**: The image was rotated by different angles to assess whether the watermark could still be recovered.
- **Salt-and-Pepper Noise**: Noise was added to the image to simulate degradation and check the watermark's robustness against noise.
- **Cropping**: Parts of the image were cropped to see if the watermark could still be detected in the remaining portion.
- **Filtering**: Different types of filters, such as median and low-pass filters, were applied to evaluate the watermark's resistance to blurring and smoothing effects.
- **Gamma Correction**: The brightness of the image was adjusted to test the watermark's visibility under different lighting conditions.

## Evaluation Metrics 📊

To evaluate the performance and robustness of the watermarking techniques, the following metrics were used:

- **Peak Signal-to-Noise Ratio (PSNR)**: This metric is used to measure the visual quality of the watermarked image compared to the original image. Higher PSNR values indicate that the watermarking process introduces less visible distortion, making the watermark imperceptible to the human eye.

- **Bit Error Rate (BER)**: BER measures the number of bits that are incorrectly extracted in the watermark, divided by the total number of bits in the watermark. A lower BER indicates a more accurate extraction of the watermark, which implies better robustness of the watermarking method.

- **Normalized Cross-Correlation (NC)**: NC is used to measure the similarity between the original watermark and the extracted watermark. An NC value close to 1 indicates that the extracted watermark is highly similar to the original, suggesting that the watermarking method is robust.

These metrics provide a comprehensive evaluation of the trade-offs between imperceptibility, robustness, and accuracy of the watermarking methods. The robust watermarking technique, particularly when using Dither Quantization in the D matrix, demonstrated high PSNR values, low BER, and high NC values, confirming its effectiveness in preserving the watermark under various transformations. On the other hand, the basic watermarking method, which embeds the watermark only into the U matrix, generally showed lower PSNR values, higher BER, and lower NC values compared to the robust method. While it still maintains some level of imperceptibility, its robustness is significantly weaker, especially when subjected to more aggressive transformations like heavy JPEG compression or extensive noise addition. This highlights the trade-off with the basic method: it is simpler to implement but less reliable in scenarios where the image undergoes substantial modifications.
All results, including the watermarked images and extracted watermarks, as well as the computed PSNR, BER, and NC values for both methods, can be found in the `/results` directory.



