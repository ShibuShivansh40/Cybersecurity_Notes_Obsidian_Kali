![[Pasted image 20250305155847.png]]
![[Screenshot 2025-03-05 161609.png]]
![[Screenshot 2025-03-05 161634.png]]
![[Screenshot 2025-03-05 161750.png]]

**To change the MAC Address of any Network Interface :**
1. Disable the network interface : `ifconfig wlan0 down`
2. To change the MAC Address : `ifconfig wlan0 hw ether 00:11:22:33:44:55`
3. Enable the network interface : `ifconfig wlan0 up`

To list all the interface : `ifconfig`
To list only Wireless Interfaces : `iwconfig`

**Shifting from Managed Mode to Monitor Mode :**
1. Disable the network interface : `ifconfig wlan0 down`
2. Kill all the processes using the interface : `airmon-ng check kill`
3. To shift : `iwconfig wlan0 mode monitor`
4. Enable the network interface : `ifconfig wlan0 up`


