
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
sed b file.txt
grep ^ file.txt
grep $ file.txt
sed '' file.txt
grep '' file.txt
sort -m file.txt
look '' file.txt
jq -rR . file.txt
sed -n p file.txt
cut -b 1- file.txt
jq -jRs . file.txt
perl -pe1 file.txt
tail -n +1 file.txt
head -n -0 file.txt # GNU head
cp file.txt /dev/fd/1
gcc -E -P -xc file.txt
scp file.txt /dev/fd/1
column -t -l 1 file.txt
comm file.txt /dev/null # BSD comm
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
vim -es --clean '+w! /dev/fd/1' '+q!' file.txt
python -c 'print(open("file.txt").read()[:-1])'
ffmpeg -v quiet -f data -i file.txt -map 0:0 -c text -f data -
emacs -Q --batch --eval '(princ (with-temp-buffer (insert-file-contents "file.txt") (buffer-string)))'
```

### Shell league

- Can use shell feature like pipes, redirect etc to work.

```sh
tee < file.txt
tr a a < file.txt
rev file.txt | rev
tac file.txt | tac
echo ',p' | ed -s file.txt
xxd -p file.txt | xxd -p -r
while read l; do echo $l; done < file.txt
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
m4 file.txt # Does not handle lines that starts with `#` or looks like definitions.
fold file.txt # Works for files without long lines
wall -n file.txt # I hope your file doesn't have any secrets
uniq -Dw0 file.txt # Doesn't work for single-line files
xargs -d\n -a a.txt echo # Ends up with a trailing newline
more -e -n 65535 file.txt # Works for files with less than 65k lines.
nl -bn -w 1 -s '' file.txt # Each line has an extra space
```
