-- BUILD ENVIRONMENT -- 
# Ubuntu LTS - 22.04.3

sudo apt install -yq android-platform-tools-base android-sdk-platform-tools android-sdk-platform-tools-common google-android-ndk-installer bc bison build-essential ccache curl flex g++-multilib gcc-multilib git git-lfs gnupg gperf imagemagick lib32readline-dev lib32z1-dev libelf-dev liblz4-tool libsdl1.2-dev libssl-dev libxml2 libxml2-utils lzop pngcrush rsync schedtool squashfs-tools xsltproc zip zlib1g-dev


mkdir -p ~/.bin

mkdir -p ~/android/lineage

curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo
chmod a+x ~/.bin/repo

## set PATH so it includes user's private bin if it exists
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

- unzip ~/commandlinetools-linux-10406996_latest.zip -d ~/android/ 

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
sudo dnf install -yq @development-tools automake bison bzip2 bzip2-libs ccache curl dpkg-dev gcc gcc-c++ gperf libstdc++.i686 libxml2-devel lz4-libs lzop make maven ncurses-compat-libs openssl-devel pngcrush python python3 python3-mako python-mako python-networkx schedtool squashfs-tools syslinux-devel zip zlib-devel zlib-devel.i686
---



