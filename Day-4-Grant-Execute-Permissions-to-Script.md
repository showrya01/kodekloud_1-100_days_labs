# Day 4: Grant Execute Permissions to a Script

### Solution

Perform the task on **App Server 3 (`stapp03`)**.

1. Connect to App Server 3:

```bash
ssh banner@stapp03
```

2. Grant the owner, group, and all other users read and execute permissions:

```bash
sudo chmod 755 /tmp/xfusioncorp.sh
```

3. Verify the permissions:

```bash
ls -l /tmp/xfusioncorp.sh
```

Expected permission format:

```text
-rwxr-xr-x
```

4. Test that the script runs directly:

```bash
/tmp/xfusioncorp.sh
```

**Note:** `chmod +x` only adds execute bits. In your terminal, the file became `---x--x--x`, which did not give users read permission, so direct execution failed. `chmod 755` gives the owner read/write/execute and gives the group and other users read/execute.
