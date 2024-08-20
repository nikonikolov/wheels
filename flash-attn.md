# Instructions

## Requirements
- `CUDA`
- `torch`
- `micromamba` / `conda` / python virtual environment


## Compilation

1. Setup environment

- You need to select a specific version of `python`, `torch` and `CUDA`
- To set up environment with `micromamba` (same process for `conda`):

```bash
micromamba env create -n flash-attn python=3.10
micromamba activate flash-attn
pip install https://download.pytorch.org/whl/cu121/torch-2.4.0%2Bcu121-cp310-cp310-linux_x86_64.whl
pip install ninja
pip install packaging
```

- We also assume you have CUDA installed on your system. Make sure it matches the CUDA version used by `torch` and your `PATH` variable is configured to provide access to cuda libraries and `nvcc`

2. Compile the wheel

- **Option 1:**

```bash
git clone https://github.com/Dao-AILab/flash-attention.git
cd flash-attention
python setup.py bdist_wheel
```
This will create a `.whl` file inside the `dist/` folder

- **Option 2:**

```bash
pip install flash-attn --no-build-isolation
```
This will fetch flash-attn and compile it locally. You will get output similar to
```
Created wheel for flash-attn: filename=flash_attn-2.6.3-cp310-cp310-linux_x86_64.whl size=... sha256=...
Stored in directory: ...
```

## Uploading
Just take the `.whl` file and upload as asset to a new release
