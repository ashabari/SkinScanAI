# 🧠 SkinScanAI – AI-Powered Skin Lesion Risk Classifier  

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python](https://img.shields.io/badge/Python-3.10-blue.svg)
![Gradio](https://img.shields.io/badge/Gradio-3.5-orange.svg)
![Docker](https://img.shields.io/badge/Docker-20.10-blue.svg)
[![Hugging Face Space](https://img.shields.io/badge/🤗%20Hugging%20Face-Space-blue)](https://huggingface.co/spaces/ashabarimajumdarPhD/SkinScanAI)




**SkinScanAI** is a full deep‑learning pipeline that classifies skin lesions as **benign** or **malignant**, designed to support triage and early detection in dermatology. Explore the live **Gradio app** hosted on Hugging Face Spaces for instant risk predictions from uploaded lesion images.

---




---

## 🗂️ Project Overview  
- **Notebook**: [MajumdarSkinScanAI.ipynb](https://github.com/ashabari/SkinScanAI/blob/main/MajumdarSkinScanAI.ipynb)  
- **README.md**: That’s this file  
- **Demo**:
- ## 🚀 Try It Live  
[**Launch SkinScanAI App**](https://huggingface.co/spaces/ashabari​majumdarPhD/SkinScanAI)  
⚠️ *Please upload clear, close-up lesion photos—selfies or unrelated images may yield inaccurate high-risk predictions.*
-
-   ![SkinScanAI Demo](SkinScanAI.gif)

---

## 📦 Features
- **Binary** classification: benign vs malignant  
- **3‑class** triage: low / moderate / high risk  
- Custom CNN + pretrained models (MobileNetV2, EfficientNetB0)  
- Stratified train/validation/test splits & class weighting  
- **Data augmentation** for robustness  
- Tabular data fusion using XGBoost & LightGBM  
- Meta‑ensemble combining image + tabular inputs  
- Interactive Gradio app deployed via Docker on Hugging Face

---

## 🔍 Dataset  
Public skin lesion images and metadata sourced from **ISIC**. Images are resized to `224×224` and pre-labeled for binary classification.

> **Note:** Dataset is *not included* due to size/licensing. See the notebook for instructions on integrating your own data.

---

## 🧪 Models Trained  

| Model                                | Val Accuracy | Notes                                     |
|-------------------------------------|:------------:|-------------------------------------------|
| Baseline CNN                        | ~ 74 %       | No augmentation or weighting              |
| CNN + Data Augmentation             | ~ 76 %       | Top-performing binary model               |
| CNN + ELU                           | ~ 63 %       | Underfit                                  |
| CNN + BatchNorm                     | ~ 37 %       | Poor convergence                          |
| CNN + Larger Batch (64)             | ~ 73 %       | Stable generalization                     |
| CNN + Class Weights                 | ~ 76 %       | Better recall for minority class          |
| **CNN + Aug + Class Weights**       | ~ 78 % ✅    | Strong overall generalization             |
| MobileNetV2 (binary)                | ~ 67 %       | Frozen backbone                           |
| MobileNetV2 (triage)                | ~ 76 %       | 3‑class softmax                           |
| EfficientNetB0 (triage)             | ~ 55 %       | Underperforms with frozen base            |
| **CNN + Tabular Ensemble**          | ~ 78 %       | Slight F1 / ROC‑AUC boost                 |

---

## 📊 Visualizations  
- Training & validation **accuracy/loss curves**  
- **Confusion matrices** & classification reports  
- **ROC‑AUC** and precision‑recall curves  
- Meta‑ensemble performance comparisons

---

## 🤖 Deployment  
App is deployed via **Gradio + Docker** on Hugging Face Spaces.  
[**Live App**](https://huggingface.co/spaces/ashabari​majumdarPhD/SkinScanAI)

**Usage Flow:**
1. Upload a close-up lesion image  
2. Optionally provide age, sex, lesion location  
3. Receive instant risk prediction  

---

## 💡 Key Takeaways
- Combining **augmentation + class weighting** greatly improves performance on small, imbalanced datasets  
- Pretrained backbones need **fine-tuning** to match custom CNNs  
- Slightly higher validation vs. training accuracy can indicate better generalization when dropout/augmentation is used  
- Integrating tabular metadata yields marginal but measurable benefits

---

## 📜 License  
Released under the **MIT License**—feel free to use, modify, and distribute with attribution. See [LICENSE](./LICENSE) for full details.

---

## 📁 Repository  
Full code and notebook:  
👉 [https://github.com/ashabari/SkinScanAI](https://github.com/ashabari/SkinScanAI)

---

## 🙌 Acknowledgements  
Thanks to the open-source **ISIC** community and contributors.  
Conversations and joint sessions with [**Tirna Deb**](https://github.com/drtirnadeb) were crucial for this app developement.

⭐️ If you find this project helpful, please **star the repo** and **share the demo**!
⭐️ Reach out to me at **ashabarimajumdar@gmail.com**!


