<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <style>
    body {
      font-family: Arial, sans-serif;
      line-height: 1.6;
      background: #f9f9f9;
      margin: 0;
      padding: 0 20px;
      color: #333;
    }
    h1, h2, h3 {
      color: #004080;
    }
    pre {
      background: #eee;
      padding: 10px;
      border-radius: 5px;
      overflow-x: auto;
    }
    code {
      background: #e6e6e6;
      padding: 2px 4px;
      border-radius: 3px;
    }
    .container {
      max-width: 900px;
      margin: auto;
      padding: 20px;
      background: white;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    ul {
      margin-left: 20px;
    }
    a {
      color: #0066cc;
    }
  </style>
</head>
<body>
<div class="container">
  <h1>🕵️‍♂️ Steganography Tool</h1>
  <p>A comprehensive steganography application that hides encrypted messages in images using LSB embedding, AES-256 encryption, and CRC32 data integrity checks.</p>

  <h2>🚀 Features</h2>
  <ul>
    <li>2-bit LSB embedding in images</li>
    <li>Optional AES-256 encryption for security</li>
    <li>CRC32 checksums for data integrity</li>
    <li>Web and desktop GUI interfaces</li>
    <li>Supports PNG, JPG, BMP, TIFF (PNG recommended)</li>
    <li>File size limit: 16MB (web)</li>
  </ul>

  <h2>📁 Project Structure</h2>
  <pre><code>steganography-tool/
├── app.py                 # Flask web application
├── main.py               # Web app entry
├── steganography.py      # Core engine
├── steganography_gui.py  # Desktop GUI
├── pyproject.toml        # Dependencies
├── templates/
│   ├── index.html
│   └── result.html
├── static/
│   ├── uploads/
│   └── processed/
└── README.md
</code></pre>

  <h2>⚙️ Installation</h2>
  <p>Python 3.11+ is required.</p>
  <pre><code># With uv (recommended)
uv add pillow pycryptodome numpy flask gunicorn

# Or with pip
pip install pillow pycryptodome numpy flask gunicorn
</code></pre>

  <h2>💻 Usage</h2>
  <h3>Web Application</h3>
  <pre><code>python main.py</code></pre>
  <p>Then visit <code>http://localhost:5000</code> in your browser.</p>

  <h3>Desktop GUI</h3>
  <pre><code>python steganography_gui.py</code></pre>

  <h2>🔍 How It Works</h2>
  <h3>LSB Embedding</h3>
  <p>Uses 2 bits from each RGB pixel to hide binary data with minimal visual change.</p>

  <h3>Encryption</h3>
  <ul>
    <li>AES-256 (CBC mode)</li>
    <li>Key auto-padded to 32 bytes</li>
    <li>Message header includes CRC32 and size</li>
  </ul>

  <h2>🛡️ Security Features</h2>
  <ul>
    <li>AES-256 industry-standard encryption</li>
    <li>CRC32 for integrity verification</li>
    <li>Image and key validation</li>
    <li>PNG recommended to prevent compression artifacts</li>
  </ul>

  <h2>🌐 API Endpoints (Web App)</h2>
  <ul>
    <li><code>GET /</code> - Main interface</li>
    <li><code>POST /embed</code> - Embed message</li>
    <li><code>POST /extract</code> - Extract message</li>
    <li><code>GET /download/&lt;filename&gt;</code> - Download output</li>
  </ul>

  <h2>📦 Dependencies</h2>
  <ul>
    <li>Pillow (image processing)</li>
    <li>Numpy (pixel manipulation)</li>
    <li>PyCryptodome (AES encryption)</li>
    <li>Flask (web server)</li>
    <li>Tkinter (GUI - preinstalled)</li>
    <li>Gunicorn (deployment)</li>
  </ul>

  <h2>⚠️ Limitations</h2>
  <ul>
    <li>Image must be large enough to hold data</li>
    <li>JPEG compression may corrupt data</li>
    <li>Max upload size: 16MB</li>
  </ul>

  <h2>🔐 Security Tips</h2>
  <ul>
    <li>Use strong encryption keys</li>
    <li>Keep keys separate from stego images</li>
    <li>Don't modify stego images post-embedding</li>
    <li>Use PNG to preserve bit accuracy</li>
  </ul>

  <h2>❗ Error Handling</h2>
  <ul>
    <li>Invalid files</li>
    <li>Corrupt or unsupported images</li>
    <li>Insufficient capacity</li>
    <li>Wrong decryption keys</li>
    <li>Data integrity failures</li>
  </ul>

  <h2>🔧 Example</h2>
  <h3>To Hide a Message</h3>
  <ol>
    <li>Choose a high-res image</li>
    <li>Enter your secret message</li>
    <li>Set an encryption key (optional)</li>
    <li>Download the output image</li>
  </ol>

  <h3>To Reveal a Message</h3>
  <ol>
    <li>Upload the stego image</li>
    <li>Enter the correct decryption key</li>
    <li>Read the hidden message</li>
  </ol>

  <h2>📜 License</h2>
  <p>This project is <strong>open-source</strong> and available under the <a href="https://opensource.org/licenses/MIT" target="_blank">MIT License</a>.</p>
</div>
</body>
</html>
