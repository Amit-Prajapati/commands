
**Windows commands: To terminate particular serivce running on port 8080:**
```
netstat -ano | findstr 8080
taskkill /pid <pid>
```

**To fix git asking user credentials everytime:**
```
git config --global credential.helper store
```

