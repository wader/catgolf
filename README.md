# cat(1) golf

### Pure league

- No shell features involved
- Only output on stdout

```sh
cat file.txt
grep '' file.txt
cp file.txt /dev/stdout
awk '/.*/ { print }' file.txt
dd status=none if=file.txt (GNU dd)
curl file://$PWD/file.txt
jq -rRs . file.txt
ffmpeg -v quiet -f data -i file.txt -map 0:0 -c text -f data -
sed '/*/p' file.txt
sed -n p file.txt
perl -e 'while(<>){print}' file.txt
head -n -0 file.txt (GNU head)
```

### Error league

- Same as pure but can have errors on stdout and stderr

### Junk league

- Same as error but most bytes from the file

