# Git-Practical-Exam

### Start with…

---

- Create a new repository for project.
- Create a new directory locally and initialise using `git init` .
- Do first commit using `git commit -m "first commit"`  after adding Readme.md file.
- Add remote origin and then push.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ echo "# project-exam" >> README.md
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ ls
    README.md
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add README.md
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "first commit"
    [master (root-commit) ddff8d8] first commit
     1 file changed, 1 insertion(+)
     create mode 100644 prac/README.md
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git remote add origin https://github.com/zilenmodi/project-exam.git
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git push -u origin master
    Username for 'https://github.com': zilenmodi
    Password for 'https://zilenmodi@github.com': 
    Enumerating objects: 4, done.
    Counting objects: 100% (4/4), done.
    Writing objects: 100% (4/4), 271 bytes | 271.00 KiB/s, done.
    Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
    To https://github.com/zilenmodi/project-exam.git
     * [new branch]      master -> master
    Branch 'master' set up to track remote branch 'master' from 'origin'.
    ```
    

### 1. Pull and Merge difference

---

- Create two branch called **master** and **feature**.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git branch
    * master
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git branch feature
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git branch
      feature
    * master
    ```
    
- To generate pull request from feature branch first checkout and create file.
- Then, Do two edits and commit them individually : **c1** and **c2**.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git checkout feature
    Switched to branch 'feature'
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ ls
    README.md
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ touch file
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "c1"
    [feature 7dcba7b] c1
     1 file changed, 1 insertion(+)
     create mode 100644 prac/file
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "c2"
    [feature 77e57f2] c2
     1 file changed, 1 insertion(+)
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline --graph
    * 77e57f2 (HEAD -> feature) c2
    * 7dcba7b c1
    * ddff8d8 (origin/master, master) first commit
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git push -u origin feature
    ```
    
- **After push two commits:**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9921a311-e438-4bf7-999f-32438a6be053/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6bd6e02a-132e-42f0-8e10-01edf4e07a65/Untitled.png)

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/7995d814-001c-485c-816b-0ec1e3e7a91a/Untitled.png)

- **Compare and generate pull request to master branch:**

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5df94768-7e35-460f-9e1b-5f3bc68799ca/Untitled.png)

- **Merging pull request of : feature → master**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9a4e8c05-2e85-42cb-9a04-bd47bd5ac3bf/Untitled.png)
    
- **After merging commits in master branch:**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dcb1599a-7b91-4816-94bc-b00cac9c6525/Untitled.png)
    
- **Terminal:**
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git pull origin master
    remote: Enumerating objects: 1, done.
    remote: Counting objects: 100% (1/1), done.
    remote: Total 1 (delta 0), reused 0 (delta 0), pack-reused 0
    Unpacking objects: 100% (1/1), 637 bytes | 637.00 KiB/s, done.
    From https://github.com/zilenmodi/project-exam
     * branch            master     -> FETCH_HEAD
       ddff8d8..d7892da  master     -> origin/master
    Updating ddff8d8..d7892da
    Fast-forward
     prac/file | 2 ++
     1 file changed, 2 insertions(+)
     create mode 100644 prac/file
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline --graph
    *   d7892da (HEAD -> master, origin/master) Merge pull request #1 from zilenmodi/feature
    |\  
    | * 77e57f2 (origin/feature, feature) c2
    | * 7dcba7b c1
    |/  
    * ddff8d8 first commit
    ```
    

### 2. Rebase

- From previous stop, We are doing two commits in master named : **c3** and **c4**.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git branch
      feature
    * master
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "c3"
    [master 78a7b5e] c3
     1 file changed, 1 insertion(+)
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "c4"
    [master 0c8f518] c4
     1 file changed, 1 insertion(+)
    ```
    
- Move to feature and do two commits : **f1** and **f2**.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git checkout feature
    Switched to branch 'feature'
    Your branch is up to date with 'origin/feature'.
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "f1"
    [feature 128471a] f1
     1 file changed, 1 insertion(+)
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "f2"
    [feature c900ab8] f2
     1 file changed, 1 insertion(+)
    ```
    
- For rebase go to master and then rebase feature with master.
    
    `git rebase feature`
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git checkout master
    Switched to branch 'master'
    Your branch is ahead of 'origin/master' by 2 commits.
      (use "git push" to publish your local commits)
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git rebase feature
    Auto-merging prac/file
    CONFLICT (content): Merge conflict in prac/file
    ```
    
- If there are conflicts, then solve and use `git rebase —continue` Command.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git rebase --continue
    [detached HEAD c1fd0bc] c3
     1 file changed, 1 insertion(+)
    Successfully rebased and updated refs/heads/master.
    ```
    
