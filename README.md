# **Autism Spectrum Disorder Classification Using Transformer Models** 


#### **Abstract**
We present a novel Transformer-based architecture for classifying Autism Spectrum Disorder (ASD) from resting-state functional magnetic resonance imaging (rs-fMRI) data. Integrating demographic features (age and gender) with brain connectivity metrics, the model employs multi-head self-attention to identify key biomarkers associated with ASD. Our findings reveal crucial brain regions contributing to ASD classification, including the **Callosomarginal Sulcus**, **Lingual Gyrus**, and **Anterior Cingulate Cortex**, emphasizing the model’s capacity to extract meaningful neurological insights. This work demonstrates the potential of deep learning in advancing computational neuroscience and precision medicine.

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

The highlighted regions of interest (ROIs) and their connections identified in the analysis can help predict Autism Spectrum Disorder (ASD) because these areas are linked to critical neural processes and behavioral features often altered in individuals with ASD. Below is a detailed explanation of the ROIs and their potential contribution to ASD prediction, supported by their known functional roles and literature on ASD-related neuroanatomical changes.

---

### **1. Callosomarginal Sulcus - Lingual Gyrus**
- **Importance:** 0.0265
- **Function:**
  - The **Callosomarginal Sulcus** is part of the medial frontal cortex, associated with higher-order cognitive functions like decision-making and social cognition.
  - The **Lingual Gyrus** is involved in visual processing and integrating visual stimuli with other sensory modalities.
- **Relevance to ASD:** Altered connectivity between frontal and visual processing regions may contribute to atypical social attention and sensory integration observed in ASD. Studies have reported atypical frontal connectivity in ASD during resting-state fMRI, which can disrupt the interpretation of visual cues in social contexts.

---

### **2. Superior Fornix and Isthmus - Postcentral Gyrus (Inferior)**
- **Importance:** 0.0248
- **Function:**
  - The **Superior Fornix** and **Isthmus** are part of the limbic system, crucial for memory and emotional regulation.
  - The **Postcentral Gyrus** is a primary somatosensory area, important for tactile information processing.
- **Relevance to ASD:** Aberrant limbic-sensory connectivity may explain atypical sensory processing and emotional responses in ASD. Over-connectivity or under-connectivity between these regions might manifest as hypersensitivity to tactile stimuli and difficulties in emotion recognition, common ASD traits.

---

### **3. Anterior Cingulate Cortex - Lingual Gyrus**
- **Importance:** 0.0236
- **Function:**
  - The **Anterior Cingulate Cortex (ACC)** is pivotal in emotion regulation, decision-making, and attention modulation.
  - The **Lingual Gyrus**, as mentioned, handles visual processing and sensory integration.
- **Relevance to ASD:** The ACC is often implicated in ASD for its role in emotional and attentional deficits. Disrupted connectivity with the Lingual Gyrus might indicate difficulties in integrating emotional cues with sensory stimuli, aligning with challenges in social communication.

---

### **4. Superior Fornix and Isthmus - Lateral Occipital Cortex**
- **Importance:** 0.0228
- **Function:**
  - The **Lateral Occipital Cortex** is critical for visual object recognition and spatial attention.
  - The **Superior Fornix and Isthmus** support emotional and mnemonic processes.
- **Relevance to ASD:** This connection highlights the integration of emotional and visual-spatial processing. Impairments here could underlie difficulties in recognizing faces or reading social scenes, hallmarks of ASD.

---

### **5. Cerebellum I-V - Occipital Pole**
- **Importance:** 0.0222
- **Function:**
  - The **Cerebellum I-V** is involved in motor coordination, timing, and potentially social cognition through its connections with cortical areas.
  - The **Occipital Pole** handles primary visual processing.
- **Relevance to ASD:** Atypical cerebellar function is a well-documented feature of ASD. Dysconnectivity with visual areas may reflect difficulties in coordinating sensory input with motor actions, such as challenges in gaze following or fine motor activities in social settings.

---

### **Broader Implications for Resting-State fMRI in ASD**
These ROIs collectively emphasize disrupted connectivity in:
1. **Sensory Integration:** Altered connections involving the Lingual Gyrus and visual processing regions point to challenges in integrating multisensory stimuli, a core issue in ASD.
2. **Social and Emotional Regulation:** Aberrant ACC and limbic connectivity highlight potential markers of social and emotional dysregulation.
3. **Motor and Coordination Deficits:** Cerebellar involvement aligns with motor planning and timing difficulties observed in individuals with ASD.

The Transformer model identifies these patterns by learning the subtle interconnections between ROIs, showcasing their collective impact on ASD-specific neural activity. This provides a foundation for developing objective biomarkers and improving understanding of ASD's neurobiological basis.

---

### **Supporting Literature**
To reinforce these insights, studies such as the following are relevant:
1. **Anterior Cingulate Cortex in ASD:** Connectivity studies emphasize its role in social-emotional deficits in ASD (Just et al., 2012; Yerys et al., 2015).
2. **Cerebellar Alterations:** The cerebellum's role in ASD is linked to disrupted motor and cognitive functions (Stoodley, 2014).
3. **Visual Processing Deficits:** Aberrant occipital connectivity reflects difficulties in processing visual-social stimuli (Kaiser et al., 2010).

These results emphasize how specific ROI connections underpin the heterogeneity of ASD and offer potential pathways for therapeutic targeting.

---

### **Conclusion**
This study demonstrates the potential of Transformer models for analyzing high-dimensional neuroimaging data. The integration of fMRI connectivity features with demographic information enhances classification performance, offering insights into ASD-specific functional connectivity patterns. Future work will focus on refining the model and validating findings across larger, diverse datasets.

---

### **Supplementary Materials**
The full feature importance table, source code, and visualization outputs are available in the project repository. The interactive connectome plot can be accessed at **`abide_connectome_plot.html`**.

The highlighted regions of interest (ROIs) and their connections identified in the analysis can help predict Autism Spectrum Disorder (ASD) because these areas are linked to critical neural processes and behavioral features often altered in individuals with ASD. Below is a detailed explanation of the ROIs and their potential contribution to ASD prediction, supported by their known functional roles and literature on ASD-related neuroanatomical changes.



