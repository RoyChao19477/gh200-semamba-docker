# GH200 SEMamba Docker Image

This Docker image provides a pre-configured development environment for running [SEMamba](https://github.com/RoyChao19477/SEMamba), a mamba-based speech enhancement model, on NVIDIA GH200 hardware. It was created to save time and ensure reproducibility for ARM64/aarch64 CUDA 12.8 setups.

The image includes all required dependencies and configurations for Mamba-based speech enhancement research and other sequence modeling tasks.
  
> ⚠️  **Warning on Package Source**
>
> This Docker image installs `PyTorch`, `Mamba-SSM`, `triton`, `decord`, `vllm`, and `FlashAttention` from the [Jetson SBSA CUDA 12.8 index](https://pypi.jetson-ai-lab.dev/sbsa/cu128), which is a custom external package repository.
>
> While it enables compatibility with ARM64 + CUDA 12.8 setups, users should be aware that:
>
> - It is **not an official PyPI source**
> - Packages may have **undocumented patches or modifications**
> - There may be **potential security or reproducibility risks**
>
> Use with discretion, especially in sensitive or production-level environments.


---

## Contents

- **OS**: Ubuntu 24.04 (ARM64)
- **Python**: 3.12
- **CUDA**: 12.8
- **PyTorch**: 2.7
  *(This package is installed from [Jetson SBSA CUDA 12.8 index](https://pypi.jetson-ai-lab.dev/sbsa/cu128))*
- **Mamba-SSM**: v2.2.4
  *(This package is installed from [Jetson SBSA CUDA 12.8 index](https://pypi.jetson-ai-lab.dev/sbsa/cu128))*
- **FlashAttention**: v2.7.4.post1
  *(This package is installed from [Jetson SBSA CUDA 12.8 index](https://pypi.jetson-ai-lab.dev/sbsa/cu128))*
- **Essential packages**: `ffmpeg`, `vim`, `htop`, `tmux`, `screen`, etc.

---

## Usage

### Option 1: Use GHCR-hosted Image (Recommended)

```bash
docker pull ghcr.io/roychao19477/gh200_semamba_py312_pt27_cuda128:latest

docker run --gpus all -it -v $(pwd):/workspace ghcr.io/roychao19477/gh200_semamba_py312_pt27_cuda128:latest
```

> Replace `$(pwd)` with the directory you want to mount if different.

---

### Option 2: Load from Hugging Face `.tar` (Alternative)

#### Download Docker Image

```bash
wget https://huggingface.co/datasets/rc19477/gh200-semamba-docker/resolve/main/gh200_semamba_py312_pt27_cuda128.tar
```

#### Load Docker Image

```bash
docker load < gh200_semamba_py312_pt27_cuda128.tar
```

#### Run Container

```bash
docker run --gpus all -it -v $(pwd):/workspace gh200_semamba_py312_pt27_cuda128
```

## ⚠️ **WARNING AGAIN**  

This Docker installs some packages from a third-party source: [Jetson SBSA CUDA 12.8 index](https://pypi.jetson-ai-lab.dev/sbsa/cu128).  
These are not official releases, and **I cannot guarantee their security or integrity**.  
Use at your own risk, especially in sensitive or production environments.

---

## Notes

- This image is intended **only for GH200 (ARM64) systems** with CUDA 12.8.
- Python packages are installed via a custom PyPI index for ARM64 provided by Jetson AI Lab.
- **Do not use this image on x86 systems**; it will not work.
- This environment was built to support projects like SEMamba that use selective state space models.

---

## License & Attribution

- This Docker image is shared for **non-commercial research purposes**.
- All third-party packages, including PyTorch, FlashAttention, and Mamba-SSM, retain their **original licenses**.
- PyTorch was installed from a community-provided index: https://pypi.jetson-ai-lab.dev
- Users are responsible for complying with the licenses of any included or downloaded components.

---

## Acknowledgments

Thanks to the developers of:
- Jetson AI Lab for maintaining ARM64-compatible PyTorch wheels.

---

## Maintainer

For any issues, feel free to open a discussion or contact me.
