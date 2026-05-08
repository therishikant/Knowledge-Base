# Git

## Description
- Git is a distributed version control system that allows developers to track changes in their code and collaborate with others. It is widely used in software development for managing source code and coordinating work among multiple developers.

## Commands 
**1. Change local repo username and email**

```bash
git config user.name "Your New Name"
git config user.email "yournewemail@example.com"
```
**2. Add Origin**
```bash
git remote add origin <URL>
```

**3. Get current origin**
```bash
git remote -v
```

**4. Push**
```bash
git push # Uploads your current branch to its linked remote branch

git push origin <Branch> # Push to Specific Remote/Branch

git push -u origin <branch-name> # Set Upstream Links a new local branch to a remote one for the first time so you can use just git push later.

git push --all # Uploads every local branch that has a remote counterpart
```


