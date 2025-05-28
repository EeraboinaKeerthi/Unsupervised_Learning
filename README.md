**Unsupervised learning**

Unsupervised learning finds patterns in data.

Ex: "clusters" of customers based on their purchase histories, or searching for patterns and correlations among these purchases, 
and using these patterns to express the data in a compressed form. 
These are examples of unsupervised learning techniques called "clustering" and "dimension reduction".

Clustering:

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

