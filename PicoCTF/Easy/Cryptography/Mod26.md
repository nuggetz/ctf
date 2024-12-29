#easy #cypher #rot13

# Mod26 Walkthrough


This challenge hints that it should be simple, as the solution is contained in the description itself:

![[Mod 26 - dash.png]]


> [!NOTE]
> **What is ROT13?**
> 
> ROT13 is a straightforward letter substitution cipher. It replaces each letter with the one 13 positions ahead in the Latin alphabet, effectively “rotating” the alphabet by 13.
> 
> For example:
> - **A → N**, **B → O**, … **M → Z**
> - And similarly: **N → A**, **O → B**, … **Z → M**
> 
> Since the Latin alphabet has 26 letters, applying ROT13 twice returns the original text.
> 
> ROT13 is a special case of the Caesar cipher, which was used by Julius Caesar in the 1st century BC to encode his messages. While ROT13 is not secure by modern cryptographic standards, it remains a fun and quick cipher to solve.


### Decoding the Challenge


**Method 1: Online Decoder**

Using any online ROT13 decoder, input the string:
cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}

The decoded result reveals the solution:

![[Mod 26 - online solution.png]]


**Method 2: Python Script**

You can also solve this challenge using Python. The codecs library makes decoding ROT13 extremely simple.

1. Open your favorite text editor or IDE and create a file named rot13_decoder.py.
2. Write the following code:

```python
import codecs

# ROT13 encoded string_
encoded = "cvpbPGS{arkg_gvzr_V'yy_gel_2_ebhaqf_bs_ebg13_nSkgmDJE}"

# Decode using codecs_
decoded = codecs.decode(encoded, 'rot_13')

# Print the result_
print("Decoded string:", decoded)
```
  
3. Run the script.


### Conclusion

ROT13 is a simple yet fun cipher to decode. While not secure for practical cryptography, it’s a great way to get started with cryptographic challenges like this one. Whether you prefer online tools or scripting, decoding ROT13 is quick and efficient!
