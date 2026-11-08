# Day 3: Secure Root SSH Access

### Solution

Perform these steps on **all three app servers**: `stapp01`, `stapp02`, and `stapp03`.

1. Connect to each server using the lab-provided account:

```bash
ssh <user>@stapp01
```

2. Edit the SSH server configuration:

```bash
sudo vi /etc/ssh/sshd_config
```

Set this option (add it if it is missing):

```text
PermitRootLogin no
```

3. Save the file, then validate the SSH configuration:

```bash
sudo sshd -t
```

No output means the configuration passed the syntax check.

4. Restart and verify the SSH service:

```bash
sudo systemctl restart sshd
sudo systemctl status sshd
```

5. Confirm the effective setting:

```bash
sudo sshd -T | grep permitrootlogin
```

Expected output:

```text
permitrootlogin no
```

Repeat the same steps on `stapp02` and `stapp03`.

**Note:** On these servers the service is named `sshd`, not `ssh`. Keep your current SSH session open until you have confirmed the service is running and the setting is `no`.
