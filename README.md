# ttyescape-for-arch-and-mobian-and-nixos
fork from https://framagit.org/lolgzs/ttyescape_manjaro_pinephone

PKGBUILD files for ttyescape and dependencies on manjaro phosh
See https://github.com/dreemurrs-embedded/Pine64-Arch/pull/268

or 
https://github.com/gmicroul/Pine64-Arch

How to

install dependencies


sudo pacman -S linux-sdm845-headers terminus-font

Build and install buffyboard


cd src/buffyboard
makepkg
sudo pacman -U buffyboard-0.2.0-1-aarch64.pkg.tar.zst

Build and install hkdm


cd src/hkdm
makepkg
sudo pacman -U hkdm-0.1.8-1-aarch64.pkg.tar.zst

Build and install ttyescape


cd src/ttyescape
makepkg
sudo pacman -U ttyescape-1.0.1-1-any.pkg.tar.zst

Enable and start hkdm


sudo systemctl enable hkdm

sudo systemctl start hkdm

Now you should be able to switch to ttyescape holding volume down button then 3 press on power button.

Arch:Done
![image](https://github.com/user-attachments/assets/44db417e-9972-4126-a431-e2711f656a06)


mobian:Done
![image](https://github.com/user-attachments/assets/03f6dd6b-61d1-43ec-8fcb-27ddaee303e6)


NixOS:in progress
![image](https://github.com/user-attachments/assets/4b80ffae-01bd-43e8-bcf1-8e38e8a1fad5)
