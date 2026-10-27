SSH Brute-Force Investigation — Lab 2
Summary
Investigated a simulated SSH brute-force attack against a Linux server using command-line log analysis (grep, cut, sort, uniq).

Incident Report
On Oct 20, between 10:02:11 and 10:32:44 (a 30-minute 33-second window), the server logged 24 failed SSH login attempts and 1 successful SSH login. The attempts came from 3 source IPs: 198.51.100.23 (10 failed + 1 accepted), 203.0.113.45 (8 failed), and 192.0.2.78 (6 failed). Seven usernames were targeted: admin, guest, oracle, postgres, testuser, root, and kent. The kent account was breached: after 2 failed attempts at 10:28:12 and 10:28:15, it was successfully logged into from 198.51.100.23 at 10:28:19.

Recommendations: change kent's password immediately, disable password authentication and use SSH keys only, and check whether the attacker left any persistence or did anything else with the account.
Detailed evidence (commands and outputs): see evidence.md.
