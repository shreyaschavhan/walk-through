`Link` : `https://overthewire.org/wargames/bandit/bandit3.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟐 - 𝐋𝐞𝐯𝐞𝐥 𝟑
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in a file called spaces in this filename located in the home directory

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- `ls`
- `cat spaces\ in\ this\ filename`

```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat spaces\ in\ this\ filename 
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
bandit2@bandit:~$ exit
logout
Connection to bandit.labs.overthewire.org closed.

```
