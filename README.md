Hex String Flattening
This repository contains a utility function for converting a byte array in hexadecimal format from a detailed representation (e.g., [0x00][0x00][0x00][0x00][0x00][0x00][0x03][0x94][0x8E][0x0B]) to a compressed hex string representation (00000000000003948E0B). This function is particularly useful for reconstructing Codec messages from Teltonika devices.

Overview
The Hex String Flattening function is designed to take a series of bytes, each represented as 0xXX, and convert them into a continuous hexadecimal string without any separators or prefixes. When parsing Codec messages from Teltonika devices, the raw message is often in the detailed format with 0x prefixes. In this format, the data cannot be easily parsed, so flattening it into a compact hex string is necessary for proper message reconstruction.

Example
Input:
plaintext
Copy code
[0x00][0x00][0x00][0x00][0x00][0x00][0x03][0x94][0x8E][0x0B]
Output:
plaintext
Copy code
00000000000003948E0B
Features
Converts a hexadecimal byte array to a string without 0x prefixes and square brackets.
Essential for reconstructing Codec messages from Teltonika devices.
Makes the data in a compact format, which is easier to parse and process.
Easy integration into Teltonika device message parsing workflows.
Usage
Installation
Clone the repository:

bash
Copy code
git clone https://github.com/yourusername/hex-string-flattening.git
Navigate to the project directory:

bash
Copy code
cd hex-string-flattening
Install dependencies (if necessary).

Example Code
Here is an example of how to use the Hex String Flattening function in your project to reconstruct a Codec message:

python
Copy code
def flatten_hex_string(hex_list):
    # Converts a list of hex bytes like [0x00, 0x00, 0x03, 0x94] to '0000000394'
    return ''.join(format(byte, '02X') for byte in hex_list)

# Example input from Teltonika device Codec message (in detailed format)
hex_bytes = [0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x03, 0x94, 0x8E, 0x0B]

# Flatten the hex string to reconstruct the message
flattened = flatten_hex_string(hex_bytes)

# Output result (this would be the format needed for parsing)
print(flattened)  # Output: 00000000000003948E0B
Why This is Important
Teltonika devices often send data in a detailed hexadecimal format like [0x00][0x00][0x00][0x00][0x00][0x00][0x03][0x94][0x8E][0x0B]. However, when reconstructing Codec messages for parsing, the data needs to be in a compact format, such as 00000000000003948E0B. This function allows you to transform the raw data into the correct format for easier message reconstruction and decoding.
