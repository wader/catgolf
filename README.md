# cat(1) golf

### Pure league

- No shell features involved
- Only output on stdout

```sh
cat file.txt
awk 1 file.txt
paste file.txt
pv -q file.txt
grep '' file.txt
sort -m file.txt
sed -n p file.txt
cut -b 1- file.txt
jq -rRs . file.txt
perl -pe1 file.txt
sed '/*/p' file.txt
tail -n +1 file.txt
head -n -0 file.txt (GNU head)
gcc -E -P -xc file.txt
cp file.txt /dev/stdout
scp file.txt /dev/stdout
dd status=none if=file.txt (GNU dd)
openssl enc -none -in file.txt
curl file:///proc/self/cwd/file.txt
diff --line-format=%L /dev/null file.txt
vim -es --clean '+w! /dev/stdout' '+q!' file.txt
ffmpeg -v quiet -f data -i file.txt -map 0:0 -c text -f data -
emacs -Q --batch --eval '(princ (with-temp-buffer (insert-file-contents "file.txt") (buffer-string)))'
python -c 'print(open("file.txt").read()[:-1])'
bat --color=never --style=plain file.txt
w3m -dump_source file.txt
```

### Pipe league

```
tr a a < file.txt
rev < file.txt | rev
```

### Error league

- Same as pure but can have errors on stdout and stderr

```sh
dd if=file.txt
gcc -xc file.txt
```

### Junk league

- Same as error but most bytes from the file
