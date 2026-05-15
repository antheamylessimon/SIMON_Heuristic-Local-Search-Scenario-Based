# Laboratory Work 5: Comparative Analysis of Pre-trained CNN Models for Custom Image Classification

## 🔗 Project Links
- **Google Colab Notebook**: [Open in Colab](https://colab.research.google.com/drive/1ry3YFRG_Ra7izCzlKu4IkCYQkhB2W3co?usp=sharing)

## Project Objectives
1. Use three (3) pre-trained CNN models (VGG16, ResNet50, MobileNetV2).
2. Train models using a custom image dataset (20 Bonsai Categories).
3. Evaluate models using: Accuracy, Loss, Precision, Recall, F1-score, Confusion Matrix, ROC Curve, and AUC Score.
4. Compare performance across custom and pre-trained architectures.
5. Apply Grad-CAM for explainability.
6. Publish results via GitHub and Google Colab.

---

## PART 12: Performance Comparison Table

| Model | Train Accuracy | Train Loss | Test Accuracy | Test Loss | Precision | Recall | F1-score | ROC AUC |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Pre-Trained 1 (VGG16)** | 92.4% | 0.25 | 89.1% | 0.32 | 0.88 | 0.89 | 0.88 | 0.95 |
| **Pre-Trained 2 (ResNet50)** | 95.8% | 0.12 | 92.3% | 0.21 | 0.92 | 0.91 | 0.91 | 0.97 |
| **Pre-Trained 3 (MobileNetV2)**| 94.5% | 0.18 | **93.5%** | **0.19** | **0.93** | **0.93** | **0.93** | **0.98** |
| **Teachable Machine** | 99.0% | 0.05 | 74.0% | 0.85 | 0.72 | 0.71 | 0.71 | 0.96 |
| **Your 1st Model (Basic)** | 97.3% | 0.13 | 48.4% | 2.48 | 0.46 | 0.48 | 0.45 | 0.65 |
| **Your 2nd Model (Enhanced)** | 53.9% | 1.37 | 55.8% | 1.42 | 0.55 | 0.53 | 0.52 | 0.72 |
| **Your 3rd Model (The Good)** | 94.2% | 0.18 | 88.5% | 0.24 | 0.87 | 0.86 | 0.86 | 0.94 |

---

## GUIDE QUESTIONS (FINAL REFLECTION)

### A. Model Performance
1. **Which pre-trained model achieved the highest accuracy? Why?**  
   MobileNetV2. Its architecture is optimized for feature extraction on smaller datasets, preventing the overfitting seen in VGG16.
2. **Which model had the lowest performance? What could be the reason?**  
   The 1st Model (Basic). It lacked regularization (Dropout/BatchNormalization), leading to severe overfitting.
3. **How did loss values compare across models?**  
   Pre-trained models maintained low, stable validation loss (below 0.35), while custom models showed high volatility.

### B. Evaluation Metrics
4. **Why is accuracy not enough to evaluate a model?**  
   Accuracy doesn't reveal if a model is failing on specific classes or if it has high "False Positives."
5. **Which model had the best F1-score? What does it indicate?**  
   MobileNetV2 (0.93). It indicates high precision and high recall across all 20 bonsai classes.
6. **How did Precision and Recall differ across models?**  
   Custom models often had a large gap between Precision and Recall, whereas pre-trained models were balanced.

### C. Confusion Matrix Analysis
7. **Which classes were frequently misclassified?**  
   Species with similar leaf shapes, specifically Trident Maple and Japanese Maple.
8. **What patterns did you observe in the confusion matrix?**  
   Pre-trained models showed a clean diagonal, while custom models showed "clusters" of confusion between biologically similar trees.

### D. ROC and AUC
9. **Which model had the highest AUC score?**  
   MobileNetV2 (0.98).
10. **What does AUC tell us about model performance?**  
    It represents the model's ability to distinguish between classes. A score of 0.98 is near-perfect.

### E. Explainability (Grad-CAM)
11. **What did Grad-CAM reveal about model decision-making?**  
    High-performing models look at unique biological features (leaves/bark), while poor models often focus on the background.
12. **Did the model focus on relevant image regions?**  
    Yes, specifically in the pre-trained models which highlighted the primary foliage clusters.
13. **Which model produced the most meaningful heatmaps?**  
    ResNet50 and MobileNetV2 provided the most localized and relevant heatmaps.

### F. Model Comparison & Improvement
14. **Which model would you recommend for deployment? Why?**  
    MobileNetV2. It offers the best balance of high accuracy (93.5%) and efficient computation.
15. **How can you further improve your best-performing model?**  
    By performing fine-tuning (unfreezing base layers) and increasing the resolution of training images.

### G. Real-World Application
16. **How can your model be applied in real-world scenarios?**  
    In a mobile application for bonsai identification and automated care guidance.
17. **What are the risks of deploying an inaccurate model?**  
    Giving incorrect care instructions, which could lead to the loss of expensive bonsai specimens.
18. **How can this system be integrated into a mobile/web app?**  
    By exporting the model to TensorFlow Lite (.tflite) for mobile or TensorFlow.js for web deployment.
