# Setup Windows

*Note: These steps worked for me after some tiral and error and research. Technical environments can change quickly. If you hit a problem, please leave a bug report on Github so we can fix this together.*    

Here is the setup for a Raspberry PI computer. When the PI starts, it is running a movie in a loop unattended and without artifacts (see booklet).  

```
Install PiOS Lite Legacy (Buster) https://www.raspberrypi.com/software/operating-systems/  

connect
ssh-keygen -R raspberrypi.local
ssh pi@raspberrypi.local

setup
sudo apt-get install vlc 
https://wiki.videolan.org/VLC_command-line_help

sudo nano /boot/config.txt
disable_splash=1

sudo nano /boot/cmdline.txt
fbcon=map:2 console=tty3

sudo reboot

Copy the movie 'movie.m4v':
scp -r [source directory]/movie.m4v pi@raspberrypi.local:/home/pi

cvlc movie.m4v --loop  --no-video-title-show --quiet --video-on-top --fullscreen

Autostart the movie

sudo nano /etc/systemd/system/videokiosk.service

——————————————————————————
[Unit]
Description=videokiosk

[Service]
User=pi
Environment="DISPLAY=:0"
ExecStart=cvlc movie.m4v --loop  --no-video-title-show --quiet --video-on-top --fullscreen
WorkingDirectory=/home/pi
Restart=always

[Install]
WantedBy=multi-user.target
——————————————————————————

write and save
sudo systemctl enable videokiosk.service 
sudo systemctl start videokiosk.service 
```
