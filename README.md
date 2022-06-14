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
  
Compile Raspberry Pi Kernel with PSI support <br>
Look at https://www.raspberrypi.com/documentation/computers/linux_kernel.html <p>

Edit menuconfig and add <br>
CONFIG_PSI=y <br>
CONFIG_PSI_DEFAULT_DISABLED=y <p>
  
sudo nano /boot/cmdline.txt -> add psi=1 <p>
  
cat /proc/pressure/cpu should output something like: <br>
some avg10=11.55 avg60=6.28 avg300=1.59 total=5111274 <br>
full avg10=0.00 avg60=0.00 avg300=0.00 total=116161 <p>
  
sudo nano /var/lib/waydroid/waydroid_base.prop <p>

ro.hardware.gralloc=default <br>
ro.hardware.egl=mesa <p>
  
sudo systemctl restart waydroid-container <p>
  
waydroid session start <p>
