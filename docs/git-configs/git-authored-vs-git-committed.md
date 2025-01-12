---
icon: code-commit
---

# Git Authored Vs Git Committed

1. **Authored**:
   * **Author** refers to the person who originally wrote the code or made the change. This includes the date and time when the author created the change.
   * The author information is recorded in the commit itself and can be different from the committer.
   * Example: If a developer writes a piece of code on their local machine, their details will be recorded as the author of that commit.
2. **Committed**:
   * **Committer** refers to the person who actually added the change to the repository. This includes the date and time when the commit was added to the repository.
   * The committer information is typically added when the commit is pushed to the repository.
   * Example: If the author sends their changes to another developer who then reviews and pushes the changes to the repository, the second developer’s details will be recorded as the committer.

### Viewing Author and Committer Information

```sh
git log --pretty=fuller
```

This will display a detailed log including both the author and committer information for each commit.

#### Example Output

```
commit abcdef1234567890abcdef1234567890abcdef12
Author:     Developer A <author@example.com>
AuthorDate: Mon Jan 1 12:34:56 2023 -0700
Commit:     Developer B <committer@example.com>
CommitDate: Tue Jan 2 15:43:21 2023 -0700

    Add new feature
```



