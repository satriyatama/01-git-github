## Membuat Repo

![create repo](E:\sattama\materii\SEMESTER 3\MDPL Praktik\01-git-github\images\create repo.png)

## Git Clone

```bash
$ git clone https://github.com/satriyatama/01-git-github.git
Cloning into '01-git-github'...
warning: You appear to have cloned an empty repository.
```

## Mengganti Branch dari master ke main

```bash
$ git checkout -b main
Switched to a new branch 'main'
```

## Mengelola Repo

1. Membuat File

   ```bash
   $ touch README.md
   ```

2. Edit File

   ```bash
   $ vim README.md
   ```

   ```bash
   My Awesome Project
   ~
   ~
   ~
   README.md[+] [unix] (11:14 28/09/2021)                                       1,18 All
   ```

3. Menampilkan isi file

   ```bash
   $ cat README.md
   My awesome project
   
   ```

4. git status

   ```bash
   $ git status
   On branch main
   
   No commits yet
   
   Untracked files:
     (use "git add <file>..." to include in what will be committed)
   
           README.md
           images/
           mengelola-repo-sendiri-account.md
   
   nothing added to commit but untracked files present (use "git add" to track)
   ```

5. git add

   ```bash
   $ git add .
   warning: LF will be replaced by CRLF in README.md.
   The file will have its original line endings in your working directory
   
   ```

6. committing changes

   ```bash
   $ git commit -m 'Initial commit'[main (root-commit) b788d20] Initial commit 4 files changed, 1 insertion(+) create mode 100644 README.md create mode 100644 images/create repo.png create mode 100644 images/generate personal acces token.png create mode 100644 mengelola-repo-sendiri-account.md
   ```

7. Push to origin

   ```bash
   $ git push -u origin main
   Username for 'https://github.com': satriyatamaEnumerating objects: 7, done.Counting objects: 100% (7/7), done.Delta compression using up to 4 threadsCompressing objects: 100% (5/5), done.Writing objects: 100% (7/7), 133.57 KiB | 10.27 MiB/s, done.Total 7 (delta 0), reused 0 (delta 0)To https://github.com/satriyatama/01-git-github.git * [new branch]      main -> mainBranch 'main' set up to track remote branch 'main' from 'origin'.
   ```

## Git Branching and Merging

1. Create new branch

   ```bash
   $ git checkout -b edit-readme-1Switched to a new branch 'edit-readme-1'
   ```

2. Edit File Readme

   ```bash
   $ vim README.md
   ```

   ```bash
   My awesome project
   (This is editted part)
   ~
   ~
   ~
   ~
   README.md[+] [unix] (11:23 28/09/2021)                                        3,8 All
   ```

3. Push to origin on specific branch

   ```bash
   $ git add .warning: LF will be replaced by CRLF in README.md.The file will have its original line endings in your working directory
   $ git statusOn branch edit-readme-1Your branch is ahead of 'origin/edit-readme-1' by 1 commit.  (use "git push" to publish your local commits)Changes to be committed:  (use "git reset HEAD <file>..." to unstage)        modified:   README.md
   $ git commit -m 'Edit: readme'[edit-readme-1 6ccc50f] Edit: readme 1 file changed, 1 insertion(+), 1 deletion(-)
   $ git push -u origin edit-readme-1
   Username for 'https://github.com': satriyatama
   Enumerating objects: 8, done.Counting objects: 100% (8/8), done.Delta compression using up to 4 threadsCompressing objects: 100% (4/4), done.Writing objects: 100% (6/6), 712 bytes | 118.00 KiB/s, done.Total 6 (delta 0), reused 0 (delta 0)To https://github.com/satriyatama/01-git-github.git   b788d20..6ccc50f  edit-readme-1 -> edit-readme-1Branch 'edit-readme-1' set up to track remote branch 'edit-readme-1' from 'origin'.
   ```

4. Merge remote

![merge](images\merge.png)

