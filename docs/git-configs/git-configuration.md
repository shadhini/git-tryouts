---
icon: square-sliders
---

# Git Configuration

## Configuring `user.name` and `user.email`&#x20;

### Configuring for a Specific Repository

1.  Navigate to the Repository:

    <pre class="language-bash"><code class="lang-bash"><strong>cd path/to/your/repository
    </strong></code></pre>


2.  Set the Repository-Specific Configuration:

    ```sh
    git config user.name "Your Name"
    ```



    ```sh
    git config user.email "your.email@example.com"
    ```

### Configuring as Global Settings

<pre class="language-bash"><code class="lang-bash"><strong>git config --global user.name "Your Name"
</strong></code></pre>

```sh
git config --global user.email "your.email@example.com"
```



### Verifying the Configuration

*   To verify the repository-specific configuration:

    ```sh
    git config user.name
    git config user.email
    ```
*   To verify the global configuration:

    ```sh
    git config --global user.name
    git config --global user.email
    ```



