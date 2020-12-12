## files

### Calculate MD5SUM of all the files in a directory and its subdirectories
```
find . -type f -exec md5sum "{}" \; | tee ../folder.md5sum
```

## zip

### Unzip archives into its own directory
```
find . -type f -name \*.zip | while read f; do dir=$(basename "${f%.*}"); mkdir "$dir"; unzip -d "$dir" "$f"; done
```