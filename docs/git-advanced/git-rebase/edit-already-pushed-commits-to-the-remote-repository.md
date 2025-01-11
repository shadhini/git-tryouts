---
icon: pen
---

# Edit already pushed commits to the remote repository

## Changing authorship of pushed commits

{% hint style="warning" %}
This should be done with caution, especially if the repository is shared with other collaborators.&#x20;
{% endhint %}



### Steps to Amend the Commit Author

1.  **Ensure You Are in the Correct Repository**: Navigate to your repository's directory:

    ```sh
    cd /path/to/your/repository
    ```


2.  **Checkout the Branch with the Commit**: Make sure you are on the branch with the commit you want to amend:

    ```sh
    git checkout your-branch-name
    ```


3.  **Amend the Commit Author**: Use the following command to amend the author of the most recent commit:

    ```sh
    git commit --amend --author="New Author Name <new-author-email@example.com>"
    ```

    Replace `"New Author Name <new-author-email@example.com>"` with the correct author details.

#### Example Command:

```sh
git commit --amend --author="Amal <amal@gmail.com>"
```



### Interactive Rebase for Multiple Commits:

If you need to change the author for multiple commits, you can use an interactive rebase:

1.  **Start an Interactive Rebase**:

    ```sh
    git rebase -i HEAD~n
    ```

    Replace `n` with the number of commits you want to edit.


2.  **Mark Commits for Editing**: In the interactive rebase editor, change `pick` to `edit` for the commits you want to amend.

    ```
    edit <commit-hash> Commit message 1
    edit <commit-hash> Commit message 2
    ```


3.  **Amend Each Commit**: For each commit, run:

    ```sh
    git commit --amend --author="New Author Name <new-author-email@example.com>"
    git rebase --continue
    ```


4.  **Force Push the Changes**: After amending the commits, force-push the changes to the remote repository:

    ```sh
    git push --force origin your-branch-name
    ```



### End to End Scenario Example

```sh
jwt_validation/custom-grant-handlers on  main is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 
❯ git rebase -i HEAD~2
hint: Waiting for your editor to close the file... error: There was a problem with the editor 'vi'.


jwt_validation/custom-grant-handlers on  main is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 took 6m11s 
❯ git rebase -i HEAD~2
error: invalid line 2: git commit --amend --author="a@b.com"
You can fix this with 'git rebase --edit-todo' and then run 'git rebase --continue'.
Or you can abort the rebase with 'git rebase --abort'.


jwt_validation/oauth2-grant-handlers on  HEAD (b58fc2c) (REBASING) [?] via 💎 v3.1.3 took 36s 
❯ git rebase --edit-todo
edit aa2f7df add configurations
edit 5e12686 add Custom JWT Bearer Grant Handler


jwt_validation/custom-grant-handlers on  HEAD (b58fc2c) (REBASING) [?] via 💎 v3.1.3 took 5s 
❯ git rebase --continue
Stopped at aa2f7df...  add configurations
You can amend the commit now, with
  git commit --amend 
Once you are satisfied with your changes, run
  git rebase --continue


jwt_validation/custom-grant-handlers on  HEAD (aa2f7df) (REBASING 1/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 
❯ git commit --amend --author="ab <a@b.com>"
[detached HEAD 31ba576] add configurations
 Date: Wed Jan 8 12:45:37 2025 +0530
 4 files changed, 185 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 custom-grant-handlers/pom.xml
 create mode 100644 custom-grant-handlers/src/main/java/config/ConfigUtil.java
 create mode 100644 custom-grant-handlers/src/main/java/config/Constants.java


jwt_validation/custom-grant-handlers on  HEAD (31ba576) (REBASING 1/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 took 15s 
❯ git rebase --continue                                                
Stopped at 5e12686...  add Custom JWT Bearer Grant Handler
You can amend the commit now, with
  git commit --amend 
Once you are satisfied with your changes, run
  git rebase --continue


jwt_validation/custom-grant-handlers on  HEAD (6fe6d17) (REBASING 2/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 
❯ git commit --amend --author="ab <a@b.com>"
[detached HEAD 2d412fa] add Custom JWT Bearer Grant Handler
 Date: Wed Jan 8 12:46:18 2025 +0530
 2 files changed, 172 insertions(+)
 create mode 100644 custom-grant-handlers/src/main/java/CustomJWTBearerGrantHandler.java
 create mode 100644 custom-grant-handlers/src/main/java/internal/CustomJWTBearerGrantHandlerComponent.java


jwt_validation/custom-grant-handlers on  HEAD (2d412fa) (REBASING 2/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 took 6s 
❯ git rebase --continue                                                
Successfully rebased and updated refs/heads/main.


jwt_validation/custom-grant-handlers on  main [⇕] is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 
❯ git push --force origin main
Enumerating objects: 35, done.
Counting objects: 100% (35/35), done.
Delta compression using up to 10 threads
Compressing objects: 100% (14/14), done.
Writing objects: 100% (34/34), 6.08 KiB | 3.04 MiB/s, done.
Total 34 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/dvtechlab/sampathbank_enhanced_jwt_validation.git
 + 5e12686...2d412fa main -> main (forced update)


jwt_validation/custom-grant-handlers on  main is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 
❯ git push --force origin main
Everything up-to-date
```





\
