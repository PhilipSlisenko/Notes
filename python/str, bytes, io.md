Converting from **code point** to byte or sequance of bytes is encoding. Converting from bytes to code points
is decoding.  
Unicode has a big table with **code point** to each existing character.  
Binary sequences are really sequences of integers.

### Decoding files
1. Use utility `file` with option MIME encoding (--mime-encoding)
2. Use `cat` to print the content in terminal, see if replace character � (U+FFFD) is printed. If yes, you probably need to specify the encoding for file I/O.
3. Use `xxd` to make a hex dump of this file.

For example, I have a txt file called iso-8859-1.txt. I can check its encoding using the tricks mentioned above.
```bash
$ file iso-8859-1.txt --mime-encoding
iso-8859-1.txt: iso-8859-1
```
```bash
$ cat iso-8859-1.txt
re�u
```
```bash
$ xxd iso-8859-1.txt
00000000: 7265 e775 0a                             re.u.
```
Note that when using xxd, the hexadecimal presentation is shown. For example, character ‘ç’ from word “reçu” is shown as e7.