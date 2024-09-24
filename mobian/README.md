# ###Begin###
# git clone https://gitlab.com/cherrypicker/buffyboard.git
# cd buffyboard
# git submodule init
# git submodule update
# meson _build
# sudo apt install meson
# meson _build
# sudo apt install cmake
# meson _build
# sudo apt install libinput-dev
# meson compile -C _build
# meson _build
# sudo apt install libxkbcommon-dev
# meson _build
# meson compile -C _build
# sudo chvt 2
# sudo apt install pipenv
# ./regenerate-layouts.sh
# cd ttyescape/
# sudo mkdir -p /etc/conf.d
# sudo cp ttyescape.conf /etc/conf.d/
# sudo mkdir -p /etc/hkdm/config.d/
# sudo cp ttyescape-hkdm.toml /etc/hkdm/config.d/ttyescape.toml
# sudo cp togglevt.sh /usr/bin/
# cd hkdm
# sudo cp hkdm.example.toml /etc/hkdm/config.d/hkdm.example
# sudo cp target/debug/hkdm /usr/bin/
# sudo scp user@192.168.2.249:/etc/systemd/system/hkdm.service .
# sudo cp hkdm.service /etc/systemd/system/hkdm.service
# cd ..
# cd buffyboard
# cd _build/
# sudo cp buffyboard /usr/bin/
# sudo chmod 755 /usr/bin/hkdm
# sudo chmod 755 /usr/bin/buffyboard
# sudo chmod 755 /usr/bin/togglevt.sh

# sudo scp user@192.168.2.249:/usr/share/kbd/consolefonts/ter-128n.psf.gz /usr/share/consolefonts/ter-128n.psf.gz

# vi /lib/systemd/system/rc-local.service

# sudo vi /etc/rc.local

# sudo chmod a+rx /etc/rc.local

# sudo systemctl enable --now rc-local.service

# sudo systemctl status getty@tty1.service

# sudo systemctl unmask phosh

# sudo reboot
# ###Done###

