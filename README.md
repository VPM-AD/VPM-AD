# 🚗 VPM-AD: Integrating LVLM with Planning Module for End-to-End Autonomous Driving
<p align="center">
  <img src="overview.jpg" alt="Project Overview" style="max-width:100%; height:auto;" />
</p>

## 📋 Project Status

- [x] **Stage 1 (NIPS submission)**
- [ ] **Stage 2 (Code and model release)**

---

## 🚀 Quick Start Guide

Follow these steps to get the project up and running:

### 1. ⚙️ Environment Setup

```bash
conda create -n vpm_ad python=3.10
conda activate vpm_ad
pip install -r requirements.txt
```

---

### 2. 📂 Stage 1: Data Preparation

Run the following commands sequentially to generate training data:

```bash
python vpm_ad/data_generation/VQA_fromGT.py
python vpm_ad/data_generation/VQA_fromLVLM.py
python vpm_ad/utils/merge_json.py
```

---

### 3. 🏁 Stage 1: Training

**Prepare training data:**

```bash
mv path/to/train_vqa_data.json data/
```

**Single-GPU training:**

```bash
llamafactory-cli train examples/train_full/qwen2vl_full_sft.yaml
```

**Multi-GPU distributed training:**

```bash
FORCE_TORCHRUN=1 NNODES=2 NODE_RANK=0 MASTER_ADDR=192.168.0.1 MASTER_PORT=29500 llamafactory-cli train examples/train_lora/qwen2vl_full_sft.yaml
```

---

### 4. 🚦 Stage 2: Data Preparation

Execute these commands to prepare trajectory data:

```bash
python vpm_ad/data_generation/generateTrainTrajectory.py
python vpm_ad/utils/merge_json.py
```

---

### 5. 🎯 Stage 2: Training

Use PyTorch distributed training:

```bash
torchrun --nproc_per_node=8 vpm_ad/Planning_Module/planModel.py \
    --batch_size=8 \
    --output_dir=./checkpoints \
    --train_data=/path/to/train_data.json \
    --val_data=/path/to/val_data.json
```

---

### 6. 📊 Evaluation

Evaluate model performance with:

```bash
python vpm_ad/Planning_Module/planModel.py --eval
```

---

### 7. 📈 Visualization and Qualitative Analysis

Use the following scripts to generate visualizations and qualitative examples:
<p align="center">
  <img src="result_case1.png" alt="Project Case" style="max-width:100%; height:auto;" />
</p>
---

---
## 📄 License

This project is released under the MIT License. See the [LICENSE](LICENSE) file for details.
## 🙏 Acknowledgments

We would like to thank the [LLaMA-Factory](https://github.com/hiyouga/LLaMA-Factory) ,[Qwen2.5-VL](https://github.com/QwenLM/Qwen2.5-VL)projects, which greatly inspired and supported parts of our implementation.

