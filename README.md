# Customer Segmentation with K-Means

An unsupervised Machine Learning project that groups mall customers
using demographic and spending-related features. The notebook builds
K-Means clusters, evaluates candidate cluster counts, profiles the
resulting groups, and visualizes the segments for easier interpretation.

## Project Objective

Identify customer groups with similar characteristics using: - Age -
Annual Income (`k$`) - Spending Score (`1–100`)

The goal is to create interpretable customer segments that can help
inform marketing analysis. The clusters are descriptive patterns in this
dataset, not predictions about individual customers.

## Dataset

-   **Dataset:** Mall Customer Segmentation Data
-   **Source:** [Kaggle --- Customer Segmentation
    Tutorial](https://www.kaggle.com/datasets/vjchoudhary7/customer-segmentation-tutorial)
-   **Download method:** The notebook uses `kagglehub` to download the
    dataset and searches for the CSV containing the expected columns.
-   **Rows clustered in the saved notebook output:** 200

`CustomerID` is treated as an identifier and excluded from clustering.
`Gender` is retained for optional post-clustering demographic profiling,
but it is not used to form the clusters.

## Workflow

1.  Load the dataset and inspect its structure.
2.  Check the selected variables and prepare complete rows for
    clustering.
3.  Standardize the clustering features with `StandardScaler`.
4.  Test candidate values of `k` from 2 through 10 using K-Means.
5.  Compare candidates using:
    -   **Inertia / Elbow Method** to examine within-cluster variation.
    -   **Silhouette Score** to assess cluster cohesion and separation.
6.  Fit the final K-Means model using the selected number of clusters.
7.  Profile clusters using the original feature units.
8.  Visualize customer groups and use PCA to project the standardized
    feature space into two dimensions.
9.  Create descriptive, business-facing segment labels from the observed
    cluster profiles.

## Model and Results

-   **Algorithm:** K-Means
-   **Selected number of clusters (`k`):** 6
-   **Best silhouette score:** 0.4274
-   **Customers clustered:** 200
-   **Random state:** 42
-   **Initialization:** `n_init=20`

The notebook assigns descriptive labels based on the median annual
income and spending score of the cluster profiles, including: -
High-Value Customers - High-Income / Lower-Spending - Lower-Income /
High-Spending - Lower-Income / Lower-Spending

These labels summarize the observed profiles; they are not causal
conclusions or predictions. Cluster IDs are arbitrary and may differ
across runs or configurations.

## Visualizations

The notebook includes: - Elbow and Silhouette diagnostics for selecting
`k` - Cluster profiles in the original feature space - A PCA scatter
plot showing the six clusters in two dimensions - A final segment
summary with customer counts, share, age, income, and spending score

PCA is used only for visualization. The K-Means model is fitted on the
three standardized original features, not on the two PCA components.

## Requirements

Main libraries: - Python - pandas - NumPy - Matplotlib - Seaborn -
scikit-learn - kagglehub

Install dependencies with:

``` bash
pip install pandas numpy matplotlib seaborn scikit-learn kagglehub
```

## How to Run

1.  Open `customer-segmentation.ipynb` in Jupyter Notebook, JupyterLab,
    or Google Colab.
2.  Install the required packages.
3.  Run the notebook cells from top to bottom.
4.  The notebook downloads the dataset through `kagglehub`; configure
    Kaggle access as required by your environment.

## Repository Contents

-   `customer-segmentation.ipynb` --- complete analysis and clustering
    workflow.
-   `README.md` --- project overview, methodology, results, and
    instructions.

## Limitations

-   This is a small, illustrative dataset with 200 customers.
-   The best silhouette score is a selection aid, not proof that six
    segments are universally optimal.
-   K-Means is distance-based and works best when the data has cluster
    structures suited to its assumptions.
-   The usefulness and stability of these segments should be validated
    on larger, richer, and more representative customer data before
    using them for real marketing decisions.
