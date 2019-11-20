
termux-setup-storage
pkg update
pkg install tsu
pkg install wget



wget -O kodi.apk http://mirrors.kodi.tv/releases/android/arm64-v8a/kodi-18.5-Leia-arm64-v8a.apk
wget -O installer.sh https://raw.githubusercontent.com/lwaldren/test/master/installer
chmod a+X installer.sh 
tsu
