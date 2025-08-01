PASSWORD 1 : 
PASSWORD 2 :
  ` import hashlib

qwerty_map = {
    'a': 's', 'b': 'n', 'c': 'v', 'd': 'f', 'e': 'r', 'f': 'g', 'g': 'h', 'h': 'j',
    'i': 'o', 'j': 'k', 'k': 'l', 'l': ';', 'm': ',', 'n': 'm', 'o': 'p', 'p': '[',
    'q': 'w', 'r': 't', 's': 'd', 't': 'y', 'u': 'i', 'v': 'b', 'w': 'e', 'x': 'c',
    'y': 'u', 'z': 'x',
    '1': '2', '2': '3', '3': '4', '4': '5', '5': '6', '6': '7', '7': '8', '8': '9', '9': '0', '0': '-'
}

def caesar(text, shift):
    shifted = ''
    for c in text:
        if 'a' <= c <= 'z':
            shifted += chr((ord(c) - ord('a') + shift) % 26 + ord('a'))
        else:
            shifted += c
    return shifted

def qwerty_shift(text):
    return ''.join(qwerty_map.get(c, c) for c in text)

def transform(word, shift):
    word = word.lower()
    word = caesar(word, shift)
    word = qwerty_shift(word)
    word = word[::-1]  
    return word

target_hash = "cd6e58d947e2f7ace23cb6d602daa1ae46934c3c1f4800bfd25e6af2b555f6f5"

with open("rockyou.txt", encoding='latin1') as f:
    for line in f:
        pwd = line.strip()
        for shift in range(1, 26):  
            transformed = transform(pwd, shift)
            hashed = hashlib.sha256(transformed.encode()).hexdigest()
            if hashed == target_hash:
                print(f" Found! Original: {pwd}, Shift: {shift}, Final: {transformed}")
                exit()
` 

PASSWORD 3 : 
with hashcat : 
