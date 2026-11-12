# Day 7: Configure Passwordless SSH Access

## Solution

1.  On the jump host, generate an SSH key pair as `thor`:

    ``` bash
    ssh-keygen -t ed25519
    ```

    Accept the default file location. Leave the passphrase empty if
    passwordless, non-interactive access is required.

2.  Copy the public key to each app-server account:

    ``` bash
    ssh-copy-id tony@stapp01
    ssh-copy-id steve@stapp02
    ssh-copy-id banner@stapp03
    ```

    Enter each account's password when prompted. The key is added to
    that user's `~/.ssh/authorized_keys`.

## Verify

From the jump host, test:

``` bash
ssh tony@stapp01
ssh steve@stapp02
ssh banner@stapp03
```

Each connection should work without asking for the account password. Use
`logout` to return to the jump host.

**Note:** Keep the private key (`~/.ssh/id_ed25519`) on the jump host.
Only copy the public key (`~/.ssh/id_ed25519.pub`) to the app servers.
The first connection may ask you to confirm the server's host key.
