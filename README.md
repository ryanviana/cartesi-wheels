# cartesi-wheels

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![RISC-V](https://img.shields.io/badge/RISC--V-283272?style=flat&logo=riscv&logoColor=white)

Pre-compiled Python wheel (`.whl`) packages for **RISC-V 64-bit** (`linux_riscv64`), enabling Python ML and utility libraries to run inside [Cartesi's](https://cartesi.io/) RISC-V execution environment.

Many Python packages with C extensions do not publish RISC-V wheels on PyPI. This repository hosts wheels that were cross-compiled for `riscv64` so they can be installed directly with `pip install --no-index --find-links=...` during Cartesi DApp Docker builds.

## Available Packages

Key libraries included (multiple versions available for many):

- **ML/AI**: numpy, Pillow, diffusers, tokenizers, transformers, h5py, keras, TensorFlow-related (flatbuffers, gast, absl-py)
- **Computer Vision**: OpenCV (opencv_python), scikit-image, imageio, easyocr, contourpy, PyWavelets
- **Visualization**: matplotlib, fonttools, kiwisolver, cycler
- **Networking/HTTP**: requests, urllib3, certifi, idna, charset_normalizer, grpcio
- **Utilities**: PyYAML, regex, tqdm, filelock, Jinja2, MarkupSafe, packaging, typing_extensions
- **HuggingFace**: huggingface_hub, tokenizers, diffusers, safetensors
- **Build tools**: ninja, cmake (RISC-V builds)

Wheels target **CPython 3.10** and **3.11** on `linux_riscv64`.

## Usage

In a Cartesi DApp Dockerfile:

```dockerfile
# Download wheels
RUN wget -P /wheels https://github.com/ryanviana/cartesi-wheels/raw/main/numpy-1.26.4-cp310-cp310-linux_riscv64.whl

# Install from local wheels
RUN pip install --no-index --find-links=/wheels numpy
```

## Related Projects

- [sd-with-wheels](https://github.com/ryanviana/sd-with-wheels) -- Python Stable Diffusion DApp that uses these wheels
- [cartesi-stable-diffusion](https://github.com/ryanviana/cartesi-stable-diffusion) -- C++ Stable Diffusion for Cartesi
