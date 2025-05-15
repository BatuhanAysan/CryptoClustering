# 📊 CryptoClustering: PCA & KMeans Clustering on Cryptocurrency Data

This project applies **unsupervised machine learning** techniques—specifically **KMeans clustering** and **Principal Component Analysis (PCA)**—to explore whether cryptocurrencies can be grouped based on their price change behaviors across multiple timeframes.

---

## 🎯 Objective

The goal is to evaluate the effectiveness of clustering cryptocurrencies using:
- All available percentage change features (after scaling)
- A reduced feature set via PCA (dimensionality reduction)

This analysis aims to determine if using fewer features affects the clustering results, and whether PCA can retain the essential structure of the original dataset.

---

## 🧰 Technologies Used

- Python
- pandas, numpy
- scikit-learn (StandardScaler, KMeans, PCA)
- hvPlot (interactive visualizations)

---

## 📁 Dataset Description

The dataset used in this project is `crypto_market_data.csv`, which includes:

- `coin_id`: Identifier for each cryptocurrency  
- Price change percentages across multiple timeframes:
  - `price_change_percentage_24h`
  - `price_change_percentage_7d`
  - `price_change_percentage_14d`
  - `price_change_percentage_30d`
  - `price_change_percentage_60d`
  - `price_change_percentage_200d`
  - `price_change_percentage_1y`

> While the scatter plots focus on visualizing clusters using the `24h` and `7d` price change percentages, the clustering and PCA transformations were applied to **all seven** numeric features to capture comprehensive temporal behavior.

---

## 🧹 Step 1: Data Preparation

- Loaded the dataset into a pandas DataFrame.
- Cleaned the data and confirmed valid numerical ranges.
- Scaled the numerical features using `StandardScaler`.
- Created a new scaled DataFrame indexed by `coin_id`.

---

## 🧮 Step 2: Clustering with Scaled Data

- Used the **elbow method** to determine the optimal number of clusters (`k`) by iterating over `k = 1 to 11`.
- Based on the elbow curve, the optimal value of `k` was found to be **4**.
- Applied **KMeans clustering** using `k=4` on the scaled data.
- Cluster labels were added to a copy of the scaled DataFrame.
- Created an interactive scatter plot using:
  - `x = price_change_percentage_24h`
  - `y = price_change_percentage_7d`
  - Color-coded points by cluster
  - `coin_id` added as hover label

---

## 🔁 Step 3: Dimensionality Reduction with PCA

- Applied PCA to reduce the 7-dimensional feature space to 3 principal components.
- Retrieved explained variance ratios:
  - PC1: ~37.2%
  - PC2: ~34.7%
  - PC3: ~17.6%
- **Total explained variance**: **≈89.5%**
- Created a new PCA-transformed DataFrame with `coin_id` as index.

---

## 🔂 Step 4: Clustering with PCA Data

- Re-applied the **elbow method** on the PCA data.
- Optimal number of clusters was again found to be **k = 4**.
- Performed KMeans clustering using PCA-transformed data.
- Added cluster labels to the PCA DataFrame.
- Created an interactive scatter plot using:
  - `x = PC1`
  - `y = PC2`
  - Color-coded by cluster
  - `coin_id` added as hover label

---

## 🪞 Step 5: Composite Visualizations & Comparison

- Created a **composite elbow plot** to compare inertia between:
  - Original scaled data
  - PCA-transformed data
- Created a **composite cluster plot** to compare the clustering results visually.
  - Both plots use `PC1` and `PC2` for visual alignment

---

## ✅ Summary of Key Results

- **Best k value**: `k = 4` for both original and PCA data
- **Total explained variance** with 3 principal components: ~89.5%
- **Clustering outputs were identical** — same labels assigned
- PCA successfully reduced dimensionality without distorting cluster structure

---

## 💡 Conclusion: Impact of Using Fewer Features

> Based on visual and analytical evaluation, reducing the number of features using PCA had **no negative impact** on clustering quality.  
> The identical clustering results suggest that PCA preserved the underlying structure of the dataset while reducing dimensionality and improving computational efficiency.

---

## 📦 Project Structure

```
CryptoClustering/
│
├── Crypto_Clustering.ipynb # Main notebook with full analysis
├── Resources/
│ └── crypto_market_data.csv # Input dataset with cryptocurrency price change data
├── README.md # Project documentation
```

---

## 🚀 Deployment & Submission

- All code and outputs are included in this repository.
- Files were added and committed using Git CLI with clear commit messages.
- The repository was pushed to GitHub as required.

---

## ✍️ Author Notes

This challenge demonstrates a practical use case of unsupervised learning in the financial sector.  
It showcases how PCA and KMeans can be used together to uncover patterns in complex datasets, even when feature reduction is applied.
