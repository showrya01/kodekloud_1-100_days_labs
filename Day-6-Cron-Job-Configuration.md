# Day 6: Cron Job Configuration

## Solution

1.  Install the cron package (`cronie`) on the app server:

    ``` bash
    sudo yum install -y cronie
    ```

2.  Start and enable the `crond` service:

    ``` bash
    sudo systemctl start crond
    sudo systemctl enable crond
    ```

3.  Open the root user's crontab:

    ``` bash
    sudo crontab -e
    ```

4.  Add the cron job (runs every 5 minutes):

    ``` text
    */5 * * * * echo hello > /tmp/cron_text
    ```

5.  Save and exit the editor. The new crontab is installed automatically.

## Verify

Check that the service is running:

``` bash
sudo systemctl status crond
```

Expected output:

``` text
Active: active (running)
```

Check that the job is installed:

``` bash
sudo crontab -l
```

Expected output:

``` text
*/5 * * * * echo hello > /tmp/cron_text
```

Wait for the next 5-minute mark, then check the output file:

``` bash
cat /tmp/cron_text
```

Expected output:

``` text
hello
```

**Note:** `crond` must be running, or the job will never fire. The file
will not appear in `/tmp` immediately; it is created at the next
`*/5` interval. `sudo crontab -e` edits the **root** crontab, so the
job runs as root and `/tmp/cron_text` is owned by root. The `>`
operator overwrites the file on each run; use `>>` to append instead.
