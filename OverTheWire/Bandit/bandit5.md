`Link` : `https://overthewire.org/wargames/bandit/bandit5.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟒 - 𝐋𝐞𝐯𝐞𝐥 𝟓
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in the only human-readable file in the `inhere` directory. Tip: if your terminal is messed up, try the “reset” command.

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- `ls`
- `cd inhere`
- `ls`
- ` cat ./-file07`

```
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere/
bandit4@bandit:~/inhere$ ls
-file00  -file02  -file04  -file06  -file08
-file01  -file03  -file05  -file07  -file09
bandit4@bandit:~/inhere$ ls -la
total 48
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file00
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file01
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file02
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file03
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file04
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file05
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file06
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file07
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file08
-rw-r----- 1 bandit5 bandit4   33 May  7  2020 -file09
bandit4@bandit:~/inhere$ cat ./-file00
�/`2ғ�%��rL~5�g��� �����bandit4@bandit:~/inhere$ cat ./-file01
��p,k�;��r*��   �.!��C��J       �dx,�bandit4@bandit:~/inhere$ cat ./-file02
e�)�#��5��
          ��p��V�_���ׯ�mmbandit4@bandit:~/inhere$ cat ./-file03
������h!TQO�`�4"aל�߂phT��,�Abandit4@bandit:~/inhere$ cat ./-file04
?�bandit4@bandit:~/inhere$ cat ./-file05
�r�l$�?h�9('���!y�e�#�x�O��=��bandit4@bandit:~/inhere$ cat ./-file06
ly���~��A�f����-E�{���m�����ܗMbandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh
bandit4@bandit:~/inhere$ cat ./-file08
�T�?�i��j���îP�F�l�n��J����{��@bandit4@bandit:~/inhere$ 

```
