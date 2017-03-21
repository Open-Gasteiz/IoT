## Flashear la SD

*  [Descargar](https://www.raspberrypi.org/downloads/raspbian/) el OS

* [Instalar](https://www.raspberrypi.org/documentation/installation/installing-images/linux.md) el OS

## Habilitar la cámara

```
sudo raspi-config
Enable camera   
```


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
