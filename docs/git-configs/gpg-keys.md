---
icon: key
---

# GPG Keys

**`GPG`** (**GNU Privacy Guard**) keys are used to sign commits and tags in Git repositories, providing cryptographic assurance of the identity of the author.&#x20;



## Setting Up GPG Keys to Sign Commits

#### Step 1: Install GPG

On macOS:

```sh
brew install gpg
```

#### Step 2: Generate a GPG Key pair

```sh
gpg --full-generate-key
```

Follow the prompts to configure your key:

1. **Key Type**: Choose `(1) RSA and RSA (default)`.
2. **Key Size**: Choose `4096`.
3. **Key Expiration**: Choose the expiration period or `0` for no expiration.
4. **User ID Information**: Enter your name, email address, and an optional comment.
5. **Passphrase**: Enter a secure passphrase to protect your key.



#### Step 3: List Your GPG Keys

```sh
gpg --list-secret-keys --keyid-format LONG
```

This will show output similar to:

```
/home/user/.gnupg/secring.gpg
------------------------------
sec   4096R/<YOUR_KEY_ID> 2025-01-08 [expires: 2026-01-07]
uid                          Your Name <your-email@example.com>
ssb   4096R/<SUBKEY_ID> 2025-01-08
```

Find the key ID of the key you want to use. It will look something like this:

```
/home/user/.gnupg/secring.gpg
------------------------------
sec   4096R/ABC123DEF 2025-01-08 [expires: 2026-01-07]
uid                          Your Name <your-email@example.com>
ssb   4096R/12345678 2025-01-08
```

The key ID in this example is `ABC123DEF`.





#### Step 4: Configure Git to Use Your GPG Key for signing commits

1.  Set the GPG Key:

    ```sh
    git config --global user.signingkey <YOUR_KEY_ID>
    ```
2.  Tell Git to Sign All Commits (optional):

    ```sh
    git config --global commit.gpgSign true
    ```

#### Step 4.2: Configure Git to use your GPG key for signing commits only for a specific repository

1.  Navigate to Your Repository:

    ```sh
    cd /path/to/your/repository
    ```
2.  Set the User Signing Key: Configure the repository to use the specific GPG key by running:

    ```sh
    git config user.signingkey ABC123DEF
    ```
3.  Enable Commit Signing for the Repository: Set Git to automatically sign commits for this repository:

    ```sh
    git config commit.gpgSign true
    ```
4.  Check the Configuration: Verify that the signing key and commit signing are set up correctly for this repository:

    ```sh
    git config --get user.signingkey
    git config --get commit.gpgSign
    ```





#### Step 5: Add Your GPG Key to GitHub

1.  Export Your GPG Public Key:

    ```sh
    gpg --armor --export <YOUR_KEY_ID>
    ```
2. Copy the Output and go to GitHub:
   * Go to [GitHub GPG keys settings](https://github.com/settings/keys).
   * Click on "New GPG key".
   * Paste the copied GPG key into the provided field and click "Add GPG key".



#### Step 6: Sign Your Commits and Tags

*   Sign a Commit:

    ```sh
    git commit -S -m "Your commit message"
    ```
*   Sign a Tag:

    ```sh
    git tag -s v1.0 -m "Version 1.0"
    ```





#### Verify Signed Commits

```sh
git log --show-signature
```





### If your git sign and commit attempt is not prompting for the GPG passphrase and is returning an error...

1.  Ensure that the GPG agent is running and properly configured to cache your passphrase.

    1.  **Configure GPG to Use the Agent**:&#x20;

        * Ensure that your GPG configuration file (`~/.gnupg/gpg.conf`) includes the following line to use the GPG agent:&#x20;
        * If the `~/.gnupg/gpg.conf` file doesn't exist, then create it and add the following line.

        ```
        use-agent
        ```



    **Restart the GPG agent to apply the changes**:&#x20;

    ```sh
    gpgconf --kill gpg-agent
    gpgconf --launch gpg-agent
    ```


2.  **Configure GPG Agent for Caching**: Ensure that your GPG agent configuration file (`~/.gnupg/gpg-agent.conf`) includes the following settings to cache the passphrase:

    ```
    default-cache-ttl 600
    max-cache-ttl 7200
    ```



    After modifying the file, reload the GPG agent:

    ```sh
    gpgconf --reload gpg-agent
    ```




3.  **Use `pinentry` Program**: Ensure that you have a `pinentry` program installed (e.g., `pinentry-gnome3`, `pinentry-mac`, `pinentry-curses`). This program is responsible for prompting you for the passphrase.

    ```sh
    brew install pinentry-mac
    ```



    You can specify the `pinentry` program to use in your `~/.gnupg/gpg-agent.conf`:

    ```
    pinentry-program /opt/homebrew/bin/pinentry-mac
    ```





    **Restart the GPG agent to apply the changes**:&#x20;

    ```sh
    gpgconf --kill gpg-agent
    gpgconf --launch gpg-agent
    ```







