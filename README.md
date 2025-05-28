**Unsupervised learning**

Unsupervised learning finds patterns in data.

Ex: "clusters" of customers based on their purchase histories, or searching for patterns and correlations among these purchases, 
and using these patterns to express the data in a compressed form. 
These are examples of unsupervised learning techniques called "clustering" and "dimension reduction".

**Clustering:**

**K Means Clustering:**

K-Means is an unsupervised machine learning algorithm used for clustering data into K distinct groups (clusters) based on feature similarity. 
It minimizes the distance between points within a cluster and maximizes the distance between clusters.

K-Means works like this:

1. Choose K (number of clusters, e.g., 3)
2. Randomly initialize K centroids
3. Assign each customer to the nearest centroid (based on distance, like Euclidean)
4. Recalculate the centroid of each cluster
5. Repeat until centroids stabilize (convergence)

Example: 

A retail company wants to understand its customers better to tailor marketing strategies, but it doesn't have any labels like "high spender" or "loyal customer."

Solution:

K-Means — to group customers based on purchase behavior.

Step 1:

K-Means starts by randomly placing K points in feature space (e.g., Age, Income, Spending Score).
These points are called centroids — the center of a cluster.

Step 2:

Each customer is assigned to the nearest centroid based on Euclidean distance.
So customers with similar age, income, and spending values will fall into the same group.

Step 3:
Now that customers are grouped:
The algorithm calculates the mean of each group.

Step 4:
It moves the centroids to these new means.

It repeats steps 3 and 4:

Step 5:
Re-assign customers to the nearest new centroid
Update centroids again

This continues until the cluster assignments no longer change much — meaning the clusters are stable.

Result:
Each cluster now contains customers with similar behaviors, such as:
Cluster 0: Young, low-income, high spenders → "Student Spenders"
Cluster 1: Middle-aged, high-income, moderate spending → "Affluent Professionals"
Cluster 2: Older, moderate income, low spending → "Conservative Buyers"

These clusters didn’t exist beforehand, but were discovered based on patterns in the data.

Why It’s Useful:
The company can create targeted promotions or personalized experiences for each segment.

For example:
Push discounts to Cluster 0
Upsell premium items to Cluster 1
Send loyalty rewards to Cluster 2

**Transforming features for better clusterings / Standardization/ Normalization**

Clustering algorithms like K-Means rely on Euclidean distance to assign points to clusters. 
If your features are on different scales, one feature might dominate the distance calculation.
Example:
Feature	            Range
Age	                18–70
Annual Income	  $10,000–$100,000

Without scaling, income will have a much larger effect on distance than age, simply because of its numeric range.

Why Standardization Helps:
Standardization transforms data so that each feature:
Has a mean of 0
Has a standard deviation of 1

This ensures all features contribute equally to the clustering process.

What Happens Without Standardization?

Clusters may be formed based on one dominant feature.
You get incorrect or misleading clusters.
Metrics like silhouette score can be low even if K is chosen correctly.

StandardScaler is an example of a "preprocessing" step. There are several of these available in scikit-learn, for example MaxAbsScaler and Normalizer.

**Evaluating a Clustering:**

A good clustering has tight clusters, meaning that the samples in each cluster are bunched together, not spread out.

1. Inertia measures clustering quality: 
How spread out the samples within each cluster are can be measured by the "inertia". Intuitively, inertia measures how far samples are from their centroids.
We want clusters that are not spread out, so lower values of the inertia are better.
A good clustering has tight clusters (meaning low inertia). But it also doesn't have too many clusters. 

A good rule of thumb is to choose an elbow in the inertia plot, that is, a point where the inertia begins to decrease more slowly. 

2. Silhouette Score

Measures how similar a point is to its own cluster vs other clusters.
Range: -1 to 1
1: well clustered
0: overlapping clusters
<0: possibly wrong cluster

**Two unsupervised learning techniques for visualization: t-SNE and hierarchical clustering.**

**Hierarchical clustering** 

