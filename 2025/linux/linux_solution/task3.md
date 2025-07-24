# Task 3: Log File Analysis with AWK, Grep, and Sed

## Objective

1. Download the `Linux_2k.log` file from the LogHub GitHub repository.
2. Extract insights using the following commands:
   - Use `grep` to find all occurrences of the word "error".
   - Use `awk` to extract timestamps and log levels.
   - Use `sed` to replace all IP addresses with `[REDACTED]` for security.

---

### downloading the file 
```bash
vim Log_file.txt
```

access the repository and copy the data from `Linux_2k.log` file

paste the data in `log_file.txt`

### Using `grep` coomand 

loate `log_file.txt`

```bash
grep -i "error" log_file.txt
```

The output will not show anything as upon researching, its found that the error message is "authentication failure"

```bash
grep -i "authentication failure" log_file.txt
```
OR

```bash
grep -i "failure" log_file.txt
```

### using `awk`to extract timestamp and log level 

Use the following command to fileter the data according to timestamp and log level

```bash
aek '/failure/ {print $1,$2,$3,$5,$6,$7}' log_file.txt
```
The output will be

```bash
Jul 26 07:02:27 combo sshd(pam_unix)[28842]: authentication failure;
Jul 26 07:02:35 combo sshd(pam_unix)[28844]: authentication failure;
Jul 26 07:02:37 combo sshd(pam_unix)[28846]: authentication failure;
Jul 26 07:02:45 combo sshd(pam_unix)[28848]: authentication failure;
Jul 26 07:02:47 combo sshd(pam_unix)[28850]: authentication failure;
Jul 26 07:02:55 combo sshd(pam_unix)[28852]: authentication failure;
Jul 26 07:02:57 combo sshd(pam_unix)[28854]: authentication failure;
Jul 26 07:03:05 combo sshd(pam_unix)[28856]: authentication failure;
Jul 26 07:03:07 combo sshd(pam_unix)[28858]: authentication failure;
Jul 26 07:03:15 combo sshd(pam_unix)[28860]: authentication failure;
Jul 26 07:03:17 combo sshd(pam_unix)[28862]: authentication failure;
Jul 26 07:03:26 combo sshd(pam_unix)[28864]: authentication failure;
Jul 26 07:03:27 combo sshd(pam_unix)[28866]: authentication failure;
Jul 26 07:03:35 combo sshd(pam_unix)[28868]: authentication failure; 
Jul 26 07:03:37 combo sshd(pam_unix)[28870]: authentication failure; 
Jul 26 07:03:45 combo sshd(pam_unix)[28872]: authentication failure;

```
### Using `sed` to replace all IP address as `REDACTED`

using the following command to replace all IP address

```bash
sed -E 's/([0-9]{1,3}\.){3}[0-9]{1,3}/REDACTED/g' log_file.txt
```

The output will be
```bash
Jul 26 07:02:27 combo sshd(pam_unix)[28842]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:02:35 combo sshd(pam_unix)[28844]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:02:37 combo sshd(pam_unix)[28846]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:02:45 combo sshd(pam_unix)[28848]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:02:47 combo sshd(pam_unix)[28850]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:02:55 combo sshd(pam_unix)[28852]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:02:57 combo sshd(pam_unix)[28854]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:05 combo sshd(pam_unix)[28856]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:07 combo sshd(pam_unix)[28858]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:15 combo sshd(pam_unix)[28860]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:17 combo sshd(pam_unix)[28862]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:26 combo sshd(pam_unix)[28864]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:27 combo sshd(pam_unix)[28866]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:35 combo sshd(pam_unix)[28868]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:37 combo sshd(pam_unix)[28870]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:45 combo sshd(pam_unix)[28872]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:47 combo sshd(pam_unix)[28874]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:55 combo sshd(pam_unix)[28876]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:03:57 combo sshd(pam_unix)[28878]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:04:02 combo sshd(pam_unix)[28880]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:04:05 combo sshd(pam_unix)[28882]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:04:07 combo sshd(pam_unix)[28884]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
Jul 26 07:04:12 combo sshd(pam_unix)[28886]: authentication failure; logname= uid=0 euid=0 tty=NODEVssh ruser= rhost=REDACTED  user=root
```
