# 🐍 Raspberry Pi Boot GIF Splash

Tampilkan **GIF animasi saat booting Raspberry Pi** menggunakan `mpv`. Tutorial ini akan memutar file GIF secara fullscreen setelah sistem masuk ke tampilan grafis (GUI). Repo ini khusus untuk 2 atau 1 screen 1 gif

## Instalasi

**Update dan install package yang dibutuhkan:**

```bash
sudo apt update
sudo apt install mpv -y
sudo apt install wlr-randr wayland-utils -y
echo "$WAYLAND_DISPLAY" 
wlr-randr

```

1. Buat service :
```bash
sudo nano /etc/systemd/system/splash.service
```
2. isi file dengan konfigurasi berikut:
```bash
[Unit]
Description=Play splash GIF on boot
After=lightdm.service

[Service]
User=pi
Environment=DISPLAY=:0
Environment=XAUTHORITY=/home/pi/.Xauthority
ExecStart=/bin/sh -c "sleep 2; mpv --no-terminal --fullscreen --loop=inf /boot/firmware/splash.gif"
Restart=no

[Install]
WantedBy=graphical.target
```
3. Aktifkan dan reboot:
```bash
sudo systemctl enable splash.service
sudo reboot
```
note: tested smoothly in raspi 5, apabila pakai raspi zero 2, tolong sleepnya diubah jadi 10


# happy coding pakde

by:andre angin







