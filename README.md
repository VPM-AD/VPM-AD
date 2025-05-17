# VPM-AD: Integrating an LVLM and a Planning Module for End-to-End Autonomous Driving

## 🚧 Project Plan
- [x] **TODO 1**: nips  
- [ ] **TODO 2**: code and models released  
## 🚀 一键运行步骤
1. ⚙️ **环境配置**  
   - 安装 Python 3.8+  
   - `pip install -r requirements.txt`  
2. 📂 **数据准备**  
   - 下载并解压数据集至 `data/` 目录  
   - 配置路径于 `config.yaml`  
3. 🏁 **Stage 1 训练**  
   - `python train_stage1.py --config config.yaml`  
4. 🚀 **Stage 2 训练**  
   - `python train_stage2.py --config config.yaml`  
5. 📊 **指标评测**  
   - `python evaluate.py --config config.yaml` 查看模型性能指标  

## 📄 License
本项目采用 MIT License，详情请见 [LICENSE](LICENSE) 文件。  
