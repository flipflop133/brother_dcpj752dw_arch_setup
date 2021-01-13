# How to install
Install both packages using "makepkg -si".
Install cups package and enable and start cups.service
Then to connect to your printer through network you need to setup hostname resolution with Avahi:
- Install the Avahi package
- Install the nss-mdns package
- Enable and start avahi-daemon.service
- Install cups package
- Enable and start cups.service and cups.socket
- Edit /etc/nsswitch.conf and change the hosts line to:
hosts: ... mdns_minimal [NOTFOUND=return] resolve ...
- Open UDP port 5353 if you use a firewall
- Run avahi-discover in a terminal and you should see your printer
- With avahi-discover opened, head to localhost:631, go to Administration page and connect as root user then select "Add Printer" and configure your printer either via usb or select your printer in "Discovered Network Printers"
### Links:
- https://wiki.archlinux.org/index.php/Packaging_Brother_printer_drivers
- https://wiki.archlinux.org/index.php/CUPS
- https://wiki.archlinux.org/index.php/Avahi#Hostname_resolution
