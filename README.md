# **Autism Spectrum Disorder Classification Using Transformer Models**

## **Abstract**
We introduce a Transformer-based model for classifying Autism Spectrum Disorder (ASD) using resting-state fMRI (rs-fMRI) data. By combining brain connectivity metrics with demographic features (age and gender), the model utilizes multi-head self-attention to identify key biomarkers associated with ASD. Key brain regions like the **Callosomarginal Sulcus**, **Lingual Gyrus**, and **Anterior Cingulate Cortex** are highlighted, offering insights into the neurological basis of ASD. Our work demonstrates how deep learning can advance computational neuroscience and precision medicine.

---

## **Introduction**
Autism Spectrum Disorder (ASD) involves disrupted brain connectivity. Resting-state fMRI (rs-fMRI) provides valuable data on these alterations. Traditional machine learning methods often struggle with high-dimensional connectivity matrices. To address this, we propose a Transformer-based architecture, leveraging its ability to capture long-range dependencies and sequence patterns in fMRI data.

---

## **Methods**

### **Dataset Overview**
- **Subjects**: 871 (468 controls, 403 ASD)
- **Demographic Features**: `AGE_AT_SCAN`, `SEX`, `DX_GROUP`
- **fMRI Data**: 64×64 connectivity matrices (2016 features), preprocessed for normalization.

### **Model Architecture**
1. **Demographic Encoding**: 
   - Age encoded using a multi-layer perceptron (MLP)
   - Gender encoded as an embedding vector
2. **Brain Connectivity Encoder**: 
   - Dense layer reduces dimensionality and creates region embeddings
3. **Transformer Module**: 
   - Multi-head attention layers capture region dependencies
   - Positional encodings contextualize sequence data
4. **Output Layer**: 
   - Fully connected layer predicts ASD probability

### **Training**
- **Loss Function**: Binary Cross-Entropy (adjusted for class imbalance)
- **Optimizer**: Ranger with cosine annealing
- **Metrics**: Accuracy, AUC, F1 score

---

## **Results**

### **Model Performance**
- **Accuracy**: 69.7%
- **AUC**: 66.6%
- **F1 Score**: 69.5%


These results highlight the model's effectiveness in classifying ASD from rs-fMRI data.

---

### **Feature Importance**
Top brain regions identified as important for classification:
| **Feature**                              | **Importance** |  
|------------------------------------------|---------------|  
| Callosomarginal Sulcus - Lingual Gyrus   | 0.0265        |  
| Superior Fornix & Isthmus - Postcentral Gyrus Inferior | 0.0248 |  
| Anterior Cingulate Cortex - Lingual Gyrus| 0.0236        |  
| Superior Fornix & Isthmus - Lateral Occipital Cortex | 0.0228 |  
| Cerebellum I-V - Occipital Pole          | 0.0222        |  

### **Visualization of Feature Importance**
A **connectome visualization** highlights key brain regions, such as the **Callosomarginal Sulcus** and **Lingual Gyrus**, which have the strongest contributions to ASD classification. These results align with previous studies linking these regions to ASD-related cognitive processes.

---

## **Discussion**

Our Transformer model effectively identifies brain connectivity patterns associated with ASD. Key regions like the **Callosomarginal Sulcus**, **Lingual Gyrus**, and **Anterior Cingulate Cortex** are implicated in social cognition, sensory processing, and emotion regulation, all of which are often disrupted in ASD. 

- **Callosomarginal Sulcus**: Involved in executive functions, altered in ASD
- **Lingual Gyrus**: Linked to visual processing abnormalities in ASD
- **Anterior Cingulate Cortex**: Plays a role in social cognition and emotion regulation, often atypical in ASD

![newplot](https://github.com/user-attachments/assets/6ded66c6-b05d-4481-ae37-13f0b1de540f)

### **Key Region Contributions to ASD Prediction**
1. **Callosomarginal Sulcus - Lingual Gyrus**: Altered connectivity between frontal and visual regions impacts social attention and sensory integration.
2. **Superior Fornix & Isthmus - Postcentral Gyrus**: Atypical limbic-sensory connectivity may lead to hypersensitivity and emotion recognition issues.
3. **Anterior Cingulate Cortex - Lingual Gyrus**: Disrupted emotional-sensory integration aligns with social communication challenges in ASD.
4. **Superior Fornix & Isthmus - Lateral Occipital Cortex**: Emotional and visual-spatial processing impairments, impacting face and social scene recognition.
5. **Cerebellum I-V - Occipital Pole**: Dysconnectivity here may affect motor coordination and sensory-motor integration.

### **Broader Implications for Resting-State fMRI in ASD**
These regions highlight:
- **Sensory Integration**: Altered connections in visual processing and sensory integration.
- **Social and Emotional Regulation**: Disruptions in emotion regulation and social interaction.
- **Motor Coordination**: Cerebellar involvement indicates motor planning and coordination challenges.

---

## **Conclusion**
This study demonstrates the power of Transformer models in analyzing high-dimensional neuroimaging data. By combining fMRI connectivity and demographic features, we offer insights into ASD-specific neural patterns. Future work will refine the model and expand its application to larger, diverse datasets.

---

## **Supplementary Materials**
- Full feature importance table, source code, and visualizations are available in the project repository.
- Interactive connectome plot available at **`abide_connectome_plot.html`**.

---

