# INT142 Software Development Tools
## Class 03 Git Branches and Multiple Local Repositories

### Overview

In this class, you will create a new branch `class03` and work on this branch instead of `main`. This way, if there is any issues with `class03` branch, you can delete the branch and start over again.  

You will also create multiple local repositories on your computer to simulate working on multiple machines.

### Setup Instructions
1. Configure default branch name to `main`
    ```bash
    $ git config --system init.defaultbranch main
    ```

2. Configure default text editor
    ```bash
    git config --global core.editor "code --wait"
    ```  
    `--wait` asks git to wait until the file is saved

---

### Stage 1 - Create `class03` branch and add `index.html` from `class02` to `class03` repository
### Instructions

1. Clone `class03` repository to `Documents/<your-github-id>/class03-kmutt`

2. Configure author's name and author's email to `<Firstname Surname> (INT142-class03-KMUTT)` and `<your-private-github-email>`, respectively

3. Create a new branch `class03`
    ```bash
    $ git branch class03
    ```

4. View local branches
    ```bash
    $ git branch
      class03
    * main
    ```  
    The current local branch is marked with `*`.

5. View remote branches.
    ```bash
    $ git branch --remotes
      origin/main
    ```

6. View all branches and details.
    ```bash
    $ git branch --all -vv
      class03             abe3a16 add deadline
    * main                abe3a16 [origin/main] add deadline
      remotes/origin/main abe3a16 add deadline
    ```

7. Change to `class03` branch.
    ```bash
    $ git switch class03
    Switched to branch 'class03'
    ```

8. View current branch and find out whether there is a new `remotes/origin/class03` or not.

9. Pull files from `class02` without making a commit and commit histories
    ```bash
    $ git pull --squash <class02-repository-url> main
    remote: Enumerating objects: 11, done.
    remote: Counting objects: 100% (11/11), done.
    remote: Compressing objects: 100% (5/5), done.
    remote: Total 11 (delta 1), reused 11 (delta 1), pack-reused 0 (from 0)
    Unpacking objects: 100% (11/11), 5.07 KiB | 649.00 KiB/s, done.
    From github.com:IT-BANGMOD-INT142-2025/class02
    * branch            main       -> FETCH_HEAD
    hint: You have divergent branches and need to specify how to reconcile them.
    hint: You can do so by running one of the following commands sometime before
    hint: your next pull:
    hint: 
    hint:   git config pull.rebase false  # merge
    hint:   git config pull.rebase true   # rebase
    hint:   git config pull.ff only       # fast-forward only
    hint: 
    hint: You can replace "git config" with "git config --global" to set a default
    hint: preference for all repositories. You can also pass --rebase, --no-rebase,
    hint: or --ff-only on the command line to override the configured default per
    hint: invocation.
    fatal: Need to specify how to reconcile divergent branches.
    ```
    `--squash` tells Git to just stage without making a commit, and without the commit history

10. Fix issues in step 9. Use merge. The output should look like:
    ```bash
    From github.com:IT-BANGMOD-INT142-2025/class02
    * branch            main       -> FETCH_HEAD
    Auto-merging .github/workflows/classroom.yml
    CONFLICT (add/add): Merge conflict in .github/workflows/classroom.yml
    Auto-merging README.md
    CONFLICT (add/add): Merge conflict in README.md
    Squash commit -- not updating HEAD
    Automatic merge failed; fix conflicts and then commit the result.
    ```

11. View status using `git status`

12. Fix the conflict using VS Code
    - Keep `README.md` and `classroom.yml` from `class03`
    - Add both files to staging area

    ```bash
    $ git status
    On branch class03
    Changes to be committed:
    (use "git restore --staged <file>..." to unstage)
        new file:   index.html
    ```

    If you want to redo step 9, use the following commands **with care**
    ```bash
    $ git reset --hard
    ```
    or
    ```bash
    $ git reset --hard origin/main
    ```    

13. Commit your work with the message `Add index.html from class02`. Check commit history and make sure that it is correct. If not, amend the commit meta-data.

14. Modify `index.html`. Replace `Class 02 Exercise 2` with `Class 03`

15. Commit with the message `Update index.html to class03`

16. Push your local commit to remote repository
    ```bash
    $ git push -u origin class03
    ```

16. Check that there is new remote branch `class03`

---

### Stage 2 - Work on `class03` at home

### Instructions

1. Clone `class03` repository to `Documents/<your-github-id>/class03-home`

2. Configure author's name and author's email to `<Firstname Surname> (INT142-class03-home)` and `<your-private-github-email>`, respectively

3. View existing branches

4. Switch to 'class03'.

5. View all existing branches

6. Modify `index.html`. Add a line  `<p>Modified at home at <current-timestamp></p>`.

7. Commit your change with the message `Update index.html at home`

8. Push the new commit to remote repository

---

### Stage 3 - Work on `class03` at KMUTT

### Instructions

1. Switch to `Documents/<your-github-id>/class03-kmutt`

2. Check status, log, branches

3. Fetch meta-data

4. Check status, log, branches again

5. Pull the commits from remote

6. Check status, log, branches again

7. Modify `index.html`. Add a line  `<p>Modified at KMUTT at <current-timestamp></p>`.

8. Commit your change with the message `Update index.html again at KMUTT`

9. Push the new commit to remote repository

---

### Stage 4 - Work on `class03` at home

### Instructions

1. Switch to `Documents/<your-github-id>/class03-home`

2. Modify `index.html`. **Modify** the line  `<p>Modified at home at <current-timestamp></p>`, update the timestamp.

3. Commit your change with the message `Update index.html again at home`

4. Push the new commit to remote repository

5. Fix the issues. Use merge method. Keep both `Modified` lines.

6. Push the new commit to remote repository
