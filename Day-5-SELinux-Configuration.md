# Day 4: SELinux Configuration

## Solution

1.  Install the required SELinux packages:

    ``` bash
    sudo yum install -y selinux-policy selinux-policy-targeted
    ```

2.  Edit the SELinux configuration:

    ``` bash
    sudo vi /etc/selinux/config
    ```

3.  Set:

    ``` ini
    SELINUX=disabled
    SELINUXTYPE=targeted
    ```

4.  Save the file. Do not reboot; the maintenance reboot is already
    scheduled.

## Verify

``` bash
grep '^SELINUX=' /etc/selinux/config
```

Expected output:

``` text
SELINUX=disabled
```

**Note:** Use `disabled`, not `disable`. `getenforce` reports the
current runtime status; `/etc/selinux/config` controls the setting
applied after reboot.
