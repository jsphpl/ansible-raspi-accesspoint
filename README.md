# Raspberry Pi als WiFi Access Point

Die komplette Konfiguration wird von einem tool namens [Ansible](https://www.ansible.com/) in einem Befehl erledigt.

1. Installiere ein frisches [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) auf eine mindestes 4GB große SD-Karte
2. Lege die Karte in einen Raspberry Pi 3 (oder Version 2 mit USB-Wifi-Stick) und fahre ihn hoch
3. Installiere Ansible: `sudo apt-get install ansible`
4. Klone dieses Repository: `git clone https://github.com/jsphpl/ansible-raspi-accesspoint`
5. Wechsle in den frisch erstellten Ordner: `cd ansible-raspi-accesspoint`
6. Passe die Einstellungen für den Accesspoint in der Datei `group_vars/all.yml` an
7. Installiere den Access Point mit Standard-Einstellungen: `ansible-playbook access-point.yml -e target=local`

# Raspberry Pi as a WiFi access point

The entire configuration is managed by a tool called [Ansible](https://www.ansible.com/) in just one command.

1. Install a fresh [Raspbian](https://www.raspberrypi.org/downloads/raspbian/) on an SD card with at least 4GB
2. Put the sd card into a Raspberry Pi 3 (or version 2 with a USB-Wifi-Stick) and boot it
3. Install Ansible: `sudo apt-get install ansible`
4. Clone this Repository: `git clone https://github.com/jsphpl/ansible-raspi-accesspoint`
5. Change into the freshly created directory: `cd ansible-raspi-accesspoint`
6. Adjust the settings for the access point in `group_vars/all.yml`
7. Set up the access point with the default settings: `ansible-playbook access-point.yml -e target=local`

