### Log Analysis – Compromised WordPress

#### Challenge Submission

> Log Analysis File ->  access.txt

**Q1**: Identify the URI of the admin login panel that the attacker gained access to (include the token) 

**A1**: /wp-login.php?itsec-hb-token=adminlogin

> - http.request.method: POST AND NOT http.response.status_code: 403 AND \*login*

**Q2**: Can you find two tools the attacker used?

**A2**: WPScan AND sqlmap

> Investigate in user_agent fields

**Q3**: The attacker tried to exploit a vulnerability in ‘Contact Form 7’. What CVE was the plugin vulnerable to? (Do some research!)

**A3**:  CVE-2020-35489

> Contact Form 7 Plugin Vulnerability In WordPress -> Google search

**Q4**: What plugin was exploited to get access?

**A4**: simple file list 4.2.2

**Q5**: What is the name of the PHP web shell file? 

**A5**: fr34k.php

> **url.original**: \*.php* AND http.request.method: POST AND NOT http.response.status_code: 404

**Q6** : What was the HTTP response code provided when the web shell was accessed for the final time? 

**A6**: 404

> url.original : /wp-content/uploads/simple-file-list/fr34k.php AND source.ip: 103.69.55.212