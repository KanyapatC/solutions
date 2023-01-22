# How to Fix bootmgr on Windows10
For resolve can't access to boot Windows

Command:
```
Bootrec /fixmbr //Edit Master Boot Record
Bootrec /fixboot //Resolve file sytem boot
Bootrec /rebuildbcd //Config Boot Configuration Data new
```

But command above not working
Command:
```
bcdedit /export C:\BCD_Backup
c:
cd boot
attrib bcd -s -h -r
ren c:\boot\bcd bcd.old
bootrec /RebuildBcd
```

Can resolve boot records
Command:
```
chkdsk /f //Verify your disk
sfc /scannow //Verify and fix your system
```