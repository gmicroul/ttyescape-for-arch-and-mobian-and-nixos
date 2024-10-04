# ###Begin###

#git clone https://gitlab.com/cherrypicker/buffyboard.git

#cd buffyboard

#git submodule init

#git submodule update

#meson _build

#sudo apt install meson

#meson _build

#sudo apt install cmake

#meson _build

#sudo apt install libinput-dev

#meson compile -C _build

#meson _build

#sudo apt install libxkbcommon-dev

#meson _build

#meson compile -C _build

#sudo chvt 2

#sudo apt install pipenv

#./regenerate-layouts.sh

#git clone https://salsa.debian.org/realroot/ttyescape

#cd ttyescape/

#sudo mkdir -p /etc/conf.d

#cd debian

#sudo cp ttyescape.conf /etc/conf.d/

#sudo mkdir -p /etc/hkdm/config.d/

#sudo cp ttyescape-hkdm.toml /etc/hkdm/config.d/ttyescape.toml

#sudo cp togglevt.sh /usr/bin/

#git clone https://gitlab.com/calebccff/hkdm

#cd hkdm

#sudo cp hkdm.example.toml /etc/hkdm/config.d/hkdm.example

#sudo cp target/debug/hkdm /usr/bin/

#sudo scp user@192.168.2.249:/etc/systemd/system/hkdm.service .

#sudo cp hkdm.service /etc/systemd/system/hkdm.service

#cd ..

#cd buffyboard

#cd _build/

#sudo cp buffyboard /usr/bin/

#sudo chmod 755 /usr/bin/hkdm

#sudo chmod 755 /usr/bin/buffyboard

#sudo chmod 755 /usr/bin/togglevt.sh

#sudo scp user@192.168.2.249:/usr/share/kbd/consolefonts/ter-128n.psf.gz /usr/share/consolefonts/ter-128n.psf.gz

#vi /lib/systemd/system/rc-local.service

#sudo vi /etc/rc.local

#sudo chmod a+rx /etc/rc.local

#sudo systemctl enable --now rc-local.service

#sudo systemctl status getty@tty1.service

#sudo systemctl unmask phosh

#sudo reboot

# ###Done###

refer to : https://tinhte.vn/thread/ubuntu-22-04-5-ttyescape-nexus-7-2012-wifi-3g-rev-e1565-kernel-6-1-0-postmarketos-grate.3584471/
Dùng loop để mount 2 partition trong image

# sudo modprobe loop
# sudo losetup -f
# sudo losetup /dev/loop0 /home/[username]/ubuntu-22.04-ttyescape-armhf+asus-grouper-kernel-5.19.0-rc8.img

# sudo partprobe /dev/loop0

# sudo mount -t ext2 -o loop /dev/loop0p1 /media/boot

# sudo mount -t ext4 -o loop /dev/loop0p2 /media/rootfs

Thiết lập chroot

# sudo mount -t proc none /media/rootfs/proc

# sudo mount -o bind /sys /media/rootfs/sys

# sudo mount -o bind /dev /media/rootfs/dev

# sudo mount -o bind /dev/pts /media/rootfs/dev/pts

# sudo chroot /media/rootfs

# apt update && apt upgrade

Các đường dẫn đến thư mục thiết lập như sau:
zram-init:

    /etc/modprobe.d/zram.conf
    /sbin/zram-init
    /usr/bin/zram-init
    /usr/lib/systemd/system (zram-btrfs.service, zram-swap.service, zram-tmp.service, zram-var-tmp.service)
    /usr/share/ (doc, locale, man, zsh)


ttyescape:

    /etc/conf.d/ttyescape.conf
    /etc/hkdm/config.d/ttyescape.toml
    /usr/bin/togglevt.sh


hkdm:

    /etc/hkdm/config.d/hkdm.example
    /usr/bin/hkdm
    /etc/systemd/system/hkdm.service


buffyboard:

    /usr/bin/buffyboard


Cài các gói lệ thuộc( package depends) để hỗ trợ chạy ttyescape, hkdm, buffyboard
git clone https://github.com/vaeth/zram-init

# sudo apt install libevdev2 libinput-bin libinput10 libxkbcommon0 udev

Tạo phân quyền cho ttyescape, hkdm, buffyboard chạy

# sudo chmod 755 /usr/bin/hkdm

# sudo chmod 755 /usr/bin/buffyboard

# sudo chmod 755 /usr/bin/togglevt.sh

# sudo chmod 755 /tmp

# sudo chmod 755 /sbin/zram-init

# sudo chmod 755 /usr/bin/zram-init

Cấp quyền visudo chạy không cần root passwd để khởi động hkdm daemon và buffyboard

# visudo

mobian ALL=(ALL:ALL) ALL

ALL ALL=(ALL) NOPASSWD: /usr/bin/hkdm, /etc/conf.d/ttyescape.conf,/etc/hkdm/config.d/ttyescape.toml, /usr/bin/buffyboard, /usr/bin/togglevt.sh, /dev/tty0, /dev/uinput

Kích hoạt hkdm.service và zram-init

# sudo systemctl enable hkdm.service

# sudo systemctl start hkdm.service

# sudo systemctl enable zram-swap.service

# sudo systemctl enable zram-tmp.service

# sudo systemctl enable zram-var-tmp.service

Tạo rc.local và kích hoạt rc-local.service

# sudo nano /etc/rc.local

#!/bin/sh -e

sudo togglevt.sh
# sudo chmod a+rx /etc/rc.local

# sudo systemctl enable rc-local.service

# sudo systemctl start rc-local.service

Bỏ shutdown máy khi nhấn power button

# sudo nano /etc/systemd/logind.conf

HandlePowerKey=ignore

# umount /media/rootfs/proc
# umount /media/rootfs/sys
# umount /media/rootfs/dev/pts
# umount /media/rootfs/dev/
# umount /media/rootfs/

Kết nối wifi bằng iwd trên tty1

# sudo iwctl
[iwctl]# device list
[iwctl]# station wlan0 scan
[iwctl]# station wlan0 get-networks
[iwctl]# station wlan0 connect [your_ssid]
Passwd: [your_router_passwd]
[iwctl]# exit
# sudo ping -c 3 google.com

# sudo apt update

# sudo apt upgrade

Duyệt web bằng w3m trên tty1 (chạy hkdm) rất nhanh

Xem dung lượng pin bằng cat

# cat /sys/class/power_supply/bq27541-0/capacity

Điều chỉnh độ sáng từ 0-254

# sudo su

# cat /sys/class/backlight/backlight/max_brightness
254

# cat /sys/class/backlight/backlight/brightness

15

# echo 30 | sudo tee /sys/class/backlight/backlight/brightness

Tự cài các DE như XFCE, Xubuntu, Ubuntu MATE, LXQT, Lubuntu, gnome-shell-common, i3wm, dwm

Sau khi cài DE, stop hkdm.service, rc-local.service, và # sudo togglevt.sh trong /etc/rc.local

