---
layout: page
title: Convert given plaintext to ciphertext using Railfence Transposition.
permalink: /ias/lab-3/
---
```python
def encrypt(layers, plain_text):
    # remove all white spaces in text
    plain_text = plain_text.replace(" ", "")

    # change plain text to upper case
    plain_text = plain_text.upper()

    # divide plain text into layers number of strings
    rail = [""] * layers
    layer = 0
    for character in plain_text:
        rail[layer] += character
        if layer >= layers - 1:
            layer = 0
        else:
            layer += 1

    cipher = "".join(rail)
    return cipher

# get the number of layers to rail encrypt
layers = int(input("Enter the number of layers: "))
# get the plain text
plain_text = raw_input("Enter the plain text: ")
# encrypt the plain text
cipher_text = encrypt(layers, plain_text)
print("Encrypted text: " + cipher_text)
```

## Convert given plaintext to Ciphertext using Columnar Transposition.

```python
import string
keystring = raw_input('keyword please: ')
keylist = list(string.upper(keystring))
seqlist = []
idxlist = []
messagestring = raw_input('message please: ')
messagelist = list(string.upper(messagestring))
print ' '

def unstray(listinput):
    for stray in listinput:
        if stray not in string.uppercase:
            listinput.remove(stray)

def keysequence(alphakey):
    for letter in range(len(string.uppercase)):
        for item in range(len(alphakey)):
            if string.uppercase[letter] == alphakey[item]:
                   seqlist.append(item)

def transpose(keyseq, message):
    for number in range(len(keyseq)):
        for letter in range(keyseq[number], len(message), len(keyseq)):
            idxlist.append(message[letter])

def telegraph(result):
    for number in range(len(result)):
        print result[number],

def encipher():
    unstray(keylist)
    unstray(messagelist)
    keysequence(keylist)
    transpose(seqlist, messagelist)
    telegraph(idxlist)

encipher()
```
