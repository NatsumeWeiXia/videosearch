
# Ubuntu 16.04

## 1) install FFmpeg

```
sudo add-apt-repository ppa:djcj/hybrid

sudo apt-get update

sudo apt-get install ffmpeg
```

## 2) install Python

```
sudo apt-get install python
```

## 3) install OpenCV

```
sudo apt-get install build-essential
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev libdc1394-22-dev
sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev libv4l-dev liblapacke-dev
sudo apt-get install libxvidcore-dev libx264-dev 
sudo apt-get install libatlas-base-dev gfortran


wget https://github.com/opencv/opencv/archive/3.2.0.zip
wget https://github.com/opencv/opencv_contrib/archive/3.2.0.zip


cd opencv-3.2.0 // YOUR DIR

mkdir build
cd build
cmake -D CMAKE_BUILD_TYPE=RELEASE 
   -D CMAKE_INSTALL_PREFIX= YOUR PREFIX //python -c "import sys; print sys.prefix" 
   -D INSTALL_PYTHON_EXAMPLES=ON 
   -D INSTALL_C_EXAMPLES=OFF 
   -D OPENCV_EXTRA_MODULES_PATH= YOUR opencv_contrib DIR
   -D PYTHON_EXCUTABLE= YOUR PYTHON LOCATION 
   -D WITH_TBB=ON 
   -D WITH_V4L=ON  
   -D WITH_GTK=ON 
   -D WITH_OPENGL=ON 
   -D BUILD_EXAMPLES=ON .. 
$ make -j4
$ sudo make install
$ sudo /bin/bash -c 'echo "/YOUR PREFIX/lib" > /etc/ld.so.conf.d/opencv.conf'
$ sudo ldconfig
```


## ERRORS:

### If you receive error :
```
/usr/bin/ld: extract.o: undefined reference to symbol 'pthread_create@@GLIBC_2.2.5'
/lib/x86_64-linux-gnu/libpthread.so.0: error adding symbols: DSO missing from command line
```
### when doing:

*Step 6: Build SIFT extractor and extract SIFT for each keyframe in database:*
```
cd $mypath/videosearch/indexer/local_descriptors/
make
./run_sift_extraction_test.sh
```
### add **-pthread** to the Makefile at this folder:
```
CXXFLAGS = -std=c++0x -O3 -g -Wall -fmessage-length=0 -pthread 
```
