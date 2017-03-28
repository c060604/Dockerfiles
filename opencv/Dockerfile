FROM ubuntu:14.04
MAINTAINER c060604 "c060604@gmail.com"
RUN apt-get -y update
RUN apt-get -y upgrade
RUN apt-get -y install build-essential cmake git pkg-config
RUN apt-get -y install libjpeg8-dev libtiff4-dev libjasper-dev libpng12-dev
RUN apt-get -y install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev
RUN apt-get -y install libgtk2.0-dev
RUN apt-get -y install libatlas-base-dev gfortran
RUN apt-get -y install git
RUN apt-get -y install wget
RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python3 get-pip.py
RUN apt-get -y install python3.4-dev
RUN pip install numpy
RUN mkdir /usr/src/opencv
RUN cd /usr/src/opencv && git clone https://github.com/Itseez/opencv.git
RUN cd /usr/src/opencv/opencv && git checkout 3.0.0
RUN cd /usr/src/opencv && git clone https://github.com/Itseez/opencv_contrib.git
RUN cd /usr/src/opencv/opencv_contrib && git checkout 3.0.0
RUN cd /usr/src/opencv/opencv && mkdir build && cd build && cmake -D CMAKE_BUILD_TYPE=RELEASE \
    -D CMAKE_INSTALL_PREFIX=/usr/local \
    -D INSTALL_C_EXAMPLES=ON \
    -D INSTALL_PYTHON_EXAMPLES=ON \
    -D OPENCV_EXTRA_MODULES_PATH=/usr/src/opencv/opencv_contrib/modules \
    -D BUILD_EXAMPLES=ON ..
RUN cd /usr/src/opencv/opencv/build && make -j4 && make install
CMD ["/bin/bash"]