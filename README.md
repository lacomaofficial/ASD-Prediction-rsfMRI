# **Autism Spectrum Disorder Classification Using Transformer Models:** 

(A Novel Approach to Resting-State fMRI Analysis)

#### **Abstract**
We present a novel Transformer-based architecture for classifying Autism Spectrum Disorder (ASD) from resting-state functional magnetic resonance imaging (rs-fMRI) data. Integrating demographic features (age and gender) with brain connectivity metrics, the model leverages multi-head self-attention to identify key biomarkers associated with ASD. Our findings reveal crucial brain regions contributing to ASD classification, including the **Callosomarginal Sulcus**, **Lingual Gyrus**, and **Anterior Cingulate Cortex**, emphasizing the model’s capacity to extract meaningful neurological insights. This work demonstrates the potential of deep learning in advancing computational neuroscience and precision medicine.

---

### **Introduction**
Autism Spectrum Disorder (ASD) is a complex neurodevelopmental condition characterized by altered functional connectivity within and between brain regions. Resting-state fMRI (rs-fMRI) captures intrinsic brain activity and provides a rich dataset for studying these alterations. Previous efforts to classify ASD have relied on traditional machine learning models, often constrained by their inability to process the high-dimensional connectivity matrices effectively. We propose a Transformer-based architecture to address these challenges, leveraging its capacity for sequence modeling and capturing long-range dependencies.

---

### **Methods**

#### **Dataset Description**
**Phenotypic Data:**  
- **Subjects:** 871  
- **Target Distribution:** 468 controls, 403 ASD  
- **Features:** `AGE_AT_SCAN`, `SEX`, and `DX_GROUP`  

**fMRI Connectivity Data:**  
- **Input Format:** Upper triangular elements of 64×64 connectivity matrices (2016 features).  
- **Preprocessing:** Normalization of demographic features and conversion of matrices to symmetric form.  

#### **Model Architecture**
**TransformerModel Highlights:**  
1. **Demographic Encoding:**  
   - A multi-layer perceptron (MLP) encodes age.  
   - Gender is represented as an embedding vector.  

2. **Brain Connectivity Encoder:**  
   - A dense layer reduces dimensionality to create embeddings for each brain region.  

3. **Transformer Module:**  
   - Multi-head attention layers capture interdependencies between regions and demographics.  
   - Positional encodings contextualize sequence data.  

4. **Output Layer:**  
   - A fully connected layer predicts the probability of ASD.  

#### **Optimization and Training**
- **Loss Function:** Binary Cross-Entropy with class imbalance adjustments.  
- **Optimizer:** Ranger with cosine annealing learning rate scheduler.  
- **Validation Metrics:** Accuracy, AUC, F1 score.  

---

### **Results**

#### **Model Performance**
- **Validation Accuracy:** 67.4%  
- **AUC:** 66.6%  
- **F1 Score:** 69.5%  

These results underscore the model’s robustness in identifying ASD from high-dimensional rs-fMRI data.

---

#### **Feature Importance**
Feature attribution analysis identified the following brain regions as most significant for classification:  

| **Feature Name**                              | **Importance** | **Marker 1**                  | **Marker 2**                   |  
|-----------------------------------------------|---------------|-------------------------------|--------------------------------|  
| Callosomarginal Sulcus - Lingual Gyrus        | 0.0265        | Callosomarginal Sulcus        | Lingual Gyrus                  |  
| Superior Fornix and Isthmus - Postcentral Gyrus Inferior | 0.0248 | Superior Fornix and Isthmus | Postcentral Gyrus Inferior     |  
| Anterior Cingulate Cortex - Lingual Gyrus     | 0.0236        | Anterior Cingulate Cortex     | Lingual Gyrus                  |  
| Superior Fornix and Isthmus - Lateral Occipital Cortex | 0.0228 | Superior Fornix and Isthmus | Lateral Occipital Cortex       |  
| Cerebellum I-V - Occipital Pole               | 0.0222        | Cerebellum I-V                | Occipital Pole                 |  

---

#### **Visualization of Feature Importance**
A **connectome visualization** was generated to highlight the critical interactions between brain regions. The **Callosomarginal Sulcus** and **Lingual Gyrus**, shown as central nodes, exhibited the strongest contributions to classification. This aligns with previous studies suggesting these regions' involvement in ASD-related cognitive processes.

---

### **Discussion**
The Transformer model effectively identifies patterns in rs-fMRI data that align with known ASD biomarkers. The top features emphasize regions implicated in social cognition, sensory processing, and motor functions—domains often disrupted in ASD.  
- **Callosomarginal Sulcus:** Linked to altered connectivity in ASD, affecting executive functions.  
- **Lingual Gyrus:** Associated with visual processing abnormalities in ASD.  
- **Anterior Cingulate Cortex:** Plays a role in emotion regulation and social cognition, frequently atypical in ASD populations.
  
![newplot](https://github.com/user-attachments/assets/6ded66c6-b05d-4481-ae37-13f0b1de540f)

---

### **Conclusion**
This study demonstrates the potential of Transformer models for analyzing high-dimensional neuroimaging data. The integration of fMRI connectivity features with demographic information enhances classification performance, offering insights into ASD-specific functional connectivity patterns. Future work will focus on refining the model and validating findings across larger, diverse datasets.

---

### **Supplementary Materials**
The full feature importance table, source code, and visualization outputs are available in the project repository. The interactive connectome plot can be accessed at **`abide_connectome_plot.html`**.

