# GANs Verse

> PyTorch + Streamlit implementations of DCGAN, WGAN-GP, Pix2Pix, and CycleGAN — with interactive demos and a unified dashboard.

---

## Live Demos on Hugging Face Spaces

Three of the models are deployed as standalone Gradio apps:

| Model | Task | Live Demo |
|-------|------|-----------|
| DCGAN vs WGAN-GP | Anime face generation — compare two GAN paradigms | [🌸 anime-face-generation-dcgan-vs-wgan-gp](https://huggingface.co/spaces/prospect01/anime-face-generation-dcgan-vs-wgan-gp) |
| Pix2Pix (cGAN) | Sketch → colorized anime image translation | [🖌️ pix2pix-sketch-colorization](https://huggingface.co/spaces/prospect01/pix2pix-sketch-colorization) |
| CycleGAN | Unpaired image-to-image translation (Sketch ↔ Photo) | [🎨 cyclegan-sketch-to-photo-translation](https://huggingface.co/spaces/prospect01/cyclegan-sketch-to-photo-translation) |

---

## Models & Notebooks

| Model | Task | Notebook |
|-------|------|----------|
| DCGAN vs WGAN-GP | Anime face generation — compare stability & diversity | [Q1_DCGAN_WGANGP_FIXED.ipynb](https://github.com/Zubair-Ali-Sandhu/pytorch-gans/blob/main/Q1_DCGAN_WGANGP_FIXED.ipynb) |
| Pix2Pix (cGAN) | Sketch → realistic image translation | [q2-pix2pix.ipynb](https://github.com/Zubair-Ali-Sandhu/pytorch-gans/blob/main/q2-pix2pix-kaggle968e27e0cd%20(2).ipynb) |
| CycleGAN | Unpaired image-to-image translation (Sketch ↔ Photo) | [q3-cyclegan.ipynb](https://github.com/Zubair-Ali-Sandhu/pytorch-gans/blob/main/q3-cyclegan-kaggle310747e72a.ipynb) |

---

## Repository Structure

```
gans-verse/
├── App.py                  # Unified Streamlit dashboard (all 3 questions)
├── app_q1.py               # Standalone DCGAN / WGAN-GP demo
├── app_q2.py               # Standalone Pix2Pix demo
├── app_q3.py               # Standalone CycleGAN demo
├── Q1_DCGAN_WGANGP_FIXED.ipynb
├── q2-pix2pix-kaggle968e27e0cd (2).ipynb
├── q3-cyclegan-kaggle310747e72a.ipynb
├── requirements.txt
└── .streamlit/
    └── config.toml         # Raised upload limits for large checkpoints
```

> **Note:** Model weight files (`.pt` / `.pth`) are excluded from the repository due to size. Load them via the sidebar path inputs or upload directly through the UI.

---

## Getting Started

### 1. Clone

```bash
git clone https://github.com/Zubair-Ali-Sandhu/pytorch-gans.git
cd pytorch-gans
```

### 2. Create a virtual environment

```bash
python -m venv .venv
```

Activate — Linux/macOS:
```bash
source .venv/bin/activate
```
Activate — Windows:
```powershell
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

---

## Running the Apps

### Unified dashboard _(recommended)_

```bash
streamlit run App.py
```

The sidebar lets you switch between:
- **Home** — project overview and model status
- **Q1** — side-by-side DCGAN vs WGAN-GP image grids
- **Q2** — single or batch sketch-to-image translation with download support
- **Q3** — bidirectional CycleGAN translation with cycle reconstruction and SSIM/PSNR metrics

### Standalone demos

```bash
streamlit run app_q1.py   # DCGAN / WGAN-GP
streamlit run app_q2.py   # Pix2Pix
streamlit run app_q3.py   # CycleGAN
```

---

## Default Checkpoint Paths

| Model | Default path |
|-------|-------------|
| DCGAN Generator | `output/dcgan_generator_final.pth` |
| WGAN-GP Generator | `output/wgan_generator_final.pth` |
| Pix2Pix Generator | `output/pix2pix_generator_final.pth` |
| CycleGAN | `cyclegan_weights.pt` |

Paths can be overridden from the sidebar in any app.

---

## Troubleshooting

| Issue | Fix |
|-------|-----|
| Model not loading | Check the path in the sidebar; look for status messages below the input |
| Random / garbage output | Checkpoint missing — app falls back to random weights |
| Upload fails | Confirm `.streamlit/config.toml` is present and restart Streamlit |
| Slow inference | CPU is used by default; GPU inference requires a CUDA-enabled environment |

---

## Author

**Zubair Ali Sandhu** — [GitHub](https://github.com/Zubair-Ali-Sandhu)
