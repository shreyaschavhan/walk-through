`Link` : `https://overthewire.org/wargames/bandit/bandit11.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟏𝟎 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟏
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in the file data.txt, which contains base64 encoded data

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- `ls`
- `cat data.txt`
- `base64 -d data.txt`

```
bandit10@bandit:~$ ls
data.txt
bandit10@bandit:~$ cat data.txt
VGhlIHBhc3N3b3JkIGlzIElGdWt3S0dzRlc4TU9xM0lSRnFyeEUxaHhUTkViVVBSCg==
bandit10@bandit:~$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
bandit10@bandit:~$ 

```
