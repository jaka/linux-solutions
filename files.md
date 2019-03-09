## files

### Calculate MD5SUM of all the files in a directory and its subdirectories
```
find . -type f -exec md5sum "{}" \; | tee ../folder.md5sum
```
