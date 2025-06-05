# Visual-GPT# 🚀 Visual ChatGPT Setup Guide (CPU-Friendly, Python 3.8 Compatible)

Visual ChatGPT is a powerful system combining ChatGPT with vision tools like Stable Diffusion, BLIP, SAM, and GroundingDINO.

This guide helps you set up the system **on CPU** with correct versions and missing components filled in.

---

## Set up Python environment (conda)

```bash
conda create -n visgpt python=3.8
conda activate visgpt
```

---

## Install base dependencies

```bash
pip install -r requirements.txt
```


---

##  Fix library versions (for compatibility with Python 3.8)

```bash
pip install "diffusers<0.26" "transformers<4.37" "huggingface_hub<0.17" "accelerate<0.21"
```

---

## Install vision modules

### GroundingDINO

```bash
git clone https://github.com/IDEA-Research/GroundingDINO.git
cd GroundingDINO
pip install -e .
cd ..
```

### Segment Anything (SAM)

```bash
git clone https://github.com/facebookresearch/segment-anything.git
cd segment-anything
pip install -e .
cd ..
```

### Install more models as per requirement

---

## Download Required Checkpoints

```bash
mkdir -p checkpoints

# GroundingDINO checkpoint
curl -L -o checkpoints/groundingdino_swint_ogc.pth \
  https://github.com/IDEA-Research/GroundingDINO/releases/download/v0.1.0-alpha/groundingdino_swint_ogc.pth

# SAM checkpoint
curl -L -o checkpoints/sam_vit_h_4b8939.pth \
  https://dl.fbaipublicfiles.com/segment_anything/sam_vit_h_4b8939.pth
```

### Clone More checkpoints as required

---

## Export your OpenAI API key

### For Linux/macOS:
```bash
export OPENAI_API_KEY="sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
```

### For Windows CMD:
```cmd
set OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## Launch Visual ChatGPT

**CPU-friendly version:**

```bash
python visual_chatgpt.py --load ImageCaptioning_cpu,Text2Image_cpu
```

> 💡 Add more models as needed from the README table, like `Image2Canny_cpu`, `DepthText2Image_cpu`, etc.

---


