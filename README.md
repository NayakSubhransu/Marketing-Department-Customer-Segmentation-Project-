#  **Marketing Department Customer Segmentation Project**

### Business-Driven Clustering & Deep Learning with Autoencoders  

---
<img width="1078" height="500" alt="image" src="https://github.com/user-attachments/assets/5e648be0-f121-4a84-b6ee-fe43c3c2de0b" />

<img width="1069" height="246" alt="image" src="https://github.com/user-attachments/assets/e4811383-4972-4285-aa44-40e23aa6de86" />


##  Project Overview  

This project aims to help a **New York-based bank’s Marketing Department** understand its **credit card customers** better using **data-driven segmentation**.  
The solution combines **Machine Learning (K-Means)** and **Deep Learning (Autoencoders)** to uncover behavioral patterns and enable **targeted marketing campaigns**.

By clustering customers based on their **spending, payment, and cash advance patterns**, this project identifies key customer groups for **personalized marketing**, **credit optimization**, and **customer retention**.

---

##  Business Objective  

The main business goal is to:
- Segment customers into meaningful groups.  
- Identify high-value and low-engagement segments.  
- Drive marketing efficiency and personalization.  
- Improve credit card usage and revenue per customer.

---

##  Key Business Questions  

1. How do customers differ in their purchase and payment behaviors?  
2. Can we identify high-value customers for targeted campaigns?  
3. Which groups show signs of inactivity or under-engagement?  
4. How can segmentation help optimize credit offers and marketing ROI?

---

##  Tech Stack  

| Category | Tools & Libraries |
|-----------|-------------------|
| **Language** | Python 3.10+ |
| **Libraries** | Pandas, NumPy, Seaborn, Matplotlib |
| **Machine Learning** | Scikit-learn (K-Means, PCA) |
| **Deep Learning** | TensorFlow / Keras (Autoencoder) |
| **Evaluation Metrics** | Silhouette Score, Davies–Bouldin Index |
| **Visualization** | PCA 2D Clustering, Elbow & Silhouette plots |

---

## 🧩 Methodology  

### Step 1: Data Preprocessing  
- Removed non-numeric columns (`CUST_ID`).  
- Imputed missing values using **mean strategy**.  
- Standardized data using **StandardScaler** for clustering.  

<img width="883" height="646" alt="image" src="https://github.com/user-attachments/assets/fe4be9c6-52ea-4c12-81a1-cfac1a22642c" />

### Step 2: Clustering with K-Means  
- Applied **MiniBatch K-Means** for efficiency.  
- Determined optimal `k` using:
  - **Elbow Method**  
  - **Silhouette Score**  
- Achieved best results at **k = 2 clusters**.

<img width="913" height="635" alt="image" src="https://github.com/user-attachments/assets/9539c570-6df5-4d2a-8a6d-221d822c3fcf" />

<img width="936" height="636" alt="image" src="https://github.com/user-attachments/assets/6951f394-7dbb-45d9-852c-7d92d956fd8d" />

<img width="944" height="607" alt="image" src="https://github.com/user-attachments/assets/bb82fbf8-7840-4bf4-9e36-7e4bbf5a41c1" />

#### What is the Elbow Method?

The Elbow Method is a visual approach used to determine the ideal ‘K’ (number of clusters) in K-means clustering. It operates by calculating the Within-Cluster Sum of Squares (WCSS), which is the total of the squared distances between data points and their cluster center. However, there is a point at which increasing K no longer leads to a significant decrease in WCSS, and the rate of decline slows. This point is often referred to as the elbow.

### Step 3: Feature Compression via Autoencoder  
- Built a **Neural Network Autoencoder**:
  - Input → Dense(64) → Dense(32) → Dense(8, name='bottleneck') → Dense(32) → Dense(64) → Output  
- Reduced 17 behavioral features into **8 latent features**.  
- Reconstruction loss improved from **0.97 → 0.085**, showing strong learning performance.  

<img width="875" height="529" alt="image" src="https://github.com/user-attachments/assets/b5f2de53-448e-492f-a86c-5ccbbb8d0535" />

<img width="854" height="571" alt="image" src="https://github.com/user-attachments/assets/76928be3-01b0-4eee-8bb8-1d9f9149b4e2" />

<img width="883" height="572" alt="image" src="https://github.com/user-attachments/assets/85e990cd-f707-4d10-83c2-8705844ec429" />

### Step 4: Re-Clustering on Encoded Features  
- Applied **K-Means on Autoencoder embeddings**.  
- Generated clear behavioral clusters with higher separation and interpretability.  

### Step 5: Visualization  
- PCA used for 2D visualization of encoded clusters.  
- Generated plots for Elbow curve, Silhouette scores, and latent feature mapping.

<img width="883" height="536" alt="image" src="https://github.com/user-attachments/assets/45743039-df19-44e1-9fd9-128edabdf44e" />


### Step 6: Business Insight Generation  
- Automated textual interpretation of each customer segment.  
- Mapped clusters to marketing personas (Dormant, Active, Cash Advance users).  

---

##  Model Evaluation  

