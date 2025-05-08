# KIDS
  
## **Kidney Intelligent Diagnosis System (KIDS)**
  
KIDS is a deep learning based platform for the comprehensive management of chronic kidney disease (CKD) using fundus images. It is designed to:
  
- Detect CKD in community populations.
  
- Perform pathological diagnosis and staging in identified CKD patients.
  
- Predict CKD prognosis based on pathological findings.
  
This system aims to improve clinical management of patients with CKD, particularly those who are ineligible for renal biopsies.
  
## System Requirements

### Operating System and Hardware Requirements

- **Supported Operating Systems:**  
  - Windows 10 or later  
  - macOS 10.15 (Catalina) or later  
  - Linux (Ubuntu 18.04 or later)

- **Minimum Hardware Requirements (sufficient for running Python 3.8):**  
  - **Processor (CPU):** 64-bit Intel Core i3 or AMD Ryzen 3 (Intel i5 / Ryzen 5 or higher recommended)  
  - **Memory (RAM):** At least 4 GB (8 GB or more recommended for smoother performance)  
  - **Storage:** Minimum 10 GB of free disk space for installation and data  
  - **Graphics (optional):** NVIDIA GPU with CUDA support (e.g., GTX 1050 or higher) is recommended for faster model inference and training

  
### Software Dependencies
- **To ensure compatibility, use the following versions for key dependencies:**
  - **Python:** Recommended version 3.8
  - **TensorFlow:** Tested with TensorFlow 2.8.0  
  - **Other Libraries:**  
    - pandas >= 2.0.2
    - numpy >= 1.20.3
    - Pillow >= 9.5.0  
    - joblib >= 1.2.0  
    - scikit-learn>=1.2.2
    - lifelines>= 0.27.8
  
### Package Installation
For a straightforward setup, we provide environment files using pip.
1. Ensure you have [pip](https://pip.pypa.io/en/stable/installation/ ) installed.
2. Install required Python packages by running:
  
   ```bash
   pip install -r requirements.txt
   ```
Typical install time on a "normal" desktop computer: 5-15 minutes.

## Instructions for Use
  
After downloading the source code and demo data, following files were included in the folders:
  
### Data Preparation

- Data was split randomly to train, validation, and test datasets at a ratio: `data prep for CKD screening` and `data prep for CKD diagnosis`
- Data cleaning of an external test dataset for the CKD diagnosis models: `kashi_data cleaning`
  
### Modeling
- CKD screening modeling including data preprocessing and model development: `data` and `SNEfficient`
- CKD progression modeling: `progression_prediction_modeling`
- High percentage of sclerotic glomeruli (>=75%) modeling: `PSG_modeling`
  
### Prediction
You can use the provided `pred` scripts to perform predictions on either the included demo dataset or your own input data. These scripts are designed to:

1. Read  input data (images and/or clinical data)
2. Perform necessary preprocessing (image croping, resizing, normalization, etc.)
3. Load pretrained models corresponding to different prediction tasks
4. Execute predictions
5. Save output results in structured format (CSV)

Each prediction task corresponds to a specific clinical goal and is handled by a dedicated script:

#### 🔍 CKD Screening

- **Script:** `CKD_screening_pred.py`  
- **Function:** This model performs initial screening for chronic kidney disease using fundus images alone. It is designed for use in population-based screening settings or primary care.
- **Input:** Fundus image data  
- **Output:** Binary classification result (CKD vs. non-CKD), with probability scores

#### 🧬 Pathological Diagnosis

The pathological diagnosis model predicts the histological class of CKD based on different input modalities.

- **Fundus Images Only:**  
  - **Script:** `image_pred.py`  
  - **Function:** Predicts pathological classification using retinal images alone  
- **Clinical Data Only:**  
  - **Script:** `meta_pred.py`  
  - **Function:** Uses patient clinical features (demographics, lab tests, renal ultrasonography) for diagnosis  
- **Multimodal Input (Fundus + Clinical Data):**  
  - **Script:** `bimodal_pred.py`  
  - **Function:** Using Combined fundus images and clinical metadata for  pathological diagnosis
- **Output:** Probabilities of IgAN, DN, MN, ANS, and MCD/FSGS.

#### 🧪 Sclerotic Glomeruli Estimation

- **Script:** `PSG_pred.py`  
- **Function:** Predicts the probability of the percentage of sclerotic glomeruli >=75% (high PSG) in CKD patients, an important indicator for disease chronicity and prognosis
- **Input:** Clinical Data
- **Output:** Probability of high PSG

#### 📈 CKD Progression Prediction

- **Script:** `prog_pred.py`  
- **Function:** Forecasts disease progression in CKD patients over time, based on predicted  pathological diagnosis from fundus images and clinical data 
- **Use Case:** Risk stratification, follow-up planning, early intervention  
- **Output:** Probability of CKD progression within 5-year


Each script includes basic configuration options that can be adjusted to suit your input format or analysis goals. If you plan to use your own dataset, make sure it matches the expected format in terms of file structure, and clinical variables. For further customization or integration into your own pipeline, these scripts can also serve as a template.
Expected run time for demo on a "normal" desktop computer: 5-20 seconds.

## Webpage version
  
KIDS models were also deployed on the [zockids website](https://zockids.gzzoc.com/modelstore/#/login), and interested participants can contact the developer to request an account to try it out.
  
- Login via account:
![Index0](https://github.com/user-attachments/assets/1b875178-6876-4259-b9a7-f593943c9bf2)

  
- Choose models:
![Index1](https://github.com/user-attachments/assets/4dbedd37-6e10-461a-aacf-e93158d43ee3)

  
- CKD screening using fundus images only:
![Screening for CKD](https://github.com/user-attachments/assets/8a4c8aea-a13b-4cfe-be69-68a1ba20d968)

  
- Pathological diagnosis and prognosis prediction for CKD patients using fundus images and/or clinical data:
![Pathological diagnosis   prognosis prediction](https://github.com/user-attachments/assets/eae18e21-b80b-492e-836b-50f07ec16d6b)

  
## Application
  
Source code and de-identified participant data of KIDS will be provided upon reasonable request by signing the [KIDS_Access_Form](https://github.com/user-attachments/files/16519892/KIDS_Access_Form.pdf ) and [License_for_KIDS_Code](https://github.com/user-attachments/files/16519893/License_for_KIDS_Code.pdf ). Please provide appropriate protocols, analysis plans, and data exchange plans and require institutional approval prior to transmitting any information contained in the data.  Requests should be directed to the lead corresponding author (linht5@mail.sysu.edu.cn). Submitted license and data access forms will be evaluated by the data manager.
  
  
## Contact
In addition, we would like to hear from you. Please let us know if you have any comments or suggestions, or if you have any questions about the code or the project.

Also, if you would like to contribute to this project, please contact us.

Please feel free to contact us for any questions or comments: Haotian Lin.
📧 E-mail: linht5@mail.sysu.edu.cn
  
  
  
