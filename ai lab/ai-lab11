---
layout: page
title: Pos_Tagging
permalink: /ai/lab-11/
---
```python
import nltk
text = nltk.word_tokenize('ive into NLTK: Part-of-speech tagging and POS Tagger')
pos = nltk.pos_tag(text)
print(text)
print(pos)
```
## Stemming
```python
from nltk.stem import PorterStemmer
from nltk.tokenize import word_tokenize

ps= PorterStemmer()

example_words = [" python,pythonly,phythoner,pythonly"]

for w in example_words:
    print(ps.stem(w))
```
## Stopword
```python
import nltk
from nltk.corpus import stopwords
f1 = open("file1.txt","r")
f2 = open("file2.txt","w")
stop = stopwords.words('english')
for line in f1:
    w = line.split(" ")
    for word in w:
        if word not in stop:
            f2.write(word)
            f2.write(" ")

f1.close()
f2.close()
```
