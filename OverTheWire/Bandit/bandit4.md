`Link` : `https://overthewire.org/wargames/bandit/bandit4.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟑 - 𝐋𝐞𝐯𝐞𝐥 𝟒
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in a hidden file in the `inhere` directory.

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- `ls`
- `cd inhere`
- `ls -la`
- `cat .hidden`

```

bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cat inhere/
cat: inhere/: Is a directory
bandit3@bandit:~$ cd inhere/
bandit3@bandit:~/inhere$ ls -la
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
bandit3@bandit:~/inhere$ cat .hidden 
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
bandit3@bandit:~/inhere$ exit
logout
Connection to bandit.labs.overthewire.org closed.
                                                    
```
