
**Windows commands: To terminate particular serivce running on port 8080:**
```
netstat -ano | findstr 8080
taskkill /pid <pid>
```

**To fix git asking user credentials everytime:**
```
git config --global credential.helper store
```
**Rename multiple files from .php extension to .html:**
```
rename .php .html *.php
```
**To copy SSH key to destination server:**
```
ssh-copy-id username@<ip_address>
```
