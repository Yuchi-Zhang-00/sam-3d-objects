# 50系卡安装SAM-3D   (torch2.7.0+cu128)

# 改动之处：

pyproject.toml：
```
-PIP_EXTRA_INDEX_URL = "https://pypi.ngc.nvidia.com https://download.pytorch.org/whl/cu121"  

改为 

+PIP_EXTRA_INDEX_URL = "https://pypi.ngc.nvidia.com https://download.pytorch.org/whl/cu128"
```
requirements.inference.txt：
```
kaolin==0.17.0 改为 kaolin==0.18.0
```
requirements.txt：
```
nvidia-pyindex==1.0.9 改为 # nvidia-pyindex==1.0.9    （即注释掉）

torchaudio==2.5.1+cu121 改为 torchaudio, 
xformers==0.0.28.post3 改为 xformers （即取消指定torchaudio和xformers的版本）
```

# 运行以下安装命令 

```
uv venv --python 3.11

source .venv/bin/activate

# uv pip install torch==2.7.0 torchvision==0.22.0 torchaudio==2.7.0 --index-url https://download.pytorch.org/whl/cu128

uv pip install torch==2.7.1 torchvision==0.22.1 torchaudio==2.7.1 --index-url https://download.pytorch.org/whl/cu128

export PIP_FIND_LINKS="https://nvidia-kaolin.s3.us-east-2.amazonaws.com/torch-2.7.1_cu128.html"

uv pip install hatch-requirements-txt editables wheel

uv pip install -e '.[dev]'  -i https://mirrors.ivolces.com/pypi/simple

uv pip install -e '.[p3d]' --no-build-isolation  -i https://mirrors.ivolces.com/pypi/simple

uv pip install -e ".[inference]"     --no-build-isolation     --find-links https://nvidia-kaolin.s3.us-east-2.amazonaws.com/torch-2.7.1_cu128.html  -i https://mirrors.ivolces.com/pypi/simple

```
