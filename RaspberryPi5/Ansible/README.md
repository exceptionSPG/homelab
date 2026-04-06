# Ansible Playbooks

## Adding multiple WiFi networks
Playbook: playbooks/addWifi.yml
      This Playbook takes conn\_name, ssid, and psk (password) values from variables/wifi\_profiles.yml file and adds them to our raspberry pi host. It also uses `isDebug` variable (controlled from commandline) to show connections before and after it adds. 

To run:
    `ansible-playbook  tasks/addWifi.yml -i inventory --extra-vars "isDebug=true"`

`nmcli` 

```bash
nmcli
nmcli dev status #to check status of all interfaces
nmcli d wifi list
nmcli con  # Get the NAME of the WiFi connection
nmcli con down "connection_name_here"

sudo nmcli d wifi connect "ssid_here" password "password_here" ifname wlan1



nmcli device show #to show details of known devices
nmcli connection show # get an overview on active connection profiles.


#Add wifi connection profile
sudo nmcli connection add type wifi con-name "added-o2-24" ifname wlan0 ssid "o2-WLAN-2.4GHz-3BEE"

# modify password for just added connection profile
 sudo nmcli connection modify "added-o2-24" wifi-sec.key-mgmt wpa-psk wifi-sec.psk "YOUR_WIFI_PASSWORD"

# connect to new connection profile, without putting down the current one:
sudo nmcli connection up <con-name>
```



