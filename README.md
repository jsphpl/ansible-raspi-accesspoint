# Raspberry Pi als WiFi Access Point

## 1. Raspbian installieren

Wir installieren ein frisches [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) auf eine 8GB-SD-Karte.

## 2. Benötigte Pakete installieren

Als erstes installieren wir die benötigten Pakete mit apt-get:

```bash
apt-get update
apt-get install hostapd udhcpd
```

## 3. Hotspot einrichten

Wir konfigurieren hostapd, 

## 4. DHCP-Server einrichten

Der DHCP-Server ist dafür zuständig, den Geräten die sich am Hotspot anmelden, IP-Addressen und andere Konfigurationsparameter zuzuweisen.
