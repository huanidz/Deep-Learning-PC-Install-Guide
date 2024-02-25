Source from: https://tech.amikelive.com/node-735/how-to-install-nvidia-collective-communications-library-nccl-2-for-tensorflow-on-ubuntu-16-04/#google_vignette

Step 1: Select or create a directory to store the installer file. 

```
cd ~ && mkdir -p ~/installers/nccl
```

Step 2: Download NCCL deb package from NVIDIA website (https://developer.nvidia.com/nccl/nccl-download) and put into the installer directory

Step 3: Extract the tar file
Demonstrate with: For NCCL 2.1.15 and CUDA 9.1, the tar file name is nccl_2.1.15-1+cuda9.1_x86_64.txz

```
tar -xvf nccl_2.1.15-1+cuda9.1_x86_64.txz
```
Step 4: Copy the extracted directory to /usr/local

```
sudo mkdir -p /usr/local/nccl-2.1
sudo cp -vRf nccl_2.1.15-1+cuda9.1_x86_64/* /usr/local/nccl-2.1
```

Step 5: Add NCCL library into LD_LIBRARY_PATH
```
vi ~/.profile

## Add this
LD_LIBRARY_PATH="/usr/local/nccl-2.1:/usr/local/cuda-9.1${LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}"
``` 

Step 6: Create symbolic link for NCCL header file
```
sudo ln -s /usr/local/nccl-2.1/include/nccl.h /usr/include/nccl.h
```

