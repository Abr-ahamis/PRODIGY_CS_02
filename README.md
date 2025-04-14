# Image_Encryption_Tool_with_GUI
This project implements an image encryption tool in Python that transforms any input image into an unrecognizable output resembling random noise. The tool supports both encryption and decryption—ensuring that using the same key recovers the original image losslessly. It also features a user-friendly GUI built with Tkinter.

## Installation

### Prerequisites
- **Python 3.6+** (recommended)
- The following Python libraries:
  - [Pillow](https://python-pillow.org/) for image handling.
  - [numpy](https://numpy.org/) for efficient pixel manipulation.
  - [tkinter](https://docs.python.org/3/library/tkinter.html) (usually included with Python).

### Dependency Installation
Install the required packages via pip:
```bash
pip install pillow numpy
```

# Setup Steps
 Clone the repository:
```bash
git clone https://github.com/yourusername/image-encryptor-gui.git
```
Navigate to the project directory:
```bash
cd image-encryptor-gui
```
Usage
GUI Operation
Run the script:
```bash
python image_encryptor_gui.py
```
# In the GUI window:
Click "Select Image" to choose an input image file (JPEG, PNG, BMP, etc.).
Enter an encryption key in the provided field.
Choose "Encrypt" to transform the image into random noise or "Decrypt" to recover the original image (using the same key).
Click "Process". The tool will save the output image in the same directory as the input with an appended filename (_encrypted or _decrypted).
The original and result images will be displayed in the window.
Command-Line Options
 #### Note: The current version is GUI-first. Future releases may include command-line argument support for headless operation.

# How It Works
## Encryption Process
Image Conversion: The input image is loaded and converted to a numpy array.
Flattening: The pixel data is flattened to a one-dimensional array.
Key Derivation: A reproducible seed is derived from the user-provided key using SHA-256.
Permutation & Key Stream: Two random generators (seeded independently) produce:
A permutation array that shuffles pixel positions.
A key stream (array of random integers) for XOR operations.
Transformation: The tool permutes the pixel array and applies XOR with the key stream, ensuring that the output appears as random noise.
Reshaping: The transformed array is reshaped back into the original image dimensions and saved.

## Decryption Process
Image Conversion: The encrypted image is loaded and converted to a numpy array.
Flattening: The pixel data is flattened.
Key Regeneration: Using the same key, the identical permutation and key stream are regenerated.
Reverse Operations: The tool first reverses the XOR operation, then applies the inverse permutation to restore the original pixel order.
Reshaping: The recovered data is reshaped into the original image dimensions to perfectly reconstruct the original image.

# Key/Seed Role
The user-provided key is hashed to produce a seed for random number generation. This seed ensures that both the permutation and key stream are reproducible, so that encryption and decryption are perfectly reversible when the same key is used.


