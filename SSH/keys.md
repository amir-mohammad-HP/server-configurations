# Generate SSH key :

To generate an SSH key in Ubuntu ( origin server ), follow these steps:

### 1. Open a Terminal
Open a terminal window by pressing `Ctrl + Alt + T` or searching for "Terminal" in the applications menu.

### 2. Generate the SSH Key Pair
Run the following command to generate a new SSH key pair:

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

- `-t rsa`: Specifies the type of key to create (in this case, RSA).
- `-b 4096`: Specifies the number of bits in the key (4096 bits is a good, secure size).
- `-C "your_email@example.com"`: Adds a comment to the key, typically your email address.

### 3. Specify the File to Save the Key
You will be prompted to enter a file in which to save the key. Press `Enter` to accept the default location (`~/.ssh/id_rsa`):

```bash
Enter file in which to save the key (/home/your_username/.ssh/id_rsa):
```

### 4. Set a Passphrase (Optional)
You will be prompted to enter a passphrase. This is optional but recommended for added security. If you don't want to set a passphrase, just press `Enter`:

```bash
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
```

### 5. Verify the SSH Key Generation
Once the key is generated, you will see output similar to this:

```bash
Your identification has been saved in /home/your_username/.ssh/id_rsa
Your public key has been saved in /home/your_username/.ssh/id_rsa.pub
The key fingerprint is:
SHA256:your_fingerprint your_email@example.com
The key's randomart image is:
+---[RSA 4096]----+
|                 |
|                 |
|                 |
|                 |
|                 |
|                 |
|                 |
|                 |
|                 |
+----[SHA256]-----+
```

### 6. Add the SSH Key to the SSH Agent (Optional)
If you want to use the SSH key with the SSH agent, you can add it by running:

```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```

### 7. Copy the Public Key to Your Server
To use the SSH key for authentication, you need to copy the public key to your server. You can do this using the `ssh-copy-id` command:

```bash
ssh-copy-id username@remote_host
```

Replace `username` with your remote username and `remote_host` with the remote server's IP address or hostname.

Alternatively, you can manually copy the public key:

```bash
cat ~/.ssh/id_rsa.pub
```

Copy the output and paste it into the `~/.ssh/authorized_keys` file on the `remote server`.

### 8. Test the SSH Connection
Finally, test the SSH connection to ensure everything is working:

```bash
ssh username@remote_host
```

If everything is set up correctly, you should be able to log in without being prompted for a password (unless you set a passphrase).

### Summary
- The private key (`id_rsa`) should be kept secure and never shared.
- The public key (`id_rsa.pub`) can be shared and added to remote servers for authentication.

That's it! You've successfully generated an SSH key in Ubuntu.
