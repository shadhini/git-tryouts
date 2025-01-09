---
icon: pen
---

# Edit already pushed commits to the remote repository

### Changing authorship of pushed commits

{% hint style="warning" %}
This should be done with caution, especially if the repository is shared with other collaborators.&#x20;
{% endhint %}



#### Steps to Amend the Commit Author

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
git commit --amend --author="Shadhini D <shadhini@dvtechlabs.com>"
```

#### Interactive Rebase for Multiple Commits:

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

#### Summary:

* Use `git commit --amend --author="New Author Name <new-author-email@example.com>"` to change the author of the most recent commit.
* For multiple commits, use `git rebase -i` to interactively edit and amend the commits.
* Force-push the changes to the remote repository after amending the commits.

By following these steps, you should be able to correct the syntax error and successfully amend the commit author.





sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  main is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3&#x20;

❯ git rebase -i HEAD\~2

hint: Waiting for your editor to close the file... error: There was a problem with the editor 'vi'.

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  main is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 took 6m11s&#x20;

❯ git rebase -i HEAD\~2

error: invalid line 2: git commit --amend --author="shadhini@dvtechlabs.com"

error: invalid line 3: git rebase --continue

error: invalid line 6: git commit --amend --author="shadhini@dvtechlabs.com"

error: invalid line 7: git rebase --continue

You can fix this with 'git rebase --edit-todo' and then run 'git rebase --continue'.

Or you can abort the rebase with 'git rebase --abort'.

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (b58fc2c) (REBASING) \[?] via 💎 v3.1.3 took 35s&#x20;

❯ git rebase -i HEAD\~2

fatal: It seems that there is already a rebase-merge directory, and

I wonder if you are in the middle of another rebase.  If that is the

case, please try

&#x20;       git rebase (--continue | --abort | --skip)

If that is not the case, please

&#x20;       rm -fr ".git/rebase-merge"

and run me again.  I am stopping in case you still have something

valuable there.

\
\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (b58fc2c) (REBASING) \[?] via 💎 v3.1.3&#x20;

❯ git rebase --edit-todo&#x20;

error: invalid line 2: git commit --amend --author="shadhini@dvtechlabs.com"

error: invalid line 3: git rebase --continue

error: invalid line 6: git commit --amend --author="shadhini@dvtechlabs.com"

error: invalid line 7: git rebase --continue

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (b58fc2c) (REBASING) \[?] via 💎 v3.1.3 took 36s&#x20;

❯ git rebase --edit-todo

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (b58fc2c) (REBASING) \[?] via 💎 v3.1.3 took 5s&#x20;

❯ git rebase --continue

Stopped at aa2f7df...  add configurations

You can amend the commit now, with

\


&#x20; git commit --amend&#x20;

\


Once you are satisfied with your changes, run

\


&#x20; git rebase --continue

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (aa2f7df) (REBASING 1/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3&#x20;

❯ git commit --amend --author="shadhini@dvtechlabs.com"

fatal: --author 'shadhini@dvtechlabs.com' is not 'Name \<email>' and matches no existing author

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (aa2f7df) (REBASING 1/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3&#x20;

❯ git commit --amend --author="shadhini-dvtl \<shadhini@dvtechlabs.com>"

\[detached HEAD 31ba576] add configurations

&#x20;Date: Wed Jan 8 12:45:37 2025 +0530

&#x20;4 files changed, 185 insertions(+)

&#x20;create mode 100644 .gitignore

&#x20;create mode 100644 oauth2-grant-handlers/pom.xml

&#x20;create mode 100644 oauth2-grant-handlers/src/main/java/org/sampathbank/carbon/identity/oauth2/grant/jwt/config/ConfigUtil.java

&#x20;create mode 100644 oauth2-grant-handlers/src/main/java/org/sampathbank/carbon/identity/oauth2/grant/jwt/config/Constants.java

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (31ba576) (REBASING 1/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 took 15s&#x20;

❯ git rebase --continue                                               &#x20;

Stopped at 5e12686...  add Custom JWT Bearer Grant Handler and it's component

You can amend the commit now, with

\


&#x20; git commit --amend&#x20;

\


Once you are satisfied with your changes, run

\


&#x20; git rebase --continue

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (6fe6d17) (REBASING 2/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3&#x20;

❯ git commit --amend --author="shadhini-dvtl \<shadhini@dvtechlabs.com>"

\[detached HEAD 2d412fa] add Custom JWT Bearer Grant Handler and it's component

&#x20;Date: Wed Jan 8 12:46:18 2025 +0530

&#x20;2 files changed, 172 insertions(+)

&#x20;create mode 100644 oauth2-grant-handlers/src/main/java/org/sampathbank/carbon/identity/oauth2/grant/jwt/CustomJWTBearerGrantHandler.java

&#x20;create mode 100644 oauth2-grant-handlers/src/main/java/org/sampathbank/carbon/identity/oauth2/grant/jwt/internal/CustomJWTBearerGrantHandlerComponent.java

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  HEAD (2d412fa) (REBASING 2/2) is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3 took 6s&#x20;

❯ git rebase --continue                                               &#x20;

Successfully rebased and updated refs/heads/main.

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  main \[⇕] is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3&#x20;

❯ git push --force origin main

Enumerating objects: 35, done.

Counting objects: 100% (35/35), done.

Delta compression using up to 10 threads

Compressing objects: 100% (14/14), done.

Writing objects: 100% (34/34), 6.08 KiB | 3.04 MiB/s, done.

Total 34 (delta 1), reused 0 (delta 0), pack-reused 0

remote: Resolving deltas: 100% (1/1), done.

To https://github.com/dvtechlab/sampathbank\_enhanced\_jwt\_validation.git

&#x20;\+ 5e12686...2d412fa main -> main (forced update)

\


sampathbank\_enhanced\_jwt\_validation/oauth2-grant-handlers on  main is 📦 v1.0.0 via ☕ v1.8.0 via 💎 v3.1.3&#x20;

❯ git push --force origin main

Everything up-to-date

\
