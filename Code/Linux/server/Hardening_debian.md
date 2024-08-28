from a fresh install:
1. `apt update && apt upgrade -y`
2. install [[ufw]], [[fail2ban]], unattended-upgrades, [[sudo]]
3. configure automatic security updates: `sudo dpkg-reconfigure --priority=low unattended-upgrades`
4.  set up [[ufw]]
5. change [[sshd_config]], change default port, disable root login, disable password auth, allowusers only one. and restart `systemctl restart ssh`
6. setup [[fail2ban]]
7.  mayyyybee secure [[shared_memory|shared memory]] with `tmpfs /run/shm tmpfs defaults,noexec,nosuid 0 0`
8. install [[acct]] for process accounting and systemctl start + enable it
9. install [[auditd]] then start + enable
10. install [[logwatch]]
11. 