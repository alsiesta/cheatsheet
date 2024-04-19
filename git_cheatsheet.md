# Git Cheat Sheet
By default, cloned Git repos have a remote *named* ***origin***, which refers to the remote repository from which it was cloned.               
| Command                        | Use                                  | Notes                             |
|--------------------------------|--------------------------------------|-----------------------------------|
| `git init`                     | Initialize a new git repository      | -                                 |
| `git clone [url]`              | Clone a repository                   | -                                 |
| `git add [file]`               | Add a file to the staging area       | Use `.` to add all files          |
| `git commit -m "[message]"`    | Commit your changes                  | -                                 |
| `git status`                   | Check the status of changes          | -                                 |
| `git remote -v`                 | List all remote connections              | Usefull, if remote is not named origin                                 |
| `git ls-remote --get-url origin`   | Get remote origin URL    |       |
| `git remote show origin`   | Get all details of remote origin    |       |
| . . .   | . . .    | . . .       |
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

### Set remote origin on local repo
| Command                        | Use                                  | Notes                             |
|--------------------------------|--------------------------------------|-----------------------------------|
| `git remote add origin <URL>`| **Add** a new remote named origin to  local Git repo |  If there is no remote named origin yet associated with local repo                                 |
| `git remote set-url origin <URL>`| **Change** the URL of local remote repo named origin |  Needed if remote repo has moved to a different URL|