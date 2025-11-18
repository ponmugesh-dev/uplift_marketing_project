# Causal Digital Marketing Campaign: Uplift Modeling

##  Project Overview
This project applies **uplift modeling** to a Kaggle dataset on digital marketing campaigns.  
The aim is to move beyond predictive modeling into **causal inference**, estimating the **heterogeneous treatment effect (HTE)** of ad exposure on customer conversions.  

The analysis identifies:
- **Persuadables** → customers positively influenced by ads
- **Do-not-disturbs** → customers unaffected or negatively influenced

##  Techniques Used
- **T-Learner** with Gradient Boosting
- **DR Learner (Causal Forest style)** via `econml`
- Evaluation using **Qini coefficient** and **AUUC**

##  Deliverables
- Colab notebook (`uplift_project.ipynb`) with code implementation
- Report (`report.md`) summarizing methodology, metrics, and segment interpretation
- Strategic recommendation based on uplift results

##  How to Run
1. Clone the repo:
     ```bash
   git clone https://github.com/<your-username>/uplift-marketing-project.git


2.Install dependencies:
pip install -r requirements.txt

3.Open uplift_project.ipynb in Jupyter/Colab and run all cells
  Results Snapshot
  Qini coefficient:-0.1907
  AUUC: -0.0726
  Top segments: High-frequency users in Social/Search channels
  Bottom segments: Low-engagement users in Display channel




   ```bash
   git clone https://github.com/<your-username>/uplift-marketing-project.git
