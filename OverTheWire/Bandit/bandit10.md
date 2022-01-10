`Link` : `https://overthewire.org/wargames/bandit/bandit10.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟗 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟎
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in the file `data.txt` in one of the few human-readable strings, preceded by several ‘=’ characters.

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- `strings data.txt | grep =`

```
bandit9@bandit:~$ strings data.txt | grep =
========== the*2i"4
=:G e
========== password
<I=zsGi
Z)========== is
A=|t&E
Zdb=
c^ LAh=3G
*SF=s
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
S=A.H&^
bandit9@bandit:~$ 

```
