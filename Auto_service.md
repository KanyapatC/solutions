# Resolve service not start automatic

Solution-1

```
Go to Start > Run > and type regedit

Navigate to: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control

With the control folder selected, right click in the pane on the right and select new DWORD Value

Name the new DWORD: ServicesPipeTimeout

Right-click ServicesPipeTimeout, and then click Modify

Click Decimal, type '180000', and then click OK
```

Solution-2

Open cmd with administrator

```
sc config "SVCNAME" start= delayed-auto
```