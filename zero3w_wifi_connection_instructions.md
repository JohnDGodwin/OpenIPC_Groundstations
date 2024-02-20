<h3>Setup of autoconnect on boot</h3>

We're going to rely on NetworkManager.<br>
Enter the following, replacing your_SSID and your_password as needed.


`nmcli connection add ifname wlan1 type wifi ssid Your_SSID`

`nmcli connection edit wifi-wlan1`

	nmcli> goto wifi
	nmcli 802-11-wireless> set mode infrastructure
	nmcli 802-11-wireless> back
	nmcli> goto wifi-sec
	nmcli 802-11-wireless-security> set key-mgmt wpa-psk
	nmcli 802-11-wireless-security> set psk Your_Password
	nmcli 802-11-wireless-security> save
	nmcli 802-11-wireless-security> quit
