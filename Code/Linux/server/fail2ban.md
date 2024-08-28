bans an ip when it detects suspicious traffic such as too many requests.

basic setup: 
- `sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local`
- `sudo nano /etc/fail2ban/jail.local`
- configure as needed
- start with `systemctl start fail2ban` and `systemctl enable fail2ban`
- 