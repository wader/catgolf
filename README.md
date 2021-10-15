# cat(1) golf

Currentl rules are:
- No piping
- No redirect
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
```
