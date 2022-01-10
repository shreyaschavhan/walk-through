`Link` : `https://overthewire.org/wargames/bandit/bandit13.html`

## [𝐖𝐚𝐥𝐤𝐭𝐡𝐫𝐨𝐮𝐠𝐡] ~ 𝐁𝐚𝐧𝐝𝐢𝐭 𝐋𝐞𝐯𝐞𝐥 𝟏𝟐 - 𝐋𝐞𝐯𝐞𝐥 𝟏𝟑
## 𝐋𝐞𝐯𝐞𝐥 𝐆𝐨𝐚𝐥
> The password for the next level is stored in the file `data.txt`, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

## 𝐒𝐨𝐥𝐮𝐭𝐢𝐨𝐧

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
BZh91AY&SY�O����ڞOv���}?��}��^����������ߣ��;����▒4��▒h�F�F��4▒LM
                                                                @��z��FM��C�hF�C@�4@f��h
4hh�▒=C%�>X▒,�k���1��GY��
�J�쌑Oϊ��{RBp�Qix�Y�Z!d��j�(�搿ݳ��/��A�#�A��F��0P��v��`�"3�

                                          ��d�bX?��z��2��<��A �n}
5(3A��
      wO�R����6�XS{�
���9?L�P�yB��=z�m?�L�Nt*�7{qP���%"�w9�qm4�� N3�6���K��H䋑[��}!
                                                              d��3A4$��M~�\ɠJ�C�kUƦ\���\�FSN��&=�[��q   \)�$:��H�t&/�(����]��BB9<s bandit12@bandit:/tmp/tempBandit$ file data
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
P�^data4.bin��=H▒���F:t0E�D4)rgri�KPZ�RNp�H▒3($q        ���Ej�LRl���t�M5���=+ةZ��Y���y�������~��(��{S-�z�u�z|��hחBQUk(dE܃�X<▒�e▒��u���#�k��{������ο���C�+ܨ�����T�.bb�r�0�����h$��3��"�|�j�jTȢY�Ŕ��Q���a������#��|�Q�Q�9+綜3a񼯲�rU*�#%���O��q3�$���
%�U�y~,tz�xS�04�6ߥ�kBC��=�me�"��kGdEo?n�,mo��O�Sz6��8��T�[��\fҐ~�c.�Ӵ�*�:Ӿo��Ċm�k���,���
�
 �Pbandit12@bandit:/tmp/tempBandit$ file data
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
