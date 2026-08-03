# Image Steganography Using LSB Technique

## Overview

Image Steganography is a C-based project that hides secret information inside a BMP image using the **Least Significant Bit (LSB)** technique. The hidden data can later be extracted from the stego image using the decoding operation.

The project demonstrates the concepts of **file handling, bitwise operations, data encoding, and data decoding in C**.

## Features

* Encode secret data into a BMP image
* Decode hidden data from a stego image
* Uses the Least Significant Bit (LSB) technique
* Supports hiding text files inside BMP images
* Preserves the visual appearance of the original image
* Validates whether the image has sufficient capacity to store the secret data
* Stores information required to retrieve the hidden file
* Uses file handling and bitwise operations in C

## How It Works

The project provides two main operations:

### 1. Encoding

During encoding, the secret file is hidden inside the source BMP image.

The encoding process stores:

1. BMP header
2. Magic string
3. Secret file extension size
4. Secret file extension
5. Secret file size
6. Secret file data
7. Remaining image data

Each bit of the secret information is stored in the **Least Significant Bit (LSB)** of the image data bytes.

### 2. Decoding

During decoding, the application reads the LSBs of the stego image and reconstructs the hidden information.

The decoding process retrieves:

1. Magic string
2. Secret file extension size
3. Secret file extension
4. Secret file size
5. Secret file data

The extracted information is then written into a new output file.

## Technologies Used

* C Programming
* File Handling
* Bitwise Operations
* Structures
* Pointers
* Command-Line Arguments
* BMP Image Processing

## Project Files

```text
Image-Steganography/
│
├── encode.c
├── encode.h
├── decode.c
├── decode.h
├── common.h
├── types.h
├── main.c
├── Makefile
├── beautiful.bmp
└── secret.txt
```

## Compilation

Compile the project using GCC:

```bash
gcc *.c -o steganography
```

Or, if a Makefile is provided:

```bash
make
```

## Usage

### Encoding

```bash
./steganography -e <source_image.bmp> <secret_file.txt> [output_image.bmp]
```

Example:

```bash
./steganography -e beautiful.bmp secret.txt stego.bmp
```

This hides the contents of `secret.txt` inside `beautiful.bmp` and creates `stego.bmp`.

### Decoding

```bash
./steganography -d <stego_image.bmp> [output_file]
```

Example:

```bash
./steganography -d stego.bmp decoded
```

This extracts the hidden information from `stego.bmp`.

## LSB Technique

The **Least Significant Bit (LSB)** is the rightmost bit of a byte.

For example:

```text
Original image byte:
10110110

Secret bit:
1

After encoding:
10110111
```

Only the least significant bit is modified. Since this change has a very small effect on the pixel value, the difference is generally not noticeable visually.

## Learning Outcomes

Through this project, I gained practical experience with:

* File handling in C
* Bitwise operators
* Manipulating individual bits
* BMP image structure
* Encoding and decoding techniques
* Pointers and structures
* Modular programming
* Error handling and input validation

## Applications

Image steganography can be used for:

* Concealing information inside digital media
* Digital watermarking
* Secure information transfer
* Understanding information-hiding techniques

## Author

**Vijay H M**
