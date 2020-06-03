unrar all archives in current folder $ for f in *.rar;do unrar e -o+ $f;done
show folder size $ du -h --max-depth=1
list folder by size $ ls -lSha /home/jason
copy with progress bar and transferspeed display $ rsync -ah --progress source-file destination-file
convert movie to xbox360 format $ ffmpeg -i "file.mkv" -vcodec libx264 -acodec ac3 -ab 160k "file.mp4"
batch convert above $ for i in *.mkv;   do name=`echo $i | cut -d'.' -f1`;   echo $name;   ffmpeg -i "$i" "${name}.mp4" -vcodec libx264 -acodec ac3 -ab 160k; done
monero daemon $ monerod --data-dir /mnt/cloud/monero
import gpg key for aur packages $ gpg --receive-key keyid
ethereum blockchain sync $ geth --syncmode "fast"
show external ip $ curl ifconfig.me
weather forecast $ curl wttr.in/Wilhelmshaven
set gtk cursor global value for browsers $ gsettings set org.gnome.desktop.interface cursor-theme Adwaita
compress files or folders $ tar -cvzf tarballname.tar.gz itemtocompress itemtocompress
calculator $ bc -l
switch command output language from native language to english $ export LC_ALL=C
backup through ssh $ rsync -avz /source/folder/ user@remoteadress:/remote_folder
unrar all archives in folder (autoverwrite enabled)  $ find . -name "*.rar" -exec unrar x -o+ {} \;
show cpu frequency $ cat /proc/cpuinfo | grep "MHz" & watch -n1 "cat /proc/cpuinfo | grep \"^[c]pu MHz\""
force cpu governor $ sudo cpupower frequency-set -g powersave or performance
list available governors $ cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
show network usage $ iftop
create playlist $ ls -1 *.mp4 > playlist.m3u 
cut characters playlist example $ cut -c 50- playlist.m3u > newplaylist.m3u
batch rename delete example $ for file in *text* ; do mv "$file" "`echo $file | sed 's/\text//'`" ; done
batch rename simple $ rename 0000 000 file*
output orphaned packages to file & run removal  $ sudo pacman -Qqdt > .pkglist.txt & sudo pacman -R - < .pkglist.txt
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
clone partition to image $ partclone.ext4 -c -s /dev/sda1 | gzip -c > image_sda1.pcl.gz
clone image to partition $ zcat image_sda1.pcl.gz | partclone.ext4 -r -o /dev/sda1
ungzip to image $ sudo cat ubuntu_server_2.pcl.gz | sudo gzip -d -c | sudo partclone.restore -C -s - -O partition.img
check image & resize sudo e2fsck -f partition.img & sudo resize2fs partition.img 
mount image to folder & sudo mount -o loop -t ext4 partition.img /tmp/clone/
git $ vim text.md & git add text.md & git commit -m "description" & git push -u origin master
ssh download file & scp user@remote_host:remote_file local_file 
ssh upload file & scp local_file user@remote_host:remote_file
GALLIUM_HUD=simple,fps,temperature LD_PRELOAD=$LD_PRELOAD:/usr/\$LIB/libgamemodeauto.so %command%
show last boot log $ journalctl -b -12
play stream with vlc $ vlc "$(youtube-dl --get-url --format best 'https://www.youtube.com/watch?v=video_id')"
combine video files $ ffmpeg -i "concat:input1.mp4|input2.mp4|input3.mp4" -c copy output.mp4
switch between cpu govenors $ sudo cpupower frequency-set -g powersave / sudo cpupower frequency-set -g ondemand
force vega performance level $ echo manual > /sys/class/drm/card0/device/power_dpm_force_performance_level & echo 7 > /sys/class/drm/card0/device/pp_dpm_sclk
revert vega performance control $ echo auto > /sys/class/drm/card0/device/power_dpm_force_performance_level
copy multiple files from one type within subdirectories $ find -iname '*.mp3' -exec cp {} /home/sk/test2/ \;
enable root x applications in current wayland session $ xhost +SI:localuser:root
firefox,enable tab mouse scroll $ about:config, toolkit.tabbox.switchByScrolling true
firefox, disable theme sync $ about:config, services.sync.prefs.sync.lightweightThemes false
search files $find /home/username/ -name "*.err"
monitor zustand einmalig setzen $ xset dpms force {standby|suspend|off|on}
read current huge pages value $ sudo sysctl -w vm.nr_hugepages=$(nproc) 
enable huge pages $ for i in $(find /sys/devices/system/node/node* -maxdepth 0 -type d);do    echo 3 > "$i/hugepages/hugepages-1048576kB/nr_hugepages";done
insert date /time and vim $ :r! date
query ETH price $ watch -tcn5  "curl -s https://api-pub.bitfinex.com/v2/ticker/tETHEUR | awk -F',' '{print \"ETH/EUR: €\" \$7}'"
set star citizen linux resource limit $ sudo sysctl -w vm.max_map_count=16777216
watch stream with hls & no cache $ streamlink -p mpv -a '--cache=no {filename}' --verbose-player --hls-live-edge 1 --hls-segment-threads 2 'url' 'quality'
generate 2fa code $ oathtool -b --totp 'xxxx xxxx xxxx xxxx'
query available streams with youtube-dl $ youtube-dl -F URL
stream audio only with mpv $  mpv --ytdl-format=251 URL
