# nerfstudio install

> [!NOTE]
> Documentation and troubleshooting notes for nerfstudio install.\
> Windows 11 IoT LTSC 2024.\
> Dec 2025.

[Official guide](https://docs.nerf.studio/quickstart/installation.html) | Troubleshooting sources [1](https://github.com/nerfstudio-project/nerfstudio/issues/3607), [2](https://github.com/nerfstudio-project/nerfstudio/issues/3696)

---

### 1. VS2022 version

Make sure to use VS2022 **v17.8**, as newer versions will most likely throw errors when installing `tiny-cuda-nn` due to CUDA 11.x incompatiability.

Download LTSC 17.8 via this [link](https://aka.ms/vs/17/release.ltsc.17.8/vs_enterprise.exe) ([direct link](https://download.visualstudio.microsoft.com/download/pr/bd2300cc-5700-4b59-955d-4e5ef66b964a/3fb9aec96707d61e06a38a39d9ba30c6653394747f73d45dfe5240f77e0b2600/vs_Enterprise.exe))

Then install via
```
vs_Enterprise.exe install --channelUri https://aka.ms/vs/17/release.LTSC.17.8/channel --productId Microsoft.VisualStudio.Product.Community
```

Make sure your VS22 installation also includes `Desktop development with C++` workload, with the optional MSVC v143 and Win11 SDK included, too.


### 2. Follow the official guide to create environment

Make sure to activate the Visual C++ environment, and create the conda environment inside `x64 Native Tools Command Prompt for VS`.

Follow the guide to create and activate the conda env and upgrade your pip.

Install dependencies. I went with Torch 2.1.2 with CUDA 11.8 & the cuda-toolkit.


### 3. Manually set conda environment variables to point to the current CUDA inside nerfstudio's conda env.

```
set CUDAVER=11.8
set CUDA_HOME=%CONDA_PREFIX%
set CUDA_ROOT=%CONDA_PREFIX%
set PATH=%CONDA_PREFIX%\Library\bin;%PATH%
set LD_LIBRARY_PATH=%CONDA_PREFIX%\Library\lib;%LD_LIBRARY_PATH%
set LD_LIBRARY_PATH=%CONDA_PREFIX%\Library\lib64;%LD_LIBRARY_PATH%
set CUDA_HOST_COMPILER=C:\Program Files\Microsoft Visual Studio\2022\Community\VC\Tools\MSVC\14.3x.xxx\bin\Hostx64\x64\cl.exe
```

### 4. Install tcnn

```
pip install git+https://github.com/NVlabs/tiny-cuda-nn/#subdirectory=bindings/torch
```

### 5. Install pywinpty before installing nerfstudio from pip

```
pip install pywinpty==2.0.13
pip install nerfstudio
```
