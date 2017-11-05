---
layout: page
title: Program to implement AES key generation.
permalink: /ias/lab-5/
---
```python
import numpy as np
keyfinal = []
sBox = [['0x63', '0x7c', '0x77', '0x7b', '0xf2', '0x6b', '0x6f', '0xc5','0x30', '0x01', '0x67', '0x2b', '0xfe', '0xd7', '0xab', '0x76'],['0xca', '0x82', '0xc9', '0x7d', '0xfa', '0x59', '0x47', '0xf0','0xad', '0xd4', '0xa2', '0xaf', '0x9c', '0xa4', '0x72','0xc0']
    ,['0xb7', '0xfd', '0x93', '0x26', '0x36', '0x3f', '0xf7', '0xcc','0x34', '0xa5', '0xe5', '0xf1', '0x71', '0xd8', '0x31', '0x15']
    ,['0x04', '0xc7', '0x23', '0xc3', '0x18', '0x96', '0x05', '0x9a','0x07', '0x12', '0x80', '0xe2', '0xeb', '0x27', '0xb2', '0x75']
    ,['0x09', '0x83', '0x2c', '0x1a','0x1b', '0x6e', '0x5a', '0xa0','0x52', '0x3b', '0xd6', '0xb3', '0x29', '0xe3', '0x2f', '0x84']
    ,['0x53', '0xd1', '0x00', '0xed','0x20', '0xfc', '0xb1', '0x5b','0x6a', '0xcb', '0xbe', '0x39', '0x4a', '0x4c', '0x58', '0xcf']
    ,['0xd0', '0xef', '0xaa', '0xfb', '0x43','0x4d', '0x33', '0x85', '0x45', '0xf9', '0x02', '0x7f', '0x50', '0x3c', '0x9f', '0xa8']
    ,['0x51', '0xa3', '0x40', '0x8f', '0x92', '0x9d', '0x38','0xf5','0xbc', '0xb6', '0xda', '0x21', '0x10', '0xff', '0xf3', '0xd2']
    ,['0xcd', '0x0c', '0x13', '0xec', '0x5f', '0x97', '0x44', '0x17','0xc4', '0xa7', '0x7e', '0x3d','0x64', '0x5d', '0x19', '0x73']
    ,['0x60', '0x81', '0x4f', '0xdc', '0x22', '0x2a', '0x90', '0x88','0x46', '0xee', '0xb8', '0x14', '0xde', '0x5e', '0x0b', '0xdb']
    ,['0xe0', '0x32', '0x3a', '0x0a', '0x49', '0x06', '0x24', '0x5c','0xc2', '0xd3', '0xac', '0x62', '0x91', '0x95', '0xe4', '0x79']
    ,['0xe7', '0xc8', '0x37', '0x6d','0x8d', '0xd5', '0x4e', '0xa9','0x6c', '0x56', '0xf4', '0xea', '0x65', '0x7a', '0xae', '0x08']
    ,['0xba', '0x78', '0x25', '0x2e', '0x1c', '0xa6', '0xb4', '0xc6','0xe8', '0xdd', '0x74', '0x1f', '0x4b', '0xbd', '0x8b', '0x8a']
    ,['0x70','0x3e', '0xb5', '0x66', '0x48', '0x03', '0xf6', '0x0e',  '0x61', '0x35','0x57', '0xb9', '0x86', '0xc1', '0x1d', '0x9e']
    ,['0xe1', '0xf8', '0x98', '0x11', '0x69', '0xd9', '0x8e', '0x94', '0x9b', '0x1e', '0x87', '0xe9', '0xce', '0x55', '0x28', '0xdf'],['0x8c', '0xa1', '0x89', '0x0d', '0xbf', '0xe6', '0x42', '0x68', '0x41', '0x99', '0x2d', '0x0f', '0xb0', '0x54', '0xbb', '0x16']]
num = {'0':0,'1':1,'2':2,'3':3,'4':4,'5':5,'6':6,'7':7,'8':8,'9':9,'a':10,'b':11,'c':12,'d':13,'e':14,'f':15}
anum = {0:'0',1:'1',2:'2',3:'3',4:'4',5:'5',6:'6',7:'7',8:'8',9:'9',10:'a',11:'b',12:'c',13:'d',14:'e',15:'f'}
xnum = {'0':'0000','1':'0001','2':'0010','3':'0011','4':'0100','5':'0101','6':'0110','7':'0111','8':'1000','9':'1001','a':'1010','b':'1011','c':'1100','d':'1101','e':'1110','f':'1111'}
rcon = [[[0,0,0,0],[0,0,0,1],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]],[[0,0,0,0],[0,0,1,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
 ,[[0,0,0,0],[0,1,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
 , [[0,0,0,0],[1,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
,[[0,0,0,1],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
,[[0,0,1,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
, [[0,1,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
, [[1,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
, [[0,0,0,1],[1,0,1,1],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]
, [[0,0,1,1],[0,1,1,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0],[0,0,0,0]]]
def rotate(l, n):
    return l[n:] + l[:n]
k = input("Enter Your Key: ")
if len(k) !=16:
    print("you entered the string length less than 16")
    exit(0)
v = [None]*len(k)
for  i in range(len(k)):
   v[i] = str(hex(ord(k[i]))[2:])
v1 = []
v1.append(v[0:4])
v1.append(v[4:8])
v1.append(v[8:12])
v1.append(v[12:16])
for l in range(10):
    v4r = rotate(v1[3],1)
    v4a = [None]*4
    final = []
    for i in range(4):
        temp = v4r[i]
        temp1 = sBox[num[temp[0]]][num[temp[1]]]
        v4a[i] = str(temp1[2:])
    temp = v4a[0]
    s = ''
    s1= ''
    results = list(map(int, list(xnum[temp[0]])))
    plainep = np.array(results)
    key1 = np.array(rcon[l][0])
    plaink1 = plainep ^ key1
    plaink1 = plaink1.tolist()
    str1 = ''.join(str(e) for e in plaink1)
    val = int(str1,2)
    s = anum[val]
    temp12 = s + temp[1]
    temp = temp12
    results = list(map(int, list(xnum[temp[1]])))
    plainep = np.array(results)
    key1 = np.array(rcon[l][1])
    plaink1 = plainep ^ key1
    plaink1 = plaink1.tolist()
    str1 = ''.join(str(e) for e in plaink1)
    val = int(str1,2)
    s1 = anum[val]
    temp11 = temp[0]+s1
    v4a[0] = ''
    v4a[0]+=temp11
    for k in range(4):
        vt = [None]*4
        for i in range(4):
            imp = ''
            temp = v4a[i]
            temp1 = v1[k][i]
            for j in range(2):
                results = list(map(int, list(xnum[temp[j]])))
                results1 = list(map(int, list(xnum[temp1[j]])))
                plainep = np.array(results)
                key1 = np.array(results1)
                plaink1 = plainep ^ key1
                plaink1 = plaink1.tolist()
                str1 = ''.join(str(e) for e in plaink1)
                val = int(str1, 2)
                imp+= list(num.keys())[list(num.values()).index(val)]
            vt[i] = imp
        v4a = vt
        final.append(vt)
    v1 = final
    keyfinal.append(v1)
for i in range(10):
    print("KEY ",i+1,"  ",keyfinal[i])
```


