`Link` : `https://overthewire.org/wargames/bandit/bandit13.html`

## [ððð¥ð¤ð­ð¡ð«ð¨ð®ð ð¡] ~ ððð§ðð¢ð­ ððð¯ðð¥ ðð - ððð¯ðð¥ ðð
## ððð¯ðð¥ ðð¨ðð¥
> The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## ðð¨ð¥ð®ð­ð¢ð¨ð§

- `cp data.txt /tmp/tempBandit/data.txt`
- `cd /tmp/tempBandit`
- `ls`
- `xxd -r data.txt data`
- `ls`
- `file data`
- `mv data data.gz`
- `ls`
- `file data.gz`
- `gzip -d data.gz`
- `ls`
- `mv data data.bz2`
- `file data.bz2`
- `bzip2 -d data.bz2`
- `gzip -d data.gz`
- doing same thing recursively


```
bandit12@bandit:~$ !5
cp data.txt /tmp/tempBandit/data.txt
bandit12@bandit:~$ !17
cd /tmp/tempBandit
bandit12@bandit:/tmp/tempBandit$ ls
data.txt
bandit12@bandit:/tmp/tempBandit$ xxd -r data.txt data
bandit12@bandit:/tmp/tempBandit$ ls
data  data.txt
bandit12@bandit:/tmp/tempBandit$ file data
data: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/tempBandit$ mv data data.gz
bandit12@bandit:/tmp/tempBandit$ ls
data.gz  data.txt
bandit12@bandit:/tmp/tempBandit$ type data.gz
-bash: type: data.gz: not found
bandit12@bandit:/tmp/tempBandit$ file data.gz
data.gz: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/tempBandit$ man gzip
bandit12@bandit:/tmp/tempBandit$ gzip -d data.gz
bandit12@bandit:/tmp/tempBandit$ ls
data  data.txt
bandit12@bandit:/tmp/tempBandit$ cat data
BZh91AY&SYï¿½Oï¿½ï¿½ï¿½ï¿½ÚOvï¿½ï¿½ï¿½}?ï¿½ï¿½}ï¿½ï¿½^ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ß£ï¿½ï¿½;ï¿½ï¿½ï¿½ï¿½â4ï¿½ï¿½âhï¿½Fï¿½Fï¿½ï¿½4âLM
                                                                @ï¿½ï¿½zï¿½ï¿½FMï¿½ï¿½Cï¿½hFï¿½C@ï¿½4@fï¿½ï¿½h
4hhï¿½â=C%ï¿½>Xâ,ï¿½kï¿½ï¿½ï¿½1ï¿½ï¿½GYï¿½ï¿½
ï¿½Jï¿½ìOÏï¿½ï¿½{RBpï¿½Qixï¿½Yï¿½Z!dï¿½ï¿½jï¿½(ï¿½æ¿Ý³ï¿½ï¿½/ï¿½ï¿½Aï¿½#ï¿½Aï¿½ï¿½Fï¿½ï¿½0Pï¿½ï¿½vï¿½ï¿½`ï¿½"3ï¿½

                                          ï¿½ï¿½dï¿½bX?ï¿½ï¿½zï¿½ï¿½2ï¿½ï¿½<ï¿½ï¿½A ï¿½n}