Hierarchical clustering is an unsupervised learning method that builds a hierarchy of clusters — like a tree (called a dendrogram). Unlike K-Means, you don’t need to specify the number of clusters (K) upfront.

Types of Hierarchical Clustering:

Agglomerative (Bottom-Up)

Start with each point as its own cluster
Merge the closest clusters step-by-step
Stop when everything is merged or a threshold is reached

Divisive (Top-Down)

Start with one big cluster
Recursively split clusters into smaller ones

**T-SNE**

t-SNE stands for "t-distributed stochastic neighbor embedding". 
It maps samples from their high-dimensional space into a 2- or 3-dimensional space so they can visualized.

**Dimensionality Reduction:**

Dimension reduction finds patterns in data, and uses these patterns to re-express it in a compressed form. 
This makes subsequent computation with the data much more efficient, and this can be a big deal in a world of big datasets. 
However, the most important function of dimension reduction is to reduce a dataset to its "bare bones", discarding noisy features.

**Principal Component Analysis:**

PCA is most fundamental of dimension reduction techniques.
PCA performs dimension reduction in two steps, 

In the first step, PCA rotates the samples so that they are aligned with the coordinate axes. 
In fact, it does more than this: PCA also shifts the samples so that they have mean zero.
And, No information is lost - this is true no matter how many features the dataset has. 

PCA, due to the rotation it performs, "de-correlates" the data, in the sense that the columns of the transformed array are not linearly correlated.

Linear correlation can be measured with the **Pearson correlation**. 
It takes values between -1 and 1, where larger values indicate a stronger correlation, and 0 indicates no linear correlation. 

PCA is called "principal component analysis" because it learns the "principal components" of the data. 

principal components = directions of variance = directions in which the samples vary the most.

PCA aligns principal components with the coordinate axes.

Intrinsic Dimension:

The intrinsic dimension of a dataset is the number of features required to approximate it. 
Essential idea behind dimension reduction
The intrinsic dimension informs dimension reduction, because it tells us how much a dataset can be compressed.

So how can the intrinsic dimension be identified, even if there are many features? 
The intrinsic dimension can be identified by counting the PCA features that have high variance.
The intrinsic dimension is the number of PCA features that have significant variance.

Dimension reduction with PCA:

PCA performs dimension reduction by discarding the PCA features with lower variance, which it assumes to be noise, and retaining the higher variance PCA features, which it assumes to be informative.

**How PCA Works:**

Standardize the data (Mean = 0, Std. Dev = 1)
Compute the covariance matrix
Compute eigenvectors and eigenvalues. These determine the principal components
Select top k principal components. Choose those that explain the most variance (using a scree plot or cumulative variance)
Project the data
Transform the original data onto the new lower-dimensional space

**Why Use Dimensionality Reduction?**

Reduce computational complexity
Remove redundant or irrelevant features
Help with visualization 

**Example: Medical Diagnosis Using Patient Data**

A hospital collects data from thousands of patients with the goal of identifying patterns that could help in diagnosing heart disease. Each patient’s record includes:
Age, Blood pressure, Cholesterol level, Heart rate, ECG results, Number of previous hospital visits, BMI, Blood sugar level, Family history of heart disease, Exercise level, Medication adherence, Smoking status, Alcohol consumption
Total: 20+ features per patient
Problem:
The dataset has high dimensionality.
Many features may be correlated (e.g., cholesterol & blood pressure).
Hard to visualize patterns in such a high-dimensional space.
Machine learning models suffer from overfitting or slow training due to redundant features.

Solution: Apply PCA
Standardize the data
Use PCA to reduce the 20+ features to 3 or 4 principal components that explain 90–95% of the variance.

Use these components to:
Feed into clustering algorithms to find patient risk groups
Visualize patient health profiles in 2D or 3D
Train faster and more accurate predictive models

Outcome:
After applying PCA:
Component 1 captures general health risk (combining age, BP, cholesterol, etc.)
Component 2 reflects lifestyle factors (exercise, smoking, alcohol)
Component 3 includes genetic and medical history







