
## Targeted Packet Sniffing

![[Screenshot 2025-03-05 163014.png]]
Command used to intercept the traffic for a particular BSSID : `airodump-ng --bssid <bssid> --channel <number> --write <filename> <interface-name>`

Then this will give `.cap` file as the output and we can use Wireshark. But we won't get any good results because everything must be encrypted and hence we need to crack the encryption in order to see anything useful on Wireshark.

## De-authentication Attack

![[Screenshot 2025-03-05 180420.png]]

First, we'll pretend to be the client to the Router by imitating the MAC Address of the actual client.
![[Screenshot 2025-03-05 180515.png]]

Then we'll pretend to be the router for the actual Client saying that the client will get disconnected by imitating the MAC Address as of Router.
![[Screenshot 2025-03-05 180603.png]]


Now to do so, we'll do it using `aireplay-ng`, using the command : `aireplay-ng --deauth <number-of-deauthentication-packets> -a <mac-of-tagrget-network> -c <mac-of-client> <name-of-wireless-adpater-in-monitor-mode>`
Provide a very high number of packets so that it keeps the client and router disconnected. This command fails if we don't use `airodump-ng` parallel to it.