- **Git log in terminal after rebase:**
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline --graph
    * 6da7c6a (HEAD -> master) c4
    * c1fd0bc c3
    * c900ab8 (feature) f2
    * 128471a f1
    * 77e57f2 (origin/feature) c2
    * 7dcba7b c1
    * ddff8d8 first commit
    ```
    
- **On master branch github:**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/fabcd65e-08d5-4da0-a258-0bcb129d366d/Untitled.png)
    
    - **Sequence in master → c1 ← c2 ← f1 ← f2 ← c3 ← c4.**
- **On feature branch github:**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e9c6a8f3-f310-450b-8189-0bbbaf62c33e/Untitled.png)
    

### 3. Change commit message

- Change last commit message : `git commit —amend`
- **Message : f4 → f4 change to f3**
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add file
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "f4"
    [feature c063597] f4
     1 file changed, 1 insertion(+)
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit --amend
    [feature 252843c] f4 change to f3
     Date: Fri Feb 17 17:30:31 2023 +0530
     1 file changed, 1 insertion(+)
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline
    252843c (HEAD -> feature) f4 change to f3
    c900ab8 (origin/feature) f2
    128471a f1
    ```
    
- Change commit message in-between : use **rebase -i** and done by reword.
- **Message : f4 change to f3 → f3**
    
    `git rebase -i <commit-id>`
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git rebase -i c900ab8
    [detached HEAD 87cb511] f3
     Date: Fri Feb 17 17:30:31 2023 +0530
     1 file changed, 1 insertion(+)
    Successfully rebased and updated refs/heads/feature.
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline
    87cb511 (HEAD -> feature) f3
    c900ab8 (origin/feature) f2
    128471a f1
    ```
    

### 4. Cherry-pick

- Create in file named : **name.txt**  and do commit named : **f4**.
- Move to master and then pick commit f4 using commit ID.
- Command : `git cherry-pick <commit-id>`
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ touch name
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add name
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "f4"
    [feature 335c056] f4
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 prac/name
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git checkout master
    Switched to branch 'master'
    Your branch is up to date with 'origin/master'.
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git cherry-pick 335c056
    [master b9dfcfe] f4
     Date: Fri Feb 17 17:43:18 2023 +0530
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 prac/name
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git push -u origin master
    ```
    
- **On master branch github: New commit added f4**
    
    ![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8f059848-750a-4494-b7d5-ddf09767520d/Untitled.png)
    

### 5. Drop commit

- To drop commit use reset command.
- A mixed option is a default option of the git reset command. If we would not pass any argument, then the git reset command considered as **-mixed** as default option.
- A mixed option updates the ref pointers. The staging area also reset to the state of a specified commit. The undone changes transferred to the working directory. - `git reset —mixed <c-id>`
- The soft option does not touch the index file or working tree at all, but it resets the Head as all options do.
- When the soft mode runs, the refs pointers updated, and the resets stop there. It will act as git amend command. `git reset —soft <c-id>`
- Reset from all area - `git reset —hard <c-id>`
- **Create 3 files called : f1, f2 and f3**
- Add and do commit individually and apply three above reset.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ touch f1
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ touch f2
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ touch f3
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add f1
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "Created f1"
    [feature ff988ee] Created f1
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 prac/f1
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add f2
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "Created f2"
    [feature b71bf5d] Created f2
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 prac/f2
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git add f3
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git commit -m "Created f3"
    [feature 64085a0] Created f3
     1 file changed, 0 insertions(+), 0 deletions(-)
     create mode 100644 prac/f3
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline
    64085a0 (HEAD -> feature) Created f3
    b71bf5d Created f2
    ff988ee Created f1
    335c056 (origin/feature) f4
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git reset --hard b71bf5d
    HEAD is now at b71bf5d Created f2
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git reset --mixed ff988ee
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git reset --soft 335c056
    ```
    
- **Result:**
    - Initial there are 3 file f1,f2 and f3.
    - Hard reset on b71bf5d.
    - Mixed reset on ff988ee.
    - Soft reset on 335c056.
    - f3 will delete from work area, stage area and local repo.
    - f2 will delete from stage area and local repo.
    - f1 will delete from local repo only.
    
    ```
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git log --oneline
    335c056 (HEAD -> feature, origin/feature) f4
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git ls-files
    README.md
    f1
    
    zilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ ls
    f1  f2
    
    ilen@sf-cpu-438:~/Desktop/Workspace/Git/prac$ git push
    Username for 'https://github.com': zilenmodi
    Password for 'https://zilenmodi@github.com': 
    Everything up-to-date
    ```
