#easy #cypher #caesar #base64

# interencdec Walkthrough


<img width="509" alt="interencdec - dash" src="https://github.com/user-attachments/assets/6ca6312d-015f-4e38-b7c1-5b5a7422852a" />


This challenge revolves around cryptography and comes with a file to download.
Upon examining the file with a simple cat, we see the following base64 encoded string:
```
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg==.
```

<img width="722" alt="interencdec - cat encoding" src="https://github.com/user-attachments/assets/89021cf0-d01b-4c7f-8d11-b3bc8481b5b5" />


### Step 1: Base64 Decoding

This appears to be a base64 encoded string. There are several methods to decode it.


**Method 1: Python Script**

1. Open your preferred text editor or IDE (e.g., VSCode) and create a new file named interencdec.py.
2. Inside the file, write the following Python code:
```python
import base64

encoded = "YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6YzRNalV3YUcxcWZRPT0nCg=="
decoded = base64.b64decode(encoded).decode('utf-8')
print(decoded)
```

3. Running the script will output: `b'd3BqdkpBTXtaHlfazNqeTl3YTNrXzc4MjUwY3UwYU1qUw=='`.

<img width="637" alt="interencdec - first encription" src="https://github.com/user-attachments/assets/204c920a-cae9-4a28-984c-12eafc6dfbc0" />


This suggests that the file is double nested base64 encoded. Let’s decode it again.


### Step 2: Double Nested Base64 Decoding

1. Pass the resulting base64 string d3BqdkpBTXtaHlfazNqeTl3YTNrXzc4MjUwY3UwYU1qUw== through the decoder again.
2. We get:
	wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj}.

<img width="467" alt="interencdec - second encription" src="https://github.com/user-attachments/assets/b68fc80e-4d0f-4072-823c-be7ab7ef3f70" />


This output matches the standard PicoCTF flag format (wpjvJAM{...}). From the challenge dashboard, we can spot the tag “caesar”, suggesting a Caesar cipher.


### Step 3: Caesar Cipher Decryption

To decrypt the message, we can either:

1. Manually shift through each key or
2. Use an online Caesar cipher tool to decrypt.

Using a Caesar cipher site, input wpjvJAM{jhlzhy_k3jy9wa3k_78250hmj} and adjust the shift key. By scrolling through the possible keys, we reach key 19 and clearly read the flag:

wpjvJAM{flag_here}.

<img width="1501" alt="interencdec - caesar encription" src="https://github.com/user-attachments/assets/a1a91cee-c54f-430d-a5fd-a54275f231fc" />


Alternatively, another method involves using an online base64 decoder to decrypt the initial nested base64 string.

<img width="498" alt="interencdec - cypher2" src="https://github.com/user-attachments/assets/d74b1cd9-91ed-4039-8688-eb46e95f2e84" />

<img width="308" alt="interencdec - cypher2 2" src="https://github.com/user-attachments/assets/c0ec2a44-a2f4-4698-86bf-7216257f669e" />
