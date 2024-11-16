FROM ubuntu:22.04

RUN apt update && apt install -y libboost-all-dev libusb-1.0-0-dev doxygen python3-docutils python3-mako python3-numpy python3-requests python3-ruamel.yaml python3-setuptools cmake build-essential software-properties-common git wget sudo psmisc vim libjson-c-dev gdb iputils-ping iproute2
WORKDIR /home/
RUN git -C /home clone https://github.com/EttusResearch/uhd.git; git -C /home/uhd checkout v4.7.0.0; cd uhd/host && mkdir -p build && cd build && cmake ../ && make -j $(nproc) && make test && sudo make install && sudo ldconfig && sudo uhd_images_downloader
WORKDIR /home/
RUN git clone https://gitlab.eurecom.fr/oai/openairinterface5g.git ; cd openairinterface5g/ ; git checkout develop
WORKDIR /home/openairinterface5g/cmake_targets
RUN ./build_oai -I ; sudo apt install -y libforms-dev libforms-bin ; ./build_oai -w USRP --ninja --nrUE --gNB --build-lib "nrscope" -C
