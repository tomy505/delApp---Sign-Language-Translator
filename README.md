# WLASL — Recognition and Translation

Compact instructions to run the I3D-based sign-language recognition and translation project using the WLASL dataset.

**TL;DR:** Requires an NVIDIA GPU with CUDA, PyTorch, and the WLASL dataset placed in a `data/` folder next to the `WLASL/` directory.

**Prerequisites**
- **GPU:** NVIDIA GPU with CUDA support and at least ~4–5 GB VRAM for training/inference.
- **Python:** 3.8+ recommended.
- **Conda (recommended):** for creating an isolated environment.

Installation (recommended)

1. Create and activate a conda environment:

```
conda create -n wlasl python=3.8 -y
conda activate wlasl
```

2. Install PyTorch with a CUDA toolkit that matches your driver. Example used for this project:

```
conda install pytorch torchvision torchaudio cudatoolkit=11.3 -c pytorch
```

3. Install Python requirements for the I3D code:

```
pip install -r WLASL/I3D/requirements.txt
```

Dataset
- Download the WLASL dataset (example on Kaggle: https://www.kaggle.com/datasets/utsavk02/wlasl-complete).
- Place the dataset root in a `data/` directory at the same level as the `WLASL/` folder. The project expects `data/` to contain the dataset files referenced by `WLASL/I3D` scripts.

Quick run
- Change to the I3D folder and run inference/train helpers as needed:

```
cd WLASL/I3D
python run.py
```

Configuration & checkpoints
- Configuration files are in `WLASL/I3D/configfiles/`.
- Pretrained model weights and I3D weights are in `WLASL/I3D/weights/` and `WLASL/I3D/archived/`.

Code layout (important files)
- `WLASL/I3D/run.py` — main script for running the demo/workflow.
- `WLASL/I3D/train_i3d.py` — training entrypoint for the I3D model.
- `WLASL/I3D/test_i3d.py` / `test.py` — evaluation/test utilities.
- `WLASL/I3D/pytorch_i3d.py` — I3D model implementation.
- `WLASL/I3D/preprocess/` — dataset manifests and sample lists.

Model & NLP
- This project uses the I3D model for video-based sign recognition.
- For text-generation / translation, the project integrates KeyToText and an NGram model. See `WLASL/I3D` for integration details.

Notes & tips
- Ensure the installed `cudatoolkit` version is compatible with your GPU drivers and PyTorch. See https://pytorch.org/get-started/locally/ for guidance.
- If you only want to run inference and avoid long installs, confirm necessary weights exist under `WLASL/I3D/weights/` and `WLASL/I3D/archived/`.

Further resources
- Original WLASL repo for training scripts and dataset details: https://github.com/dxli94/WLASL
- KeyToText repository used for NLP: https://github.com/gagan3012/keytotext

License & contact
- This repository is an academic/demo project. Check the original authors' licenses for model/data usage details.
