#### The Planet's Prestige

#### Challenge Submission

> file : A Hope to CoCanDa.eml

Using Mozilla Thunderbird,  Message Header Analyzer

#### Questions

##### 1) What is the email service used by the malicious actor? 

Email headers contain information about the source of the email, and where it has traveled in order to land in your inbox. The email was sent from IP 93.99.104.210, with the sending domain.

```
Received: from localhost (emkei.cz. [93.99.104.210])
        by mx.google.com with ESMTPS id s16si170171wmj.176.2021.01.25.22.41.18
        for <themajoronearth@gmail.com>
        (version=TLS1_2 cipher=ECDHE-ECDSA-CHACHA20-POLY1305 bits=256/256);
        Mon, 25 Jan 2021 22:41:18 -0800 (PST)
```

**Answer:** emkei.cz

##### 2) What is the Reply-To email address? 

```
Reply-To: negeja3921@pashter.com
```

**Answer:**negeja3921@pashter.com

##### 3) What is the filetype of the received attachment which helped to continue the investigation?

The email attachment arrived as a pdf file, however a browser cannot properly view the PDF. This is because the PDF is actually a zip file. This could be discovered if the file is opened in a text editor, names of contained files will appear, implying that this is a zip file.

**Answer:** .zip

##### 4) What is the name of the malicious actor? 

By using exiftool, metadata about the PDF can be discovered, where other tools might only identify anticipated metadata fields based on the file type. One of the metadata fields includes the author of this document.

```
$ cd PuzzleToCoCanDa\PuzzleToCoCanDa
$ exiftool GoodJobMajor

ExifTool Version Number         : 12.28
File Name                       : GoodJobMajor
Directory                       : .
File Size                       : 28 KiB
File Modification Date/Time     : 2021:07:06 07:56:55-07:00
File Access Date/Time           : 2021:07:06 08:01:08-07:00
File Creation Date/Time         : 2021:01:26 10:14:22-08:00
File Permissions                : -rw-rw-rw-
File Type                       : PDF
File Type Extension             : pdf
MIME Type                       : application/pdf
PDF Version                     : 1.5
Linearized                      : No
Author                          : Pestero Negeja
Producer                        : Skia/PDF m90
Page Count                      : 1

```

**Answer:** Pestero Negeja

##### 5) What is the location of the attacker in this Universe?

```
Both of the excel sheets were exported as a text file to make it easy to read data since there are thousands of entry columns in the excel sheet.
Looking into the output of 2nd file:
`VGhlIE1hcnRpYW4gQ29sb255LCBCZXNpZGUgSW50ZXJwbGFuZXRhcnkgU3BhY2Vwb3J0Lg==`

base64 decode > The Martian Colony, Beside Interplanetary Spaceport
```

**Answer:** The Martian Colony, Beside Interplanetary Spaceport

##### 6) What could be the probable C&C domain to control the attacker’s autonomous bots?

```
Since all mail that responds to this email goes to the listed Reply-To, it is probable that the autonomous bots are controlled under the same domain, and are listening for events sent by that domain.
```

**Answer:** pashter.com

