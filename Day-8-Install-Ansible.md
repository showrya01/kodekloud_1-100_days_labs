# Day 8: Install Ansible

## Solution

1.  Check whether Ansible is already installed:

    ``` bash
    which ansible
    ```

2.  Remove any existing user-level install so it does not shadow the
    global one:

    ``` bash
    pip3 uninstall -y ansible ansible-core
    ```

3.  Install Ansible 4.10.0 globally using `sudo`, so it is available to
    all users on the jump host:

    ``` bash
    sudo pip3 install ansible==4.10.0
    ```

4.  Do not run `pip3 install` without `sudo`. That installs into
    `~/.local` for the current user only.

## Verify

``` bash
pip3 show ansible
```

Expected output:

``` text
Name: ansible
Version: 4.10.0
Location: /usr/local/lib/python3.9/site-packages
```

Confirm the binary is on the global path and reports the bundled core
version:

``` bash
which ansible
ansible --version
```

Expected output:

``` text
/usr/local/bin/ansible
ansible [core 2.11.12]
```

**Note:** Use `==` for the version pin, not `=`. A single `=` gives
`Invalid requirement`. The `Location` line is the quick check for scope:
`/usr/local/lib/...` means a global install, while
`/home/<user>/.local/lib/...` means user-only. Ansible 4.10.0 pulls in
`ansible-core` 2.11.12 automatically. pip warns about running as root;
this is expected here and can be ignored for this task.
