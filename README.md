# roomservice


# LineageOS Repository for Device GTA3XLWIFI / SM-T510 / LOS20

This repository contains the device-specific files for building LineageOS for Device XYZ. The following sections provide details on how to use these files and instructions for building the LineageOS ROM.
Remotes

The manifest includes three remotes:

    mrki1111: Fetches from https://github.com/  - my own forks
    lineage: Fetches from https://github.com/LineageOS/ - official 
    K9100ii: Fetches from https://github.com/K9100ii/ - exynos and samsung slsi repo

# Projects
---
## Kernels

The kernels include:

    android_kernel_samsung_gta3xlwifi

## Device

The device includes:

    device_samsung_gta3xlwifi

## Vendor

The vendor projects include:

    vendor_samsung_gta3xlwifi
## SLSI

The SLSI projects include:

    android_hardware_samsung
    android_device_samsung_slsi_sepolicy
    android_hardware_samsung_slsi_libbt
    android_hardware_samsung_slsi_scsc_wifibt_wifi_hal
    android_hardware_samsung_slsi_scsc_wifibt_wpa_supplicant_lib
    android_hardware_samsung_slsi-linaro_config
    android_hardware_samsung_slsi-linaro_exynos
    android_hardware_samsung_slsi-linaro_exynos5
    android_hardware_samsung_slsi-linaro_graphics
    android_hardware_samsung_slsi-linaro_openmax


# BUILD ENVIRONMENT 
-----
## Ubuntu LTS - 22.04.3

sudo apt install -y openjdk-17-jre python-is-python3 python3-full python3 python3-dev bc bison build-essential ccache curl flex g++-multilib gcc-multilib git git-lfs gnupg gperf imagemagick lib32readline-dev lib32z1-dev libelf-dev liblz4-tool libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev

For Ubuntu 23.10 (mantic), install libncurses5 from 23.04 (lunar) as follows:
--- 
wget http://archive.ubuntu.com/ubuntu/pool/universe/n/ncurses/libtinfo5_6.4-2_amd64.deb && sudo dpkg -i libtinfo5_6.4-2_amd64.deb && rm -f libtinfo5_6.4-2_amd64.deb
wget http://archive.ubuntu.com/ubuntu/pool/universe/n/ncurses/libncurses5_6.4-2_amd64.deb && sudo dpkg -i libncurses5_6.4-2_amd64.deb && rm -f libncurses5_6.4-2_amd64.deb
 

mkdir -p ~/.bin

mkdir -p ~/android/lineage

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo


chmod a+x ~/.bin/repo

#### set PATH so it includes user's private bin if it exists
if [ -d "$HOME/.bin" ] ; then

 
    PATH="$HOME/.bin:$PATH"

fi

export PATH=$PATH:/usr/lib/android-ndk


##
source ~/.profile

git config --global user.email ""
git config --global user.name ""

git lfs install


# Initialize local repository
~/android/lineage 

repo init -u https://github.com/LineageOS/android.git -b lineage-20.0 --git-lfs

# Sync
repo sync -c -j$(nproc --all) --force-sync --no-clone-bundle --no-tags



---

# Fedora / Android Build Environment /

wget https://dl.google.com/android/repository/commandlinetools-linux-10406996_latest.zip

- unzip ~/commandlinetools-linux-10406996_latest.zip -d ~/android 

wget https://dl.google.com/android/repository/platform-tools-latest-linux.zip

- unzip ~/platform-tools_r34.0.5-linux -d ~/android/ && mv ~/platform-tools_r34.0.5-linux/platform-tools ~/android 

wget https://dl.google.com/android/repository/android-ndk-r26b-linux.zip

- unzip ~/android-ndk-r26b-linux -d ~/android/ && mv ~/android-ndk-r26b-linux/android-ndk-r26b ~/android 

/$HOME/android/cmdline-tools/bin/sdkmanager --sdk_root=/$HOME/android --licenses

---
- export ANDROID_HOME=$HOME/android
- export ANDROID_NDK_HOME=$HOME/android/android-ndk-r26b
- export PATH=$PATH:$ANDROID_HOME
- export PATH=$PATH:$ANDROID_HOME/platform-tools
- export PATH=$PATH:$ANDROID_NDK_HOME

---
PATH="${HOME}/.bin:${PATH}"

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

chmod a+rx ~/.bin/repo



Below is a list of the key dependencies that we will be installing. Each dependency is listed as a package that needs to be installed via the `dnf` package manager.

