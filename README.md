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
look '' file.txt
sed -n p file.txt
cut -b 1- file.txt
jq -rRs . file.txt
perl -pe1 file.txt
sed '/*/p' file.txt
tail -n +1 file.txt
head -n -0 file.txt # GNU head
gcc -E -P -xc file.txt
comm file.txt /dev/null # BSD comm
cp file.txt /dev/stdout
scp file.txt /dev/stdout
w3m -dump_source file.txt
dd status=none if=file.txt # GNU dd
hexdump -ve '"%c"' file.txt
join -a 1 file.txt /dev/null
openssl enc -none -in file.txt
curl file:///proc/self/cwd/file.txt
git -P grep --no-index -h ^ file.txt
shuf --random-source=/dev/zero file.txt
bat --color=never --style=plain file.txt
diff --line-format=%L /dev/null file.txt
python -c 'print(open("file.txt").read()[:-1])'
vim -es --clean '+w! /dev/stdout' '+q!' file.txt
ffmpeg -v quiet -f data -i file.txt -map 0:0 -c text -f data -
emacs -Q --batch --eval '(princ (with-temp-buffer (insert-file-contents "file.txt") (buffer-string)))'
```

### Pipe league

```sh
tee < file.txt
tr a a < file.txt
rev file.txt | rev
tac file.txt | tac
echo ',p' | ed -s file.txt
xxd -p file.txt | xxd -p -r
```

### Error league

- Same as pure but can have errors on stdout and stderr

```sh
dd if=file.txt
gcc -xc file.txt
```

### Junk league

- Same as error but most bytes from the file

```sh
fold file.txt # Works for files without long lines
wall -n file.txt # I hope your file doesn't have any secrets
uniq -Dw0 file.txt # Doesn't work for single-line files
nl -bn -w 1 -s '' file.txt # Each line has an extra space
```
