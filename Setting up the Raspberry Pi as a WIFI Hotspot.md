# Setting up the Raspberry Pi as a WIFI Hotspot

## Install hostapd & udhcpd

```bash
sudo apt-get install hostapd udhcpd
```

## Set up Access Point

`hostapd` is capable of creating a WIFI accesspoint. We can configure many aspects of the hotspot, including name and security settings of the network.

Open the config file in a text editor…

```bash
sudo nano /etc/hostapd/hostapd.conf
```

…and make sure if looks as follows. The values after `ssid=` and `wpa_passphrase=` should be customized, where `ssid` is the name of your WiFi cell and `wpa_passphrase` the password required to connect. Also, you might want to switch the channel, depending on your environment.

```ini
interface=wlan0
driver=nl80211
ssid=My_AP
hw_mode=g
channel=6
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=2
wpa_passphrase=My_Passphrase
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP
```
For an unencrypted Network, use the config below.

```ini
interface=wlan0
ssid=My_AP
hw_mode=g
channel=6
auth_algs=1
wmm_enabled=0
```

Edit `/etc/default/hostapd`:

change `#DAEMON_CONF=""` to `DAEMON_CONF="/etc/hostapd/hostapd.conf"`


## Set up DHCP-Server

```bash
sudo nano /etc/udhcpd.conf
```

```
start           192.168.33.20   #default: 192.168.0.20
end             192.168.33.254  #default: 192.168.0.254
interface       wlan0           #default: eth0
remaining       yes             #default: yes
opt     dns     8.8.8.8 4.2.2.2 # google dns
option  subnet  255.255.255.0
opt     router  192.168.33.1
option  lease   864000          # 10 days of seconds
```

```bash
sudo nano /etc/default/udhcpd
```
change `DHCPD_ENABLED="no"` to `#DHCPD_ENABLED="no"`
 
 
## Configure Network Adapter
 
```bash
sudo ifconfig wlan0 192.168.33.1
```
 
add to `/etc/network/interfaces` and replace the line `iface wlan0 inet dhcp` with:
 
```
iface wlan0 inet static
  address 192.168.33.1
  netmask 255.255.255.0
```

Comment out the following lines:

```
allow-hotplug wlan0
wpa-roam /etc/wpa_supplicant/wpa_supplicant.conf
iface default inet manual
```


## Start everything

### Now

```bash
sudo service hostapd start
sudo service udhcpd start
```

### On Startup

```bash
sudo update-rc.d hostapd enable
sudo update-rc.d udhcpd enable
```


## Enable port forwarding (optional)


## Fix for Edimax EW-7811Un

```bash
cd /usr/sbin
sudo mv /usr/sbin/hostapd /usr/sbin/hostapd.bak
sudo wget http://itwelt.org/downloads/hostapd

sudo chown root:root hostapd
sudo chmod 755 hostapd
```


--
*from: [http://elinux.org/RPI-Wireless-Hotspot](http://elinux.org/RPI-Wireless-Hotspot)*
