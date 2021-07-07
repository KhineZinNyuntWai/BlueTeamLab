#### Network Analysis – Ransomware

#### Challenge Submission

> pcap File ->  /Challenge Files

Using Wireshark, 

#### Questions

##### 1) What is the operating system of the host from which the network traffic was captured? (Look at Capture File Properties, copy the details exactly) 

We can see this question's answer 

```
Statistics-> Capture File Properties
```

**Answer:** 32-bit Windows 7 Service Pack 1, build 7601

##### 2) What is the full URL from which the ransomware executable was downloaded?

```
Filter => http 
> Full URL
```

**Answer:** http://10.0.2.15:8000/safecrypt.exe

##### 3) Name the ransomware executable file?

```
Filter => http 
> Full URL
```

**Answer:** safecrypt.exe

##### 4) What is the MD5 hash of the ransomware?

```
File -> Export Object -> http -> safecypt.exe (save)

PS(cmd) >  Get-Filehash -Path .\safecrypt.exe -Algorithm md5
```

**Answer:** 4a1d88603b1007825a9c6b36d1e5de44

##### 5) What is the name of the ransomware? 

```
search in google
```

**Answer:** TeslaCrypt

##### 6) What is the encryption algorithm used by the ransomware, according to the ransom note? 

```
view in ransom note
```

**Answer:** RSA-1046

##### 7) What is the domain beginning with ‘d’ that is related to ransomware traffic?

```
Filter => dns
```

**Answer:** dunyamuzelerimuzesi.com

##### 8) Decrypt the Tender document and submit the flag

```

```

**Answer:** 

