Unsupervised learning finds patterns in data.

Ex: "clusters" of customers based on their purchase histories, or searching for patterns and correlations among these purchases, 
and using these patterns to express the data in a compressed form. 
These are examples of unsupervised learning techniques called "clustering" and "dimension reduction".

Clustering:

K Means Clustering:

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




