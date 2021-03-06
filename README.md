This describes the steps taken in Ubuntu 16.04 to install Colmap. 
So far, unsuccessful. 


# CUDA
See: 
- https://developer.nvidia.com/cuda-toolkit

Note... need a CUDA enabled graphics card. Using XPS 15 - L521X BTX Base

```
sudo dpkg -i cuda-repo-ubuntu1604-9-1-local_9.1.85-1_amd64.deb
#sudo apt-key add /var/cuda-repo-<version>/7fa2af80.pub
sudo apt-key add /var/cuda-repo-9-1-local/7fa2af80.pub
sudo apt-get update
sudo apt-get install cuda
```

# Colmap
See the following for discussion: 
- https://colmap.github.io/install.html
- http://blog.eihis.com/2017/05/16/3d-photogrammetry-on-linux-with-cuda-colmap/
- https://github.com/colmap/colmap/issues/156

```
sudo apt-get install cmake build-essential libboost-all-dev libeigen3-dev libsuitesparse-dev libfreeimage-dev libgoogle-glog-dev libgflags-dev libglew-dev qtbase5-dev libqt5opengl5-dev

sudo apt-get --purge remove libeigen3-dev

#ceress-solver
sudo apt-get install libatlas-base-dev libsuitesparse-dev
git clone https://ceres-solver.googlesource.com/ceres-solver
cd ceres-solver
mkdir build
cd build
#cmake .. -DBUILD_TESTING=OFF -DBUILD_EXAMPLES=OFF
cmake .. -DBUILD_TESTING=OFF -DBUILD_EXAMPLES=OFF -DEIGEN_INCLUDE_DIR=/usr/local/include/eigen3
make
sudo make install


#colmap
cd path/to/colmap
mkdir build
cd build
cmake -DEIGEN3_VERSION=3.2.10 -DEIGEN3_INCLUDE_DIRS=/usr/local/include/eigen3 -DEIGEN_INCLUDE_DIR=/usr/local/include/eigen3/ ..
make
sudo make install
colmap -h
```

# Meshlab

```
sudo apt-get install meshlab
```
