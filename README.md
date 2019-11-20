
termux-setup-storage

pkg install wget

export fileid=1XZWoue74_0nhHHrVblT27WAds8zv-j2c
export filename=kodi.zip

## WGET ##
wget --save-cookies cookies.txt 'https://docs.google.com/uc?export=download&id='$fileid -O- \
     | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1/p' > confirm.txt

wget --load-cookies cookies.txt -O $filename \
     'https://docs.google.com/uc?export=download&id='$fileid'&confirm='$(<confirm.txt)

## CURL ##
curl -L -c cookies.txt 'https://docs.google.com/uc?export=download&id='$fileid \
     | sed -rn 's/.*confirm=([0-9A-Za-z_]+).*/\1/p' > confirm.txt

curl -L -b cookies.txt -o $filename \
     'https://docs.google.com/uc?export=download&id='$fileid'&confirm='$(<confirm.txt)

rm -f confirm.txt cookies.txt


wget -O kodi.apk http://mirrors.kodi.tv/releases/android/arm64-v8a/kodi-18.5-Leia-arm64-v8a.apk

pm install kodi.apk

rm -r storage/shared/Android/data/org.xbmc.kodi/files
mv org.xbmc.kodi/files storage/Shared/Android/data/org.xbmc.kodi/files
