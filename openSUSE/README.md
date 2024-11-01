    1  meson_build
    2  sudo zypper in meson_build
    3  meson _build
    4  cd buffyboard/
    5  meson _build
    6  sudo zypper in gcc
    7  meson _build
    8  sudo zypper in cmake
   12  sudo zypper in libinput-devel
   17  sudo zypper in libxkbcommon-devel
   18  meson _build
   19  meson compile -C _build
   24  sudo zypper in systemd-devel
   25  meson compile -C _build
