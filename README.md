# RASPI BOOT GIF

sudo apt update

sudo apt install mpv -y

sudo nano /etc/systemd/system/splash.service

[Unit]
Description=Play splash GIF on boot
After=lightdm.service

[Service]
User=pi
Environment=DISPLAY=:0
Environment=XAUTHORITY=/home/pi/.Xauthority
ExecStart=/bin/sh -c "sleep 13; mpv --no-terminal --fullscreen --loop=inf /boot/firmware/paok.gif"
Restart=no

[Install]
WantedBy=graphical.target

sudo systemctl enable splash.service

sudo reboot
