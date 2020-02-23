# petalinux-docker

Copy petalinux-v2019.1-final-installer.run file to this folder. Then run

`docker build --build-arg PETA_VERSION=2019.1 --build-arg PETA_RUN_FILE=petalinux-v2019.1-final-installer.run -t petalinux:2019.1 .`

On the host extract the sstate-cache to /opt with:

`tar -zxf sstate-rel-v2019.1.tar.gz --directory /opt/`

After installation, launch petalinux on a linux host with:

`docker run -ti --rm -e DISPLAY=$DISPLAY --net="host" -v /tmp/.X11-unix:/tmp/.X11-unix -v $HOME/.Xauthority:/home/vivado/.Xauthority -v $HOME/Xilinx:/home/vivado/project -v /opt/sstate-rel-v2019.1:/opt/Xsstate petalinux:2019.1 /bin/bash`
