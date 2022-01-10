`Link` : `https://overthewire.org/wargames/bandit/bandit6.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟓 - 𝐋𝐞𝐯𝐞𝐥 𝟔
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:
> - human-readable
> - 1033 bytes in size
> - not executable

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

- Code:
```
for ((i=0; i < 10; i++)); do 
	cd /home/bandit5/inhere/maybehere0$i
	pwd
	ls -la | grep rw-r
done

```

- Output:
```
bandit5@bandit:~/inhere/maybehere09$ 
bandit5@bandit:~/inhere/maybehere09$ for ((i=0; i < 10; i++)); do 
> cd /home/bandit5/inhere/maybehere0$i
> pwd
> ls -la | grep rw-r
> done
/home/bandit5/inhere/maybehere00
-rw-r-----  1 root bandit5 9388 May  7  2020 -file2
-rw-r-----  1 root bandit5 7836 May  7  2020 .file2
-rw-r-----  1 root bandit5 6850 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere01
-rw-r-----  1 root bandit5  288 May  7  2020 -file2
-rw-r-----  1 root bandit5 3070 May  7  2020 .file2
-rw-r-----  1 root bandit5 4543 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere02
-rw-r-----  1 root bandit5 3511 May  7  2020 -file2
-rw-r-----  1 root bandit5 2577 May  7  2020 .file2
-rw-r-----  1 root bandit5 8488 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere03
-rw-r-----  1 root bandit5 6595 May  7  2020 -file2
-rw-r-----  1 root bandit5 8880 May  7  2020 .file2
-rw-r-----  1 root bandit5 3385 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere04
-rw-r-----  1 root bandit5 2619 May  7  2020 -file2
-rw-r-----  1 root bandit5 6144 May  7  2020 .file2
-rw-r-----  1 root bandit5 2491 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere05
-rw-r-----  1 root bandit5 5959 May  7  2020 -file2
-rw-r-----  1 root bandit5 5917 May  7  2020 .file2
-rw-r-----  1 root bandit5 2420 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere06
-rw-r-----  1 root bandit5 1076 May  7  2020 -file2
-rw-r-----  1 root bandit5 8976 May  7  2020 .file2
-rw-r-----  1 root bandit5 4251 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere07
-rw-r-----  1 root bandit5 2488 May  7  2020 -file2
-rw-r-----  1 root bandit5 1033 May  7  2020 .file2
-rw-r-----  1 root bandit5 9064 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere08
-rw-r-----  1 root bandit5 3825 May  7  2020 -file2
-rw-r-----  1 root bandit5  747 May  7  2020 .file2
-rw-r-----  1 root bandit5 3693 May  7  2020 spaces file2
/home/bandit5/inhere/maybehere09
-rw-r-----  1 root bandit5  774 May  7  2020 -file2
-rw-r-----  1 root bandit5 8517 May  7  2020 .file2
-rw-r-----  1 root bandit5 8716 May  7  2020 spaces file2
bandit5@bandit:~/inhere/maybehere09$ cd /home/bandit5/inhere/maybehere07
bandit5@bandit:~/inhere/maybehere07$ cat .file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7

```
