Here's a Git cheat sheet in markdown format:

```markdown
# Git Cheat Sheet

| Command                        | Use                                  | Notes                             |
|--------------------------------|--------------------------------------|-----------------------------------|
| `git init`                     | Initialize a new git repository      | -                                 |
| `git clone [url]`              | Clone a repository                   | -                                 |
| `git add [file]`               | Add a file to the staging area       | Use `.` to add all files          |
| `git commit -m "[message]"`    | Commit your changes                  | -                                 |
| `git status`                   | Check the status of changes          | -                                 |
| `git push [remote] [branch]`   | Push changes to remote repository    | Defaults to `origin master`       |
| `git pull [remote] [branch]`   | Pull updates from remote repository  | -                                 |
| `git branch [branch-name]`     | Create a new branch                  | -                                 |
| `git checkout [branch-name]`   | Switch branches                      | Use `-b` to create and switch     |
| `git merge [branch]`           | Merge a branch into the active one   | -                                 |
| `git rebase [branch]`          | Reapply commits on top of another base | Use interactive mode `-i` for more control |
| `git log`                      | View changes                         | Use `--oneline` for a brief view  |
| `git diff`                     | Show file differences not yet staged | -                                 |
| `git reset [file]`             | Unstage a file                       | Use `--hard` to discard changes   |
| `git stash`                    | Stash changes in a dirty working directory | -                             |
| `git stash pop`                | Apply stashed changes and remove them from the stash | -               |
| `git remote add [name] [url]`  | Connect to a remote repository       | -                                 |
| `git remote -v`                | List remote connections              | -                                 |
```

This cheat sheet covers basic Git commands and their uses along with some brief notes where applicable.