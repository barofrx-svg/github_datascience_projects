⚠️ FOR DYNAMIC, 3D PLOTS AND BEST EXPERIENCE please view the notebook on nbviewer or Google Colab, as GitHub's built-in viewer cannot render heavy interactive JavaScript or 3D plots. ⚠️

[View full notebook on NBViewer](https://nbviewer.org/github/barofrx-svg/github_datascience_projects/blob/main/project_4_clustering/clustering.ipynb) or [View full notebook on Google Colab](https://colab.research.google.com/github/barofrx-svg/github_datascience_projects/blob/main/project_4_clustering/clustering.ipynb)

# Customer Segmentation
I followed these steps in this project: data preprocessing, feature extraction and creation, applying StandardScaler, creating clusters using the elbow method and silhouette score, inferred and recommended strategies for clusters, created clusters for outlier customers


Unfortunately the 3d plots are to big for GitHub to show them inside the notebook so I will create static images from the 3d plots.

<img width="900" height="700" alt="7" src="https://github.com/user-attachments/assets/429c5806-ed16-4dbe-91cc-5c997d6675af" />

Every point on this plot represents a unique customer in the United Kingdom zone. There are points almost anywhere which implies customer diversity. Identifying clusters will help the marketing department tailor specific strategies to each group.

Also there is a positive correlation with frequency and monetary value, which is a no brainer, a customer who spends regurarly spends more in total.

<img width="950" height="750" alt="8" src="https://github.com/user-attachments/assets/56b80272-12a6-4d9a-965a-285cbf65d038" />

Now these clusters look much more meaningful, and tell much more about the retail store`s customer base. I can see top spenders in yellow and turquise, and lost customers in light blue. Now that I have these clusters, I need to create a description about each one of them, how many customers there are, what are the statistics within the clusters. This helps identifying and describing the customer segments.