5(3Aï¿½ï¿½
      wOï¿½Rï¿½ï¿½ï¿½ï¿½6ï¿½XS{ï¿½
ï¿½ï¿½ï¿½9?Lï¿½Pï¿½yBï¿½ï¿½=zï¿½m?ï¿½Lï¿½Nt*ï¿½7{qPï¿½ï¿½ï¿½%"ï¿½w9ï¿½qm4ï¿½ï¿½ N3ï¿½6ï¿½ï¿½ï¿½Kï¿½ï¿½Hä[ï¿½ï¿½}!
                                                              dï¿½ï¿½3A4$ï¿½ï¿½M~ï¿½\É Jï¿½Cï¿½kUÆ¦\ï¿½ï¿½ï¿½\ï¿½FSNï¿½ï¿½&=ï¿½[ï¿½ï¿½q   \)ï¿½$:ï¿½ï¿½Hï¿½t&/ï¿½(ï¿½ï¿½ï¿½ï¿½]ï¿½ï¿½BB9<s bandit12@bandit:/tmp/tempBandit$ file data
data: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tempBandit$ mv data data.bz2
bandit12@bandit:/tmp/tempBandit$ file data.bz2
data.bz2: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tempBandit$ man bz2
No manual entry for bz2
bandit12@bandit:/tmp/tempBandit$ man bzip2
bandit12@bandit:/tmp/tempBandit$ bzip2 -d data.bz2
bandit12@bandit:/tmp/tempBandit$ ls
data  data.txt
bandit12@bandit:/tmp/tempBandit$ cat data
Pï¿½^data4.binï¿½ï¿½=Hâï¿½ï¿½ï¿½F:t0Eï¿½D4)rgriï¿½KPZï¿½RNpï¿½Hâ3($q        ï¿½ï¿½ï¿½Ejï¿½LRlï¿½ï¿½ï¿½tï¿½M5ï¿½ï¿½ï¿½=+Ø©Zï¿½ï¿½Yï¿½ï¿½ï¿½yï¿½ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½~ï¿½ï¿½(ï¿½ï¿½{S-ï¿½zï¿½uï¿½z|ï¿½ï¿½h×BQUk(dEÜï¿½X<âï¿½eâï¿½ï¿½uï¿½ï¿½ï¿½#ï¿½kï¿½ï¿½{ï¿½ï¿½ï¿½ï¿½ï¿½ï¿½Î¿ï¿½ï¿½ï¿½Cï¿½+Ü¨ï¿½ï¿½ï¿½ï¿½ï¿½Tï¿½.bbï¿½rï¿½0ï¿½ï¿½ï¿½ï¿½ï¿½h$ï¿½ï¿½3ï¿½ï¿½"ï¿½|ï¿½jï¿½jTÈ¢Yï¿½Åï¿½ï¿½Qï¿½ï¿½ï¿½aï¿½ï¿½ï¿½ï¿½ï¿½ï¿½#ï¿½ï¿½|ï¿½Qï¿½Qï¿½9+ç¶3añ¼¯²ï¿½rU*ï¿½#%ï¿½ï¿½ï¿½Oï¿½ï¿½q3ï¿½$ï¿½ï¿½ï¿½
%ï¿½Uï¿½y~,tzï¿½xSï¿½04ï¿½6ß¥ï¿½kBCï¿½ï¿½=ï¿½meï¿½"ï¿½ï¿½kGdEo?nï¿½,moï¿½ï¿½Oï¿½Sz6ï¿½ï¿½8ï¿½ï¿½Tï¿½[ï¿½ï¿½\fÒ~ï¿½c.ï¿½Ó´ï¿½*ï¿½:Ó¾oï¿½ï¿½Ämï¿½kï¿½ï¿½ï¿½,ï¿½ï¿½ï¿½
ï¿½
 ï¿½Pbandit12@bandit:/tmp/tempBandit$ file data
data: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/tempBandit$ mv data data.gz
bandit12@bandit:/tmp/tempBandit$ gzip -d data.gz
bandit12@bandit:/tmp/tempBandit$ ls
data  data.txt
bandit12@bandit:/tmp/tempBandit$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tempBandit$ mv data data.tar
bandit12@bandit:/tmp/tempBandit$ man tar
bandit12@bandit:/tmp/tempBandit$ tar -x data.tar
tar: Refusing to read archive contents from terminal (missing -f option?)
tar: Error is not recoverable: exiting now
bandit12@bandit:/tmp/tempBandit$ tar -x -f data.tar
bandit12@bandit:/tmp/tempBandit$ ls
data5.bin  data.tar  data.txt
bandit12@bandit:/tmp/tempBandit$ file data5.bin 
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tempBandit$ mv data5.bin data.tar
bandit12@bandit:/tmp/tempBandit$ tar -xf data.tar
bandit12@bandit:/tmp/tempBandit$ ls
data6.bin  data.tar  data.txt
bandit12@bandit:/tmp/tempBandit$ file data6.bin 
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/tempBandit$ mv data6.bin data.bz2
bandit12@bandit:/tmp/tempBandit$ bzip2 -d data.bz2 
bandit12@bandit:/tmp/tempBandit$ ls
data  data.tar  data.txt
bandit12@bandit:/tmp/tempBandit$ file data
data: POSIX tar archive (GNU)
bandit12@bandit:/tmp/tempBandit$ mv data data.tar
bandit12@bandit:/tmp/tempBandit$ tar -xf data.tar
bandit12@bandit:/tmp/tempBandit$ ls
data8.bin  data.tar  data.txt
bandit12@bandit:/tmp/tempBandit$ file data8.bin 
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/tempBandit$ mv data8.bin data.gz
bandit12@bandit:/tmp/tempBandit$ ls
data.gz  data.tar  data.txt
bandit12@bandit:/tmp/tempBandit$ gzip -d data.gz 
bandit12@bandit:/tmp/tempBandit$ ls
data  data.tar  data.txt
bandit12@bandit:/tmp/tempBandit$ file data
data: ASCII text
bandit12@bandit:/tmp/tempBandit$ cat data
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
bandit12@bandit:/tmp/tempBandit$ 
                                                  
```
