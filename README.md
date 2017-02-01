# Raspberry Pi als WiFi Access Point

Die komplette Konfiguration wird von einem tool namens [Ansible](https://www.ansible.com/) in einem Befehl erledigt.

1. Installiere ein frisches [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) auf eine mindestes 4GB große SD-Karte.
2. Lege die Karte in einen Raspberry Pi 3 (oder Version 2 mit USB-Wifi-Stick) und fahre ihn hoch
3. Installiere Ansible: `sudo apt-get install ansible`
4. Klone dieses Repository: `git clone https://github.com/jsphpl/ansible-raspi-accesspoint`
5. Wechsle in den frisch erstellten Ordner: `cd ansible-raspi-accesspoint`
6. Installiere den Access Point mit Standard-Einstellungen: `ansible-playbook access-point.yml -e target=local`

