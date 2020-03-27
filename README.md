# Formating-MAC-Address
I wrote this to ensure that regardless of how MAC address was retrieved via WMI (I.E. lower case, :, whatever), It would be the same
#PowerShell

$MacAddr = (((Get-NetAdapter -Physical | Where-Object {$_.PhysicalMediaType -like "802.3"} | Select-Object MacAddress).MacAddress -replace "\W").ToUpper() -replace '(..)','$1-').trim("-")

So here is what happens here
<ol>
  <li>Get the Mac Address for 802.3, which is a wired network adapter.</li>
  <li>Then get just the MAC Address</li>
  <li>Remove all non letters or numbers (-replace("\W")</li>
  <li>Then Upper case everthing</li>
  <li>Then replace every two characters with itself follwed by a dash -replace '(..)','$1-'</li>
  <li>Last remove the final -</li>
  </ol>
  