| Metric | Raw Data Clustering | Autoencoder Clustering |
|--------|---------------------|------------------------|
| **Silhouette Score** | 0.212 | 0.239 |
| **Davies–Bouldin Index** | 1.912 | 1.761 |
| **Autoencoder Loss** | 0.973 → 0.085 | Improved drastically |

**Conclusion:** Autoencoder-based feature learning improved clustering quality and revealed hidden spending behaviors.

---

##  Cluster Insights & Business Interpretation  

### **Cluster 0 – Moderate / Balanced Users (≈85%)**  
| Feature | Value | Insight |
|----------|--------|----------|
| **Purchases** | ₹624 | Low-to-moderate spend levels |
| **Cash Advance** | ₹755 | Occasional small cash usage |
| **Purchases Frequency** | 0.45 | Low engagement |
| **Credit Limit** | ₹3,832 | Low credit exposure |
| **Full Payment %** | 12% | Partial repayments dominate |

** Interpretation:**  
These are low-engagement customers — conservative spenders who use credit occasionally.  

** Marketing Strategy:**  
- Send cashback or reward-based reactivation offers.  
- Introduce zero-interest EMI and convenience features.  
- Encourage digital transactions and small-limit increases.  

---

### **Cluster 1 – Active / High-Value Users (≈15%)**  
| Feature | Value | Insight |
|----------|--------|----------|
| **Purchases** | ₹3,184 | High spenders |
| **Installment Purchases** | ₹1,375 | EMI-heavy users |
| **Cash Advance** | ₹2,263 | Uses short-term credit |
| **Credit Limit** | ₹8,297 | High trust & utilization |
| **Full Payment %** | 34% | Disciplined repayment |

** Interpretation:**  
These are high-value, financially engaged customers — responsible spenders with strong repayment habits.  

** Marketing Strategy:**  
- Upsell premium credit cards or co-branded partnerships.  
- Offer travel, lifestyle, and EMI-linked rewards.  
- Cross-sell personal loans or credit protection plans.  
- Promote auto-pay and loyalty reward programs.  

---

##  Business Impact Summary  

| Category | Insight | Business Action |
|-----------|----------|----------------|
| **Customer Base** | 85% moderate users → low activity | Focus on reactivation campaigns |
| **Revenue Distribution** | 15% active users → high revenue | Retain through premium offerings |
| **Credit Utilization** | Moderate cluster has low credit use | Offer small upgrades to increase spend |
| **Installment Trends** | EMI-heavy among active users | Push Smart EMI and flexible payments |
| **Repayment Discipline** | High full-payment ratio in Cluster 1 | Safe for high-limit offers |
| **Campaign ROI** | Better targeting → less spend waste | Personalize offers via CRM segmentation |

** Expected Business Results:**
- 25–30% increase in engagement among low users.  
- 10–15% increase in average revenue per active customer.  
- Reduced churn through personalized campaigns.  
- Improved marketing ROI via data-driven segmentation.  

---

## Future Work  

| Goal | Description |
|------|--------------|
| **Expand Clusters (k=3 or 4)** | Identify “Cash Advance Users” or “Luxury Spenders.” |
| **Integrate Demographics** | Combine behavior + demographics for hybrid segmentation. |
| **Dashboard Development** | Deploy using Streamlit or Power BI for Marketing Analytics. |
| **Churn Prediction** | Train ML models on autoencoder features. |
| **Automated Reports** | Generate PDF/PowerPoint summaries from insights. |

---

##  Project Structure  

marketing_segmentation/
│
├── marketing_department_solution_final.py # Main code file
├── Marketing_data.csv # Input dataset
├── artifacts/
│ ├── encoder_model.keras # Saved autoencoder model
│ ├── clustered_customers_k2.csv # Clustered dataset
│
├── README.md # Project documentation

---

##  Sample Output : 

Loaded dataset with shape: (8950, 18)
After imputation: 8950 rows, 17 features
Best K by silhouette: 2 (score=0.212)
k=2: silhouette=0.212, DB=1.912

Autoencoder Cluster Means:
Cluster 0: Moderate Users (~85%)
Cluster 1: Active / High-Value Users (~15%)

---

##  Key Takeaways  

- The majority of customers (≈85%) show **low activity**, representing a major opportunity for reactivation.  
- A smaller, high-value group (≈15%) drives **most of the revenue and engagement**.  
- **Deep learning (Autoencoders)** significantly enhances behavioral understanding.  
- Personalized campaigns and credit optimizations can lead to **20–30% revenue uplift**.  

---

##  Author  

**Name:** Subhransu Priyaranjan Nayak  
**Email:** *subhransu.nayak.connect@gmail.com*  
**LinkedIn:** *https://www.linkedin.com/in/subhransu-p-nayak/*  

---

##  Conclusion  

This project demonstrates how **data science and business analytics** together can transform raw customer data into actionable strategies.  
Through unsupervised learning and deep representation models, we discovered **behavioral patterns** that directly support **marketing, credit, and risk decisions**.  

>  *"Data tells you what happened. Insights tell you what to do next."*  

---

