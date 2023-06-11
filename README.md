
# cat(1) golf
<img style="float: right" width="180" src="catgolf.svg">
Get the file to stdout as intact as possible.
<div style="clear: both">

### Pure league

- No shell features are involved.
- Only outputs to `stdout`.


```sh
cat file.txt
awk 1 file.txt
paste file.txt
pv -q file.txt
pr -t file.txt
grep ^ file.txt
grep $ file.txt
grep '' file.txt
sort -m file.txt
look '' file.txt
sed -n p file.txt
cut -b 1- file.txt
jq -rRs . file.txt
perl -pe1 file.txt
tail -n +1 file.txt
head -n -0 file.txt # GNU head
gcc -E -P -xc file.txt
comm file.txt /dev/null # BSD comm
cp file.txt /dev/stdout
scp file.txt /dev/stdout
w3m -dump_source file.txt
dd status=none if=file.txt # GNU dd
hexdump -ve '"%c"' file.txt
split --filter=tee file.txt # GNU split
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

- Needs pipes to work.

```sh
tee < file.txt
tr a a < file.txt
rev file.txt | rev
tac file.txt | tac
echo ',p' | ed -s file.txt
xxd -p file.txt | xxd -p -r
```

### Brittle league

- May not handle every character.
- May not handle every file length.

```sh
sed '/*/p' file.txt
gcc -E -P -xc file.txt
```

### Error league

- Same as "Pure league", but errors on `stdout` and/or `stderr` are acceptable.

```sh
dd if=file.txt
gcc -xc file.txt
```

### Junk league

- Same as "Error league", but most of the output bytes are from the file.

```sh
fold file.txt # Works for files without long lines
wall -n file.txt # I hope your file doesn't have any secrets
uniq -Dw0 file.txt # Doesn't work for single-line files
xargs -d\n -a a.txt echo # Ends up with a trailing newline
more -e -n 65535 file.txt # Works for files with less than 65k lines.
nl -bn -w 1 -s '' file.txt # Each line has an extra space
```