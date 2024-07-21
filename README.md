# pan_card_OCR
Extracting information from a PAN (Permanent Account Number) card using Python can be done with Optical Character Recognition (OCR) libraries such as Tesseract. Here's a step-by-step guide to accomplish this:

1.Install Tesseract and its Python wrapper, pytesseract:

      1.Install Tesseract OCR:Windows: Download the installer from Tesseract at UB Mannheim and follow the instructions to install.
      
2.Install the pytesseract library and OpenCV:pip install pytesseract opencv-python

3.Set up Tesseract in your Python script:
    import cv2
    import pytesseract

     # Path to the tesseract executable
    pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
    
4.Load the image and preprocess it:

5.Extract text using Tesseract:

6.Extract specific information using regex:

Explanation:
-->Importing Libraries:

The necessary libraries (cv2, pytesseract, re, json) are imported.

Loading the Image:


Preprocessing:The PAN card image is loaded using OpenCV.

Text Extraction:The image is converted to grayscale and thresholded for better OCR accuracy.


Information Extraction:Text is extracted from the preprocessed image using Tesseract.

Regular expressions are used to extract the PAN number, name, and date of birth from the extracted text.
JSON Conversion:


1.json: Used for encoding and decoding JSON data.

2.pytesseract: A Python wrapper for Google's Tesseract-OCR Engine.

3.cv2 (OpenCV): A library for image processing and computer vision tasks.

4.numpy: A library for numerical computations and handling multi-dimensional arrays.

5.sys: Provides access to some variables and functions that interact with the Python interpreter.

6.re: Provides regular expression matching operations.

7.os: Provides functions for interacting with the operating system.

8.PIL (Pillow): A library for opening, manipulating, and saving image files.

9.ftfy: Fixes Unicode text with various issues.

10.pan_read: (Assuming it's a custom module) A module for reading PAN card information.

11.io: Provides the core tools for working with streams (input and output).

Each of these libraries has a specific purpose and functionality that helps in different aspects of programming and data processing.



When using the re module for PAN card extraction, here are the main points:

Pattern Matching: Use regular expressions to find and match the specific patterns of a PAN number, name, and date of birth within the extracted text.

          1.pan_pattern = re.compile(r'([A-Z]{5}[0-9]{4}[A-Z]{1})'): Matches the PAN number format.

          2.name_pattern = re.compile(r'Name\s*:\s*(.*)'): Matches the name field.

          3.dob_pattern = re.compile(r'Date of Birth\s*:\s*(\d{2}/\d{2}/\d{4})'): Matches the date of birth field.


Extraction: Extract the matched patterns using the search() function to retrieve relevant information from the text.

        1.pan_match = pan_pattern.search(text): Searches the text for the PAN number.
        2.name_match = name_pattern.search(text): Searches the text for the name.
        3.dob_match = dob_pattern.search(text): Searches the text for the date of birth.

Validation: Ensure the extracted data conforms to expected formats (e.g., PAN number format: five letters, four digits, one letter).

        1.pan_number = pan_match.group(1) if pan_match else "Not found": Extracts the PAN number if found, otherwise returns "Not found".
        2.name = name_match.group(1).strip() if name_match else "Not found": Extracts and strips the name if found, otherwise returns "Not found".
        3.dob = dob_match.group(1) if dob_match else "Not found": Extracts the date of birth if found, otherwise returns "Not found".

Cleaning: Use regular expressions to clean and standardize the extracted information, removing any unnecessary whitespace or characters.

The strip() function is used to remove any leading or trailing whitespace from the extracted name.


Notes:
 1.Ensure the image is of good quality for better OCR results.
 2.Preprocessing steps like noise removal, resizing, or sharpening may improve the OCR accuracy.
 3.Adjust the regex patterns based on the exact text layout on the PAN card.
 
This script assumes a typical layout of a PAN card. You may need to tweak the preprocessing and regex patterns based on the specific format and quality of the PAN card images you are working with.















