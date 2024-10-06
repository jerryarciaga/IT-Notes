If your Windows computer is experiencing random shutdowns, you can look for the instances in **Event Viewer**, filtering out the following codes:

| Event ID | Description                                                                                                                                                    |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 41       | The system has rebooted without cleanly shutting down first. This error could be caused if the system stopped responding, crashed, or lost power unexpectedly. |
| 1074     | When an app or user initiates a system shutdown or restart. This usually precedes the next event ID: 6006.                                                     |
| 6006     | Indicates a proper shutdown with a message "The event log service was stopped."                                                                                |
| 6008     | Logged as an abrupt shutdown with the message "The previous system shutdown at TIME and DATE was unexpected."                                                  |
In PowerShell, you can enter the following command:
```
Get-WinEvent -FilterHashTable @{ LogName= 'System'; ID = 41,1074,6006,6008 }
```

---
Related Links:
[[IT Support Notes/Hardware|Hardware]]
[[Software]]
[Online Article](https://geekflare.com/windows-10-11-random-shutdown-cause)

#hardware #software #troubleshooting #powershell #eventviewer