#easy #reverse-engineering

# Transformation Walkthrough

<img width="488" alt="Transformation - dash" src="https://github.com/user-attachments/assets/0177f536-f793-42a5-b1a1-97020a1cbdb8" />


This challenge provides a file enc containing the Unicode string:
```
灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸強㕤㐸㤸扽
```

The description gives a critical clue about the encoding mechanism used:
```python
''.join([chr((ord(flag[i]) << 8) + ord(flag[i + 1])) for i in range(0, len(flag), 2)])
```

This snippet hints at how the string was generated. Our task is to reverse the process and retrieve the original flag.

The simple and easy way to obtain the flag is to use an online tool:

<img width="1212" alt="Transformation - solution" src="https://github.com/user-attachments/assets/0678f850-2c74-4f75-b4e0-76b080c1fde2" />


### 1. Understanding the Encoding Mechanism

The provided Python snippet works as follows:
1. **Pairs of Characters:** The original flag is split into pairs of two characters.
2. **Bitwise Shift and Addition:**
	- For each pair, the Unicode code point of the first character is shifted left by 8 bits (ord(flag[i]) << 8).
	- The Unicode code point of the second character is added to this shifted value (ord(flag[i + 1]))
3. **Conversion to Unicode:** The resulting value is converted into a single Unicode character with chr().

This encoding process effectively merges two ASCII characters into one Unicode character.


### 2. Reversing the Process

To decode the string, we reverse the steps:

1. For each Unicode character in the string:
	- Retrieve its code point using ord().
	- Extract the **high byte** (first ASCII character) using (code_point >> 8).
	- Extract the **low byte** (second ASCII character) using (code_point & 0xFF).
2. Convert these bytes back to ASCII characters using chr().
3. Combine all characters to reconstruct the flag.


### 3. Python Script to Decode the Flag

Here’s the Python code to reverse the encoding and decode the string:

```python
# Encoded string from the file `enc`
encoded = "灩捯䍔䙻ㄶ形楴獟楮獴㌴摟潦弸強㕤㐸㤸扽"

# Function to decode the string
def decode_flag(encoded):
    decoded = ""
    for char in encoded:
        # Get the Unicode code point
        code_point = ord(char)
        # Extract the high and low bytes
        high_byte = (code_point >> 8) & 0xFF
        low_byte = code_point & 0xFF
        # Convert bytes to characters and append
        decoded += chr(high_byte) + chr(low_byte)
    return decoded

# Decode the string
decoded_flag = decode_flag(encoded)

# Print the decoded flag
print("Decoded flag:", decoded_flag)
```


### 4. Key Takeaways

1. **Encoding Mechanism:**
	- The challenge used a method of combining two ASCII characters into one Unicode character via bitwise operations.
	- Specifically: (ord(char1) << 8) + ord(char2).
2. **Reversing the Process:**
	- Extract the high and low bytes from the Unicode code point to recover the original ASCII characters.
3. **Python Tools for Decoding:**
	- ord(char): Returns the Unicode code point of a character.
	- chr(int): Converts a code point back into a character.
	- Bitwise operations (>> and &) are key for splitting the code point.


### 5. General Usefulness of This Encoding


This encoding technique is simple and efficient for combining two characters into one, making it useful for obfuscation. Recognizing and reversing such patterns is a critical skill in solving CTF challenges, as many rely on custom or simple encoding schemes.

Now, you’ve successfully decoded the flag while understanding the exact process behind it!
