---
icon: code-merge
---

# Git Rebase

> **`git rebase`**&#x20;
>
> **Reapply Commits**: takes the commits from the current branch and re-applies them on top of another base commit.&#x20;
>
> **Linearize History**: helps in creating a cleaner, linear commit history by moving the entire branch to start from the tip of another branch.&#x20;
>
> * This can make the commit history easier to read and understand.

This is different from `git merge`, which combines changes from two branches along with their commit histories.



## Example Usage

### **Basic Rebase**

If you want to rebase your current branch onto another branch (e.g., `main`):

```sh
git checkout feature-branch
git rebase main
```

This command will take all the commits on `feature-branch` and reapply them on top of `main`.



### **Interactive Rebase**

Interactive rebase allows you to edit commit history, such as squashing commits, reordering them, and more:

```sh
git rebase -i HEAD~n
```

Where `n` is the number of commits you want to rebase interactively. This will open an editor where you can specify actions for each commit.



### Common Rebase Options

*   **`--onto`**: Rebase the current branch onto another branch.

    ```sh
    git rebase --onto newbase oldbase feature
    ```

    This will rebase the commits from `feature` that are not in `oldbase` onto `newbase`.
*   **`--continue`**: Continue the rebase after resolving conflicts.

    ```sh
    git rebase --continue
    ```
*   **`--abort`**: Abort the rebase process and return to the original branch state.

    ```sh
    git rebase --abort
    ```
*   **`--skip`**: Skip the current patch if there are conflicts that you don't want to resolve.

    ```sh
    git rebase --skip
    ```





## Benefits of `git rebase`

1. **Cleaner History**: By creating a linear commit history, it is easier to follow the evolution of a project.
2. **Avoid Merge Commits**: Reduces the number of unnecessary merge commits in the history.
3. **Simplify Collaboration**: When working with others, a cleaner history can make understanding and reviewing changes easier.



## Potential Downsides

* **Rewriting History**: Since `git rebase` rewrites commit history, it's generally advised not to rebase commits that have been pushed to a shared repository.
* **Conflict Resolution**: Rebasing can lead to conflicts, which need to be manually resolved.

