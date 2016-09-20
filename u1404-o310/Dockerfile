FROM congying/ubuntu-dev:14.04

MAINTAINER Congying <congying1112@gmail.com>

RUN apt-get install -y unzip
RUN cd /tmp && wget -O opencv.zip https://github.com/Itseez/opencv/archive/3.1.0.zip && unzip opencv.zip
RUN apt-get remove -y unzip

RUN mkdir /tmp/opencv-3.1.0/3rdparty/ippicv/downloads && mkdir /tmp/opencv-3.1.0/3rdparty/ippicv/downloads/linux-808b791a6eac9ed78d32a7666804320e
RUN cd /tmp/opencv-3.1.0/3rdparty/ippicv/downloads/linux-808b791a6eac9ed78d32a7666804320e && wget https://raw.githubusercontent.com/Itseez/opencv_3rdparty/81a676001ca8075ada498583e4166079e5744668/ippicv/ippicv_linux_20151201.tgz

RUN cd /tmp/opencv-3.1.0 \
&& mkdir build \
&& cd build \
&& cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D INSTALL_C_EXAMPLES=OFF \
-D BUILD_EXAMPLES=OFF .. \
&& make -j4 \
&& make install \
&& ldconfig

RUN rm -rf /tmp/*