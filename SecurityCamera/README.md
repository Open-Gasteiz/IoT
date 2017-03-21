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
