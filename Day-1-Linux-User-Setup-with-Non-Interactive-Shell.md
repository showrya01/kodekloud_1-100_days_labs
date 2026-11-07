# Day 1: Linux User Setup with Non-Interactive Shell

### Solution

1. Connect to the server specified in the lab.
2. Create the user with `/sbin/nologin` as the login shell:

```bash
sudo useradd -s /sbin/nologin <username>
```

3. If the user already exists, update its shell instead:

```bash
sudo usermod -s /sbin/nologin <username>
```

4. Verify the user's shell:

```bash
getent passwd <username>
```

The output should end with:

```text
/sbin/nologin
```

**Note:** Replace `<username>` with the exact username given in the lab. `/sbin/nologin` prevents the account from opening a normal interactive login shell.
