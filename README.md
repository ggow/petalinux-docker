# petalinux-docker

Copy petalinux-v2019.2-final-installer.run file to this folder. Then run

`docker build --build-arg PETA_VERSION=2019.2 --build-arg PETA_RUN_FILE=petalinux-v2019.2-final-installer.run -t petalinux:2019.2 .`

On the host extract the required architecture specific state-cache to /opt/petalinux/2019.2/ with:

`tar -zxf sstate_aarch64_2019.2.tar.gz --directory /opt/Xstate/`

On the host extract the common state-cache to /opt/petalinux/2019.2/ with:

`tar -zxf downloads_2019.2.tar.gz --directory /opt/Xsstate`

After installation, launch petalinux on a linux host with:

`docker run -ti --rm -e DISPLAY=$DISPLAY --net="host" -v /tmp/.X11-unix:/tmp/.X11-unix -v $HOME/.Xauthority:/home/vivado/.Xauthority -v $HOME/Xilinx:/home/vivado/project -v /opt/Xstate:/opt/Xsstate petalinux:2019.2 /bin/bash`
