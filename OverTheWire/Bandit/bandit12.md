`Link` : `https://overthewire.org/wargames/bandit/bandit12.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟏𝟏 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟐
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in the file `data.txt`, where all `lowercase (a-z)` and `uppercase (A-Z)` letters have been `rotated by 13 positions`

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧
- `cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' `

```
bandit11@bandit:~$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m' 
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
bandit11@bandit:~$ 

```
