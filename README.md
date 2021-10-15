# cat(1) golf

### Pure league

- No shell features involved
- Only output on stdout

```sh
cat file.txt
grep '' file.txt
sort -m file.txt
sed -n p file.txt
jq -rRs . file.txt
sed '/*/p' file.txt
head -n -0 file.txt (GNU head)
cp file.txt /dev/stdout
scp file.txt /dev/stdout
curl file://$PWD/file.txt
dd status=none if=file.txt (GNU dd)
awk '/.*/ { print }' file.txt
openssl enc -none -in file.txt
perl -e 'while(<>){print}' file.txt
diff --new-line-format="%L" /dev/null file.txt
ffmpeg -v quiet -f data -i file.txt -map 0:0 -c text -f data -
emacs -Q --batch --eval '(princ (with-temp-buffer (insert-file-contents "file.txt") (buffer-string)))'
```

### Error league

- Same as pure but can have errors on stdout and stderr

### Junk league

- Same as error but most bytes from the file

