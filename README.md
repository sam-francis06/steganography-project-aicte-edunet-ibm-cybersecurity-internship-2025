# Image Steganography Tool

## Overview
This project provides a Python-based tool for performing image steganography, enabling users to hide secret messages within PNG images and retrieve them using a password-protected mechanism. The tool consists of two scripts: `encrypt.py` for embedding messages into images and `decrypt.py` for extracting hidden messages.

## Features
- **Message Embedding**: Hide text messages in PNG images using least significant bit (LSB) steganography.
- **Password Protection**: Secure the hidden message with a password, stored in a separate file.
- **End Marker**: Uses a unique bit sequence (`1111111111111110`) to mark the end of the hidden message.
- **Error Handling**: Validates image size, file existence, and password correctness.

## Prerequisites
- **Python 3.x**: Ensure Python is installed on your system.
- **OpenCV**: Install the OpenCV library using:
  ```bash
  pip install opencv-python
  ```
- **Operating System**: The `encrypt.py` script uses `os.system("start encrypted_Image.png")`, which is specific to Windows. For other operating systems, modify this command (e.g., use `open` for macOS or `xdg-open` for Linux).

## Installation
1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/sam-francis06/steganography-project-aicte-edunet-ibm-cybersecurity-internship-2025.git
   ```
2. Navigate to the project directory:
   ```bash
   cd steganography-project-aicte-edunet-ibm-cybersecurity-internship-2025
   ```
3. Install the required dependencies:
   ```bash
   pip install opencv-python
   ```

## Usage

### Encrypting a Message
1. Run the `encrypt.py` script:
   ```bash
   python encrypt.py
   ```
2. Enter the path to a PNG image file when prompted.
3. Input the secret message to hide in the image.
4. Provide a password to secure the message.
5. The script will:
   - Embed the message in the image using LSB steganography.
   - Save the password to `password.txt`.
   - Save the message length to `msg_length.txt`.
   - Output an encrypted image as `encrypted_Image.png`.
   - Open the encrypted image (Windows only).

### Decrypting a Message
1. Run the `decrypt.py` script:
   ```bash
   python decrypt.py
   ```
2. Enter the path to the encrypted PNG image (`encrypted_Image.png`).
3. Input the password used during encryption.
4. If the password matches the one in `password.txt`, the script will:
   - Extract the hidden message from the image.
   - Display the decrypted message.
5. If the password is incorrect, an authentication error will be displayed.

## Files
- **encrypt.py**: Script to embed a secret message into a PNG image.
- **decrypt.py**: Script to extract and display the hidden message from an encrypted PNG image.
- **password.txt**: Stores the password used for encryption (generated automatically).
- **msg_length.txt**: Stores the length of the secret message (generated automatically).
- **encrypted_Image.png**: The output image containing the hidden message (generated automatically).

## Limitations
- The image must be in PNG format and large enough to store the message (height × width × 3 bits).
- The `os.system("start encrypted_Image.png")` command is Windows-specific. Modify for other operating systems if needed.
- The password and message length are stored in plain text files (`password.txt` and `msg_length.txt`), which may pose a security risk in shared environments.
- The tool assumes UTF-8 encoding for messages and may not handle all character sets correctly.

## Example
### Encryption
```bash
$ python encrypt.py
Enter the image file path: sample.png
Enter your secret message: Hello, this is a secret!
Enter a password: mypassword
Image Encrypted Successful.
```
Output: `encrypted_Image.png`, `password.txt`, and `msg_length.txt` are created.

### Decryption
```bash
$ python decrypt.py
Enter the encrypted image file path in PNG format: encrypted_Image.png
Enter password for Decryption: mypassword
Decryption message: Hello, this is a secret!
```

## Security Considerations
- The LSB steganography method is basic and may be detectable by advanced image analysis techniques.
- Store `password.txt` and `msg_length.txt` securely, as they contain sensitive information.
- Consider encrypting the password file or using a more secure storage mechanism for production use.

## Contributing
Contributions are welcome! Please submit a pull request or open an issue on GitHub to suggest improvements or report bugs.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact
For questions or support, please open an issue on the GitHub repository or contact the maintainer at francissamuvel06@gmail.com .
