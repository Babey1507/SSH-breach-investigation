kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ wc -l auth-sample2.log 
27 auth-sample2.log
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -i "failed password" auth-sample2.log | wc -l
24
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -iv "failed password" auth-sample2.log 
Oct 20 10:09:02 ubuntu sshd[3201]: Disconnected from authenticating user admin 203.0.113.45 port 51235 [preauth]
Oct 20 10:28:19 ubuntu sshd[3356]: Accepted password for kent from 198.51.100.23 port 44603 ssh2
Oct 20 10:32:44 ubuntu sshd[3401]: Connection closed by 198.51.100.23 port 44610 [preauth]
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -iv "failed password" auth-sample2.log | wc -l
3
**********************
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -i "kent" auth-sample2.log 
Oct 20 10:28:12 ubuntu sshd[3350]: Failed password for kent from 198.51.100.23 port 44601 ssh2
Oct 20 10:28:15 ubuntu sshd[3352]: Failed password for kent from 198.51.100.23 port 44602 ssh2
Oct 20 10:28:19 ubuntu sshd[3356]: Accepted password for kent from 198.51.100.23 port 44603 ssh2
***** THIS MUST BE A BRUTE-FORCE ATTACK, BECAUSE THE USER LOGGED IN SUCCESSFULLY IN 3 ATTEMPTS ( 2 FAILED AND 1 SUCCESSFUL) WITHIN 7 SECONDS WHICH IS TOO QUICK FOR A HUMAN *****
**********************
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -i "password for invalid user" auth-sample2.log |cut -d " " -f11 | sort | uniq -c
      4 admin
      4 guest
      3 oracle
      3 postgres
      4 testuser
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -i "password" auth-sample2.log | grep -iv "invalid user" | cut -d " " -f9 | sort | uniq -c
      3 kent
      4 root
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -i "password for invalid user" auth-sample2.log | cut -d " " -f13 | sort | uniq -c | sort -nr
      8 198.51.100.23
      6 192.0.2.78
      4 203.0.113.45
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ grep -i "password" auth-sample2.log | grep -iv "invalid user" | cut -d " " -f11 | sort | uniq -c | sort -nr
      4 203.0.113.45
      3 198.51.100.23
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ head -n1 auth-sample2.log 
Oct 20 10:02:11 ubuntu sshd[3101]: Failed password for invalid user admin from 203.0.113.45 port 51231 ssh2
kent@kent-VirtualBox-UbuntuLab:~/lab/lab2$ tail -n1 auth-sample2.log 
Oct 20 10:32:44 ubuntu sshd[3401]: Connection closed by 198.51.100.23 port 44610 [preauth]
