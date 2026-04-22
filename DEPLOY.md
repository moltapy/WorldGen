## DEPLOYMENT

This respository should be employed in Linux environment.

```shell
git clone --recursive https://github.com/ZiYang-xie/WorldGen.git
cd WorldGen

# Use uv to manage environment
uv venv --python=3.11   # activate

# Have a look at CUDA Version
nvidia-smi

# Install torch and torchvision
uv pip install torch torchvision

# Install worldgen
uv pip install .

# Install DA-2 (360 depth estimation) -- use --no-deps to avoid version conflicts
uv pip install git+https://github.com/EnVision-Research/DA-2.git#subdirectory=src --no-deps

# Install pytorch3d dependencies
uv pip install git+https://github.com/facebookresearch/pytorch3d.git --no-build-isolation

# Huggingface login and access to FLUX.1-dev model
hf auth login   # paste token after the prompt

# Reminds:
# Mind the versions of nunchaku CUDA PyTorch and Python
# I finally use nunchaku 1.3.0 dev / CUDA 12.8 / PyTorch 2.11 / Python 3.11
# https://github.com/nunchaku-ai/nunchaku/releases/download/v1.3.0dev20260202/nunchaku-1.3.0.dev20260202+cu12.8torch2.11-cp311-cp311-linux_x86_64.whl
# curl -L -o nunchaku-1.3.0.dev20260202+cu12.8torch2.11-cp311-cp311-linux_x86_64.whl https://github.com/nunchaku-ai/nunchaku/releases/download/v1.3.0dev20260202/nunchaku-1.3.0.dev20260202+cu12.8torch2.11-cp311-cp311-linux_x86_64.whl
# uv pip install nunchaku-1.3.0.dev20260202+cu12.8torch2.11-cp311-cp311-linux_x86_64.whl
# Also, mind the version of xformers
# Finally, I can use python demo.py "prompt" to test