| Package Name | Description |
| ------------ | ----------- |
| @development-tools | Development Tools |
| automake | Automake Tool |
| bison | Bison Compiler |
| bzip2 | Bzip2 Compression Library |
| bzip2-libs | Bzip2 Compression Library Libraries |
| ccache | Cache for C Compilers |
| curl | Command Line HTTP Client |
| dpkg-dev | Debian Package Development Tools |
| gcc | GNU Compiler Collection |
| gcc-c++ | GNU C++ Compiler |
| gperf | GNU Perfect Hash Function Generator |
| libstdc++.i686 | C++ Standard Library |
| libxml2-devel | XML Parsing Library |
| lz4-libs | LZ4 Fast Data Compression Library |
| lzop | LZO Compression Utilities |
| make | Make Build Automation Tool |
| maven | Apache Maven Project Management Tool |
| ncurses-compat-libs | Ncurses Compatibility Libraries |
| openssl-devel | OpenSSL Development Tools |
| pngcrush | PNG Image Optimization Tool |
| python | Python Programming Language |
| python3 | Python 3 Programming Language |
| python3-mako | Mako Template Engine for Python 3 |
| python-mako | Mako Template Engine for Python |
| python-networkx | NetworkX Python library |
| schedtool | CPU Scheduler Tuning Tool |
| squashfs-tools | SquashFS Filesystem Tools |
| syslinux-devel | System Linux Bootloader Development Tools |
| zip | Zip Archive Tool |
| zlib-devel | Zlib Development Libraries |
| zlib-devel.i686 | Zlib Development Libraries for 32-bit Systems |
  ff

-----
To develop Android ROMs and kernels on Fedora Linux, you will need to install several packages. Here is a list of the packages you need to install, along with the corresponding installation commands:

    Development Tools and Libraries

  sudo dnf -y groupinstall "Development Tools" "Development Libraries"

    gcc-c++ and its variants

  sudo dnf -y install gcc-c++.* gcc-c++-arm* gcc-c++-x*

    readline and its variants

  sudo dnf -y install readline.* readline-devel.* readline-static.*

    z compression libraries

  sudo dnf -y install zlib.* zlib-devel.* zlibrary.* zlibrary-devel.*
  sudo dnf -y install zlibrary.*
  sudo dnf -y install zlibrary-devel.*
  sudo dnf -y install lzma*
  sudo dnf -y install xz*

    ncurses and its variants

  sudo dnf -y install ncurses.* ncurses-devel.* ncurses-*

    ImageMagick

  sudo dnf -y install ImageMagick.* ImageMagick-*

    SDL and SDL2

  sudo dnf -y install SDL* SDL-* SDL2*

    openssl and openssl-libs

  sudo dnf -y install openssl* openssl-*

    gtk3 and its variant

  sudo dnf -y install gtk3 gtk3-devel*

    libxml2 and its variants

   sudo dnf -y install libxml2 libxml2-devel.* libxml++.* libxml++*

    java-1.8.0-openjdk and its variant

   sudo dnf -y install java-1.8.0-openjdk.*
   sudo dnf -y install java-1.8.0-openjdk-devel.*

    libxslt

   sudo dnf -y install libxslt libxslt-devel

    bc, bison, ccache, curl, flex, git, gnupg, gperf, lzop, pngcrush, rsync, schedtool, squashfs-tools, zip

   sudo dnf -y install bc bison ccache curl flex git gnupg gperf lzop pngcrush rsync schedtool squashfs-tools zip

    glibc-devel.x86_64 and glibc-devel.i686

   sudo dnf install -y glibc-devel.x86_64 glibc-devel.i686

    python3 and python3-devel

   sudo dnf install -y python3 python3-devel

    xorg-x11-proto-devel

   sudo dnf install -y xorg-x11-proto-devel

    libX11-devel.*

   sudo dnf install -y libX11-devel.*

    ccache

   sudo dnf install -y ccache

    Open GL library mesa-libG*

   sudo dnf install -y mesa-libG*

    VirtualBox dependencies

   sudo dnf install -y binutils gcc make patch libgomp glibc-headers glibc-devel kernel-headers kernel-devel dkms qt5-qtx11extras libxkbcommon

    32 bit packages

   sudo dnf install glibc.i686 glibc-devel.i686 libstdc++.i686 zlib-devel.i686 ncurses-devel.i686 libX11-devel.i686 libXrender.i686 libXrandr.i686




