---
description: About git garbage collection command
---

# Git Garbage Collection

## Git gc

```bash
git gc
```

> **optimizes the local repository by cleaning up unnecessary files and compressing history, helping maintain its health and performance as it grows**

* **Prune Unreachable Objects:** Removes objects like commits, blobs, and trees that are no longer referenced by any branch or tag.
* **Compress Files:** Packs loose objects into a compact packfile to improve performance and reduce disk usage.
* **Clean Up Temporary Files:** Deletes temporary files and unnecessary data left behind by operations like rebases, merges, and commits.
* **Optimise References:** Compresses the `.git/refs` directory to make the repository metadata more efficient to read and write.

## Command Guide

<table><thead><tr><th width="262">Command</th><th>Description</th></tr></thead><tbody><tr><td><pre class="language-bash"><code class="lang-bash">git gc
</code></pre></td><td>Optimises the local repository by cleaning up unnecessary files and compressing history.<br>Runs as soon a called.<br>In very large repositories, it can take a significant amount of time and resources. Thus, it’s best to run it during off-peak hours.<br>Prunes objects older than 14 days by default.</td></tr><tr><td><pre class="language-bash"><code class="lang-bash">git gc --auto
</code></pre></td><td>Automatically runs under safe conditions.<br>Decides when it’s necessary to run.</td></tr><tr><td><pre class="language-bash"><code class="lang-bash"><strong>git gc --prune=&#x3C;DATE>
</strong></code></pre></td><td>Prunes objects older than the given date.</td></tr><tr><td><pre class="language-bash"><code class="lang-bash"><strong>git fsck
</strong></code></pre></td><td>Check the health of the repository.<br>This helps to identify any corruption or issues that might interfere with garbage collection.</td></tr></tbody></table>

## Best Practices

* Before running `git gc`, you can use `git fsck` to check the health of your repository.&#x20;
* Avoid running `git gc` in shared repositories (like bare repositories on a server) where multiple users might be pushing or pulling simultaneously. Instead, use `git gc --auto`. &#x20;
* Avoid running `git gc` in large repositories during peak hours. Instead, use `git gc --auto` as it decides when it's necessary to run.
* For large or heavily used repositories, consider **scheduling regular garbage collection**, either manually or through automated scripts.
* Be careful with aggressive pruning, as it might remove objects still needed by other repositories or references.
* After running `git gc`, you can monitor the amount of disk space saved by checking the size of the `.git` directory before and after.
