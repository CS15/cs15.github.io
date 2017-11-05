---
layout: page
title: Python program for AES Operations.
permalink: /ias/lab-6/
---
```python
key="0100101011110101"
rc1="10000000"
rc2="00110000"
plaintext="1101011100101000"
def rotate(key,right_key):
    left_key_rot=left_key[1:] + left_key[:1]
    right_key_rot=right_key[1:] + right_key[:1]
    key_rot=left_key_rot+right_key_rot
    return permutation(P8,key_rot)
def Sbox(input):
	if input=="0000":
   			z="1001"
	elif input=="0001":
   			z="0100"
	elif input=="0010":
   			z="1010"
	elif input=="0011":
   			z="1011"
	elif input=="0100":
			z="1101"
	elif input=="0101":
			z="0001"
	elif input=="0110":
			z="1000"
	elif input=="0110":
			z="0101"
	elif input=="1000":
   			z="0110"
	elif input=="1001":
   			z="0010"
	elif input=="1010":
   			z="0000"
	elif input=="1011":
			z="0011"
	elif input=="1100":
			z="1100"
	elif input=="1101":
			z="1110"
	elif input=="1110":
			z="1111"
	else:
   			z="0111"
	return z
def F(right,subkey):
    expanded_cipher=permutation(E,right)
    xor_cipher=bin(int(expanded_cipher,2)^int(subkey,2) )[2:].zfill(8)
    left_xor_cipher=xor_cipher[:4]
    right_xor_cipher=xor_cipher[4:]
    left_sbox_cipher=Sbox(left_xor_cipher,S0)
    right_sbox_cipher=Sbox(right_xor_cipher,S1)
    return permutation(P4,left_sbox_cipher+right_sbox_cipher)
def xor(x,y):
	z=int(x)^int(y)
	return z
w0= key[:len(key)//2]
w1 = key[len(key)//2:]
print("w0= ",w0)
print("w1= ",w1)
word_1_left= w1[:len(w1)//2]
word_1_right= w1[len(w1)//2:]
rotated=word_1_right+word_1_left
print("w1 after rotation= ",rotated)
left_for_substitution=rotated[:len(rotated)//2]
right_for_substitution=rotated[len(rotated)//2:]
left_substituted=Sbox(left_for_substitution)
right_substituted=Sbox(right_for_substitution)
substituted=left_substituted+right_substituted
print ("w1 after substitution= ",substituted)
xored_result=bin(int(substituted,2)^int(rc1,2) )[2:].zfill(8)
print ("w1 after xor with round constant= ",xored_result)
w2=bin(int(xored_result,2)^int(w0,2) )[2:].zfill(8)
print ("w2= ",w2)
w3=bin(int(w2,2)^int(w1,2) )[2:].zfill(8)
print ("w3= ",w3)
word_3_left= w3[:len(w3)//2]
word_3_right= w3[len(w3)//2:]
rotated3=word_3_right+word_3_left
print ("rotated3= ",rotated3)
left3_for_substitution=rotated3[:len(rotated3)//2]
right3_for_substitution=rotated3[len(rotated3)//2:]
left3_substituted=Sbox(left3_for_substitution)
right3_substituted=Sbox(right3_for_substitution)
substituted3=left3_substituted+right3_substituted
print( "substituted3= ",substituted3)
xored3_result=bin(int(substituted3,2)^int(rc2,2) )[2:].zfill(8)
print ("w3 after xor with round  constant 2= ",xored3_result)
w4=bin(int(xored3_result,2)^int(w2,2) )[2:].zfill(8)
print ("w4= ",w4)
w5=bin(int(w3,2)^int(w4,2) )[2:].zfill(8)
print ("w5= ",w5)
key0=w0+w1
key1=w2+w3
key2=w4+w5
print ("Key 0= ",key0)
print ("Key 1= ",key1)
print ("Key 2= ",key2)
print ("ENCRYPTION")
print ("ROUND 0")
round0=bin(int(key0,2)^int(plaintext,2) )[2:].zfill(16)
print ("Result after adding round 0 Key: ", round0)
print ("ROUND 1")
print ("NIBBLE SUBSTITUTION")
lft1=round0[0:4]
print (lft1)
lft2=round0[4:8]
print (lft2)
lft3=round0[8:12]
print (lft3)
lft4=round0[12:16]
print (lft4)
rht1=Sbox(lft1)
rht2=Sbox(lft2)
rht3=Sbox(lft3)
rht4=Sbox(lft4)
r1_substitution=rht1+rht2+rht3+rht4
print ("Round1 result after substitution is= ",r1_substitution)
r1_shift=rht1+rht4+rht3+rht2
print ("Round1 result after shifting rows= ",r1_shift)
```
