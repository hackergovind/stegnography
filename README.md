# stegnography

STEGANOGRAPHY
A comprehensive steganography application that allows you to hide encrypted messages in images using LSB (Least Significant Bit) embedding with AES-256 encryption and CRC32 data integrity checks.

Features
LSB Steganography: Hide messages in image pixels using 2-bit LSB embedding
AES-256 Encryption: Optional encryption for maximum security
Data Integrity: CRC32 checksums to verify data hasn't been corrupted
Multiple Interfaces: Both web application and desktop GUI
Support for Multiple Formats: PNG, JPG, JPEG, BMP, TIFF
File Size Limit: Up to 16MB for web uploads
Project Structure
steganography-tool/
├── app.py                 # Flask web application
├── main.py               # Main entry point for web app
├── steganography.py      # Core steganography engine
├── steganography_gui.py  # Desktop GUI application
├── pyproject.toml        # Project dependencies
├── templates/
│   ├── index.html        # Web interface home page
│   └── result.html       # Results display page
├── static/
│   ├── uploads/          # Temporary upload folder
│   └── processed/        # Processed images folder
└── README.md            # This file
Installation
Install Python 3.11+

Install dependencies using uv (recommended) or pip:

# Using uv
uv add pillow pycryptodome numpy flask gunicorn

# Or using pip
pip install pillow pycryptodome numpy flask gunicorn
Usage
Web Application
Start the web server:

python main.py
Open your browser and navigate to:

Use the interface to:

Hide Message: Upload an image, enter your secret message, optionally set an encryption key
Reveal Message: Upload a steganographic image, enter decryption key if used
Desktop GUI Application
Run the GUI application:

python steganography_gui.py
Use the tabbed interface:

Hide Message Tab: Select cover image, enter message, set encryption key, choose output location
Reveal Message Tab: Select steganographic image, enter decryption key, view extracted message
How It Works
LSB Steganography
The tool uses Least Significant Bit embedding to hide data in image pixels. Each pixel channel (R, G, B) can store 2 bits of data in its least significant bits without causing visible changes to the image.

Encryption Process
Message is encrypted using AES-256 in CBC mode (if key provided)
A header containing message size and CRC32 checksum is created
Data is converted to binary and embedded in image pixels using LSB
Modified image is saved as PNG to preserve data integrity
Extraction Process
LSB data is extracted from image pixels
Header is parsed to get message size and expected checksum
Data integrity is verified using CRC32
Message is decrypted if encryption key is provided
Security Features
AES-256 Encryption: Industry-standard encryption for message protection
CRC32 Checksums: Detects data corruption or tampering
Key Padding: Automatic key padding/truncation to 32 bytes for AES-256
File Validation: Ensures uploaded files are valid images
API Endpoints (Web App)
GET / - Main interface
POST /embed - Hide message in image
POST /extract - Extract message from image
GET /download/<filename> - Download steganographic image
Dependencies
PIL (Pillow): Image processing
numpy: Array operations for pixel manipulation
pycryptodome: AES encryption and cryptographic functions
Flask: Web framework (for web app)
tkinter: GUI framework (for desktop app, included with Python)
gunicorn: WSGI server for production deployment
Supported Image Formats
PNG (recommended for steganographic images)
JPEG/JPG
BMP
TIFF
Note: PNG is recommended for output as it preserves data without compression artifacts.

Limitations
Image must be large enough to hold the message data
Compressed formats (JPEG) may cause data loss
Maximum file size: 16MB (web interface)
Security Considerations
Use strong encryption keys for sensitive messages
Keep decryption keys secure and separate from steganographic images
Avoid editing or compressing steganographic images
Use PNG format to prevent compression artifacts
Error Handling
The application includes comprehensive error handling for:

Invalid file formats
Corrupted images
Insufficient image capacity
Wrong decryption keys
Data corruption detection
Example Usage
Hiding a Message
Select a cover image (preferably high resolution)
Enter your secret message
Optionally set an encryption key for security
Generate steganographic image
Download and share the steganographic image
Revealing a Message
Upload the steganographic image
Enter the decryption key (if message was encrypted)
Extract and view the hidden message
License
This project is open source and available under the MIT License.
