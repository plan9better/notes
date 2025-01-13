[[SSH]] settings and general config

Path: `/etc/ssh/sshd_config`
important settings:
- `Port (not 22)`
- `PermitRootLogin no`
- `PasswordAuthentication no`
- `AllowUsers username`
Also `LogLevel` to VERBOSE, or maybe DEBUG(1-3) but debug only when its just me using the machine since it violates the privacy of users.