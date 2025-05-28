
# Cross-Modal Memory Networks for Radiology Report Generation & Disease Classification  
**FAST-NUCES | BS(AI) Fall 2024 | Computer Vision Course Project**  

*A joint academic project by [Syed Saadullah Hussaini](https://github.com/saadProgram), [Ali Raza](https://github.com/aliraza998), and [Muhammad Sameed](https://github.com/Sameed-75210)*  

## Overview  
This repository implements an enhanced **Cross-Modal Memory Network (CMN)** to automate radiology report generation and disease classification from X-ray images (IU-Xray dataset). Developed as part of FAST University's **Computer Vision course**, the project addresses critical challenges in medical AI:  
- **Cross-modal misalignment** between images and text  
- **Feature degradation** in multi-stage pipelines  
- **Class imbalance** in disease diagnosis  

Our architecture outperforms baselines with:  
- **BLEU-1: 0.4788** (report generation)  
- **80.39% precision** (classification)  


## Model Improvements  
### 1. **Cross-Modal Alignment Engine**  
- **Shared Memory Mechanism**: Stores aligned image-text features for consistent retrieval.  
- **Contrastive Loss**: Minimizes distance between matched image-report pairs (`L_contrastive = 1 − cosine_similarity(v, t)`).  
- **L2 Normalization**: Ensures scale-invariant feature comparisons (`x_norm = x / ||x||`).  

### 2. **Feature Preservation**  
- **Linear Projection Layer**: Maps textual features to visual space (`T’ = T⋅W_t + b_t`).  
- **Attention Pooling**: Focuses on clinically relevant regions via learnable weights (`e_i = w_t^T ⋅ T_i’`).  

### 3. **Disease Classification**  
- **Focal Loss Integration**: Tackles class imbalance by down-weighting easy examples (`L_total = L_CE + L_focal`).  
- **Multi-Modal Fusion**: Combines ResNet/ViT image features with BioClinicalBERT text embeddings.  


## Key Results  
| **Task**               | **Metric**       | **Score**   | Improvement |  
|------------------------|------------------|------------|-------------|  
| Report Generation      | BLEU-1           | 0.4788     | +8.3% vs Base CMN |  
|                        | ROUGE-L          | 0.3667     | +7.1%       |  
| Disease Classification | Precision        | 80.39%     | +2.94% (vs no focal loss) |  

*(See full tables in `results/`)*  


## Academic Context  
Developed under **FAST-NUCES' Computer Vision course** (Fall 2024), advised by [Prof. Name]. This work bridges curriculum concepts (attention mechanisms, multi-modal learning) with real-world medical challenges.  

## Citation  
```bibtex  
@misc{fast2024cmn,  
  title={Enhanced Cross-Modal Memory Networks for Medical AI},  
  author={Raza, Ali and Sameed, Muhammad and Hussaini, Syed Saadullah},  
  year={2024},  
  institution={FAST-NUCES},  
  note={Computer Vision Course Project}  
}  
```  
