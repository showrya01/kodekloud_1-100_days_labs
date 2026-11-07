# Day 2: Temporary User Setup with Expiry

### Solution

1. Connect to the server specified in the lab.
2. Create the user with the required account-expiry date:

```bash
sudo useradd -e <YYYY-MM-DD> <username>
```

3. If the user already exists, set its expiry date:

```bash
sudo usermod -e <YYYY-MM-DD> <username>
```

4. Verify the account expiry:

```bash
sudo chage -l <username>
```

Check the **Account expires** line. It should show the date specified in the lab.

**Note:** Replace `<username>` and `<YYYY-MM-DD>` with the exact values given in the lab. The `-e` option sets account expiry; it does not set password expiry.
