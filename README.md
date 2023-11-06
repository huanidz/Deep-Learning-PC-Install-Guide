# 1. Fresh packages update
```
sudo apt-get update
sudo apt-get upgrade
```
#### Flexing @@!
```
sudo apt-get install neofetch
```
# 2. Install NVIDIA Drivers and CUDA Toolkit
![Nvidia Logo](https://companieslogo.com/img/orig/NVDA_BIG-8c0fdc59.png?t=1633073585 "NVIDIA")
#### Download and Install Nvidia driver.
```
nvidia-detector <-- Run this to find best suitable driver for current graphics card.

sudo apt-get install nvidia-driver-<VERSION>
```

#### Download and Install CUDA Toolkit 
LASTEST: [LINK](https://developer.nvidia.com/cuda-downloads)
For Ubuntu 18.04 --> Choose 10.2
For Ubuntu 20.04+ --> Choose 11.2 (minimum)

# 3. Install Essential packages (Cmake, Git, GCC)
#### Essential packages
```
sudo apt-get install build-essential cmake git manpages-dev g++ freeglut3-dev build-essential libx11-dev libxmu-dev libxi-dev libglu1-mesa libglu1-mesa-dev unzip pkg-config libjpeg-dev libpng-dev libtiff-dev libavcodec-dev libavformat-dev libswscale-dev libv4l-dev libxvidcore-dev libx264-dev libgtk-3-dev libatlas-base-dev gfortran libomp5
```
#### Image & Videos Codec Processing packages (Borrow from GStreamer required packages)
```
sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-bad1.0-dev gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
```
# 4. Python
```
sudo apt-get install python3.8
sudo apt-get install python-is-python3
```
# 5. OpenCV
#### Presiquisites

```
sudo apt update && sudo apt install -y \
cmake \
g++ \
pkg-config \
python3-dev \
python3-numpy \
libavcodec-dev \
libavformat-dev \
libswscale-dev \
libgstreamer1.0-dev \
libgstreamer-plugins-base1.0-dev \
libgtk-3-dev \
libpng-dev \
libjpeg-dev \
libopenexr-dev \
libtiff-dev \
libwebp-dev \
libtbb2 \
libtbb-dev \
libdc1394-22-dev \
libv4l-dev \
libxvidcore-dev \
libx264-dev \
libatlas-base-dev \
gfortran \
libeigen3-dev
```

#### Build C++ Lib
```
wget -O opencv.zip https://github.com/opencv/opencv/archive/3.4.2.zip  
wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/3.4.2.zip  
unzip opencv.zip  
unzip opencv_contrib.zip  
mv opencv-3.4.2 opencv  
mv opencv_contrib-3.4.2 opencv_contrib

cd opencv
mkdir build && cd build

cmake -D CMAKE_BUILD_TYPE=RELEASE \
-D CMAKE_INSTALL_PREFIX=/usr/local \
-D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib-${version}/modules \
-D OPENCV_GENERATE_PKGCONFIG=ON \
-D BUILD_TESTS=OFF \
-D BUILD_PERF_TESTS=OFF \
-D BUILD_EXAMPLES=OFF \
-D WITH_GSTREAMER=ON \
-D WITH_LIBV4L=ON \
-D WITH_TBB=ON \
-D WITH_IPP=ON \
-D BUILD_opencv_python3=OFF \
-D BUILD_opencv_python2=OFF \
-D BUILD_opencv_java=OFF \
-D INSTALL_C_EXAMPLES=OFF \
-D INSTALL_PYTHON_EXAMPLES=OFF \
-D BUILD_opencv_apps=OFF \
-D OPENCV_ENABLE_NONFREE=ON \ 
-D ENABLE_FAST_MATH=1 ..


sudo make install  
sudo ldconfig
```
#### Install Python Lib
```
python -m pip install opencv-python
```
# 6. C++ Boost Library
Download latest from [LINK](https://www.boost.org/users/download/)
Extract then:
```
./bootstrap
./b2 install
```

