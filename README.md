# Formating-MAC-Address
I wrote this to ensure that regardless of how MAC address was retrieved via WMI (I.E. lower case, :, whatever), It would be the same
#PowerShell

$MacAddr = (((Get-NetAdapter -Physical | Where-Object {$_.PhysicalMediaType -like "802.3"} | Select-Object MacAddress).MacAddress -replace "\W").ToUpper() -replace '(..)','$1-').trim("-")
