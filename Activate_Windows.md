# How to Activate Windows Server

Open with administrator for type Windows Server

```
C:\>DISM /online /Get-CurrentEdition
C:\>winver
```

To activate Windows Server with your product key, you need to convert the Evaluation version to Licensed. To check available versions type the following command from an elevated Command Prompt:

```
C:\>DISM /online /Get-TargetEditions

    ServerStandard
    ServerDatacenter
```
To convert the version, type the command:

```
C:\>DISM /online /Set-Edition:ServerStandard /ProductKey:XXXXX-XXXXX-XXXXX-XXXXX-XXXXX /AcceptEula
```

Windows Server, version 1903 and Windows Server, version 1809
Operating system edition 	KMS Client Setup Key
```
Windows Server Datacenter 	6NMRW-2C8FM-D24W7-TQWMY-CWH2D
Windows Server Standard 	N2KJX-J94YW-TQVFB-DG9YT-724CC
```

Windows Server, version 1803
Operating system edition 	KMS Client Setup Key
```
Windows Server Datacenter 	2HXDN-KRXHB-GPYC7-YCKFJ-7FVDG
Windows Server Standard 	PTXN8-JFHJM-4WC78-MPCBR-9W4KR
```

Windows Server, version 1709
Operating system edition 	KMS Client Setup Key
```
Windows Server Datacenter 	6Y6KB-N82V8-D8CQV-23MJW-BWTG6
Windows Server Standard 	DPCNP-XQFKJ-BJF7R-FRC8D-GF6G4
```

Windows Server LTSC/LTSB versions
Windows Server 2019
Operating system edition 	KMS Client Setup Key
```
Windows Server 2019 Datacenter 	WMDGN-G9PQG-XVVXX-R3X43-63DFG
Windows Server 2019 Standard 	N69G4-B89J2-4G8F4-WWYCC-J464C
Windows Server 2019 Essentials 	WVDHN-86M7X-466P6-VHXV7-YY726
```

Windows Server 2016
Operating system edition 	KMS Client Setup Key
```
Windows Server 2016 Datacenter 	CB7KF-BWN84-R7R2Y-793K2-8XDDG
Windows Server 2016 Standard 	WC2BQ-8NRM3-FDDYY-2BFGV-KHKQY
Windows Server 2016 Essentials 	JCKRF-N37P4-C2D82-9YXRT-4M63B
```
