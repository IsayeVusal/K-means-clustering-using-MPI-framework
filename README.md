# K-means-clustering-using-MPI-framework

Distributed K-means clustering using MPI framework

Mission of the k-means clustering algorithm is to take a given dataset and partition these observations up into k number of clusters. Deciding on where these clusters lie is computationally difficult but each cluster should be representative of all its surrounding data points. It algorithm is unsupervised learning method and hopes to gain some sort of insight into data that may be unseemingly unrelated.

Distributed Functionalities

Given that k-means clustering problem is a NP-Hard computationally intensive problem, a distributed approach seems appropriate. By dividing up the computation load among many worker nodes, the program can be parallelized and sped up.
The root node reads in the entire dataset and randomly chooses the initial k-means for each cluster.
The root node broadcasts the k-means to each n number of workers.
The root node distributes the dataset among n number of workers.
Given its portion of the entire dataset, each worker does computational work against each k-means cluster and returns the result to the root.
The algorithm repeats for X number of iterations.

• Initialize K centroids

• Divide Data instances among P workers (X shown in figure, different colors represent parts at
different workers)

• Unitill converge

– step 1
∗ calculate distance of each Data instance from each centroid using the euclidean distance.
(populate Distrance matrix shown in the figure)
∗ Assign membership of each data instance using the minimum distance in the distance
matrix.

– step 2
∗ Each worker calculates the new centroids (local means) using the new membership of data
instance.
∗ collect updated centroids (local mean) information from each worker and find the global
centroids (global mean).
∗ redistribute new centroids of clusters to each worker.


With MPI, we can distribute data points to different processes using MPI_Bcast, and use MPI_Allreduce to exchange information whenever needed. Thus, both the E-step and the M-step can be parallelized. This time, we get speed-up in both steps, so the overall scaling is better than OpenMP.

