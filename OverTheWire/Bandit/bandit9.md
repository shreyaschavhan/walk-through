`Link` : `https://overthewire.org/wargames/bandit/bandit9.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟖 - 𝐋𝐞𝐯𝐞𝐥 𝟗
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in the file `data.txt` and is the only line of text that occurs only once

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- sort data.txt | uniq -u

```
bandit8@bandit:~$ 
bandit8@bandit:~$ sort data.txt | uniq -u
UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
bandit8@bandit:~$ 
```
