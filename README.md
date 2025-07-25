# 🐍 Raspberry Pi Boot GIF Splash

Tampilkan **GIF animasi saat booting Raspberry Pi** menggunakan `mpv`. Tutorial ini akan memutar file GIF secara fullscreen setelah sistem masuk ke tampilan grafis (GUI).

## 🔧 Persiapan

1. **Update dan install `mpv`:**

```bash
sudo apt update
sudo apt install mpv -y

```
2. Buat service `splash.service` :
```bash
sudo nano /etc/systemd/system/splash.service
```
  Isi file dengan konfigurasi berikut:
```bash
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
```
3. Aktifkan dan reboot:
```bash
sudo systemctl enable splash.service
sudo reboot
```
# happy coding pakde

by:andre angin







