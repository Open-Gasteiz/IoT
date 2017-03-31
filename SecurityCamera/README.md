## Flashear la SD

*  [Descargar](https://www.raspberrypi.org/downloads/raspbian/) el OS

* [Instalar](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md) el OS

## Habilitar la cámara

```
sudo raspi-config  
```

![image](https://cloud.githubusercontent.com/assets/11192915/24167439/0c8dbb14-0e77-11e7-9e69-7bf814e1769e.png)

![image](https://cloud.githubusercontent.com/assets/11192915/24167445/117b3cf0-0e77-11e7-8711-5ad203c3ac85.png)

## Depencencias

```
sudo apt-get update
sudo apt-get install -y motion
```

## Configuración de motion

```
# The mini-http server listens to this port for requests (default: 0 = disabled)
stream_port 9000

webcam_localhost off

control_localhost off

# Quality of the jpeg (in percent) images produced (default: 50)
stream_quality 50

# Output frames at 1 fps when no motion is detected and increase to the
# rate given by stream_maxrate when motion is detected (default: off)
stream_motion off
```

### Activar el demonio

sudo vim /etc/default/motion

```

# set to 'yes' to enable the motion daemon
start_motion_daemon=yes
```

### Cámara integrada

Cargar el módulo del kernel y hacerlo persistente:

```
sudo bash -c 'echo "bcm2835-v4l2" >> /etc/modules'
```

# MotionEye

## Flashear la SD

*  [Descargar](https://www.raspberrypi.org/downloads/raspbian/) el OS

* [Instalar](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md) el OS

## Habilitar la cámara

```
sudo raspi-config  
```

![image](https://cloud.githubusercontent.com/assets/11192915/24167439/0c8dbb14-0e77-11e7-9e69-7bf814e1769e.png)

![image](https://cloud.githubusercontent.com/assets/11192915/24167445/117b3cf0-0e77-11e7-8711-5ad203c3ac85.png)

### Cámara integrada

Cargar el módulo del kernel y hacerlo persistente:

```
sudo bash -c 'echo "bcm2835-v4l2" >> /etc/modules'
```

## Depencencias

```
wget https://github.com/ccrisan/motioneye/wiki/precompiled/ffmpeg_3.1.1-1_armhf.deb
sudo dpkg -i ffmpeg_3.1.1-1_armhf.deb
sudo apt-get remove libavcodec-extra-56 libavformat56 libavresample2 libavutil54
sudo apt-get install -y python-pip python-dev curl libssl-dev libcurl4-openssl-dev \
                        libjpeg-dev libx264-142 libavcodec56 libavformat56 libmysqlclient18 \
                        libswscale3 libpq5
sudo wget https://github.com/Motion-Project/motion/releases/download/release-4.0.1/pi_jessie_motion_4.0.1-1_armhf.deb
sudo dpkg -i pi_jessie_motion_4.0.1-1_armhf.deb
sudo pip install motioneye
```

## Configuración

```
sudo mkdir -p /etc/motioneye
sudo cp /usr/local/share/motioneye/extra/motioneye.conf.sample /etc/motioneye/motioneye.conf
```

### Carpeta media

```
sudo mkdir -p /var/lib/motioneye
```

### Demonio

```
sudo cp /usr/local/share/motioneye/extra/motioneye.systemd-unit-local /etc/systemd/system/motioneye.service
sudo systemctl daemon-reload
sudo systemctl enable motioneye
sudo systemctl start motioneye
```

## Acceso al front-end

```
http://<ip/nombre>:8765
```

### Contraseña

![image](https://cloud.githubusercontent.com/assets/11192915/24216707/82551ede-0f3d-11e7-80bc-bcd0e81a3998.png)

```
user=admin
pass=" "

