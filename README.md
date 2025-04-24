# Cell Counter with Deep Learning

A deep learning-based tool for automated cell counting in microscopy images using a U-Net architecture.

## Overview

This project implements an automated cell counting system that uses deep learning to identify and count cells in microscopy images. Instead of traditional computer vision approaches that might struggle with overlapping cells or varying cell appearances, this system uses a U-Net neural network to generate density maps and provide accurate cell counts.

## Goals

1. **Automated Cell Counting**: Replace manual cell counting with an automated, reliable system
2. **Density Map Generation**: Create visual representations of cell distributions
3. **Deep Learning Application**: Utilize modern deep learning techniques for biological image analysis
4. **Accuracy**: Provide accurate cell counts even in images with overlapping or clustered cells

## How It Works

The system works in several steps:

1. **Image Preprocessing**:
   - Resizes input images to 512x512 pixels
   - Normalizes pixel values to range [0,1]

2. **Ground Truth Generation**:
   - Takes cell coordinates from CSV files
   - Creates Gaussian kernels around each cell location
   - Generates ground truth density maps

3. **Model Architecture**:
   - Implements U-Net architecture with:
     - Contracting path (encoding)
     - Bottleneck
     - Expanding path (decoding)
   - Uses batch normalization for training stability

4. **Training**:
   - Trains on image-density map pairs
   - Uses Mean Absolute Error (MAE) loss
   - Employs Adam optimizer

5. **Visualization and Output**:
   - Shows side-by-side comparison of ground truth and predicted density maps
   - Provides numerical cell count predictions

## Input Requirements

1. **Image Files**: 
   - TIF format microscopy images
   - Will be automatically resized to 512x512

2. **CSV Files**:
   - Must contain 'X' and 'Y' columns
   - Coordinates for each cell in the corresponding image

## Dependencies

- Python 3.10+
- TensorFlow/Keras
- OpenCV (cv2)
- NumPy
- Pandas
- Matplotlib

## Usage

1. Place your TIF image and corresponding CSV file in the same directory
2. Update the filenames in the `main()` function if different from default
3. Run the script:
   ```bash
   python cell-counter.py
   ```

## Output

The script provides:
1. Visual output showing:
   - Ground truth density map
   - Predicted density map
2. Numerical output:
   - Predicted cell count
   - Training progress metrics

## Technical Details

- **Model Architecture**: U-Net with skip connections
- **Input Size**: 512x512x1 (grayscale images)
- **Output**: Density map (512x512x1)


## Hardware Requirements

- Compatible with CPU and GPU
- Optimized for Apple Silicon (M1/M2) using tensorflow-metal
- Minimum 8GB RAM recommended

## Future Improvements

1. Implement data augmentation for better generalization
2. Add model checkpointing and early stopping
3. Include validation metrics and confusion matrix
4. Add support for different image formats

## License

This project is open-source and available for research and educational purposes. 
