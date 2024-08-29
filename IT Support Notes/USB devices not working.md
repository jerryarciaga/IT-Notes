# Check physical hardware
 USB devices not working could be a result of using a bad USB cable, ports or device. Make sure to eliminate those possibilities first by replacing them with known, good equipment.
# Potential driver issues
If it works on a known, good computer, but it doesn't on another, it could be a driver issue. You can try installing a different driver as seen in Device Manager.

In PowerShell, you can list the following devices with issues:
* `Get-PnPDevice -Status Error`
You can try to disable and enable the device, effectively restarting them.
* `Disable-PnPDevice` then `Enable-PnPDevice`
# Registry Editor
It is recommended to try out the earlier options first since editing the Windows Registry can render your computer unusable. You can access the registry editor using either the GUI or PowerShell by simply going to any of the Filesystem Providers. `Get-PSDrive -PSProvider Registry`



---
Related links
[[IT Support Notes/Hardware|Hardware]]

#hardware #troubleshooting #usb #registry-editor #powershell #desktop-support
