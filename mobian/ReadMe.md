
sudo scp user@192.168.2.249:/usr/share/kbd/consolefonts/ter-128n.psf.gz /usr/share/consolefonts/ter-128n.psf.gz
vi /lib/systemd/system/rc-local.service
sudo vi /etc/rc.local
sudo systemctl enable --now rc-local.service
sudo systemctl status getty@tty1.service
