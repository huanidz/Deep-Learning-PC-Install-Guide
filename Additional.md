# 1. Geo/Matrix calculation packages
```
GEOS: https://libgeos.org/usage/download/

# Unpack and setup build directory
tar xvfj geos-3.11.2.tar.bz2
cd geos-3.11.2
mkdir _build
cd _build
# Set up the build
cmake \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr/local \
    ..
# Run the build, test, install
make
ctest
make install


EIGEN: sudo apt install libeigen3-dev
```

# 2. LibTorch (For Pre/Postprocessing - Inference cut off) (This is required for ARM, x86 can rebuild for faster binary)
```
1. Clone the repo:
git clone -b master --recurse-submodule  https://github.com/pytorch/pytorch.git 

Checkout to 1.13.1 version.

2. inside the pytorch model: 
mkdir pytorch-build && cd pytorch-build

3. Verify these things:
- Use atleast gcc 10
- revert /third-party/flatbuffers to v2.0.5 (use git checkout)
- revert /third-party/fmt to 7.1.0 (use git checkout)

3. Cmake as follow:
cmake -DBUILD_SHARED_LIBS:BOOL=ON -DCMAKE_BUILD_TYPE:STRING=Release -DUSE_CUDA:BOOL=OFF -DUSE_QNNPACK:BOOL=OFF -DUSE_PYTORCH_QNNPACK:BOOL=OFF -DUSE_XNNPACK:BOOL=OFF -DONNX_ML:BOOL=OFF -DUSE_VALGRIND:BOOL=OFF -DUSE_KINETO:BOOL=OFF -DPYTHON_EXECUTABLE:PATH=`which python3` -DCMAKE_INSTALL_PREFIX:PATH=../pytorch-install ../

4. Build the lib:
cmake --build . --target install -j 8

5. If everything ok, go to /pytorch-install folder that has been included the cmake command. Use that folder as the shared library like a normal libtorch
```
