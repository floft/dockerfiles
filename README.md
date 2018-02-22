Docker
======

Here are a few docker images I use.

## Building

    cd ros
    sudo docker build -t ros .

    cd tf
    sudo docker build -t tf .

## Running

    alias ros='sudo docker run --rm -it -v "/home/garrett/.ros:/root/.ros" -v "/home/garrett/Documents/School/18_Spring/RAS:/ras" -v /tmp/.X11-unix:/tmp/.X11-unix --device=/dev/dri:/dev/dri --env="DISPLAY"  --add-host tegra-ubuntu:$(systemd-resolve -4 tegra-ubuntu | head -n 1 | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b") --add-host wsu-ras:$(systemd-resolve -4 wsu-ras | head -n 1 | grep -Eo "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b") ros'
    alias roslocal='sudo docker run --rm -it -v "/home/garrett/.ros:/root/.ros" -v "/home/garrett/Documents/School/18_Spring/RAS:/ras" -v /tmp/.X11-unix:/tmp/.X11-unix --device=/dev/dri:/dev/dri --env="DISPLAY" ros'

    ros
    roslocal
