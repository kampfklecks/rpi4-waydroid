# rpi4-waydroid

sudo apt update <br>
sudo apt upgrade <p>
  
sudo apt install python3 pip ca-certificates curl lxc rpi-wayland <p>
  
sudo raspi-config -> enable Wayland and reboot <p>
  
echo $XDG_SESSION_TYPE needs to be "wayland" <p>

export DISTRO="bullseye" && \ <br>
sudo curl -# --proto '=https' --tlsv1.2 -Sf https://repo.waydro.id/waydroid.gpg --output <br> /usr/share/keyrings/waydroid.gpg && \ <br>
echo "deb [signed-by=/usr/share/keyrings/waydroid.gpg] https://repo.waydro.id/ $DISTRO main" > ~/waydroid.list && \ <br>
sudo mv ~/waydroid.list /etc/apt/sources.list.d/waydroid.list && \ <br>
sudo apt update <p>

pip install pyclip <p>
  
sudo apt install waydroid <p>
  
sudo waydroid init <p>
  
sudo nano /etc/gbinder.d/waydroid.conf <p>
  
[Protocol] <br>
/dev/binder = aidl2 <br>
/dev/vndbinder = aidl2 <br>
/dev/hwbinder = hidl <p>

[ServiceManager] <br>
/dev/binder = aidl2 <br>
/dev/vndbinder = aidl2 <br>
/dev/hwbinder = hidl <p>
  
sudo systemctl start waydroid-container <p>
