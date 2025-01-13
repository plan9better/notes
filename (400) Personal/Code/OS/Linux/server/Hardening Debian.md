from a fresh install:
1. `apt update && apt upgrade -y`
2. install [[Ufw]], [[Fail2ban]], unattended-upgrades, [[Sudo]]
3. configure automatic security updates: `sudo dpkg-reconfigure --priority=low unattended-upgrades`
4.  set up [[Ufw]]
5. change [[SSH Config(Host)]], change default port, disable root login, disable password auth, allowusers only one. and restart `systemctl restart [[ssh]]`
6. setup [[Fail2ban]]
7.  mayyyybee secure [[Shared Memory|shared memory]] with `tmpfs /run/shm tmpfs defaults,noexec,nosuid 0 0`
8. install [[acct]] for process accounting and systemctl start + enable it
9. install [[auditd]] then start + enable
10. install [[logwatch]]
11. 