5. Merge Local

   ```bash
   $ git checkout mainSwitched to branch 'main'M       mengelola-repo-sendiri-account.mdYour branch is up to date with 'origin/main'.
   $ git merge edit-readme-1
   Updating b788d20..6ccc50fFast-forward README.md
   | 2 ++ 1 file changed, 2 insertions(+)
   $git branch -D edit-readme-1
   Deleted branch edit-readme-1 (was 6ccc50f).
   $ git branch
   * main
   $ git pull
   remote: Enumerating objects: 1, done.remote: Counting objects: 100% (1/1), done.remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0Unpacking objects: 100% (1/1), done.From https://github.com/satriyatama/01-git-github   b788d20..099d2f4  main       -> origin/mainUpdating 6ccc50f..099d2f4Fast-forward
   ```

## Cancel Changes

```bash
$ git checkout -b edit-readme-2
Switched to a new branch 'edit-readme-2'
$ vim README.md
$ cat README.md
My awesome project

(This is editted part)

Mess change
$ git checkout main
Switched to branch 'main'
M       README.md
Your branch is ahead of 'origin/main' by 3 commits.
  (use "git push" to publish your local commits)
$ cat README.md
My awesome project

(This is editted part)

Mess change
$ git branch -D edit-readme-2
Deleted branch edit-readme-2 (was f413d9d).
$ git reset --hard
HEAD is now at f413d9d Edit
$ cat README.md
My awesome project

(This is editted part)
```

## Undo Last Commit

```bash
$ git log --oneline
099d2f4 (HEAD -> main, origin/main, origin/HEAD) Merge pull request #1 from satriyatama/edit-readme-1
6ccc50f (origin/edit-readme-1) Edit: readme
f239a03 edit readme
b788d20 Initial commit
$ vim README.md
$ cat README.md
My awesome project

(This is editted part)


Additional Content
$ git add .
$ git commit -m 'Add: content'
[main b4facd9] Add: content
 1 file changed, 5 insertions(+), 1 deletion(-)
$ git push -u origin main
Username for 'https://github.com': satriyatama
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 394 bytes | 98.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/satriyatama/01-git-github.git
   099d2f4..b4facd9  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

```bash
$ git revert HEAD
[main e90650d] Revert "Add: content"
 1 file changed, 1 insertion(+), 5 deletions(-)
$ cat README.md
My awesome project

(This is editted part)
$ git push -u origin main
Username for 'https://github.com': satriyatama
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 411 bytes | 205.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/satriyatama/01-git-github.git
   b4facd9..e90650d  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.
```

## Undo to specific commit position

```bash
$ vim README.md
$ cat README.md
My awesome project

(This is editted part)

Random string
$ git log --oneline
5a5ba5b (HEAD -> main) Add: random string
e90650d (origin/main, origin/HEAD) Revert "Add: content"
b4facd9 Add: content
099d2f4 Merge pull request #1 from satriyatama/edit-readme-1
6ccc50f (origin/edit-readme-1) Edit: readme
f239a03 edit readme
b788d20 Initial commit
$ git revert e90650d
$ cat README.md
My awesome project

(This is editted part)

<<<<<<< HEAD
Random string
=======

Additional Content

>>>>>>> parent of e90650d... Revert "Add: content"
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

You are currently reverting commit e90650d.
  (fix conflicts and run "git revert --continue")
  (use "git revert --abort" to cancel the revert operation)

Unmerged paths:
  (use "git reset HEAD <file>..." to unstage)
  (use "git add <file>..." to mark resolution)

        both modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
$ git revert --continue
[main 2b90304] Revert "Revert "Add: content""
 1 file changed, 6 insertions(+)
$ git push -u origin
Username for 'https://github.com': satriyatama
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 4 threads
Compressing objects: 100% (9/9), done.
Writing objects: 100% (9/9), 1.20 KiB | 245.00 KiB/s, done.
Total 9 (delta 0), reused 0 (delta 0)
To https://github.com/satriyatama/01-git-github.git
   e90650d..b9fafe1  main -> main
Branch 'main' set up to track remote branch 'main' from 'origin'.

```

