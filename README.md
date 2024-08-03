# ttyescape-for-arch-and-mobian-and-nixos
fork from https://framagit.org/lolgzs/ttyescape_manjaro_pinephone

PKGBUILD files for ttyescape and dependencies on manjaro phosh
See https://github.com/dreemurrs-embedded/Pine64-Arch/pull/268

How to

install dependencies


sudo pacman -S linux-pinephone-headers terminus-font

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


sudo sytemctl enable hkdm
sudo sytemctl start hkdm
Now you should be able to switch to ttyescape holding volume down button then 3 press on power button.
