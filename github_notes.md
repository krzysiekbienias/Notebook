# Github utilities

### how to create new branch and switch on it.
```
git checkout -b  <branch name>
```

# Git pull --rebase
Using git pull --rebase instead of the default git pull can be better in many scenarios, particularly when collaborating with others, as it helps maintain a cleaner project history. 

- Always try git pull --rebase first. 
- If you get a merge conflict, you can undo everything with git rebase --abort
- pull normally using git pull

### Conclusion
git pull --rebase is generally better for maintaining a clean, linear history, especially on shared or feature branches. However, it requires careful use to avoid rewriting shared history.